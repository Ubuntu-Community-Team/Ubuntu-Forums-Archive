---
title: "dell inspiron 1525 and gutsy gibbon: wired connection problem"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by threeonethree on 2008-03-09
my friend just got a dell inspiron 1525 laptop which came preloaded with vista. i told him how linux is secure and he should use linux.. i installed ubuntu GG for him.. everything worked out of the box.. but then he said he cant play his mp3 and video files.. i told him that this is because you dont have the required codecs and you need internet connection for it.. we headed to a local cyber cafe and took out the ethernet cable from one of the computers and booted ubuntu after putting it in.(with the owners consent)..

after that there were two computers on top right corner like normal but when i tried to open google it didnt work.. i checked connection information and it seemed like it didnt get ip address from the router..(0.0.0.0) .. i unchecked roaming mode and enabled dhcp and restarted.. nothin... no ip .. 

i booted vista and it got ip and net started to work .but i still want him to use linux because of its security..

tell me is this a known problem for dell 1525? how do i fix it? i tried searching on google but no luck..

---

### Post by threeonethree on 2008-03-10
is there anyone willing to help me?

---

### Post by threeonethree on 2008-03-11
once more i ask for help!

---

### Post by ocap on 2008-03-18
I have the same problem in an inspiron 1525 with vista, and linux installed. But i still am not sure of the solution:

* The kernel 2.6.24 get an ip from a dhcp server without problems in all places (ubuntu hardy live)
* I had the same problem with debian testing (no ip), and no problem with kernel 2.6.24 from unstable. Also i got it working compiling the sk98lin driver. But i had other problems with debian: no sound, no webcam, no suspend, no wireless, etc. I went back to ubuntu.

* I installed the dvd from dell, an no problems at home with the ethernet card (dhcp without proxy), but again i cannot get an ip from dhcp in my workplace (dhcp server with proxy). I do not know if the problem is the proxy or what. But it is frustrating finding so many problems with a model that comes with ubuntu preinstalled.

---

