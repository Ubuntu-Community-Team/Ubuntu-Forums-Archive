---
title: "System unusable due to graphics corruption"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by CrystalShadow on 2009-05-04
OK... So I installed Kubuntu 8.10 from a live CD into some free space left over from previous experiments with linux about a year ago.

Everything seemed fine, though I got a notice saying an upgrade to 9.04 was available. So... I installed that... 

Again everything seemed fine. Installed opera, then started installing a few other packages.

Now here is where it all went wrong though. Without intending to, I switched to a TTY console. A little fiddling about got me back to the X server, but moments later the system locked up.
Not knowing any better, I forced a hard reset.
When the system rebooted, the display was garbled, and nothing I've been able to find seems to fix it.

The option to 'automatically fix' graphics problems in the recovery system doesn't do anything.
Neither do any of the suggestions I've been able to find on this forum.

Whatever I do, the graphics output remains corrupted, and hence the Xserver is currently unusable.

I'm running this on a laptop using an ATI X1400 chip, and I know it was working fine up until the crash...

Any suggestions?

---

### Post by lavinog on 2009-05-05
did you have the proprietary driver installed?
What is the output of fglrxinfo?

---

### Post by CrystalShadow on 2009-05-05
I really don't know right now. I haven't been able to boot into linux at the moment.

I'll try to get the output fglrxinfo, though I have a hard time working out how to copy it, since I'm looking at these forums using windows on the same computer.

(How exactly can I get the output saved in such a way that I can view it in windows?)

---

### Post by lavinog on 2009-05-05
forget about fglrxinfo (kind of autopilot mode)
What I was meaning was did you have the restricted drivers installed prior to the upgrade?

either way try this from the command line:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
this will rename your xorg.conf file to a different name.
If your xorg.conf is referring to the old ati driver, you will have problems in jaunty.
if you reboot, xorg should boot into mesa giving back your desktop.
if it doesn't and you want to put your xorg.conf file back use:
```
sudo mv /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

---

### Post by CrystalShadow on 2009-05-05
Thanks. I'll try it and see where it leads.

I don't think I had the proprietary drivers installed prior to the upgrade (both 8.10 and 9.04 worked initially.), but it's possible I might have installed them just before the system crashed.

I'll let you know what happened when I try this out.

Thanks in advance.

---

### Post by CrystalShadow on 2009-05-05
Thanks for the Help.

It wasn't the solution, but along with some other stuff, it did point me in the right direction.

Basically, I used aptitude to remove the Proprietary ATI drivers. Now it works again.

---

### Post by lavinog on 2009-05-05
Glad you were able to fix it.
I wonder if the issue you had was because of upgrading instead of a clean install?
The new ATI driver (9-5) should be out in 2-3 weeks, you might want to wait until then to install.
A good site for instructions on manually installing the driver can be found here:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
Or you can use envy to handle the install for you.
```
sudo apt-get install envyng-gtk
```

---

### Post by lavinog on 2009-05-06
The following cards are no longer supported by the proprietary driver:
```

ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
ATI Radeon X700 Series
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series 

```
I don't see X1400 on the list, but it seems like it should be since the X1200, X1300 X1550, X1600 all are

---

### Post by b6of12 on 2009-05-06
I think the x1400 is a custom edition or mobile edition so ya it on there its just hiding
I had the same props on x1250 I just went back to ubuntu 8.10 every thing is cool now

---

