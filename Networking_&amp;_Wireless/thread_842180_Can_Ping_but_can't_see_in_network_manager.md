---
title: "Can Ping but can't see in network manager"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by cdcool1 on 2008-06-27
I have my ubuntu 64 box (hardy heron) connected to my router and a vista 64 box (ultimate) also connected to my router.  Both computers have access to the internet, both can configure the router, both can ping each other and I can even remote desktop from my ubuntu box to my vista box.

What I can't do however is see my vista box from network manager on ubuntu.  I've tried assigning them both to WORKGROUP, and in the network window, it does show windows network, and within that it does show workgroup, but it only has my ubuntu box in that network.

File sharing is turned on on my vista box and i have a drive shared on it and it was all working up until yesterday but now its stopped and i'm unsure why.

Any ideas or anything I should try?

Thanks
Craig

---

### Post by cpetercarter on 2008-06-27
This may be worth a try. I had a similar problem getting my computer to see a wireless printer, and it worked in that case.

System > Administration > Network > Hosts > Unlock 

Enter your passwors and add details of your Vista box's IP address (192.168 something something) and host name.

---

### Post by cdcool1 on 2008-06-27
After restarting my ubuntu box, WORKGROUP has now gone so it must have only been present because of something i'd been trying in that session.  Windows Network is now empty.

cpetercarter, I've just tried that but unfortunately to no avail.

Edit: and now workgroup is back but with just my ubuntu box in.:confused:

---

### Post by cdcool1 on 2008-06-27
Ok, very strange now, if I open terminal and type (192.168.0.2 is the ip address of my vista box)
```
nautilus smb://192.168.0.2
```
then all the shared folders appear, so why doesn't it do this in the network bit??

---

### Post by BlakeM on 2009-01-27
I realise this thread is a bit old...just wondered if you guys figured out why you couldn't see the server in Places>Network. I can also access using

```
sudo nautilus smb://<IP Address>
```

---

