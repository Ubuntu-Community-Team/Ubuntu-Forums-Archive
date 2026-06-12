---
title: "VMWare, Microsoft, Ubuntu. Who's bug is this?"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by Underpants on 2007-01-12
I’ve discovered an interesting problem and would like some input as to who’s problem it actually is. Microsoft’s, Ubuntu’s, or VMWare’s. On a side note, I’m going to post this in newsgroups for all 3 products. Here’s the scoop:

I’m running the latest release of Ubuntu (Edgy 6.10 fully updated)
I have the latest version of VMWare server installed. 
I have a guest OS of Windows XP Professional with SP2 integrated. 

The problem comes in when I try to use either automatic updates or windows update on the guest OS. Initially automatic updates wouldn’t work at all and windows update would always bomb out with a nebulous hex number telling me that it can’t update. Lots of research went into the error. Most returned information to “adjust my firewall” or “disable my firewall” Well, I in fact, I have no firewall that should be affecting this (read: I run an enterprise sized network). The guest OS is in bridged network mode meaning it has an IP issued by my networks DHCP server, just like 100 other pc’s that access windows update without any hiccups. 
I tried a Server 2003 installation under vmware just for a test. Same problem. I’ve gone back to working with XP at this point. 

I decided to change some of the network settings in vmware for the guest OS. I’ve changed the network mode from “bridged” to “NAT that has external access” so now my guest has a private IP on a little virtual  vmware network and has a gateway to my external network. 
I try to run windows update, guess what? Works like a champ. 
I saw a lot of threads with a lot of people saying they can’t run auto updates in vmware under linux, and I saw a lot that said they could. I didn’t once see anyone say what type of guest OS networking option was in use. 
My immediate thought is that this is a bug in VMWare. 

Who does this problem need to be elevated to? 
Ubuntu because it’s Host OS specific? (I don’t really know if it’s OS specific, I’m looking for input from other users)
Microsoft because Windows Update is a picky little devil?
Or VMWare because it’s a problem with their network drivers?

---

### Post by PilotJLR on 2007-01-12
I have the exact same setup as you, and I can update easily with XPP and 2003Ent. So it can be done!

Does your XP guest have VMware Tools installed and running??

edit: as an aside, the only reason I have a "production" XP guest on my workstation is because I need some proprietary apps for grad school. Thank goodness for vmwar's memory ballooning, cause XP hogs the ram when it's in use. If it idles for a few minutes (but is running, not standby), vmware shrinks the balloon and the ram footprint is much less. Pretty nifty stuff.

---

### Post by Underpants on 2007-01-12
I wonder if it's either my psyical network card, or a config is different when we set up vmware.

---

### Post by PilotJLR on 2007-01-12
Just to confirm, Tools is running??

If so, you can also try to disable TSO checking, which is occasionally an issue (though I don't need to do this in my case, except for large host-to-guest transfers). On the HOST, run this (assume you physical nic is eth0):
```

sudo ethtool -K eth0 tso off

```

---

### Post by Underpants on 2007-01-12
Tools are installed.

Same error after your command.

---

### Post by PilotJLR on 2007-01-12
This is a weird one. I have experience with Server and ESX, and I've never seen this.

It's highly unlikely this is a bug in VMware or Ubuntu/Linux.

 - How did you install XP, i.e. do you have a means to check the integrity of the installation media (be in ISO or physical)?
 - What is the exact error in the guest, and when do you get it?
 - Can you perform a manual update in the guest via the Windows Update link in the Tools menu of IE??

---

### Post by Underpants on 2007-01-13
1. XP came from an unattended installation that I customized for my company. It's a VLK version that has had no changes other than a new winnt.sif that answers all of the questions while it installs. I mounted the ISO in vmware, I have burned dozens of cd's with this ISO and have been doing successful installations for a few years now from it. 

2. Error comes after clicking "express" or "custom" and it is 0x80072EE2

3. When I'm "bridged" No update method will work. Not windows update, microsoft update, or automatic update.

---

### Post by PilotJLR on 2007-01-13
I think I'm stumped on this one, though I found several things on vmtn that maybe could help. You may have already tried this...

1. manually reinstall BITS: [http://support.microsoft.com/kb/842773/](http://support.microsoft.com/kb/842773/)
2. disable tools and folder sharing temporarily: [http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=988&sliceId=SAL_Public](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=988&sliceId=SAL_Public)
3. changing the host MTU to 1492

---

### Post by Underpants on 2007-01-13
If anyone wants to help, the pcap file is here:

[http://waxgroove.com/aarons-update-error.zip](http://waxgroove.com/aarons-update-error.zip)

I started the capture right before clicking "custom" and stopped it a few seconds after getting the error.

---

