---
title: "Server Address?"
date: 2018-04-20
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2018-04-20
I have a hdd plugged into the usb port of my router. I want to run deja-dup to backup /home, etc. to the networked drive.

When I try to access the device, I'm asked for a Server Address. I don't know it, that is to say, it's not the IP address. Making smb://192.xxx.xxx.x doesn't work.

If you could point me to a howto or tutorial I would be obliged.

I find that the password was all that was needed. Thnx. Sorry you are here.

---

### Post by TheFu on 2018-04-20
Be very careful if you connect storage to a router. Many routers have made that storage available to the internet unintentionally.
[https://routersecurity.org/bugs.php](https://routersecurity.org/bugs.php)  This sort of bug has happened across most router vendors.

It is especially worrisome with backups which contain everything. Should that data be revealed to a "bad actor", or just be found by search engines like [https://www.shodan.io/](https://www.shodan.io/)  ... ouch.

---

### Post by lisati on 2018-04-20
> **Mark_in_Hollywood said:**
> I find that the password was all that was needed. Thnx. Sorry you are here.

If this has solved your problem, please mark this thread "Solved" using the option on the "Thread tools" option.

Side note: please avoid using a mixture of way-out font sizes, it can be hard on those of us whose eyesight isn't as good as it once was.

---

### Post by Mark_in_Hollywood on 2018-04-22
> **TheFu said:**
> Be very careful if you connect storage to a router. Many routers have made that storage available to the internet unintentionally.
[https://routersecurity.org/bugs.php](https://routersecurity.org/bugs.php)  This sort of bug has happened across most router vendors.

It is especially worrisome with backups which contain everything. Should that data be revealed to a "bad actor", or just be found by search engines like [https://www.shodan.io/](https://www.shodan.io/)  ... ouch.


I dunno, I'm running OpenWRT. That's not safe?

---

### Post by TheFu on 2018-04-22
All software has bugs. All software/firmware needs to be patched.

OpenWRT drops support for hardware from time to time. You'll need to be careful and keep track of new releases and noticing when your hardware isn't supported any more. Don't expect to be notified.

But attaching storage to a WAN router just "smells" like a terrible idea, doesn't it?

---

