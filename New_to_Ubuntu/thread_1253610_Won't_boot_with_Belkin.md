---
title: "Won't boot with Belkin"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by peterbrown77 on 2009-08-30
I installed the latest LiveCD on an older XPS T450.  After successfully running updates, I installed a Belkin Wireless G PCI card.  The machine then failed to boot.  I attempted to reinstall Ubuntu but it would hang in the initial splash screens (at "Local media found" or similar).

I removed the Belkin card and it now boots to the original installation.

Any way to get Ubuntu to boot with the Wireless G card?

TIA

---

### Post by peterbrown77 on 2009-08-30
I installed the latest LiveCD on an older XPS T450. After successfully running updates, I installed a Belkin Wireless G PCI card. The machine then failed to boot. I attempted to reinstall Ubuntu but it would hang in the initial splash screens (at "Local media found" or similar).

I removed the Belkin card and it now boots to the original installation.

Any way to get Ubuntu to boot with the Wireless G card?

TIA

---

### Post by overdrank on 2009-08-30
Hi and welcome, please do not create multiple threads on the same issue. thread merged and moved to Absolute Beginner Talk

---

### Post by LewRockwell on 2009-08-30
> **peterbrown77 said:**
> I installed the latest LiveCD on an older XPS T450.  After successfully running updates, I installed a Belkin Wireless G PCI card.  The machine then failed to boot.  I attempted to reinstall Ubuntu but it would hang in the initial splash screens (at "Local media found" or similar).

I removed the Belkin card and it now boots to the original installation.

Any way to get Ubuntu to boot with the Wireless G card?

TIA

Hi Peter! We think you'll do fine once you've figured out what hardware and chipsets you have and take the appropriate corrective actions to alleviate your trouble-call symptoms

.

---

### Post by peterbrown77 on 2009-08-30
Ummmm - okay!  But I thought that is what I asked.

How am I supposed to determine all this information - and when I do, is it really going to help?  Aside from telling me that there is a problem.

I cannot get my machine to boot or get past the first splash screen on an install from LiveCD or even run LiveCD when this card is in the slot.

TIA

---

### Post by peterbrown77 on 2009-08-31
Bump

---

### Post by LewRockwell on 2009-08-31
G'Day Mate! Top of the mornin' to ya!

please may we have the information off of the PCMCIA device in question?

.

---

### Post by peterbrown77 on 2009-08-31
Lew,

It's not PCMCIA, just a standard PCI card that I installed in a Dell desktop PC (XPS-T450 - pretty old, I know).  It is a Belkin Wireless G card.  Most likely the F5D7000.

Regards

---

### Post by LewRockwell on 2009-08-31
those belkin cards are notorious

you will need to confirm the numbers as some of them absolutely refuse to work with *nix distros

you would not be the first person to take a sledge-hammer to one...

keep us posted!

(ps-even windoze doesn't like some of them: [http://www.techsupportforum.com/networking-forum/networking-support/188428-belkin-xp-wireless-router-problems-death-screen.html](http://www.techsupportforum.com/networking-forum/networking-support/188428-belkin-xp-wireless-router-problems-death-screen.html))

.

---

### Post by peterbrown77 on 2009-08-31
Okay Lew, I will look at it again tonight when I get home.

---

### Post by zerhacke on 2009-08-31
In a terminal, type "lspci" without the quotes.  If you want to get fancy, type "lspci | grep Belkin" without the quotes.  The second command will only return the information on the Belkin card you have.

Post the results, please.  This will give us the information we need to know to research your card and see if it is supported.

---

### Post by hyperdude111 on 2009-08-31
I have the same card as you. The [http://catalog.belkin.com/IWCatProductPage.process?Product_Id=141055](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=141055) Belkin wireless G. 

I have had no problems with the card since install. i would recommend you re-install ubuntu since the drivers are working perfectly for me. It could be you have a damaged install or corrupted drivers.

---

### Post by LewRockwell on 2009-08-31
> **hyperdude111 said:**
> I have the same card as you. The [http://catalog.belkin.com/IWCatProductPage.process?Product_Id=141055](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=141055) Belkin wireless G. 

I have had no problems with the card since install. i would recommend you re-install ubuntu since the drivers are working perfectly for me. It could be you have a damaged install or corrupted drivers.

others have previously corrected similar trouble-calls by removing and re-inserting the card several times(and making sure the inside of the unit is clean while you're in there!)

.

---

### Post by peterbrown77 on 2009-08-31
Okay, I have the card in my hand and it is definitely a Belkin F5D07000F.
 
As I said though, I cannot reinstall Ubuntu because when the card is installed I cannot even get past the initial splash screen of the install where it asks if I want to test the media or skip it.  Forget trying to boot the current system.

---

### Post by hyperdude111 on 2009-08-31
> **peterbrown77 said:**
> Okay, I have the card in my hand and it is definitely a Belkin F5D07000F.
 
As I said though, I cannot reinstall Ubuntu because when the card is installed I cannot even get past the initial splash screen of the install where it asks if I want to test the media or skip it.  Forget trying to boot the current system.

This is really weird I just got out my packaging and it is a Belkin F5D07000F, I got it from pc world for about £25. It has worked perfectly ootb. Have you installed it correctly did the card click as you put it in, depending on you pc model you might have to enable it via bios.

---

### Post by peterbrown77 on 2009-08-31
No, the card worked in the previous Win2K installation, so the BIOS is not the issue.  As I mentioned in my first post, I installed Ubuntu without the card installed, got it running, ran updates from the hardwire eth0, shut down, put in the card and the system refused to boot or install from LiveCD.  Was your install the latest rev?
 
TIA

---

### Post by hyperdude111 on 2009-09-01
> **peterbrown77 said:**
> No, the card worked in the previous Win2K installation, so the BIOS is not the issue.  As I mentioned in my first post, I installed Ubuntu without the card installed, got it running, ran updates from the hardwire eth0, shut down, put in the card and the system refused to boot or install from LiveCD.  Was your install the latest rev?
 
TIA

I think i got my card about April and used it with Jaunty as it came out. You problem seems unusual. Maybe it's an issue with ubuntu and some other hardware conflicting with the card.

At the grub boot try all other kernel options see if that is the problem.

---

### Post by peterbrown77 on 2009-09-01
I tried again last night, to no success.  I removed all PCI cards (modem, 10/100 NIC) from the machine and left in only the Belkin Wireless G.  Booting from disk it stopped after the "Ubuntu" progress bar (like Knight Rider) and the little circle with the Ubuntu logo came on.  Booting from LiveCD, it stopped after the language selection. 

Not sure where to go from here or what I can do if I can't get to a prompt.

How do I get into the Grub boot and what options should I try?

---

### Post by LewRockwell on 2009-09-01
we would like to request a favor

could you get the latest Puppy Linux LiveCD and try it out with your normal hardware configuration please(including this card)

[http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)

unless you can get the card working with some other operating system right now, we would be inclined to say that the card is buggered

.

---

### Post by peterbrown77 on 2009-09-01
Lew,

Okay, I downloaded and burned Puppy and am running it as I type this on my laptop, so I know the image file/CD are good.  I will try it on my problem-child when I get home tonight.

---

### Post by hyperdude111 on 2009-09-01
> **LewRockwell said:**
> we would like to request a favor

could you get the latest Puppy Linux LiveCD and try it out with your normal hardware configuration please(including this card)

[http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)

unless you can get the card working with some other operating system right now, we would be inclined to say that the card is buggered

.

+1 If the card wont work with another take it back to the shop and request a replacement or refund.

---

### Post by LewRockwell on 2009-09-01
as an additional note:

if the card only works with windows then you'll need to decide what you want to do with THAT card

obviously if you desire to have a card that works with *nix distros you'll be replacing it

.

---

### Post by peterbrown77 on 2009-09-02
Puppy would run without the Belkin installed, but would hang at the question about whether I was using a USB mouse when the Belkin card was installed.

I also tried to install Puppy to the local disk when the card was not installed, and wanted to see if it would boot from local disk if I installed the card afterwards.  However, I got stymied because (with no wireless card installed) it would keep booting to the **grub>** prompt, and I didn't know what to do from there.

---

### Post by LewRockwell on 2009-09-02
now you understand more fully why others have used sledge-hammers on the Belkin and REFUSE to purchase their products AND warn others against Belkin purchases as well

.

---

### Post by hyperdude111 on 2009-09-02
> **LewRockwell said:**
> now you understand more fully why others have used sledge-hammers on the Belkin and REFUSE to purchase their products AND warn others against Belkin purchases as well

.

I have had no problems with my belkin, maybe I'm lucky.

---

### Post by LewRockwell on 2009-09-02
> **hyperdude111 said:**
> I have had no problems with my belkin, maybe I'm lucky.

so it's established...somewhat...that certain devices are "hit or miss" with *nix


one would think...and rightly assume...that manufacturers would desire to sell their product(s) to as many customers as possible...and thus, therefore, never neglect a market segment where it is insanely easy to find plenty of contributors more than willing to assist in product hardware and software development


{{sigh}}


.

---

### Post by peterbrown77 on 2009-09-02
As an aside, and a little bit off-topic - was it normal for the hard-disk install of Puppy to boot to the grub prompt?  Or did I do something wrong?  When I typed "boot" it said that the kernel wasn't loaded and I didn't know where to go from there.

---

### Post by LewRockwell on 2009-09-02
> **peterbrown77 said:**
> As an aside, and a little bit off-topic - was it normal for the hard-disk install of Puppy to boot to the grub prompt?  Or did I do something wrong?  When I typed "boot" it said that the kernel wasn't loaded and I didn't know where to go from there.

you probably are referring to the grub menu appearing at initial machine power-up

it should have shown a splash screen with a Puppy(go figure) and several selections

at any rate, usually the LiveCD disks are set to automatically proceed with a boot-up after a brief timed period and often the grub menus also have a timed function(although we're not immediately sure if the default Puppy installed grub menu does that)

you might just try to hit the enter key without keying anything and see what happens

like most anything, there is a learning curve

.

---

### Post by peterbrown77 on 2009-09-02
I wonder if it is something else with that machine.

I was easily able to get Puppy to run from the LiveCD.  On its desktop there is an "Install" icon, which I did and followed the instructions.  It reformatted the disk and installed Puppy, then it asked to install Grub, which I did according to the instruction.  It then reported it was done.  I removed the CD from the tray and rebooted.  It then booted to the Grub prompt, no selections available and just hitting "Enter" provoked no response.  

I loaded Puppy twice to the same results, getting the GRUB> prompt.  I guess it's something for the Puppy forums.  I kind of liked it, it was nice and lightweight which is good for that old machine.  I only want something to put in my cellar on the workbench so when I'm fixing something I can look up info online instead of going up and down the stairs.

---

