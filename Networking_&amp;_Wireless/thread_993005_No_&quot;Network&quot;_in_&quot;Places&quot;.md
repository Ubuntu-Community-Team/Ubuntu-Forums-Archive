---
title: "No &quot;Network&quot; in &quot;Places&quot;"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by jstevans on 2008-11-25
Hi,
A newbie here - I got Xubuntu 8.1 up and running smoothly, it was incredibly easy to get printer, Internet, etc. running, so much was automatic.  However, networking into my Windows machines has me stumped and it a do-or-die issue for me to be using Linux..

I used the "General Properties" tab in 8.10's "Admin > System > Shared Folders" to put my Xubuntu machine onto the same workgroup as my other machines.  And then I used the "Shared Folders" tab of the same dialog box to make one particular folder on the Xubuntu machine to be shared.  Those two steps enabled the Windows machines to see my Xubuntu machine and access files in the shared folder.

However, I cannot figure out how to enable the Xubuntu machine to see the windows machine.

BTW - I can ping each of the Windows machines from my Xubuntu one so the network is there and so are the machines.

I am 99% sure that not having "Network" in "Places" signifies something being quite wrong.  I'm just lost as to what and how to fix it.

I'd very much appreciate any help.

Jay

---

### Post by superprash2003 on 2008-11-25
im not that sure if this applies to xubuntu, but you could give it a try [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by jstevans on 2008-11-25
Thanks for the reply.  However, as stated in the title and body of my post - I don't have "Network" showing up under "Places."

Also, as stated in my post, my Xubuntu machine can ping the Windows machines.

Xubuntu does not use Nautilus, it uses something called "File System - File Manager."  When I take your suggestion and enter smb://192.168.1.12 (the IP of one of my Windows PCs) an icon within its GUI turns red to indicate this is not an allowed address.  If I just enter 192.168.1.12 and click "enter" the File Manager just ignores it, no red light, no response at all.

If I use Firefox and enter [http://192.168.1.12/](http://192.168.1.12/) it also just ignores it, no reaction.  

However, if I enter [http://192.168.1.1](http://192.168.1.1) (the IP address for my router) that works fine, the router's login screen appears, I can log in, everything works as one would expect.

And, if I use Firefox and enter [ftp://192.168.1.254](ftp://192.168.1.254) (the IP address of my FTP server) that works fine, a log-in dialog box appears asking for username and password.

However, there's no way I can figure out to be able to see the Windows PCs that are sitting there on my LAN.

A question - should Samba be set up as a WINS server?  Is that something I'm missing?  I ask because, in Xubuntu's "Shared Folders" GUI it offers that option.

Thanks again for trying to help.  Regrettably, Xubuntu is somewhat different.

Jay

---

### Post by Bradh616 on 2009-05-08
I am having the same issue, have you ever found an answer to this?
If I do I'll post solution.

Found 1, I know this is an old thread but hey it still comes up in searches so here is what I found:

"1. XFCE uses thunar rather than nautilus. Unfortunately, thunar doesn't have network browsing as a default feature; hence no network in places."

[http://www.backports.ubuntuforums.org/showthread.php?t=745825](http://www.backports.ubuntuforums.org/showthread.php?t=745825)

---

### Post by JKyleOKC on 2009-05-09
> **jstevans said:**
> However, I cannot figure out how to enable the Xubuntu machine to see the windows machine.
I'd very much appreciate any help.

Check Synaptic for "xsmbrowser" and install it. This will give you a separate browser for the Windows machine. As someone else noted, the Thunar file manager in XFCE doesn't include network browsing.

Leave the WINS setting alone; it's part of advanced Windows features that won't apply to a simple workgroup installation.

Hope this helps!

---

