---
title: "Dell Wireless Problems (help the new guy!)"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by mdvigi7536 on 2007-04-29
Hi.

I just installed Ubuntu on my Dell laptop.  I'm brand spankin' new at this, so be gentle!

Friends have given me instructions on this whole download the driver thing.  I used that ndiswrapper on it, and put the resulting files where they are supposed to go.  I restarted.

Now up in the top, near the clock, is a wireless indicator.  It's picking up my wireless network, along with four others in the area.  I selected my network and entered my password.  The little "connecting" animation went around and around and finally gave up.  It won't let me connect to any of the networks in my neighborhood, not even the ones that don't require a password.

I don't get it...it knows its there but can't connect?  Someone help the new guy!

Love,

--Mike 
P.S.: I have a Dell Inspiron 1150 with a Broadcom BCM4306 Wireless thing [I hear those are evil.].  The wireless works fine on Windows XP--I just checked.

---

### Post by jubilee33 on 2007-04-30
After you installed ndiswrapper and the bcm5.inf, did you do the following to check whether the driver was properly installed?

```
ndiswrapper -l
```

You should see a result like "hardware present, driver loaded".  Otherwise your bcm43xx card hasn't been properly installed yet.

Also, can you post the output for the following:

```
iwconfig
```

```
ifconfig -a
```

---

