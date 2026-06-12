---
title: "USB nano-WiFi dongle that works with 5GHz access points"
date: 2018-01-21
forum: Networking &amp; Wireless
---

### Post by Scott Deagan on 2018-01-21
Could someone please recommend a decent A/C nano-Wifi dongle that works with 2.4GHz and 5GHz access points? At present, I'm using a:

```
0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n
```

(TP-LINK TL-WN725N 150 Mbps Wireless-N Nano USB Adapter, 2.4 GHz Only)

which has been working awesomely - I just plugged it in and it worked. The only problem I have is it only uses 2.4GHz, not 5GHz, which means I sometimes cannot attach to some access points that only have 5GHz enabled.

I also have the TP Link Archer T4U, which also works fantastic. It doesn't work out of the box, but thanks to this post here:

[https://askubuntu.com/questions/802205/how-to-install-tp-link-archer-t4u-driver](https://askubuntu.com/questions/802205/how-to-install-tp-link-archer-t4u-driver)

it works with Kubuntu 17.10 running kernel 4.13 (which is what I'm currently using). The only problem I have with the Archer T4U is the size - it's huge, and sticks out the side of my laptop like a sore thumb.

I'd like something that's small that does both the 2.4GHz and 5GHz channels and works relatively well on Linux (I don't mind if it's not plug and play, so long as there's a driver out there that can be installed).

Any suggestions?

---

### Post by SeijiSensei on 2018-01-21
Edimax makes tiny USB adapters.  They now have this item [https://www.newegg.com/Product/Product.aspx?Item=N82E16833315162](https://www.newegg.com/Product/Product.aspx?Item=N82E16833315162), an 802.11ac device, which uses the [Realtek 8812BU chipset]("https://wikidevi.com/wiki/Edimax_EW-7822ULC").  (The Archer device uses the 8812AU version.)  It claims to have Linux support; I wouldn't be surprised to see it pop up in the Driver Manager and offer to use 8812au source code to build the driver as happens now with the Archer device.

Of course, a tiny device means a tiny antenna, so whether it performs well at the distances required between adapter and wifi hotspot as the T4U, you'll have to see for yourself.  The [802.11n version of this device]("https://www.newegg.com/Product/Product.aspx?Item=N82E16833315091") works quite well even through walls and floors.  It is often used with Raspberry Pi's given its size.

---

### Post by Scott Deagan on 2018-01-21
Thanks - I'll try out the Edimax EW-7822ULC AC1200. I'm not worried about range or speed, I just want something that will work on Linux, will connect to AC networks, and is a "nano" form factor. The problem I have with the T4U is my kid, who has just started walking, grabs it and yanks it back and forth. This has already resulted in one damaged USB port. I also like the nano form factor because it means I can just close my laptop lid and shove my laptop in my backpack.

---

