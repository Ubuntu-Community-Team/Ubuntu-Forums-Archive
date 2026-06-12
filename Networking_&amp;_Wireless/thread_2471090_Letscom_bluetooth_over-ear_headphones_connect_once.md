---
title: "Letscom bluetooth over-ear headphones connect once, then never connect again"
date: 2022-01-21
forum: Networking &amp; Wireless
---

### Post by goemonburo on 2022-01-21
This has happened repeatedly and I have no idea what's causing it.  I have Lubuntu 20.04.3LTS running on a Dell Inspiron 3511 laptop.  The first time I install Lubuntu, the Bluetooth Wizard sees the headphones and pairs just fine.  I turn off the system, and it never sees them again.  I have used bluetoothctl to turn scanning on, to pair with the headphones via the Mac address, I have removed them via bluetoothctl...all to no avail.  Bluetooth Wizard will either fail to see them, or bring them up (H-10) but fail to connect.  

And it stays that way until I reinstall Lubuntu.  Then it works, just once, and the whole thing starts over again. 

(Had to reinstall Lubuntu for a totally different reason.)  

Does anyone know what's causing this?  Really hope to solve it.  The headphones work great when they pair.

Thank you!

---

### Post by guiverc on 2022-01-21
Are you using the HWE kernel stack?  The upgrade & reboot maybe switching kernels thus the issue (*assuming you use the same media or equivalent to re-install with*).

Ubuntu LTS releases have two kernel stack choices; with Lubuntu the stack chosen is selected by the installation media you install with; ie. 
- to use the GA kernel stack, use Lubuntu 20.04 & 20.04.1 media
- to use the HWE kernels tack, use Lubuntu 20.04.2 & later media (currently that's 20.04.3 & 20.04.4 in *testing* right now)

if you select an older kernel at `grub` on boot what options to you have?  You weren't specific as to what you're using, but it maybe 5.4 (GA), 5.8 (*20.04.2 with HWE*), 5.11 (*20.04.3 with HWE*) or 5.13 (*20.04.4 media will include this; installed systems only recently got this*).  Does it work when you select an older kernel?   

If it worked on a lower kernel (ie. 5.4, or even 5.8/5.11) then I'd suggest switching to the GA kernel stack.   All open-source systems can have both stacks installed allowing easy testing, however if you're using proprietary video drivers; some of those don't allow for it (*meaning you can't easily install both stacks but must switch from one to the other*).

For more details - [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

This is what I'd explore (*esp. if using open source drivers; as it's easy..*.).  You can also test using *live* media for clues (*not that convenient unless you have it around which I do*).

---

### Post by goemonburo on 2022-01-21
Thank you @guiverc, for the suggestions.  Do you know how I can get the kernel release stack via the cli?  I tried uname -r and it doesn't seem to say whether it's GA or HWE.  One system is kernel 5.4.0-94-generic
, the newer one is 5.11.xx (it's in the other room), I know that much, but they both seem to have the same issue.  When I opt to connect the headphones to my Android phone, it's a cinch, works as it should every time.  Another bluetooth portable speaker works fine with the 5.4 system, haven't tried it with the 5.11 one.

I've wondered if perhaps something is happening like it needs a manual code that's somehow not being entered, or not being saved, so by manually adjusting whatever file it uses to make the connection I might solve it?  I just don't know where to start with that.

Another question is that I seem to have "BlueDevil Wizard" in two separate places in the launcher:  One in "Internet" and again in "System Tools."  Would it help if I ran something as root?  Could it be as simple as a permissions issue?  

I don't really think I want to install a different kernel version and have to reboot each time I want to use the headphones.  If that's my only solution, I'll just plug them in wired and use them that way.  Sucks though.

---

