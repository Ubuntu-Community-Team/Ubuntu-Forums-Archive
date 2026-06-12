---
title: "How do I use remote desktop?"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by isaacj87 on 2009-12-24
This is something I've never really experimented with before and I was wondering...

How do I use remote desktop? What I want to do is connect to my girlfriend's laptop and help her with something. How do I go about doing that?

Here's our situation. Obviously, we're not on the same network, but I do have her IP address. Secondly, I'm using Ubuntu 9.10 and she's on OpenSUSE 11.2 with KDE. It shouldn't be too hard to connect 2 linux computers together, right?

Could someone give me some help? 

Thanks and happy holidays!

---

### Post by terry_gardener on 2009-12-24
have a look at gitso. 

i have tried it ubuntu to ubuntu and it is really easy. 

[http://code.google.com/p/gitso/]("http://code.google.com/p/gitso/")

---

### Post by bodhi.zazen on 2009-12-24
First, start with an awareness of the security implications. VNC is one of the most common services cracked on these forums.

Second, VNC will be slow.

In order to do this, first you need to enable desktop sharing. You then configure your router to forward port 5900 to your computer.

IMO it is better to use ssh.

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

The other option is FreeNX

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by garryknight on 2009-12-24
If you want to do work on her system but don't actually need access to her desktop itself, the safest way, as people have indicated, is to use ssh. And with the command 'ssh -X her.ip.address.here' you can run X apps (including KDE apps) on her machine with the display showing up on yours.

For example, once you're logged in, you could do 'kwrite &' and kwrite runs on her machine with its graphical output on yours.

Frankly, I think you can work faster and better using a combination of the command line and mc. This would allow you to ssh into her machine, su to root, then run mc to do most of the work, and all without worrying about whether root can access the X display device.

---

### Post by isaacj87 on 2009-12-24
> **garryknight said:**
> If you want to do work on her system but don't actually need access to her desktop itself, the safest way, as people have indicated, is to use ssh. And with the command 'ssh -X her.ip.address.here' you can run X apps (including KDE apps) on her machine with the display showing up on yours.

For example, once you're logged in, you could do 'kwrite &' and kwrite runs on her machine with its graphical output on yours.

Frankly, I think you can work faster and better using a combination of the command line and mc. This would allow you to ssh into her machine, su to root, then run mc to do most of the work, and all without worrying about whether root can access the X display device.

I tried running this command in terminal and it just sits there...Is there something I missing?

---

### Post by terry_gardener on 2009-12-24
for ssh to connect over internet connection she is going to need to port forward to her pc, port 22.

---

### Post by isaacj87 on 2009-12-25
> **terry_gardener said:**
> for ssh to connect over internet connection she is going to need to port forward to her pc, port 22.

Ok, nice. I'll try that thanks :)

---

