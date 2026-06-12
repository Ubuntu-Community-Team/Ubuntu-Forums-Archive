---
title: "[SOLVED] Wi-Fi not workng on Ubuntu"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by EnergySamus on 2007-12-21
Hello!
I have a Broadcom Wifi controller in my laptop that I had had some issues with(restricted drivers, Broadcom 43xx)
That is now fixed. But I have another issue.
I look at the little wireless icon in Ubuntu, click on it, and select my 128 bit secured router. 
My problem is: it won't connect!
It tells me to enter the password, which I double check.
Then it asks me the password again. On the 3rd try, it stops itself from connecting.
I know that my router is working, I can connect through my other partition (dual-booting laptop).

Here is a funny thing: I recently did the OLPC XO giving program. For anyone who doesn't know what it is, here is the URL: 
[www.laptop.org](www.laptop.org)

It is a rugged laptop running a version of Fedora Linux. When I try to connect to my router from that... It doesn't work either!!!:confused:
Anybody have any idea what is going on? I am using a Netgear router.

Thanks
EnergySamus

---

### Post by TheGreatSage on 2007-12-21
I was having the same kind of problem earlier & I ended up droping the security to none on my router to see if I could connect without a key.

Not a solution by any means, but you **could** try it to see if there are any issues with the type of security you are using. I was unable to use the existing wep key I wa susing for my router.

---

### Post by EnergySamus on 2007-12-21
How do you change the password on a router? This question may sound a bit dumb... But I don't know!!!!!

Thanks
EnergySamus

---

### Post by TheGreatSage on 2007-12-21
I wans't suggesting you change the password, just turn off the security **temporarily** to see if you can connect without having to enter a wep key.

You do it at your own risk, as anyone in range will be able to connect to your network once you have dissable encryption.

You have to login through your browser. 192.168.1.1 <enter>  user name and pw is normally on the side of netgear routers  admin  user  something like that. Once inside you can disable or change your method of encryption to something more secure if you like.

If you change you wep key etc, you will then have to edit the keys on other devices that connect to this router(wiselessly) though...so beware.

---

### Post by EnergySamus on 2007-12-21
So you are saying that I have to enter through my browser?
EnergySamus

---

### Post by CCNA_student on 2007-12-21
To configure the router enter either the IP address 192.168.0.1 or 192.168.1.1. For me it is 192.168.0.1. I hope that this helps.

       Sin Cere,

       CCNA

---

### Post by TheGreatSage on 2007-12-21
Yes mate. 192.168.1.1  hit enter and a login box will pop up. Enter the details from the side of the router.

If you are unsure about doing so, and you share the connection with other, it might not be a good idea to mess with the router.

---

### Post by EnergySamus on 2007-12-21
Got it. Changing the password doesn't do anything, but disabling the security does make it work. Both my laptop and the routered desktop have a full internet security suite, so is it safe to turn off the router's security?

Thanks
EnergySamus

---

### Post by TheGreatSage on 2007-12-21
Its not exactly safe & your neighbours or anyone in reach can simply use your banwidth, or log your internet traffic.

By turning encrytion off you have proven it likely to be something to do with the key.

I changed mine to a format that seemed to suite Ubuntu better as my original key was too shot/long for Ubuntu (weird and someone else will very likely give an answer, as I am very new to linux).

Play around with it, it's not a good idea to leave encryption off.

1 idea.. When you had it turned on and you were asked for your essid key...you typed it in more than once..Try it again and make sure that the other pass/key you are entering isn't the password for thekeyring manager

---

### Post by EnergySamus on 2007-12-21
Can I know what format you use? That might help:lolflag::lolflag::lolflag::lolflag:

Thank you for your time
EnergySamus

---

### Post by TheGreatSage on 2007-12-22
I had to use a 13 character key.

When I tried to type in my existing wep key into the network manager box, the button that says "connect" would stay greyed out with the amount of characters I was using.

It liked 7 and 13 characters, so I changed to a 13 character key.

From what you were saying, you were able to input your key, so it doesn't sound like that is your issue.

---

### Post by EnergySamus on 2007-12-22
Thank you!
I will find a way around it.
As long as my Windows partition's internet works, I'm good.:KS

Thanks
EnrgySamus

---

### Post by EnergySamus on 2007-12-22
Figured it out.
I used a WPA code instead of the normal.
Now it works fine!

Thank you for your help!
EnergySamus:lolflag::lolflag:

---

### Post by TheGreatSage on 2007-12-22
Glad you got it sorted.

:)

---

