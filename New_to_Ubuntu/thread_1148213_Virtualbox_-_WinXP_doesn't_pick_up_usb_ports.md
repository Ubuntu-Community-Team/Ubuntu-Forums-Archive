---
title: "Virtualbox - WinXP doesn't pick up usb ports"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by longtom on 2009-05-04
Hi

The headline says it all.  What I have done so far:

Reinstall the chipset drivers from the motherboard cd in Virtual XP.  USB ports work on a dual boot install of XP.  

Checked, that the settings in VB are correct (USB 2.0 is selected)

Anything else I can try?

---

### Post by Alterax on 2009-05-04
Are you running the closed-source version of virtualbox, or virtualbox-ose?  From what I understand, USB passthrough isn't an option in the OSE (Open-Source edition)

---

### Post by longtom on 2009-05-04
> **Alterax said:**
> Are you running the closed-source version of virtualbox, or virtualbox-ose?  From what I understand, USB passthrough isn't an option in the OSE (Open-Source edition)

Closed source Version 2.2.2

---

### Post by Alterax on 2009-05-04
Oh, one more thing.  The mobo's drivers shouldn't be used on the virtual image... check in the virtual XP box to see if device manager has the USB 2.0 ports listed and drivers.

If there aren't any drivers, make sure to install the Virtualbox guest additions.  It's an option in the menus that has a ton of drivers.  USB may be among them.

If that ain't it (hehehe I just said "ain't"), try using a different set of USB ports on your box.  Mine didn't notice things connected to my front ports, but it did if I plugged them into the ones on the back of the box.  That may be the case here.

---

### Post by longtom on 2009-05-04
Drivers appear to be listed and it says "Device working properly".

I tried all USB ports in front and at the back.  Light of a USB stick would flicker shortly and that would be the total interaction I get out of it.

I try the guest additions and let you know.

---

### Post by ronaldr34 on 2009-05-04
can any help me, i'm using virtualbox trying to configure handy cafe client, not detected on windows xp server.....

---

### Post by geekyhawkes on 2009-05-04
I am having similar problems.  ONe thing to check is once you have your usb device connected check the VM machines device menu and see if it is listed under USB. It might help windows detect the device by deselecting USB then reselecting it.

---

### Post by longtom on 2009-05-04
Have done the guest additions.  Lots of flickering going on.  Don't get the error messages about my VGA and base settings anymore - which is nice.

However - as far as my USB is concerned - no change to the better.

Interesting is, that when I rightclick on the USB devices tag bottom right in the VB window, I can see my devices - however, they are greyed out.

Any more suggestions?

---

### Post by lkraemer on 2009-05-04
USB Information - This used to be posted on this forum somewhere.
It should still apply......I think........

[http://www.informit.com/articles/article.aspx?p=1235054&seqNum=2](http://www.informit.com/articles/article.aspx?p=1235054&seqNum=2)

USB—Click Enable USB and USB 2.0 controller on, go to the small vertical row of icons on the right, hover the mouse over each to find the ToolTip with the Add Filter label, click the Add Filter icon, choose the USB device from the list so the Add Filter Icon triggers, and repeat until all USB devices you want the guest VM to access are connected.


[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)
To get USB support, you need the PUEL version. Via the GUI, there is an option to enable USB.

Furthermore, your user must be able to access /proc/bus/usb/*

Since Gutsy, /proc/bus/usb is not mounted by default. You need to edit /etc/init.d/mountdevsubfs.sh and uncomment the following lines:

        #
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

In order to give users in the vboxusers group write permissions to the devices in /proc/bus/usb, you'll need to edit some rules in /etc/udev/rules.d.

Under gutsy, edit /etc/udev/rules.d/40-permissions.rules to say the following:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"

Under hardy, edit /etc/udev/rules.d/40-basic-permissions.rules to say the following:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664", GROUP="vboxusers"
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"

Then, restart the udev service:

sudo /etc/init.d/udev restart

Now, if you haven't done it already, make sure your user is part of the group vboxusers using the following command:

sudo adduser $USER vboxusers


lkraemer

---

### Post by longtom on 2009-05-04
And....lkraemer has done it again!!:)

Apart from

```

sudo adduser $USER vboxusers

```

all was hot as could be.  But the website you linked, had that last line as
```
sudo usermod -G vboxusers -a `whoami`
```

than a restart - and all works as it should.

Thank you very much!!

---

### Post by phantom3113 on 2009-05-04
I think when lkraemer put "$USER" he meant for you to put in your username ;)

---

### Post by longtom on 2009-05-04
> **phantom3113 said:**
> I think when lkraemer put "$USER" he meant for you to put in your username ;)

I think so too - and so I did....:P.  I was already a member.  Still didn't work until the

sudo usermod -G vboxusers -a `whoami`

I know I might not be the sharpest knife in the drawer, but....

---

### Post by djuke04 on 2009-05-05
Alright,
  I think this is the right place for me to ask this, since I'm having this exact same problem.  

  I'm running Intrepid, and I have an XP guest using Virtual Box 2.2.2 (a PUEL version, I checked, so USB is good to go supposedly).  I'm also having the problem with the USB, where I plug my device in and it is recognized, but grey and no selectable.  

  I found the article on InformIT a few days ago as well as a few other posts around here somewhere that relay the same basic information, but I haven't been successful yet.  

  While I am new to Ubuntu and Linux in general, I'm picking it up very quickly.  I followed the directions perfectly well.  My problem is when I get to the EDIT phase of the instructions, it will not let me save the changes because I don't have permission.  How do I get permission? 

  Are the lines I need to change the same for Intrepid as they are for Hardy? Also I'm looking at probably upgrading to Jaunty soon, is that going to affect the USB aspect of VirtualBox? 

To get to the lines I needed to add, at a terminal I input:

gedit/etc/init.d/mountdevsubfs.sh

 --It opens the window, I found where I need to add the lines, go to close and it won't let me save it


Any clarifying instructions are greatly appreciated thanks!!!

---

### Post by djuke04 on 2009-05-05
Alright,
  I solved my problem by doing my homework about file permissions.  I edited everything according to the instructions (searched out a slightly different set that helped me out with Intrepid), and voila it's good to go.  

  The device was recognized, but there were problems installing it and running it.  Shoot, there's more than one speed bump on this road.

---

### Post by SentientFluid on 2009-05-05
djuke04, when you figured out how to save the changes to the file you were editing, hopefully you used ```
sudo gedit/etc/init.d/mountdevsubfs.sh
```

That would have done it.

If you went in and manually changed the permissions on the file, then that may cause other issues.

---

