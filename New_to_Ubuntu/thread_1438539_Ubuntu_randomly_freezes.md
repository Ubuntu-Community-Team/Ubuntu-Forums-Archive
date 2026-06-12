---
title: "Ubuntu randomly freezes"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by fly_boy on 2010-03-25
Why does Ubuntu randomly freeze, it happened twice to me last night, and I left my box up and running all night, and when I went back to it this morning, it had frozen again...
 
I end up having to switch of the PC and then restart it in order to get it up and runnig again...
 
Its a bit worrying, beause I was hoping for a setup that I could leave running almost indefinitely with the odd restart!
 
Any ideas?

---

### Post by coffeecat on 2010-03-25
Could be a hardware problem. RAM would be a good bet. And just because you may not get freezes in Windows doesn't rule out a RAM problem. Linux uses RAM differently from Windows and is more likely to find that one bad register.

I have had freezes in Ubuntu from software issues - but only with an alpha release or if I had been doing something unwise. You shouldn't get a freeze from simply leaving it running overnight.

---

### Post by HermanAB on 2010-03-25
Do you have an Nvidia video card?  The latest drivers from Nvidia are unstable.  I am running the VESA driver to avoid this problem.

---

### Post by KIAaze on 2010-03-25
Check the log files in /var/log as well as the kernel ring buffer through dmesg.

Notable log files:
```

/var/log/messages
/var/log/syslog
/var/log/daemon.log
/var/log/debug
/var/log/kern.log
/var/log/dmesg

```

I don't know exactly which are most relevant, but you should at least have a look at them to see if there's any noteworthy error message.

When rebooting after a freeze, check the output of dmesg:
```
dmesg >dmesg.log
```
to store it in dmesg.log

Also, try to find out what kind of freeze it is:
1) Hit ctrl-alt-F1 to switch to a virtual console. If you can log in there, it means that only X is frozen (or gdm/gnome, kdm/KDE, etc)
You should be able to kill gdm or kdm from there without having to reboot.

2) If the [magic sysrq keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key")(try REISUB) still work, it means the kernel is not locked up.

3) If both of the above don't work, you may have a soft or hard kernel lockup.
cf: [http://www.av8n.com/computer/htm/kernel-lockup.htm](http://www.av8n.com/computer/htm/kernel-lockup.htm)

---

