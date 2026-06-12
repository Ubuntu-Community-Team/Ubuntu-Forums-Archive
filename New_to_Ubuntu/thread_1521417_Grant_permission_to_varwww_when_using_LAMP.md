---
title: "Grant permission to var/www when using LAMP"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by TheAdamJanes on 2010-06-30
Hello, I am very green to Ubuntu 10.4 LTS and Linux in general. I found a great site to help me download Apache, MySQL, and PHP in a LAMP package from this [thread ]("http://ubuntuforums.org/showthread.php?t=1508998")at UbuntuForums. 

Now, I'm trying to add my folders, with PHP projects, from an external hard drive to the var/www location on my LInux OS computer. It is telling me this:

Error while copying.
The folder "IP2" cannot be copied because you do 
not have permissions to create it in the destination.
 
(IP2 is my current independent project)

What can I do in order to work out of the var/www folder? 

This looks like an awesome forum, and it's the first place I went to for help. I appreciate you taking time to help a newbie like me.

---

### Post by lisati on 2010-06-30
What I do is prepare the web site on my laptop, copy the data across to my server using samba, then from the command line move to the shared folder, and use the following:
```
sudo cp -r * /var/www/
```

---

### Post by TheStroj on 2010-06-30
If you want a GUI way to do this you must run file browser as root.

Press Alt + F2 and type:
```
gksu nautilus
```

This will grant you root acces to all files so now you can edit whetever files you want.

If you prefer using terminal, you must copy files as root by either using 'sudo' in front of command or making yourself root for the time you dont exit it:
```
sudo su
```

Hope this was helpful :)

---

### Post by TheAdamJanes on 2010-07-01
Stroj! Thank you very much. :)
I went with your first suggestion (gksu nautilus), but when I go to "http://localhost/Form_IP2/myTest.php" I get: 
**Forbidden**

 You don't have permission to access /Form_IP2/myTest.php on this server.
  Apache/2.2.14 (Ubuntu) Server at localhost Port 80
*While I am able to add and edit the files now, I'm not able to test them. Any suggestions?
 ty

---

### Post by TheStroj on 2010-07-01
I'm not an expert in internet related stuff, but try changing permission of files in folder. Maybe it's the problem because they've been modified by root.

To change permissions, open Terminal and navigate to the directory containing your folder that has the web page files in it:
```
cd /var/www/you_know_if_there_are_more/
```

When you get to the directory that has folder with your webpage stuff, use this command on it:
```
sudo chmod -R 777 folder_name
```

Now type your password and thats it.

To check if it worked type:
```
ls -l folder_name
```

Right at the begining of a file there will be a mess of characters that looks something like this:
```
drwxrwxrwx 3 jure jure 4096 2010-06-29 12:21 GTK+
```

'd' in the begining means directory, tripple 'rwx' means read/write/execute permission for root/group/user. 

Now try accesing webpage again. If it wont work at first, try restarting software running your webpage.

If that doesnt work i have no idea what's wrong :P

Hope it helps :)

---

