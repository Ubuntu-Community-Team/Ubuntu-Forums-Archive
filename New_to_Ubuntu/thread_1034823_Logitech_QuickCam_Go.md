---
title: "Logitech QuickCam Go"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by babloo75 on 2009-01-09
Hi friends,
I bought A Logitech QuickCam Go and am unable to use it on ubuntu. To be true don't know how to search for the correct software to install the same.
the output to "lsusb" is as follows:

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:092f Logitech, Inc. QuickCam Express Plus
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 413c:3016 Dell Computer Corp. 
Bus 001 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Can anybody suggest a direct link to the above mentioned webcam software. the search for the software on sourceforge.net was a bit confusing and couldn't lead me to the required one. a step be step procedure is most welcome..
Thanks in advance

---

### Post by Hallvor on 2009-01-09
> **babloo75 said:**
> Hi friends,
I bought A Logitech QuickCam Go and am unable to use it on ubuntu. To be true don't know how to search for the correct software to install the same.
the output to "lsusb" is as follows:

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:092f Logitech, Inc. QuickCam Express Plus
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 413c:3016 Dell Computer Corp. 
Bus 001 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Can anybody suggest a direct link to the above mentioned webcam software. the search for the software on sourceforge.net was a bit confusing and couldn't lead me to the required one. a step be step procedure is most welcome..
Thanks in advance

All you need is probably a driver in Synaptic. I have a Logitech webcam myself, and they usually work perfectly with linux. Search for Logitech in Synaptic and a driver should turn up. You may need to reboot to make the new driver install to your kernel.

To test if your webcam is working, try e.g. Camorama. It is also in Synaptic.

---

### Post by deepclutch on 2009-01-09
install the gspca module for the kernel version you have in Ubuntu.
else ,install gspca source and use module assistant to compile the module.and it needs few more tweaking to have some what good reception.
I hope Ubuntu users can explain the procedure exactly here.

---

### Post by babloo75 on 2009-01-09
> **Hallvor said:**
> All you need is probably a driver in Synaptic. I have a Logitech webcam myself, and they usually work perfectly with linux. Search for Logitech in Synaptic and a driver should turn up. You may need to reboot to make the new driver install to your kernel.

To test if your webcam is working, try e.g. Camorama. It is also in Synaptic.

No it didn't help me... whenever i open Camorama, it says "unable to capture image" i click "ok" and then it disappears

---

### Post by rajeev1204 on 2009-01-09
There is no need to install anything .Gspca is already built into the kernel.No need to build modules.
Its Plug and a little tweak and play.


I have the exact same model and its detected automatically in ubuntu.Sometimes camorama or other such stuff may not work. I use xawtv to adjust the camera brightness etc and then use it in skype.

What application are u using for webcam? Skype etc?

---

### Post by Hallvor on 2009-01-09
Got back on my regular computer. I don`t use Ubuntu, but on pclos there is a driver called dkms-qc-usb-messenger for Logitech Quickcams.

The gspca driver does not work with my (Logitech) webcam.

From my lsusb:
"Bus 005 Device 005: ID 046d:09a4 Logitech, Inc"

---

### Post by babloo75 on 2009-01-09
> **rajeev1204 said:**
> There is no need to install anything .Gspca is already built into the kernel.No need to build modules.
Its Plug and a little tweak and play.


I have the exact same model and its detected automatically in ubuntu.Sometimes camorama or other such stuff may not work. I use xawtv to adjust the camera brightness etc and then use it in skype.

What application are u using for webcam? Skype etc?

I was wondering can i use my web cam in ubuntu? i just hate skype, but have pidgin internet messenger installed. can i use it in yahoo option of pidgin?

---

### Post by babloo75 on 2009-01-09
> **Hallvor said:**
> Got back on my regular computer. I don`t use Ubuntu, but on pclos there is a driver called dkms-qc-usb-messenger for Logitech Quickcams.

The gspca driver does not work with my (Logitech) webcam.

From my lsusb:
"Bus 005 Device 005: ID 046d:09a4 Logitech, Inc"

can u explain a bit in detail... what does "pclos" mean?

---

### Post by Hallvor on 2009-01-09
> **babloo75 said:**
> I was wondering can i use my web cam in ubuntu? i just hate skype, but have pidgin internet messenger installed. can i use it in yahoo option of pidgin?

Pidgin doesn`t support webcams yet. I think you must use Kopete to make it work on yahoo. Perhaos there are other options, but Kopete is what I use for instant messenging.

Pclos is short for PCLinuxOS - a linux distro, but I am sure it can be fixed some way in Ubuntu, too.

---

### Post by babloo75 on 2009-01-09
> **Hallvor said:**
> Pidgin doesn`t support webcams yet. I think you must use Kopete to make it work on yahoo. Perhaos there are other options, but Kopete is what I use for instant messenging.

Pclos is short for PCLinuxOS - a linux distro, but I am sure it can be fixed some way in Ubuntu, too.

is kopete compatible with gnome desktop environment. i m using ubuntu with gnome

---

### Post by rajeev1204 on 2009-01-10
> **babloo75 said:**
> is kopete compatible with gnome desktop environment. i m using ubuntu with gnome


Ya it works fine on gnome .Kopete will let you use your wecam  for yahoo IM. Keep in mind though , voice chat is not supported.


Skype is best for voice.

---

### Post by babloo75 on 2009-01-10
can I install yahoo messenger alone (instead of pidgin).
If not, can u plz tell me how to install skype. But if i can install yahoo msngr, then plz tell me how to install that one instead.
Thanks

---

### Post by rajeev1204 on 2009-01-10
You can install yahoo messenger but i suggest you use skype instead.Its a lot easier.Yahoo messenger is ugly for linux. :),and you can use pidgin for yahoo IM .

Use medibuntu to install packages with ease .

[http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)


Scroll down and you will see skype and skype common. Install these 2 packages according to whether you are using 32 or 64 bit .

I assume you are using intrepid ibex 8.10.There are packages for older versions too.

Let me know.


regards

rajeev

---

### Post by babloo75 on 2009-01-10
thanks dear, i will install skype and let you know.

---

### Post by Aviendha09 on 2009-03-26
this is a good thread for installing logitech webcams that have a compatibility issue with 8.10 and/or Skype. It got mine working.

Using Xawtv when cam is on video0 allows you to adjust your cam before switching over to gstfakevideo for Skype.

[http://ubuntuforums.org/showthread.php?t=1043579]("http://ubuntuforums.org/showthread.php?t=1043579")

---

### Post by babloo75 on 2009-08-25
At last I have come here again........ but with same Logitech Quickcam and different Ubuntu (9.04 Jaunty)
Can anyone help me how to use this webcam on this Ubuntu 9.04. I have already installed Skype on my system.
Thanks in advance.

---

