---
title: "USB does not work in VirtualBox"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by s1baker on 2010-12-05
I have Ubuntu 10.10 32 bit running on a desktop.
VirtualBox was downloaded from the VB website.
My Ubuntu Usergroups has both vboxusers and lp groups selected.

-----------------------------------------------

I have VirtualBox ( downloaded from VirtualBox website ) installed with
Windows XP on it. "machine/settings/USB" on VB are checked.
When I start XP the settings for "Devices/USB Devices" are ghosted out.
The USB was working perfectly yesterday, but today, for some reason, they are ghosted out. Does anybody have any ides how to get my USB back.
Yesterday I was trying to setup a com connection in XP, but I don't know whether or not that may have something to do with it.

---

### Post by s1baker on 2010-12-05
anybody?

---

### Post by LinuxCharms on 2010-12-05
Have you tried restarting VB then plugging it back in?

Otherwise I'd say It would have something to do with a com you set up.

---

### Post by s1baker on 2010-12-05
yes, I have started and re-started VB many times, I have also installed the Guest Editions, but I still show the USB devices ghosted out.

---

### Post by CharlesA on 2010-12-05
> **s1baker said:**
> yes, I have started and re-started VB many times, I have also installed the Guest Editions, but I still show the USB devices ghosted out.

I don't know tbh. I ran into the same problem with VirtualBox on my Ubuntu host, never got it figured out, so I don't use USB with it.

---

### Post by aeronutt on 2010-12-05
You probably need to change /etc/group to allow virtual box access to USB via your account.
Edit /etc/group with your favorite text editer. Search for "vboxusers". And change 
```
from
	vboxusers:x:124:
to
	vboxusers:x:124:[YOUR-USER-NAME]
```

Then, in virtual box, make sure you have a filter that allows USB. Go to 'settings', 'USB', and add a filter. Either a specific device, or a filter that allows any/all USB devices.

Mine works fine after these simple changes.

---

### Post by s1baker on 2010-12-05
I have 2 files in the /etc directory. One is "group" and the other is "group-"
Should there be two files named group.?

---

### Post by s1baker on 2010-12-05
Also, under my user group setting I have VB as 125 instead as 124. Should it be 124

---

### Post by IkeLewis on 2010-12-05
I have both files in my /etc directory as well.. I assume it is normal... perhaps the group- is a backup copy.

---

### Post by Cpierce on 2010-12-05
Aeronutt is right. Go to system>Admin>users and groups. Then hit "manage groups" and scroll down to VBoxusers. Click on properties and then check your name.
also make sure you have the USB added in the "details" on your machine

---

### Post by wangsuda on 2010-12-05
On my machine (10.10 32 bit) the virtualbox user group is 125 WITH my user name checked. Additionally,  I checked my user name to make sure I have permissions with virtual box.

---

### Post by aeronutt on 2010-12-05
> **s1baker said:**
> Also, under my user group setting I have VB as 125 instead as 124. Should it be 124

I'm pretty sure you should not change that, leave as original. It's your group ID.

---

### Post by mcbeutler on 2010-12-05
Since this thread is already open, I thought I'd avoid opening another.  (have VB USB issue also, but different)

RE the original issue posted, did you go to System/Administration/Users and Groups/(your user)/Advanced Settings/User Privileges and check the box for "Use VirtualBox virtualization solution"?  This was part of my original problem when I was trying to set up VB for winXP.

I now have some USB function (wireless mouse), but still have greyed out box for the USB printer in VirtualBox and cannot get winXP to see the printer or HP WM6 palmtop device.  I have the Oracle version of VB (version 3.2.12 r68302 and Meerkat (fully updated).  Any suggestions would be wholly appreciated.

---

### Post by s1baker on 2010-12-05
My Ubuntu Usergroups has both vboxusers and lp groups selected.
My usergroup for vboxuser is 125 though.

Also in VB :
under Windows XP settings/USB I have "Enable USB Controller" checked and under that "Enable USB 2.0 (EHCI) Controller" checked.
In the "USB Device Filters" I have the SD USB Card Reader checked.

---

### Post by s1baker on 2010-12-05
Yes, I have System/Administration/Users and Groups/(your user)/Advanced Settings/User Privileges as checked.

---

### Post by s1baker on 2010-12-05
I have Bracero and I ran it and went to my SD card to copy a folder with all the files in it to my CD, but I can't see any place to select "copy" in Bracero so that I might burn it to my CD.

---

### Post by mercgt73 on 2010-12-11
After reading a bunch of threads, I still have not resolved my Virtualbox issue.  I just installed Vbox 3.2.8 on Ubuntu 10.10 to run 32bit XP.  I have created and added myself to the vboxusers group.  I added myself to the lp group.  I created and added myself to the usbfs group (another thread recommended this).  I double checked my group permissions in /etc/group.  I have also rebooted after my changes.  

What I DON'T have that this post talks about is the USB filter in Virtualbox->OS->Settings.  In settings for XP I have: General, System, Display, Storage, Audio, Network, Serial Ports and Shared Folders.  Any help is greatly appreciated!

-Rusty

---

### Post by migs73 on 2010-12-11
> **mercgt73 said:**
> After reading a bunch of threads, I still have not resolved my Virtualbox issue.  I just installed Vbox 3.2.8 on Ubuntu 10.10 to run 32bit XP.  I have created and added myself to the vboxusers group.  I added myself to the lp group.  I created and added myself to the usbfs group (another thread recommended this).  I double checked my group permissions in /etc/group.  I have also rebooted after my changes.  

What I DON'T have that this post talks about is the USB filter in Virtualbox->OS->Settings.  In settings for XP I have: General, System, Display, Storage, Audio, Network, Serial Ports and Shared Folders.  Any help is greatly appreciated!

-Rusty

Click on the word 'General' and it'll open another window, USB is listed in the left hand pane. Click on that and add a filter.

---

### Post by mercgt73 on 2010-12-11
> **migs73 said:**
> Click on the word 'General' and it'll open another window, USB is listed in the left hand pane. Click on that and add a filter.

USB is not listed, all that is shown is what I posted in the previous thread... ?

---

### Post by migs73 on 2010-12-11
> **mercgt73 said:**
> USB is not listed, all that is shown is what I posted in the previous thread... ?

Did you install the PUEL version from the Oracle website or the version in the Repos?

---

### Post by mercgt73 on 2010-12-11
> **migs73 said:**
> Did you install the PUEL version from the Oracle website or the version in the Repos?

I assume the repos, since I used Ubuntu Software Center.  Should I instead have installed the PUEL version?

---

### Post by migs73 on 2010-12-11
> **mercgt73 said:**
> I assume the repos, since I used Ubuntu Software Center.  Should I instead have installed the PUEL version?

Yes, there is no USB support in the OSE (repo) version. The PUEL version has a end user license and is not considered FOSS therefore doesn't get into the USC.

It is also at version 3.2.12 so has been updated a couple of times recently.

---

### Post by mercgt73 on 2010-12-11
> **migs73 said:**
> Yes, there is no USB support in the OSE (repo) version. The PUEL version has a end user license and is not considered FOSS therefore doesn't get into the USC.

It is also at version 3.2.12 so has been updated a couple of times recently.

Wow, in all the threads I read I did not catch that.  Thanks for your help!  I will get rid of repos VB and get the Oracle version.  I assume that when I uninstall repos VB it will free that image space for the XP guest?

---

### Post by CharlesA on 2010-12-11
Even if you purge virtualbox-ose, it'll keep your virtual machines around IIRC.

---

### Post by mercgt73 on 2010-12-11
> **CharlesA said:**
> Even if you purge virtualbox-ose, it'll keep your virtual machines around IIRC.

It sure did!  I dumped OSE and loaded Oracle's VB.  After a 30 minute hitch with dkms and a linking error, I was in business.  VB did not install cleanly for some reason, so I had to do a dkms un-install and re-install.  Then I had to do a ./vboxdrv.dpkg-dist setup to recompile the module.  Thanks again for the help!

---

### Post by CharlesA on 2010-12-11
> **mercgt73 said:**
> It sure did!  I dumped OSE and loaded Oracle's VB.  After a 30 minute hitch with dkms and a linking error, I was in business.  VB did not install cleanly for some reason, so I had to do a dkms un-install and re-install.  Then I had to do a ./vboxdrv.dpkg-dist setup to recompile the module.  Thanks again for the help!
Awesome. I know going from the ose version to plue can be a bit of a pain. Glad you got it working. :)

---

