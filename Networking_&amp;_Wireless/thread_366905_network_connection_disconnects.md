---
title: "network connection disconnects"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by yanqui on 2007-02-21
I have Ubuntu loaded onto an external hard drive, which works great for the most part.  But there are times when it just drops the network connection.  This never happens when I'm using windows, and this is a laptop that it's connected to; point here is that it's not the ethernet hardware causing the problem.  I've never timed it to see how long it stays connected, because it's usually a case of "I've come back from doing something else and the connection is lost."  A reboot clears it up, but I shouldn't have to do that.  It's an indicator that something's amiss.  ACPI is set to off, by the way.

Has anyone ever seen this before?

---

### Post by gradedcheese on 2007-02-21
instead of rebooting, run this in a terminal:

```

sudo /etc/init.d/networking restart

```

My suggestion would be to identify your network card chipset, and then the driver that supports it.  Following that, download and build a newer version of the driver.  It sounds like a driver problem to me...

To see what the chipset is, run "lspci" in the terminal and look for a line starting with "Ethernet Controller"

---

### Post by yanqui on 2007-02-21
> **gradedcheese said:**
> instead of rebooting, run this in a terminal:

```

sudo /etc/init.d/networking restart

```

My suggestion would be to identify your network card chipset, and then the driver that supports it.  Following that, download and build a newer version of the driver.  It sounds like a driver problem to me...

To see what the chipset is, run "lspci" in the terminal and look for a line starting with "Ethernet Controller"

I'll try the networking restart command next time it happens.  

On the other suggestion, you see my bean count; it corresponds pretty close to my experience in linux.  The concept of "download and build" fills me with something like terror.  I'll google it and see if I can find a play-by-play.  Your suggestion seems reasonable, though.  The laptop is quite new, it's possible that the repositories haven't gotten the latest driver yet.

Thanks for the suggestions.

---

### Post by gradedcheese on 2007-02-21
Well, I can help you build the driver, I don't expect you to know how to do that.  However you'll have to post the lspci output here so we can figure out which driver you need.

---

### Post by yanqui on 2007-02-21
That would be great!  I've kind of got a lot on my plate today and won't get to the mechanics of it till at least tomorrow.  To post the lspci output, I figure I'll have to run a command in the terminal--exactly which command?  I'll hook it up tomorrow, run it, and come back to this thread with the results.

---

### Post by gradedcheese on 2007-02-21
Go to Applications->Accessories->Terminal, that brings up the terminal.  To run a command, you type (or paste) it into the window, and then press enter.  So, open the terminal, type "lspci", press Enter, and then copy and paste the output into the post here.  Namely, the line(s) starting with "Ethernet Controller".

---

### Post by yanqui on 2007-02-22
I tried the "restart networking" command, and the return was "no dhcp offers" and the networking didn't restart.  When I rebooted, the networking restarted as it should.

this is the output from the lspci command, regarding the "wired" ethernet controller:

0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

And I appreciate, in advance, your help and patience with me.

---

### Post by yanqui on 2007-02-23
I was afraid this would get buried and gradedcheese wouldn't be able to find it, so I gave it a bump.

---

### Post by gradedcheese on 2007-02-23
Oh, hi.  Please run this:

```

lsmod | grep 8139

```

and post the result.  I want to make sure you're using the "8139too" driver (or similar)

---

### Post by yanqui on 2007-02-27
8139cp                 22528  0
8139too                26880  0
mii                     5888  2 8139cp,8139too

neither of which mean anything to me, but here it is...

---

### Post by yanqui on 2007-02-27
little bump so it doesn't get lost

---

### Post by yanqui on 2007-02-28
little bump again, hoping gradedcheese logs in soon

---

### Post by yanqui on 2007-03-06
gradedcheese, where did you go?

---

