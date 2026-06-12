---
title: "Installing Video Driver"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by card_ace on 2009-05-08
So following the advice in another thread i found the driver for my video card and downloaded it to an external HDD so i could get it to my machine.  but now i can't seem to figure out how to install it.  i'm assuming that i need a terminal code because when i try to click on it i can't make it work.  please help?

---

### Post by taurus on 2009-05-08
What graphic card do you have and what is the name of that file?  Is it still on your external drive or have you copied it to your account, $HOME, on the harddrive?

---

### Post by card_ace on 2009-05-08
here is the result of lspci | grep VGA:

```
carlton@carlton-desktop:~$ lspci | grep VGA 
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2) 
carlton@carlton-desktop:~$
```

and the name of the file is "NVIDIA-Linux-x86-96.43.11-pkg1.run"
and it is still on the external drive.  i didn't know what else to do with it afterward.

---

### Post by taurus on 2009-05-08
If you want to install nvidia driver by hand, you first need to shut down the X server.  Then, install it.  And if everything goes the way it should, assuming the drive that you have downloaded would work with your graphic card, you restart the X server again.

Press <Ctrl><Alt>F2 to get to a console.  Log in with your username and password.  Then, shutdown the X server with

```
sudo /etc/init.d/gdm stop
```
Now, navigate to where you have mount the external drive with your nvidia driver and run

```
sudo sh ./NVIDIA-Linux-x86-96.43.11-pkg1.run
```
Once it is finished installing, you can restart GDM again with

```
sudo /etc/init.d/gdm start
```
Just so you know before you'll be surprised.  The system will crap out if that is not the right driver for your graphic card.  Then, you need to reconfigure your X server again if you want to get back into Gnome.

---

### Post by card_ace on 2009-05-08
alright thanks for the help.  and the warning.  luckily i just had to make a second fresh install for a How-To for school.  i'll try it out there and test it first before i use my good install.  might not be able to come back til Monday, but i'll try to let you know how it goes.

---

### Post by card_ace on 2009-05-11
alright that worked great.  thanks for the help.  and i didn't realize how much of a difference it made having the driver.  i love the desktop effects

---

