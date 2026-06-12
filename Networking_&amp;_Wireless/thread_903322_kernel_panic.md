---
title: "kernel panic"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by MichaelSM on 2008-08-28
Have been playing with wifi recently, and everything fine.But ..

Tonight I had my usual PC (7.10) on line via ethernet and my spare PC (also 7.10 on line at the same time using Netgear wg311v3 usb adapter) both through a Netgear  wireless modem-router.

With some time to spare, I set the 'spare' PC to download a LOT of updates which was going perfectly until - coincidence? and expecting a slower download speed? - I attempted to open Firefox on my usual PC, which wouldn't happen. 'Server not found etc.' Hmmm ..

I nicked into the study where the wifi-connected PC is, and it was seized up at update 69 out of 100. Bugger!

So re-boot ...why not? Been there before etc. 

I've never seen 'kernel panic' until now.

That's what the screen says on the 'spare' 7.10 PC. If it's of any use, I'll type it in:

[ 28.358669] = = = = = = =
[ 28.388722] Code: bad EIP value
[ 28.358847] EIP:
[ 28.35904.....

I'll stop there, becos I've left the 'spare' PC on,and it's still trying to do something - the numerals have changed a lot, but what's possibly important as it cycles is the recurrent line:

[ xxxxxxxxxx] Kernel panic - not syncing: Attempted to kill the idle task!

This is with the Netgear dongle disconnected.

I could go 'Ctrl>Alt>F1' to access the drive,but I wouldn't know what to do after that!

Any ideas?

Cheers, Mike.

---

### Post by regala on 2008-08-28
> **MichaelSM said:**
> 

(...)

I've never seen 'kernel panic' until now.

That's what the screen says on the 'spare' 7.10 PC. If it's of any use, I'll type it in:

[ 28.358669] = = = = = = =
[ 28.388722] Code: bad EIP value
[ 28.358847] EIP:
[ 28.35904.....


I'll stop there, becos I've left the 'spare' PC on,and it's still trying to do something - the numerals have changed a lot, but what's possibly important as it cycles is the recurrent line:

[ xxxxxxxxxx] Kernel panic - not syncing: Attempted to kill the idle task!



WHAT???? nope, it is not cycling, impossible, when kernel panicked, the machine is dead. And the complete backtrace should be provided to have a clue or a chance to get one that explains what happened.
:)

Mathieu

---

### Post by MichaelSM on 2008-08-30
Thanks for reply, Regala.

It's fixed now. I'm fairly sure that the problem was the two computers being on-line during the update ....why that might be I don't know.

What I finally decided to do, was upgrade that drive to Hardy off a boot/install disc. The drive wouldn't boot off the disc, and after a few minutes it booted into 7.10. I downloaded and installed all the updates; fingers crossed all will remain good.

Cheers,

Michael.

---

