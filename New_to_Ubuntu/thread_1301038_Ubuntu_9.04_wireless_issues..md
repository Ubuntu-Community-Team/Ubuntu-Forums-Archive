---
title: "Ubuntu 9.04 wireless issues."
date: 2009-10-25
forum: New to Ubuntu
---

### Post by shawnpeps on 2009-10-25
Hi there.

I figure since I'm new to Linux/Ubuntu, this would be the best place to start, even though my question may be suited to another spot.

Anyways, here's the issue.. 

I installed 9.04 on my Toshiba Satellite U500 last night. Install went awesome, it was super quick and everything seems to work great although my main problem is the fact that I'm unable to pull up the wireless network I have setup in my house. 

I'm not sure if it's an issue with the install or my wireless card, or if I'm just not seeing something and doing it wrong. From what I've gathered from the Toshiba site, the wireless card is a *Realtek 802.11b/g/n* but that could be entirely wrong.

So any help is hugely appreciated.

---

### Post by Cuddles McKitten on 2009-10-25
Type ```
lspci -v
``` into a console and give us the output for your wireless card.  Mine looks like this: 

```
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
    Subsystem: Intel Corporation Device 1201
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f4100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

```

---

### Post by shawnpeps on 2009-10-27
> **Cuddles McKitten said:**
> Type ```
lspci -v
``` into a console and give us the output for your wireless card.  Mine looks like this: 

```
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
    Subsystem: Intel Corporation Device 1201
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f4100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

```


I'm internetless on the laptop with 9.04, so I'll have to type it all out and my apologies if there's any useless stuff in there. 

03:00.0 NEtwork controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
Subsystem: Realtek Semiconductor Co., Ltd. Device 8152
Flags: bus master, faste devsel, latency 0. IRQ 5
I/O ports at c800 [size=256]
Memory at fdffc000 (32bit, non-prefecthable) [size=16k]
Capabilities: <access denied>


Anyone who's able to help with my problem with earn my love, affection and undying gratitude as I'm at my sanity's end with these problems I've been facing.

---

### Post by Matt__ on 2009-10-27
Dont know whats going on here...I'm on my toshiba sat pro running exactly the same card as you (*Realtek 802.11b/g/n*) on 9.04 which works perfectly...as it did from first install (prior to any update).

    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, fast devsel, latency 0, IRQ 2300
    I/O ports at a000 [size=256]
    Memory at f8200000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at f8400000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

what router are you using? have you tried to connect to other networks? pinged anything?

---

### Post by shawnpeps on 2009-10-27
It's some kind of SMC router. I'm not 100% sure. It's from Rogers Cable, and it's one of those weird router/modem combos.

I can't even see any networks to connect to, let alone my own. When I click on the little wireless bars, I get "Wired Network" which is all greyed out and says disconnected below it..

---

### Post by Matt__ on 2009-10-27
Ok, are you dual booting and if so can you connect using windows?

If yes have you done all the basic stuff like go to system/preference/network connections
and manually add the details(SSID,username,pass etc) to a new connection? then try to connect.
You could also ping your router IP address from command line ```
ping "192.etc.etc.etc"
```Is the "enable wireless" box checked in top panel?

---

### Post by shawnpeps on 2009-10-27
"Enable Networking" is ticked and I'm not dual booting. 

I was using Windows Vista before though and had absolutely no issues. I'm using my desktop right now, via wireless, with no problems either. I've tried entering all the info to log onto the router but I'm not seeming to have any luck whatsoever. It's strange because it seems like it should be really, really easy. Should any decent, nearby signals be automatically detected and shown?

---

### Post by Matt__ on 2009-10-27
Can you log into router setup and check SSID is set to transmit, wireless acces point is checked and no fire wall rules blocking you?
Do you have an option to add a device to router using its mac address?

Maybe you just need to update Ubuntu (with wired connection?)
or perhaps use another wireless manager like [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) after removing the one you are using.

Other than so far discussed I don't know what to suggest other than to contact ISP/router manufacturer or their webs for more info.

/edit since switching to Ubuntu I see SOOO many wireless nets locally that didnt show in vista.

---

### Post by shawnpeps on 2009-10-27
I'm not sure, I've also had problems getting into the router before. 

Regardless - I tried downloading this wicd, it's telling me it conflicts with network-manager. I have no idea where to find or remove network manager, as it doesn't show up under preferences or administration. The only network/wireless things I see under those are "Network Connections" and "Network Tools" and I'm sure it's entirely possible it's one of those, and I just have no idea what I'm doing.

---

### Post by Matt__ on 2009-10-27
you can remove or restore network manager from add/remove applications (under your programs list) menu or using synaptic package manger in the administration menu.


/edit would be nice if a 'buntu guru would show up and help instead of you having to rely on a newbie like me :P

this is a nice place to start too..freebie [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

---

### Post by anewguy on 2009-10-27
Please do the following:

- open a terminal window

- type:

lsmod 

copy and paste the output back here in a reply.  Want to see if the driver module is loaded in the kernel.

Dave :)

EDIT:  removed extraneous text I accidentally put here instead of another response.

---

### Post by sandyd on 2009-10-27
have you tried lowering the bitrate?
this was a problem on my friend's laptop, it would connect at the highest bitrate possible resulting in many errors.
 
also, see
[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

---

### Post by shawnpeps on 2009-10-27
> **anewguy said:**
> Please do the following:

- open a terminal window

- type:

lsmod 

copy and paste the output back here in a reply.  Want to see if the driver module is loaded in the kernel.

Dave :)

EDIT:  removed extraneous text I accidentally put here instead of another response.
In lsmod, is there anything specific we're looking for? Like I had mentioned before, I'm unable to copy/paste so the only thing i get from "output" is *11008  1*

---

### Post by anewguy on 2009-10-27
Yes - the command list the kernel modules loaded - look for something like r81xx of some sort (xx should be a couple of numbers) is being loaded, as I *think* that would be the name of the driver for your adapter.

If worse comes to worse, you can always download the Windows driver for your adapter.  You need just the .inf and .sys files for it.  Copy those to some media you can load in while booted in Ubuntu.

While Ubuntu is running, insert the 9.04 LiveCD, and navigate via the file browser to /main/pool/n on that disk.  You should see 2 folders - 1 for ndisgtk and 1 for ndiswrapper.  You want to open each of those folders and click on each of the files within them to install them (ndiswrapper utilities, ndiswrapper common, and ndisgtk).

Once you have that, post back and we'll go the rest of the way installing your Windows drivers to see if it helps any or not.

Dave :)

---

