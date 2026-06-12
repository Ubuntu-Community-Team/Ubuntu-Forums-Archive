---
title: "Need help accessing Windows share files"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by eeefresh on 2008-03-23
I have seen a few posts about this, but being fairly new to networking, most of them were over my head.  Here's my problem:

I have a Windows XP desktop with some shared files that I am trying to access with my Ubuntu 7.10 laptop.  I am dual booting the laptop with Vista, and I can access all the shared files when I boot into Vista.  So I know I have the hardware and file sharing options set up correctly.

Here's a few more details about my network:

Desktop IP is 192.168.1.2, default gateway 192.168.1.1
Windows workgroup is called "home"
desktop name is "Mothership"
shared file is called "Videos"

When I go to Places --> Network, I can see an icon called "Windows Network," and when I click on it it shows me "home," then when I click again I can see "Mothership."  However, I can't go any further than that.  When I click on Mothership, it says the "folder contents could not be displayed."

When I click on Places --> Connect to server, I select "Windows share" as the service type, but then I don't know what to put in the rest of the fields (server, port, folder, etc.)  I think part of my confusion lies in all the networking terminology...is IP address the same as server?

Any help, or maybe a link to a simple tutorial, would be appreciated.

---

### Post by superprash2003 on 2008-03-23
try smb://192.168.1.10 where 192.168.1.10 is the ip of the computer you want to connect

---

### Post by pbpersson on 2008-03-23
Do what the last person said - use Konqueror (Nautilis) and put the IP address followed by the share such as: smb://192.168.1.10/Videos

Then once you get it working you can bookmark it so you never need to type it again

I am sort of annoyed that it keeps asking me to logon to my XP machine, but security is a good thing :)

When I first started working with this I was annoyed that I could not easily connect to my XP shares using the "standard" process.....then I discovered that from Ubuntu I could easily reach shares on my Windows 2000 machine but from WIndows 2000 I could also not find my shares on the Windows XP machine.

It turned out there was a bug in the Windows Browser Service in Windows XP - it order to have it behave, you need to stop and restart the service every few hours.  Instead, I just use the IP address.  This also applies to RDP sessions into the XP machine from Ubuntu.

---

### Post by eeefresh on 2008-03-23
Thanks, that was much easier than I thought!

I typed in smb://192.168.1.2/Videos and it showed me the folder.  Now how do I bookmark it?  I would like it to appear under the places menu, if possible.

---

### Post by eeefresh on 2008-03-23
Nevermind, I figured out how to add it to My Places.  I just right-clicked and selected "Connect to this server" in the menu.  Will this automatically mount them each time I boot into Ubuntu, or will I have to edit fstab?  

Actually, I am having another issue that I just discovered.  I am trying to open some avi files from the shared folder and I am getting this message:

```
The filename "1408.avi" indicates that this file is of type "avi document". 
The contents of the file indicate that the file is of type "AVI video". If you open this
 file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file 
from a trusted source. To open the file, rename the file to the correct extension
 for "AVI video", then open the file normally. Alternatively, use the Open With menu
 to choose a specific application for the file.
```

The files will open with Totem, but only with a green bar across the top of the screen.  They won't open at all with VLC.  I tried this with several avi files and had the same issue with all of them.

I think my router broadcasts at 11 Mbps, and my laptop is getting a strong signal, so I don't think its a speed issue.  I am also able to view the movies when I boot into Vista.

---

