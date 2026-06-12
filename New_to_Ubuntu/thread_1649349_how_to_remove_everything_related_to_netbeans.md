---
title: "how to remove everything related to netbeans"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by vermaratan on 2010-12-20
Hello there, 
can somebody guide me on how to remove every single file related to netbeans (any version) from ubuntu. 
actually i had netbeans 6.8 (installed via apt-get) but after the ubuntu upgrade it stopped working. 
then i downloaded and installed netbeans 6.9 from their site. but its functionality was also limited (e.g. i was not able to download any plugins ans also while creating a new project i was not allowed to select any framework i have installed e.g struts, MVC etc)
then i tried to uninstall netbeans but didn't succeeded. 
then i logged into my system as root and remove all files related to netbeans (i located those files using the LOCATE command)
Now i am not able to install either of the said versions of netbeans
any help is greatly appreciated. 
Please note that the matter is really urgent as i am working on live projet.

thanks in advance

---

### Post by TeoBigusGeekus on 2010-12-20
Deleting files by hand can mess up apt.
Try to reinstall netbeans
```
sudo apt-get install netbeans
```
and then purge it
```
sudo apt-get purge netbeans
```

---

### Post by vermaratan on 2010-12-20
i managed to install netbeans 6.8 through apt-get;
but now i am not able to add/download any plugins via netbeans. 
ALSO 
i have pre-installed apache2 and glassfish on my system but i am not able to add them in netbeans.
PLEASE HELP !!!

---

