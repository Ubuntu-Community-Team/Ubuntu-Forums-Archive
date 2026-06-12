---
title: "Blacklisting list?"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by iainv on 2008-03-29
I'm using a Philips SNU6500 USB with WEP via ndiswrapper, which works when you turn the computer on but will drop out after a random time (sometimes 10 mins, sometimes 2 hours) and fail to reconnect, requiring a re-boot.

Searching the forums it would seem that lots of people are having similar problems with all sorts of wifi adaptors, and one of the potential solutions mentioned seems to be to blacklist conflicting drivers. I've blacklisted a couple that are suggested in the community docs, but is there a complete list of all wifi modules so I can blacklist them all, or a command that will automatically block any wifi-related activity that might interfere with ndiswrapper? And how do I see which modules are currently blacklisted?

Thanks,

Iain

---

### Post by chili555 on 2008-03-29
> how do I see which modules are currently blacklisted?Issue a command in a terminal:```
cat /etc/modprobe.d/blacklist
```> is there a complete list of all wifi modules so I can blacklist them alThere is, but it's quite long and I'm not sure I'd want to spends weeks blacklisting modules! In a terminal, do:```
locate wireless | grep .ko
```I'd suggest you approach this from another angle. In a terminal, do:```
lsmod | less
```The 'less' part will allow you to use your arrow keys to scroll back and forth in the list. Drop out of the list with 'Shift+Q.' You can examine the list to see what modules are loaded that you may or may not want.

---

### Post by iainv on 2008-03-29
Thanks.

Now i'm confused, though.

I thought the point of blacklisting modules was to prevent them from being loaded because they might interfere with things, so there would be plenty loaded, but looking through the list provided by lsmod I can't see any of the ones from locate|wireless - are there none loading then?

Attached is my lsmod output.

:confused:

Is there anything else to try?

Iain

---

### Post by chili555 on 2008-03-29
> the point of blacklisting modules was to prevent them from being loaded because they might interfere with thingsCorrect.> so there would be plenty loadedNot quite. If a card uses a certain driver, and the card is installed or inserted, *only* that driver is loaded. Blacklist is needed because sometimes too many modules get loaded. I have a knock-off Prism II card that loads prism2, orinoco AND hostap, and then doesn't work. If I blacklist orinoco, it works perfectly.

Second, it is vital in ndiswrapper if a driver is built into the kernel that is buggy or really doesn't work at all. You install ndiswrapper and blacklist the kernel driver so both do not load and conflict.

In your *lsmod*, it looks like you have the only wireless module you need: ndiswrapper. It appears your problem is *not* conflicting drivers.

You might open up a terminal and do:```
sudo tail -f /var/log/messages
```Leave it open until the wireless poops out. See if the kernel throws out any complaints. You may get some clues.

---

### Post by iainv on 2008-03-31
Thanks.

I left the system log running and caught the drop-out message.
It almost looks as if it became unplugged, but if you actually unplug the wifi from the computer when you plug it back in again it doesn't light up until you reboot.

Attached is syslog output (sorry for the screenshot - couldn't copy and paste from the window for some reason!)

Iain

---

### Post by kevdog on 2008-03-31
Wireless drivers can either be built-into the kernel itself, and installed from a third party program (such as ndiswrapper).  Built-in driver (kernel modules) will always load by default and have preference over third-party modules.  To prevent certain built-in modules from loading at boot, they are specified in the blacklist file.   To force external modules to load at boot you need to place them in /etc/modules.

---

### Post by dstew on 2008-03-31
The output of the command ```
ndiswrapper -l
```will usually tell you if you have an alternate driver, including the name. Blacklist the alternate driver that is mentioned there.

---

