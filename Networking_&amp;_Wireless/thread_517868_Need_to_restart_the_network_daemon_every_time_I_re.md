---
title: "Need to restart the network daemon every time I restart my router"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by bharathan100 on 2007-08-05
Hi everybody, I am a 64 bit Ubuntu Fiesty Fawn user. I just made the shift a couple of weeks back.
I was able to get my wireless card up and running in no time and even access the net and my windows network from Ubuntu thanks to a lot of help from the forums. The network has one problem though. If I switch off and switch on my belkin router(Connected to an older PC dual booting XP and 98), I have to restart the  network daemon to reconnect. Unlike windows, the connection is not automatically restored. Can somebody please help me set up the network to reconnect automatically. I use the NetGear WG311v3 wireless card. I used a how to by dkreiger to get it to work(will supply link if needed). Please help this noob!!

---

### Post by bharathan100 on 2007-08-05
Just one more thing, Here is rthe command I used to restart the daemon - 
sudo /etc/init.d/networking restart .

I found it on the forums...

---

### Post by ashvala on 2007-08-05
which router do you use that it requires a restart each time around?
I think you need not switch off the router unless it rains heavily in Chennai!

---

### Post by bharathan100 on 2007-08-05
You are right, the router doesn't ordinarily need to be restarted but what happens is that my family switch off the computer, router et all when they shut down the other machine even when this one is on.The two computers share the internet connection! Then  it has to be restarted and the networking daemon restart has to be done. And besides from a convenience standpoint, I feel that the scan should be automatic, whether or not a user restaarts the router many times or not

---

### Post by bharathan100 on 2007-08-05
Please give me some pointers... Sorry for being such an irritating newbie

---

### Post by bharathan100 on 2007-08-06
I am going to write a shell script or program to automatically detect disconnection inform the user and restart the daemon if the user says yes.I don't know much. If anbody could guide me, I'd appreciate it.

---

