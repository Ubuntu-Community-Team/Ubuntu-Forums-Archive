---
title: "Linksys wireless wmp54g card won't work..*sobs*"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by tin on 2006-08-21
I'm a complete No0b to Ubuntu, just installed it yesterday.
I installed the ndiswrapper and it has recognised my card, but it won't connect.
I click the activate button and then ok, but when I load it up again it's gone back to being inactive.

:-s Anyone got any advice?

---

### Post by bionnaki on 2006-08-21
you dont need ndiswrapper with that card. what driver does your card use? rt2500?

---

### Post by tin on 2006-08-21
Here is a [link]("http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=text%2Fplain&blobheadervalue2=inline%3B+filename%3Dwmp54g_dr_ver.txt&blobkey=id&blobtable=MungoBlobs&blobwhere=1130828469029&ssbinary=true") to the driver details.
I don't understand it much.. ](*,) 

It couldn't install the driver without it though, it said. :confused:

---

### Post by randell6564 on 2006-08-21
> **tin said:**
> I'm a complete No0b to Ubuntu, just installed it yesterday.
I installed the ndiswrapper and it has recognised my card, but it won't connect.
I click the activate button and then ok, but when I load it up again it's gone back to being inactive.

:-s Anyone got any advice?

Hi!
I think that you might have acted prematurely regarding your linksys.

I have the exact same router as you and I never had to deal with ndiswrapper!

I have one PC in the house, hardwired to the router, and one PC in my garage, using a linksys wusb11 wireless antenna.

When I installed ubuntu, I never had to install any other drivers.  It just worked!

I'm guessing that in your attempt to get online, you messed around with configuring when you did not have to.

---

### Post by tin on 2006-08-22
I started again, re-installed Ubuntu, but it's still exactly the same.
It says "eth0 is not active" even after I've activated it.

I'm really lost... :S

---

### Post by DrMoxie on 2006-08-22
[Check this thread]("http://www.ubuntuforums.org/showthread.php?p=1370820") as I strongly suspect it might fix your problem.

---

### Post by tin on 2006-08-22
I tried what it said... didn't work. Just kept saying "permission denied".
:(  Is it possible the card isn't compatable?

---

### Post by DrMoxie on 2006-08-22
Remember to preface each command with sudo as you need to elevate your rights.

---

### Post by randell6564 on 2006-08-22
> **tin said:**
> I started again, re-installed Ubuntu, but it's still exactly the same.
It says "eth0 is not active" even after I've activated it.

I'm really lost... :S

Are you sure that you want eth0?  If you are wireless, isn't it something like WlanO?  what kind of wireless device are you using?

Are you using a security key and all that?  Are you set as DHCP?

Have you disabled ethernet connection before enabling wireless connection?

These are some issues that can cause problems if you miss them.

---

### Post by bionnaki on 2006-08-23
try this guide: [http://www.ubuntuforums.org/showthread.php?t=241565](http://www.ubuntuforums.org/showthread.php?t=241565)

---

