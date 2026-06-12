---
title: "Do I need a new video card?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by nevaeh on 2009-11-08
Hiya!
I'm new to the forum and ubuntu so go easy on me!
I just recently had a really really bad XP crash which resulted in me having to make a few hard decisions on my operating system.
Im glad to say that I made the choice to linux coz its great!
However I'm getting a few issues for which I need some advice desperately:

My Firefox is running really slow - when I scroll the page its very jerky and takes some time to load up stuff.

A friend of mine mentioned that it could be a graphics card issue but I dont know anything about it because my ex installed it years ago....!

What you think?
Do I need a new card?

thnx

---

### Post by Waappu on 2009-11-08
Hi,

Type to terminal```
lspci
```and post result here

---

### Post by nevaeh on 2009-11-08
Hi Wappu!
thanks for the reply.

00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

---

### Post by Waappu on 2009-11-08
Hi,

So you have ATI Radeon 9200 video card.

You could try search from google how tweak parametters for that card, and see if it helps to performance.


Edit.
Check this if any tips
[http://www.uluga.ubuntuforums.org/showthread.php?t=1308027](http://www.uluga.ubuntuforums.org/showthread.php?t=1308027)

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by nevaeh on 2009-11-08
Oh oki!
thank you for the advice and the link waappu, I'm going to have a busy night now lol!
huggles**

---

### Post by Waappu on 2009-11-08
Hi,

I did have that card, and tweaking xorg.conf I did get deacant performance.
Of course that card is quite old.

---

### Post by Marlonsm on 2009-11-08
Have you installed the right drivers for it?
Take a look at System > Administration > Hardware drivers. If there is not video driver in use, activate one (usually the latest is the best).

---

### Post by this_is_richard on 2009-11-08
Hi nevaeh.

I think I had the same problem with my laptop, which has an older Radeon card.  I corrected it using the fix available here:  

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

It's really easy (I could do it) and I learnt a little bit about xserver too!

---

### Post by this_is_richard on 2009-11-08
Whoops, I see now that fix doesn't work for karmic, only jaunty.  I do think that your problem is that which is described on that page though.  Apologies for the mistake...

---

### Post by nevaeh on 2009-11-08
lol thanks for the help richard ~ I'm not gonna pretend I have *any* clue what I'm doing, so any advice is great!

marlonsm ~ thanks for laying out the process for me :) I checked what you suggested and it came up with no drivers! 
I am now on the prowl for the right download...

;)

---

### Post by halitech on 2009-11-08
Unfortunately you won't find any downloads that will work in Karmic. ATI dropped support for older cards and the last one that supports the 9200 doesn't work in Karmic. Basically if you have graphics, you have the only driver available for your card.

---

### Post by nevaeh on 2009-11-09
Thanks for the update Halitech ~ after spending most of the night looking, I've come to that conclusion also. meh
No worries thos! Its high time I looked at a new card and psu[SIZE=1].
;)
(..and motherboard[/SIZE] [SIZE=1]and processor and hard-drive lol)[/SIZE]

---

### Post by halitech on 2009-11-09
> **nevaeh said:**
> Thanks for the update Halitech ~ after spending most of the night looking, I've come to that conclusion also. meh
No worries thos! Its high time I looked at a new card and psu[SIZE=1].
;)
(..and motherboard[/SIZE] [SIZE=1]and processor and hard-drive lol)[/SIZE]

If your motherboard only supports AGP video cards then yes, you may want to look into a full system upgrade as PCI-e cards are pretty inexpensive now while AGP cards are pretty expensive. I just bought an ATI HD 4350 which works great (I know, boo hiss on ATI but I've always had good luck with them). The Nvidia cards are better supported if you have the extra cash for one of them.

---

### Post by fatcrab on 2009-11-09
Have you shut off visual effects?

---

### Post by nevaeh on 2009-11-09
thankls **Halitech** :) yea its shocking the price of AGP cards compared to PCI what the hell happened to the market while my back was turned!?!
Im defo gonna have a looksee at some PCI motherboards, but given my level of sheer screw-up-ability, ill prolly have to buy an off the peg PC (*I* know, I know...)
 
Hi **fatcrab**! I've selected 'none' under effects tab in firefox...is that what you mean?

---

### Post by fatcrab on 2009-11-09
No, R-click desktop---L-click change desktop background----L-click visual effects

---

### Post by RochJer on 2009-11-09
> **nevaeh said:**
> thankls **Halitech** :) yea its shocking the price of AGP cards compared to PCI what the hell happened to the market while my back was turned!?!
Im defo gonna have a looksee at some PCI motherboards, but given my level of sheer screw-up-ability, ill prolly have to buy an off the peg PC (*I* know, I know...)
 
Hi **fatcrab**! I've selected 'none' under effects tab in firefox...is that what you mean?

I believe what this is meant to say is that you will probably need to check on System>Preferences>Appearance>Visual Effects and try changing to Normal or None and see if your Graphic performance improves. Enhanced desktop effects require a lot of hardware acceleration so you may need to consider changing the video card effects so use this option.

---

### Post by LowSky on 2009-11-09
AGP style graphic cards are still made and for kinda cheap, here is a list of Nvidia cards that will work better than ATI (like you currently have)

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609639+1305520548&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=48&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609639+1305520548&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=48&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

---

### Post by nevaeh on 2009-11-09
[SIZE=2]OK it turns out that my settings were already on 'none' so I guess it has to be my GFX card!

LowSki ~ thanks for the link I think I found a few compatible cards:

[/SIZE][FONT=Trebuchet MS][SIZE=2][http://www.argoncomputing.com/powercolor-x1650-pro-512mb-agp-pr-16733.html](http://www.argoncomputing.com/powercolor-x1650-pro-512mb-agp-pr-16733.html)[/SIZE][/FONT][SIZE=2]
[/SIZE] 
  [FONT=Trebuchet MS][SIZE=2]&[/SIZE][/FONT]

[SIZE=2][http://it247.com/product/1/GAICA00B/471846200-7753_Gainward_BLISS_6800GS_AGP_TV-DVI_Golden_Sample-graphics_adapter-GF_6800_GS-512_MB.html?IT247Tracked=true&channeltype=GraphicsCards&level1cat=Components&level2cat=GraphicsandSoundCards&prodid=2389-471846200-7753&campaign=googleshopping](http://it247.com/product/1/GAICA00B/471846200-7753_Gainward_BLISS_6800GS_AGP_TV-DVI_Golden_Sample-graphics_adapter-GF_6800_GS-512_MB.html?IT247Tracked=true&channeltype=GraphicsCards&level1cat=Components&level2cat=GraphicsandSoundCards&prodid=2389-471846200-7753&campaign=googleshopping)
[/SIZE] [SIZE=2]
whaddya fellas think?[/SIZE][SIZE=2] yay or nay?
[/SIZE]:)
 [SIZE=2]
[/SIZE]

---

### Post by fatcrab on 2009-11-09
I would go with the nvidia.I have never had much luck ati cards in windows or linux.How much ram do you have?

---

### Post by nevaeh on 2009-11-09
umm about 2 gigs worth?

---

### Post by fatcrab on 2009-11-09
Thats great.Most linux distros like 512gigs or better.I just built a pc to put 9.10 on and used a nvida 7300GT .It works much better than the one I have a ati 9600 in running 9.04.I will soon be changeing that to a nvidia.

---

### Post by nevaeh on 2009-11-10
woohoo!
Just thought id share this little gem of advice which worked for my Karmic setup.
If your Firefox is loading and scrolling slow, then try this:

[LIST=1]
[*]Open a new tab by typing **Ctrl-t**
(That&#8217;s the Ctrl key on your keyboard and the letter t key at the same time)
[*]Enter **about:config** in the address bar of Firefox
[*]Enter **ip** into the **Filter:** text box
[*]Look for the **network.dns.disableIPv6** entry in the table below the **Filter:** text box
[*]Double click the **network.dns.disableIPv6** entry
[*]Restart Firefox
[/LIST]
kudos to:
[http://techxplorer.com/2007/02/22/slow-browsing-using-firefox-on-ubuntu/](http://techxplorer.com/2007/02/22/slow-browsing-using-firefox-on-ubuntu/)

:KS

**thanks to all who replied here with advice.

xXx

---

### Post by sixthwheel on 2010-03-16
I have the same video card...ATI 9200 Radeon, and gave up looking for an updated driver.

I too will soon be purchasing a new video card.
My computer has AGP support, and I think it has PCI support as well.

Here are the specs to it..could one of you gurus figure out if I do indeed have PCI support?
Thanks.

**Product MPN**

               MPN                       PCVRS530GFS                  **Key Features**

               Form Factor   [ ]("http://www3.shopping.com/xWI?lid=1&fid=451&aid=3023")                           Tower                          Processor                       Intel Pentium 4 3 GHz                          Installed Memory                       512 MB (DDR SDRAM)                          Operating System   [ ]("http://www3.shopping.com/xWI?lid=1&fid=451&aid=14426")                           Microsoft Windows XP Home Edition                          HDD Size                       160 GB                          Recommended Use                       Home Use                  **Processor**

               Processor Number                       530                          Processor Type   [ ]("http://www3.shopping.com/xWI?lid=1&fid=451&aid=3021")                           Intel Pentium 4                          Processor Speed   [ ]("http://www3.shopping.com/xWI?lid=1&fid=451&aid=14464")                           3 GHz                          Processor Manufacturer                       Intel                          Processor Upgradability                       Upgradable                          Installed Qty                       1                          Max Processors Qty.                       1                  **Motherboard**

               Bus Speed                       800 MHz                          Video Output Interface                       AGP 8x                  **Memory**

               RAM Technology                       DDR SDRAM                          Installed RAM   [ ]("http://www3.shopping.com/xWI?lid=1&fid=451&aid=14457")                           512 MB                          Max Supported RAM                       2 GB                          Number of Memory Slots                       4 x DIMMs                          Installed Video Memory                       128 MB                          Supported RAM Speeds                       400 MHz                          Installed Cache Memory                       1 MB                  **Technical Features**

               Integrated Input/Output Ports                       USB 2.0 x 7    •        FireWire (IEEE1394a) x 2    •        Serial Port x 1    •        RJ45 Lan Port x 1    •        PS/2 Mouse x 1    •        PS/2 Keyboard x 1    •        Parallel Port (ECP/EPP/SPP) x 1                          Expansion Bays                       2 x 5.25" (External Access)    •        1 x 3.5"  (Internal Access)    •        1 x 3.5"  (External Access)                    [COLOR=Red]      Expansion Slots     [/COLOR]           [COLOR=Red]       AGP x8 x 1    •        PCI x 3     [/COLOR]                     Other Features                       Media Card Reader                  **Hard Drive**

               Hard Drive Capacity   [ ]("http://www3.shopping.com/xWI?lid=1&fid=451&aid=14456")                           160 GB                          Hard Drive Interface                       DMA/ATA-100 (Ultra)                          Hard Drive Rotation Speed                       7,200 RPM                          Controller Type                       DMA/ATA-100 (Ultra)                  **CD / DVD**

               Optical Drive Read Speed                       32x (CD)    •        8x (DVD)                          Optical Drive Write Speed                       16x (CD-R)    •        32x (CD-R)    •        4x (DVD+R)    •        4x (DVD-R)                          Optical Drive ReWrite Speed                       10x (CD-RW)    •        2x (DVD-RW)    •        2x (DVD+RW)                          2nd Optical Drive                       DVD-ROM                          2nd Optical Drive Read Speed                       16x (DVD)    •        40x (CD)                  **Other Drives**

               Floppy Drive                       3.5" 1.44 MB floppy                  **Audio / Video**

               Graphic Processor                       ATI RADEON 9200                          Video Out Ports                       DVI x 1    •        15 Pin D-Sub VGA port x 1    •        S-Video x 1                          Audio Input                       Microphone Jack    •        1 x Line In    •        Coaxial In                          Audio Output Type                       Sound Card    •        Headphones    •        Line out                  **Modem**

               Modem Type                       Fax / Modem                  **Networking**

               Networking Type                       Integrated 10/100 Network Card                          Data Link Protocol                       Ethernet    •        Fast Ethernet                  **Dimensions**

               Width                       7.2 in.                          Depth                       14.9 in.                          Height                       15.6 in.                          Weight                       26.5 lb.                  **Miscellaneous**

               Exterior Color                       Gray    •        Silver                          OS Certified   [ ]("http://www3.shopping.com/xWI?lid=1&fid=451&aid=14430")                           Microsoft Windows XP Home Edition    •        Microsoft Windows XP Professional                          UPC                       027242641990                          Product ID                       24935950                          Family Line                       Sony VAIO                     
 
    [ Back to top]("http://www3.shopping.com/xPO-Sony-Sony-VAIO-PCV-RS530G-Intel-Pentium-4-3-2GHz-HT-512MB-DDR-160GB-HDD-DVD-177-RW-DVD-ROM#top")

---

### Post by albert s on 2010-03-16
yep, you have it in red, 
pci x 3
are any of them empty though?

though someone with more knowledge than me will prob supply you with a command to have a look see just what your system can support.

---

### Post by halitech on 2010-03-16
not sure why you would want to put a PCI video card in if you have an AGP slot unless you are thinking of the newer PCI-express (PCI-e) which is not the same as PCI and will not fit.

---

### Post by sixthwheel on 2010-03-16
> **halitech said:**
> not sure why you would want to put a PCI video card in if you have an AGP slot unless you are thinking of the newer PCI-express (PCI-e) which is not the same as PCI and will not fit.

You think an AGP would be better?..What would you recommend?..Keep in mind, I'm a working man.:)

---

### Post by halitech on 2010-03-16
PCI-e would be the best option but your machine doesn't support it so next best would be AGP and then PCI. Far as what card, probably a lower end Nvidia card unless you want/need intense graphics for movies, games and 3d effects.

---

### Post by realzippy on 2010-03-16
...every nvidia card you can afford;agp  e.g. geforce 7800.

---

