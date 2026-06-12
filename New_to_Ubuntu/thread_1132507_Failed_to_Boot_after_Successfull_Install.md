---
title: "Failed to Boot after Successfull Install"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-04-21
I have recently installed Ubuntu 8.10 on my PC using **ubuntu-8.10-alternate-amd64.iso** and it was successful. Unfortunately, my PC was unable to finish booting. It stopped loading after 2.5 bars in the progress bar. I tried booting again, this time in the restore option in GRUB, and I wrote down the last messages on the screen before it crashed again:
```

[14.868007] [<ffffffff8021285a>]? system_call_fastpath+0x16/0x1b
[14.868007]
[14.868007] ---[end trace 6b2293e1e967c2c5]---
```

I downloaded the .iso file from the Ubuntu website and did the checksum and hashes were correct.

**What does this mean? Please help me. Thank you!**

**System Information:**
[LIST]
[*]AMD Athlon X2 64
[*]1.9Ghz
[*]3Gb RAM
[*]250GB HD
[*]Nvdia 8200M G
[/LIST]

---

### Post by cariboo on 2009-04-21
What filesystem are you using?

Jim

---

### Post by LesterPalooza on 2009-04-21
> **cariboo907 said:**
> What filesystem are you using?

Jim

ext3 for Ubuntu 8.10

I appreciate the fast reply Jim.

---

### Post by Ravernomina on 2009-04-21
did u do a graphical install (live CD) or the basic install (DOS looking)

---

### Post by LesterPalooza on 2009-04-21
> **Ravernomina said:**
> did u do a graphical install (live CD) or the basic install (DOS looking)

I did the basic install. I tried the graphical one (ubuntu-8.10-desktop-amd64.iso)and wasn't able to install because the Ubuntu progress bar stopped at 2.5 bars and crashed. Then I used the alternate one to use the basic install - t'was successful but unable to boot after installation. :(

---

### Post by Ravernomina on 2009-04-21
HAHA!!! that means your graphic drivers are giving you problems!!!

---

### Post by LesterPalooza on 2009-04-21
> **Ravernomina said:**
> HAHA!!! that means your graphic drivers are giving you problems!!!

I also tried installing the other .iso file **ubuntu-8.10-desktop-i386.iso** and it was successfully installed and booted properly. However, I believe the AMD iso is best suited for my desktop right? How come my graphics driver is giving me problems? You mean, **ubuntu-8.10-alternate-amd64.iso** did not install the correct graphics drivers?

---

### Post by Ravernomina on 2009-04-21
its a possibly maybe the 64 drivers won't work for your graphics card :l

And you really only need a 64 bit os if u have more then 3 gigs of RAM

---

### Post by LesterPalooza on 2009-04-22
Okay that is just sad. Because if I use the one for intel processors then im gonna have problems with firefox and running games. they just lag for me. is there anyway I can fix this? I really want the right release for me.

---

### Post by Ravernomina on 2009-04-22
i do not know.... im not a master of linux :l try to boot of the live CD then do the command for to download your graphic card drivers.. i forget the code sorry :l

---

### Post by Ravernomina on 2009-04-22
also try doing a memoery check could be something with your RAM as well

---

### Post by LesterPalooza on 2009-04-22
> **Ravernomina said:**
> also try doing a memoery check could be something with your RAM as well

I just did. RAMs fine.... Someone? Please? Any more ideas?

---

### Post by cariboo on 2009-04-22
I saw the same error message when trying to boot using reiserfs, but that isn't your problem. It looks like it is stopping before gdm starts, can you start in recovery mode and drop to a command prompt/

Jim

---

### Post by LesterPalooza on 2009-04-22
> **cariboo907 said:**
> I saw the same error message when trying to boot using reiserfs, but that isn't your problem. It looks like it is stopping before gdm starts, can you start in recovery mode and drop to a command prompt/

Jim

I started with recovery mode and I couldn't reach a command line point - the error message comes out first.

EDIT: I can access a command line prompt in GRUB before I select Recovery Mode from the list (grub).

it looks like this...
```

                commands are limited.... blah blah...

           grub > 
```

---

### Post by LesterPalooza on 2009-04-22
I tried rebooting on Recovery Mode and took a look at the lines before

```

...
[14.868007] [<ffffffff8021285a>]? system_call_fastpath+0x16/0x1b
[14.868007]
[14.868007] ---[end trace 6b2293e1e967c2c5]---
```

and it said something about ath_pci. You think that was causing problems?

---

### Post by LesterPalooza on 2009-04-22
*bump*

---

### Post by Gen2ly on 2009-04-22
i think you have to wait a few minutes before you bump. ;)

i'm not dissing ubu because i think it's great but if you can't figure it out you can always try another distro and see how that does.  Linux Mint is a common one that is alot like Ubuntu, or give PCLinux a try.  they both got good installers.

---

### Post by LesterPalooza on 2009-04-22
I prefer Ubuntu.... :( gosh.... does this mean I cant use the amd release? wasnt **ubuntu-8.10-alternate-amd64.iso** made for AMD? ...

I wish there will be more solutions coming...

---

### Post by LesterPalooza on 2009-04-23
*bump*

---

### Post by Kareeser on 2009-04-23
Yes and no. It's made for AMD and Intel ***_64-BIT_*** processors.

If you have a 32-bit processor, you need to download the i386 version. You said you had success with the 8.10 32-bit version, but not with the 64-bit. This means you most likely have a 32-bit processor.

You've downloaded the wrong ISO! Give the 32-bit one a try :)

---

### Post by LesterPalooza on 2009-04-23
> **Kareeser said:**
> Yes and no. It's made for AMD and Intel ***_64-BIT_*** processors.

If you have a 32-bit processor, you need to download the i386 version.

I have a 64 bit processor. AMD Athlon X2-64

---

### Post by jmmL on 2009-04-23
Have you tried the new jaunty ISOs? It's possible your problem is fixed there.

If not, you might want to use i386 anyway - at least it works, and the performance penalties shouldn't be too great.

---

### Post by LesterPalooza on 2009-04-23
> **jmmL said:**
> Have you tried the new jaunty ISOs? It's possible your problem is fixed there.

If not, you might want to use i386 anyway - at least it works, and the performance penalties shouldn't be too great.

performace penalties are great! flash videos are choppy, even openarena lags...

---

### Post by thomasboleyn on 2009-04-23
Try adding 'acpi = off' to the boot options at startup.

> **LesterPalooza said:**
> performace penalties are great! flash videos are choppy, even openarena lags...

---

### Post by LesterPalooza on 2009-04-23
> **thomasboleyn said:**
> Try adding 'acpi = off' to the boot options at startup.

Yes did that. and noapic and nolapic and pci=nopci but to no prevail.

*bump*

---

### Post by thomasboleyn on 2009-04-23
> **LesterPalooza said:**
> Yes did that. and noapic and nolapic and pci=nopci but to no prevail.

*bump*

It should be 'apci' not 'apic'.

---

### Post by LesterPalooza on 2009-04-23
> **thomasboleyn said:**
> Try adding 'acpi = off' to the boot options at startup.

Should be 'apci' and not 'acpi' and not 'apic', right?

---

### Post by LesterPalooza on 2009-04-24
I added apci=off to the boot options and it did not work - meaning, it still crashes at 2.5 bars in the loading progress bar.

---

