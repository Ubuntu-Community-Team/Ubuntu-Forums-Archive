---
title: "Intermittent wireless with DHCP (OK with static IP)"
date: 2005-04-23
forum: Networking &amp; Wireless
---

### Post by emendelson on 2005-04-23
Here is a baffling problem that I hope someone can help with.

I've installed 5.04 on a Thinkpad T42 with Atheros a/b/g wireless. Except for the one problem I've described here, everything works perfectly out of the box.

Here's the problem:

If I enter a static IP address (plus wep key, gateway, and netmask) in /etc/network/interfaces, then wireless networking works extremely well. The network notification applet icon on the panel at the top (near the clock) shows a steady, strong signal.

However, if I use the Gnome network settings application (Gnome menu: System/Admistration/Networking) to choose between different ESSIDs from the dropdown list in the Configure dialog, and I use DHCP, then the network notificaition icon shows a yellow caution sign ("!" in a triangle) every three seconds (more or less), and the connection is very intermittent.

I've tried using two alternative wireless managers, wicme and gtkwifi, but the same problem occurs with both. I wish I could use gtkwifi, because it is by far the best and fullest-featured network manager I've seen yet for Linux, but it seems to suffer from the same problem.

This doesn't seem to be a wicme or gtkwifi problem, because they have the same problem that the standard Gnome applet has if I use DHCP. Has anyone encountered the same problem, or can anyone suggest a solution?

Many thanks for any help.

---

### Post by ozE on 2005-04-26
Hi.

I can't actually *help* you - all I can do is commiserate!

I was having the same problem - WiFi was **so** unreliable, I was tempted to put XP back on!  [-X 

Then I decided to try using static IP with my WAP, and it's fine! My configuration has been done manually in /etc/network/interfaces

I have a DWL 122 USB adaptor...

The weird thing that I noticed was that ping tests were taking a ridiculous amount of time. The TTL was normal, but the time between attempts seemed excessive...

I was actually thinking of installing ethereal to determine if, for some reason, the DHCP lease was continuously being renewed. The lease period is supposed to be 24 hours.

Of course, installation with an intermittent connection wasn't going to work very well...

Since, at the moment, anyway, my WiFi use is with my own home network, and another at work, I've been able to ensure that I can manually specify an IP.

Using public AP's is a different story, of course.

So, sorry I can't solve it for you, but at least you know it's not just you!

---

### Post by emendelson on 2005-04-26
Thanks for the confirmation! I've been able to get things working the same way: manual entry of the information. Seems to be working fairly well now, but I hope Breezy is better at all this...!

---

### Post by makhand on 2005-04-26
well, this is fine and dandy for you guys, but what about someone that doesnt have the option of getting a static ip? I'm using it at school and cant just get a static ip. Basically, here, we have to use VPN. I use the cisco client. For a while, i didnt have this problem, but now, wireless is just haywire, at least here at school. At home, everything, including DHCP works just fine. 

Well, let me clarify myself, in case someone can help...

Everything worked fine as expected for a while. I could connect through DHCP, then start the VPN client and connect through the vpn. Suddenly, one day I could no longer connect to the vpn. It would just time out, though the little indicator on top showed a strong signal. A weird thing is that it seems like if i start my computer somewhere else, then suspend it and bring it to school, and resume the session, I can get the intermittent connection. This means I connect for a couple minutes. During this time, I reconnect (manually) to the vpn and start using. 2 minutes later, all connection is gone. So i have to re-open the network settings thing, click on the wireless card, go to properties, select one of the available wireless routers/servers, click ok. Then, i reconnect my vpn, typing in passwords and all... and i have another 2 minutes!!! woohoo!  ](*,) 

Sorry for the fuzzy details, i'm doing this from memory. Unfortunately, I'm typing this from my XP partition, because XP works, as expected all the time. 

Can someone please help? I've put so much time into messing with my Ubuntu, getting things to work just right... but i cant use it in this state. I really really dont want to go back to microsoft. Unfortunately, i have no choice at the time. 

mak

---

### Post by makhand on 2005-04-26
I'm back. Pretty quick compared to how long I've been affected by this problem. 

For me, it seems like the problem was Firestarter. It is evil. it broke my wireless. 
Ok, maybe not. It's probably good, I just didnt read up on it. My guess is that when I connected to the vpn, the vpn would intermittantly try to talk back to me but would be blocked by firestarter. So, having gotten rid of it, things seem to work. Lets hope they continue. 


Note to evil and malicious hackers: Please 0\/\/|\| my laptop. It is available for your use in anyway you please.

---

