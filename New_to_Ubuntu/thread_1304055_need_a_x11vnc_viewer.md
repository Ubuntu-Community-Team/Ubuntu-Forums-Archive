---
title: "need a x11vnc viewer"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by klein de usa on 2009-10-28
hi 
i have an old computer i'm using to experiment on, i installed puppy-4.3.1 and x11vncxerver and configured it, 

now i'm having trouble connecting to it with ubuntu 8.04.3.this is over a lan i do have a router but i'm not going over the internet.

i tryed applications> internet> remote desk top viewer but it came back with an error (connection to host "xxx.xxx.1.xxx:0:5900" was closed)

i tryed to install tightvnc-1.3.10_unixsrc but it comes up with a make error even though some one installed it on ubuntu before.


is there a good how to ? step by step i can follow?


i installed puppy-4.3.1 to a usb drive, installed x11vnc_server-0.9.4b.pet, i'm going to try to install samba too, then hopefully use ptl1 to start and stop my usb hdd's so they aren't spinning all the time.  so if everything works out well i will vnc into puppy spin up the hdd i need then mount it and use samba to move the files i need over my network i only need the hdd's for storage.

in order to get ubuntu 8.04.3 to connect to puppy on the ubuntu side, in terminal type vncviewer then it ask you for the server in a little box put in the server address xxx.xxx.1.xxx:0 hit inter then it will ask you for a password then hit enter 

the server adress and password comes from the set up in puppy when vncserver is set up

---

### Post by sync on 2009-10-28
Is this on a local network or over the internet.
If connecting over the internet, check that the port is forwarded to the specific machine from your router.
If on a local network, check that the service is running on that specific port.  Normally, the server will open the connection for display :1, meaning that the port should end with 1 instead of 0.

edit: in your case, it looks like you may have entered the address wrong.  try xxx.xxx.1.xxx:5901.

---

### Post by klein de usa on 2009-10-28
hi
the vncserver in puppy says that the address is xxx.xxx.1.xxx:0 on port 5900

---

### Post by sync on 2009-10-28
> **klein de usa said:**
> hi
the vncserver in puppy says that the address is xxx.xxx.1.xxx:0 on port 5900

hm.  the :0 refers to the display, however the :5900 is used to refer to the port, so instead, try ```
xxx.xxx.1.xxx:5900
```, let me know if that works.

---

### Post by klein de usa on 2009-10-28
i tryed two ubuntu 8.04.3 computers set one up to be viewed . when i go to the other ubuntu computer to view the first one i can find the computer but it will not let me connect to it. ubuntu doesn't see the puppy computer at all when you hit connect then find.

---

### Post by klein de usa on 2009-10-28
sync

i tryed that and even tryed the computers name and still the same thing something isn't right in ubuntu because i can't get two ubuntu computer to connect either

---

### Post by klein de usa on 2009-10-28
sync

ok i got it figured out for puppy, in terminal you have to type vncviewer then the server address witch was xxx.xxx.1.xxx:0 then the password and it worked.

but it would not work for the other ubuntu computer so that is still broke the command should be in terminal vncviewer lg1:0 but the terminal hangs right there

---

### Post by klein de usa on 2009-10-28
thank sync

---

