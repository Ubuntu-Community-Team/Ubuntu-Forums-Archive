---
title: "Linksys Wireless-B sees networks but won't connect to them"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by CodyZ on 2007-11-26
Hey there, I've got a linksys wireless-B (WPC11 v4) that I'm using on a Toshiba Portege 3110ct laptop.  I'm running Xubuntu 7.10, and I can see my protected wireless network, and when I try to connect it asks for my wep key, so I put it in then it waits and asks for the key again.  It just does this over and over.  If I try to connect to an un-protected network it just says it's trying to connect and never actually does.  What gives, please help!

---

### Post by yarvelling on 2007-11-27
I'm bumping this as I have a similar problem with my Acer 5600 laptop.  Type in the WEP key and it doesn't connect, just asks for the WEP key again!  Windows XP on the same machine connects instantly.....

---

### Post by kevdog on 2007-11-27
What driver are you using?? I would recommend ndiswrapper. Also try connecting via the command line -- see my signature.

---

### Post by CodyZ on 2007-11-27
> **kevdog said:**
> What driver are you using?? I would recommend ndiswrapper. Also try connecting via the command line -- see my signature.

I'm using whatever driver came with the default xubuntu install.  The problem is rather strange because the card worked perfectly when I had 6.10 installed.  Then I upgraded to 7.04 and it was no longer recognized.  Then it got worse when I upgraded to 7.10 and my machine wouldn't boot with the card plugged in, or would freeze if I inserted it after X had loaded.

Now if I boot into a different kernel (2.6.20 I think) it recognizes the card, and displays wireless networks, I just can't successfully connect to any of them.

---

### Post by yarvelling on 2007-11-30
Sorry KevDog; I'm a Ubuntu noob, and didn't 'get' too much of your suggestions.... however, I finally gave up on the wireless, and bought a Devolo Highspeed HomePlug ethernet system. (Makes network through household AC wiring)....works perfectly on my laptop, in eithe Vista or Gutsy partition; best of all, it's just 'on'...no setup needed!  Networking for idiots!  Perfect :)

---

### Post by CodyZ on 2007-12-06
> **kevdog said:**
> What driver are you using?? I would recommend ndiswrapper. Also try connecting via the command line -- see my signature.

I followed the instructions for connecting via the command line, and finally it works!  Thank you so much!  Now will I always have to connect via the command line?  What can I do to get a graphical means of connection back?  Is there a way to automate the connection via command line?  

Also, I'm using a RTL 8180 driver, and I used the commands:

sudo modprobe r818x
sudo modprobe r8187

and r8187 had an error (no surprise, because that's not the driver I have, but I wanted to err on the safe side), and the r818x command was accepted.

I still got connected, and when I went to edit the blacklist there was no blacklist for r818x
I'm using xubuntu, is it maybe in a different location?  Or for some reason isn't necessary?

Thanks so much for your help!

---

