---
title: "Samba setup in Kubuntu - how to specify workgroup?"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by sugna on 2006-12-06
I've recently installed Kubuntu Edgy and am trying to set up Samba file sharing so I can see my Windows network.  I'm trying to do it with the graphical setup interface for Samba file sharing, accessed via the system settings.  If I have to, I'll give in and edit the smb.conf file, but I want to exhaust the graphical method first.

Specifically, I want to know how to specify the workgroup to which the computer belongs on the windows network.  I seem to remember this being a very easy step via the graphical setup in Ubuntu (i.e. with Gnome), but I can't seem to see it anywhere in the Kubuntu setup.

Am I missing something?

---

### Post by gerdt on 2006-12-10
In KDE you can modify it in System Settings -> Network Settings under the tab Domain Name System

---

### Post by sugna on 2006-12-10
But which setting under that tab corresponds to the name of the Windows workgroup (eg MSHOME) in which Samba will operate?

---

### Post by gerdt on 2006-12-11
Domain name

But what I do is (also) configure it in /etc/samba/smb.conf:
Add/Modify this line (under [global] ):

workgroup = YOURWORKGROUP

---

### Post by sugna on 2006-12-11
I would not have expected 'Domain name' to correspond with the Windows workgroup.  I'm no networking expert, but I thought that they were two different concepts.  Of course, I could be wrong.  But I will make the observation that the workgroup that I manually entered into smb.conf is not reflected anywhere in the Domain name setting.  This suggests either that the integration of the menu with smb.conf is incomplete or that 'Domain name' does in fact refer to a different setting.

What I was after was a graphical setting that would essentially write the "workgroup = YOURWORKGROUP" line into the smb.conf file for me.  That might sound lazy given that I (now) know where to find the file and how to edit it, but the issue for me is that if this is truly a Linux operating system "for human beings", I shouldn't **have** to know where that file is or even that it exists just in order to do something as simple as share or access a network drive.

Ubuntu in its various flavours is clearly making strides in this direction ... but it ain't there yet.  I'd call it "Linux for slightly less geeky human beings".

---

### Post by Iowan on 2006-12-11
Domain and workgroup **are** different concepts, but most of the tutorials/HowTo's I've been reading on setting up Samba as PDC use **workgroup=** setting to "define" the domain.  Active Directory gets even more complicated...

---

