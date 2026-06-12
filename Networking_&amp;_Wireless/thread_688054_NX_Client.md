---
title: "NX Client"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by kob0724 on 2008-02-05
I seem to be having some issues with my NX client. When I try to log into my schools nx server everything authenticates just fine but it hangs at "Established the display connection". Then it says session failed and the details of the message are this:
[code]
NXPROXY - Version 3.1.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '8215'.
Session: Starting session at 'Mon Feb  4 22:58:24 2008'.
Warning: Connected to remote version 2.1.0 with local version 3.1.0.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using image streaming parameters 50/128/1024KB/6144/768.
Info: Using image cache parameters 1/1/65536KB.
Info: Using pack method '16m-rle-9' with session 'unix-kde'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':1.0'.
Session: Session started at 'Mon Feb  4 22:58:24 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Mon Feb  4 22:59:25 2008'.
Info: Waiting the cleanup timeout to complete.
Warning: Parent process appears to be dead. Exiting watchdog.
[code]

The weird thing is that I can ssh into my schools nx server just fine. Any body have any ideas as to what might be going on?

System Specs:
Gutsy Gibbon 7.10
AMD 3500+ 64bit
Radeon X1600XT
Biostar TForce4 Mobo
1 Gig of Corsair Valueselect ram
120 Gig western Digital Hard Drive

---

### Post by Gerard Barberi on 2008-02-05
Did you have encryption disabled?  I have my NX server set up to not allow unencrypted connections.  Your school may be doing the same thing.

---

### Post by kob0724 on 2008-02-05
No, I have encryption enabled. I know I have the correct key because I copied and pasted it off of my schools secure website.

---

### Post by Gerard Barberi on 2008-02-05
Sorry, I don't know what's causing the disconnection.  Try NoMachine's support forums, [here]("http://www.nomachine.com/tr/search.php?search_adv=1&src=1&pattern=Parent+process+appears+to+be+dead").
 
Also, I don't think you're SSHing into the NX server.  The server is separate from the SSH server, but listens on the same port.

---

### Post by ccfiel on 2008-02-13
i have the same problem. i can connect to other dsl but in my house i can not connect to my freenx server. any tips? this is the error


NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '8131'.
Session: Starting session at 'Wed Feb 13 19:54:27 2008'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-desktop'. Assuming agent session.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'unix-desktop'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: Using cache file '/home/ian/.nx/cache-unix-desktop/S-5A43AC9354116A6767C89EDAD1A37999'.
Info: Forwarding X11 connections to display ':0.0'.
Info: Listening to font server connections on port '11001'.
Session: Session started at 'Wed Feb 13 19:54:29 2008'.
Session: Terminating session at 'Wed Feb 13 19:54:30 2008'.
Info: Waiting the cleanup timeout to complete.
Warning: Parent process appears to be dead. Exiting watchdog.
Warning: Parent process appears to be dead. Exiting keeper.

---

