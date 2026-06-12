---
title: "Ubuntu, OSX file sharing."
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by MacPC on 2006-11-05
On and off, I have been trying to get Ubuntu, OSX and Windows on p2p file sharing. Here is a broke down of my network:

Three Windows PCs using Windows 2000 pro and Windows XP pro.
One Linux PC using Ubuntu 6.06.
Two Macs using OSX 10.8.6.

All Windows PCs have access to Ubuntu's files and folders.
All Windows PCs has access Macs' files and folders.

All Macs have access to Windows' files and folders.
All Macs have access Ubuntu's files and folders.

Ubuntu have access Windows PCs files and folders.
[COLOR="Red"]Ubuntu CANNOT access Macs' files and folders.[/COLOR]

I get the Mac to share the Ubuntu fine, but I don't seem to be able to get the Ubuntu to share the Mac. In the network browswer on the Ubuntu PC, it sees the Mac, but once I open it, it is an empty window, none of the on the Macs folders and files shows up. On the Mac, in the Sharing preference, I turned on everything. What have I missed? Is the problem on the Macs or the Ubuntu?

Any help will be appreciated.

MacPC

---

### Post by kidders on 2006-11-05
Hi there,

What filesharing protocol are you using? Since your network has Windoze machines on it, you only have one option, really ... Samba. Assuming you're using it already on your Mac & Ubuntu box, are you authenticating properly when you try to access the shares?

---

### Post by mr_lars on 2006-11-05
try to put [http://hornware.com/sharepoints/](http://hornware.com/sharepoints/) on your mac

---

### Post by dmizer on 2006-11-06
what method in ubuntu are you using to attempt to mount the mac shares?

---

### Post by MacPC on 2006-11-06
Hi,

Thanks all for you replies.

I didn't have any other software before, I thought the Mac uses Samba like the Windows boxes. 

But last night, I did some digging on the net and I found this software called SharePoints, I gave it a try and now I can access the Mac on my Ubuntu box.  

Don't know how, but it works. :D 

Thanks again.

MacPC

---

### Post by kidders on 2006-11-06
> **MacPC said:**
> I thought the Mac uses Samba

Macs do have Samba, if you'd prefer to share stuff that way :-)

---

### Post by MacPC on 2006-11-06
Hi,

I would prefer to use Samba on the Mac but can you tell me how?

MacPC

---

### Post by kidders on 2006-11-06
I'm very console-oriented ... I would just manually tweak my /etc/smb.conf.

Afaik, killing all samba-related processes is all you need to do once you've finished. OS X should start them all up again once you start using your network services.

---

### Post by MrMacHead on 2006-11-13
Kidders - 

I have exactly the same symptom as MacPc on my brand new Intel iMac. When I open up the Mac shared folder from Ubuntu 6.10, the folder appears empty. There is no request for authentication.

However, from my PowerBook, things work perfectly. Both Macs are running OS X 10.4.8 and Windows file sharing is turned on, thus activating Samba. I have never tweaked anything to get the PowerBook to share properly from Ubuntu.

Thanks to this thread, I have installed SharePoints on the Intel iMac and all is well.

---

### Post by kidders on 2006-11-14
Yeah, you're right ... to access Samba shares *from* OS X, you shouldn't need to tweak anything.

---

