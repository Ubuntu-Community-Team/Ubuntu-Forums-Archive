---
title: "Booting from LiveUSB at home"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Jelee8804 on 2011-03-29
Hi!

I experimented with ubuntu 10.10 with VirtualBox on Windows Vista. I like what I see and I would like to take it a step further to boot Ubuntu from a LiveUSB. I followed the steps online and created my USB. It works perfectly when I boot a school computer with the stick in the slot, but at home my computer completely ignores the usb and boots Windows right away. I've tried going into BIOS (F2) and setting "generic compact USB" as my first boot mode. This didn't work, so I tried entering the boot menu (F10) and selected USB from the list of boot options. The computer still boots into Windows.

I know that the USB isn't the problem now because it works at school, and it must be that my home BIOS is out of date. I have a Gateway computer, forgot the exact model right now, but AMD chipset quadcore.

Can anyone suggest anything for me? Do I need to update my BIOS? Can updating my BIOS potentially harm my files/configuration of Windows?

Any help would be appreciated. I've been struggling with this for a couple of days.

---

### Post by Dutch70 on 2011-03-29
Try other usb ports on the front & back of your computer. It may have something to do with whether they are usb 2.0 or 3.0 and I don't know much about that. Except to tell you to try all of them, not just one on the back & one on the front.

Alternatively you could burn a cd.

---

### Post by oklokl on 2011-03-29
usb->Extended partition
os save..
not booting.. system..
or corrupted
Once you are corrupted

In my case
I did that

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
Recommended

and
Depending on pc
Depending on the model should recognize USB

---

### Post by Jelee8804 on 2011-03-29
I would try burning it to a CD and installing it to my HDD, but I'd like the entire OS to be on a persistent thumb drive. This way I can carry it around with me.

Anyone have any suggestions?

---

### Post by I2k4 on 2011-03-30
Don't know if this is your problem.  When I first started using Live USB I had the impression that if I created one USB drive on my main PC, the same USB would boot on my netbook.  That was wrong.  The very good instructions here (plus Persistence)

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

worked great for whichever machine I first create the USB drive on, but that installation just won't boot on any other machine.

Maybe there is another way, and I'd be interested to know it, but I'm using different Live USB drives, specifically installed on each of my separate Windows computers, and they are not interchangeable.

If your main concern is accessing data, like schoolwork files, between home and school and whatever, you might be interested in an online sync and storage service like Dropbox, which can be installed on the Live USB as well as any Windows or Mac or even many smartphone OSs:

[www.dropbox.com](www.dropbox.com)

---

### Post by Dutch70 on 2011-03-30
I've never used the universal usb installer I2k4 is referring to, so I was unaware that you could only boot the computer it was made from with it. Sounds really weird.

Anyway, you won't have that problem if you use Startup Disk Creator that comes with Ubuntu or Unetbootin, which you can use from windows if necessary. 
You can find it here... [[COLOR="RoyalBlue"]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")

---

### Post by C.S.Cameron on 2011-03-30
A lot of older computers will not boot flash drives no matter what you do, unless you use a boot manager like **plop**.
Plop will boot flash using a floppy or CD or it can be installed in Windows.

---

### Post by I2k4 on 2011-03-31
> **Dutch70 said:**
> I've never used the universal usb installer I2k4 is referring to, so I was unaware that you could only boot the computer it was made from with it. Sounds really weird.


I didn't think it's weird, considering the Live USB (with Persistence to save settings and preferences between boots) has to deal with the specific hardware configuration for the machine it boots.  I've used the installer on two machines and on four versions of Ubuntu/Lubuntu without any hardware recognition issues of the kind others often complain about in the forum.  But again, only one machine per Live USB drive. 

I suspect that if there is some way to create an "all purpose" Live USB drive that boots Ubuntu on any machine, it will not be Persistent, which for me is a useful feature.

---

### Post by C.S.Cameron on 2011-03-31
> **I2k4 said:**
> I didn't think it's weird, considering the Live USB (with Persistence to save settings and preferences between boots) has to deal with the specific hardware configuration for the machine it boots.  I've used the installer on two machines and on four versions of Ubuntu/Lubuntu without any hardware recognition issues of the kind others often complain about in the forum.  But again, only one machine per Live USB drive. 

I suspect that if there is some way to create an "all purpose" Live USB drive that boots Ubuntu on any machine, it will not be Persistent, which for me is a useful feature.


A persistent and even a full install to flash will boot multiple computers as long as you don't install proprietary, (Nvidia), drivers on it.

---

### Post by Jelee8804 on 2011-04-13
Hi guys,

Thanks to all those who have been giving me advice on this issue. I have been doing a lot of searching on this topic and this is whAt I came up with. The problem is with my monitor and graphics card. When the screen went blank and the monitor said ther eas no input, I noticed that the USB is still working hard. His means that things are actually running underneath the black screen. Some people have been adding nomodeset from their grub menu, but instead I connected my old monitor to my computer. Seems like ubuntu can't handle hdmi connections, buy analog connections work perfectly. 

Next issue at hand. I got ubuntu 10.10 installed on my system, but I don't want to stay on my old little monitor so i installed the proprietary graphics card drivers. It tells me that I need to reboot to finish the update, but when I do, it boots straight to the terminal and prompts for login. It is on tty1. At this point I tried startx, but it fails. This terminal mode works on both hdmi and analog. 

So, I restarted the system and entered failsafe mode with low graphics, and this reverts me back to the blank screen issue. Hdmi monitor goes black, but the analog monitor shows me the GUI. 

I tried updatig the drivers via ati's site manually, and also used ubuntu's auto updater. Both take me straight to the terminal. 

Can anyone advise me?

---

### Post by Jelee8804 on 2011-04-14
bump

---

