---
title: "Grub menu"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by jnmjr on 2010-04-03
Hi all.... I've got a little problem, in the last couple of days and completely out of the blue I can,t select the Os from the Grub menu at start-up. If I restart or shut down from Ubuntu when the menu comes up the arrow keys don't work at all and Ubuntu loads automatically even though I have not selected it, mind you I've got it set up so it has to wait for my selection. In order for me to go into WinXP, which I need to do occasionally during the day (I'm not Win-Free completely yet) I found I have to shut the power to the PC completely right after it begins to boot into Ubuntu so that when I power it up again the menu and arrows function correctly and allow me to make my selection. For your further info I have 2 HDs each with it's own OS and this has never been an issue. I've got no idea what may be causing this problem, if any body has suggestions or solutions they would be greatly appreciated.... THX

---

### Post by ibuclaw on 2010-04-03
Have you made any updates to your system (ie: grub) recently?

Only think that comes to mind is:
```

sudo update-grub
sudo grub-install "(hd0)"

```

Then holding down shift when your workstation boots to show the menu, as usual.

Regards
Iain

---

### Post by kblft on 2010-04-03
I had the same problem and it turned out to be a BIOS configuration problem (grub didn't recognize my USB keyboard).

I had to enable some legacy keyboard mode in the BIOS and it worked.

---

### Post by jnmjr on 2010-04-03
> **kblft said:**
> I had the same problem and it turned out to be a BIOS configuration problem (grub didn't recognize my USB keyboard).

I had to enable some legacy keyboard mode in the BIOS and it worked.


  That sounds right, I'm going to check my Bios, but if it worked Ok for 4 months what could have changed it?

---

### Post by jnmjr on 2010-04-03
> **ibuclaw said:**
> Have you made any updates to your system (ie: grub) recently?

Only think that comes to mind is:
```

sudo update-grub
sudo grub-install "(hd0)"

```Then holding down shift when your workstation boots to show the menu, as usual.

Regards
Iain

No, none of that has changed I've check it out, each HD has Grub2 installed in its MBR, I did that a long time ago to reduce Grub's loading time, at this time Grub has only a 2-3 second delay before loading OS, before when it was only on (sda) it took forever to load while it was looking for the other HD, but thanks for your suggestion.

---

### Post by jnmjr on 2010-04-03
> **kblft said:**
> I had the same problem and it turned out to be a BIOS configuration problem (grub didn't recognize my USB keyboard).

I had to enable some legacy keyboard mode in the BIOS and it worked.

I just checked my Bios, all seems to be correct, USB Legacy support is enabled, and is the only reference to LEGACY I saw, there is no specific reference to keyboard, according to the manual this applies to all legacy devices. Thanks, but I'm still miffed by this, it's just weird.

---

### Post by drs305 on 2010-04-03
It might be time to run meierfra's boot info script. If nothing else, it may help rule out recent grub updates that might be contributing to this problem.

Please post the script results between "code" tags, which you get by clicking the **#** symbol in the post's menu.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by jnmjr on 2010-04-03
> **drs305 said:**
> It might be time to run meierfra's boot info script. If nothing else, it may help rule out recent grub updates that might be contributing to this problem.

Please post the script results between "code" tags, which you get by clicking the **#** symbol in the post's menu.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


I just solved the mystery, dumb me, please don't get get upset for me making this stupid mistake ](*,)

Notice my [SIZE=1][COLOR=Black]/etc/default/grub file

[/COLOR][/SIZE]GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=-1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

[SIZE=1][COLOR=Black]When I looked at it yesterday I didn't see the Timeout missing the -  before the 1, I guess it got changed somehow, so grub was actually going to the default Os immediately, I just changed it back to -1 and updated Grub, all works as it should. Thanks all for your help, and forgive my mistake.
[/COLOR][/SIZE]

---

