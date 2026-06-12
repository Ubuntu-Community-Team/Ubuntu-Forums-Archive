---
title: "APTonCD, is there APTonUSB or Media"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by leulae on 2009-08-12
[COLOR=#2E3436][FONT=Arial]APTonCD, is there**[COLOR=Red] APTonUSB[/COLOR]** /**[COLOR=SeaGreen] [/COLOR]**[/FONT][/COLOR]    [COLOR=#2E3436][FONT=Arial]**[COLOR=SeaGreen] APTonMedia[/COLOR]**/ [/FONT][/COLOR]
[B][COLOR=#2E3436][FONT=Arial]
[/FONT][/COLOR][/B]
  
  [COLOR=#2E3436][FONT=Arial] [/FONT][/COLOR]
  [COLOR=#2E3436][FONT=Arial]APTonCD[/FONT][/COLOR]**[COLOR=#2E3436][FONT=Arial] creates CD or DVD images, for selected packages , we have to burn and install the packages even for a small package.   Is there any method to get extract the package with all dependencies to the USB or to a Folder, [/FONT][/COLOR]**    
[B][COLOR=#2E3436][FONT=Arial]
[/FONT][/COLOR][/B]
[B][COLOR=#2E3436][FONT=Arial]or 
[/FONT][/COLOR][/B]
[B][COLOR=#2E3436][FONT=Arial]
[/FONT][/COLOR][/B]
**[COLOR=#2E3436][FONT=Arial]please suggest me any method to overcome this problem[/FONT][/COLOR]**


    
**[COLOR=#2E3436][FONT=Arial]Thanks in advance[/FONT][/COLOR]**
  
**[COLOR=#2E3436][FONT=Arial][/FONT][/COLOR]**

---

### Post by Cheesemill on 2009-08-12
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by Ji Ruo on 2009-08-12
You don't need to burn the ISO file created by AptonCD. It will save it to the hard drive, and then give you the option to burn it. Choose no and exit the program. Go into your file manager and navigate to the directory you saved it in, then copy and paste it to your USB drive. Reverse the process on the other computer and run AptonCD again to unpack it.

---

### Post by angry_johnnie on 2009-08-12
go to 

/var/cache/apt/archives

get al the *.deb files and put them on your usb stick.

---

### Post by Harii on 2009-09-16
If you put them into /var/cache/apt/archives =
can you just 
will you be able to "sudo apt-get update" then upgrade?
or add them one at a time?

aptoncd has alot of bloat.

---

### Post by angry_johnnie on 2009-09-16
> **Harii said:**
> will you be able to "sudo apt-get update" then upgrade?

You could, provided that all the dependencies are met.
As far as I know, apt will look at the archive before attempting to download anything.

But then again, dependencies can be a pain in the neck.
Unless, of course, you "sudo aptitude download" every single package in the repositories, burn it all into dvd's, and point your /etc/apt/sources.list to your disk drive, instead of online repos.

But then, that's just overkill... :p

---

### Post by false_chicken on 2011-01-31
Just out of curiosity, How would one achieve that? Downloading EVERY package from the repositories? Can it be done with one command?

---

