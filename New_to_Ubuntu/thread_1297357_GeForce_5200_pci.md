---
title: "GeForce 5200 pci"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by ibbill on 2009-10-21
I have the driver on my desktop that I downloaded from Nvidia.Enclosed a pic 



NVIDIA-Linux-x86-173.14.20-pkg1.run

can anyone help me install this please.

---

### Post by coolbrook on 2009-10-21
I suggest you copy and paste the driver to your home folder.

Open up a terminal window:

```

sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86-173.14.20-pkg1.run
sudo /etc/init.d/gdm start
```

Reboot

Edit: If it appears to hang on you after command number 1, then type Alt-F1 to get a login prompt, log in and continue.

---

### Post by ibbill on 2009-10-21
thanks ever so much for the help after I press alt f1 I  typed in name and password.Then some more stuff came up with the terminal type ending to the page I typed the next line in and said it could not open with sh tried it without sh still no luck. Going to take the card out  wait for the new system in a few days see if that will work.

Again thanks ever so much for your help

Bill

---

### Post by themusicalduck on 2009-10-21
This is what you should do - first press ctrl+alt+f1. Then login. Type:

```
sudo killall gdm
cd Desktop
sudo sh NVIDIA-Linux-x86-173.14.20-pkg1.run
```

Then reboot by typing ```
sudo reboot
```

That will work and you just need to follow the instructions on screen.

Also it might be quicker to type sudo sh NVI and then press the tab button to autocomplete the command.

EDIT: On second thought, it might just be easier to go to System > Administration > Hardware Drivers to see if you can install them from there unless you specifically want to install the one from the NVidia site.

---

### Post by ibbill on 2009-10-21
Thanks for your help got so the computer would not even boot up removed the card and all is well.

Deleted all the nvidia files and drivers I could find still get the message its running in low res.

But it is running fine.

Is there anyway to get rid of all the nvidia files on my computer now.

Question whats the best cards for ubuntu

Bill

---

### Post by themusicalduck on 2009-10-21
Try the command ```
sudo dpkg-reconfigure xserver-xorg -phigh 
``` Hopefully it'll reset your display to default settings again.

Sucks the NVidia card didn't work. Doesn't seem like there's usually a problem with those cards, but isn't such a big deal if you don't mind using onboard instead.

As for good cards, NVidia are generally the best on linux. I have a gtx260 which works great, and I've used a 9800GT which also worked great. It depends what budget you have on what can be recommended really.

---

