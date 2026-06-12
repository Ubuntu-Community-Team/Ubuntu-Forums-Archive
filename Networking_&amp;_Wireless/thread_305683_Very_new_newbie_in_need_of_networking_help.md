---
title: "Very new newbie in need of networking help"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by donang on 2006-11-23
Very new to linux.  Tried to Fedora but swithched to Ubuntu because it seemed a little more user friendly, but i still cannot do what i need to do.

I have a linksys router connected to my Linux box (eth0)
I have a windows xp box connected to my Linux box (eth1) via crossover cable

I can connect to the internet via my Linux box but i cannot connect to the net with my windows box.  

I have eth0 set with dhcp
i have eth1 set as static with ip 192.168.2.1  maskk of 255.255.255.0  no default gateway set

on windows box i have it set with ip 192.168.2.2 with mask of 255.255.255.0 with gateway set at 192.168.2.1(eth1 of linux box)

i can ping between the 2 machines but cant get windows to connect to net.  i know that i could just go from router to win box, but i  really need the machines to share connection.  Ive been trying to figure this out for 2 weeks.  anyhelp at all will be most appreciative.   Remember that i am a true newbie so you have to be pretty basic because all this is so over my head.

thanks in advances

---

### Post by john_spiral on 2006-11-23
try setting eth1 (192.168.2.1) default gateway as the assigned ip address of eth0. Anyone else?

---

### Post by FrodoB on 2006-11-23
Never done it.  Take a look at this, I think that this is your basic concept:

[http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN](http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN)

---

### Post by FrodoB on 2006-11-23
Is a hub or switch too expensive in this case? 

It makes things a lot easier, if you are new to networking.

---

### Post by donang on 2006-11-23
ok...finally got the connection right...thank you

final problem, how do i add this to the start up script so i won't lose it when i reboot.  Well i know how to add it, but where is the startup script i guess is what i am asking

---

### Post by livestockPimp on 2006-11-23
write a script and save it in /etc/init.d

pico /etc/init.d/(filename here)

code:

#!/bin/sh
(put your here line here or startup code)


after that type at the command prompt
chmod +x (filename)
ln -s /etc/init.d/(your filename) /etc/rcS.d/S99(yourfilename)

and that should be all i think.

---

