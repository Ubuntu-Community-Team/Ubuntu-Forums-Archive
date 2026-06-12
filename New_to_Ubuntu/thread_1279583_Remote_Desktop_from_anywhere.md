---
title: "Remote Desktop from anywhere"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by nominal on 2009-10-01
If I enable remote desktop now, the only people that can access my desktop are people who are on my local network, however I want to be able to access my desktop (which is actually a laptop) from anywhere, especially when i use my school's library.

how would i do this?

im on ubuntu of course, the school uses windows xp.

---

### Post by nhasian on 2009-10-01
all you need to do is forward port 5900 in your router to your laptop's IP address.  hopefully you can set your router to always assign the same ip address to your laptop.

---

### Post by nominal on 2009-10-01
all right, i can do that

but i'm really sure what i'd be typing in to the remote desktop connection at school

and do i need to setup freenx or putty or any of these?

---

### Post by tkelito on 2009-10-01
So you want to access your laptop at home from school remotely?

xx.xx.xx.xx:5900

Where xx.xx.xx.xx is your home IP Address (WAN IP, not the local 192.xx)

You need to also port forward your router to set 5900 to go to the local address of where you laptop is 192.168.xx.xx.  You can do this using either a static ip or reservation if your router supports it.

So for example, my desktop:

Wan is: 98.21.xx.xx
Local IP: 192.168.1.20
Port Forwarded: 5900

So when I am at work, and I want to access my home machine.  I type into VNC Viewer 98.21.xx.xx:5900.  The router then forwards that request to 192.168.1.20 everytime and I am immediately prompted to login.  I am using a static ip, but I suggest for a laptop to use a reservation on your router if it supports it because you will not have to remove you static information every time you leave the house.

Reservations use the name of your computer to reserve and automatically assign an address to that computer within the DHCP range.  Static IPs are usually (should be always) outside the range of DHCP.


::EDIT::

You do not need to setup Freenx or Putty unless you feel you need them.  Putty can give you a remote CLI if you need it, but if you are doing remote desktop obviously that is pointless.  You may find though that your school has limitations on your ability to be able to send/receive packets from VNC.  They may even block packets tagged with ports 5800/5900 because those are the common Remote Desktop Protocols.  You never know, you may want to use a port above 40000 on your home connection to limit the chances of your being dropped by the school internal network.  Also, make sure you USE encryption, on a school network, you never know who is listening.

---

### Post by nominal on 2009-10-01
wow, that really helped me out. i'm actually going to pull up this forum at school and try it. thanks a lot!

---

### Post by Bölvaður on 2009-10-01
It seems like you got everything you need, you only need to forward the port to the router so it will be

Library &#8594; home router &#8594; home computer

So in the library you enter the ip of the router + the port that is used on your home computer (so the router directs that port to the correct home computer.

But anyway I was just repeating what the other guys said.

What I wanted to say is VNC isnt very secure way. So make sure your user name and passwords are difficult to guess. And try to have as strong password on the VNC as you possibly can.
There was a guy on this forum that didn't have any password on his "remote desktop" (VNC) so a random hacker guessed the ip and logged in with no password, waiting until the owner of the computer took a launch break and messed up his computer while he was gone (well I dont think he did anything, but if that "hacker" would have any idea what he was doing he could have).+


So, put a strong password on the VNC so not anyone at all can connect to it.

---

