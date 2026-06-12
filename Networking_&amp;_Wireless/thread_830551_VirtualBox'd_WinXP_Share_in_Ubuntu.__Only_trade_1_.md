---
title: "VirtualBox'd WinXP Share in Ubuntu.  Only trade 1 way"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by AlucardXXVII on 2008-06-15
I've installed the Closed Source VirtualBox 1.6.2 so I can still use my Zune.  I've configured Samba now so I can share mp3s from my Ubuntu install over the network to my Virtual XP Machine.  It works just fine that way, I can put songs into the Shared Directory and access them from the Windows box through My Network Places.

However, I have some old pictures on my Zune I want to send back over to Ubuntu.  I've saved them back to a directory in Windows and adjusted the sharing properties to share over the network.  I can get to the files from a separate Windows XP Laptop.

I can get files off of my XP Laptop using the smb://IPADDRESS/ method.  I can SEE the computer name for my Virtual XP machine.  All I get for that is a white window with nothing in it.

I could easily get around this with a USB stick, of course, but it's all just the principle I'm worried about.  I'd just like to get it working.  


I've checked a few other threads on this, and even the resolved ones don't really have a solution for me.

I have a linksys router and my Desktop Linux PC has an IP of 192.168.1.107.  The windows machine network properties show an IP of 10.0.2.15.  May there be something wrong with my configuration of VirtualBox?  (I can access the Internet from Virtualized XP)

Thanks!

---

### Post by jetsam on 2008-06-16
It's hard to make out from your description exactly which directions and connections of file sharing you're having trouble with-- in particular, where the extra laptop comes in.  

I'm pretty sure I understand at least part of your problem.  It's a limitation of netbios browsing that it doesn't work well over NAT connections, and virtual box networking by default is a NAT connection.   

The full fix for this gets into pretty hairy territory:
[https://help.ubuntu.com/community/VirtualBox-Networking]("https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03")

I believe virtual box has special provisions for filesharing between the host and guest machine: 
[https://help.ubuntu.com/community/VirtualBox-Sharing Folders Between Host and Guest]("https://help.ubuntu.com/community/VirtualBox#head-7aa868356831569a64fb5b4454d8024ec05f46d6")

You might be better off using the latter approach.

---

### Post by AlucardXXVII on 2008-06-16
> **jetsam said:**
> It's hard to make out from your description exactly which directions and connections of file sharing you're having trouble with-- in particular, where the extra laptop comes in.  

I'm pretty sure I understand at least part of your problem.  It's a limitation of netbios browsing that it doesn't work well over NAT connections, and virtual box networking by default is a NAT connection.   

The full fix for this gets into pretty hairy territory:
[https://help.ubuntu.com/community/VirtualBox-Networking]("https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03")

I believe virtual box has special provisions for filesharing between the host and guest machine: 
[https://help.ubuntu.com/community/VirtualBox-Sharing Folders Between Host and Guest]("https://help.ubuntu.com/community/VirtualBox#head-7aa868356831569a64fb5b4454d8024ec05f46d6")

You might be better off using the latter approach.

The extra laptop comes in because it's a physical computer on the network.  I can share files back and forth.  You have it correct that I'm trying to get files from a virtual pc into ubuntu.

From the latter link, can you dumb this down for me?  I think it's the last step:

mount -t vboxfs share mountpoint

I'm not sure what the variables are, and if I'm supposed to specify a drive letter or something

I think this will help me

---

### Post by jetsam on 2008-06-16
With an XP guest you shouldn't need those mount commands.  

I've never actually used vbox with an XP guest, so I went searching for a more explicit tutorial.  This is quoted from an Ubuntu Tutorials blog page:
[http://ubuntu-tutorials.com/2008/02/01/how-to-do-seamless-window-integration-with-ubuntu-virtualbox/]("http://ubuntu-tutorials.com/2008/02/01/how-to-do-seamless-window-integration-with-ubuntu-virtualbox/")
> **Configuring Shared Folder Integration**

One additional thing you might want to setup is shared folder integration. What I mean by this is having the files from your Ubuntu desktop appear on your Windows desktop as well. This might be useful, for instance, if you launched Internet Exploder via your integrated Start menu and downloaded a file. The saved file would then appear on your native Ubuntu desktop, via the shared folder system.

First we’ll need to install the VirtualBox Guest Additions. I haven’t yet blogged about how to do this on Windows guests, but you might refer to my previous post on Installing Guest Additions for Ubuntu Guests. Hopefully this’ll be enough until I write a proper article on the topic.

Next activate virtual shared folder support in your guest OS (Windows). Do this via the main VirtualBox window, selecting (Machine > Settings > “Shared Folders”). Click the button to add a shared folder (the top right icon), and define the path to your share. You’ll likely want to share your current Desktop, so you might select:
    ```
/home/username/Desktop
```
Now, toggling back to your Windows guest, you’ll want to mount this shared folder. You’ll need to open a shell using (Start > Run > “cmd“). Then use the following command to “mount” this shared folder between your Ubuntu host and your Windows guest.
    ```
net use x: \\vboxsvr\Desktop
```
You should now have access to your shared folder...

The blog page is actually about seamless integration (a different topic), but the shared folders part of it seemed pretty well written and explicit.  

Hope that helps...

---

### Post by jetsam on 2008-06-16
> I've configured Samba now so I can share mp3s from my Ubuntu install over the network to my Virtual XP Machine.

...so have I just suggested an alternate way to do what you can already do?  :-s

---

### Post by AlucardXXVII on 2008-06-16
> **jetsam said:**
> ...so have I just suggested an alternate way to do what you can already do?  :-s

No, I want to xfer some pictures from my Zune back into ubuntu.  Ubuntu can't mount the zune so I have to download them back to windows.  I know I can use a usb stick but it's just the principle.  I can't share from the vbox to ubuntu.  I can only go from ubuntu to the vbox

---

### Post by jetsam on 2008-06-16
> I can put songs into the Shared Directory and access them from the Windows box through My Network Places.

Can't you just open that same share in My Network Places and copy the files to it from within the XP guest?

I have vbox set up with a Gutsy Host and a Hardy Guest, and it seems like accessing shares from the external network works from within the Guest.  

What seems troublesome is accessing shares on the Guest machine from outside it.

---

