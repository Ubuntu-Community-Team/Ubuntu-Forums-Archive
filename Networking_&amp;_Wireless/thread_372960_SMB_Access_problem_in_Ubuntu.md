---
title: "SMB Access problem in Ubuntu"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by alexcr on 2007-02-28
Hi Guys,

I have problem setting up SMB share (to access an SMB file and print server 
on my home network) on Ubuntu. Hope you can help me to figure it out.

The server is a stand alone USB storage and printer server with static IP 
address and attached directly to my router. File access and network printer 
were setup in my Windows machine w/o any problem.

However, in Ubuntu, when I go to Places > Network Servers > Windows Network,
 it says "Sorry, couldn't display all the contents of "Windows Network". If 
I go to Places > Connect to Server and setup file access from there, after 
the setup, double click the mount, it will ask for password, enter the 
password, it will ask for password again, reenter, nothing happened... 
Double click on the mount again and PC in deadlock.

Network printer cannot be setup either. When I go System > administration > 
Printing > Add a Printer, then go Network Printer > Windows Printer (SMB), 
the moment I chose SMB, it poped up an error window, said "The 
Application "gnome-cups-add" has quit unexpectedly".

Any idea of what's going on?

Thanks a lot!

---

### Post by alexcr on 2007-03-01
Anyone can help?

---

### Post by Detonate on 2007-03-01
I always use the CUPS interface to set up my printers.   It seems to work better.

[http://localhost:631](http://localhost:631)

I successfully print to two printers which are physically attached to my windows machine, one by USB and the other by parallel port.

I am able to access all of the shared folders on the windows machine on the network, but none of them have USB drives, so I can't be of much help there.

---

### Post by tagra123 on 2007-03-01
Try setting your ubuntu domain to MSHOME or WORKGROUP and see if it will display. 

OR

enter the printservers ip address directly  //192.168.1.45/myprinter

Also, There is place to set workgroup names in using gconf editor. Search the forums for this one.

---

### Post by tagra123 on 2007-03-01
As far as CUPS is concerned -- its hit and miss.  It was very dependable in Breezy. I have two different routers. If I'm on the linksys router everything shares fine. If I'm on the Belkin Router CUPS doesn't work.  Both work fine with samba so I don't get that one.

---

### Post by alexcr on 2007-03-01
I am trying your method. But it keeps asking me user name and password even though I already entered.


> **Detonate said:**
> I always use the CUPS interface to set up my printers.   It seems to work better.

[http://localhost:631](http://localhost:631)

I successfully print to two printers which are physically attached to my windows machine, one by USB and the other by parallel port.

I am able to access all of the shared folders on the windows machine on the network, but none of them have USB drives, so I can't be of much help there.

---

### Post by Detonate on 2007-03-01
What happens when you put in your username and password?  You should get a message saying printer successfully installed.  Make sure the path to the printer was entered correctly.  For example on my setup it is smb://microtel/brother.  microtel is the name of my windows computer and brother is the share name of the printer on that computer.

---

### Post by alexcr on 2007-03-01
> **Detonate said:**
> What happens when you put in your username and password?  You should get a message saying printer successfully installed.  Make sure the path to the printer was entered correctly.  For example on my setup it is smb://microtel/brother.  microtel is the name of my windows computer and brother is the share name of the printer on that computer.
Hmm... Now I am thinking that maybe I shouldn't set up the printer via the SMB  setting. It's not installed in Windows machine. It's on a print server in my home network. When I set up the printer in my windows machine, I added the printer as a local printer, then create a standard TCP/IP port to link to the print server.

---

### Post by Detonate on 2007-03-01
That's a little more complicated and I don't have any experience with a setup like that.  But I would think that if the printer is listed in windows, and sharing is enabled, and the printer has a share name, it would still work.  :?: :?:

---

### Post by alexcr on 2007-03-01
Good point! But I don't want that Windows machine open all the time. That's why I bought the little print server box. :)

> **Detonate said:**
> That's a little more complicated and I don't have any experience with a setup like that.  But I would think that if the printer is listed in windows, and sharing is enabled, and the printer has a share name, it would still work.  :?: :?:

---

### Post by alexcr on 2007-03-01
Hi Detonate,

What's the user name and pwd for CUPS? I was assuming it's my Ubuntu user name (not the root). But it keeps poping up windows asking me for user name and pwd after I entered it.

> **Detonate said:**
> What happens when you put in your username and password?  You should get a message saying printer successfully installed.  Make sure the path to the printer was entered correctly.  For example on my setup it is smb://microtel/brother.  microtel is the name of my windows computer and brother is the share name of the printer on that computer.

---

### Post by Detonate on 2007-03-03
Well, I don't understand that, because i always just enter my user name and password and it works.  You are the sudo user on the system I assume?  Try putting "root" as the username and your sudo password as the password and see if that works.

---

