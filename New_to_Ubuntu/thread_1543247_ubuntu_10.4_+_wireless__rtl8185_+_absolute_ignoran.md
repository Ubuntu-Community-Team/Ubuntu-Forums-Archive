---
title: "ubuntu 10.4 + wireless  rtl8185 + absolute ignorance"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by Lanemon on 2010-07-31
Hi all, I m completly new to the linux world. And this is so dificult to me that I m almost having a panic attack.

I ll explain my problem.

Im trying to migrate from windows 7 to Ubuntu 10.4. I ve made a dual boot just in case something went wrong (thnxs God). Installing went fine, but when i try to startup ubuntu computer freezes on the Ubuntu logo with the little moving dots.

After a while I realised that the problem comes from my wireless realtek card  rtl8185, because if i take it out everything goes fine, except of course I lack the internet.

I ve been swiming on this forum for about two hours, I ve found a lot of info about what it seems to be a driver problem??.

Bottom line is, i found some info but i can´t understand it.

is there a step by step fix for this problem?

Thnx a lot.
Im diyng to leave windows shores for once and for all.

PS: Please excuse my bad english and my linux ignorance.

---

### Post by Plumtreed on 2010-07-31
Can you tell us how you are trying to load Ubuntu? Do you have .iso that you have downloaded or are you using a disk from another source.

It is often best to try running on the live CD to see if the hardware works!

---

### Post by Lanemon on 2010-07-31
I ve tried on two ways:

1. booting up from the installed version on my hard drive (dual boot)

2. booting from an usb key

Both ways I ve the same problem Ubuntu freezes at startup.

If i take off the  rtl8185 wifi card, It works fine both ways.

---

### Post by Mr_VeRiTy on 2010-07-31
I also have terrible wireless related problems, your card is obviously not supported, neither is mine (it disconnects every so often) but if you can find a better driver for it than it should work, I have a similar card to you (mine is RTL8187) but I had no luck finding a driver, if you do post a link here plz. 

Long story short, stick with windows until october (when the new ubuntu release comes out) when I hope the problems are fixed.

---

### Post by Lanemon on 2010-07-31
do i need linux drivers? or the ones that im using with windows 7 are fine?
how do i install them?
i cant wait till october i wanna out from windows now!!

---

### Post by Plumtreed on 2010-07-31
Well I guess I should ask if you tried running the live CD and if it worked ok as the live cd.

You may be able to reinstall the card after booting into Ubuntu then initiated ...System>Administration>HardwareDrivers

---

### Post by beew on 2010-07-31
> **Mr_VeRiTy said:**
> I also have terrible wireless related problems, your card is obviously not supported, neither is mine (it disconnects every so often) but if you can find a better driver for it than it should work, I have a similar card to you (mine is RTL8187) but I had no luck finding a driver, if you do post a link here plz. 

Long story short, stick with windows until october (when the new ubuntu release comes out) when I hope the problems are fixed.

Interesting. I have rtl8187 and it works beautifully with both Ubuntu 10.04 and Fedora 13 ,both using the same gnome network manager (Nothing works with wicd on the other hand, wicd keeps dropping off and it doesn't even detect network with an athero card in the other computer, so the network manager is important)

 I installed Ubuntu in a dual boot configuration with XP in  an old Dell D410. The built in network card is a broadcom card and the default Ubuntu driver for that is ipw2200. But you see, the internal card was half dead when I got the computer, it doesn't work with Ubuntu and it didn't work with Windows XP. It was not getting any packit even though XP showed that the connection was "excellent". After posting the question in various forums without avail I bought a USB wireless card for $10 and it works beautifully with XP.:p 

After that I tried to install Ubuntu in a dual boot (I decided to keep XP for testing purpose). When I tested with a live usb and the wireless worked out of the box, networks were detected and as soon as I supplied the key connection was immediate. But after the actual installation wireless no longer work with Ubuntu. 

It was so strange that I couldn't find any solution  in the forums and after a few days I figured it out on my own. :D When plugged in live Ubuntu was basically using the same wireless card as XP,--the broadcom card was diabled in XP. But after the actual installation, Ubuntu did its own thing independent of XP and it automatically used the inetrnal card. It took me a whille to figure out the name of the driver (ipw2200) and how to disable it (editing /etc/modprobe.d/blacklist.conf) and once 

I have blacklisted ipw2200 everything works perfectly. 

Wirelless works without any bad side effect. The driver in use is RTL8187! 

So I think the culprit is probably elsewhere. I don't know if this make sense, perhaps your actual card using with this particular diriver, not the driver alone, that is the problem. I am quite new to all these, but I think the driver and the card are two different things, Linux may use the same driver on many different cards, with some it works with others it doesn't. It is kind of confusing when people often using the word "wireless card" to refer to both the actual card and the driver.


Also, an offshoot of my story is that testing with live usb/CD is very logical but it is not always reliable. I run into an exceptional case in my very first attempt at using Ubuntu. ;)

---

### Post by Lanemon on 2010-08-03
I tried the live usb, is that the same?
The same thing happens. if i ve the wireless card conected sistem freezes on boot, if i havent it doesnt.

---

### Post by RJ12 on 2010-08-03
I had a similar problem to what you had (I have a Realtek RTL8187SE) and I ended up having to use NDISWrapper.


Just my 2Cents

---

### Post by Lanemon on 2010-08-03
is there a tutorial where i can learn to use it?

---

