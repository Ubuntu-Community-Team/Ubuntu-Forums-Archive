---
title: "&quot;|&quot; keys not working via Windows Remote Desktop"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by geohei on 2011-06-23
Hi.

I use 10.04 server in a VM (VMware 7.1.2) running WinXP(1). When I connect to this WinXP(1) from another WinXP(2) box using Windows Remote Desktop, I can't enter the pipe character "|" (Ubuntu ignores the key).

In other words, I connect from WinXP(2) using Windows Remote Desktop to WinXP(1), where Ubuntu runs as guest in a VMware environment.

I'm not sure whether this is Ubuntu related or VMware related, but in the VMware forums, nobody was able to help.

Also ... all other keys (even special keys like ö, ä, ü, ß) seem to work fine. Only the "|" key seems to be affected.

If Ubuntu Server or Desktop doesn't matter. "|" never shows up on both Ubuntu versions.

"|" is shown properly on WinXP(1) when typing on WinXP(2), so the Windows Remote Desktop seems to map the Characters properly.

If I don't use the Remote Desktop to connect to WinXP(1) but the attached keyboard, "|" works fine on Ubuntu.

It seems to be the combination of Remote Desktop and Ubuntu running as guest on WinXP(1) which generates this issue.

Any ideas?

Thanks!

---

### Post by geohei on 2011-06-24
Hi.

Does nobody know this, or was the question not clear (shall I rephrase)?

Thanks,

---

### Post by crispy_420 on 2011-06-24
I'm trying to understand the situation better for myself (and others) for starters then we'll see what can be done.

So you have a xp system hosting a virtualized version of ubuntu server, right?

Then you have a separate xp system that is connecting to the first xp system via the default remote desktop client (rdp) built into xp, right?

My question to you is why not just install a ssh server on the Ubuntu server. Set the VM to bridged mode so it is on the "real" network. Then download putty and connect via ssh natively.

---

### Post by geohei on 2011-06-26
All your questions were answered correctly!

I use ssh to connect to the server, but I have to use RDP in order to connect 2 USB devices from WinXP to the Ubuntu guest. For this, I need to use RDP and the VMware interface (there is no other method know to me). Next, I need RDP to start the Ubuntu guest again via the VMware interface (again, no other method known to me).

Since I see Ubuntu then starting right in front of my eyes (inside the VMware, though RDP), I like to work with it as well initially. But the "|" doesn't work.

That was my point!

Sure ... I could use the ssh and I also use it, but I was wondering why the "|" (and only this key) doesn't get through to the Ubuntu guest using RDP?

Thanks,

---

### Post by VcDeveloper on 2011-06-26
@geohei - Hi, Would you tell me how you setup WinXP to connect to Ubuntu.  I'm running Win 7 and I keep getting a connection failure!  Thanks!...

---

### Post by crispy_420 on 2011-06-27
You know I just tried this myself and my "|" key worked fine for me granted my operating systems are close but not identical. I connected between two different Windows 7 machines with RDP on my LAN. I booted VMPlayer running a older copy of Bodhi Linux (an Ubuntu derivative). So there must be another issue somewhere besides the RDP connection.

When you RDP over to the other machine can you issue the | in Windows cmd?

Are all systems set to the same keyboard type? Both physical and virtual machine?

I guess in a pinch you could bring up the onscreen keyboard in Windows as a backup plan. It would be inconvenient but it should work.

---

