---
title: "Networking with windows..."
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by infornography on 2006-10-01
I have a home network of two computers connected through a hub, which is in turn connected to my adsl router. At the moment they are both running Windows. I setup the network with the windows network configuration wizard and it works fine (file sharing).

But I would like to change one of the computers over to Linux (Kubuntu). I am not exactly a master when it comes to networking so I was wondering if there is a tool similar to that in windows to simplify the process. Also, if they will still play nice together even though one is using XP.

I do not have a static IP# in case that is relevent.

Thanks.

---

### Post by ola on 2006-10-01
Both Kubuntu and Ubuntu have graphical tools to copy files via Samba (the network protocol used in Windows).

I think you should get your hands on a Kubuntu or Ubuntu CD and boot it up from the CD and see if the tools provided does the work for you. I personally think that both Kubuntu and Ubuntu handles network really nice.

Regarding the dynamic IP is that not a problem since you can use the computer names instead.

Hope you try out the LiveCDs and good luck! Best regards,

Ola

---

### Post by infornography on 2006-10-01
Excellent, I'll give that a try. Could you please tell me the name of the utility in Kubuntu? I can't seem to find it on the menu... Hopefully not just because I am a blind idiot.

Thanks very much

---

### Post by mips on 2006-10-01
Dunno what utility you are referring to but to configure your network:
K Menu -> System Settings -> Internet & Network -> Network Settings

---

### Post by Tom Amos on 2006-10-03
I'm an experienced windows network user, but a linux newb. Is SAMBA the protocol (or application?) that I use to connect to a windows workgroup? How do I set it up? I've been using linux for all of two days, and I've already figure out quite a bit, but I could use a hint. I am already on my network using DHCP from a linksys router, but I'd like to be able to access my windows shares, including file folders and printers.

Thanks!

---

### Post by Tom Amos on 2006-10-03
Ok, nevermind. I figured it out. 

Wow, that was actually pretty easy. I found a menu called Sharing and it prompted me to install SAMBA. I didn't need to specify the workgroup, it listed all available. That was easier than setting it up windows. 

After a little confusion as to how to browse to the shares, I used the 'Go' menu in the file browser and picked the 'Network' option. Is there an easier way to do this... Can I create a shortcut on the desktop to the workgroup? 

Impressed,
-Thomas

---

### Post by dannyboy79 on 2006-10-03
if you use the connect to server option within Places, it should have created a link to whatver location you put in, so the answeer is yes. you can also have it mounted automatically by following this great website, I refer everyone to this place as it has never done me wrong and always answered everyones samba sharing with windows q's.

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

