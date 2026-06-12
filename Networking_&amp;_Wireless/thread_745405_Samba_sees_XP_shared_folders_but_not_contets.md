---
title: "Samba sees XP shared folders but not contets"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by gratefulfrog on 2008-04-04
I cannot seem to get to the contents of my WIN XP shares via samba, even though the shared folders appear in the Nautalis browser. 

They each appear as empty.

I have no idea where to begin to debug this...

thanks for any ideas;
GF
[http://gratefulfrog.net](http://gratefulfrog.net)

---

### Post by superprash2003 on 2008-04-04
try this - go to places->computer and type smb://192.168.1.10 where 192.168.1.10 is the ip of xp

---

### Post by gratefulfrog on 2008-04-05
Indeed that works up to a point. I can see the shared folders on the PC, but I can not see their contents... The problem is to get to the files and use them from the Ubuntu box...

Thanks for the help, anyway ;-)

---

### Post by jetsam on 2008-04-05
Possibly this is a permissions problem on the Windows side if you're using XP pro.  

Right click on the shared folder, go to the sharing tab, and hit the "Permissions" button (third from the bottom.)  Make sure "Everyone" has at least read access, or more if you'd like.  

I think Nautilus uses the guest account if it's available when accessing Windows shares.

---

### Post by gratefulfrog on 2008-04-05
Thanks, but I'm using Win XP home and their's no permission issue.  A long time ago, like in the days before feisty, this used to work fine, since then it hasn't ever worked, but I never needed it. Now; I'm stuck...

thanks again,
GF

---

### Post by lswest on 2008-04-05
Hmm, you could always check on the XP home if the sub files and folders of the shared folder are being shared as well (for some strange reason, my XP home only shared the folder, unless i shared the rest of the stuff too).  Give it a shot.  Otherwise...you could set up an ftp server on your XP, might be a bit more complex than you need, but it would work.

---

### Post by gratefulfrog on 2008-04-05
Thanks, but you can't share files, it seems...

---

### Post by jetsam on 2008-04-05
These samba and windows integration problems can be frustrating and sticky and sometimes end up unresolved anyway.  

This page by another forum poster has some good ideas on trying to debug these issues:
[http://aeronetworks.ca/samba-debug-howto.html]("http://aeronetworks.ca/samba-debug-howto.html")

Basically, if you connect from the command line with smbclient, you might see some better error messages than Nautilus will give; Nautilus tends to just fail silently.  
Edited to add: The stuff on debugging accessing Windows shares from linux is about two thirds of the way down the page.  

Another possible option as a sort of workaround is that it might be easier to go the other way and set up a shared folder on the Ubuntu computer that the windows computer can access.  This is probably the most straightforward tutorial I've seen on doing that:
[http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm]("http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm")

---

### Post by Eiríkr on 2008-04-05
I'd strongly second jetsam's suggestion -- trying to use the deliberately crippled XP Home as a file server is not a solid proposition.  Plus, given what I've read elsewhere, XP has a bug in it regarding name resolution, such that trying to navigate a network with XP machines from an Ubuntu machine will fail out pretty commonly.  This issue seems to go away when using the Ubuntu machine as the Samba file server.  

Cheers,

Eiríkr

---

### Post by gratefulfrog on 2008-04-06
Thanks you guys for all your advice!

But, my problem is to access from my Ubuntu Box the files that are physically stored, for various reasons, on the XP box. 

I confirm that this used to work fine several Ubuntu's ago...

I cannot use the Ubuntu machine as the physical repository for the files....

Ciao,
GF

---

### Post by Eiríkr on 2008-04-07
Unfortunately, Samba is quite the moving target, in two directions -- Windows keeps moving around, especially with the Windows Update automatic craziness, and then Samba is evolving as well in an attempt to keep up.  So there are exactly zero guarantees that something that used to work with Samba some time ago will continue to work today.  

If there's no way to change (or at least check) the permissions on the XP side, you might have to go super old school and copy the files to a disk.

Good luck,

Eiríkr

---

