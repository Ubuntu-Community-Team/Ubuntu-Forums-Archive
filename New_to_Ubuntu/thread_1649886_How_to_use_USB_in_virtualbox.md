---
title: "How to use USB in virtualbox?"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-12-20
I finally got windows XP installed in virtual box so that i can use a scanner that doesn't work in ubuntu. When i got to the usb section in ubuntu there is no option to select the scanner as when i plug the scanner in via usb nothing actually happens, im sure the scanner works but i am not sure how i would test this. I installed the drivers in XP on virtual box but i can't make the scanner register on XP, I have no idea how to use the USB mode in VB to let XP pick up the scanner and not let it rely on the host OS picking it up.

---

### Post by johnmay on 2010-12-20
the OSE version of Virtualbox does not support USB. Here is a link about using usb [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)


I believe now though if you are using the latest versions, that it works out of the box.

---

### Post by Rave Gloves on 2010-12-20
Im using the closed source version where it dose have the usb section. Nothing seems to be happening though when i have the scanner plugged in. Not sure if it's the scanner that's the problem :(

---

### Post by t0p on 2010-12-20
I assume that you installed VirtualBox through Synaptic, or possibly you installed the "Free" version from [www.virtualbox.org]("http://www.virtualbox.org/") - **VirtualBox OSE**, "OSE" means "Open Source Edition" (I'm using the word "Free" to mean "open source" - all versions of VirtualBox are free in the monetary sense).

Unfortunately, the Free version doesn't have the ability to use usb devices.  If you want VirtualBox to have usb support, you'll have to install the full **PUEL** edition ("PUEL" stands for "Personal Use and Evaluation License", which doesn't meet the reqwuirements of the GPL).  You can get VirtualBox PUEL [here]("http://www.virtualbox.org/wiki/Downloads") - just make sure it's the **PUEL** version you install, *not* the OSE version.

**EDIT:** I just saw your reply that you *did* install the closed source edition.  When you click on **Devices** and go to the **USB** section, is the scanner in the list of devices?  If so, is it ticked?  You need to click on it to tick it, which makes it available to the guest OS.  If the scanner *doesn't* appear in the list... I dunno.

---

### Post by Rave Gloves on 2010-12-20
> **t0p said:**
> I assume that you installed VirtualBox through Synaptic, or possibly you installed the "Free" version from [www.virtualbox.org]("http://www.virtualbox.org/") - **VirtualBox OSE**, "OSE" means "Open Source Edition" (I'm using the word "Free" to mean "open source" - all versions of VirtualBox are free in the monetary sense).

Unfortunately, the Free version doesn't have the ability to use usb devices.  If you want VirtualBox to have usb support, you'll have to install the full **PUEL** edition ("PUEL" stands for "Personal Use and Evaluation License", which doesn't meet the reqwuirements of the GPL).  You can get VirtualBox PUEL [here]("http://www.virtualbox.org/wiki/Downloads") - just make sure it's the **PUEL** version you install, *not* the OSE version.

Last night i installed the Closed source edition from the website, It dose have usb support, I actually think that the scanner is broken, or my usb 2.0 cable is broken, it must be that :/

---

### Post by lbarnes on 2010-12-20
Go to System > Administration > Users & Groups and be sure vbox is checked.  Go to os settings in vbox and be sure the usb filter for the scanner is added and checked.  In windows in vbox go to Devices > USB and be sure the scanner usb filter is present and checked.

---

### Post by Rave Gloves on 2010-12-20
Im pretty sure it's this cable, i plugged in my laser printer that dose work with ubuntu the printers status says it's unplugged. Argh :(

---

### Post by seaking69 on 2011-02-26
> **lbarnes said:**
> Go to System > Administration > Users & Groups and be sure vbox is checked.  Go to os settings in vbox and be sure the usb filter for the scanner is added and checked.  In windows in vbox go to Devices > USB and be sure the scanner usb filter is present and checked.

i have done all of the above and still my usb isn't functionening. (i'm trying to work with aver media dvb via usb.

---

### Post by le1 on 2011-07-31
Go to:

System --> Administration --> Users & Groups --> Manage Groups --> 

select: vboxusers --> press: properties --> tick in "Group Members" your nickname --> OK --> reboot Ubuntu

Ps. VirtualBox-OSE does not support USB, you have to download VB from their website:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) 

and this pack: VirtualBox Oracle VM VirtualBox Extension Pack gives you support for USB 2.0.

---

### Post by dave01945 on 2011-08-18
is your usb device recognised by

```
lsusb
```

if so have you selected the device within the virtualbox device menu at the bottom same place you would mount a cd/dvd to virtualbox

---

