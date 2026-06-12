---
title: "layman's definition of NFS &amp; SAMBA"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by wpshooter on 2006-10-14
Can someone give me a layman's definition of NFS and SAMBA ?  

When I open "**Shared Folders**" on my Edgy installation, it has a help button but the information given there is not sufficient for me to know if I am supposed to install **NFS** or **SAMBA** or **both**.  I have googled these two terms but the information that is given does not impart to me which I should use.

Here is what I have:

4 computers all running either Dapper or Edgy and all 4 running thru a Netgear 8 port wired hub.  My internet service is being provided thru my Verizon DSL modem which is in turn connected to a 4 computers thru that same 8 port Netgear hub.  **I HAVE ZERO M/S WINDOWS COMPUTERS**.

P. S. - All 4 of my computers are DESKTOP installs of Ubuntu using either the DESKTOP or ALTERNATE CD.

Also, is there a GUI for setting up the NFS or does this just apply to SAMBA ?

Thanks.

---

### Post by mips on 2006-10-15
You want NFS !

If you have a linux pc that needs to access a windows pc/server install Samba-Client
If you have a linux pc/server and have to share the resources with windows pc's install Samba

If you only have Linux pc's use NFS.
SAMBA only comes into the equation when MS is involved.

Google: NFS gui

---

### Post by wpshooter on 2006-10-15
> **mips said:**
> You want NFS !

Are you sure about this ???

I have chosen the **NFS** listing on the **SHARED FOLDERS** menu of Ubuntu and have attempted to setup the folder sharing of my home folders between two different Ubuntu machines and I have tried almost every possible combinations of parameters that are listed in the GUI menus and I can **NOT** seem to view/share the home folders from the opposing workstation.

One thing I don't understand is that even when I attempt to use NFS, when I attempt to view the **NETWORK SERVERS** in Ubuntu, what comes up is always listed as **WINDOWS NETWORK**.  Why would/is this listed as **WINDOWS** if I am using a Unix/linux based sharing protocol ?

Also, in some of my earlier attempts at getting this to work, I had tried SAMBA and it seems to have the ability to allow me to view resources from one workstation to the other.  Why would SAMBA allow me to do this when you are saying that it is designed for sharing between WINDOWS machines and Linux machines, when I, in fact, have **NO** windows machines in my house ?

Thanks.

---

### Post by mips on 2006-10-15
> **wpshooter said:**
> Are you sure about this ???


No, not at all. I'm one of those individuals that just enjoys blabbing on and talking absolute nonsense ;)

Rather than relying on my ramblings I would suggest you read these for verification:

[http://nfs.sourceforge.net/](http://nfs.sourceforge.net/)
[http://en.wikipedia.org/wiki/Network_File_System](http://en.wikipedia.org/wiki/Network_File_System)
[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

[http://us3.samba.org/samba/what_is_samba.html](http://us3.samba.org/samba/what_is_samba.html)
[http://en.wikipedia.org/wiki/Samba_%28software%29](http://en.wikipedia.org/wiki/Samba_%28software%29)

---

### Post by wpshooter on 2006-10-15
Thanks.

I had already referenced some, if not all of these.

And to me, they seem to have little, if any, significance to the way the GUI parameters in **Ubuntu** are setup.  They seem to just give some generic information about NFS and SAMBA, which may not necessarily relate to the way Ubuntu handles these functions.

---

### Post by Teddy_P on 2006-10-24
Have you found any more information. I am haveing the same troubles as you.
What did you end up doing?



Teddy

---

