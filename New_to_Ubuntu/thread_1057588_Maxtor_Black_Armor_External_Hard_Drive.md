---
title: "Maxtor Black Armor External Hard Drive"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by 72andsunny on 2009-02-02
Hi all,

I'm having a little trouble getting my computer to recognize this new external hard drive. When I plug it in, I get an "unable to mount drive" message. I've tried partitioning it with GParted, but I get "Error while setting new disklabel".

I'm new to Ubuntu, any help would be appreciated.

Thanks!

---

### Post by minsf on 2009-02-02
please post here the output of
```
sudo lshw -C disk -sanitize|less
```
and ```
sudo lspci
```
to enter these commands, you will need to get a command line interface -for instance by Applications>Accessories>Terminal or Konsole or just alt+ctrl+F2 (to go back to the desktop use alt+ctrl+f7)

---

### Post by cybergalvez on 2009-02-02
> **minsf said:**
> please post here the output of
```
sudo lshw -C disk -sanitize|less
```
and ```
sudo lspci
```
to enter these commands, you will need to get a command line interface -for instance by Applications>Accessories>Terminal or Konsole or just alt+ctrl+F2 (to go back to the desktop use alt+ctrl+f7)

Shouldn't that be alt-ctrl-F1 ?  and I've always just used alt-F7 to get back

---

### Post by minsf on 2009-02-02
> **cybergalvez said:**
> Shouldn't that be alt-ctrl-F1 ?  and I've always just used alt-F7 to get back
think about these as 7 channels. you can go to channel x by alt+ctrl+Fx, where x can be 1,2,3,4,5,6,7. "channel" 7 is the used for the graphical user interface. i didnt want him to go to "channel 1" (tty1) as it is also used for some system output. for instance, say you are editing some document in "channel 1" with nano/emacs/vim and while editing, you insert something into the usb, then the system reports the connection on the screen, and this can be confusing as it is mixed with your editor's display... so i thought that alt+ctrl+f1 would be ssafer for him :)

---

### Post by 72andsunny on 2009-02-02
> **minsf said:**
> please post here the output of
```
sudo lshw -C disk -sanitize|less
```
and ```
sudo lspci
```
to enter these commands, you will need to get a command line interface -for instance by Applications>Accessories>Terminal or Konsole or just alt+ctrl+F2 (to go back to the desktop use alt+ctrl+f7)

First one just said: (END)

Here's the other

:~$ sudo lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

---

### Post by minsf on 2009-02-03
please enter ```
sudo lshw -sanitize|less
```
you may be asked for your password.
you'll then be able to scroll up and down your system's info with the arrows (quit with "q"). so scroll down until you see the info about the relevant drive, cut and paste it here.

---

### Post by lnthai2002 on 2009-02-03
I have the maxtor black armor 160G too, on the box it says: support windows XP, vista and also "Drive does not work with any other OS as unlocking utility is required". I don't even receive the "can not mount" message when i plug the disk, all I got is the drive making some small beep with the active led blinking.
Does any one know any linux alternative for this drive with on-disk data protection ?

---

### Post by halitech on 2009-02-03
wouldn't it be ```
sudo lsusb
``` if its an external drive connected by a usb cable and not lspci?

---

### Post by minsf on 2009-02-08
> **halitech said:**
> wouldn't it be ```
sudo lsusb
``` if its an external drive connected by a usb cable and not lspci?
you are right. my mistake...
thanks for spotting it
cheers

---

### Post by ctphinest on 2009-05-19
The following post gives instructions to get the Maxtor Black Armor to work in Ubuntu by using virtual box and installing a virtual windows os.

[http://ubuntuforums.org/showthread.php?p=7309718#post7309718](http://ubuntuforums.org/showthread.php?p=7309718#post7309718)

Since this security unlocking software can only run in a windows envirnment, i believe the only way to use the storage device in ubuntu is either to have a dual boot ubuntu / windows system or to have a virtual windows system in ubuntu.  After a bit of trial and error I have had success with both.

---

