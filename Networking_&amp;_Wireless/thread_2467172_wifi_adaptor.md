---
title: "wifi adaptor"
date: 2021-09-17
forum: Networking &amp; Wireless
---

### Post by jgw on 2021-09-17
I am having problems with my wifi.  Its very strange.  I connect, get on the net, and then the wireless starts stopping (for less than a minute) and then starts up again (for between 5 and 15 minutes before it stops working again.  Its not the wifi signal.  I know that because I am writing this, right now, on the same wifi signal with no problem at all.  This tells me that its either my wifi adaptor or my computer.  I have a little connection of adaptors and I have tried them all.  Some connected, some have not.  I just put a new copy of 20.04.3 on a system that needed it.  Its working but oddly and this is the last problem and its driving me nuts.  I have one adaptor which worked better than all the others (connected faster, etc).  So this is the one I am currently using and may also be a source of my problem.  I had bought a new wifi computer adaptor about a month ago.  It was working fine before I put the new system on and now isn't even recognized by the system.  This means, I think, that ubuntu doesn't run with all wifi adaptors.  

Anyway, I would appreciate any thoughts on what is going on here and also anybody's thought on which wifi computer adaptor works best with ubuntu.  Many of the adaptors I have are recognized by the system, for instance, but cam't seem to connect with the network.  

I would appreciate any help.

Thank you.................

---

### Post by jeremy31 on 2021-09-17
Start with [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520) and if that doesn't fix it, see the wireless script link in my signature and post results

---

### Post by jgw on 2021-09-18
Thanks for the reply.  Before I start with the stuff at  [https://ubuntuforums.org/showthread....&#post13614520](https://ubuntuforums.org/showthread....&#post13614520) I have two problems.  The first is checking the router.  Do you know of any programs that can do that for me?  (I'm pretty ignorant when it comes to routers but I can research it if necessary.  I really don't 
understand the code thing.  Here is what I have:

```
greg@movies:~$ sudo iw reg get
\global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)
[code]
```

I then went to a place for country codes.  That one really confused me.  then I just googled for international codes for countries and the us was either 1 or .us (I think).  All in all which code should I use?  (I am a bit ignorant)

Anyway ....................

---

### Post by jeremy31 on 2021-09-18
If in the US use ```
sudo iw reg set US
```

---

### Post by jgw on 2021-09-23
thanks for the replies.

My wifi seems to have fixed itself.  Now my wired is acting up but I think its in the connections to the router.  I will, however, mark this as solved.

---

### Post by jgw on 2021-09-30
I have a collection of WIFI adaptors that do not work Linux.  Then I started searching for adaptors that actually work with Linux and found such in EBAY.  I bought one, it came with a little CD.  I ran the cd and they explained how to make the device work with Linux.  Its a two step deal.  You go out and get a driver and then are given the command to install said driver.  I did that.  Then, for the heck of it, I took one of the adapters that won't work with Linux and gave it a try and, IT WORKED!  I tested a few that didn't work and, now they do!  So, if anybody else has adaptors that won't work under Linux buy yourself one that comes with a little cd to make it work with Linux, install the driver and now your adaptors will work!

I would send the stuff that came with the one that works with Linux but I am not sure that would be legal but you can buy one, with a cd, for around 5 bucks and you will then be able to run the ones that wouldn't.

---

