---
title: "xp and ubuntu internet sharing."
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by goatmale on 2006-08-27
Kay, so I have a computer running dapper drake and it's connected to a computer running xp via crossover cable.  Windows shows that it is connected over a lan but the internet on the xp does not work.  

can some one help me?

---

### Post by carboto on 2006-08-27
I have a similar problem, but the difference, the internet does not work on dapper drake. I connect my linux to winxp laptop via crossover cable, then enable internet connection sharing. The problem is Ubuntu seems to be unable to get a dynamic ip address. I tried SUSE Linux 10, and it works. Ubuntu should work as well, but I'm very puzzled. Can anyone help?

---

### Post by goatmale on 2006-08-27
huh... that is awfully strange.

---

### Post by funchords on 2006-08-28
> **goatmale said:**
> Kay, so I have a computer running dapper drake and it's connected to a computer running xp via crossover cable.  Windows shows that it is connected over a lan but the internet on the xp does not work.  

So the Ubuntu machine is connected using one NIC card to an XP machine, and using another NIC card to a broadband modem?

If not, please explain the topology.

---

### Post by goatmale on 2006-08-28
there are two nic cards and one crossover cable connected. each in their correspomding computers.. that's a complicated way of saying it.

---

### Post by Iowan on 2006-08-28
> **goatmale said:**
> there are two nic cards and one crossover cable connected. each in their correspomding computers.. that's a complicated way of saying it.Where does the internet connect to this network?

---

### Post by goatmale on 2006-08-29
the ubuntu network is connected by a wusb11 wireless adapter, it uses ndiswrapper

---

### Post by Iowan on 2006-08-29
Just bouncing some ideas off the floor (ie. I don't know what I'm talking about): Does XP need to use Dapper as a gateway?  If Dapper is being used as a router, does it need extra software?

---

### Post by funchords on 2006-08-29
> **goatmale said:**
> the ubuntu network is connected by a wusb11 wireless adapter, it uses ndiswrapper

Aha, good.

[Howto Share Your Internet Connection]("http://www.ubuntuforums.org/showthread.php?t=91370")

---

### Post by goatmale on 2006-08-29
yeah it's good, but the windows xp computer I have connected via crossover does not have internet.

---

### Post by funchords on 2006-08-29
Right.  What that process does is allow you to share the internet access that your Ubuntu box has with the XP box.  At the end, both boxes will share the internet connection.

Was that not what you were trying to accomplish?

---

### Post by goatmale on 2006-08-30
LOL my fault.. I didn't see your link untill the second time I checked it... all I thought you said was "Aha, good."

XD my apologies thank you.

---

### Post by funchords on 2006-08-30
No problem -- good luck!!

---

