---
title: "[SOLVED] Trouble acessing windows shares"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by karlsomewhat14 on 2008-10-16
Running Hardy, and XP.
In XP, I'm able to connect to the wired network and browse folders on a machine with a share setup by pulling up run and typing \\computer_name
However, in Hardy, I can't find this machine anywhere. From what I can tell from XP, it's in the MSHOME group, so pulling up networks in Nautilus and browsing to the MSHOME group should show it, but it doesn't. Going directly to smb://mshome/computer_name fails, as does smb://computer_name
I'm perplexed as to why it would be showing up in XP, but Ubuntu can't connect to it at all.

Any help or insights would be greatly appreciated.

---

### Post by cariboo on 2008-10-16
Can you ping the XP computer from the Ubuntu computer? Have you added an ip alias in /etc/host for your xp computer. It should look something like this:

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	intrepid
192.168.1.200	willy
192.168.1.202	minibuntu
192.168.1.1	router
```

Also a problem might be that Ubuntu defaults to WORKGROUP for a work group name. To change the work group name in Ubuntu you will need to install samba and edit /etc/samba/smb.conf. You will also need samba to enable your XP computer to see the Linux  computer on the network.

Jim

---

### Post by karlsomewhat14 on 2008-10-30
Sorry for the delay...

More details on the issue: The computer I'm trying to connect to is not mine. I'm not sure who owns the computer, or what the internal IP address is. All I know is that someone on my college campus' network owns it.

The computer is somewhat-visible to windows machines (have Vista running on my laptop now, and am able to connect to the computer using it). However, it doesn't show up in the main network window, only in the sidebar view of the network devices, and only in Windows. The only way to connect to it is if you know it's there, or if you use this view in Windows.

However, in Ubuntu (Hardy), the same laptop as the one running Vista, connected to the same network, in the same port, cannot access this other computer. It doesn't show up in the networking window, not under any sub-options of Network, and knowing the name/workgroup of the computer won't allow access to it either.


Any clues why a computer would be visible only to Windows machines but not Ubuntu? And could Samba/smbf possibly fix this? (If Samba/smbf can fix it, please link to a very thorough guide on setting them up - I've tried and failed, numerous times)

---

### Post by karlsomewhat14 on 2008-11-01
Also, upgraded to Ibex, still can't see the other computer.

Help please.

---

### Post by karlsomewhat14 on 2008-11-08
As per a friend's suggestion, I tried pinging the computer to get its IP.
I got a message that it's an unknown host =/

More suggestions would be nice.

---

### Post by HereInOz on 2008-11-08
It is probable that you are running into the problem that *nix systems don't always work well with Windows netbios names.  

My guess is that if you were able to get the IP address, possibly by pinging it by netbios name from windows, then record the IP address thus returned, and use that, then you will be able to connect to it using the "connect to server" function, but perhaps not using the "network" function. 

Good luck.

---

### Post by karlsomewhat14 on 2008-11-09
Thanks for the tip, HereInOz, I'll make sure and check it out next time I'm in Windows and the computer will show up. :D
Maintenance on the network is disrupting things all over campus, so I can't test it out tonight, unfortunately.

---

### Post by lolwhites on 2008-11-09
Having the same problem. The Windows computers on my home network can see my shared folders OK, but I can't see the Windows ones.

---

### Post by karlsomewhat14 on 2008-11-10
Nice, booted up windows and pinged the computer, got the IP address, and I can now connect :D
Only problem seems to be that everything is suddenly password protected on the mystery computer :(

Infinite thanks to HereInOz

---

