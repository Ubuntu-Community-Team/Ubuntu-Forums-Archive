---
title: "Wifi double trouble"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by Whohlme on 2007-10-15
I have two problems: one is that we recently switched to DSL internet at my house and an Ubuntu box that had a fine connection before with cable can no longer get online. It says there is a connection but ping and browser tests fail.

The second problem is that I had another computer I put Ubuntu on earlier that just didn't work at all with wifi. I installed the RaConfig2500 utility, but when I start it, it says device not found and to check some file (i forget).

Both wireless cards are in desktops and are Linksys WMP54G's, which supposedly are supported. 

I thought I'd check here before I switched to another distro (or even NetBSD) that gave me better hardware support since I have also had a problem with low mic volume and the inability to record in Audacity.

---

### Post by openaddict on 2007-10-15
Some DSL providers require you use a username/password before you can connect.  I would double check that you don't need anything like that for your DSL service before you poke around inside the operating system.

However, if you have already verified you do not need a username/password or you are using the correct one, check to see your ethernet card isn't set up with a manual configuration for the old cable internet service.  Change everything back to Automatic configuration (DHCP) if it's not and reboot your computer just to make sure everything restarts correctly and you pull a good IP and DNS information.

Also, before you switch to another distro for your wireless card, ensure that your wireless network card settings are configured for your access point and encryption key if you are using encryption.

---

### Post by Whohlme on 2007-10-15
The right WAP settings are there and I am set to DHCP. We did get a new user and password for the Net, but I can't figure out where to put it. I tried the "pppoeconf" command, but it didn't find anything according to it. This is probably the problem and I hope it can be fixed because I got rather addicted to GLest on Ubuntu and I do like the distro in general...

What about the second problem?

---

### Post by rustybronco on 2007-10-15
can you get online with a ethernet cable from one machine to the dsl router?

---

### Post by Whohlme on 2007-10-15
Yes, I have one Ubuntu box that is doing this just fine through ethernet and I didn't have to enter any passwords or anything. It just worked.

---

### Post by Whohlme on 2007-10-15
Also, the Windows boxes didn't need to put any password info either. I also have a Handheld PC (Jornada 720) that can get on the Net just fine via ethernet without passwords. (it can get on under Linux too)

---

### Post by Whohlme on 2007-10-16
Would I need to reinstall the RaConfig Utility, or plug into Ethernet and install something else?

---

### Post by Whohlme on 2007-10-17
Is something that can even be fixed at this point? I took the box in question (the one that worked with wifi with cable internet but not with DSL) upstairs and hooked it to ethernet. No problems, no user authentication required. Is DSL in general not good with wifi? I know it drops in and out even from 5 feet from my router with my Windows XP laptop (which I love running LiveCD's on since it's not really mine). That box had the strongest wireless connection in the whole house and was the farthest and now it is passed by everyone except me as a piece of junk. That's not cool, because I know they think it has to do with Linux deep down... I hope there is a fix.

---

### Post by Whohlme on 2007-10-17
I'm completely baffled. I can see the network, and even prompted for the WPA Key, but it just won't connect... Is Ubuntu and Linux in general capable of connecting to a DSL network through wifi? It seems to be possible from WinXP.

---

### Post by rustybronco on 2007-10-17
> **Whohlme said:**
> Is Ubuntu and Linux in general capable of connecting to a DSL network through wifi? It seems to be possible from WinXP.Thats what I use, sbc dsl wired and wireless.

---

### Post by Whohlme on 2007-10-17
And you didn't have the problem I'm having? Could it be that the computer "remembers" the cable settings? That shouldn't be, because I have DHCP chosen...

---

### Post by Whohlme on 2007-10-18
I have good news! After giving up, I took the computer back downstairs in defeat and went to sleep (it was around 4 AM). The next morning when I came home from school, however, my dad said the internet worked! Apparently something must have happened, and I think it was this: I did a search for "DSL" in Synaptic and installed one or two things i thought might help. I did not pay attention to this until I heard that wifi was back up. In any event, I am super happy about this!

---

