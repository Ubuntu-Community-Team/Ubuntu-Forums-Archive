---
title: "First Time Linux User - Connecting to Windows Network?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by PhoenixFyre on 2010-12-22
I have been using Windows since I started using computers, and have recently set up one of my desktops with Ubuntu. I want to connect to the internet, and everyone keeps telling me that I need to configure some stuff, and get some settings, and find out some information... then it seems that everyone forgets that I've never touched Linux before, and have no idea what to do with that information.

I want to connect to my home network, which is administered by my father. Every other computer on the network is Windows, and so when I go to Network on my Ubuntu desktop, I see one network, entitled "Windows Network." When I double-click it, I get the error message, "Unable to mount location: Failed to retrieve share list from server".

I'm connecting to the network via Ethernet, using a Cisco ValetPlus wired/wireless router.
My ethernet controller is an Intel 82562ET/EZ/GT/GZ - PRO/100 VE
My ISP is Blue Ridge Cable, in America.
I'm running Ubuntu 10.10, Maverick

I've heard that Linux servers need to use Samba to connect to the Windows equivalent, the SMB. Does a Linux desktop need Samba to connect to a Windows network?

Thanks!

---

### Post by Jerry N on 2010-12-22
I don't know why but I have found recent versions of Linux Mint to work better on Windows networks than Ubuntu.  I got rid of exactly the problem you are describing by changing to Mint.  

In case you haven't seen Mint, it is Ubuntu with some usability improvements.  I find the Ubuntu forums to be more informative than the Mint forums.  

You do need Samba to share Ubuntu files on the network.

Edit:  If your Ubuntu computer sees the Windows computers on the LAN, I see no reason why you would have to change anything to access the internet, unless there is some setting in the router that is locking you out.  In that case, you will have to talk to your system administrator.

Jerry

---

### Post by CharlesA on 2010-12-22
Are you able to connect to one of the machines by using "connect to server" and punching in the ip address?

---

### Post by PhoenixFyre on 2010-12-22
> **Jerry N said:**
> 
Edit:  If your Ubuntu computer sees the Windows computers on the LAN, I see no reason why you would have to change anything to access the internet, unless there is some setting in the router that is locking you out.  In that case, you will have to talk to your system administrator.
Jerry

My Ubuntu computer doesn't actually see the other computers on the LAN -- unless of course I would find that somewhere other than the Network directory. Where would the other computers show up?


> **CharlesA said:**
> Are you able to connect to one of the machines by using "connect to server" and punching in the ip address?

I tried inputting my own IP (the IP address of the Windows 7 computer I'm posting from), and I got "Cannot display location "smb://x.x.x.x/" Failed to retrieve share list from server".

---

### Post by CharlesA on 2010-12-22
Ok. Do you have any machines with file sharing enabled (and the firewall not blocking those ports) ?

---

### Post by JRV on 2010-12-24
Try opening a terminal and type:

  nautilus smb://[HOSTNAME]/[SHARE]

---

### Post by Morbius1 on 2010-12-24
There's a bug in Samba concerning Win7 and spnego. Until the bug fix gets passed on to Ubuntu you'll have to consider uninstalling Windows Live Sign-in Assistant and / or Windows Live Essentials.

---

