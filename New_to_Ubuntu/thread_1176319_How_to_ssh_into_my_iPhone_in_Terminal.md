---
title: "How to ssh into my iPhone in Terminal?"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by raziiq on 2009-06-02
Hi there.
I have got an iPhone 3g, how can i ssh into my iPhone using Terminal?

---

### Post by Volt9000 on 2009-06-02
Apparently Nautilus, the built-in Gnome file explorer, supports SSH, so you can access the iPhone by open up the location bar (Ctrl+L) and typing into it

```

sftp://user:password@host

```

---

### Post by raziiq on 2009-06-02
i know i can do it through GUI but i want to know how can i ssh into my iPhone using Terminal commands?

---

### Post by Mornedhel on 2009-06-02
```
ssh username@ip_address
```

---

### Post by raziiq on 2009-06-02
Hey thanks man, that was what i was looking for.

Above command is for Wifi right? What if i want to ssh using my USB cable?

---

### Post by Mornedhel on 2009-06-02
The above command is usable when :

1. Target has an SSH server running
2. Target has a known IP or other means of identifying it on a network
3. Target is reachable from client (you)

I have no idea whether this will work over an USB connection, although I suspect it won't.

---

### Post by Hospadar on 2009-06-02
To my knowlege, you cannot ssh through the usb connection on an iphone.

---

### Post by raziiq on 2009-06-02
thanks for the info, means i cannot ssh into my iPhone using USB right?

---

### Post by Cypher on 2009-06-02
You can SSH into a device through USB, but that requires some additional software that isn't available on the iPhone. So you will only be able to SSH through the WiFi connection.

---

### Post by raziiq on 2009-06-02
oh really, thats some info, can you please tell me what that software is? May be i cant get that software but still it will be a nice info

---

### Post by Cypher on 2009-06-02
Traditionally on Linux, at least, there's a Ethernet-Over-USB gadget driver that makes the USB port behave like an Ethernet port within Linux. So if you were to connect the device to a PC, it shows up as an RNDIS device and you can assign IP addresses and do everyhing Ethernet related.

Pretty sure this scheme won't translate easy to the iPhone OS..:)

---

### Post by hovzio on 2009-06-02
Hi, I was wondering about the usb connection for a long time and found it bothersome not being able to connect with my laptop on the run.. The way I did it was setting up the wifi card for adhoc to create an access point.(laptop) Not all wifi cards can easily do ad-hoc or promisc. I wrote a little script that does this since its bothersome disabling NManager, i[fw]configing.. and so forth. When wifi card is in ad-hoc modus you can connect to your wireless card from your iphone as you would then connect to any router.. an ifconfig will verify that avahi is at work. 

From here you can take it in any direction.. you can login to you iphone connecting to a socket redirect your browser to localhost and the appr. port and from there you can surf the net from your laptop. flash and all work.. if you want i'll post the shell script for an AP and ad-hoc.

---

### Post by timcredible on 2009-06-02
you have to jailbreak it first, then you can do it, you'll have to lookup the username and password, it's the same on all iphones, there's a youtube video about jailbreaking it.

---

### Post by y@w on 2009-06-02
[http://junxian-huang.blogspot.com/2009/02/how-to-ssh-to-iphone.html](http://junxian-huang.blogspot.com/2009/02/how-to-ssh-to-iphone.html)

---

### Post by hovzio on 2009-06-02
> **timcredible said:**
> you have to jailbreak it first, then you can do it, you'll have to lookup the username and password, it's the same on all iphones, there's a youtube video about jailbreaking it.

Very true. the iphone has two users; mobile and root. The default password is alpine. It is wise to change this once one has gained access. Once logged in use < passwd root > to change password. Do the same for user mobile. I also recommend getting bossprefs to toggle your ssh-server. I really don't recommend running it unessesarilly.(if only for batteries sake).

---

### Post by raziiq on 2009-06-02
Thanks for help all of you, i have been using iPhone for almost 9 months now, i know a bit of how to jailbreak n ssh using WINSCP in windows n Cyberduck in Mac, i already did that(Means i have already jailbroken my iphone 8 months back ;)) but the prob is i want to know how to ssh into iphone using Terminal using USB cable.

---

### Post by hovzio on 2009-06-02
> **raziiq said:**
> Thanks for help all of you, i have been using iPhone for almost 9 months now, i know a bit of how to jailbreak n ssh using WINSCP in windows n Cyberduck in Mac, i already did that(Means i have already jailbroken my iphone 8 months back ;)) but the prob is i want to know how to ssh into iphone using Terminal using USB cable.

I have heard rumors of this not being possible with apples OS. Well possible sure.. apple is *very* tight when it comes to its iphone. They go through great leangths to keep things proprietary and are very strickt concering the software that is on the iphone. (hence "jailbreaking") I have even heard rumors of encryption of sorts taking place between your usb cable and itunes. As of know I do not think that it is possible to use your usb cable as an ethernet cable. Like mentioned in my first post, check out ad-hoc.

---

