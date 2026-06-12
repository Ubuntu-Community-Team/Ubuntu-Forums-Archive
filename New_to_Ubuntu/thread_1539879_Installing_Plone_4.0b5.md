---
title: "Installing Plone 4.0b5"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by ghinix on 2010-07-27
I achieved this using the [Plone-4.0b5-UnifiedInstaller]("http://plone.org/products/plone/releases/4.0") download, then using the [Unified Installer Instructions]("http://plone.org/documentation/kb/installing-plone-with-the-unified-installer") and it worked.

Then I started Zope/Plone, but I made an **error while changing the admin password **, very likely a typo, and now I can no longer re-login, so I deleted the /home/user/Plone folder in an attempt to re-installing Plone 4 the same way it was successful at first and now I get this instead.... 

Detailed installation log
Starting at Tue Jul 27 03:58:00 EDT 2010
Before install bootstrap.
Scanning installed packages
No setuptools distribution found
running install
install_dir /usr/local/Plone/Python-2.6/lib/python2.6/site-packages/
running bdist_egg
running egg_info
writing distribute.egg-info/PKG-INFO
writing top-level names to distribute.egg-info/top_level.txt
writing dependency_links to distribute.egg-info/dependency_links.txt
writing entry points to distribute.egg-info/entry_points.txt
reading manifest file 'distribute.egg-info/SOURCES.txt'
reading manifest template 'MANIFEST.in'
writing manifest file 'distribute.egg-info/SOURCES.txt'
installing library code to build/bdist.linux-i686/egg
running install_lib
running build_py
creating build
creating build/lib
copying pkg_resources.py -> build/lib
copying easy_install.py -> build/lib
copying site.py -> build/lib
creating build/lib/setuptools
copying setuptools/extension.py -> build/lib/setuptools
copying setuptools/archive_util.py -> build/lib/setuptools
copying setuptools/__init__.py -> build/lib/setuptools
copying setuptools/depends.py -> build/lib/setuptools
copying setuptools/package_index.py -> build/lib/setuptools
copying setuptools/dist.py -> build/lib/setuptools
copying setuptools/sandbox.py -> build/lib/setuptools
creating build/lib/setuptools/tests
copying setuptools/tests/test_easy_install.py -> build/lib/setuptools/tests
copying setuptools/tests/test_resources.py -> build/lib/setuptools/tests
copying setuptools/tests/test_build_ext.py -> build/lib/setuptools/tests
copying setuptools/tests/test_packageindex.py -> build/lib/setuptools/tests
copying setuptools/tests/__init__.py -> build/lib/setuptools/tests
copying setuptools/tests/test_sandbox.py -> build/lib/setuptools/tests
copying setuptools/tests/doctest.py -> build/lib/setuptools/tests
copying setuptools/tests/test_develop.py -> build/lib/setuptools/tests
copying setuptools/tests/test_upload_docs.py -> build/lib/setuptools/tests
creating build/lib/setuptools/command
copying setuptools/command/install_scripts.py -> build/lib/setuptools/command
copying setuptools/command/bdist_egg.py -> build/lib/setuptools/command
copying setuptools/command/egg_info.py -> build/lib/setuptools/command
copying setuptools/command/upload_docs.py -> build/lib/setuptools/command
copying setuptools/command/bdist_wininst.py -> build/lib/setuptools/command
copying setuptools/command/develop.py -> build/lib/setuptools/command
copying setuptools/command/sdist.py -> build/lib/setuptools/command
copying setuptools/command/saveopts.py -> build/lib/setuptools/command
copying setuptools/command/install_lib.py -> build/lib/setuptools/command
copying setuptools/command/alias.py -> build/lib/setuptools/command
copying setuptools/command/__init__.py -> build/lib/setuptools/command
copying setuptools/command/upload.py -> build/lib/setuptools/command
copying setuptools/command/build_ext.py -> build/lib/setuptools/command
copying setuptools/command/bdist_rpm.py -> build/lib/setuptools/command
copying setuptools/command/test.py -> build/lib/setuptools/command
copying setuptools/command/setopt.py -> build/lib/setuptools/command
copying setuptools/command/rotate.py -> build/lib/setuptools/command
copying setuptools/command/easy_install.py -> build/lib/setuptools/command
copying setuptools/command/build_py.py -> build/lib/setuptools/command
copying setuptools/command/install.py -> build/lib/setuptools/command
copying setuptools/command/install_egg_info.py -> build/lib/setuptools/command
copying setuptools/command/easy_install2.py -> build/lib/setuptools/command
copying setuptools/command/register.py -> build/lib/setuptools/command
copying setuptools/cli.exe -> build/lib/setuptools
copying setuptools/gui.exe -> build/lib/setuptools
creating build/bdist.linux-i686
creating build/bdist.linux-i686/egg
copying build/lib/site.py -> build/bdist.linux-i686/egg
copying build/lib/pkg_resources.py -> build/bdist.linux-i686/egg
creating build/bdist.linux-i686/egg/setuptools
copying build/lib/setuptools/extension.py -> build/bdist.linux-i686/egg/setuptools
creating build/bdist.linux-i686/egg/setuptools/tests
copying build/lib/setuptools/tests/test_easy_install.py -> build/bdist.linux-i686/egg/setuptools/tests
copying build/lib/setuptools/tests/test_resources.py -> build/bdist.linux-i686/egg/setuptools/tests
copying build/lib/setuptools/tests/test_build_ext.py -> build/bdist.linux-i686/egg/setuptools/tests
copying build/lib/setuptools/tests/test_packageindex.py -> build/bdist.linux-i686/egg/setuptools/tests
copying build/lib/setuptools/tests/__init__.py -> build/bdist.linux-i686/egg/setuptools/tests
copying build/lib/setuptools/tests/test_sandbox.py -> build/bdist.linux-i686/egg/setuptools/tests
copying build/lib/setuptools/tests/doctest.py -> build/bdist.linux-i686/egg/setuptools/tests
copying build/lib/setuptools/tests/test_develop.py -> build/bdist.linux-i686/egg/setuptools/tests
copying build/lib/setuptools/tests/test_upload_docs.py -> build/bdist.linux-i686/egg/setuptools/tests
copying build/lib/setuptools/archive_util.py -> build/bdist.linux-i686/egg/setuptools
copying build/lib/setuptools/__init__.py -> build/bdist.linux-i686/egg/setuptools
copying build/lib/setuptools/depends.py -> build/bdist.linux-i686/egg/setuptools
copying build/lib/setuptools/package_index.py -> build/bdist.linux-i686/egg/setuptools
copying build/lib/setuptools/cli.exe -> build/bdist.linux-i686/egg/setuptools
copying build/lib/setuptools/dist.py -> build/bdist.linux-i686/egg/setuptools
copying build/lib/setuptools/gui.exe -> build/bdist.linux-i686/egg/setuptools
copying build/lib/setuptools/sandbox.py -> build/bdist.linux-i686/egg/setuptools
creating build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/install_scripts.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/bdist_egg.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/egg_info.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/upload_docs.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/bdist_wininst.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/develop.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/sdist.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/saveopts.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/install_lib.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/alias.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/__init__.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/upload.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/build_ext.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/bdist_rpm.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/test.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/setopt.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/rotate.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/easy_install.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/build_py.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/install.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/install_egg_info.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/easy_install2.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/setuptools/command/register.py -> build/bdist.linux-i686/egg/setuptools/command
copying build/lib/easy_install.py -> build/bdist.linux-i686/egg
byte-compiling build/bdist.linux-i686/egg/site.py to site.pyc
byte-compiling build/bdist.linux-i686/egg/pkg_resources.py to pkg_resources.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/extension.py to extension.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_easy_install.py to test_easy_install.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_resources.py to test_resources.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_build_ext.py to test_build_ext.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_packageindex.py to test_packageindex.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/__init__.py to __init__.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_sandbox.py to test_sandbox.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/doctest.py to doctest.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_develop.py to test_develop.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_upload_docs.py to test_upload_docs.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/archive_util.py to archive_util.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/__init__.py to __init__.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/depends.py to depends.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/package_index.py to package_index.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/dist.py to dist.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/sandbox.py to sandbox.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/install_scripts.py to install_scripts.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/bdist_egg.py to bdist_egg.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/egg_info.py to egg_info.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/upload_docs.py to upload_docs.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/bdist_wininst.py to bdist_wininst.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/develop.py to develop.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/sdist.py to sdist.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/saveopts.py to saveopts.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/install_lib.py to install_lib.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/alias.py to alias.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/__init__.py to __init__.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/upload.py to upload.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/build_ext.py to build_ext.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/bdist_rpm.py to bdist_rpm.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/test.py to test.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/setopt.py to setopt.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/rotate.py to rotate.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/easy_install.py to easy_install.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/build_py.py to build_py.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/install.py to install.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/install_egg_info.py to install_egg_info.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/easy_install2.py to easy_install2.pyc
byte-compiling build/bdist.linux-i686/egg/setuptools/command/register.py to register.pyc
byte-compiling build/bdist.linux-i686/egg/easy_install.py to easy_install.pyc
creating build/bdist.linux-i686/egg/EGG-INFO
copying distribute.egg-info/PKG-INFO -> build/bdist.linux-i686/egg/EGG-INFO
copying distribute.egg-info/SOURCES.txt -> build/bdist.linux-i686/egg/EGG-INFO
copying distribute.egg-info/dependency_links.txt -> build/bdist.linux-i686/egg/EGG-INFO
copying distribute.egg-info/entry_points.txt -> build/bdist.linux-i686/egg/EGG-INFO
copying distribute.egg-info/entry_points.txt.orig -> build/bdist.linux-i686/egg/EGG-INFO
copying distribute.egg-info/top_level.txt -> build/bdist.linux-i686/egg/EGG-INFO
copying distribute.egg-info/zip-safe -> build/bdist.linux-i686/egg/EGG-INFO
creating dist
creating 'dist/distribute-0.6.12-py2.6.egg' and adding 'build/bdist.linux-i686/egg' to it
Traceback (most recent call last):
  File "./setup.py", line 177, in <module>
    scripts = scripts,
  File "/usr/local/Plone/Python-2.6/lib/python2.6/distutils/core.py", line 152, in setup
    dist.run_commands()
  File "/usr/local/Plone/Python-2.6/lib/python2.6/distutils/dist.py", line 975, in run_commands
    self.run_command(cmd)
  File "/usr/local/Plone/Python-2.6/lib/python2.6/distutils/dist.py", line 995, in run_command
    cmd_obj.run()
  File "/home/jv/Plone-4.0b5-UnifiedInstaller/packages/distribute-0.6.12/setuptools/command/install.py", line 73, in run
    self.do_egg_install()
  File "/home/jv/Plone-4.0b5-UnifiedInstaller/packages/distribute-0.6.12/setuptools/command/install.py", line 93, in do_egg_install
    self.run_command('bdist_egg')
  File "/usr/local/Plone/Python-2.6/lib/python2.6/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/local/Plone/Python-2.6/lib/python2.6/distutils/dist.py", line 995, in run_command
    cmd_obj.run()
  File "/home/jv/Plone-4.0b5-UnifiedInstaller/packages/distribute-0.6.12/setuptools/command/bdist_egg.py", line 241, in run
    dry_run=self.dry_run, mode=self.gen_header())
  File "/home/jv/Plone-4.0b5-UnifiedInstaller/packages/distribute-0.6.12/setuptools/command/bdist_egg.py", line 532, in make_zipfile
    z = zipfile.ZipFile(zip_filename, mode, compression=compression)
  File "/usr/local/Plone/Python-2.6/lib/python2.6/zipfile.py", line 663, in __init__
    "Compression requires the (missing) zlib module"
RuntimeError: Compression requires the (missing) zlib module

Please help!
Thanks in advance!

---

### Post by kuadhual on 2010-07-29
> **ghinix said:**
> 
    "Compression requires the (missing) zlib module"
RuntimeError: Compression requires the (missing) zlib module


Missing zlib library?

Is there any error when you try 
```

python -c "import zlib" 

``` ?

well, you can try to install  **zlib1g** or **zlib1g-dev** and try again ;)

---

