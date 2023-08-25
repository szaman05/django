# Django

## Basic Settings:

1. Create Project:

   ```python
   django-admin startproject btre
   ```
2. Run Dev Server:

   ```
   python3 manage.py runserver
   ```
3. Create App:

   ```python
   django-admin startapp pages
   ```
4. Add the new app to project-folder/settings.py

   ```python
   INSTALLED_APPS = [
       'django.contrib.admin',
       'django.contrib.auth',
       'django.contrib.contenttypes',
       'django.contrib.sessions',
       'django.contrib.messages',
       'django.contrib.staticfiles',
       'pages.apps.PagesConfig'
   ]
   ```
5. Apply the changes with migration:

   ```bash
   python3 manage.py migrate
   ```
6. Create superuser:

   ```ba
   python3 manage.py createsuperuser
   ```
7. Create urls.py into the new app folder:

   ```bash
   touch pages/urls.py
   ```
8. In the base project urls.py include the path for new apps urls:

   ```python
   from django.contrib import admin
   from django.urls import include, path


   urlpatterns = [
       path('admin/', admin.site.urls),
       path('',include('pages.urls')),
   ]
   ```
9. In the newly created app name pages urls page add the pages apps urls:

   ```python
   from django.contrib import admin
   from django.urls import path
   from . import views


   urlpatterns = [
       path('', views.index, name='index'),
   ]
   ```
10. Add the view functions to view the page:

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    # Create your views here.
    def index(request):
        return HttpResponse('Hello World')
    ```
