---
title: "Can i flash dvd-rw in linux / ubuntu?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by geekyhawkes on 2009-05-26
Pretty much as per the title really, I need to reflash my SATA dvd drive to RPC1 so i can play my various DVDs from region1/2.  Is there a way I can do this without resorting to a Microsoft product?  

If it matters the drive is an LG and I have already found the binary file on the rpc database, its just the flashing bit in linux im missing.

---

### Post by halitech on 2009-05-26
most bios flash utilities I've seen are usually written requiring windows. Do you have any instructions from the LG website on how they say to do it?

---

### Post by geekyhawkes on 2009-05-27
Sadly all the utils i can find are windows based hence my post really.  Is there any experiance with WINE and  dvd flashing?  Seems a bit risky to me using WINE but im not sure why.

---

### Post by durand on 2009-05-27
> **geekyhawkes said:**
> Sadly all the utils i can find are windows based hence my post really.  Is there any experiance with WINE and  dvd flashing?  Seems a bit risky to me using WINE but im not sure why.

I think you can change the region with a linux program but I can't remember what it's called. I'll try and find it.

EDIT: Found it, its called [regionset]("apt://regionset").
```
sudo regionset
```

---

### Post by jmszr on 2009-05-27
geekyhawkes,

To add to durand's post: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes) .

---

### Post by geekyhawkes on 2009-05-27
Unless i have missed something regionset doesnt change the rpc2 restrictions of 5 region changes before the drive becomes locked to that region!?  I was hoping to be able to switch regions as required between my R1 and R2 dvds.

---

### Post by durand on 2009-05-27
I think there is a maximum of 5 switches whatever method you use.

---

### Post by kamitsukai on 2009-05-27
> **geekyhawkes said:**
> Unless i have missed something regionset doesnt change the rpc2 restrictions of 5 region changes before the drive becomes locked to that region!?  I was hoping to be able to switch regions as required between my R1 and R2 dvds.

Yep I had this problem and never found a solution except to buy a new dvd-rw which luckily is normally about £15.99 for a 22x write speed with built in lightscribe (which I've never used:p)
[B][I]
**EDIT**[/I][/B]

Noticed you were in the UK (England...as in not New England USA??) so I thought I'd post a link to the drive I bought

> [http://www.play.com/PC/PCs/-/672/879/-/6579352/LG-GH22LP20-22x-Internal-LScribe-Black-Bare-DVD+-RW-Drive-Black/Product.html?searchtype=genre](http://www.play.com/PC/PCs/-/672/879/-/6579352/LG-GH22LP20-22x-Internal-LScribe-Black-Bare-DVD+-RW-Drive-Black/Product.html?searchtype=genre)

---

### Post by durand on 2009-05-27
> **kamitsukai said:**
> Yep I had this problem and never found a solution except to buy a new dvd-rw which luckily is normally about £15.99 for a 22x write speed with built in lightscribe (which I've never used:p)
[B][I]
**EDIT**[/I][/B]

Noticed you were in the UK (England...as in not New England USA??) so I thought I'd post a link to the drive I bought

I normally use ebuyer for hardware like that. You could just have one drive for one region and another for the other region or you might be able to find a universal drive. I know that the dvd player we have is so old that it doesn't even know about regions and plays everything :D

---

### Post by kamitsukai on 2009-05-28
> **durand said:**
> I normally use ebuyer for hardware like that. You could just have one drive for one region and another for the other region or you might be able to find a universal drive. I know that the dvd player we have is so old that it doesn't even know about regions and plays everything :D

I bought my one from ebuyer but I posted that link because it works out cheaper from play.com if your only buying the dvd-rw as it's free postage;)

on another note he will only need the one drive as linux doesn't actually ask for region codes there just ignored:)

PS: I like your Teeworlds avatar =]

---

### Post by geekyhawkes on 2009-05-28
It is not true about 5 switches what ever method you use.  If you reflash the firmware to RPC1 then you can switch as required.  I have foudn binflash as a linux app that will support reflashing the firmware in my drive so solving the region issue.

---

### Post by durand on 2009-05-28
> **geekyhawkes said:**
> It is not true about 5 switches what ever method you use.  If you reflash the firmware to RPC1 then you can switch as required.  I have foudn binflash as a linux app that will support reflashing the firmware in my drive so solving the region issue.

Hmm ok, that's new to me.

---

