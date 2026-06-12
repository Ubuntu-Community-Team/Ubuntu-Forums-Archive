---
title: "Half-height graphics card suitable for Ubuntu"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by Reljoy on 2011-01-14
Can anyone recommend a half-height graphics card that will work perfectly with Ubuntu 10?
I have looked at [http://community.linuxmint.com/hardware](http://community.linuxmint.com/hardware) but I don't know if any of the ones listed are half-height.

---

### Post by elgordodude on 2011-01-14
Depends on whether you just want to send emails or if you need cuda, cal, or fermi for some particular game or application. Older / slower cards should install easily through **Additional Drivers** Newer cards require a bit more tweaking, but they will work.

If you can find something appropriate and low-profile, someone should be able to confirm that it works.

---

### Post by Reljoy on 2011-01-14
Well, I am not a gamer. The odd game of Tux Racer is about my limit. But I do like the compiz effects. So I was planning on getting a fairly cheap card - I just want to make sure it will work before I buy it. It's for a Dell Optiplex GX260.

---

### Post by coffeecat on 2011-01-14
> **Reljoy said:**
> Well, I am not a gamer. The odd game of Tux Racer is about my limit. But I do like the compiz effects. So I was planning on getting a fairly cheap card - I just want to make sure it will work before I buy it. It's for a Dell Optiplex GX260.

Hi. You'll have to do a search for a supplier in your region of the world (wherever that is), but here's a UK link for the card I'm using:

[http://www.ebuyer.com/product/239012](http://www.ebuyer.com/product/239012)

As far as I'm concerned it has everything going for it. It comes complete with two LP brackets - one for VGA only and one for DVI and HDMI - as well as the standard bracket. It is passively cooled = SILENT. And it has the ATI Radeon HD4350 chipset which works out of the box, compiz included, with the open source driver in Lucid, Maverick and Natty. You don't have to bother with the proprietary driver which you would if you bought an nvidia card.

Oh, and it's inexpensive. £30 in the UK. You'll probably get it for that many dollars in the US.

**EDIT:** by the way, if you need to use the VGA connector you'll probably need a spare PCI slot for the second LP bracket. The VGA socket is on a flexible cable. See the illustration for what I mean.

---

### Post by cascade9 on 2011-01-14
> **Reljoy said:**
> Well, I am not a gamer. The odd game of Tux Racer is about my limit. But I do like the compiz effects. So I was planning on getting a fairly cheap card - I just want to make sure it will work before I buy it. It's for a Dell Optiplex GX260.

Bad news- that uses AGP for video, not the newer PCIe system.

[http://support.dell.com/support/edocs/systems/opgx260/en/ug/specs.htm](http://support.dell.com/support/edocs/systems/opgx260/en/ug/specs.htm)

 AGP cards are more expensive for much older technology than PCIe. About the only AGP card that is even worth looking at that will fit in your system is an AGP nVidia 6200. 

A PCI card should work as well, but I've heard of people having no end of toubles with PCI cards in systems with that chipset, so I'm not convinced that its worth even trying.

---

### Post by coffeecat on 2011-01-14
> **cascade9 said:**
> Bad news- that uses AGP for video, not the newer PCIe system.

Oops. Thanks for noticing that. 

@Reljoy, ignore my post. That's a PCIe card I describe.

---

### Post by Frogs Hair on 2011-01-14
I prefer Nvidia products , include the words low profile in your search terms That should narrow things down a bit.

---

### Post by Reljoy on 2011-01-15
I am thinking of getting a nVidia Geforce 6200 256MB DDR2 AGP Low Profile. From what I read, it only comes with a full sized ATX bracket. It is for a Dell Optiplex GX260 which is very slim. Would I be right in thinking I only have to remove the full sized bracket and it will fit right in easily? That's what it seems to say on [http://cgi.ebay.com.au/nVidia-Geforce-6200-256MB-DDR2-AGP-Low-Profile-Heatsink-/230572865927?pt=AU_Components&hash=item35af36b987](http://cgi.ebay.com.au/nVidia-Geforce-6200-256MB-DDR2-AGP-Low-Profile-Heatsink-/230572865927?pt=AU_Components&hash=item35af36b987)

---

### Post by cascade9 on 2011-01-15
AU$? Are you in australia Reljoy? 

I might be able to find you a better deal somewhere. I know of places that are selling new 6200s cheaper than that, and there are 2nd hand places around as well.

---

### Post by Reljoy on 2011-02-10
I got a second hand card from a place where the guy cut the bracket and shaped the end, and installed it for me for $20. Tested it in the shop - worked perfectly.

---

