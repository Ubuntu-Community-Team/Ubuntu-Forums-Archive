---
title: "Sharing FIles with Networked Windows PC"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by ClickForth on 2007-04-16
I ran Shared Folders in Edgy to share files with the windows PC downstairs. It allows me to add folders to share with the Windows PC, but I didn't see a way to access the folders of the Windows PC. How do I access these/start sharing with it?

---

### Post by ClickForth on 2007-04-16
And I wanna do this through the Shared Documents folder in Windows, if possible. I pretty much just wanna be able to access that from the Ubuntu PC. And they're connected via an ethernet cable, not wireless if that matters.

---

### Post by yomama062 on 2007-04-20
I am also wondering about how to do this. 
I have a wireless router, Netgear WWGR614. Ubuntu installed on a older box with a couple of larger HDs with media on them. I also have XP on this box. 

Then I have a Vista Home Prem laptop connecting wirelessly to the router.
Both are getting access to the internet fine. What I want to do next is allow the laptop to read and write to the drives and folders on the older box. 

I have clicked on a folder I want the Vista laptop to be able to access, by going 'share folder'. It then installed some things and gave me the choice:
Do not share
Share through Windows networks (SMB)
Share thru Unix networks (NFS)

I chose Windows (SMB). I can't yet see the folders on the Ubuntu PC looking at the Network folder in the Vista laptop. 
Am no doubt missing something simple, like letting the PCs see each other at all to begin with. Not sure how to do that. 

ANy help would be great.

---

### Post by Stickymaddness on 2007-04-21
What version of Ubuntu are you guys running? I'm using Feisty and I can access normal XP shares by going to Places->Network.

---

### Post by tarnok on 2007-05-02
I am also attempting to access a shared folder on an XP machine from an Ubuntu machine.  Feisty is the installation.  I'm wondering if the reason I can't find the shared folder under network places is because I ran windows' network wizard thingy when I set the folder to be shared.  

If this is the problem, what do I need to do about it?

---

### Post by adromidon on 2007-11-18
I believe there is an issue with Samba being read correctly on a Vista machine.  I have had issues trying to do this and the Microsoft forums suggest that the current version of Samba is not compatible with Vista at least not 100%

If you have Vista ultimate it has built in NFS support you just have to enable it but people like you and me that have Home Prem are out of luck as they will not release this service package to home or home premium users :(

If you do manage to get Samba working I have found that Vista has this new security feature (at least they claim it is a security feature) that limits all connections to network shares via the windows network (IE Samba) to one user per network share. this has cause numerous errors when the the files share in my home are tried to be accessed on the windows side. If you can manage to get a NFS client in Vista you likely to have much better connectivity and luck with regards to sharing

---

### Post by al7kz on 2007-11-19
delete

---

