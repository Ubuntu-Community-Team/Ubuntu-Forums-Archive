---
title: "[SOLVED] Have to run dhclient each time to run internet"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by morty35 on 2008-07-12
In an earlier thread, I was able to get my internet working using:

$ sudo dhclient eth0

  However, I have to use that command every once in a while or whenever I logout or suspend, etc.  I was wondering if there is a way to make the internet work each time I start up ubuntu or log in, instead of having to run the command each time.  It isn't much of a problem, but I would like to not have to do it every time.

---

### Post by NilsE on 2008-07-14
> **morty35 said:**
> In an earlier thread, I was able to get my internet working using:

$ sudo dhclient eth0

  However, I have to use that command every once in a while or whenever I logout or suspend, etc.  I was wondering if there is a way to make the internet work each time I start up ubuntu or log in, instead of having to run the command each time.  It isn't much of a problem, but I would like to not have to do it every time.
I am having exactly the same problem.  Most times I have to do this each time I boot and then suddenly it will work without the dhclient for awhile then start requiring it again.

I look in the logs and see exactly the same messages at startup that I see when I run dhclient so that does not even give me any leads. I have even tried everything that seems close in these forums without luck.

Ironically wireless works flawlessly when I am at home on my wireless router or detect another connection.  It is only when I am on Ethernet that I have to do this.

---

### Post by Iowan on 2008-07-14
Post the **/etc/network/interfaces** - or at least check to see if there is an **auto eth0** line.

---

### Post by NilsE on 2008-07-15
> **Iowan said:**
> Post the **/etc/network/interfaces** - or at least check to see if there is an **auto eth0** line.
I tried that and it did not help.  All I now have in the interfaces file is

auto lo
iface lo inet loopback

Which always worked before 8.04

---

### Post by Iowan on 2008-07-15
The **auto** line *should* "make the internet work each time I start up ubuntu or log in, instead of having to run the command each time." Did you restart networking after adding the line?

---

### Post by NilsE on 2008-07-16
> **Iowan said:**
> The **auto** line *should* "make the internet work each time I start up ubuntu or log in, instead of having to run the command each time." Did you restart networking after adding the line?
Yes, I did.  I also rebooted.  I took the extra auto out and rebooted again and it worked.  That is what makes it difficult to debug since sometimes it works and sometimes it does not.

---

### Post by morty35 on 2008-07-18
here is the content of my interface file:

auto lo
iface lo inet loopback

how do I use an auto eth0?

---

### Post by jayach on 2008-07-18
> **morty35 said:**
> In an earlier thread, I was able to get my internet working using:

$ sudo dhclient eth0

  However, I have to use that command every once in a while or whenever I logout or suspend, etc.  I was wondering if there is a way to make the internet work each time I start up ubuntu or log in, instead of having to run the command each time.  It isn't much of a problem, but I would like to not have to do it every time.

I had this same problem after going to 8.04 from 7.10.  I have a Dell desktop with an intel nic (no wireless).  I ended up resolving it via the gui.  I clicked on 'Manual configuration' via the network icon in the upper right of the desktop.   Unlocked the window, selected properties for 'Wired connection', disabled roaming mode, and finally set it to dhcp.

---

### Post by morty35 on 2008-07-18
That did the trick.  It works when I start it up.  Thanks.

SOLVED

---

### Post by jayach on 2008-07-18
Cool, glad I could help!

---

### Post by jjtstan on 2009-08-31
Could somebody clarify how this thread applies to my situation?  I have the same problem - have to run dhclient every time the machine starts up, but I can't figure out from this thread what changes I should be making to etc/network/interfaces.

I'm running Hardy 8.04 on a Dell.  The etc/network/interfaces file looks like this:

> 
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


auto eth0
iface eth0 inet manual
  

How do I fix this?

Thanks.

---

### Post by abdusamed on 2011-02-24
I have to have unique IP on my network. I can't find 'Manual Configuration' to enable DHCP.

I'm on ubuntu 10.04.1

---

