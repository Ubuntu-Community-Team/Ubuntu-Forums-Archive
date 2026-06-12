---
title: "What Firestarter policy?"
date: 2005-10-29
forum: Networking &amp; Wireless
---

### Post by user_stu on 2005-10-29
I'm using Firestarter in its default configuration (coz I don't know better). It is not in Internet Sharing mode.

I am trying to access a shared windows folder on the LAN, but cannot do so unless I turn the Firestarter firewall off.

I have tried adding various inbound policies, but to no avail (I don't really know the syntax or anything). Can someone please explain to a networking novice how to go about this (I don't even know how to determine IP addresses for computers on my network).

Cheers
Stuart

---

### Post by greenway on 2005-10-30
You might want to start to take a look at the blocked events in firestarter (found under the "events" tab).

Also, determine the ip of the PC holding the window folder. In windows go to the command line and type the command "ipconfig" (if I am not mistaken, it has been a while since I've networking on a Windoze box:p ), anyway this should give you the ip for the PC holding the shared folder.

Then look if there are any blocked events from this PC. If you're getting confused, just post the events here and I will take a look. But you do need the ip address for the PC first. Good luck!

-greenway

---

