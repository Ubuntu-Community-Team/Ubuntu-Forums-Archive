---
title: "Hi all, Newbie Hardware question for Dell GX260"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by derryt on 2010-01-03
Hi everyone, I've recently installed Karmic, and love using it, but I'd like to use compiz-fusion to really get some customisation going.

The problem is, as in the title, I have a Dell GX260, and my google-fu is throwing up lots of contradictory information. Many people seem to think that only a low profile 4xAGP video card will work, however, according to my specs on the Dell support site, I have a PCI slot

[http://support.dell.com/support/edocs/systems/opgx260/en/ug/specs.htm#1110653?ACD=10550055-3342876-&AID=3342876](http://support.dell.com/support/edocs/systems/opgx260/en/ug/specs.htm#1110653?ACD=10550055-3342876-&AID=3342876)

Mine is the small form factor unit, on this basis, am I actually able to use a PCI card?

I'm still quite new to hardware beyond hard drives so any advice very gratefully received!

Regards,

Derry

---

### Post by Pascal11110 on 2010-01-03
Could you actually post your serial/model numbers on here instead? I work at a computer shop and we have 2 kinds of       gx260's there and there might even be a third kind. The large dells would be about the size of a regular desktop and do have a full pci slot and agp or pci-e video. The smaller form-factor dells have a low profile agp video slot, but have a expansion card that allows for two full sized pci cards.

---

### Post by dmaxel on 2010-01-03
I am not exactly sure how Ubuntu would react to graphic cards in PCI slots. However, all motherboards (or at least all that I've ever come across) have PCI slots. So in your case, as you are saying, both AGP and PCI graphics cards could fit into your motherboard. It's best to open the case for your computer though and make sure that you have a space available.

---

### Post by starcraft.man on 2010-01-03
If I read your post right, your wondering whether you can upgrade your graphics card to a PCI-e card. The answer is no. That motherboard is too old, it still uses DDR1 and a pentium 4 chip. I understand confusion, there are in fact several sister PCI specifications, only PCI-e (released in 2004-2005, if you bought your pc before I can assure you it does not have this) is designed for graphics. See disambiguation [here]("http://en.wikipedia.org/wiki/PCI_Express"). There are a few means of getting pcie on such old cards, but not natively and I don't advise them.

Instead I'd advise you to buy a new computer if your wanting to use pcie cards and modern components. I know spending more money isn't what people want to hear. An additional complication is the small form factor of that case, I doubt you could fit some of the more recent graphics cards in it.

---

### Post by derryt on 2010-01-03
Pascal11110 - it's this one:

[http://images.google.co.uk/images?hl=en&source=hp&q=dell+gx260+small+form+factor&btnG=Search+Images&gbv=2&aq=f&oq=](http://images.google.co.uk/images?hl=en&source=hp&q=dell+gx260+small+form+factor&btnG=Search+Images&gbv=2&aq=f&oq=)

As I understand it this is definitely the small form factor one.

I do have slots for both AGP and PCI, but by the sounds of it, I'm not likely to get a suitable upgrade for this machine? I don't mind if it's AGP or PCI (the old kind!) as long as compiz will run on it.

Otherwise, will have to wait till my mum gives me my laptop back and then i can mess around with that!

Thanks for the replies so far guys

---

### Post by Pascal11110 on 2010-01-03
Ok, so your is the one with the low profile agp slot and the two full size pci slots. First thing is that an AGP video card will be faster than a pci card. AGP was made specifically to hold a video card and be faster than PCI slots. THe best video card that I can find that your computer would support would be [This one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814139165"), but I do not know if it is enough to run compiz. I have never used it before, and I don't want to advise you to get something that won't solve your problem. But since it's nvidia its driver should be built into the kernel. I'll do a little more research for you though.

---

### Post by Pascal11110 on 2010-01-03
Actually it will support these as well,a nd these are a little better than the one I just posted :[http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=28&sel=Detail;229_176_48674_48674,Detail;55_158_2064_2064,Detail;236_1239_3359_3359]("http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=28&sel=Detail;229_176_48674_48674,Detail;55_158_2064_2064,Detail;236_1239_3359_3359")

---

### Post by derryt on 2010-01-03
Thanks Pascal, just out of interest, how can you tell visually if a card is low profile or not?

---

### Post by Pascal11110 on 2010-01-03
Well people in [this thread]("http://ubuntuforums.org/showthread.php?t=732391") say that it will at least run compiz so I think one of [these]("http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=28&sel=Detail;229_176_48674_48674,Detail;55_158_2064_2064,Detail;236_1239_3359_3359") video cards should solve your problem.

---

### Post by Pascal11110 on 2010-01-03
Seems to work ok for this guy as well [http://www.youtube.com/watch?v=A0AreUCI-eI]("http://www.youtube.com/watch?v=A0AreUCI-eI")

---

### Post by Pascal11110 on 2010-01-03
Visually, the metal plate on the front of the card will be half the height of the plate of a normal sized card. You can find low profile cards online by making one of your search options (I know newegg and tigerdirect have this option) form factor: low profile

---

### Post by derryt on 2010-01-03
thanks for the searching, I've found this online and the store in my town has one in stock, do you think this would handle it?

[http://www.maplin.co.uk/Module.aspx?ModuleNo=223892&C=Froogle&U=223892&T=Module](http://www.maplin.co.uk/Module.aspx?ModuleNo=223892&C=Froogle&U=223892&T=Module)

Seems to be a rebranded FX5200, whch seems to run compiz ok on other threads

edit: just noticed it doesn't seem to be low profile, so wouldn't work unless I left my case open i guess!

---

### Post by starcraft.man on 2010-01-03
I'd just like to chime in after a lot of posts from pascal, least before I run to get lunch fixed. I agree that you probably could get decent performance from a 6200, the 6 series from nvidia was decent (I use to get pretty good compiz performance from a 6800GT). Those cards are a bit underpowered compared to modern 8 series though, todays rough standard. If you have the money and fancy it for the desktop then be my guest.

I will say that compiz is a bit overrated, don't turn on all the effects or you'll spend more time starting and playing with desktop then doing work. So ya, get card if ya like. One suggestion is you'll probably want to turn filtering down and tweak options.

Install the compizconfig package like so:

```
sudo apt-get install compizconfig-settings-manager
```

Then System > Preferences > Compiz Settings > General OPtions > Textur Filter to Fast. Tweak other settings to get better performance.

That's my say, if your notebook has a better gfx card then the 6200 you might just wait for it.

Edit: I don't recommend the FX generation, it was poor quality IMO and I'd be remiss to tell ya to buy something from that run. FX also I'm not sure if it has high enough support for openGL2.1 required for compiz, I could be wrong. 6 series I'm sure works on other hand.

---

### Post by cascade9 on 2010-01-03
> **Pascal11110 said:**
> Ok, so your is the one with the low profile agp slot and the two full size pci slots. First thing is that an AGP video card will be faster than a pci card. AGP was made specifically to hold a video card and be faster than PCI slots. THe best video card that I can find that your computer would support would be [This one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814139165"), but I do not know if it is enough to run compiz. I have never used it before, and I don't want to advise you to get something that won't solve your problem. But since it's nvidia its driver should be built into the kernel. I'll do a little more research for you though.

LOL, newegg data-droid skillz need work. That 5200FX is NOT the 'best' AGP low profile card you will find. 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814139044](http://www.newegg.com/Product/Product.aspx?Item=N82E16814139044)

True, AGP is made to be faster than PCI- but you will only notice that in games. I would get a 8400GS, PCI myself, get the benefit of VDPAU and a more powerful core.

---

### Post by Bartender on 2010-01-03
I looked into GX260 video solutions a few weeks ago and believe I landed right where cascade9 did.

Here's the problem.  That's an awful lot of money for an older graphics chipset, and you don't even get a DVI output.  But you're boxed in with an oddball PC like that, so your choices are pretty slim.  Only you can decide if the money's well spent or not.  I bought the GX260 for $20, and wasn't gonna spend that kind of money for a half-*** solution.  Gave it to my Dad's girlfriend, who will not be asking how to run compiz :)

---

