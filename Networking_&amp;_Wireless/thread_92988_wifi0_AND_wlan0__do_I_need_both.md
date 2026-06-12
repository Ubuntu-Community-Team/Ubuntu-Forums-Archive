---
title: "wifi0 AND wlan0?  do I need both?"
date: 2005-11-20
forum: Networking &amp; Wireless
---

### Post by dolhop on 2005-11-20
I have just installed ubuntu onto my thinkpad, insterted my dlink dwl-650 rev p1 (which I did manage to get working using hostap and WPA, I hope to  post a how-to soon as I know many have still not got it working). and iwconifg/ifconfig shows both wifi0 and wlan0 interfaces?  Do I need both?  is one dependent upon the other?  

Normally I wouldn't care since the networking is satisfactory....my issue is that when I 'standby', I had to add ifdown/up wlan0 in the sleep.sh script - which does work, but upon resume I get a whole whack of errors releated to wifi0:

```

[4296011.706000] wifi0: hfa384x_cmd: entry still in list? (entry=c23f27e0, type=0, res=-1)
[4296011.724000] wifi0: hfa384x_cmd: interrupted; err=-110
[4296011.733000] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fd51, len=6)
[4296013.688000] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[4296013.697000] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff

```

After this repeats on screen (console) about ten times, twenty or so seconds later, I eventually get gnome back and can operate.....

---

### Post by mips on 2005-11-21
Does your Thinkpad not have a built in wireless card ?

---

### Post by dolhop on 2005-11-21
no, it's an X21 - so the PCMCIA is my best option.  USB is only 1.1, so kinda rules out that choice.  After some further reading, I'm wondering whether or not I can use the linux-wlan-ng driver instead of the hostap driver and if that will fare any better?

I'm rather new to linux (more of a bsd guy).  Using lsmod, I don't see any wlan or wifi modules loaded....are they built into the kernel?  Are they actually part of the hostap driver?  If I do use linux-wlan-ng, how do I tell ubuntu to use it instead of hostap?

Thanks for your patience!

---

