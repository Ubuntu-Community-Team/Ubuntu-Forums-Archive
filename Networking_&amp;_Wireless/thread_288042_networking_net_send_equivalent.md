---
title: "networking: net send equivalent?"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by Kulgan on 2006-10-29
I was trying to find an equvalent for "net send" for linux. I am on ubuntu and would like to send (and possibly receive, though it is not so important) messages to a Windows XP machine. 

A google gave me 

```

$ smbclient -M NetBIOS-computer-name 
$ Message to send to user
$ ctrl-d

```

but for that I get 

```

Connection to DESKTOP failed

```

I have samba installed, obviously... 

At least I presume i need to enter the network name of the computer? (Which I presume is the name I get in Places -> Network Servers -> Windows Network -> <workgroup> ?)

Any ideas what is going wrond?

Thanks,
-K

---

### Post by fritz_monroe on 2006-11-04
Good luck with this one.  I want to do the same.

I tried the command you posted and mine sends the message but it isn't received on the Windows machine.  I'm using Win98, not XP on the receiving machine.  I got the computer name from my router/DHCP server.

I suspect my problem is the Win98 machine needs a piece of client software.  Could it be the firewall in your XP machine?  I would think that it probably blocks some ports by default.

If you find the answer, please post.

---

### Post by Kulgan on 2006-11-05
yes, I'm getting a little confused... unfortuneately I didn't test netsend before I changed the second machine to linux. I have tried disabling the firewall... and since the windows firewall is turned off it can't screw things up either. I have no idea what to do... it wasn't as if it were all that important, but I would really liked to have had it. 

I'll try in the norwegian linux forums - they tend to have things like this...


-K

---

