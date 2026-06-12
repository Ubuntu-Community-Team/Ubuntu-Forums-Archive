---
title: "Intel i7. X58 / 1366 motherboard choice?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by KingOfMyCastle on 2009-04-18
Hi! I'm hoping to build a new Ubuntu PC soon, my first. I'm new to Ubuntu/Linux so I'm unsure about how to check hardware compatibility and I don't want to end up with an incompatible kit that forces me to resort to Vista.

I'd like to make the leap to 64bit computing as I want my machine to last 7 years, just like my AMD/Win-XP box has. It's got to be pretty future proof, so need 4GB+ of memory.

So I've plumbed for the 64bit Intel i7 920 (2.66 Ghz) chip. I will install the latest Ubuntu Jaunty 9.04.

Now I've read that the new Ubuntu will work with the i7 fine but is there anyway to work out which 1366/X58 motherboards would also be compatible? There's quite a few options by MSI, Intel, ASUS etc..

As you can tell I'm not sure at all how Ubuntu works with this kind of hardware. Any advice will be appreciated, thanks.

---

### Post by swoll1980 on 2009-04-18
[Ubuntu hardware Database]("ubuntuhcl.org/")

---

### Post by KingOfMyCastle on 2009-04-18
Wow, that's just what I was looking for! Thanks for your help!

---

### Post by KingOfMyCastle on 2009-04-18
Gah, I spoke too soon. It doesn't have any X58 / 1366 motherboards on there yet.

It will help solve all my graphic cards options though.

---

### Post by Abu_Dayya on 2009-04-18
Just note that an nvidia card is possibly better suited for linux than an ati. Nvidia is more friendly than ati when it comes to linux. Although I read on Phoronix.com that the new ATI catalyst propriatary driver has just been released today, and it supports xserver 1.6

---

### Post by jolx on 2009-04-18
> **KingOfMyCastle said:**
> Gah, I spoke too soon. It doesn't have any X58 / 1366 motherboards on there yet.

It will help solve all my graphic cards options though.

Yeah it also doesn't have a full list of graphics cards. The *latest* nvidia driver supports [these video cards]("http://us.download.nvidia.com/XFree86/Linux-x86_64/180.44/README/appendix-a.html"). Although the latest drivers aren't in intrepid's repos but they are in jaunty's (which will be released soon).

Go with a GTX 260 (the one with 216 stream processors) for price/performance although one could easily do with a 9600 GT-ish. If money wasn't an issue, you could add a GTX 260 or two or a couple of GTX 285's or 295's instead.

Regarding the motherboard the asus p6t deluxe has gotten good reviews, but I am unsure of its Linux-friendliness although it should be fine. I saw in [OutOfReach's]("http://ubuntuforums.org/member.php?u=605340") signature that they are using an EVGA X58 SLI so that should work fine as well. You could go with Gigabyte but I think their boards are fugly :P

The core i7 has an integrated triple channel DDR3 memory controller, so you should go with some tri-channel memory which come in 3 x 1GB & 3 x 2GB for 3 gig and 6 gig.

---

### Post by Lionmax67 on 2009-04-18
Hi to all
I'm new on this forums and I'm a beginner user. I've installed UBUNTU 8.04 on my old cumputer (Athlon XP 2600). Now I've a new PC with Nehalem i7 920 installed on a ASUS P6T DELUXE. I've tried Ubuntu 8.10 with the CD trial version (without installation) but i've encountered problems with the lan of the ASUS P6T: i've a wire connection with Internet but it'doesn't work correctly. I need help to understand how to modify in order to Install Ubuntu that i've appreciated so much with my old PC. If someone can help me I'll really appreciate.

---

### Post by Abu_Dayya on 2009-04-18
> **Lionmax67 said:**
> Hi to all
I'm new on this forums and I'm a beginner user. I've installed UBUNTU 8.04 on my old cumputer (Athlon XP 2600). Now I've a new PC with Nehalem i7 920 installed on a ASUS P6T DELUXE. I've tried Ubuntu 8.10 with the CD trial version (without installation) but i've encountered problems with the lan of the ASUS P6T: i've a wire connection with Internet but it'doesn't work correctly. I need help to understand how to modify in order to Install Ubuntu that i've appreciated so much with my old PC. If someone can help me I'll really appreciate.

Asus PT6 board uses the 'Realtek 8111C Gigabit' network interface. Try googling the driver for this interface, and how to load it.

Hope that helps

---

### Post by KingOfMyCastle on 2009-04-19
Wow, thanks for all your help, it's really helping me get to where I need. After your advice and reading the board all day I think I've solved everything apart from my graphics card. Here's my theoretical PC spec so far:

CPU: Inter i7 - inc. hs&f - £240
Motherboard: ASUS P6T SE 1366/X58 - £160
Memory: Crucial 6GB (3x2) DDR3 1333 - £80
Case: Antec Sonata III (with PSU) - £100
HDD: Seagate 1TB - £80
CD/DVD: Basic - £20
Graphics Card: Cheapest compatible NVIDIA - £50

That's just over £700. I plan on investing in a decent graphics card next year so I'll take any old one I can get hold of for now. The mb has 3 x PCIe 2.0 x16 / 1 x PCIe x1 / 2 x PCI slots so can I just put any PCI card in there? Any recommendations?

Also with this set up do you think I'd need thermal paste, extra cables or a fan for the case? I don't intend to overclock at all (for now :) ).

Anyway, I'd be interested to hear what you think.

---

### Post by jolx on 2009-04-19
> **KingOfMyCastle said:**
> I plan on investing in a decent graphics card next year so I'll take any old one I can get hold of for now.

Well you could get an 8400GS for ~£25

> **KingOfMyCastle said:**
> The mb has 3 x PCIe 2.0 x16 / 1 x PCIe x1 / 2 x PCI slots so can I just put any PCI card in there? Any recommendations?

Yeah I suppose so. Just don't put the graphics card in the last pcie slot as that slot only runs at x4, although it probably wouldn't matter.

> **KingOfMyCastle said:**
> Also with this set up do you think I'd need thermal paste, extra cables or a fan for the case? I don't intend to overclock at all (for now :) ).

well the intel heatsink will have pre-applied thermal material, so you wouldn't need any more thermal paste, but if you choose to put some different TIM on, just make sure you wash off the pre-applied stuff first.

I don't know if you will need more fans because the front fan on the Sonata III says "optional". But if it doesn't come with one then I think you should put one there. Although I was thinking that maybe you could go with a Lian Li PC7-B Plus II & a Silverpower SP-SS-500 for ~£108

---

### Post by crazyHedgehog on 2009-06-07
> **KingOfMyCastle said:**
> Wow, thanks for all your help, it's really helping me get to where I need. After your advice and reading the board all day I think I've solved everything apart from my graphics card. Here's my theoretical PC spec so far:

CPU: Inter i7 - inc. hs&f - £240
Motherboard: ASUS P6T SE 1366/X58 - £160
Memory: Crucial 6GB (3x2) DDR3 1333 - £80
Case: Antec Sonata III (with PSU) - £100
HDD: Seagate 1TB - £80
CD/DVD: Basic - £20
Graphics Card: Cheapest compatible NVIDIA - £50


Hi wondered if you ended up buying the p6t se, and if so if you had any trouble (in particular  with audio/networking). I am looking to get the same board, so your feedback is greatly welcome.

Thanks

---

### Post by j-g-faustus on 2009-06-07
I have Asus Rampage II Gene, zero problems the first month.

The one issue I had was how to get temperature readings in Linux, the lm-sensors available through apt-get didn't work.
But that's fixed, here's how: [Asus Rampage II Gene forum]("http://vip.asus.com/forum/view.aspx?id=20090518224331815&board_id=1&model=Rampage+II+Gene&page=1&SLanguage=en-us")

---

### Post by oneiota on 2009-07-12
> **crazyHedgehog said:**
> Hi wondered if you ended up buying the p6t se, and if so if you had any trouble (in particular  with audio/networking). I am looking to get the same board, so your feedback is greatly welcome.

Thanks

And I would like to hear from both of you!  I'm thinking of getting:

[INDENT][I]Intel® Core™i7 Processor i7-920 (2.66GHz) 4.8GTs/8MB Cache

ASUS® P6T WS PROFESSIONAL: NEW ERA CORE i7 WORKSTATION
[/I][/INDENT]
And would like to know your views!

One

---

### Post by FoxFireX on 2009-07-12
I have had BAD luck with asus boards, 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131386](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131386)

The ratings of that board arent that great. I mean 5 star but you know theres a good percentage of 1 and 2 and 3 stars as well.
So the board must give alot of people problems. Assuming you onyl want to pay around 200$ for a motherboard I would go with this board
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813188049](http://www.newegg.com/Product/Product.aspx?Item=N82E16813188049)

look at the reviews and ratings for it.


I'm building a similar PC only mines with:


Antec 1200 Case ($180)
EVGA X58 E758-A1 3-Way Sli Motherboard ($300)
Intel core i7 920 (280$)
A bunch of liquid cooling stuff, tubes and blocks and such, some lights. (300$)
NZXT SEN-001LX Sentry LX Aluminum dual bay fan controller ($70)
CORSAIR CMPSU-850TX 850W ATX12V 2.2 / EPS12V 2.91 SLI Ready ($140$
CORSAIR XMS3 6GB (3 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Timing: 7-7-7-20 ($146$)

Saitek Eclipse III Black USB Wired Standard Backlit Multimedia Keyboard ($80$)
Revoltec FightMouse Advanced Gaming Mouse (40$)

---

### Post by oneiota on 2009-07-12
Thanks FoxFireX - this info is most appreciated.  I have read the reviews and I understand and share your reservations now on the ASUS boards.

I am more interested now in the higher priced EVGA given references to difficulties using the PCI-e slot in the one you linked to.  This is also because I'll be using a pci-e dual graphics card.

You say you are using EVGA X58 E758-A1.  How are you finding that and do you recommend it in general?

---

### Post by FoxFireX on 2009-07-12
Well, yeah I havn't really had much luck with asus boards, The computer I listed above is what I am building soon. 

The EVGA board I listed above, for 300$ is a very very nice board. I can say this because its very popular, and is a customer choice award winning board and have 532 reviews, 62% of those reviews are 5 star ratings. 14% 4 star, 6% 3 star, 4% 2 star, 8% 1 star

Those are good reviews, the 1 star ratings or 2, are moderate for decent products, out of 532 people, your gonna have some boards come dead on arrival and need to be replaced for free by newegg on rare occasion, this can happen anywere. Some other reason for low ratings is, and I quote what a 5 star rater said, "I just scratched my head when I read a "2-egger" comment he expected his board to possibly run on a cool day!!?? You have got to be kiddin me! Sorry you're having hardware issues there bud, but if it's got issues it's got issues, and knowing this board, most likely user issues! This board has been nothing but butter since I got it. It OC's a W3520 like a dream, on meth!"


If you want stuff to run cool you need a case thats good on cooling, fans with good CFM airflow, and if your gonna be overclocking hardcore, Liquid cooling.

When I say overclocking to the point where you need liquid cooling, I mean bumping your i7 core cpu up from 2.66ghz to 4.4 ghz, and YES that is possible its been done tons of times. Don't do it without liquid cooling though.

I remember you speaking of something about a sli issue with the 200$ board? That board is 2 way sli and 3 way sli compatible, just make sure you read the manual.

Somebody noted on one of the board reviews "If you're going to run Tri SLI you're going to want to run the third card on the very last slot and most Tri SLI capable cards are dual slot cooling solutions. Make sure that your case has that extra slot for the last card's second slot or else you'll be forced to run the third card at x4 PCIe rather the x8 offered by the last slot."

They are both great boards.

not to sure when I can have my computer built but hopefully within a month or 2,
and if you want you can wait for me to build mine and I can update you with how good it is, and my thoughts on it.



I mean the asus board is prolly good, but I'm just saying the ratings look like alot of people have had some issues with it, some havnt.

Thats common for every board, Sometimes a board can become damaged form shipping, and malfunction, in which case you have to setup a RMA, and ship the board back to where you got it from and have them send you a new one.

it happens rarly, and thats where some of the low ratings come from, the less low ratings you have the better.

People could get boards and not know that they have been damaged and thats where they think the board sucks, not knowing its a faulty board.


I havn't had to RMA a board yet, meaning I havn't gotten a faulty board yet.

I hope I don't ever get one either.

Newegg have good customer service and shipping, If your a new customer send me a private message before you order I could prolly get you 20$ off on your order. :)




Link to 300$ board which is also on sale for 260$ish right now
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813188046](http://www.newegg.com/Product/Product.aspx?Item=N82E16813188046)



as for the 200$ evga board, you mentioned some difficulties or something about the pci-e and I remember reading a review on the board about somebody having trouble with the x8 sli or something, they most likly are either doing something wrong or the board may be damaged. They need to contact evga or newegg.

---

### Post by jakupl on 2009-07-12
Hello, sorry for the hijacking.
I'm buying a motherboard and a processor, but the processor interface lists "LGA1366" and the motherboard socket is "Intel Socket B (LGA 1336)". Is this compatible?

motherboard ; Asus P6T Deluxe V2
processor ; Intel Core i7 920

Just thought this to be too trivial for its own thread.
Thanks.

---

### Post by FoxFireX on 2009-07-12
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131365](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131365)


Core  type = i7 so yes.

---

### Post by oneiota on 2009-07-13
Thanks again for all the info, FoxFireX.  Unfortunately, I am not well positioned to purchase from newegg in North America or I might have.  Mind you, I'm not a hardware person by any stretch and have no plan to build my own.

The company I have been dealing with wants me to use the Intel DX58SO Motherboard with the i7 CPU.  They also want to use an ATX case (with only a 350W PSU) so that's a couple of strikes against them. I may have to look for someone else in the UK to do the build with better components.

I don't know how/when I might overclock.  But what case and cooling system do you recommend in either case?

---

### Post by mfgrace on 2009-08-16
> **KingOfMyCastle said:**
> Wow, thanks for all your help, it's really helping me get to where I need. After your advice and reading the board all day I think I've solved everything apart from my graphics card. Here's my theoretical PC spec so far:
 
CPU: Inter i7 - inc. hs&f - £240
Motherboard: ASUS P6T SE 1366/X58 - £160
Memory: Crucial 6GB (3x2) DDR3 1333 - £80
Case: Antec Sonata III (with PSU) - £100
HDD: Seagate 1TB - £80
CD/DVD: Basic - £20
Graphics Card: Cheapest compatible NVIDIA - £50
 
That's just over £700. I plan on investing in a decent graphics card next year so I'll take any old one I can get hold of for now. The mb has 3 x PCIe 2.0 x16 / 1 x PCIe x1 / 2 x PCI slots so can I just put any PCI card in there? Any recommendations?
 
Also with this set up do you think I'd need thermal paste, extra cables or a fan for the case? I don't intend to overclock at all (for now :) ).
 
Anyway, I'd be interested to hear what you think.
 
I have almost same equip but with nvidia card. cant get amd64bit install to even start.
what did you end up installing?? 32 or 64 bit?

---

### Post by 0xff on 2009-10-09
> **j-g-faustus said:**
> I have Asus Rampage II Gene, zero problems the first month.

The one issue I had was how to get temperature readings in Linux, the lm-sensors available through apt-get didn't work.
But that's fixed, here's how: [Asus Rampage II Gene forum]("http://vip.asus.com/forum/view.aspx?id=20090518224331815&board_id=1&model=Rampage+II+Gene&page=1&SLanguage=en-us")

Did you try to install Linux on Intel Matrix Storage?

---

### Post by taavikko on 2009-10-09
I have: ASUS P6 DLX V2

It's working nicely.
Only discontent is that it only has 6 sata ports.

---

### Post by j-g-faustus on 2009-10-17
> **0xff said:**
> Did you try to install Linux on Intel Matrix Storage?

No, I haven't tried that.

---

