pip freeze > requirement.txt
pip install -r requirements.txt
pip install django
django-admin startproject ***
在manage.py目录下 python manage.py startapp ***
在项目文件夹创建虚拟环境

setting.py:
ALLOWED_HOSTS = ['*']
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'mysitedb',
        'USER': 'root',
        'PASSWORD': 'password',
        'HOST': '127.0.0.1',
        'PORT': '3306',
    }
}
pip install pymysql
在项目__init__.py中添加：
import pymysql
pymysql.install_as_MySQLdb()


AUTH_USER_MODEL = "app_name.User_class" #替换默认用户表   User_class inherit (AbstractUser): from django.contrib.auth.models import AbstractUser

LANGUAGE_CODE = 'zh-hans'
TIME_ZONE = 'Asia/Shanghai'

TEMPLATES = [
    'DIRS': [os.path.join(BASE_DIR, 'templates')],    
]  #设置TEMPLATES里的'DIRS'，添加模板目录templates的路径，后面我们做网站模板的时候用得着。



INSTALLED_APPS = [
    'django.contrib.admin',
    ....
    'blog.apps.BlogConfig',#注册APP应用
]

在项目根目录里创建static和media，两个目录。static用来存放模板CSS、JS、图片等静态资源，media用来存放上传的文件，后面我们在讲解数据库创建的时候有说明。
settings里找到STATIC_URL，然后在后面一行加上如下代码。
myblog/settings.py

#设置静态文件目录和名称
STATIC_URL = '/static/'
#加入下面代码
#这个是设置静态文件夹目录的路径
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "static")
]
#设置文件上传路径，图片上传、文件上传都会存放在此目录里
MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')

django将所有app放到一个apps文件夹中
第一步 新建一个文件夹 apps
第二步将所有的app拖到apps中，会提示勾选Search for references ，把这个勾去掉
第三步选中apps文件夹，右键Make Directory As -> Resoure Root
第四步 在setting.py 中添加 sys.path.insert(0,os.path.join(BASE_DIR,”apps”)) 


编写model  class ***（models.Model)：



python manage.py makemigrations
python manage.py migrate


python manage.py createsuperuser






