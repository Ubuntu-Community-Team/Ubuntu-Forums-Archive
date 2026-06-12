---
title: "is ubuntu compatible with 802.11 b/g/n wireless chipset"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by jocelynbennicoff on 2009-12-23
I'm not familiar with chipsets or anything, but some new laptops i'm looking at purchasing have the Intel 802.11 b/g/n.  i checked the chipset directory but i'm afraid i don't really understand what i'm looking at.  could someone please let me know if ubuntu will recognize the wireless i mentioned?  thanks!

---

### Post by coffeecat on 2009-12-23
Of all the different makes, I believe Intel wireless is most likely to be trouble-free in Ubuntu. Since the chipset you've seen in b/g/n, then it's probably from the newer 5*** series. I have the 5100 Intel chipset in my Sony laptop and it worked out of the box in both Jaunty and Karmic.

But I have seen a couple of threads from people having problems with the 5100 chipset. One seemed to be down to BIOS issues.

Do you know exactly which Intel chipset your favoured machine has?

---

### Post by cenzorrll on 2009-12-23
for the most part yes, 802.11n has been around long enough that it's pretty stable in linux.  i have a broadcom 4322 that works well, there are a few bumps, i had to install wicd rather than use NetworkManager (card still worked, just slow on a home network) but other than that all is fine.

although i'm too cheap to get a wireless n router, so i can't say if it works or not.

---

### Post by jocelynbennicoff on 2009-12-23
An asus laptop i am interested in lists this info on the asus website:
Chipset: Mobile Intel GL40 Express Chipset +ICH9M.   Fax/modem/LAN/WLAN: Integrated 802.11 a/b/g/n 10/100/1000 Base T.

i have no idea what any of that means, but i hope it helps you answer my question.

---

### Post by coffeecat on 2009-12-23
> **jocelynbennicoff said:**
> Chipset: Mobile Intel GL40 Express Chipset

Unfortunately, that doesn't necessarily mean an Intel wireless chipset. See this:

[http://www.intel.com/products/notebook/chipsets/gl40/gl40-overview.htm](http://www.intel.com/products/notebook/chipsets/gl40/gl40-overview.htm)

The wireless often (always?) comes on a separate mini-PCIe card, so Asus might very well be using different makes for the wireless and the ethernet. What Asus model number is it? It might be useful to do a bit of googling, but unfortunately it can be very difficult to find the precise wireless chipset, even on the manufacturer's website. That last laptop I bought, I insisted on having a fiddle in Vista's control panel on the shop's display machine to find out what wireless it had before I bought one.

---

### Post by Shpongle on 2009-12-23
yea im using it trouble free on my laptop :-)

---

### Post by jocelynbennicoff on 2009-12-23
coffeecat, i'm inquiring about the ASUS k501J-x8.  you've given me a lot of info, but i'm still confused.  Isn't the chipset they list the chipset they use?  you make it sound like they might not be using the intel wireless chipset.  What should i be looking out for, rather, what part of the list of numbers/letters do i use to determine compatibility?  is it not enough to say 802.11 b/g/n?  how do i find out what series it is, like you mentioned?  Thanks for the help, i really have no clue about this.

---

### Post by Trisket on 2009-12-23
I'm running ubuntu 9.10 on my Toshiba with Intel 802.11b and it works seamlessly.by far the best Linux distro Ive installed(out of about 12) and i had no problem as soon as it booted for the first time, i entered my wep and was on the net within two minutes.

---

### Post by coffeecat on 2009-12-23
> **jocelynbennicoff said:**
> coffeecat, i'm inquiring about the ASUS k501J-x8.  you've given me a lot of info, but i'm still confused.  Isn't the chipset they list the chipset they use?  you make it sound like they might not be using the intel wireless chipset.  What should i be looking out for, rather, what part of the list of numbers/letters do i use to determine compatibility?  is it not enough to say 802.11 b/g/n?  how do i find out what series it is, like you mentioned?  Thanks for the help, i really have no clue about this.

As far as I can make out the Intel GL40 Express covers only the graphics, SATA controller, memory controller and USB controller. No mention of wireless. Speaking of which, 802.11 is simply a set of international standards covering wireless LANs. See:

[http://en.wikipedia.org/wiki/IEEE_802.11](http://en.wikipedia.org/wiki/IEEE_802.11)

**All** makes of wireless chipsets (Intel, Atheros, Broadcom, Realtek, Ralink, Marvell, etc, etc) have to be 802.11 compliant. the a/b/g/n refers to the particular protocol - 'a' being older than 'b' and so on.

But back to the laptop in question, those specs tell us no more about the wireless and ethernet controllers than that they conform to international specifications. We don't know what chipset/makes they are. Laptop manufacturers do weird and wonderful mixtures - unfortunately. I tried googling your Asus model number and the best I could come up with is this thread on this forum:

[http://ubuntuforums.org/showthread.php?t=1233342](http://ubuntuforums.org/showthread.php?t=1233342)

But that may or may not be the identical model to your Asus - I see from googling that there are a number of affix numbers that go with K501J.

If yours has the Atheros AR9285 wireless chipset like the OP of that post, you may or may not get problems. There are a few threads about that wireless device. Some managed to fix their problems; some did not.

**Edit:** just to clarify this word "chipset": that most often refers to the [motherboard chipset](http://en.wikipedia.org/wiki/Chipset) which in your case would be the Intel bit. But a wireless device has its own chipset. When you had laptops with the Intel trademark "Centrino" on I believe you could be sure that you had Intel in the wireless as well as on the motherboard. But without "Centrino" I believe this is not necessarily the case. It pays to be cautious. Some wireless chipsets can be a right pain.

---

### Post by Shpongle on 2009-12-23
> **Trisket said:**
> I'm running ubuntu 9.10 on my Toshiba with Intel 802.11b and it works seamlessly.by far the best Linux distro Ive installed(out of about 12) and i had no problem as soon as it booted for the first time, i entered my wep and was on the net within two minutes.

i should have been more specific , the same applies for me on my toshiba equium

---

### Post by coffeecat on 2009-12-23
> **Trisket said:**
> I'm running ubuntu 9.10 on my Toshiba with Intel 802.11b and it works seamlessly.by far the best Linux distro Ive installed(out of about 12) and i had no problem as soon as it booted for the first time, i entered my wep and was on the net within two minutes.

> **DillByrne said:**
> i should have been more specific , the same applies for me on my toshiba equium

Sorry to say this, but without knowing the precise wireless chipsets your machines are using, this does not help the OP. Some wireless chipsets work just fine in Ubuntu. Some need a little work on them. And a few are best not touched with a 50ft bargepole (*cough* ACX-111 *cough*). :wink:

---

