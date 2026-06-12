---
title: "Connect to other computer through network?"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-03-29
I used to be able to connect to the other computers on my network in Windows. Does anyone know if it is possible to see the other computers connected via router on Linux and be able to exchange files from computer to computer?

---

### Post by RetchingRabbit on 2009-03-29
> **UnknownFear said:**
> I used to be able to connect to the other computers on my network in Windows. Does anyone know if it is possible to see the other computers connected via router on Linux and be able to exchange files from computer to computer?

Yes. Definitely possible. If the other computers are windows machines try Samba.

---

### Post by UnknownFear on 2009-03-29
> **RetchingRabbit said:**
> Yes. Definitely possible. If the other computers are windows machines try Samba.

I don't want to install another OS, I am perfectly fine with Ubuntu, thank you :) No, I want to be able to connect to my other Windows Vista family computer and be able to transfer files over from this computer to that one. Is there anyway of doing this WITHOUT installing a new OS? There has to be a way.

---

### Post by xpod on 2009-03-29
> Is there anyway of doing this WITHOUT installing a new OS?

Yup,samba.:wink:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by mkvnmtr on 2009-03-29
Samba is the app that connects to Windows machines. It is very simple to use. I am sure a google search will give you a better tutorial than I can. The basics are already installed on your Ubuntu but you might want to go to the package manager and put samba in the search box and study the packages that are there. That is what I did and in about 30 minutes I had it working.

---

### Post by cool_fp on 2009-03-29
Yes I think the is possible through logmein.com as well
___________
[collections]("www.offcollections.com")

---

### Post by coffeecat on 2009-03-29
There's one easy thing to do to get samba working, as follows:

Go to your home folder and create a folder. Call it what you will. Right-click on it and select 'Sharing Options'. Click on "Share this folder" and a window will pop up saying 'Sharing service not installed'. Click on the 'Install service' button and whatever needs to be installed will be. You'll then be prompted to restart your session (log out and log in again).

After that any shares you set up in Ubuntu should be visible in your Windows machine (follow the same procedure as before but this time you will be able to create a share) and any shares in your Windows machine should be visible in Ubuntu.

Have fun!

---

### Post by dross_kuh on 2009-03-29
30 min`s ...  if i remember right it takes about 30 sec`s ...

right-mouse-button on the desktop, create new folder (call it shared :))
right-mouse-button over the new-folder and onto sharing-options,

the rest is self explanatory...


eek sum1 beat me 2it :(

---

### Post by halitech on 2009-03-29
> **cool_fp said:**
> Yes I think the is possible through logmein.com as well
___________
[collections]("www.offcollections.com")

this is helpful in controlling them if they are behind the same router but moving files back and forth is not possible without upgrading to Pro or IT Reach.

[https://secure.logmein.com/products/free/](https://secure.logmein.com/products/free/)

---

### Post by stchman on 2009-03-29
> **UnknownFear said:**
> I used to be able to connect to the other computers on my network in Windows. Does anyone know if it is possible to see the other computers connected via router on Linux and be able to exchange files from computer to computer?

If you are going all Ubuntu then use either NFS

[http://www.stchman.com/share_NFS.html](http://www.stchman.com/share_NFS.html)

or use ssh

Both are a fast and easy way to transfer files.

---

### Post by UnknownFear on 2009-03-29
> **coffeecat said:**
> 
Have fun!

I followed everything you said, but I don't know where I can see the other computer. I went to Places -> Network and I saw my iPod Touch (which I found was a simpler way to access all my music :)), and I saw Windows Network. I clicked on it, but I got an error saying *Unable to mount location. Failed to retrieve share list from server*. What exactly does this mean?

---

