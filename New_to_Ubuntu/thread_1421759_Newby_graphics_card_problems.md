---
title: "Newby graphics card problems"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Stickman123 on 2010-03-04
Hi guys

I'm running Ubuntu 9.10 which I installed the other day as a dualboot with Win XP, and its very impressive - but I am having some graphics card problems. The card is an ATI Radeon 9200 SE. At first I couldn't even see Ubuntu's desktop so I knew there was a problem, and a search of Ubuntu Software Centre suggested 'ATI Binary X.org' which I installed, along with 'ATI Catalyst Control Center'.

These brought the desktop back which was a good start, but graphics performance was slow and flash videos rendered terribly in full screen.

I also tried Envy but it said I already had the recommended driver.

So I uninstalled and reinstalled each of those in different combinations but nothing helped, and now when I boot up I get this a warning that Ubuntu is going to boot in low graphics mode, and the following reason given:

(EE) Failed to load module "fglrx" (module does not exist, 0)

I understand fglrx is the old ATI proprietary driver, and I've followed various online guides to removing it (the guides suggest it blocks an open source Radeon driver, but none of them tell you where to get this driver from).

I can only think that something in the Ubuntu boot sequence is looking for fglrx for some reason. How do I tell it not to? Is there any way to return to defaults for display stuff and start again?

I have tried a few things now, but it looks like a lost cause, and I may have to format the partition and start again. I really hope somebody can help me out because I'm losing countless hours fiddling here.

Thank you in advance,

Simon

---

### Post by sandyd on 2010-03-04
> **Stickman123 said:**
> Hi guys

I'm running Ubuntu 9.10 which I installed the other day as a dualboot with Win XP, and its very impressive - but I am having some graphics card problems. The card is an ATI Radeon 9200 SE. At first I couldn't even see Ubuntu's desktop so I knew there was a problem, and a search of Ubuntu Software Centre suggested 'ATI Binary X.org' which I installed, along with 'ATI Catalyst Control Center'.

These brought the desktop back which was a good start, but graphics performance was slow and flash videos rendered terribly in full screen.

I also tried Envy but it said I already had the recommended driver.

So I uninstalled and reinstalled each of those in different combinations but nothing helped, and now when I boot up I get this a warning that Ubuntu is going to boot in low graphics mode, and the following reason given:

(EE) Failed to load module "fglrx" (module does not exist, 0)

I understand fglrx is the old ATI proprietary driver, and I've followed various online guides to removing it (the guides suggest it blocks an open source Radeon driver, but none of them tell you where to get this driver from).

I can only think that something in the Ubuntu boot sequence is looking for fglrx for some reason. How do I tell it not to? Is there any way to return to defaults for display stuff and start again?

I have tried a few things now, but it looks like a lost cause, and I may have to format the partition and start again. I really hope somebody can help me out because I'm losing countless hours fiddling here.

Thank you in advance,

Simon
when it boots in low graphics mode, select "exit to console"
type this in...
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo shutdown 0 -r
```are you using 64 or 32 bit ubuntu?

open a text editor, and paste this in
```

wget -c https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/fglrx64_6_8_0-8.28.8-1.x86_64.rpm
chmod 777 fgrlx*
sh ./fgrlx*

```

save it to your desktop as install_ati.sh

```

sudo mv ~/Desktop/install_ati.sh /root/install_ati.sh
sudo chmod 777 /root/install_ati.sh

```
boot in recovery mode, choose netroot at the blue screen, and
```

./install_ati.sh
```

---

### Post by Stickman123 on 2010-03-04
Thanks for the reply. 

I presume I'm using 32-bit as this is an old motherboard/processor/graphics card home build.

Before I carry out the instructions, do I need to remove any of the current stuff (that's all not working). I've fiddled a bit more since my Original Post, namely with Envy through terminal (its GUI won't open for some reason?) so according to Software Centre I've currently got installed:

ATI binary X.org driver
ATI Catalyst Control Centre
Envy (which I *think* installed fglrx)
Hardware drivers Jockey-gtk

Should I remove all of these and then use your instructions above?

Thank you so much, the support on here seems just as good as I've always been told it was!

Simon

---

### Post by sandyd on 2010-03-05
no. the driver will overwrite whats already there. your card just happaned to be one of the "special" ones that requires special drivers not kn the repos. I might go to launchpad and drop a bug/wishlist in about this tomorow if I have some time.

---

### Post by Stickman123 on 2010-03-05
Brilliant, thanks for the advice Carlee, I'll give it a shot when I get home from work tonight.

Just a couple of questions on carrying out the above:

1) "when it boots in low graphics mode, select "exit to console"" - do you mean before the desktop etc are showing, during bootup when the warning shows?

2) "open a text editor, and paste this in" - is this once things are booted up or do you mean open a text editor from the console? If its the latter, how?

3) How do I boot in recovery mode? Is this one of the options in GRUB?

Sorry for all the questions but I really want to get this right.

(I'm also stopping at Borders on the way to pick up 'Linux for Dummies'...!)

I hope your bug report helps others with the same problem - I've seen a number of 'unsolved threads' online where people are struggling with this card. I'll report on my results.

Thanks

Simon

---

### Post by 3rdalbum on 2010-03-05
ATI does not support your card with linux drivers anymore. There is an open-source driver for your card, but it is not complete yet, and it is activated by default when you install Ubuntu.

---

### Post by vmsda on 2010-03-05
I have just installed Ubuntu 9.10 on an emachines E725, and am having problems with the graphics, since some screens do not display properly. I am not trying anything fancy, mind you. 

The machine sports an Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09). Funny thing is, I went looking for the relevant xorg.conf file, see if I could smell anything there, and the file does not exist!

Could anyone help out, please?

---

### Post by Stickman123 on 2010-03-05
> **3rdalbum said:**
> ATI does not support your card with linux drivers anymore. There is an open-source driver for your card, but it is not complete yet, and it is activated by default when you install Ubuntu.

Ah right. Well it didn't work well, I couldn't see the desktop and vids were choppy.

Does this mean the above advice is not going to work?

Do I need to buy a new graphics card?

Thanks

---

