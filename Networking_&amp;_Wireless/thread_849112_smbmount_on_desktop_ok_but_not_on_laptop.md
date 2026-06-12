---
title: "smbmount on desktop ok but not on laptop"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by linuxonbute on 2008-07-04
Hi,

 I can issue this command :

 smbmount //192.168.1.10/PUBLIC nas1

on my desktop PC running Ubuntu 7.10

but on my laptop running Ubuntu 8.04

it fails.

Any idea what I need to do to fix it?

the error is :
error 20 Not a directory

thanks

---

### Post by superprash2003 on 2008-07-04
are you able to ping 192.168.1.10 successfully from the laptop

---

### Post by linuxonbute on 2008-07-04
> **superprash2003 said:**
> are you able to ping 192.168.1.10 successfully from the laptop

Yes, no problem.
I can also access it via the web interface.

---

### Post by superprash2003 on 2008-07-04
go to the terminal and type sudo nautilus smb://192.168.1.10 .. now are you able to see the files?

---

### Post by linuxonbute on 2008-07-04
> **superprash2003 said:**
> go to the terminal and type sudo nautilus smb://192.168.1.10 .. now are you able to see the files?

No.  Message was :  Couldn't display "smb://192.168.1.10".
Nautilus cannot handle smb: locations.

However nautilus smb://192.168.1.10  ( without the sudo )

does work!!!!!!!!!!!

---

### Post by superprash2003 on 2008-07-05
strange..now try mounting again also try changing mount folder to some directory in your home folder

---

### Post by linuxonbute on 2008-07-05
> **superprash2003 said:**
> strange..now try mounting again also try changing mount folder to some directory in your home folder

I did, but it doesn't work and nas1 is a folder in my home directory. 

That is what is so baffling. 

What I am trying to do is set this up so I have an automatic way of keeping all my work identical on each machine so if i edit a document when working on one it will actually be the same document when i view it on the other.

---

### Post by linuxonbute on 2008-07-05
> **linuxonbute said:**
> I did, but it doesn't work and nas1 is a folder in my home directory. 

That is what is so baffling. 

What I am trying to do is set this up so I have an automatic way of keeping all my work identical on each machine so if i edit a document when working on one it will actually be the same document when i view it on the other.

Update.
From my laptop :-
I can access the web interface to my nas box 192.168.1.10
but not the web interface to my adsl modem/router 192.168.1.1
I can also ping both from it.
My modem/router is set up to allow all local ie 192.168.1.0
to access the intranet and I have no problem from my desktop (192.168.1.30)

Has anyone any idea why there is this problem?

---

### Post by linuxonbute on 2008-07-06
Just an update to my problem which began :

I can issue this command :

smbmount //192.168.1.10/PUBLIC nas1

on my desktop PC running Ubuntu 7.10

but on my laptop running Ubuntu 8.04

it fails.

Any idea what I need to do to fix it?

the error is :
error 20 Not a directory

Added info was :
From my laptop :-
I can access the web interface to my nas box 192.168.1.10
but not the web interface to my adsl modem/router 192.168.1.1
I can also ping both from it.
My modem/router is set up to allow all local ie 192.168.1.0
to access the intranet and I have no problem from my desktop (192.168.1.30)

From my desktop PC I can access both web interfaces.

To try to track down the problem, which I now have come to believe is something to do with the version of some part of Ubuntu 8.04, I have tried the following:

Replaced network manager with wicd.  --- No change.

Tried connecting via wired network.  ---- can connect to my routers web interface as well BUT smbmount still fails with the same message.

Can anyone suggest what else I can try or better still a full solution? :)
Thanks

---

### Post by linuxonbute on 2008-07-07
After further thought I am coming to the conclusion that this is a bug in the software. 

But which bit? How can I report a bug if I cannot identify which piece of software is at fault?

Could it be the version of libsmbclient?

If so, could I replace it with the version in 7.10 and if so how?

Would I need to run dpkg or something else, as synaptic doesn't seem to have an option to install an older version of any software?

---

### Post by linuxonbute on 2008-07-07
> **linuxonbute said:**
> After further thought I am coming to the conclusion that this is a bug in the software. 

But which bit? How can I report a bug if I cannot identify which piece of software is at fault?

Could it be the version of libsmbclient?

If so, could I replace it with the version in 7.10 and if so how?

Would I need to run dpkg or something else, as synaptic doesn't seem to have an option to install an older version of any software?

Can anyone help please?

---

### Post by linuxonbute on 2008-07-09
> **linuxonbute said:**
> Can anyone help please?

Another update.

I have now set up samba on my desktop machine.

It's very weird - here is my setup.

my NAS box is on 192.168.1.10

I have set up my user name and password on both machines to be the same.

from my desktop : smbmount //192.168.1.10/PUBLIC ./nas1  works.

from my laptop, with the same name for a directory on my home directory there : smbmount //192.168.1.10/PUBLIC ./nas1 does not work.

My desktop machine is on 192.168.1.30 and issuing the command

smbmount //192.168.1.30/nas1 ./nas1  from my laptop works.

So I can read and write to //192.168.1.30/nas1 which has, in fact 

//192.168.1.10/PUBLIC  mounted on it.

This means that, although I cannot mount it directly I can via the desktop PC. I have full access to it.

Anyone any idea how I can fix this?

---

