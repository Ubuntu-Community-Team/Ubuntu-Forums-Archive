---
title: "ndiswrapper &amp; broadcom4328 help"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by flyingsolo on 2006-11-22
Please help a noob!  Using Edgy on Inspiron core 2 duo with Dell wireless draft n which is Broadcom 4328.  I've used ndiswrapper so far and network manager now sees bcmwl5 present under currently installed windows drivers and says "hardware present: yes" but I haven't a wireless connect yet.

lspci gives me:
0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)

and, dmesg gives a lot of stuff (much of which I really don't understand) including the following which would suggest ndiswrapper isn't working:

[17179619.892000] eth0: no IPv6 routers present
[17179780.108000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179780.128000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179780.128000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
my-laptop kernel: [17179780.10800] ndiswrapper version 1.22 loade (preeempt=no,smp=no]
my-laptop loadndisdriver: loadndisdriver: main (638)version 1.7 doesn't match driver version 1.8
my-laptop kernel: [17179780.12800]ndiswrapper(wrapper_init:129):loadndiswrapper failed

Viewing system log (as suggested above)gives:

my-laptop loadndisdriver: loadndisdriver: main(638): version 1.7 doesn't match driver version 1.8

(that should read-main638; I don't know how the smiley jumped in there and I can't get it out!)

I'm feeling out of my league here but willing to persist but clearly need help.  What should I do next? (by the way, I copied drivers from the Windows partition to ubuntu; drivers were initially downloaded from Dell site)

thank you

---

