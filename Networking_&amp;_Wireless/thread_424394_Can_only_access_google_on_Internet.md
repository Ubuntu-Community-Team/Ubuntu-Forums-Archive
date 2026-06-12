---
title: "Can only access google on Internet"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by meinzy on 2007-04-26
I started working on this problem in the beginners thread (I'm a total newbie).  All the background is located at the following link:

[http://ubuntuforums.org/showthread.php?t=424203](http://ubuntuforums.org/showthread.php?t=424203) 

It seems this is a very deep and mysterious problem.  Hoping to find a networking guru looking for a major challenge.  Please check out included link above so I don't have to try and rehash three pages of help already accomplished.

Please help, this is going on three days of troubleshooting.

---

### Post by lloyd_b on 2007-04-27
I think the poster that suggested trying different MTU values may have been on to something.  At least it's something to try:) 

Open a terminal window.  In this window, type the following:
```
sudo ifconfig eth0 mtu 1400
```
(it'll prompt you for your password)

Then try to reach a site using Firefox ([www.yahoo.com](www.yahoo.com), for example).

If it fails at 1400, try again at 1300, 1200, etc, until you reach 500.

If at any point during this process, Firefox starts working correctly, then we'll have the problem identified, and can start working on a permanent fix.

Lloyd B.

---

### Post by meinzy on 2007-04-27
***WooHoo***...that seems to have done the trick!  It works with a setting of 1400.  Good job and thanks much.

---

### Post by lloyd_b on 2007-04-27
Ok, now for the tough part.  You see, the next time you boot that machine, you're probably going to have the same problem.  So unless you want to manually type that command in every time you boot, we need to sort out how to set that value automatically.

Here's the problem: I don't see any option in the DHCP configuration to manually force a given  MTU value.  I know how to set it for static IP's, but not DHCP.

What I can suggest (in a terminal window)
```
sudo nano /etc/init.d/rc.local
```
And add, as the 2nd line in the script, the command:
```
ifconfig eth0 mtu 1400
```

This probably isn't the "proper" way to handle this situation, but it's the only one I can think of off the top of my head.

Hopefully this will either provide you a permanent fix, or somebody with a better knowledge of DHCP will wander by with info on how to set the MTU via the DHCP configuration...

Lloyd B.

---

### Post by aerofax on 2008-02-25
my problem solve already. my firefox conflict with ipv6

thanks guys..

---

