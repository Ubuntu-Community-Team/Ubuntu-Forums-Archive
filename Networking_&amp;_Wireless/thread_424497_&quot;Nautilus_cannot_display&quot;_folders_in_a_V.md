---
title: "&quot;Nautilus cannot display&quot; folders in a Vista share."
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by iammike on 2007-04-26
Ok, a quick breakdown.

Primary gaming rig is running Vista Ultimate OEM and acts as the primary file server.
Secondary workhorse desktop is running XP SP2 and only shares one drive.
Laptop is running Ubuntu 7.04 and shares nothing.

The primary computer can access shares on the secondary computer.
The secondary computer can access shares on the primary computer.
The Ubuntu laptop can access shares on the secondary computer.
....but....

On the Ubuntu laptop, I browse through the network, go to the Primary system and it displays all the shares on the system.

I double click the share I'd like to access and I get a list of all folders and files in that share.

Now the problem, when I double click on a folder I get the error "Nautilus cannot display 'smb://primary/share/folder'.  Please select another viewer and try again."

The Nautilus then displays the folder as a blank file instead and will continue to do that to any directory I try to open.

If I try to open a file it just tells me that the file was not found or says nothing at all as it makes it look like a blank file as well.

I have changed many permissions through secpol and normal sharing properties to try to resolve this but it just keeps doing it.

To try a few other things, I tried typing the direct path to a folder in Firefox and get no errors but also nothing displayed and when I tried to mount it at command line but that also didn't work.

Is this a common problem people are having or am I doing something wrong here?

---

### Post by tturrisi on 2007-04-26
You may have to config Vista to allow the laptop to access.  Firewall or s/g similar.

---

### Post by apsalyers on 2007-04-27
I am having the same issue exactly, and have tried the following solutions:

Added Ubuntu to my local workgroup, as well as trying to setup a domain.

Completely turning off the Windows Vista Firewall

Verifying permissions of the account I am connecting with, which is setup in Vista as an admin.



Basically I have gone as far as completely turning off local network security, and the same problem persists.

---

### Post by ryanmbeal on 2007-04-29
This one is driving me a bit crazy too. I've tried the stuff posted here:

[http://blogs.zdnet.com/Bott/?p=237](http://blogs.zdnet.com/Bott/?p=237)
[http://blogs.zdnet.com/Bott/?p=238](http://blogs.zdnet.com/Bott/?p=238)

which looks like good content but I'm still having no luck:

---

