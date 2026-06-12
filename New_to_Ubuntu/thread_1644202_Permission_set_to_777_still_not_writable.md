---
title: "Permission set to 777 still not writable"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by flameash on 2010-12-12
Hi Everyone,

I'm  trying to set up a testing zencart on my LAMP before uploading to the actual server.

However when I try to follow the  installation guide for zen, it says:

cache = Unwriteable   (chmod 777 read/write/execute) 
same errors for  pub, images, media and other folder etc.

So i followed its suggestion to change the permission to 777. 
cd zencart
sudo chmod -R 777 ./cache (same code for other folders)

And after that; I can actually see the permission is changed via Filezilla.

However when i go back to the installation progress again. It still shows the same thing. ><

So I have no idea what to do now.

My Server details are below:
Webserver = Apache/2.2.14 (Ubuntu) 
HTTP Host = localhost
Path_Translated = /var/www/zencart/zc_install/index.php(SCRIPT_FILENAME)
Real Path = /var/www/zencart
PHP O/S = Linux
PHP API Mode = apache2handler
PHP Max Execution Time per page = 300

Please help out.

---

