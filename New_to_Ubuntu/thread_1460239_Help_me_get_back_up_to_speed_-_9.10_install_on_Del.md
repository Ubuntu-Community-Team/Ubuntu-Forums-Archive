---
title: "Help me get back up to speed - 9.10 install on Dell Poweredge 2950"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by yah.shoor on 2010-04-22
[FONT=Arial][SIZE=2]Howdy folks, 

I'm not an absolute beginner... but I haven't installed Linux on anything at all since OS X 10.2 came out. So, I'm really rusty, and pretty much everything has changed in the intervening years. 

I'm going to try to install 9.10 Karmic Koala, on a Dell Poweredge 2950. I agreed to try the install some time back, and this is the machine that I have available, and my investigation leads me to believe that I'm walking into a major snafu. There are lots of posts about this on these forums:

[/SIZE][/FONT]    [FONT=Arial][SIZE=2][COLOR=#1f497d][http://georgia.ubuntuforums.org/showthread.php?t=1444037&highlight=2950+sas](http://georgia.ubuntuforums.org/showthread.php?t=1444037&highlight=2950+sas)[/COLOR][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][COLOR=#1f497d][http://georgia.ubuntuforums.org/showthread.php?t=1367857&highlight=2950+sas](http://georgia.ubuntuforums.org/showthread.php?t=1367857&highlight=2950+sas)[/COLOR][/SIZE][/FONT]
  [FONT=Arial][SIZE=2]
and they're all discouraging. The machine certainly has the SAS 6I/R controller that may be an LSI controller inside, and there are plenty of posts saying "Why doesn't this work?" and no posts saying "Install umpty-ump driver at the bootprompt." However, most of the posts are about older releases, and I would have assumed that an issue like this would have been resolved. However, some of the old posts I've found where solutions were mentioned, using a 2.4 kernel wound up being the final advice. And, without really specific noob-guidance, it might take me days and days to piece together exactly what I should do at the bootprompt. 

Should I try posting about this in the Dell-specific forum? Or are my serial-attached SCSI concerns groundless noob fears? Advice pls.
[/SIZE][/FONT]

---

### Post by 2hot6ft2 on 2010-04-22
Welcome and it's been a while since the 2.4 kernel. A lot has changed since then.
With it only being a few days until the release of 10.04 I would either install the rc for it or wait for the regular release of it.

I don't know any specific answers on your hardware.

---

### Post by MooPi on 2010-04-22
Sounds as if you have more than one computer. If so then the risk of experimenting on your Dell shouldn't be that great a risk. I say jump in and solve issues if and when they appear. If you already know that your computer may have a certain problem your miles ahead before you start. Have fun and jump head first into the deep end.

---

### Post by Sentinel83 on 2010-04-22
My recommendation would be to run the 9.10 live CD and check the logs for those types of errors with dmesg before buckling down and installing the OS.  

I think you can run something similar to ```
dmesg | grep 'error'
``` where the error is what is found in the other threads.  Someone please jump in and correct if that syntax is wrong.

Hope that helps!

---

### Post by yah.shoor on 2010-04-22
> **2hot6ft2 said:**
> With it only being a few days until the release of 10.04 I would either install the rc for it or wait for the regular release of it.
Nope, I'm at work (in what has been a strict MS shop, for years) getting a server ready for a database product, and if the db vendor says "Use Karmic Koala" I most certainly do not upgrade to the latest, even if it is the latest stable long-term support release.

 > My recommendation would be to run the 9.10 live CD and check the logs  for those types of errors with dmesg before buckling down and installing  the OS.
Good idea... it looks like the live CD is a desktop version, not a server version, but it's still worth a shot.

---

### Post by Sentinel83 on 2010-04-22
Ah, right, good point.  Wasn't thinking server version even though you mentioned a poweredge.

Hopefully the hardware detection is similar in the server version compared to the desktop version.  The server version should have more advanced RAID and hard drive capabilities...either way you can still check the logs for errors once it's installed.

---

### Post by tgalati4 on 2010-04-22
Well, you could use the 32-bit server version if the 64-bit version is not working.  If you don't really need RAID, perhaps you can bypass it by connecting the drives directly to the SATA ports.  You can also use software RAID to completely bypass the SAS controller, but then you give up some performance and battery-powered cache dumping.  

Otherwise, look at Centos or even BSD to run the server.  Depending on what applications you want to run, they are probably available for several linux/unix distros.

---

### Post by yah.shoor on 2010-04-22
> **Sentinel83 said:**
> Hopefully the hardware detection is similar in the server version compared to the desktop version.  The server version should have more advanced RAID and hard drive capabilities...either way you can still check the logs for errors once it's installed.
Yeah, and it's the RAID controller that comes up in my searches as a potential issue. The BIOS of the RAID controller (Dell SAS 6 I/R) is set up for RAID 0, and some of the posts I've found (quoted in my OP) mention that it just loses the drives entirely, usually after finishing the install and restarting. 

My hunch is that I should take this question over to the Dell forum here:

"I can't see any evidence that the Dell SAS 6 I/R controller works in Ubuntu Server 9.10 x64. Can anyone confirm/deny?"

but I don't even know if that question has enough information.

---

### Post by yah.shoor on 2010-04-22
> **tgalati4 said:**
> Otherwise, look at Centos or even BSD to run the server.  Depending on what applications you want to run, they are probably available for several linux/unix distros.
Nah, I think that even software RAID is better than switching distros, once I've already picked one that supports the db in question (therefore not BSD), and for which I can buy a support contract (therefore not CentOS) after I'm already installed and up and running (therefore not RHEL). I really would have been happy with a BSD; my first Unix experience was

32-bit might be okay for me, while I dig away at the driver issue. There won't be many people using this server at first anyways, so I think that the performance hit and memory limitations won't be a problem at all.

---

### Post by tgalati4 on 2010-04-22
I bet the SAS raid controller works under RHEL.

---

### Post by yah.shoor on 2010-04-22
> **tgalati4 said:**
> I bet the SAS raid controller works under RHEL.
I bet it does too :(

---

### Post by yah.shoor on 2010-04-23
Well, the hard-drive controller part of my install went off without a hitch. I managed to partition the drive, install, and made it to a command prompt. Hooray! And, by the way, I can't believe how much easier this is than it was back in the day. I'm in love with aptitude. 

I still have lingering questions; is this a good place to ask 'em? Seeing as I'm still technically an absolute beginner. I installed the OpenSSH task package, which looked like it went fine (going to check it from home later today, whoo-hoo!). Then I installed the ubuntu-desktop package. I had thought that if I didn't start gdm, then I would have rebooted to the command line. Instead, it throws me directly into Gnome upon reboot. At no point did I personally start gdm, and I can't figure out where it's hiding to start x without me actually typing "startx." Uh, what should I do?

---

