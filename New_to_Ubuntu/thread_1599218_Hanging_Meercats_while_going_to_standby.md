---
title: "Hanging Meercats while going to standby"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by Nesaskewatch on 2010-10-17
I am having trouble with 10.10 hanging when the lid is closed on my Toshiba L500 laptop.  The hang does not happen all the time; just occasionally.  When it hangs the cpu fan kicks on and a *lot* more heat than normal starts to get blown out.  The screen is black and I am unable to do anything aside from a hard shutdown by holding down the power button.  Nothing else has any effect.  This machine ran well on Lucid, but none of the function keys worked without tweaking.  On Meercat the Fn keys now work and it recognises it as an L500.  Everything aside from the hang seems to work very well.  It has Windows 7 on a primary, with 10.04 and 10.10 on their own separate partitions.  Both Linux's have separate / and /home partitions and are clean installs from a live dvd.  Would there be a log file generated during a hang like this?  Or is that lost when I force it to shut down?  What would I need to be looking for as a "smoking gun"?  

Cheers!

---

### Post by Nesaskewatch on 2010-10-19
Well.  I can't find anything wrong.  I'm just not good enough with Linux yet I guess.  The standby freeze is now happening every time I  close the lid.  Too bad.  It was great for a while there, with everything working "out of the box".  Not any more...  Having to do a hard shutdown every time I close the lid or attempt a Fn+F3 (standby) is getting tedious.  This is a laptop after all.  And closing the lid without locking up or having to shut down is not too much to ask really.  With Ubuntu, it seems for every improvement, something else goes hooey.  Don't get me wrong; I am very happy to have a **free** operating system that by and large does *almost* everything Windows does.  It's just annoying to constantly be so tantalisingly close, then have something previously good go bad.  10.10 is definitely an improvement in many, many ways; but the lid freeze thing is a deal breaker for me.  10.04 is still on another partition, and it works reasonably well enough without freezing up.  I'll just go back to not having any Fn keys, and remain hopeful a future update will fix whatever is wonky with 10.10 on this machine.  So close and yet so far...

Cheers!

/rant off.

---

### Post by 101 on 2010-11-13
i have exactly the same problem on a HP ProBook 5310m notebook since i've upgraded to Ubuntu Meerkat 64bit (besides the fn keys, they were and are working for me).

have you found a bug report somewhere to follow? it's most probably a kernel regression, and it must be connected to the cpu fan, because sometimes when it comes back from suspend the cpu fan goes on 100% and i need to manually set it to full speed and then back to auto.

echo 0 then 1 (or vica versa)

sudo bash -c "echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B\:00/thermal_cooling/cur_state"

---

