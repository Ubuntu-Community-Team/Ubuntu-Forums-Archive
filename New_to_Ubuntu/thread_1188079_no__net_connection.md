---
title: "no  net connection"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by ahisome on 2009-06-15
:-( hi guys I've just installed ubuntu 9.04. But it's not showing any internet connectivity .I'm connected via LAN .BY the way there is no problem in windows XP (where I'm using LAN driver in XP)...... Help

---

### Post by cmnorton on 2009-06-15
cable or wireless?

Is the Network Manager icon displayed on upper right toolbar?

If not, check Synaptic Package Manager. Is Network Manager installed?

What does /etc/network/interfaces look like?

---

### Post by superprash2003 on 2009-06-15
post output of **ifconfig **from the terminal

---

### Post by Iowan on 2009-06-15
By "LAN", I presume you mean a wired connection. **ifconfig** will reveal much - also include **lshw -C network**.

---

### Post by ahisome on 2009-06-16
i think u have a mejor problem

---

### Post by cmnorton on 2009-06-16
We're asking you to post output from various programs, so we can help you. I am confused as to your last post.

---

### Post by Iowan on 2009-06-16
> **ahisome said:**
> i think u have a mejor problemWould I be correct to assume you may need more guidance as to how to provide the requested information?  Sometimes "we" assume (OK, at least I do) that posting results of **lshw -C network** is simple.

---

