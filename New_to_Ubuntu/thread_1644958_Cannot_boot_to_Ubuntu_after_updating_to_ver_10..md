---
title: "Cannot boot to Ubuntu after updating to ver 10."
date: 2010-12-13
forum: New to Ubuntu
---

### Post by BGTex on 2010-12-13
I cannot boot to Ubuntu after updating to ver 10.
I am using a dual boot Vista system, I installed Ubuntu 9 and was having not problem for months. Then I updated from within Ubuntu to ver 10 from the update manager. Now when I get to the boot screen and choose Ubuntu the PC restarts and goes back to the boot screen.

Vista boots fine but Ubuntu will not start.
Any help would be appreciated. 
I am a novice to Ubuntu, but have plenty of experience with PCs and Windows, I have built over a dozen computers from scratch and can format and partition hard drive and use the dos prompt.

---

### Post by amjjawad on 2010-12-13
Hello and welcome :)

Please, follow the instruction on this link: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please, post back the result here and wrap up the text with "#" or "CODE" tags.

Thank you!

---

### Post by CharlesA on 2010-12-13
What happens if you choose recovery mode?

---

### Post by BGTex on 2010-12-13
Recovery mode? Do you mean from Windows?
When I re-start the PC, after POST I get to the screen to choose Vista or Ubuntu.

---

### Post by lisati on 2010-12-14
> **BGTex said:**
> Recovery mode? Do you mean from Windows?
When I re-start the PC, after POST I get to the screen to choose Vista or Ubuntu.

If you did a normal dual-boot install of Ubuntu, there should be an Ubuntu recovery mode listed. By any chance did you use Wubi to install Ubuntu?

---

### Post by BGTex on 2010-12-14
> **amjjawad said:**
> Hello and welcome :)

Please, follow the instruction on this link: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please, post back the result here and wrap up the text with "#" or "CODE" tags.

Thank you!
Can I run "boot info script" from a Windows command prompt?

---

### Post by lisati on 2010-12-14
> **BGTex said:**
> Can I run "boot info script" from a Windows command prompt?

It's probably easier to run it from a "Live CD"/installation CD

---

### Post by amjjawad on 2010-12-14
> **BGTex said:**
> Can I run "boot info script" from a Windows command prompt?

It's a Linux Script, you need Linux LiveCD. Don't you have Ubuntu's LiveCD or LiveUSB?

---

### Post by BGTex on 2010-12-14
> **lisati said:**
> If you did a normal dual-boot install of Ubuntu, there should be an Ubuntu recovery mode listed. By any chance did you use Wubi to install Ubuntu?
Don't know if I used Wubi, but before updating to ver 10 I did have four choices to boot to one may have been Recovery mode.
I did my original install from within Vista.

---

### Post by BGTex on 2010-12-14
> **amjjawad said:**
> It's a Linux Script, you need Linux LiveCD. Don't you have Ubuntu's LiveCD or LiveUSB?
No I don't have LiveCd or LiveUSB, sound like that is where I should start.
I'm sure I can find out how to get them in this forum.

---

### Post by amjjawad on 2010-12-14
> **BGTex said:**
> No I don't have LiveCd or LiveUSB, sound like that is where I should start.
I'm sure I can find out how to get them in this forum.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Read everything in that link.

---

### Post by BGTex on 2010-12-14
Thank you amjjawad, I will give it a try and post my results.
 
Thanks everyone; I can't belive the quick and helpful replies. I think I'm going to enjoy this.

---

### Post by amjjawad on 2010-12-14
> **BGTex said:**
> I think I'm going to enjoy this.

Trust me, you'll ;)

Don't thank me, I'll be very glad if you'll manage to fix your problem :D

---

### Post by Rubi1200 on 2010-12-14
Hi and welcome to the forums :)

This does sound as if it might be a Wubi install as all the symptoms you describe indicate as such.

However, to make sure, let's play it safe.

Download and burn to CD the image as amjjawad already suggested.

Then, boot the computer choosing to try not install Ubuntu.

You may need to set BIOS to boot from the CD drive beforehand.

Run the script also suggested above and we can help you sort this out.

Thanks.

---

### Post by Dutch70 on 2010-12-14
> **BGTex said:**
> Don't know if I used Wubi, but before updating to ver 10 I did have four choices to boot to one may have been Recovery mode.
**I did my original install from within Vista.**

I'm think that tells the tale. 

Can he not just back up his files & uninstall Ubuntu from within vista & reinstall the version he wants? Just trying to help and learn myself. I have another vista pc with Ubuntu installed via wubi, but just put it on there a few weeks ago.

---

### Post by Rubi1200 on 2010-12-14
> **Dutch70 said:**
> I'm think that tells the tale. 

Can he not just back up his files & uninstall Ubuntu from within vista & reinstall the version he wants? Just trying to help and learn myself. I have another vista pc with Ubuntu installed via wubi, but just put it on there a few weeks ago.
Of course it is possible to do that. However, I usually try and see if it is possible to fix the problem before doing what you suggest because users don't just save stuff, they also have certain settings they like etc. which can be time-consuming to set up again. Just my opinion, though.

---

### Post by waynefoutz on 2010-12-14
if you want to fix the problem, get rid of the Wubi install and put Ubuntu on a real partition. Wubi was never meant to be a permanent way to install, it's meant try out Ubuntu without making permanent changes to your hard drive. Saving data on a loop mounted phony drive is NOT a good idea. The drive your Wubi install is on is not a drive at all, it's one huge file. If that file gets corrupted, which a good Windows crash or a power failure while Wubi Ubuntu is running will do, then your Ubuntu install is GONE. 

From Wikipedia:


[http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)]("http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)")

> Limitations

Compared with a regular installation, a Wubi installation faces some limitations. Hibernation is not supported and the filesystem is more vulnerable to hard reboots[1]. Also, if the Windows drive is unmounted uncleanly (most commonly because of a Windows crash), Ubuntu will not be able to mount the Windows drive and boot until Windows has successfully booted and shut down. If the Windows system cannot be booted after the crash, the user also cannot boot Ubuntu.
Performance related to hard-disk access is also slightly slower, more so if the disk image file is fragmented, on a Wubi install compared to a normal one.

What I would do:
go into Windows add/remove programs and get rid of Ubuntu. Then take an Ubuntu disk and BOOT from it. Follow the prompts. If it detects Windows, it will set up a dual boot system for you.

---

### Post by BGTex on 2010-12-14
> **waynefoutz said:**
> if you want to fix the problem, get rid of the Wubi install and put Ubuntu on a real partition. Wubi was never meant to be a permanent way to install, it's meant try out Ubuntu without making permanent changes to your hard drive. Saving data on a loop mounted phony drive is NOT a good idea. The drive your Wubi install is on is not a drive at all, it's one huge file. If that file gets corrupted, which a good Windows crash or a power failure while Wubi Ubuntu is running will do, then your Ubuntu install is GONE. 

From Wikipedia:


[http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)]("http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)")



What I would do:
go into Windows add/remove programs and get rid of Ubuntu. Then take an Ubuntu disk and BOOT from it. Follow the prompts. If it detects Windows, it will set up a dual boot system for you.
I do have Ubuntu listed in my Add/Remove a program list in Vista.
I did make a Ubuntu 10.10 ISO DVD.
But I don't know if I should run the Boot Info Script or try to Un-Install Ubuntu from Vista.
What choice is better?

---

### Post by Hippytaff on 2010-12-14
Looks like you have a Wubi install. You can either uninstall it and then do a 'real' partition, or try the wubi fixes by Rubi1200 here - [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

It's up to you :-)

---

### Post by bcbc on 2010-12-15
> **BGTex said:**
> I do have Ubuntu listed in my Add/Remove a program list in Vista.
I did make a Ubuntu 10.10 ISO DVD.
But I don't know if I should run the Boot Info Script or try to Un-Install Ubuntu from Vista.
What choice is better?

Uninstalling Ubuntu will delete Ubuntu from your computer including any data/programs/settings you have installed while using Wubi.
Running the bootinfoscript is only useful if you would like help to fix the problem.

Since you have been using ubuntu since version 9.xx I'd say you probably don't want to just uninstall it. Rubi1200 has created the Wubi megathread that clearly spells out how to fix your current problem. It also contains other important info like how to migrate your Wubi to a traditional partition install, if you want do that. There's also a link to allow you to recover important data from your Wubi install from Windows.

As Hippytaff said, it's up to you...

---

