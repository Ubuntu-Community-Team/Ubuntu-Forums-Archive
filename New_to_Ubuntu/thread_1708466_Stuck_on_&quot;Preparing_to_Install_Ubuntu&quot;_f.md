---
title: "Stuck on &quot;Preparing to Install Ubuntu&quot; for several minutes"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by liist on 2011-03-16
Hello everyone.

I am currently running a Ubuntu boot disk because Windows bootup has corrupted, and I don't yet have the Windows 7 recovery disk. I am currently running a Lenovo ThinkPad T410i.

Right now, I am in the process of installing Ubuntu, but I've been stuck on this screen for about 10 minutes. I tried installing it yesterday before I ran out of time, and again, I have not gotten past the screen that states "Preparing to install Ubuntu." I have at least 2.6GB of free space, plugged into a power source, and I am connected the internet.

---

### Post by ubudog on 2011-03-16
Welcome!

I don't know if I can offer much help, but maybe...

Is there anything that says "More details", or something similar?  If so,  click on that and post the output here.  Strange.  You also may want to try an "alternate" CD.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by liist on 2011-03-16
Nope. The installation never goes past the preparation point, and there is no way to display an output of what's going on.

The only options I have are "Download updates while installing" and "Install this Third Party Software."

It seems like I'm not beginning the installation process at all, while the thing never goes past this stage. Also, it looks like I can quit any time I want to no ill effect.

Edit: I'm not sure about the alternate disk. I don't have the required resources with me at the moment, and it seems like my current disk is running fine, at least with the boot from CD version of Ubuntu. I did install it on a DVD, so I'm not sure if that would affect the installation at all.

---

### Post by hotrod6657 on 2011-03-16
have you tried the utility to check the live CD for errors?

---

### Post by liist on 2011-03-16
No I haven't. How would I go about doing that. What are some resources that I should look up that would help me with these issues?

---

### Post by hotrod6657 on 2011-03-16
I believe there is an option to check the disk before booting in to the live CD.  At least there used to be.

That should check the disk for defects and at least rule that out as a cause of the problem.

---

### Post by liist on 2011-03-16
Is having a messed up CD a common issue? I remember when the guy who put Ubuntu in my computer to test if my hard drive didn't die (it didn't), the first CD couldn't boot up. It seems this CD works perfectly fine, it boots up OK and the little stuff I messed with seems fine.

I'll go and check it again, but I have some stuff I have to do before I power off my computer.

---

### Post by ubudog on 2011-03-16
I found this thread, may be of some help: [http://ubuntuforums.org/showthread.php?t=1598461](http://ubuntuforums.org/showthread.php?t=1598461)

If you don't have anything you really need from Windows, you may want to completely wipe the drive with Gparted, then retry the install.  No guarantee though, but it may work.  I really wish I could be of more help.

---

### Post by hotrod6657 on 2011-03-16
> **liist said:**
> Is having a messed up CD a common issue? I remember when the guy who put Ubuntu in my computer to test if my hard drive didn't die (it didn't), the first CD couldn't boot up. It seems this CD works perfectly fine, it boots up OK and the little stuff I messed with seems fine.

I'll go and check it again, but I have some stuff I have to do before I power off my computer.

I've found a messed up Cd to be pretty common.  Not that the iso image was bad, but that it was a bad burn.  Likely a sideffect of my buying really cheap cds, a really cheap cd drive, and usually forgetting to dial back the burn speed.

---

### Post by ubudog on 2011-03-16
> **hotrod6657 said:**
> I've found a messed up Cd to be pretty common.  Not that the iso image was bad, but that it was a bad burn.  Likely a sideffect of my buying really cheap cds, a really cheap cd drive, and usually forgetting to dial back the burn speed.

Yep, I've had many issues with too high burn speed.  Very annoying little issue.  You could try re-burning I suppose, using a lower burn speed.  It's worth the try, so that we get all the little things out of the way, so that we don't do a bunch of work just to find that it was just this little tiny thing.

---

### Post by Rex Bouwense on 2011-03-16
Did you mean to say that you are trying to install Ubuntu on a 2.6 Gig partition?  I don't think that is enough space for a full install.  Does everything work when you try Ubuntu with the live CD?
See [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by ubudog on 2011-03-16
> **Rex Bouwense said:**
> Did you mean to say that you are trying to install Ubuntu on a 2.6 Gig partition?  I don't think that is enough space for a full install.  Does everything work when you try Ubuntu with the live CD?
See [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I believe he is saying that he has checked off the small list of requirements on the installer (Power Source, Internet Connection, 2.6 GiB of space).

---

### Post by CavalryJim on 2011-03-29
I had the same problem installing Ubuntu 10.10 - 64bit on a Dell Optiplex 740.  It would hang on the Preparing to Install... screen when trying to install via a USB thumb drive so I burned to a CD and the same thing happened again (and again and again).  I unplugged all unnecessary devices (external hard drive, printer, etc.) and it finally worked!

---

### Post by cmcanulty on 2011-03-29
Try 2 things try a flash disk to install or try run and not install then when you get to the desktop click on the install option. Both worked for me on balky machines.

---

