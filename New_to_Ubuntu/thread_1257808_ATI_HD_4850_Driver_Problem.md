---
title: "ATI HD 4850 Driver Problem"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by Heero_Yuy_X on 2009-09-04
Hi, I'm a user migrating from Windows to Ubuntu, I own an ATI HD4850 Graphics Card and I recently downloaded the latest version 9.04 jaunty and bought a kingston 8gb pen drive to try it out. Used this guide [http://www.pendrivelinux.com/usb-kubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-kubuntu-904-persistent-install-windows/) to install it and the 3gb casper loop file... Everything seems normal up to now... 

I tried to install the ATI Driver from the Hardware manager in the System Menu and restarted. Just after the Ubuntu loading screen the colours crash, I tired another reboot to find some errors and some console in the end of it :confused:

I also tried Kubuntu 9.04, downloaded the driver from ati.com and used the installation guide at the site to install it, after restarting KWin becomes unstable, and the keyboard doesn't type into anything in the whole OS.. :(

I've tried both at least 3 times each with the same result, I did some research and it seems there are similar problems with ATI 4850, most get it working alright and failing after installing Compiz or something else... but I can't even get Ubuntu running !!! :(

Any help would be appreciated... :(

---

### Post by xir_ on 2009-09-04
What driver version have you installed? There was recently a catalyst update which fixed a lot of jaunty issues (the driver didnt work with the new xorg properly)

try installing envy and use that to get you going (might just tide you over), be warned these are not the bleeding edge drivers.

```

sudo apt-get install envyng*

```and then from there it offers automagic installation options

---

### Post by Heero_Yuy_X on 2009-09-04
I'll try that thanks for the fast reply ;)

Can I enable the desktop effects and open 3D Applications normal?

and btw, what's bleeding edge ? :)

Edit : Forgot to mention the driver version... When I tried installing the driver on Kubuntu I tried the 9.8 Catalyst version, On Ubuntu I dun actually know, I just clicked the Activate Hardware button in the Hardware Manager, and it just started to download and install the drivers on its own, then told me to restart...

---

### Post by xir_ on 2009-09-04
bleeding edge is the latest release, normally has all the new fun toys, but has a habit of getting you cut. Because the envy drivers are not the newest they can have problems, but one step at a time.

Using envyng to install your drivers you should be able to enable desktop effects. if this doesn't work then it might be the driver version.

There have been some improvements since then. 

The latest drivers are [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

but id suggest doing an envy install before going here.


BTW we can fix the system to boot with the opensource drivers if you just want it to get up and running (but no real eye-candy).



can you post the output of ```
 uname -a 
```

---

### Post by Heero_Yuy_X on 2009-09-04
I just made another fresh install of Ubuntu, and I'm installing envyng* right now...
I'll post after I restart :)

Output of uname -a :

Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Thanks again for your help ;)

---

### Post by hockeytux on 2009-09-04
> **Heero_Yuy_X said:**
> Hi, I'm a user migrating from Windows to Ubuntu, I own an ATI HD4850 Graphics Card and I recently downloaded the latest version 9.04 jaunty and bought a kingston 8gb pen drive to try it out. Used this guide [http://www.pendrivelinux.com/usb-kubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-kubuntu-904-persistent-install-windows/) to install it and the 3gb casper loop file... Everything seems normal up to now... 

I tried to install the ATI Driver from the Hardware manager in the System Menu and restarted. Just after the Ubuntu loading screen the colours crash, I tired another reboot to find some errors and some console in the end of it :confused:

I also tried Kubuntu 9.04, downloaded the driver from ati.com and used the installation guide at the site to install it, after restarting KWin becomes unstable, and the keyboard doesn't type into anything in the whole OS.. :(

I've tried both at least 3 times each with the same result, I did some research and it seems there are similar problems with ATI 4850, most get it working alright and failing after installing Compiz or something else... but I can't even get Ubuntu running !!! :(

Any help would be appreciated... :(


You mean your screen now looks something like this?:

[http://ubuntuforums.org/showthread.php?t=1156640](http://ubuntuforums.org/showthread.php?t=1156640)

The solution of how you delete the 'bad' drivers is there as well.

---

### Post by Heero_Yuy_X on 2009-09-04
ITS EXACTLY LIKE ITTTT !!!! :D
I'll check it out ASAP 

Thanks alot !!!

Edit : I checked out the forum you mentioned, they seem to have removed the drivers and got back to square one, it still doesn't solve the problem of installing the driver. I'm still downloading Envy though, I'll post when I can..

---

### Post by Heero_Yuy_X on 2009-09-04
Same scenario as installing from the Hardware manager.. The screen crashes just like hockeytux mentioned...

I tried pressing ctrl + F8 and ctrl + F9 or anything that could possibly get me to a terminal or sth but to no vail...

Any ideas on how to fix this ? :cry:

Could the problem be that the install is on a flash drive?

---

### Post by xir_ on 2009-09-04
> **Heero_Yuy_X said:**
> Same scenario as installing from the Hardware manager.. The screen crashes just like hockeytux mentioned...

I tried pressing ctrl + F8 and ctrl + F9 or anything that could possibly get me to a terminal or sth but to no vail...

Any ideas on how to fix this ? :cry:

Could the problem be that the install is on a flash drive?

Try this driver [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English ]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English")(im assume you want to carry on with the binary route). This is the latest and greatest and may work better.

otherwise i can try and help you get you opensource drivers restored.

im not sure if the pen drive could cause this as a problem.


edit theres a guide here that i forgot about
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Alternatives](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Alternatives)

---

### Post by remymarathe on 2009-09-04
> **Heero_Yuy_X said:**
> Same scenario as installing from the Hardware manager.. The screen crashes just like hockeytux mentioned...

I tried pressing ctrl + F8 and ctrl + F9 or anything that could possibly get me to a terminal or sth but to no vail...

Any ideas on how to fix this ? :cry:

Could the problem be that the install is on a flash drive?

I ran into the same problems as you after installing ATI's fglrx drivers for my HD 4200 via the "restricted drivers" menu.  After restoring my access to gnome by gouging out fglrx in a way similar to that linked above, I had success with the method described here under "Installing the drivers manually":
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Alternatives](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Alternatives) 

If I get time I'd like to try and figure out what makes the two methods different, my current suspect is the line under step 7 where you force fglrx to use xorg.conf.  It's just a hunch right now, because when I was getting crashes after the automated ATI install there was nothing I could do to xorg.conf to change which driver got loaded; froze regardless and the rescue mode's automatic graphics fix didn't work, probably for the same reason.

---

### Post by hockeytux on 2009-09-04
I wouldnt actually mess with ATI drivers at all. They just not that well supported yet...

---

### Post by Heero_Yuy_X on 2009-09-04
xir_, I used this one in kubuntu 9.04 and failed ( KWin got unstable ), I'll try it out in Ubuntu though, using the manual install method... 

I'm starting to think this is something got to do with the flash drive while mounting or sth... 

I really hope this one works !!!

Edit : Remymarthe I think the forcing driver thingy might be the problem as u said, I saw it in a search or sth I dun remember, the default driver and the ATI driver may conflict... anyways I'll try again and post my findings...

---

### Post by Heero_Yuy_X on 2009-09-04
First of all, I would like to thank you all for your helpful and fast replies, without you guys I wouldn't have got this far.. :KS

I've got good news and bad news...

Good news is Ubuntu loads normal finally !!!!! :)

Bad news is when trying to enable the desktop effects, I get the "Can't enable desktop effects" message...

I checked with the hardware manager, and it seems the driver is not recognized or sth...

So I clicked the activate hardware button, it kept searching for avaliable drivers, then recommended a restart, I restarted, came back to the hardware manager, to find that its still not recognized, and its the same way I left it before the restart... :(

Can anyone explain all this ? :(

Edit : There wasn't a success at all !!!! I just remembered typing the "fglrxinfo" command to confirm the driver installation and it wasn't installed correctly !!!! I don't know how though I followed each step carefully :(
The output from fglrx info : 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

Does anybody have any idea what this is?

---

### Post by Heero_Yuy_X on 2009-09-05
I just tried it again with a fresh install and following each step in the manual install method carefully and still this same damn message !!!!! :(

I've been searching for what it means or how people solved it, but it seems whoever solves it just marks his thread as solved and doesn't post a solution !!! :(

Can anybody help, because I'm already starting to feel that Windows wasn't such a bad idea after all :(

---

### Post by hockeytux on 2009-09-05
What exactly did you delete? Just the ccc package (Catalyst Control Centre) and fglrx?

You may have deleted more than just the files that you installed...

---

### Post by Heero_Yuy_X on 2009-09-05
No!!! I didn't delete anything :D

I only formatted my USB Drive and reinstalled Ubuntu 9.04, and used the manual install method in [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

However, when I type to "fglrxinfo" in the console to verify the driver's installion as said in the guide, I find this damn error message mention above...

And just now, I found that the xorg.conf file doesn't get edited !!!!! I found that what I edit is backuped only !!! This probably why fglrxinfo states the error :(

Here are some screenshots to explain...

Somehow after reboot, xorg.conf miraclously gets reset :confused:

Of course, I have used "sudo gedit /etc/X11/xorg.conf" to edit it, just as mentioned in the guide and made sure I have saved the file. But after reboot it resets back :(

Any way to overcome this?

I'll try to restore the backups and reboot again, but I'm open to any suggestions..:(

Edit : I can't seem to rename the files in the file browser, it seems I have to be the superuser, how do I rename the files in the console?
Edit : I used Save as to save the backup as "xorg.conf", however after restart it restores back to default :(

---

### Post by Heero_Yuy_X on 2009-09-05
anybody???

---

### Post by Heero_Yuy_X on 2009-09-05
I FOUND ITTT !!!! FINALLLYYY !!!!!!:guitar:

The problem was this was a godamn pendrive installation in the first place !!!! :P

I Shrunk my Hardrive a bit and installed a full Ubuntu installion, used the manual method again to install the driver and voilaaa !!!! :D

Thanks Everyone for your support :D

And for anyone facing this, DON'T INSTALL DRIVERS ON A UBUNTU PEN DRIVE INSTALLATION !!! :D

Marking this thread as solved...

---

