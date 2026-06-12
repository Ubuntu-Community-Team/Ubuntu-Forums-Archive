---
title: "No internet via Modem, but yes via router"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by cartisdm on 2009-12-22
I am able to get an internet connection via a wired connection to my router.  However, if I plug the wire directly into my **cable** modem, I can't get a connection.  It may be possible that my **cable **modem is just finicky but I am really concerned because I am about to ship this desktop to my grandmother and she will be connecting to the web via direct connection from the **cable** modem...:confused::confused:

---

### Post by unmole on 2009-12-22
Did you configure the  ppp connection when you plugged the wire directly into your computer ?

---

### Post by cartisdm on 2009-12-23
No I didn't make any changes to the system, it's a fresh install.  I thought PPP had to do with dial-up connections?

---

### Post by unmole on 2009-12-23
My bad, I thought you were routing a dialup to a LAN.

---

### Post by cartisdm on 2009-12-23
> **unmole said:**
> My bad, I thought you were routing a dialup to a LAN.

No worries.  I am confused as to why I wouldn't get a connection though.  Nothing should change between 

Cable Modem ---> Router ----> PC  

-versus-

Cable Modem ----> PC

---

### Post by steveneddy on 2009-12-23
Use the application

Gnome PPP

or try

```
pppoeconf
```

---

### Post by cartisdm on 2009-12-23
not for dial-up....

---

### Post by Some Penguin on 2009-12-23
> **cartisdm said:**
> not for dial-up....

The 'E' in PPPoE stands for 'Ethernet'.  That's why people keep suggesting PPP to you -- it's relevant.

---

### Post by cartisdm on 2009-12-23
> **steveneddy said:**
> Use

```
pppoeconf
```

no such luck.  I'm beginning to think it might be my cable modem.  It's 2am now but I think I will hit up the store in the morning if I don't get anywhere tonight...

---

### Post by cartisdm on 2009-12-23
I just bought a new cable modem in hopes of getting somewhere and I think Ubuntu might be blocking me from doing a connection directly to the Modem via wired connection.

When I plugged the computer into the NEW MODEM before I registered the Mac address of the NEW MODEM with my ISP, it would register that I had an eth0 wired connection (but obviously I couldn't connect to the internet).

After I called my ISP and set up the NEW MODEM with the correct Mac address, my linux desktop tells me there is no wired connection available.  If I take that same cord and plug it into my Windows machine, I get internet just fine.

If I run various LiveCDs w/ the linux desktop directly connected to the NEW MODEM it tells me there is a wired eth0 connection, but I cannot get online or ping anything.

There has to be some sort of firewall or something that is blocking me from connecting directly to the internet via the Modem that I am missing because I am online right now via a wired connection through my ROUTER!

Please help I have to get this computer in the mail TODAY!

---

