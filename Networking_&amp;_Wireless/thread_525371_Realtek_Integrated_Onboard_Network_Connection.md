---
title: "Realtek Integrated Onboard Network Connection"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by dESAI on 2007-08-14
Hi All, 

I've just installed my first ever Linux (Ubuntu on a test pc with AMD 1600+ with 256ram and 128 ati gc). But the built in network port is not working - no light on port or router. No internet is a real show stopper for me.

When I run windows, everything is fine. 

I went straight to a Ubuntu chatroom on mIRC to discuss the problem and there was someone else who had the same problem. So i think it's a problem with the Realtek of adapter.

I went to the realtek website, which said that Ubuntu already has the drivers included.

This is really dissapointing. I really want to start moving away from MS, but to fall at the first hurdel like this is really demotivating. I mean - it should just work!

I hope someone can help with this. I want to really sink my teeth into Linux. I'm someone who helps a lot of people with XP PC problems. I would like to one day say 'Yes, Linux is better, I'll install it for you.'

I'm gonna try moving the installed HD to another PC to see if it works in there. I'll let you know how that goes.

THANNKS! :-)

---

### Post by dESAI on 2007-08-14
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100B(L)/RTL8100C(L)/RTL8101L/RTL8139C(L)/RTL8139C(L)+/RTL8139D(L)/RTL8100(L)/RTL8130/RTL8139B(L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100B(L)/RTL8100C(L)/RTL8101L/RTL8139C(L)/RTL8139C(L)+/RTL8139D(L)/RTL8100(L)/RTL8130/RTL8139B(L))

---

### Post by serfczar on 2007-09-24
I know this is an old post, but i'm having troubles with my realtek Realtek RTL8100C

like that guy said, on the website it says it is packaged in the linux kernel, but It isn't working! what should i do?

---

### Post by noob12 on 2007-09-24
The original poster's problem is probably the one addressed in this thread:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)


serfczar:  If that's not your problem (check), you may want to start a new thread with the type of card you have in the title.  You may find it useful to use a USB jump drive to get material on and off until you've got a network connection.  Post the output of these for better diagnostics.

```

lspci -nn

sudo lshw -C network

sudo ethtool eth0

dmesg

```

---

### Post by serfczar on 2007-09-25
> **noob12 said:**
> The original poster's problem is probably the one addressed in this thread:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)


serfczar:  If that's not your problem (check), you may want to start a new thread with the type of card you have in the title.  You may find it useful to use a USB jump drive to get material on and off until you've got a network connection.  Post the output of these for better diagnostics.

```

lspci -nn

sudo lshw -C network

sudo ethtool eth0

dmesg

```


O thx so much, that fixed my problem :D.

---

