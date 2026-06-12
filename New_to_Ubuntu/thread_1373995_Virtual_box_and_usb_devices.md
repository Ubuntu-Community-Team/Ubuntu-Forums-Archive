---
title: "Virtual box and usb devices"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Falc7 on 2010-01-06
Hi
I am trying to get windows 7 installed in virtual box running on ubuntu to see the usb devices i've attached, i went to settings of the guest machine->usb-> and put 3 empty filters in, but the guest OS sees nothing. Can someone help?

---

### Post by Methuselah on 2010-01-06
I think (anyone sure?) that VirtualBox-OSE does not have USB passthrough.
Is that what you are using?

---

### Post by clive littlewood on 2010-01-06
Hi

On my virtual win 7 I just enter settings and USB then tick the 2 USB boxes.

I do not enable any filters.

When you have the os running, right click on the USB icon in the bottom taskbar and enable the device.

With this setup I can see any USB device plugged in.

Hope this helps.

Clive

---

### Post by Saghaulor on 2010-01-06
> **Methuselah said:**
> I think (anyone sure?) that VirtualBox-OSE does not have USB passthrough.
Is that what you are using?

Yeah, for usb passthrough you gotta use the non ose version.

Some devices don't work well though. I had issues with something, but currently I can't remember what it was. More coffee . . . .

---

### Post by mkvnmtr on 2010-01-06
I am using the latest download from Sun and I click on the second icon where you add filters and it lists all my usb devices. I click on the box of the one that I wish to enable and it is done. My usb mouse and keyboad seem to be automaticly working. I switched from the OSE version when I had a little trouble getting usb to work.

---

### Post by Darce on 2010-01-06
Hi Falc,

You can get the non OSE version here :

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

or from the Syanptic Package Manager

Cheers.

---

### Post by Falc7 on 2010-01-06
Yep i am using the non OSE version as got from the above link^

[www.ubuntu-pics.de/bild/36831/screenshot_012_i0NLPW.png](www.ubuntu-pics.de/bild/36831/screenshot_012_i0NLPW.png)

Here is a screenshot, as you can see virtual box says there are no usb devices attached, yet i have my external HDD attached and mounted. i've enabled usb filters as shown here

[www.ubuntu-pics.de/bild/36832/screenshot_013_1iqWT6.png](www.ubuntu-pics.de/bild/36832/screenshot_013_1iqWT6.png)

But i still cant see usb devices in the guest OS, except that is, for the mouse

---

### Post by Darce on 2010-01-06
Falc,

Just to clarify, are they not there at all, or greyed-out and not selectable ?

Tim

---

### Post by Falc7 on 2010-01-06
> **clive littlewood said:**
> Hi

On my virtual win 7 I just enter settings and USB then tick the 2 USB boxes.

I do not enable any filters.

When you have the os running, right click on the USB icon in the bottom taskbar and enable the device.

With this setup I can see any USB device plugged in.

Hope this helps.

Clive

> **Darce said:**
> Falc,

Just to clarify, are they not there at all, or greyed-out and not selectable ?

Tim

The boxes on the bottom of the taskbar in which the guest machine is running are greyed out

---

### Post by Darce on 2010-01-06
Right click on the Virtual Box Machine USB icon. It should bring up a box as in attached pic. Place tick next to devices you want the machine to see

---

### Post by adelphos on 2010-01-06
If they are greyed out, then you need to add yourself to the "vboxusers" system group.

---

### Post by Falc7 on 2010-01-06
For me those are greyed out 

[www.ubuntu-pics.de/bild/36839/screenshot_017_93isgn.png](www.ubuntu-pics.de/bild/36839/screenshot_017_93isgn.png)

---

### Post by Darce on 2010-01-06
Go to System/Admin/Users&Groups
Click the key button and enter your PW
Click on 'manage groups'
Scroll down to vboxusers and click properties
Place a tick on your username under 'group members' and hit OK,close,close.

You will need to restart your PC ( Real not virtual ! )

---

### Post by adelphos on 2010-01-06
> **Falc7 said:**
> For me those are greyed out 

[www.ubuntu-pics.de/bild/36839/screenshot_017_93isgn.png]("http://www.ubuntu-pics.de/bild/36839/screenshot_017_93isgn.png")

Yeah, that looks like a lot like you haven't added yourself to the "vboxusers" group, since you can't use those tick-boxes. The same thing happened to me.

EDIT: Ah. Thanks, Darce! I didn't think to give instructions, which was silly.

---

### Post by Falc7 on 2010-01-06
> **Darce said:**
> Go to System/Admin/Users&Groups
Click the key button and enter your PW
Click on 'manage groups'
Scroll down to vboxusers and click properties
Place a tick on your username under 'group members' and hit OK,close,close.

You will need to restart your PC ( Real not virtual ! )

Thanks! working great now :D

---

