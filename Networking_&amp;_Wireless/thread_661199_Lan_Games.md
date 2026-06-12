---
title: "Lan Games"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by Stoodle on 2008-01-07
I'm having a problem networking games. I don't know what's wrong, but apparently my network (for Windows) wasn't completely set up when my grandpa did it (he's decently knowledgeable about computers, but not Linux). To fix this, I've been working on my own network with Samba but it's still not done I think. Anyway, I wanted to use this Linux-box to LAN two of my other computers and play Command and Conquer. Sadly, It's still not working. I had them both logged in. What's wrong?

---

### Post by sauronsmatrix on 2008-01-18
I know Lan play is perfect in 7.04, but when I upgraded to 7.10 it stopped working.

---

### Post by mikedep333 on 2008-01-18
I'm not quite sure what you are asking.

Are you trying to run a LAN game of C&C where 2 of the players are on Windows PCs and one player is on Linux using Wine? This would assume that you have a switch/hub/wireless access point (or a router with those things built in) connecting the computers. LAN games may not be possible given how old C&C is. You would be best off making sure those other computers can play with eachother then working on getting the Ubuntu box going.

Or,

Are you asking about having the Linux computer handle the traffic between the two PCs? If the Linux box has 2 wired networks cards, you can do a network bridge. It should work. If this computer is connecting them with a VPN, it may not be able to work.

BTW: Samba has nothing to do with connecting games for network play.

---

### Post by sauronsmatrix on 2008-01-19
I'm lanning Warcraft III massively in a school dorm. Everyone else has windows, but i have ubuntu.

they can all connect, and so can I only when I boot into XP. When I use ubuntu, I can sometimes see games, but can never get in for some reason.

---

### Post by Ardrias on 2008-01-19
You could try using Hamachi perhaps. I've not run WC3 in Wine (or Windows for that matter) so can't say anything about how it works. Have you tried other games?

---

### Post by Stoodle on 2008-01-19
Well, the networking at my house is crappy. Computers can't even see each other, with the exception being when it's from linux to windows. I've tried directly connecting computers with ethernet and it didn't work so I decided that maybe I could get them to access each other with linux as the server. My computers are both connected to a router. I've only gotten my uncle's desktop computer and my Winbox to connect which is strange. However, it's very inconvient to have him bring it over whenever I want to LAN.

So basically what I'm trying to say is that yes, I'm trying to use my linux box to handle the network traffic unless there's been something I've been missing with Windows.

We're trying to play Command and Conquer Generals: Zero Hour so it should be able to play.

---

### Post by sauronsmatrix on 2008-01-19
no i haven't

but the thing is that WC3 worked perfectly fine before when i had 7.04, but when I upgraded, everything stopped working.

---

### Post by mikedep333 on 2008-01-19
> **Stoodle said:**
> Well, the networking at my house is crappy. Computers can't even see each other, with the exception being when it's from linux to windows. I've tried directly connecting computers with ethernet and it didn't work so I decided that maybe I could get them to access each other with linux as the server. My computers are both connected to a router. I've only gotten my uncle's desktop computer and my Winbox to connect which is strange. However, it's very inconvient to have him bring it over whenever I want to LAN.

So basically what I'm trying to say is that yes, I'm trying to use my linux box to handle the network traffic unless there's been something I've been missing with Windows.

We're trying to play Command and Conquer Generals: Zero Hour so it should be able to play.

First of all, thank you for specifying that you are attempting to play c&c generals zero hour rather than c&c (tiberium dawn) (1995.)

I am still a little bit confused though.

So normally you have your ubuntu box and your windows box connected to eachother through a router w/ a 4 port switch built-in. When your uncle comes over, his computer is similarly connected to the router/switch. You can play a game between his box and your windows box, but you cannot play a game between your linux box and your windows box?

I am still not sure what you mean by handle the network traffic. Are you saying that you want your Linux box to host the game?

Anyway, assuming you are just plugging everything into the router/switch, my suggestion is to see if the computers can ping eachother. On the windows box, you need to find out the IP address of the computer by going to the command prompt and entering "ipconfig". On linux, you bring up the console and type "ifconfig". Once you have the IP address of each computer, type "ping other_comp's_ip_address" (eg.  ping 192.168.1.3) See if each comp can ping eachother successfully (it will say that it received a response if successful.) If not, then you probably have a firewall issues, or your router/switch is interfering (sometimes they separate wireless networks from wired networks.) It could also be that wine is incompatible with generals working well enough to play a LAN game. Also, make sure you have the same version of c&c generals zero hour.

Another thing you can do in c&c generals zero hour is to do a "direct IP" game from the LAN menu. With this, you make one computer host, and then you have the connecting computer enter the IP address of the other one and then connect. This helps with firewall issues often.

---

### Post by mikedep333 on 2008-01-19
> **sauronsmatrix said:**
> no i haven't

but the thing is that WC3 worked perfectly fine before when i had 7.04, but when I upgraded, everything stopped working.

Make sure you don't have a firewall in the way.

Also, don't forget that wine can be very fussy. Frequently new versions of wine break compatibility (or partial compatibility such as for LAN play) with an app/game.

You could try updating wine to a newer version.
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
You could also try backing up your wine C drive (rename ~/.wine/drive_c to ~/.wine/drive_c_old) and then letting wine reinstall  all of its system files and stuff. This is sometimes necessary to ensure things work well after you upgrade wine. Then you would have to reinstall warcraft 3 and everything else. If you want to restore your old wine C drive, remove/rename the new ~/.wine/drive_C and rename ~/.wine/drive_c_old to ~/.wine/drive_c .

---

### Post by Stoodle on 2008-01-19
I have C&C installed on my windows computer and C&C installed on a laptop used by my cousins that stays here at my house. It also runs windows XP. I started the game up, went to network, and the computers don't show up. They are both connected to one router. However, the laptop is wireless. I even plugged an ethernet cable into it and it didn't work. I did direct play and it doesn't work. All I could think was that maybe I could connect both computers to my Linux box and then they'd see each other.

Just tried to ping my windows computer and it didn't work. When I pinged from my desktop to the laptop, it worked. Maybe it's the firewall on the desktop.

---

### Post by bapoumba on 2008-01-21
Moved to Networking after talking with the OP.

---

### Post by Stoodle on 2008-01-28
I think the problem may lie within C&C. I could lan between two computers for Stepmania but I still can't with C&C. It was my windows box and a Powerbook G4.
Is it because one is First Decade (includes C&CG:ZH) and the other is just the game?

---

