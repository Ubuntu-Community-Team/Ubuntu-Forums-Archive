---
title: "usb in oracle virtual box"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by josephmills on 2011-02-11
Hi there gnu/linux users, 
So I installed virtualbox 4.0 last night and have been having some problems with usb connecting inside of the virtualbox. I installed the extension pack and also the guest additions. Also I have went to the settings on virtual box and looked at the usb part and added some usb devices. The settings recognize the devices but when I launch virtual box I cant seem to find any any of the devices via usb. or anything usb for that matter. well thanks for looking this over and I thank you in advance for the help.



Richard Stallmans nervous system is completely wireless:D

---

### Post by P4man on 2011-02-11
Did you install the OSE version from the repositories, or the PUEL version from oracle site? The first one doesnt support USB, you need the PUEL version.

---

### Post by josephmills on 2011-02-11
> **P4man said:**
> Did you install the OSE version from the repositories, or the PUEL version from oracle site? The first one doesnt support USB, you need the PUEL version.

I installed from this website.and selected the linux user one.  [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) 
I should also state that I am a complete noob.so please bare with me if I did not answer your question correctly

---

### Post by P4man on 2011-02-11
Okay that is the correct version. 

Next thing to check, go to System -> Administration > "Users and Groups" > "Manage Groups" > vboxusers >  Properties

Check the box beside your user name to ensure you are member of vboxusers.

Reboot.

---

### Post by josephmills on 2011-02-11
> **P4man said:**
> Okay that is the correct version. 

Next thing to check, go to System -> Administration > "Users and Groups" > "Manage Groups" > vboxusers >  Properties

Check the box beside your user name to ensure you are member of vboxusers.

Reboot.

thank you thank you thank you I think that I am where I want to be now but I am not going to mark as solved just yet. If I have any more problems I will post once again thank you for your time

---

