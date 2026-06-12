---
title: "radeon 9600 in jaunty how to?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by powel212 on 2009-07-29
so I am trying to get jaunty installed on my friends computer but...

It is an older machine, but it still runs quite well and is a decent machine.

But it has a radeon 9600 which has no VGA out - it only has DVI out.

I managed to get Gutsy running but after upgrading to Hardy The graphics card no longer works... so I replaced the Hardy xorg with the one from Gutsy but it didn't work.

Does anyone one know how to do a straight install of jaunty with this video card or a command line install that will accommodate this video card?

Any help is appreciated.

Powel

---

### Post by jimsheep on 2009-07-29
quick answer - don't.

my suggestion is that you download 8.04 LTS because it's the last version that actually seemed to (wholly) support ATI drivers.

8.10 will work, as well...but i found 8.04 easier to get going.

---

### Post by Mark Phelps on 2009-07-29
As jimsheep pointed out, there are no restricted ATI drivers for your card that work with Ubuntu 9.04, but there are open source drivers, and those will be installed by default.

If you're only interested in 2D video (moves, Youtube, etc), they should work OK. It's just that they don't have the hardware acceleration needed for 3D games, and they don't support special outputs (like TV Out).

---

### Post by powel212 on 2009-07-30
Thanks for the straight talk guys. I'm not a big fan of ATi anyhow.

My solution.

Bought a new Nvidia NX6200, ($50.00USD), with VGA, and DVi outs. It's an old AGP? slot so I didn't have a lot of options.

Jaunty didn't recognise it but iBex is now running it with the Nvidai180 Driver. It looks and works great.

Thanks again for the help.

Powel

---

### Post by lestatius on 2009-07-30
I have a ATI 4890HD and I got it to work fine. Downloaded the drivers from the ati site.

here's the drivers for the radeon 9600.

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English)

---

### Post by powel212 on 2009-07-30
Thanks for that but... the ATi card is now in the Garbage... where it belongs.

Peace

Powel

---

### Post by Mark Phelps on 2009-07-30
> **lestatius said:**
> ... here's the drivers for the radeon 9600.

You would do better to do some research before you offer someone drivers that WILL NOT WORK!  The 9.3 drivers do not work in Ubuntu 9.04.  If the OP installs those, he will hose up his machine big time.  If you'd bothered to have checked a few of the dozens of threads about this, you would have known that.

---

