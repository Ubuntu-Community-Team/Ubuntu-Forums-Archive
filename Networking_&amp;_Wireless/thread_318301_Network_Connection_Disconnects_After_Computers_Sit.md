---
title: "Network Connection Disconnects After Computers Sit Idle"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by justinkoehn on 2006-12-13
I have two computers running Edgy and they are both dropping their network connection after sitting idle for a while. Here are the computers:

Dell Latitude D810 connecting wireless (Dell wireless card)

HP connecting wired (Intel e1000)

I would think it was just a problem with my computer if it wasn't doing it on two different machines connected differently through wired and wireless. 

If i do ifup/ifdown for the interfaces on either machine, it will work fine, i just have to do it after everytime i let the computer sit idle. 

Is there some kind of connection timeout feature added to Edgy? If so i would like to get rid of that one. I dont think Dapper did this.

Any help would be greatly appreciated. Thanks in advance :confused:


I would also like to add that i know it is not my router or dhcp server, as i have tested it with other computers and i dont have this problem, only with Edgy

---

### Post by gtkourounis on 2006-12-13
i had the same problem once, everytime that it would do that i would type this in a terminal and the connection would get reactivated

> sudo dhclient

cant help much more, i am a newbie myself :/

hope it helps :D

---

### Post by cdbackslash on 2006-12-14
I'm having the same problem with a machine I've setup with 6.10 server. I intend for this machine to be a file server so the "timeout" issue is obviously undesirable.

Aside from installing 6.10 the only other thing I've done is install OpenSSH Server. I'm at a stopping point with the server until I can figure what setting needs to be tweaked. I thought it was the NIC so I swapped it out (and did a fresh install) but no luck with the alternate NIC.

Just wanted to let you know that I'm in the same boat and will continue to look for an answer which I'll post if I find it.

"sudo dhclient" does reactivate the connection but it doesn't last long.

---

### Post by cdbackslash on 2006-12-15
I know you stated that your router wasn't an issue but I've got some relief (enough to move forward with my file server installation) by changing the Lease Time from 1 Week to 1 Hour on my D-Link DI-624 which is the DHCP server for my network.

My Windows machines have been operating at 1 Week for quite some time so I didn't give it much thought with the Ubuntu install until I ran the "sudo dhclient" and noticed that the renewal time was a very large number.

Maybe there's a renewal setting on the machine that will override the time it gets from the DHCP server which would make it renew on it's own? Maybe /etc/dhcp3/dhclient.conf is the key file and I just need to educate myself more.

---

### Post by justinkoehn on 2006-12-15
That could be a possibility. 

I also noticed that it is not actually disconnecting from my AP, it just wont open web pages. I still have my IP address i had before, and it is still sending and recieveing packets to and from the AP. 

I just have to ifdown/ifup to get it connected again. Pretty ridiculous sometimes

---

### Post by ghstridr on 2007-01-24
Check the bios settings, there are ones pertaining to the onboard ethernet and when to keep it powered on.  I'm betting that a power-saving mode is being activated for the ethernet.
:guitar:

---

### Post by justinkoehn on 2007-01-24
you know that could be a possibility. i just checked all of the settings and there was one ting that sounds like it could be the case, but i am not sure. It never does it in Windows. Weird stuff...

---

### Post by mking213 on 2007-03-13
Did you ever get any resolution to this? I have an onboard Intel NIC thats doing the same thing.

Mike

:guitar:

---

### Post by justinkoehn on 2007-03-13
I reinstalled Edgy and it works beautifully now. It has not done it since. I am not sure if some update fixed it or what, but it is fine now. Are you on a laptop or a desktop?

---

