---
title: "PPP and modem configuration, help please."
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by oliverb on 2007-12-16
I'm just not getting this.

I'm trying to put some kind of PPP connection onto a 7.10 system.

I've looked at my two spare internal modems, one is Connexant, marked RH56D-PCI, the other ESS ES2898S

I also have an external 28800 USR Sportster. I'm trying the external first as I really don't get the install procedure for the internals.

Serial port is dev/ttyS0

I've tried the Network manager and had sporadic squeaks from the modem and had it dial half the number then hang up. The only time I had a connection that way is when I rebooted with it set as default connection, then it dialed up on booting before I'd logged in.

I'm trying gnome-ppp now.

Found it in the application installer. I've set it up. I can now get it to dial up but it seems to stop before connecting.

If I look at the log window it looks like it has connected, I'm seeing wvdial report IP addresses and DNS addresses and funnily enough I found that it was connected but the window doesn't close or go to a "you are now connected" state.

Any clues please? 

Should I stick with Gnome-ppp?
Can I make it Dial-on-demand?
Can I get one of the internal modems working? Using a precompiled binary? Can I install it from the package manager?

I just can't believe I'm making this much of a mess of it?

---

### Post by Bartender on 2007-12-17
> **oliverb said:**
> I just can't believe I'm making this much of a mess of it?

Probably cause you thought it was gonna be easy like in that other OS.  While many parts of Ubuntu are amazing, dial-up is a big ugly sinkhole and not likely to get much better because dial-up is such a dead-end technology.
Take a read thru my [diary]("http://ubuntuforums.org/showthread.php?t=480717") and see if it makes any sense to you.
As afar as I know, the "Network" GUI still doesn't work right.  And apparently GNome-ppp has a bug but I just read a post recently that said there was a patch.  If I could only find that post!

---

### Post by oliverb on 2007-12-22
OK so that project's a bust then. I wanted to "hand down" an old PC as a fully usable system but if I'm having this trouble myself then there's just no way I can pass it on to someone else if the things they want are dial-up internet and email.

Granted I did get some results with Gnome-PPP but I gather it'll never do "connect on demand".

I think I'll just junk it.

---

### Post by Bartender on 2007-12-22
I wouldn't say it's a bust.  With a 56K serial modem and a cooperative ISP you can get it working pretty easily.
And some folks have gotten some winmodems to work.

The frustrating part is what happens after you get dial-up working.  Daily life with Linux means frequent, relatively large, downloads.  Keeping the system up-to-date and trying out new programs is horribly tedious with dial-up.

If there are wi-fi hotspots available to you nearby then a laptop might serve to partially answer the problem.

---

### Post by madjr on 2007-12-22
> **oliverb said:**
> I'm just not getting this.

I'm trying to put some kind of PPP connection onto a 7.10 system.

I've looked at my two spare internal modems, one is Connexant, marked RH56D-PCI, the other ESS ES2898S

I also have an external 28800 USR Sportster. I'm trying the external first as I really don't get the install procedure for the internals.

Serial port is dev/ttyS0

I've tried the Network manager and had sporadic squeaks from the modem and had it dial half the number then hang up. The only time I had a connection that way is when I rebooted with it set as default connection, then it dialed up on booting before I'd logged in.

I'm trying gnome-ppp now.

Found it in the application installer. I've set it up. I can now get it to dial up but it seems to stop before connecting.

If I look at the log window it looks like it has connected, I'm seeing wvdial report IP addresses and DNS addresses and funnily enough I found that it was connected but the window doesn't close or go to a "you are now connected" state.

Any clues please? 

Should I stick with Gnome-ppp?
Can I make it Dial-on-demand?
Can I get one of the internal modems working? Using a precompiled binary? Can I install it from the package manager?

I just can't believe I'm making this much of a mess of it?


bug report here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487)

gnome-ppp patched:
[http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb](http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb)

---

### Post by gwbennett on 2008-01-23
That patch above DOES work for gutsy 32 bit. I use it with m internal sprint evdo modem on my eee. Anyone know how to make the tray icon NOT blink though? I want it in the tray but I don't want it flashing like it's 1997 again.


And WHY has this gnome-ppp update not been packaged and rolled out through udates yet? This tiny bug is due to wvdial's text output haveing been altered. gnome-ppp waits for it to say "connected" and instead now in dumb mode it says "hoping for the best" or some absurdity like that.  But how can a bug persist this long unrepaired in ubuntu??

---

### Post by yellowbread on 2008-01-23
If you want that tray icon to not blink, an easy fix would be to go to /usr/local/share/gnome-ppp (at least that's where they are on my computer) and copy the file gnome_ppp_idle.png to all the other png files there, gnome_ppp_sending.png, gnome_ppp_receiving.png, and gnome_ppp_sending_receiving.png. That way, no matter what your modem is doing, it will always show the same icon.

---

### Post by gwbennett on 2008-01-23
I tried that and somehow it regenerates them or something! I compied the "recieving" one over the others, as root, and it still blinked. I tried rebooting even in case it somehow had them already in memory and had to re read them. No luck. Not sure what else to do.

---

### Post by yellowbread on 2008-01-24
After patching gnome-ppp, the png files show up in two places on my system, /usr/local/share/gnome-ppp and /usr/share/gnome-ppp. Itst apparently using the first of these for its data directory, because changing those files had the desired effect.

---

