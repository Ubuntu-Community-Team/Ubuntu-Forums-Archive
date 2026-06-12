---
title: "Slow Boot in Feisty after Installing ndiswrapper"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by anabelle on 2007-04-26
My laptop (hp dv6000) used to boot in practically no time. But since i installed ndiswrapper and the wireless windows driver the boot process is really slow.

It hangs at 50% of the loading bar and stays there for a while.

I've been searching the forums and i found that someone had the same problem hanging at configuring network interfaces using ubuntu 5.05

What can i do so my pc gets back booting at a normal speed??

---

### Post by cessna_89702 on 2007-04-27
Im not sure but the same thing happens to me after i used ndiswrapper

---

### Post by sedlie on 2007-04-27
I've got the same problem. I'm glad I'm not the only one since this is my first experience with linux and I was worried I had messed something up.

---

### Post by huygens on 2007-04-27
As I'm not using ndiswrapper, I do not know if you can use it with the NetworkManager applet. But if you use NetworkManager applet, then you might be interested by this solved ticket: [https://answers.launchpad.net/ubuntu/+question/4995](https://answers.launchpad.net/ubuntu/+question/4995)
It seems that the first point (in the second answer) had solve the slow boot process. Perhaps, this could help you.
Try to uncomment instead of deleting the lines in /etc/network/interfaces, so you can restore the previous configuration in case this was not the root of your problem.

---

### Post by anabelle on 2007-07-03
I can't solve the slow boot problem but i found out how to skip it....

when the loading bar hangs (almost at the middle) when configuring network interfaces you can press Ctrl+Alt+Supr and it jumps to the next step in the boot process. It really speeds up booting. :)

---

### Post by Ayuthia on 2007-07-03
Have you tried using the suggestion that huygens posted about commenting the items in /etc/network/interfaces?  It solved my boot issue in Feisty.  It seems that the fix has been made in Gutsy because I no longer have them commented.

---

### Post by Circus-Killer on 2007-07-03
> **Ayuthia said:**
> Have you tried using the suggestion that huygens posted about commenting the items in /etc/network/interfaces?  It solved my boot issue in Feisty.  It seems that the fix has been made in Gutsy because I no longer have them commented.

just out of interest, did gutsy automagically detect your wireless network card or did you have to use ndiswrapper like in feisty?

---

### Post by Ayuthia on 2007-07-03
Unfortunately, it did not.  I am still using ndiswrapper.  However, the Restricted Drviers Manager did detect that I had a wireless card (Broadcom 4311) and offered bcm43xx-fwcutter as an option.

---

### Post by James.Dedon on 2007-07-03
bcm43xx-fwcutter is all I needed to get my wireless up and running (Dell 1390 mini wireless).  I keep seeing people telling newcomers to use ndiswrapper and everyone keeps ignoring my comments on just running the fwcutter.

---

### Post by Circus-Killer on 2007-07-03
> **Ayuthia said:**
> Unfortunately, it did not.  I am still using ndiswrapper.  However, the Restricted Drviers Manager did detect that I had a wireless card (Broadcom 4311) and offered bcm43xx-fwcutter as an option.

thanks for the reply Ayuthia. think i might download gutsy tonight and give it a bash.

---

### Post by GrouchoMarx on 2007-07-03
I've been annoyed by this timeout for some time, as it can last half a minute. Apparently, the wireless interface is being configured before ndiswrapper is loaded. At startup...

> [FONT="Courier New"]Configuring network interfaces...
udev-event[4084]: rename-netif: error changing netif name wlan0 to eth1: Device or resource busy.[/FONT]

I've seen it suggested ([https://bugs.launchpad.net/ubuntu/+bug/108152]("https://bugs.launchpad.net/ubuntu/+bug/108152")) that everything except loopback should be removed from /etc/network/interfaces, but then this leaves the interfaces unconfigured after startup.

Another suggestion ([https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/102675]("https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/102675")) was to move networking further down the boot process, but this doesn't necessarily work smoothly.

Finally today I re-read the Windows Wireless Drivers (ndiswrapper) setup in the Feisty Wiki, and I swear it wasn't there before ;) but:

>     * Set ndiswrapper to load on startup 

```
sudo ndiswrapper -m
gksudo gedit /etc/modules
```
    * Add the following module to the list

```
ndiswrapper
```


... and finally the timeout disappears. So for those of you having this problem, don't forget this step in your ndiswrapper setup!

---

