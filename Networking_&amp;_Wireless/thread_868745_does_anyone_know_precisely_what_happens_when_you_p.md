---
title: "does anyone know precisely what happens when you plug in a PCMCIA card?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by gopher38 on 2008-07-24
The reason I ask is this: I have Ubuntu installed on an old notebook, and it's running very well.  The notebook was unusable with XP, but Ubuntu has given it new life.  As I said, it's old, so the wireless is a PCMCIA linksys W54-something version 2 card.  Everything works except that I lose my wireless when returning from suspend.  I tried restarting wicd (which I'm using to manage wireless) and I tried a couple of suggestions that I found in this forum.  I don't remember all the details, but they involved stopping and resuming the network on suspend, startup; and adding some scripts.  The problem might be that I'm using ndiswrapper.  At any rate, they didn't work.

The one thing that does work every time is physically removing the PCMCIA card, waiting a second or two, and then plugging it back in.  So my question is: what exactly does Ubuntu do when it detects a new PCMCIA card?  There must be some script that it is running, and I figure if I can find that script and run it after returning from suspend, I might be able to fix this.

Thanks for your help.

---

### Post by gopher38 on 2008-07-30
Well, I'd pretty much given up on this after much searching, and then I stumbled upon something that gave me a workaround.  Perhaps it will help someone else.  

To summarize the situation, I would lose my wireless connection after suspend, and the only way that I could get it back was by physically unplugging and replugging the PCMCIA card.  I found all sorts of potential fixes having to do with adding "networking" and "ndiswrapper" modules to the acpi scripts, ifup this, ifdown that, scripts in pm-utils, blah, blah .... none of it worked (not to dismiss those instructions - do a search on this forum for "suspend wireless" and you'll get all sorts of suggestions that seemed to work with a lot of people, but not for me).

Anyway, I finally found out how to simulate the PCMCIA card being ejected.  You have to install cardctl (don't remember the command; do a search), which creates a new command /sbin/pccardctl

I then went to the /etc/pm/sleep.d directory, which apparently gets executed on resume in Hardy.  I had created a script there from one of the earlier attempts to fix this, and I added the eject/insert commands for the PCMCIA card.  And voila, I've got my wireless back after suspend.

Probably not the best solution, but better than nothing.  Ciao.

case "$1" in
	hibernate|suspend)
		 # /etc/init.d/networking stop
		;;
	thaw|resume)
		 (sleep 5 ; /sbin/pccardctl eject )&
		 (sleep 5 ; /sbin/pccardctl insert )&
		;;
	*)
		;;
esac

---

### Post by jimv on 2008-07-30
I think the process goes something like this:

1.  Insert PCMCIA card.
2.  ...
3.  Profit!

---

### Post by Craigus on 2009-04-25
Thanks. This method works fine with my Toshiba 3480CT / Dlink DWL-G650+ running Enlightenment on Debian Lenny.

Even lid close / open; suspend / resume works.

---

### Post by poltr1 on 2009-04-28
I don't know what happens when I plug in a PCMCIA card.  All I can say is that it's magic.  :)

FWIW, if you're still having trouble with that Linksys wireless card -- I'm gonna guess it's a WPC54G v2 -- give this thread a look.  [http://ubuntuforums.org/showthread.php?t=324148]("http://ubuntuforums.org/showthread.php?t=324148")

---

