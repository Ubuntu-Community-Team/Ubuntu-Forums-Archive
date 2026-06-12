---
title: "wireshark"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by noodles_x on 2006-12-09
When i start capturing in wire shark, it doesn't work.No packets are captured. I visited [http://wiki.wireshark.org/CaptureSetup/CaptureSupport](http://wiki.wireshark.org/CaptureSetup/CaptureSupport).
I don't know have to enable packet socket support?
Help please?
thanks

---

### Post by Malakia on 2006-12-09
That's because its configured into the kernel and mostly likely you are running a ubuntu-kernel instead of a vanilla kernel. It's probably not set in the kernel and thats why it won't work. If you want to you can recompile your kernel and set it that way.
Here is some links  to recompile your kernel. Just to warn  you it could break some things in Ubuntu.  
[http://www.ubuntuforums.com/showthread.php?t=307411&highlight=kernel](http://www.ubuntuforums.com/showthread.php?t=307411&highlight=kernel)
[http://www.ubuntuforums.com/showthread.php?t=311158&highlight=kernel](http://www.ubuntuforums.com/showthread.php?t=311158&highlight=kernel)

---

### Post by noodles_x on 2006-12-09
thanks...but how do I set it that way?](*,)

---

### Post by Malakia on 2006-12-09
This should be the path to set it when you are in config menu.

Device Drivers --->
  Networking support --->
    [*] Networking support
    Networking options --->
      <*> Packet socket
      [*]   Packet socket: mmapped IO
      <*> Unix domain sockets

---

