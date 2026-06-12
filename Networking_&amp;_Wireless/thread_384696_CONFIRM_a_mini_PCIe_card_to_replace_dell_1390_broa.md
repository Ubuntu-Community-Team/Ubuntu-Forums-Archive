---
title: "CONFIRM a mini PCIe card to replace dell 1390 broadcom card"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by Ebacherville on 2007-03-14
OK i have a dell 1705 with the dreaded 1390 broadcom card (mini PCIe) , I have tried for over 20 hours for the last week, doing 4 clean installs, following tutorials etc., trying to get this flippen card to work only with limited success but not usable.. (got it working and able to see my router, but cant connect in any way open, wep, wpa, nothing...   Even got a different brand type of router and couldn't connect to that either. So I'm done with the Dell/Broadcom 1390!

So I want a conformation from some one to say that this card I found will work OUT OF THE BOX...

Intel PRO/Wireless 3945ABG Mini-PCIe Card
[http://www.pugetsystems.com/store/item.php?cat=Accessories&id=3671&com=d41d8cd9](http://www.pugetsystems.com/store/item.php?cat=Accessories&id=3671&com=d41d8cd9)

For $43.00 I'll just replace the 1390 card, my time is definatly not worth saving $43.00

Can any one, personally confirm, this works out of the box.

If no one can personally confirm this card, But can suggest a different card I'm very open to suggestions at this point. Whatever will work out of the box!

I have to have reliable wireless or Ubuntu is just not going to cut it.

Thanks,
Ebacherville

---

### Post by SactoBob on 2007-03-14
You could call the nice folks at [www.netgate.com](www.netgate.com) who specialize in open source.  I was referred there by our local Linux User Group.  I have talked to them on the phone and they are great.  I bought a PCMCIA (Atheros) card that worked out of the box with madwifi, and an awesome but expensive indoor bridge for my desktop.  They have quite a few mini-pci cards. 

Both my units worked straight off, and Bill had some great advice for me.  I like to support people who support open source.  What a pleasure after weeks trying to get cards to work that were never going to work.

Bob

---

### Post by Ebacherville on 2007-03-14
I did about a hour of research on this card, its seems its fully supported in ubuntu 6.10.. so I ordered it..  We will see how it works, Ill post my findings when i get it.

Ebacherville

---

### Post by dasunst3r on 2007-03-14
I know it is kinda late, but I'd like to put in my confirmation that the ipw3945 card will work right out of the box in 6.10 (Edgy).

---

### Post by f03el on 2007-03-20
Hi,
I am about to replace the BC4311 card in my laptop (HP dv6101) and the Intel 3945 seems to be a suitable replacement. When searching for the card I found two alternative product numbers: WM3945AGM2GEN and WM3945AGM2WB. Does anybody know the difference between them?

---

### Post by krayzee8 on 2007-03-22
Hey Ebacherville,

Have you received the card and installed it yet?  I was curious as I am considering replacing the 1390 card in my Compaq V5209US with the same.  Also, since f03el mentioned that there are two model numbers, by any chance can you indicate which one you received?

---

### Post by f03el on 2007-04-12
I ordered the model called WM3945AGM2WB and replaced the Broadcom 4311 in my HP Pavilion dv6101 (after removing ndiswrapper). Works like a charm!

---

### Post by maestrobwh1 on 2007-08-01
I think I know the answer to this, but I am going to ask based on this post:

I have a broadcom 4318 mini PCI in my Acer laptop.  It works, but I am tired of fussing around with ndiswrapper, as I suspect that if I ever upgrade to Feisty or later, Gutsy (when officially released - love it on my desktop), I am going to have issues... 

Can I simply buy an atheros mini pci that is listed to be OEM for another brand of laptop?  If it fits the slot, I am wondering if I will have issues with the button/light that currently turns on/off and shows "active" with my broadcom card.  There is no setting in my BIOS as in a desktop regarding pci devices so I am reticent to waste money on something that might not work at all.

I could get a PCMCIA card, but I can't find one that works out of the box that doesn't "stick out" of the side.

---

### Post by portach king on 2008-01-24
Hey Guys,
Well I'm officially committed to pulling the horrid broadcom 4318 out of my laptop (HP dv6000) and replacing it with a more reliable card. You can read my other thread and see why. *headache returns*
In any case, the info on this thread is great, however I'm wondering how complicated the process in replacing the card is. I've opened Desktops up and installed new hardware in them before, but never a laptop which makes me nervous.
Is there a guide of some sort anywhere that I could use, or could someone reassure me it won't be very difficult? :D

Also if it isn't too much trouble, could someone reccomend a card I should invest in. I'm leaning towards the Intel 3945 at the moment... :)

---

### Post by maestrobwh1 on 2008-01-24
Its generally no harder than changing a memory chip.  I have an acer that had that chip and it was right under the center panel on the bottom (under the memory).

Go with an atheros chip and look for an "older" a/b/g and be sure to check on madwifi

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

To make sure it works.

---

### Post by chili555 on 2008-01-24
> I'm officially committed to pulling the horrid broadcom 4318 out of my laptop (HP dv6000)Just be sure your DV6000 doesn't have a whitelist in the BIOS that allows only certain wireless cards. Google is your new best friend. Google up 'DV6000 whitelist wireless.'

---

### Post by portach king on 2008-01-24
Well, I'd have to do a BIOS hack to get an Atheros to work (and I am not doing that, no sirree), but other models in the dv6000 range (mines a dv6179EA) ship with an Intel 3945..
Surely thats good enough reason to assume that it would work? Maybe?

---

### Post by chili555 on 2008-01-24
A Google search looks promising. I'd try it!

---

### Post by portach king on 2008-01-24
Thanks Chili555!  
*High Fives!*

I'll report back with some results in the next few days.

---

### Post by maestrobwh1 on 2008-01-24
Wow, how devicive is that?  A manufacturer would do that?  Dude, I'm never gettin' a Dell.

---

### Post by chili555 on 2008-01-24
HP, Compaq, Dell and IBM are reported to have this 'feature.' There is a whole sub-cult that discusses hacking the BIOS, which I have never tried and cannot endorse. 

Just when you think you know a little somethin' about the personal confuser, you get a surprise.

---

### Post by maestrobwh1 on 2008-01-26
Funny, but anymore I am so "open source" conscious, I just won't buy crap that doesn't work, but knowing that some manufacturers rig their bios NOT to work with certain hardware was something I didn't consider.  My ACER laptop was kind of annoying with the ACPI, but they didn't make it so that it purposely would not work.  It just didn't right off (with feisty) so it needed some tweaking.  Gutsy handled it.

Anyway, for those of you who can handle an atheros card, it is the way to go if you are a linux user.  I still have win XP on my latptop and I managed to find the drivers on a google first hit. 

Unrelated: I am pleased to say that I "blew away" my XP partition on my desktop and replaced it with the KDE4 version of Gutsy.  Ahhh, one step closer to independence.

---

### Post by portach king on 2008-02-04
Oh boy....
 
Ok, so I ordered the wireless card (intel 3945) as I said I would. It arrived today, and now I feel like an idiot. 
It's a mini pcie card. The wireless card in laptop is a min pci. I honestly didn't even know there was a difference until a few minutes ago. Gah.
Is there anyway I can install this?
I'd appreciate any answer.

---

### Post by kevdog on 2008-02-04
Little off topic -- but you sure you weren't able to get that broadcom card to work with ndiswrapper??  Seems like ndiswrapper/winxp driver would be the way to go.  That's of course just adding fuel to the fire.

As far as installing the minipcie card, its going to depend on how the old one was connected.  It seems like if you unscrewed the compartment where the old pcie card was located, it would be simply a matter of unplugging the card from the slot (which could indeed be very difficult depending on how it is secured).  I think pcie cards are meant to be removed/added so it shouldn't be impossible.

---

### Post by portach king on 2008-02-04
Hey Kevdog,
We meet again. Thanks for your reply. I opened a thread a few weeks ago. I tried everything (fwcutter, ndiswrapper, multiple fresh installs, even upgrading the kernel to try the new b43 drivers, which were an improvement but still far from adequate I'm afraid) to get my Broadcom card working. The entire affair left me heartbroken. I've given up on it.

I think you failed to see my question above though. I was asking if there is a way to install the Mini PCI Express card that just arrived in the post, into the slot which currently houses a Mini PCI card (ie. Not express). As I mentioned, and I hate to sound so foolish, but didn't realise there was a difference before today.

---

