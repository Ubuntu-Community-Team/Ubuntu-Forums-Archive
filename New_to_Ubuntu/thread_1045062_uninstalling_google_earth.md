---
title: "uninstalling google earth"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-20
hi.. i just installed google earth by following the instructions from

[http://davestechsupport.com/blog/2008/10/31/10-things-to-do-after-you-install-ubuntu-linux/](http://davestechsupport.com/blog/2008/10/31/10-things-to-do-after-you-install-ubuntu-linux/)

i want to unistall this application(google earth). i have searched for the same in
Add/Remove and Synaptic Package manager..
 
in both the places i cannot find google earth..

how do i uninstall google earth.. please help...

---

### Post by overdrank on 2009-01-20
> **chethankrish said:**
> hi.. i just installed google earth by following the instructions from

[http://davestechsupport.com/blog/2008/10/31/10-things-to-do-after-you-install-ubuntu-linux/](http://davestechsupport.com/blog/2008/10/31/10-things-to-do-after-you-install-ubuntu-linux/)

i want to unistall this application(google earth). i have searched for the same in
Add/Remove and Synaptic Package manager..
 
in both the places i cannot find google earth..

how do i uninstall google earth.. please help...

Hi and you may find this [helpful]("https://help.ubuntu.com/community/GoogleEarth#Uninstallation")

---

### Post by chethankrish on 2009-01-20
i followed the instructions in the site(link provided by you)... but am getting some error.. the screen shot of the same is as below..

krsna@ubuntu:~$ sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth
[sudo] password for krsna: 
rm: cannot remove `/usr/share/mime/application/vnd.google-earth.*': No such file or directory
rm: cannot remove `/usr/share/mimelnk/application/vnd.google-earth.*': No such file or directory
rm: cannot remove `/usr/share/applnk/Google-googleearth.desktop': No such file or directory
rm: cannot remove `/usr/share/mime/packages/googleearth-mimetypes.xml': No such file or directory
rm: cannot remove `/usr/share/gnome/apps/Google-googleearth.desktop': No such file or directory
rm: cannot remove `/usr/share/applications/Google-googleearth.desktop': No such file or directory
rm: cannot remove `/usr/local/bin/googleearth': No such file or directory
krsna@ubuntu:~$

---

### Post by chethankrish on 2009-01-20
please somebody help.... please....................

---

### Post by overdrank on 2009-01-20
> **chethankrish said:**
> please somebody help.... please....................

I believe I received the same errors as that when I removed also. Have you tried the second command and are you sure that google earth is not removed.

---

### Post by chethankrish on 2009-01-20
i have not tried the second command.. but i am sure google earth is not removed..

 its still in applications>internet>google earth

---

### Post by jrusso2 on 2009-01-20
You installed google earth from a .bin file.  Those usually have an uninstall.  I would check where it installed to and look for something like .uninstall. or .uinstallgoogleearth

---

### Post by chethankrish on 2009-01-20
where can i find those files... where is it installed in my system.. i really have very little idea of the same...

---

### Post by jrusso2 on 2009-01-20
I am not sure since I have the google earth from mediabuntu but if I had to guess I would say check /opt/google

---

### Post by chethankrish on 2009-01-20
yup.. i found it.. it was in my home folder.. it had an unistall file.. i unistalled and deleted that folder too.. now its not showing up in applications>internet... 

thanx a lot for your help...

---

### Post by darkhole on 2009-02-18
The answer to uninstall Google Earth 5 installed using the .bin file like sudo in Ubuntu Linux:
[http://ubuntuforums.org/showpost.php?p=6753733&postcount=10](http://ubuntuforums.org/showpost.php?p=6753733&postcount=10)

---

