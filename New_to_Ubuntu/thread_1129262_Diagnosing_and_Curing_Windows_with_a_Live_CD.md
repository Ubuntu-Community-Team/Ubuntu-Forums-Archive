---
title: "Diagnosing and Curing Windows with a Live CD"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by DnDer on 2009-04-18
I know, or have heard, that you can run Linux CLI tools to help cure issues with the OS you have actually installed on your hard drive (many years ago, I was told that was pretty much the sole purpose of knoppix). I've never needed that ability till now.

I have a friend whose computer is dying. The only way they can access apps is through task manager and control panel. I'm having them make an ubuntu live cd before it dies for two reasons: to simply have an OS and keep working on the net, and to hopefully use some of the tools remotely to diagnose and cure their computer.

What tools should I be looking for using apt get? (Ubuntu uses that, right? Not some other package manager?) Could anyone offer me a place to start, so I can help my friend?

---

### Post by eeeandrew on 2009-04-18
that sounds like a pretty dead windows install. Have you got the reinstall disk for windows? I would use the liveCD to backup the data from windows. that is, boot into liveCD, plug in a flash stick and back any important data up onto the flash stick. Then reinstall windows. You could also try ubuntu if you can't reinstall windows.

Ubuntu does use apt-get or optionally dkpg (which I've never personally used).

Hope this helps,
Andrew

---

### Post by Alterax on 2009-04-18
I concur.  The problem with Windows (in this particular case) would be that of faulty shell extensions and corruptions in the registry.  It may be due to viral/malware activity, and the best fix for these that would still maintain Windows would be the Windows installation CD.  Boot it as if you were doing a fresh install, then when it detects an already-existing installation, use the repair option to replace the system files and registry options.

Usually Linux LiveCDs come in handiest when it comes to data recovery--such as the system will not boot, but you need to grab the existing user data from it, scan it for viruses (using ClamAV), and put it on another storage medium so that you can re-install without losing the data.  But to make a long story short, we don't (and legally cannot) develop programs to reinstall Windows system files and registry keys because it would be illegal under Microsoft's licensing terms.

This isn't a fault of Ubuntu, or of the GNU/Linux projects at all; it's due completely to Microsoft's licensing requirements and the proprietary/secretive nature of its code (not to mention their practices of being lawsuit-happy about any supposed infringement of their patents while happily exterminating competing products).  

You might do well to explain this to your friend; the fact that Microsoft doesn't want anyone BUT them to help improve and maintain their operating system is a good reason to consider switching to Free Software--then the community's hands are not tied when it comes to helping the end user.

--Alterax

---

### Post by cariboo on 2009-04-18
If you have an XP install disk, I would suggest you have a look at [BartPE]("http://www.nu2.nu/pebuilder/"). It is a live XP environment, with tools that can be used to repair a broken XP installation. 

The problems you described seem to warrant a complete reinstall.

Jim

---

### Post by DnDer on 2009-04-18
> **Alterax said:**
> Usually Linux LiveCDs come in handiest when it comes to data recovery--such as the system will not boot, but you need to grab the existing user data from it, scan it for viruses (using ClamAV), and put it on another storage medium so that you can re-install without losing the data.

I didn't know about ClamAV previously. This will help out *immensely* to have an AV tool that works. (My friend, because of these problems + shoddy connection speed could not get Avira or Comodo - my preferred pair of Windows protectorates.)

Also, Cariboo, thanks for the tip on BartPE. I'm going to go fish for this now.

---

### Post by L Campbell on 2009-04-19
> **DnDer said:**
> I know, or have heard, that you can run Linux CLI tools to help cure issues with the OS you have actually installed on your hard drive (many years ago, I was told that was pretty much the sole purpose of knoppix). I've never needed that ability till now.

I have a friend whose computer is dying. The only way they can access apps is through task manager and control panel. I'm having them make an ubuntu live cd before it dies for two reasons: to simply have an OS and keep working on the net, and to hopefully use some of the tools remotely to diagnose and cure their computer.

What tools should I be looking for using apt get? (Ubuntu uses that, right? Not some other package manager?) Could anyone offer me a place to start, so I can help my friend?

I have often 'wondered' about knoppix and your post inspired me to check it out.

Here is some stuff that you might find interesting:-

[http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1111316,00.html](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1111316,00.html)

[http://lss.wisc.edu/~sara/?q=node/16](http://lss.wisc.edu/~sara/?q=node/16)

[http://press.oreilly.com/pub/pr/1260](http://press.oreilly.com/pub/pr/1260)

[http://www.troubleshooters.com/linux/knoppix/index.htm](http://www.troubleshooters.com/linux/knoppix/index.htm)

[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

[http://www.knoppix-std.org/](http://www.knoppix-std.org/)

[http://www.grape-info.com/doc/win2000srv/security/ntpasswd.html](http://www.grape-info.com/doc/win2000srv/security/ntpasswd.html)

---

