---
title: "Speed up FTP transfers"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by k33bz on 2010-09-19
I have a file server at home that I am trying to transfer files (alot of big files, total of over 130 gbs). Is there a way to speed up my transfer, currently it is going to be taking over 28 hours.

---

### Post by CharlesA on 2010-09-19
How fast is it transfering now?

Are you transfering the files over the internet or on yer local network?

---

### Post by k33bz on 2010-09-19
over local network, speed fluctuates between 1.1mb p/sec to 1.4mb p/sec

---

### Post by CharlesA on 2010-09-19
What speed is the network? 10/100 or 10/100/1000?

---

### Post by k33bz on 2010-09-19
> **CharlesA said:**
> What speed is the network? 10/100 or 10/100/1000?
Im not a 100% sure, but I would have to say 10/100

---

### Post by CharlesA on 2010-09-19
What sort of devices are you transfering to/from? I don't think the network is the bottleneck for it.

---

### Post by k33bz on 2010-09-19
Coming from a wireless laptop through a Netgear Router Wireless G Router, from the router it is ethernet cable to server.


I was thinking since it is a local connection it would be faster than this, would I be able to speed it up if I connected laptop directly (via ethernet) to the router?

---

### Post by rev0lv3r on 2010-09-19
> **k33bz said:**
> Coming from a wireless laptop through a Netgear Router Wireless G Router, from the router it is ethernet cable to server.


I was thinking since it is a local connection it would be faster than this, would I be able to speed it up if I connected laptop directly (via ethernet) to the router?

If you are doing it wireless it'll be maximum 54mbit. Theoretical. Real world is maybe 1/3rd of that. 

So 54/8 = 6.75mbytes/sec
1/3rd of that is about 2.5mb/s, so maybe you're pretty far from your router

If you did wired 10/100 that's 100mbit / 8 = 12mb/s, You'll get maybe 80% of that, so 10mb/s or so.

---

### Post by k33bz on 2010-09-19
> **rev0lv3r said:**
> If you are doing it wireless it'll be maximum 54mbit. Theoretical. Real world is maybe 1/3rd of that. 

So 54/8 = 6.75mbytes/sec
1/3rd of that is about 2.5mb/s, so maybe you're pretty far from your router

If you did wired 10/100 that's 100mbit / 8 = 12mb/s, You'll get maybe 80% of that, so 10mb/s or so.

actually I am literally 2 feet from router, however I do have things in between my laptop and router (monitor, office supplies, etc) fluctuates between 94% to 100% connection rate.

---

### Post by k33bz on 2010-09-19
> **rev0lv3r said:**
> If you are doing it wireless it'll be maximum 54mbit. Theoretical. Real world is maybe 1/3rd of that. 

So 54/8 = 6.75mbytes/sec
1/3rd of that is about 2.5mb/s, so maybe you're pretty far from your router

If you did wired 10/100 that's 100mbit / 8 = 12mb/s, You'll get maybe 80% of that, so 10mb/s or so.

well I wish I was getting that, I now have it plugged (the laptop) directly to the router. I am not getting 10mb/sec. I am getting more than I was with just wireless, 2.5mb/sec now. 

Oh well at least it is twice as fast now.

---

### Post by rev0lv3r on 2010-09-19
Everything is wired?

---

### Post by k33bz on 2010-09-19
> **rev0lv3r said:**
> Everything is wired?

ya everything was wired.

---

### Post by rev0lv3r on 2010-09-19
sftp or regular ftp?

you might want to check if you are in full 100 duplex mode and what not

are both ubuntu?

---

### Post by k33bz on 2010-09-19
> **rev0lv3r said:**
> sftp or regular ftp?

you might want to check if you are in full 100 duplex mode and what not

are both ubuntu?

sftp

how do I check to see if in full 100 duplex mode?

Server is Ubuntu 10.04 (no gui what so ever, and low amount of resources being utilized, how ever the RAM is low 256, cpu 2.6Ghz) If any of that matters.

Laptop is also Ubuntu 10.04

---

### Post by 0004tom on 2010-09-19
What kind of Wireless card do you have on the laptop?

---

### Post by k33bz on 2010-09-19
> **0004tom said:**
> What kind of Wireless card do you have on the laptop?

Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by rev0lv3r on 2010-09-19
> **k33bz said:**
> sftp

how do I check to see if in full 100 duplex mode?

Server is Ubuntu 10.04 (no gui what so ever, and low amount of resources being utilized, how ever the RAM is low 256, cpu 2.6Ghz) If any of that matters.

Laptop is also Ubuntu 10.04

i think sftp is the problem, that's ssh ftp, so first it is encrypting or whatever

if both machines are ubuntu i suggest rsync, it's brilliant and will work very nicely for your huge amount of files.

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)
[http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)
[http://ss64.com/bash/rsync.html](http://ss64.com/bash/rsync.html)

---

### Post by k33bz on 2010-09-19
> **rev0lv3r said:**
> i think sftp is the problem, that's ssh ftp, so first it is encrypting or whatever

if both machines are ubuntu i suggest rsync, it's brilliant and will work very nicely for your huge amount of files.

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)
[http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)
[http://ss64.com/bash/rsync.html](http://ss64.com/bash/rsync.html)

Perfect, I will try that next time I have a large amount of files. Probable wont be till I upgrade my server.

---

### Post by k33bz on 2010-09-19
What port does rsync use?

---

### Post by rev0lv3r on 2010-09-19
> **k33bz said:**
> What port does rsync use?

You shouldn't have to mess around with ports

---

### Post by k33bz on 2010-09-19
> **rev0lv3r said:**
> You shouldn't have to mess around with ports

In my router I would need to so I could port forward it.

---

### Post by CharlesA on 2010-09-19
> **k33bz said:**
> In my router I would need to so I could port forward it.
rsync uses the same port as ssh.

---

### Post by k33bz on 2010-09-19
> **CharlesA said:**
> rsync uses the same port as ssh.

ok, then that is already taken care of. Thanks

---

### Post by rev0lv3r on 2010-09-19
> **k33bz said:**
> In my router I would need to so I could port forward it.

if you are transferring from internal network to internal network (within network) you dont need to port forward
thats for nat (outside to inside)

---

### Post by k33bz on 2010-09-19
> **rev0lv3r said:**
> if you are transferring from internal network to internal network (within network) you dont need to port forward
thats for nat (outside to inside)

True, but when I am away from home I will need to port forward. Which is what I am doing to my server. Making sure everything is set up to work within local network and outside the network. As well as being secure. I am almost done with setting up all the databases and configuring other little things. I believe I am done with port forwarding now (unless I will need it for Grisbi and streaming Audacious). Then I will be working on the major bulk of security.

---

### Post by jkurtisr32 on 2010-09-19
> **rev0lv3r said:**
> if both machines are ubuntu i suggest rsync, it's brilliant and will work very nicely for your huge amount of files.

If you feel like giving it a try, I would strongly recommend using Unison. It uses ssh like Rsync, but it can sync in two directions. I use it to sync my laptop and my desktop through my server. It will automatically detect and resolve any discrepancies or file changes between the desktops. Pretty cool stuff.

-Kurt

---

### Post by k33bz on 2010-09-19
> **jkurtisr32 said:**
> If you feel like giving it a try, I would strongly recommend using Unison. It uses ssh like Rsync, but it can sync in two directions. I use it to sync my laptop and my desktop through my server. It will automatically detect and resolve any discrepancies or file changes between the desktops. Pretty cool stuff.

-Kurt
Thanks for the info, however I think I will pass on that. To me, and please correct me if I am wrong, but it seems that it is used to keep two devices similar VIA 3rd party (the server). Thats not what I am looking for.

---

### Post by jkurtisr32 on 2010-09-19
> **k33bz said:**
> Thanks for the info, however I think I will pass on that. To me, and please correct me if I am wrong, but it seems that it is used to keep two devices similar VIA 3rd party (the server). Thats not what I am looking for.

That is just the application that I use the program for. It does use some really smart transferring methods, and it's been pretty fast for my means. I agree that the build in file transfer methods are slow.

If I were to use Unison to transfer large files between a server and a client, I would designate a transfer directory on both machines, then copy whatever I wanted offloaded from the machine into the directory. When you told it to sync, the new/latest files both directories would be copied to the other machines.

I just like programs with versatility, and I like that this one can be bi-directional. I use Rsync for backups, because I will do a backup OR a restore, not a sync.

Good luck with whichever you choose. Both will work.

-Kurt

---

