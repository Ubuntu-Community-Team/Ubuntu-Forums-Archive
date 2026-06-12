---
title: "[SOLVED] Pre-dualboot questions."
date: 2008-12-28
forum: New to Ubuntu
---

### Post by DOS4dinner on 2008-12-28
Pentium 4 2.6ghz
1 gig RAM
ATI Radeon 9800
Lousy motherboard (Had to use a weird solution from [this bug]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684") to get it to work and find my graphics card)


I've been using Ubuntu 8.04 in Wubi for a while now, and I decided to go for a true dual boot. Anywho, I have a couple of questions:

Based on the specs, should I get 8.04 or 8.10? I've been happy with 8.04, and everything (save that weird bug) seems to work fine. Would 8.10 make my ATI card able to do more, or would it be about the same? 

Is there anything, other than uninstalling wubi, that I need to do on the windows XP side beforehand? 

Lastly, is installing ubuntu for a dual boot really as easy as just sliding the little bar to partition the drives and not hitting "Use whole drive?

---

### Post by Coder543 on 2008-12-28
It should be that easy if it is XP (vista... makes problems....)

8.04 or 8.10
It *really* doesn't matter. If 8.04 is working well you can stick with that. Or you could try out 8.10 and see if it has any new software in the repos that you want to use. Once you install 8.04 you can upgrade to 8.10 later on.

---

### Post by shifty_powers on 2008-12-28
> **DOS4dinner said:**
> Pentium 4 2.6ghz
1 gig RAM
ATI Radeon 9800
Lousy motherboard (Had to use a weird solution from [this bug]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684") to get it to work and find my graphics card)


I've been using Ubuntu 8.04 in Wubi for a while now, and I decided to go for a true dual boot. Anywho, I have a couple of questions:

Based on the specs, should I get 8.04 or 8.10? I've been happy with 8.04, and everything (save that weird bug) seems to work fine. Would 8.10 make my ATI card able to do more, or would it be about the same? 

Is there anything, other than uninstalling wubi, that I need to do on the windows XP side beforehand? 

Lastly, is installing ubuntu for a dual boot really as easy as just sliding the little bar to partition the drives and not hitting "Use whole drive?

pretty much, but please remember, repartitioning is never without risk. please cak up any irreplaceable data before installing another os.

but it is very simple, yes.

oh and i would go for 8.10, personally, but 8.04 is an lts release, so will be supported for three years, so feel free to use it...

---

### Post by hamofgrey on 2008-12-28
> **DOS4dinner said:**
> Based on the specs, should I get 8.04 or 8.10? I've been happy with 8.04, and everything (save that weird bug) seems to work fine. Would 8.10 make my ATI card able to do more, or would it be about the same? 


I am very doubtful that it will be able to make your card "do" any more, since there were very little changes to compiz-fusion. When you upgrade to 8.10 you will probably finder a more stable and bug fixed OS compared to the previous version.

Here is a guide to dual booting, I have assumed that you have XP already installed. Enjoy:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Alternatively here is the tutorial if you have Linux already installed.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by northern lights on 2008-12-28
Intrepid (8.10) is obviously more bleeding edge than Hardy (8.04). The latest kernel in the Hardy repositories, for instance, is 2.6.24-22 whereas Intrepid is 2.6.27-9.
Some applications also have newer candidates in the Intrepid repos than in the Hardy ones.

The differences are slim anyhow. Still, the advantage is clear: few apps might be more feature-rich. On the same page, while it probably will be just as smooth a computing experience as you had with Hardy, it is slightly more likely to bug out.

It's really a matter of preference. You could also triple boot Windows, Hardy and Intrepid, if you have the space.

The different wallpaper might be the only thing you notice, depending on your usage.

As far as the ease of installation is concerned, yes, it is that easy. Just don't pick "guided partitioning - use entire disk".

Here's a good [Installation Tutorial for Beginners]("http://www.psychocats.net/ubuntu/installing").

[EDIT]
> **hamofgrey said:**
> I am very doubtful that it will be able to make your card "do" any more
I don't think you'll notice much either. Compiz hasn't changed much, that much is true. There is however a newer fglrx (proprietary ATI driver) in the Intrepid repos. All my machines run on nvidia devices, so I can't say whether there's notable performance enhancements. I doubt it too.

> **hamofgrey said:**
> When you upgrade to 8.10 you will probably finder a more stable and bug fixed OS compared to the previous version.This assumption will prove faulty for most users. It might be as stable in most cases and will be not as stable in some. More stable than Hardy, it being 6 months older and an LTS release, will be the by far least experienced case (I don't want to say never experienced, though it's approaching zero for sure, as it might just happen with very particular hardware).
[/EDIT]

---

### Post by DOS4dinner on 2008-12-28
Thanks everyone! I'll probably stick with 8.04, as I'm not to concerned about the bleeding edge of technology (except for wine, of course:) )

---

