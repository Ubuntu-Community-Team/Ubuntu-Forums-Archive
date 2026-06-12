---
title: "USB wifi adapter seen as ethernet, not assigned ip address"
date: 2017-03-05
forum: Networking &amp; Wireless
---

### Post by ge96 on 2017-03-05
I'm not sure if that's a thing where you can only run one "ethernet" at once.

I bought this USB Wifi Adapter called N-150 Nano USB 202039 by Cable Matters

Just mentioning, this USB WiFi adapter works for Raspberry Pi, I bought two different brands and so I bought this one again hoping it would work for Ubuntu on Desktop.

Right now I'm using a wired connection called enp2s0 (from ifconfig)

The USB WiFi Adapter shows up as wlx70886b8010c3 so it is "recognized" by Linux but the problem is it doesn't have an ip address/can't get it to work.

I was trying to use the editing ethernet connection and it doesn't show up there under ethernet. I see the HWaddr from ifconfig.

I'm not quite sure what to do next, this is what I currently have for my /etc/network/interfaces

auto wlx70886b8010c3
iface wlx70886b8010c3 inet dhcp

I commented out the rest, which there were only 2-3 other lines, even now with those other lines commented out, the wired connection works right away.

These are the other lines:

auto lo
auto enp2s0
iface lo inet loopback
iface enp2s0 inet dhcp

Any thoughts?

---

### Post by opsusec on 2017-03-06
internal hardware bridging, more than likely from VMware, 3rd party drivers, or ISP tunneling w/IPv6; I noticed this when using my old computer as an access point for VMware bridging and switching.

---

### Post by jeremy31 on 2017-03-06
I would change /etc/network/interfaces back to original
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

Unplug the ethernet cable and see if Network Manager finds any wireless access points.  Network Manager usually ignores interface names if they are listed in /etc/network/interfaces

---

### Post by ge96 on 2017-03-06
@opsusec

Interesting I do have virtualbox on this computer

edit: VMware might not be necessarily related to VirtualBox not sure that just popped into my head

---

### Post by ge96 on 2017-03-06
@jeremy31

Okay let me try that.

It's nuts to me how ridiculously slow my desktop gets using the ubuntu de versus i3. My computer freezes with only 7 tabs or so open on chromium. It's an old desktop and what not but has 8GB RAM and a quad core but still old/weak. Anyway not related to the question. I was in Ubuntu DE just because of the nice tools like the image creator, (can't seem to get unetbootin to work on linux) and the network editing.

edit: Well this worked! Awesome.

The speed drop sucks haha going from wired to wifi but oh well, 30Mbps is still not bad as opposed to 100 wired.

Now I don't have to have this 100 ft long ethernet cable running through the rooms haha.

Thanks a lot! Pretty simple solution.

Does suck that I couldn't figure out how to connect to the wifi through i3, I tried the ifconfig -> ifdown -a sort of deal but in the default Ubuntu DE, you've got that dashboard/bar on the top right that deals with power/settings/wifi/logout so that worked for me with enabling it.

---

### Post by ge96 on 2017-03-06
Problem now is I keep losing connection every couple of minutes. Por que!!!! No se, no se... I don't know.

Could be dual band/multiple frequencies?

---

### Post by jeremy31 on 2017-03-07
What is the result for ```
iwconfig
```

---

### Post by ge96 on 2017-03-09
It's odd, it seems to be working well today. Something happened to my ethernet connection where that kept dropping/trying over and over again pretty rapidly with a yellow ip (no-ip).

Says it's on 2.452 GHz (iwconfig)

I guess all is well now?

I should note before I was using a 6' usb extension if that matters at all. Now it's directly plugged in, also not into a USB 3.0 port like it was before. This is a USB 2.0 adapter so doesn't really make sense to use that, oh well.

Thanks

---

