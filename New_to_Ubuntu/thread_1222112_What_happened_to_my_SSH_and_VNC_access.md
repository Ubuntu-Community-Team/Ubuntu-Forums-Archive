---
title: "What happened to my SSH and VNC access"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by tsnow257 on 2009-07-24
Relatively new to Ubuntu and but a proficient mac user with a Ubuntu box to play with:

Here is my problem, I would like to use Ubuntu 9.04 (desktop) on a headless box stashed away someplace basically as a linux project. In order to do this I need SSH and VNC access to the box from other computers (iMac and Powebook) on my LAN. (i'm not concerned about port forwarding from the WAN to get into this box yet)

I set up Ubuntu and got it on my network painlessly and even got both SSH and VNC running well, I was happy. The next morning I woke up and the Ubuntu box had disappeared from my screen sharing bonjor list and all connection attempts failed. I tried ssh and that connection failed. What happened overnight causing this to happen?

This has happened two days in a row now, the first time I restarted the box and everything worked again, however since this is looking like a daily occurance, I would rather solve the problem than restart my box each morning.

I have openssh installed and it is running, port 22 is open (as far as I can tell) if I go hook up a monitor and keyboard i can ssh localhost and that appears to work. Insights into and solutions to this issue would be greatly appreciated.

---

### Post by Hospadar on 2009-07-24
I don't know what would cause this behavior, but try hooking up a monitor and keys to the server box so you can attempt to diagnose the problem after a failure has occured.  Did the machine crash? is ssh still running? is the network connection still good? etc, etc.

---

### Post by tsnow257 on 2009-07-24
Ok, so I fixed the SSH problem using iptables however i am still having vnc issues, any suggestions are still welcome.

---

### Post by tsnow257 on 2009-07-24
To answer your questions, yes the connection was still good, I can use the box like normal when I hooked a keyboard and mouse up to it, the box is fine and everything behaves normally when I am on the box itself. Something in my iptables was rejecting ssh  which I have fixed, so now it is just the VNC adding another rule to accept port 5900 did not fix the VNC issue though I hear that there are better VNC servers out there than vino, I think I will try that.

---

