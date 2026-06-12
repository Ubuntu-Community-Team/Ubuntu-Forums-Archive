---
title: "hooked up router and now nothing"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by vegasyota94 on 2007-09-20
im running ubuntu feisty , and have a linksys 4 port router.
i hooked up my cable modem to the router, then my puter to the router.. then my other puter(win xp home) to the router.. i cant get either one of them to get the net... I can figure out the windows one later, but the linux one im totally stuck at.. i dont know what to do. when i hook up the router,ubuntu shows me that im wired, but i have no net..
anyone help me out?

---

### Post by Mud.Knee.Havoc on 2007-09-20
What can you ping from each computer?  Anything?

Did you go into the router's user interface and check out all of the settings, just to make sure everything's set up right?

---

### Post by vegasyota94 on 2007-09-20
could u tell me how to get into the routers interface? its been awhile since ive done that..
i cant ping anything...

---

### Post by vegasyota94 on 2007-09-20
ok i got into my router...
i see my 192.168.1.1
and 255.255.255.0

then there is obtain dns auto
obtain an ip auto - connection type used by your ISP

---

### Post by greengolem64 on 2007-09-20
First thing to do is determine what IP address is assigned to your Linux box...

If it is not a 192.168.1.x range IP then you aren't talking to the Linksys if it is out of the box...if it is, then the Linksys is DHCP'ing you ok...you need to log on and see what the router is 'seeing' from the DSL box...

[http://192.168.1.1](http://192.168.1.1) for your URL

When the login box for the Linksys pops up enter

USERNAME (nothing)
PASSWORD admin

Check the "status" tab on the Linksys router...you should see some IP addresses there (depends on what your ISP provider is as to what you'll see) IF no IP's...then you probably aren't talking to the DSL box...'

Grab a cup, and the manual and have a sit and read... :)

MD

---

### Post by vegasyota94 on 2007-09-20
ok, i loged in and under status i have

login- DHCP
LAN - ip address 192.168.1.1
subnet mask - 255.255.255.0
DHCP server - enable

then under wan, i have no ip addy
or subnet
or default gateway
or dns

---

### Post by vegasyota94 on 2007-09-20
oh im on cable modem with the motorola surfboard box... cox cable is who i use

---

### Post by str8line on 2007-09-21
Is it the WinXP machine that is connecting to the internet via the Cable Modem alone?

---

