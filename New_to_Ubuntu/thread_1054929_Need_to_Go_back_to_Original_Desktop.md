---
title: "Need to Go back to Original Desktop"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by halovivek on 2009-01-30
Hi 
I have installed the compiz and dock bar using this [thread]("http://ubuntuforums.org/showthread.php?t=1038142").
Now i want the original desktop back. 
because i could not watch the movies due to flickering of the screen. So i am getting angry on this. So planning to go back.
Please help me.

---

### Post by hyper_ch on 2009-01-30
simples way would be to just delete/rename the .gnome folder in your home. Then it will regenerate all gnome settings to a default stage.

So you won't loose any settings and stuff I'd say rename it:
```

mv ~/.gnome /gnome_old

```

Do this when you're logged out.

---

### Post by halovivek on 2009-01-30
> **hyper_ch said:**
> simples way would be to just delete/rename the .gnome folder in your home. Then it will regenerate all gnome settings to a default stage.

So you won't loose any settings and stuff I'd say rename it:
```

mv ~/.gnome /gnome_old

```

Do this when you're logged out.

Yesterday i have installed the KDE desktop. There also i am having the dock. I want to replace in both KDE as well as Gnome.

---

### Post by hyper_ch on 2009-01-30
for kde the according folder is .kde :)

---

### Post by LowSky on 2009-01-30
your problem is from your graphics card. Yuo could always keep your settings and install fusion-icon (it in the repos), and switch between Compiz and Metacity (normal settings) during video playback

---

### Post by halovivek on 2009-01-31
> **hyper_ch said:**
> simples way would be to just delete/rename the .gnome folder in your home. Then it will regenerate all gnome settings to a default stage.

So you won't loose any settings and stuff I'd say rename it:
```

mv ~/.gnome /gnome_old

```

Do this when you're logged out.

gurudheva@gurudheva-laptop:~$ mv ~/.gnome /gnome_old
mv: cannot move `/home/gurudheva/.gnome' to `/gnome_old': Permission denied
gurudheva@gurudheva-laptop:~$ sudo su
[sudo] password for gurudheva: 
root@gurudheva-laptop:/home/gurudheva# mv ~/.gnome /gnome_old
mv: cannot stat `/root/.gnome': No such file or directory
root@gurudheva-laptop:/home/gurudheva# mv ~/.gnome /gnome_old
mv: cannot stat `/root/.gnome': No such file or directory
root@gurudheva-laptop:/home/gurudheva# 
 
how to do this?

---

### Post by Nepherte on 2009-01-31
~ is a short notation for the user home directory, so for the user gurudheva it's /home/gurudheva. With sudo su you switched to the user root. That means ~ is now a short notation for the root home directory.

The command you need to type in is:
```
mv /home/gurudheva/.gnome /home/gurudheva/.gnome_old
```

---

### Post by ugm6hr on 2009-01-31
Strange you don't have permissions to your user folder.

The other option is simply to uninstall compiz if you don't want it:

```
sudo apt-get remove compiz-core
```

Remember to edit your "Sessions" to remove Avant from the auto-started apps list.

---

### Post by halovivek on 2009-02-01
> **ugm6hr said:**
> Strange you don't have permissions to your user folder.

The other option is simply to uninstall compiz if you don't want it:

```
sudo apt-get remove compiz-core
```

Remember to edit your "Sessions" to remove Avant from the auto-started apps list.

I have removed as you said. But till now i could not do Right click in the desktop and i could not see the files in the desktop. How i can get it back?

---

### Post by ugm6hr on 2009-02-01
> **halovivek said:**
> I have removed as you said. But till now i could not do Right click in the desktop and i could not see the files in the desktop. How i can get it back?

What do you mean - you can't right clink on the desktop?  Usually, a drop-down menu appears.  I don't know how to remove / activate that option in Gnome...

Post the output from:
```
ls -l ~/
```

---

### Post by halovivek on 2009-02-01
gurudheva@gurudheva-laptop:~$ ls -l ~/
total 15244
drwx------ 2 gurudheva gurudheva     4096 2009-01-23 15:06 amsn_received
drwxr-xr-x 2 gurudheva gurudheva     4096 2009-01-04 00:16 Azureus Downloads
drwxr-xr-x 2 gurudheva gurudheva     4096 2009-01-05 20:41 bin
drwxr-xr-x 4 gurudheva gurudheva     4096 2008-12-26 14:03 c
drwxr-xr-x 4 gurudheva gurudheva     4096 2009-02-01 16:56 Desktop
drwxr-xr-x 7 gurudheva gurudheva     4096 2009-01-02 20:42 Documents
drwxr-xr-x 2 gurudheva gurudheva     4096 2009-01-02 19:29 dwhelper
lrwxrwxrwx 1 gurudheva gurudheva       26 2008-12-26 13:14 Examples -> /usr/share/example-content
-rw-r--r-- 1 gurudheva gurudheva     6498 2008-03-02 04:35 getlibs-all.deb
drwxr-xr-x 3 gurudheva gurudheva     4096 2009-01-05 20:41 google-earth
drwx------ 8 gurudheva gurudheva     4096 2009-01-05 15:26 Mail
-rw-r--r-- 1 gurudheva gurudheva     5767 2008-12-29 21:12 melody.pls
drwxr-xr-x 2 gurudheva gurudheva     4096 2008-12-26 13:19 Music
-rw-r--r-- 1 gurudheva gurudheva        0 2008-12-27 10:35 photos-20081228-0.db
drwxr-xr-x 3 gurudheva gurudheva     4096 2009-01-09 20:51 Pictures
drwxr-xr-x 2 gurudheva gurudheva     4096 2008-12-26 13:19 Public
-rw-r--r-- 1 gurudheva gurudheva 15506542 2008-06-16 10:49 skype-install.deb
drwxr-xr-x 2 gurudheva gurudheva     4096 2008-12-26 13:19 Templates
-rw-r--r-- 1 gurudheva gurudheva       30 2008-12-27 10:47 Unsaved Document 1
drwxr-xr-x 3 gurudheva gurudheva     4096 2009-01-02 23:14 Videos
drwxr-xr-x 3 gurudheva gurudheva     4096 2009-01-04 02:04 zimbra
gurudheva@gurudheva-laptop:~$

---

### Post by ugm6hr on 2009-02-01
Your Desktop folder is there.

Not sure what the problem is, unless you have installed an alternative Desktop manager - perhaps thunar or pcmanfm or rox-filer?

---

### Post by halovivek on 2009-02-01
Nothing i have installed. And last i have done one thing.
this is the thing i have done
mv /home/gurudheva/.gnome /home/gurudheva/.gnome_old

---

### Post by halovivek on 2009-02-05
Even i tried the above one. till now i could not see anything in the desktop. I kept some files in desktop.

---

### Post by ugm6hr on 2009-02-05
Try this:
```
nautilus ~/Desktop
```

---

### Post by halovivek on 2009-02-05
> **ugm6hr said:**
> Try this:
```
nautilus ~/Desktop
```

i am getting the contents in desktop but i could not see anything in normal view. here below i have attachements for your reference


gurudheva@gurudheva-laptop:~$ nautilus ~/Desktop
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension
seahorse nautilus module initialized
Initializing nautilus-image-converter extension

** (nautilus:7076): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Shutting down nautilus-image-converter extension
seahorse nautilus module shutdown
Shutting down nautilus-share extension
Shutting down nautilus-open-terminal extension
Segmentation fault

---

### Post by ugm6hr on 2009-02-05
So the files are still there.

Presumably, moving your .gnome folder changed the location of your desktop in nautilus.

---

### Post by halovivek on 2009-02-05
so how to get back that one?

---

