---
title: "PCI v PCI express: what's the difference?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Lord Stig on 2010-03-01
Sorry, I can't see the New Thread option in community/forum discussions so not sure how to post there. I'm sure it's something obvious!
Perhaps someone can move for me?

I have a Fujitsu Siemens Esprimo Edition P2510 which has an on-board ATi Radeon Xpress 200. I think it's about 3 years old - it's a Pentium D.
I've been out of the loop on video hardware for some years and basically don't know (and can't find from the PC's spec sheets) whether this machine has PCI slots or PCI express. Can't find anything on google that I can understand.

1. What is the difference? 
2. Can I buy a PCI express card and put it in this machine? 
3. Is PCI express only for video cards?
4. Any suggestions for a proven well-supported video card that will work fully out-of-the box on Mint 7/Ubuntu Intrepid through to Karmic.
5. Is PCI express the same as those half-height PCI cards? Guessing not as video cards are huge these days!

There don't seem to be many PCI video cards around, and I only want a basic nvidia or intel chipset model that has TV out. The cheaper the better. I assume I can just buy a PCI express and not worry but no harm in asking.

Can't do ```
lspci
``` (if that helps) as not at that machine right now.

EDIT: don't even need DVI/HDMA - just one of those SVHS ports

---

### Post by halitech on 2010-03-01
PCI is old technology and PCIe (express) is pretty new technology and no, you can't put a PCI card in a PCIe slot. If the spec sheet doesn't say which you have, take a look at the board itself. you should have 2 or more PCI slots and if you have a PCIe slot, it will be back farther from the others.

---

### Post by SwiftDestiny on 2010-03-01
1) PCI Express has much more bandwidth available to it than standard PC ports, you say you knew the market 3 years ago, well from that persepective consider PCI-E as the replacement of AGP

2) It all depends on mobo, with one that age hard to say, 5 years ago it was "new", 3 years ago it was "becoming mainstream" and now its standard. It is a different form factor though so physically looking should tell you.

3) Nope, I have a PCI-E Sound Card, although it is only PCI-E x1 it uses the same port. You can also get PCI-E TV cards, network cards, SSD's and USB3 controllers. 

A video card will normally be PCI-E x8 or x16, but if you have one full size x16 port don't worry, it can take anything :) Your mobo will autodetect and configure the right option

4) I'm a Linux nub, I can talk your ear off about hardware, but I'll leave question 4 to the people who belong here

5) Guessed right :) Any card can be half height PCI or PCI-E, there just aimed at HTPC's where space is an issue. You look at some of the modern GPU's and believe me, you could do serious damage with one :P

As for a suggestion of a PCI card, all the ones that spring to mind aren't around anymore. 

I would just pop the side off your case, and you should see a slot a different form factor, then try and work out if its either AGP (just dying 3 years ago) or PCI-E and take it from there. PCI graphics cards have been dead and buried since the day's of the Voodo cards I believe ;)

---

### Post by pirateghost on 2010-03-01
[http://www.directron.com/expressguide.html](http://www.directron.com/expressguide.html)
[http://en.wikipedia.org/wiki/PCI_Express](http://en.wikipedia.org/wiki/PCI_Express)

1. slot size, bandwidth, architecture
2. I couldnt find anything on your particular model, but it would do you best to power it down, open it up and see what kind of slots are in it (refer to the links for pictures of the slots) 
3. no.  many raid cards, network cards, and sound cards take advantage of this type of slot.  basically pci is slowly dying out.
4. nvidia would be my first preferred video card for any linux distro
5. no.  refer to the links and number 1.  size of the video card means nothing when you are talking about the pci/pci-ex architecture driving it.

---

### Post by KegHead on 2010-03-01
Hi!

Check and then double check what your mobo accepts.

I purchased a PCI/e video card and it didn't fit my pci slot on my mobo.

Check again!

KegHead

---

### Post by admiralspark on 2010-03-01
Hello,
Congratulations on being a member of the* _Integrated Graphics_* family. You Radeon Xpress 200 is a member of one of ATi's integrated chips families, and specifically is their mainstream 200 series chip. In other words, it's one of the most common graphics chips made in the last 5 years. 
The only thing google turned up is that your case, apparently, is a Mini-tower. I';m going to guess that if you open it up, if it even has an open slot on the MB it will be pci-express. Between the two brand you mentioned, I'd go for an nVidia card, and search the forums for a recommended card. A list of supported graphics cards can be found on the site help pages. 
Maybe more specifics on what you'll be using it for? (besides tv, obviously)

---

### Post by Lord Stig on 2010-03-02
Wow! Lots of information from everybody, and all supplied very quickly. This is excellent, thank you all!
I can see the difference in connectors and have a better idea about the market now. I'll check tonight to see if I have PCI express or just PCI. Possibly both.

In response to admiralspark, I don't really intend to do much beyond having this machine output video to my TV. My DVD player plays Div-X files but I have some Quicktime files I'd like to be able to watch on my TV. I want to spend as little as possible and make use of as much hardware I already have as possible. I don't need gaming from the card but I do want it to be as Linux compatible as possible, if that isn't too nebulus a term to use, so will probably go for an nVidia chipset to avoid driver issues. (I am running Hardy rather than Karmic due to the frglx driver seemingly not being supported in the kernels of later Ubuntu distros, as it was one click to install the driver on Hardy).

@swiftdestiny - I remember Voodoo cards!! - my first 3D card was a Voodoo 2 3DFX with 12MB RAM. I was amazed at seeing hardware 3D support and my previous card had been a pretty abominable 4MB S3 Virge (software 3D!!).

My TV is standard definition and the only inputs it has are composite, SCART and S-video. 
1. A lot of cards seem to have just the VGA-type connector or the HDMI and DVI interfaces. Do you think I'll have trouble getting an S-Video card?
2. If I find an appropriate card, can I just plug an S-Video lead into it and rely on the hardware to switch or mirror the output direct through that lead or is there some OS intervention required? If so, what would I need to do?

Sorry to add more questions. Really appreciate the responses from everyone so far.

---

### Post by cascade9 on 2010-03-02
1- Others have answered this already, but as for why there are things other that just video cards in PCIe its because of the much larger bandwidth PCIe has. PCI is limited to (theoretical) 133 MB/sec, which pretty much the bandwidth of gigabit LAN. Other bits and pieces like the extra bandwidth of PCIe, in particular RAID cards. Some stuff, like sound cards, will never need the bandwidth of PCIe but are moving toward it because PCI is slowly being phased out. 

2- No. I've managed to find the spec sheet for the ESPRIMO Edition P2510, there is no PCIe slots (typical 'budget' corporate board, its got the spots for a PCIe x1 and a PCIe x8/16 but they havent been soldered in) see here- 

[http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/professionalpc/ESPRIMO/Value/EditionP2510.htm](http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/professionalpc/ESPRIMO/Value/EditionP2510.htm)

3- No, see answer 1, etc.

4- No add-on card will work fully out of the box with ubuntu. Adding the nvidia drivers (and ATI) is pretty painless though. 

5- Nope, but there are half-height PCIe cards as well.  

BTW, no all modern video cards are huge- the gaming cards sure are though. 

As for what to get...I'd get a Geforce 8400 GS or 9400 GT. There are models around with s-video out. I have no idea where you would be sourcing your cards from, or else I would check there for you, but you can always got to newegg, and pick a few of the right options and you'll get a list like this- 

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609642%201232814103&bop=And&ShowDeactivatedMark=False&ActiveSearchResult=True&Order=PRICE](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609642%201232814103&bop=And&ShowDeactivatedMark=False&ActiveSearchResult=True&Order=PRICE)
That is all the cards newegg stocks in PCI, with svideo (and HDMI) out. While that might not help you much, its handy to know what models do have S-video out. Whatever you do, DONT get less than a 8xxx series nVidia card, those models and later have VDPAU (hardware video decoding).

---

### Post by sandyd on 2010-03-02
if your getting a pci card, a cheap one w/ s-video is the geforce 5500 fx.

---

