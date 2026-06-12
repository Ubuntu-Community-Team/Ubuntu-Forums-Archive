---
title: "Configuring USB (ext) modem in 8.10"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by didzejevski on 2008-11-07
Hello.

I installed Ubuntu 8.10 (Gnome) (amd64), and since this is my first time, I need some help.

1) I heard of some WvDial tool, but I can't find it anywhere. Does it have a GUI frontend or it is only cmd-line tool? And what GUI dialer should I use? As I said, I am on Gnome.

2) My second problem is next. When I searched net and ubuntu's help, everywhere it says that I need to run: 'system>administration>network' for configuring my modem, but there is nothing like this. Where I can find that 'network' thing? Only options I've found is for proxy, wireless and dsl. But nothing is mentioned about modem(s).

3) My modem is external USB for ISDN, Intracom NetMod. I searched their site, and found some help files for installation on linux, but it is outdated and for X Windows. There isn't a single command that works on my machine. I heard of some module cdc-acm, but I don't know what does it means, and what to do with that.

---
And a little bit of offtopic: when I look at the package manager, I see a bunch of programs that wont install, error it shows is that I am on amd64 platform and it can't run on that platform. Should I better switch to x86? Btw, I have amd64 x2 processor.
---

Regards.

---

### Post by GeorgeVita on 2008-11-16
Hi, after boot, plug your modem to the USB port, wait 30 seconds, open a terminal window (Applications > Accesories > Terminal) and execute **lsusb** (command that lists all usb peripherals).
Then execute (into terminal) the command **wvdialconf** (runs the auto configurator for the wvdial dialler program).

Copy and post here the results.

Note that terminal commands are case sensitive so type exactly the above. Also **wvdial** is a dialler program that runs on a terminal window.

Regards,
George

---

