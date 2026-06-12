---
title: "Lenovo G50-30 Wireless disabled [rtl8723be]"
date: 2014-09-12
forum: Networking &amp; Wireless
---

### Post by wyldwulf on 2014-09-12
Hi everyone!

I am new in Linux and has been playing around with Ubuntu, Mint and a little Mageia:)
I bought a new (entry level) laptop so I could have a dedicated Linux system. My problem is that I cannot enable the wireless adapter.

I am done updating Ubuntu and have tried hard to get the drivers for the wireless card (rtl8723be). However, I cannot still enable my wireless adapter for some reason.
If i do an RFKILL LIST command, it shows that my WLAN is HARD BLOCKED. My laptop does not have a wireless switch (I also tried pressing the key combinations to enable wifi) and the wireless device is enabled in BIOS.

I am decided to ditch WIndows from my life so I need the wireless to be working :p
Hope someone here can help me.

Thanks in advance!

---

### Post by dave131 on 2014-09-12
I don't know if this is possible, but perhaps if you were running Windows somehow the adapter got disabled somehow by Windows (i can only guess on this - just following the thought of how some disks, etc., aren't accessable because the weren't properly removed or "dismounted" from Windows).  If you still have Windows installed, how does the wireless work there?

---

### Post by dave131 on 2014-09-12
I just looked at the user guide for your laptop.  it says to turn airplane mode off to enable wireless.  They show a key with a little airplane on the upper left of the key.  I don't know if there is any indicator showing if airplane mode is on or off.   Perhaps you've already done this - it's all I could find.

---

### Post by wyldwulf on 2014-09-12
Thanks for the reply, Dave.

Actually I am also suspecting that it might've been disabled in windows somehow.
Problem is: I no longer have windows on my system. Lol.

I am trying to find a way on how to enable it in Linux (and yes I already tried pressing that airplane thingy :p) . Been working on it for 4 days now.
Just tried a sudo command (forgot what it was) earlier to bypass lenovo's lock on the adapter but my system halted with a "kernel panic" error.

---

### Post by dave131 on 2014-09-13
Sorry I couldn't be of any help.  Good luck as I'm sure someone will come around and see your post and know a lot more than I do.

Dave

BTW - if you have a Windows disk you could shrink your existing partition(s) and install Windows for dual boot and try to fix it.  I think that Windows will still override the boot information, so you may need to boot a live media and run sudo update-grub  or perhaps boot-repair.  It's been quite a while since I "messed" mine up as far as the boot thing goes, so I don't know if it still applies or not.

---

### Post by pawe3pl on 2014-09-13
Hello wyldwulf.

Try this command:
```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
rfkill list all
```

It worked in my case. I am also using Lenovo G50-30.

---

### Post by wyldwulf on 2014-09-13
> **pawel-juchnowski said:**
> Hello wyldwulf.

Try this command:
```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
rfkill list all
```

It worked in my case. I am also using Lenovo G50-30.


Hi,

Thanks for the reply. Good to know that there is someone who is using the same laptop as me :)
Actually this is the command I was referring to on my earlier post.
my system halted with error:  
Kernel error panic - not syncing: Fatal exception in interrupt
Panic occured switching back to text console
(it was just a black screen with a long text log and I cannot do anything. I then just rebooted my PC)
Is there anything else that you did before executing the first command?

Thanks in advance  :)

---

### Post by varunendra on 2014-09-13
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by wyldwulf on 2014-09-14
I just tried the command (sudo rfkill -r ideapad-laptop) in Linux Mint and it worked for me.
I guess I messed up Ubuntu while trying to resolve my wireless issue.

:)

Thanks everyone! ;)

---

### Post by Xaitec on 2014-11-22
How well does linux run on this? I was thinking of getting one for my kids?

---

