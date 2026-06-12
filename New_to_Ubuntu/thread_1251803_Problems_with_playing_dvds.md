---
title: "Problems with playing dvds"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by monkey_wrench85 on 2009-08-28
I'm new to Ubuntu and linux too. I just installed Ubuntu 9.04.
I'm trying to play a movie on my computer. When I put the movie in and choose movie player I recieve this error:"could not open file location; you may not have permission to open the file". But I checked under my user account and I do have permission to use the cd/dvd drive. I should tell you that I'm following along in a linux tutorial. So in the linux tutorial it states that in order to play dvds I have to install libdvdread4 and this happened.


monkeywrench@computer1:~$ sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
monkeywrench@computer1:~$ 

then when i try to activate the decoder i get this:

monkeywrench@computer1:~$ sudo/usr/share/doc/libdvdread4/install-css.sh
bash: sudo/usr/share/doc/libdvdread4/install-css.sh: No such file or directory


So i went into usr/share/doc/libdvdread4 and clicked "install-css.sh" shell script. I chose run in terminal and nothing happened, then I just clicked on it and chose run and still nothing happened. So finally I just decided to do the third part of the tutorial and that was install vlc through the terminal aswell. Everything downloaded fine but when I try to open up a movie with vlc I get this error:

Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.

and random windows popped up with stills from the movie in them. I figure this is due to not being able to activate libdvdread4/install-css.sh. And for the first one I take it it was already installed but I don't know what is causing the problem with activating the decoder.

Would someone be willing to help me out?

---

### Post by mthalis on 2009-08-28
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

---

### Post by arochester on 2009-08-28
Add the Medibuntu Repository. Instructions here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Note that it is a 2 part installation. 1) Add Repository 2) Get GPG key

sudo apt-get update

Install the package: libdvdcss2

---

### Post by monkey_wrench85 on 2009-08-28
> **arochester said:**
> Add the Medibuntu Repository. Instructions here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
 
Note that it is a 2 part installation. 1) Add Repository 2) Get GPG key
 
sudo apt-get update
 
Install the package: libdvdcss2
 
 
Thank you, everything works fine now. I noticed in your sig you have a link for the linux starter pack and that is the guide I am following for playing dvds. It's odd that it didn't mention anything about having do install medibuntu.

---

