---
title: "[SOLVED] Problems with Realtek RTL8168C/8111C"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by Idefix82 on 2008-09-09
I am on the verge of giving up, please help!

My Realtek ethernet card sometimes works and sometimes doesn't. I have a dual boot system with Ubuntu 8.04.1 64bit and with WinXP. More often than not when I start Ubuntu, the ethernet card is not recognised properly by the r8169 driver. The output from lshw says, among other things
product: ILLEGAL VENDOR ID
vendor: ILLEGAL VENDOR ID
...
and no IP address after "configuration:"

What could be the reason? I have read elsewhere that this problem occurs only with dual booting and is usually solved by telling Windows to enable wake-on-lan but it didn't solve the problem for me.

Does anybody have any ideas? Thanks very much in advance!

---

### Post by Idefix82 on 2008-09-09
A small update: the ethernet pretty much never works after I restart Linux even if it worked before the restart. However, it does sometimes work when I had windows running and then restart the computer and boot with linux. Does anybody have any ideas?
Can people confirm that this is definitely just a dual boot issue? (Note that sometimes the ethernet card stops working between linux sessions without me booting with windows inbetween!) If it is for sure a dual boot issue I will consider throwing windows out of the window (haha) forever, so I would be grateful if you can share your experience with the same ethernet card!

---

### Post by Idefix82 on 2008-09-10
Bump. I am sure there are some knowledgeable people out there and I would really greatly appreciate any help I can get.

---

### Post by sam1948 on 2008-09-10
I really not sure i'll help but I found out that when closing one of the OS on the computer _with hibernate_ it might still have _some resources occupied_ in my Comp' it was the sound card

---

### Post by Idefix82 on 2008-09-10
Thanks for the idea but I haven't used the hibernate option on either OS for ages. The thing is that after restarting from windows and booting linux my card works more often than after just switching on the laptop or restarting from linux.

---

### Post by lilmale1 on 2008-09-10
rescue is here, im seriously able to help

i have a rtl8180 and you have to istall the driver by it self on ubuntu

there is alot to do from here. do u know how to use terminal command on ubuntu. 


some people are just lazy on this site and didn't help you but i can help u.

---

### Post by Idefix82 on 2008-09-10
I think I am reasonably happy with using the shell although I do need instructions for lots of things, since I am quite a Linux newbie.

But are you sure that we are talking about the same piece of hardware? Isn't the RTL8180 a wireless lan card? Ironically, I got my wireless card to work but still can't sort out the wired, which is what this thread is about.

---

### Post by Idefix82 on 2008-09-18
Solved it thanks to this:
[http://www.jamesonwilliams.com/hardy-r8168.html]("http://www.jamesonwilliams.com/hardy-r8168.html")

---

### Post by jcpshd on 2009-02-20
OMG!!! Thank you very much for that! It worked for me! :D

My setup:

 lspci | grep Ethernet
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

uname -mro
2.6.22-14-generic i686 GNU/Linux

---

