---
title: "how to load usb creator on a netbook with 8.04"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by pwynn on 2010-12-02
I am totally new to linux and unbuntu. So  I am really confused! I wanted to load a newer version of unbuntu onto my dell mini laptop. I sure cant figure it out. I downloaded the gtk and the kde and i try to go to the comand line and run it. i guess i should type "sudo usb-creator-gtk" have the time it tell me bad command the other half it asks for a password but it will not allow me to do it. Can anyone give this nebie some help. But i warn you it is going to have to be pretty much step by step. 
thanks

---

### Post by ma4589Ey on 2010-12-02
I worked out a really easy way to transfer the contents of ther  Ubuntu LiveCD to my USB stick and set it bootable, and I thought I’d  document the process here in case it can help anyone else.


  [&#1589;&#1608;&#1585;   ](http://www.mixania.com/)

---

### Post by jmszr on 2010-12-02
pwynn,

First try:
```
sudo apt-get install usb-creator-gtk
```

If that doesn't work, you can download it from here: [http://packages.ubuntu.com/hardy-backports/usb-creator](http://packages.ubuntu.com/hardy-backports/usb-creator) (click on "_all_" near the bottom of the page, then select a mirror from the page that comes up when you click on "_all_". The resultant download can then be installed using the GDebi package installer [which should come up automatically when you download usb-creator].) When installed, it should then be listed under System > Administration.

Edit: When you enter your password in the terminal it will not be visible (for security); just type it in and press "Enter".

---

### Post by pwynn on 2010-12-02
> **ma4589Ey said:**
> I worked out a really easy way to transfer the contents of ther  Ubuntu LiveCD to my USB stick and set it bootable, and I thought I’d  document the process here in case it can help anyone else.


  [&#1589;&#1608;&#1585;   ](http://www.mixania.com/)
Thanks,
Hope you will document it here soon.

---

### Post by pwynn on 2010-12-02
> **jmszr said:**
> pwynn,

First try:
```
sudo apt-get install usb-creator-gtk
```

If that doesn't work, you can download it from here: [http://packages.ubuntu.com/hardy-backports/usb-creator](http://packages.ubuntu.com/hardy-backports/usb-creator) (click on "_all_" near the bottom of the page, then select a mirror from the page that comes up when you click on "_all_". The resultant download can then be installed using the GDebi package installer [which should come up automatically when you download usb-creator].) When installed, it should then be listed under System > Administration.

Edit: When you enter your password in the terminal it will not be visible (for security); just type it in and press "Enter".
Thanks for the help, i have tried entering in my password but it says it is invalid. It is right it must be it is the same password i have to use to do all of the admin stuff on the computer.

---

### Post by jmszr on 2010-12-02
pwynn,

As long as you are using "sudo" and not a variant (not recommended for everyday use) that calls for a root password ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)), I don't know the answer to your issue. 

I suggest starting a new thread with a title that indicates this particular problem.

---

### Post by C.S.Cameron on 2010-12-03
Have you tried just hitting enter when it asks for the password?

---

### Post by pwynn on 2010-12-03
I have been able to get the usb creator to load and i think i made a startup disk but now i am having this problem.

Could not find Kernel Image: Linux

Can you help?

---

### Post by jmszr on 2010-12-03
pwynn,

From looking around there are several possibilities - most of which involve starting over.

The first and simplest is post#5 on this thread:[http://ohioloco.ubuntuforums.org/showthread.php?p=7725008](http://ohioloco.ubuntuforums.org/showthread.php?p=7725008) .

This is from adityasv: For USB sizes greater than 1 GB, go to Gparted (sudo gparted).
In gparted,
1. Select the USB device
2. Format as Fat16
3. Check that the flag section only has - boot (I had boot, lba - and had to remove lba)

Exit Gparted.

Then create the USB startup disk from System->Administration->Create USB startup disk.

These may be of help: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick), also: [http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/#more-5191](http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/#more-5191) , and: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Several threads suggest using UNetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/).

Another says instead "use another program called "win32diskimager" on windows to mount the ISO image onto the USB drive."

This one's a rather technical fix for "Could not find Kernel Image: Linux", so I saved it for last: [http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/) .

Hope that helps, I think I'll pick up another flash drive and try it out for myself.

---

### Post by C.S.Cameron on 2010-12-03
> **pwynn said:**
> I have been able to get the usb creator to load and i think i made a startup disk but now i am having this problem.

Could not find Kernel Image: Linux

Can you help?

This could be due to  a bad iso download, check the MD5SUM.

---

