---
title: "Installed Google Earth as Root and Now Im in Trouble"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2009-01-05
Yeah I didn't read the posts prior saying don't click start. So I followed the instructions and hit start, now I installed Google Earth as root. I'm trying to delete it, main program in gone. But it looks like I have alot of google earth files left (from installing as root). Any simple way to get rid of all of those files or am I going to have to do a fresh install of Ubuntu? BTW There might be more files elsewhere don't know.

---

### Post by lapubell on 2009-01-05
is there any kind of install log?  you can try to follow that and clean up all the files it created manually.

You probably don't need to do a fresh install of ubuntu, but I know the feeling like you did something wrong and want to start from scratch.

just be extra super carful deleting anything with root permissions...

---

### Post by RookieUbuntuUser58 on 2009-01-05
> **lapubell said:**
> is there any kind of install log?  you can try to follow that and clean up all the files it created manually.

You probably don't need to do a fresh install of ubuntu, but I know the feeling like you did something wrong and want to start from scratch.

just be extra super carful deleting anything with root permissions...

I dont see any install log. Theres a guide on Google website but it didn't help, files still there. The google earth files on my desktop and etc are gone. But doing a terminal search I found alot of files regarding Google Earth. Theres probably more too as I didn't search using other terms.

---

### Post by RookieUbuntuUser58 on 2009-01-05
Okay I went to the Filesystem> then to root. Theres a folder there named .googleearth

How do I delete it, I cant even view the contents of the file?

---

### Post by RookieUbuntuUser58 on 2009-01-05
Edit: I tried sudo apt-get autoremove ~/root/.googleearth but it says couldn't find package.

---

### Post by Malalo on 2009-01-05
Try typing this in a terminal window :

gksu nautilus

This will open up your file system browser with root privileges and you will then be able to view the contents of hidden folders (the ones that start with a period).
You can also try to remove this folder while you have root privileges.

---

### Post by RookieUbuntuUser58 on 2009-01-05
Thanks. I was able to delete all the root apps with names google earth. But how could I be sure I got them all, considering they could be named something else.

Also there are 3 files with the name google earth in them that will not delete (not in root). Couldn't even find them. They were in /usr/local/share/mime/application.

When I type it in terminal under root privileges it still says permission denied.

---

### Post by oldos2er on 2009-01-05
If you installed GE from the *.bin file, run the script /opt/google-earth/uninstall as root.

---

### Post by RookieUbuntuUser58 on 2009-01-05
> **oldos2er said:**
> If you installed GE from the *.bin file, run the script /opt/google-earth/uninstall as root.

Tried that. Said it can't locate the file. I know it didn't do the job because of all the files I have left.

---

### Post by stchman on 2009-01-05
Googleearth is available in the Medibuntu repos.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Once the repos are installed then do the following:

```
sudo apt-get install googleearth
```

---

### Post by LowSky on 2009-01-05
> **stchman said:**
> Googleearth is available in the Medibuntu repos.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Once the repos are installed then do the following:

```
sudo apt-get install googleearth
```

 +1 This is the best way to install Gogle Earth

---

### Post by darkhole on 2009-02-18
To uninstall Google Earth 5 installed using the .bin file:
[http://ubuntuforums.org/showpost.php?p=6753733&postcount=10](http://ubuntuforums.org/showpost.php?p=6753733&postcount=10)

---

