---
title: "Dual Video Cards (nVidia)"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by LitUpAgain on 2010-11-14
[FONT=Times New Roman, serif]I have been looking around for info about dual video cards in Ubuntu/other distros, and I've seen a variety of seemingly conflicting information.[/FONT]
 
 [FONT=Times New Roman, serif]Some sources mention the nVidia drivers now automatically handle multiple video cards.[/FONT]
 [FONT=Times New Roman, serif]But other sources mention you (always?) have to manually config it.[/FONT]
 
 [FONT=Times New Roman, serif]I tried a test box with a 9400GT card in a PCI-Ex slot & a 5200FX card in a PCI slot and that didn't happen. It took me a bit before finding the xorg.conf file and fighting with it. (And then later realizing the nVidia driver DLs were separate for these cards, and thus required a bit more configuring if it was possible at all.)[/FONT]
 
 [FONT=Times New Roman, serif]A bit after that I found a thread mentioning multiple cards wouldn't work unless they were all 8xxx or above.[/FONT]
 
 [FONT=Times New Roman, serif]If I can make the 9400gt/5200fx thing happen, that'd be great and an important learning experience. But I'm eventually looking at getting a true dual video card beast* to run 3 or 4 monitors. Two of these (#1 & #2) will be 16:10 and the last one or two will be mixed. (#3 will be 16:9, #4 will be either 16:9 or 4:3.)[/FONT]
 
 [FONT=Times New Roman, serif]I only need spanning on monitors #1 & #2, so (I think) a regular Twinview setup should be OK. (With multiple X Screens...?)[/FONT]
 
 [FONT=Times New Roman, serif]Any personal experience with this sort of setup (or links to threads I missed) would really help. Although I may put other OSs on this box, my main concern is Ubuntu. [/FONT] 
 
 [FONT=Times New Roman, serif]Thanks![/FONT]
 

 [FONT=Times New Roman, serif]* These would be either two nVidia 250gts (personal preference), or two 465gtx's &#8211; I'm choosing these as I might start playing around with the Hackintosh thing at some point.

[/FONT]

---

### Post by cariboo on 2010-11-14
I would suggest you're going to have nothing but problems trying to get your setup to work, as the cards use different drivers. 

It would help if you told use what version of Ubuntu you are using, as it makes a lot of difference in what drivers we suggest you use.

---

### Post by GabrielYYZ on 2010-11-15
i thought you needed the 2 cards to be of the same model and series (e.g. two 9400GT or two 5200FX) for it to work. even if they are from different manufacturers, have different BIOS revisions or clock speeds.

edit: wait, this isn't for SLI, is it? if it isn't, disregard my post...

---

### Post by LitUpAgain on 2010-11-15
Thanks for the replies.

I'm using 10.10 currently, but I'm going back to 10.04.

This isn't for SLI (9400gt on PCI-Express, FX5200 on PCI), although that's something I might consider with the dual 250gts'/465gtx's when that time comes. (Early next year - right now is the research phase.) My biggest concern for this setup is getting the three monitors going.

(Back to the current setup) Everything I'm reading so far seems to indicate the fx5200 is stuck in the legacy drivers. But, again, if there's a way around that, I'm up for it.

---

### Post by cSquall on 2011-03-02
> **GabrielYYZ said:**
> i thought you needed the 2 cards to be of the same model and series (e.g. two 9400GT or two 5200FX) for it to work. even if they are from different manufacturers, have different BIOS revisions or clock speeds.

edit: wait, this isn't for SLI, is it? if it isn't, disregard my post...

@GabrielYYZ: Can you elaborate on the requirements for SLI and how well it is supported in Ubutnut 10.10 and newer? Is there some place with an 'official' description of SLI support, do's and don'ts?

I've been searching all over the forums for recent information on this to see if progress has been made.

Thanks!

cSquall

---

### Post by seawolf167 on 2011-03-02
[Here ]("http://www.geforce.com/#/Hardware/Technologies/sli/supportedgpus")is the current list of supported SLI cards.

I haven't had any problems with my config, but then again, I have two of the exact same cards and have it activated through their graphics suite. I don't know if or how you'd be able to config two different cards with two different drivers.

---

### Post by Seinfeld on 2011-03-07
Hi..

I really appreciate your advice here. I am using two monitors with my dual head nvidia GF Asus 8600 GT. No problems so far. 
Now I really need to add one or two monitors to work in TwinView to expand my desktop. My motherboard does support dual video cards (Intel DX58SO). Can I add another card to my motherboard and just simply plug the third monitor ??
Also, could I use an Asus 7600GS or should it be an 8xxx as well ??

Thanks v. much in advance :)

---

### Post by Seinfeld on 2011-03-07
Hi..

I really appreciate your advice here. I am using two monitors with my dual head nvidia GF Asus 8600 GT. No problems so far. 
Now I really need to add one or two monitors to work in TwinView to expand my desktop. My motherboard does support dual video cards (Intel DX58SO). Can I add another card to my motherboard and just simply plug the third monitor ?? No xorg.conf editing necessary ?? I am using Maverick..
Also, could I use an Asus 7600GS (got it on ebay now :) ) or should it be an 8xxx as well ??

Thanks v. much in advance :)

---

