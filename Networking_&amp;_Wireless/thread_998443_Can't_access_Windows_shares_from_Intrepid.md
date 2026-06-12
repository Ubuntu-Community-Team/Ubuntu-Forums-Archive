---
title: "Can't access Windows shares from Intrepid"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by SlaughterDog on 2008-11-30
I've got a couple WinXP computers set up with sharing folders, each can access each other. When I ran previous versions of Ubuntu, accessing them was as simple as browsing to them in Nautilus. 

But now on Intrepid, I've not been able to see any shared folders. In fact, I only see workgroups listed part of the time. And when they are listed, only part of the time can I browse one and see my computers listed. I've got Samba service installed and running, of course. 

I am trying to do this wirelessly, by the way; In the past, I was on my home network via ethernet.

Anyone have advice?

---

### Post by SlaughterDog on 2008-12-07
Also, is there an easy way to share via nfs?

edit: I am also noticing that it doesn't ever ask me to log on, as it did in previous Ubuntu releases. When running Windows, I can access my computer running Ubuntu.

---

### Post by tgunness on 2008-12-12
Just wondering if you had this problem fixed. I've got the same issue.

---

### Post by SlaughterDog on 2008-12-12
Nope, I'm afraid not.

---

### Post by gjtoth on 2008-12-12
My network is wired but, I have the same problem.  Was working under 8.04 and now it's not.

In 8.04, there was a way to add the host in the network config from the control panel.  Looks like that's not possible in 8.10.

---

### Post by biotrox on 2008-12-12
try to check it with CLI
try to browse it with smbtree first
and then try it with smbclient to connect to one of the windows share...
it shouldn't have a problem

if u still seeing this problem try to upgrade the samba

hope this helps

---

### Post by gjtoth on 2008-12-12
> **biotrox said:**
> try to check it with CLI
try to browse it with smbtree first
and then try it with smbclient to connect to one of the windows share...
it shouldn't have a problem

if u still seeing this problem try to upgrade the samba

hope this helps

upgraded to 3.2.3 (I think)

I can print to the Windows share printer.  But, no drives are visible.  Either way.

---

### Post by vnevoa on 2008-12-13
For me it started working again after I put the windows machine's IP address and name in /etc/hosts .

---

### Post by tachyon47 on 2008-12-23
I've been seeing some of the same problems. I tried adding another repository to get unofficial upgrades to samba, as mentioned in another thread, but that didn't seem to help 

[http://ppa.launchpad.net/tcarrez/ubuntu/intrepid](http://ppa.launchpad.net/tcarrez/ubuntu/intrepid) main

Anyway on another suggestion I tried installing SMB4k, the KDE samba browser. And I can see and access the shares usng that. I also tried manually entering smb://<ip address> in nautilus and that worked. So its just the browsing that is the trouble, and apparently something with nautilus

Any thoughts anyone?

---

### Post by TheCosmologist on 2009-02-17
> **vnevoa said:**
> For me it started working again after I put the windows machine's IP address and name in /etc/hosts .

This worked for me too. I'm using a fully updated Intrepid.

---

### Post by drdave69 on 2009-04-14
> **tachyon47 said:**
> I've been seeing some of the same problems. I tried adding another repository to get unofficial upgrades to samba, as mentioned in another thread, but that didn't seem to help 

[http://ppa.launchpad.net/tcarrez/ubuntu/intrepid](http://ppa.launchpad.net/tcarrez/ubuntu/intrepid) main

Anyway on another suggestion I tried installing SMB4k, the KDE samba browser. And I can see and access the shares usng that. I also tried manually entering smb://<ip address> in nautilus and that worked. So its just the browsing that is the trouble, and apparently something with nautilus

Any thoughts anyone?
Can someone please explain to me how to manually enter smb://<ip address> in nautilus. I am such a newbie that I need step by step instructions please.
Thank You, Dave

---

### Post by nukedathlonman on 2009-04-19
> **drdave69 said:**
> Can someone please explain to me how to manually enter smb://<ip address> in nautilus. I am such a newbie that I need step by step instructions please.
Thank You, Dave

Easy enough - what's the IP of the computer with the share?  For example, my D-Link DNS-323 (it's a Linux enabled NAS (a.k.a.: a very "basic" file server on my network)) has an IP address of 192.168.0.19.  Just a further note that you may also have to add the name of the shared folder as well immediately after the IP address (it doesn't work for me unless I do, in my case my share name is "Volume_1" so I add "/Volume_1" to all that).  So in the address bar of Nautilus (like in a web browser), you would manually connect to it by simply typing (in my case) smb://192.168.0.19/Volume_1


And yes, I'm in a similar situation as are lot's of other people - I can manually mount my shared directories from a command prompt, manually connect to my server using this manual method, or  connect to my shares with "Connect to Server..." under places.  If I browse the network with Nautilus,I can get just pass double clicking on "Windows Network", and can see the workgroup.  Everything falls apart after that.  If I double click on the workgroup, Nautilus takes a good minute and then displays the infamous message "Unable to Mount Location Failed to retrieve share list from server".

I'm still studying this and doing lot's of reading and hacking - it's rather annoying and I want to get this working properly on both my Ubuntu and Debian systems.  I know that people were saying that one of the problems in my case is that D-Link is using the line "security=SHARE" in it's Samba configuration, but I have hacked my DNS-323 so that it defaults to "security=USER".  That didn't get me anywhere, and now I'm heading back to the drawing board in digging and experimenting.

---

