---
title: "Unable to make ethernet connect"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by zo3adams on 2007-04-02
Greetings All,

I am trying to setup Ubuntu as a sandbox test server / backup  for a freeBSD system and having some difficulty. The install went fine and all hardware appears to be recognized, but I cannot ping out or get a DHCP ip address.

Steps I've tried:
Setting the appropriate DNS servers, Subnet  Mask, Gateway, DNS Search servers, and a valid static up in the GNOME GUI (Administrator > networking )
The gui reports the eth0 connection is active.

using the pppoeconf tool. It scans and then reports that the "access concentrator of your provider did not respond"  (no other instance of pppoeconf or any app that accesses the hardware is isa running as the error message say to check for.)

the files in etc/network have been modified to our workspace's specific settings,  as recommended in these forums.

I have tried wireless connection from a different Ubuntu machine ( a laptop) and found no problem there, but i don't' have wireless hardware for the desktop server.

Any suggestions to try? I mentioned the freeBSD server because I can access any files there to see what settings i need, on my own I found nothing that helped though.

Thanks for any advice or suggestions!

---

### Post by zo3adams on 2007-04-04
bump.

I found the guide for active directory connection ([https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto) )

but I fail in the first step when i try to ping our AD Server by name. Pinging it by ip address (10.0.0.3) works however (with ubuntu set to static ip.)  

I cannot ping the ubuntu server from another machine though, it times out, which has me confused.

---

