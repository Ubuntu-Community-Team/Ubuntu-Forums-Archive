---
title: "No Network Connection"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by sudeepk on 2008-12-16
I have installed ubuntu 8.10, it seem my internet connection is not working. I have dual boot with windows and internet is just working fine in windows.My ISP did not provied any IP address or subnet mask or DNS server.SO any one can u please help me out.

---

### Post by Yardarm on 2008-12-16
Is it wired or wireless?  What is the output of ifconfig?

---

### Post by shifty_powers on 2008-12-16
are you using wireless or wired connection?

what does netowrk manager tell you?

---

### Post by sudeepk on 2008-12-16
I am using wired netwrok connection.
ts showing ip as 192.168.0.12 and subnet mask as 255.255.255.0

---

### Post by Yardarm on 2008-12-16
So you're getting your IP from your router I take it.  Can you ping any sites?  Is your DNS working?

Try typing:
> dig ubuntuforums.org
to test DNS

---

### Post by sudeepk on 2008-12-16
no i cannt ping any sites and my dns is not working. currently i am using windows

---

### Post by Yardarm on 2008-12-16
So is your 192.168.0.12 address in Windows?  If you run ifconfig in ubuntu it should tell you if your ethernet card is working (it will show up as eth0) and if you're getting an IP address.

If eth0 doesn't show up in ifconfig can you try running lspci to see what kind of ethernet card you have?

---

### Post by Law506 on 2008-12-16
2 things you might want to check.

1. Quick simple thing to check as well, did this my first time.

Up in the corner where it shows the network icon, left click on it and it should drop down a menu and if I am correct, you should see something like Auto eth0.  If there isn't a dot next to it then that means it isn't selected and it won't connect.

Try clicking it and see what happens.

Of course if you got that IP from Ubuntu then this is irrelevant.

2. Another thing to check, this also happened to me.

On your windows side go to Device Manager and find your network card and right click and go to properties.  Go over to the Advanced Tab and you should see a selection for Wake On Settings in the Properties box.  To the side of it you should see a drop down menu and if this is disabled you need to change it to one of the other selections.  I am at work right now and my XP computer is set to "Wake On Magic & Directed".  I dual boot at my house which is turned off.

Hopefully some of this helps.

---

### Post by eraker on 2008-12-16
> **Yardarm said:**
> So is your 192.168.0.12 address in Windows?  If you run ifconfig in ubuntu it should tell you if your ethernet card is working (it will show up as eth0) and if you're getting an IP address.

If eth0 doesn't show up in ifconfig can you try running lspci to see what kind of ethernet card you have?

^I'd try this stuff first. Here's the networking checklist I always go through:
1. ifconfig
2. If there is eth0 and lo output, edit/check /etc/network/interfaces
3. Ping the router: ```
ping -c3 192.168.1.0
```
4. Run ```
/etc/init.d/networking --force-reload
``` (or stop and then start instead of --force-reload) and check for errors
5. ping somewhere else: ```
ping -c3 www.google.com
```

If no eth0 and lo output, check lspci and figure out why the card's not working.

---

### Post by albinootje on 2008-12-16
> **eraker said:**
> 
3. Ping the router: [code]ping -c3 192.168.1.0

In this case that would be  : ping -c3 192.168.0.1

---

