---
title: "Boot/Install impossible, red/grey screen"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by Sunfire00 on 2010-07-06
Hello everyone,

this is my first forage into Linux, so I decided to fire up a Live CD and tried to install Ubuntu via Wubi on my laptop. With both I encountered the same nasty problem: after trying to boot via the boot manager (I suspect it's Grub, I am a noob with Linux), I get a messed up screen with a huge red and yellow rectangle on it, which slowly fades out to a completely grey screen. After that, nothing happens until I force a reboot by turning the laptop off.

I tried to boot in safe graphics mode via the boot loader, same result. I also tried every other option on the boot loader with no change. I can't manage to open a console or anything, the only thing I can do is edit the boot variables of the different options.

Today I tried the same booting/installing with Mint Linux, to see if that works. The results were the same, red screen fading out to grey and that's it.

The laptop in question is a Dell Inspiron 1520 with a Nvidia 8600M GT as GPU. I know the card should be supported by both distributions.

Perhaps any of you guys gut an idea about this?


Thanks!
Sunfire

---

### Post by Rubi1200 on 2010-07-06
Just out of curiosity, have you tried the previous version of Ubuntu (9.10) as a LiveCD?

The issue is almost certainly either hardware or graphics.

See here for some possible workarounds (courtesy of oldfred; experienced forum member):

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by Sunfire00 on 2010-07-06
Thanks Rubi, I'll try those workarounds right away.

I've only tried Ubuntu 10.04 and Linux Mint 9 so far, no older versions.

---

### Post by Sunfire00 on 2010-07-06
At least I got a reaction when using this: [http://ubuntu-tutorials.com/2010/05/...up-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/") ;)

Since there is no spash screen the text is scrolling down. Now the booting stops at the line "init: ureadahead-other main process (2516) terminated with status 4"

After that there is the same line twice more, only the number changes to 2517 and 18, after that there is "setting sensor limits [ok]" and nothing more, it freezes again.

---

### Post by Rubi1200 on 2010-07-06
> **Sunfire00 said:**
> At least I got a reaction when using this: [http://ubuntu-tutorials.com/2010/05/...up-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/") ;)

Since there is no spash screen the text is scrolling down. Now the booting stops at the line "init: ureadahead-other main process (2516) terminated with status 4"

After that there is the same line twice more, only the number changes to 2517 and 18, after that there is "setting sensor limits [ok]" and nothing more, it freezes again.

I am assuming you used the nomodeset parameter? 

How long did you wait after it got to the "setting sensor limits" line?

It may appear to freeze, but leave it for a couple of minutes at least to see what happens.

The same thing happened to me with an Intel chipset; I used the i915.modeset parameter and also got to that line. Waited a few minutes and then the Desktop came up.

One more option you could try: following the advice in the link, remove quiet splash and instead of adding the parameters suggested there you could try adding this:

xforcevesa noapic noapci nosplash irqpoll

You need to add all of them as I have them here. Play around also; for example try them but with nomodeset instead of xforcevesa.

Good luck!

---

### Post by Sunfire00 on 2010-07-07
Tried again, let the laptop run for 15 minutes, nothing changed. No activity on the hard disc or any sign of the machine being alive. 

Also tried your other suggestions, xforcevesa instead of nomodeset is giving me a red screen again, nomodeset in combination with the remaining options is freezing the boot sequence just like without them.


Would it be a valid option to try and insteall 9.10 instead of 10.04?


[edit]
Tried booting from a live cd instead of installing via Wubi. Took ages, but worked like a charm with nomodeset active. Sometimes I am amazed by my own stupidity... will try installing from CD without Wubi now.

---

### Post by Rubi1200 on 2010-07-07
Wubi is great for people who just want to take a quick look at something "new and unusual." 

It is not really recommended, however, if you want a stable environment. 

Good luck with the install and let us know if you need more help.

---

### Post by Sunfire00 on 2010-07-07
Thanks for the help so far, Rubi :)

Somehow I suspect this won't be the only problem I will encounter in the next time... ;)

---

