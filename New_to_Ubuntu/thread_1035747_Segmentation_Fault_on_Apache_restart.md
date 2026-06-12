---
title: "Segmentation Fault on Apache restart"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2009-01-10
Hello ya'll,

I now have 2 Kubuntu 8.04 Hardy test web servers and 1 Xubuntu notebook set up and working correctly. I am trying to set up a 
3rd Kubuntu syststem I have copied all web data from the other Kubuntu system including the Apache.conf file for some reason when I restart the Apache server I get a Segmentation Fault error.  I have reverted back to the original Apache.conf file and restarted but get the same Segmentation Fault error it will not even run the It Works! page running from localhost.  Does anyone have an idea what this error is telling me to check. All tips and help will be appreciated.

Thanks in advance


James in GA USA

---

### Post by blueridgedog on 2009-01-10
Perhaps something went wrong during the install.  I suggest you uninstall it and reinstall it.
```

sudo apt-get remove apache

sudo apt-get install apache
```

After a clean install, verify that it works before migrating other config data.

---

### Post by JKHinton CPBD on 2009-01-10
Hey Blueridgedog,

Thanks for the response.  I tried the commands you had the only thing I had to change was adding a 2 to the end of Apache.  It ran the command and uninstalled Apache2 so then I ran the install command and it also ran went through the usual reading database and then unpacking followed by setting up apache2       (2.2.8-1ubuntu0.3_all.deb)  I then ran the restart command got the same error Segmentation fault.  I then went to my /root/etc/apache2/apache2.conf file and opened to find my old conf. file which proabaly had a newer date, seems like it should have deleted this file and installed the default .conf file should I have to manually delete my file first and then try uninstall and install again?

Thanks again for the help.

James in GA USA

---

### Post by blueridgedog on 2009-01-10
It may be that apache is faulting in an effort to load a module that is not there, as referenced by the config, so deleting it and doing the uninstall/reinstall may get results.

---

### Post by minsf on 2009-01-10
the reason you found your old apache.conf file is that you removed apache2 and not purged it. when you use
```
sudo apt-get remove package_name
```
it removes the package files (in our case, apache2) but NOT the configuration files. when you use 
```
sudo apt-get purge package_name
```
or when you use the "apt-get remove" command with the option "-purge", it will remove the package completely, and then when you install it again, you will have the default installation files.
I am not sure if you really want all your configuration files to be removed, so be careful about using purge.
i know this does not help solving your segmentation problem, but i hope it explains a bit of the reinstallation mystery that you had.
cheers :)

---

### Post by JKHinton CPBD on 2009-01-10
Thanks to you too minsf for your response. Sounds like my best bet would be to delete my apache2.conf file and then run the commands that blueridgedog shared to uninstall and then reinstall apache2 and this should install a new apache2.conf file.  Please excuse this next newbie question, what is the best command to use to delete the /etc/apache2/apache2.conf file only without deleting the whole folder will this command work?

 sudo rm -/etc/apache2/apache2.conf

---

### Post by minsf on 2009-01-10
hi James (and thanks for ur help on my thread)
i am not sure why you have a minus sign before the path. i think you want:
```
sudo rm -i /etc/apache2/apache2.conf
```
I like to add the -i option for safety, it means it will ask for your confirmation for every file before really deleting it, windows-style... it is especially useful option when dealing with more than one file, like when you put * and ?

when i look in my apache2.conf file (i have a fresh lamp-server installation), i see that it includes other configuration files from the /etc/apache2 directory and its subdirectory, especially the ports.conf file and the /etc/apache2/sites-available/default file (which is symlinked from /etc/apache2/sites-enabled/000-default), but other files too.

my point is that the configuration file is spread over multiple files, so if you delete apache2.conf and reinstall (dont purge) and it still does not work, you may want to do the same to other configuration files in /etc/apache2; that is, back them up and delete them by 
```
mv filename.conf filename.conf.backup
``` 
(or you can first copy with "cp" and then delete with "rm")
and then remove and install apache2. 

by the way, i think that 
```
 sudo apt-get install --reinstall apache2
``` is equivalent to doing "apt-get remove" and then "apt-get install".

---

