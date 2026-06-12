---
title: "error: grub rescue I can't even boot from any cd"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by captgadget on 2010-11-06
with the error message about the grub rescue I can't even boot from any cd/dvd. Like I just tried to boot from winxp I get hit any key to boot and then when I do I get the no partion grub rescue. Any ideas how I can even get a cd to boot? I also tried a live cd and no go there either

---

### Post by kansasnoob on 2010-11-06
It sounds like you need to change the BIOS settings to boot CD first.

[http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm](http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm)

That's not totally correct, I've found other key or key combinations are sometimes needed to get into the BIOS, but that's a general idea.

---

### Post by wilee-nilee on 2010-11-06
Is your keyboard working? if you get the hit any key from a XP cd boot then the cd is being read, it would seem. 

There is a per session boot key mine is f12 yours could be that or escape or another. This just brings up a menu to choose the boot from choice, use the key prompt at hitting the power on button.

If you get into a Ubuntu session with this key prompt run the bootscript in my signature, and post it in code tags. The link explains what to do but can be confusing so feel free to ask any questions.

---

### Post by kansasnoob on 2010-11-06
wilee-nilee is more correct than I was!

Thanks W-N :)

---

### Post by wilee-nilee on 2010-11-06
> **kansasnoob said:**
> wilee-nilee is more correct than I was!

Thanks W-N :)

Well there is a first time for everything, a anomaly I suspect.;)

---

### Post by captgadget on 2010-11-06
BIOS is set to boot from cd, except the error message kicks in first and I can't to any where after that error message.

---

### Post by wilee-nilee on 2010-11-06
> **captgadget said:**
> BIOS is set to boot from cd, except the error message kicks in first and I can't to any where after that error message.

Booting this way gets broke sometimes not sure why, use the key prompt to boot. Look on the web with your computer model to find this information, it will be in any manual on your computer.

---

### Post by captgadget on 2010-11-07
and when I use the prompt key that's when I get the grub rescue, no partition  error message.

---

### Post by wilee-nilee on 2010-11-07
> **captgadget said:**
> and when I use the prompt key that's when I get the grub rescue, no partition  error message.

I was thinking last night while falling asleep that it may be the cd reader, clean the lens correctly and try another reader if you can. The symptoms from your description of the XP cd boot sound like some hardware problem like the cd player. That is if you boot the XP cd and get the hit any key and it doesn't work. Could be that your keyboard maybe really hard to say.

---

### Post by captgadget on 2010-11-08
I finally got it: used this website: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

