---
title: "Installing new graphics card?"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by FadedReality on 2009-10-28
I'm going to be installing a new graphics card an update from integrated graphics on a dell Optiplex 170l. I'll be installing this card: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814187057](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187057)

Do I need to do anything before I shut down the computer and slide it in the pci slot? Can I just install it reboot and expect ubuntu to find and install drivers on its own?

Thanks for any help. :)
...(Ubuntu 9.10)

---

### Post by falconindy on 2009-10-28
Make sure to remove your current graphics drivers and set aside your xorg.conf before shutting down to install the new card.

---

### Post by FadedReality on 2009-10-28
What do I need to type in the terminal to uninstall my current drivers?

---

### Post by penguinv on 2009-10-28
> **falconindy said:**
> Make sure to remove your current graphics drivers and set aside your xorg.conf before shutting down to install the new card.

How do you do that?

I've tried removing programs and have failed. "Cant find it"

---

### Post by falconindy on 2009-10-28
Mmm, it only applies to the proprietary driversets installed under 'Hardware Drivers' in the Administration menu. If you're using a built-in driver set for an Intel, SiS, etc chipset, you'll be okay. If you want to play it safe, you can boot without an xorg.conf and recreate one after logging in with `sudo dpkg-reconfigure -phigh xserver-xorg`.

---

### Post by JBAlaska on 2009-10-28
A GeForce 9400 GT with passive cooling....I don't know about that, You may want to rethink that purchase M8.

---

### Post by FadedReality on 2009-10-28
They say the card gets hot but I don't plan on maxing it out (Just desktop effects and HD playback). If I have to I can add a fan down the road.

It says I don't have any proprietary drivers on this system so that means I can just slide the card in and I'm good to go then?

---

### Post by falconindy on 2009-10-28
> **JBAlaska said:**
> A GeForce 9400 GT with passive cooling....I don't know about that, You may want to rethink that purchase M8.
I've built rack mount servers with similar cards. They're fine. The part I choked on was the vanilla PCI bus. It's been so long, I forgot video cards used to be PCI.

> They say the card gets hot but I don't plan on maxing it out (Just desktop effects and HD playback). If I have to I can add a fan down the road.

It says I don't have any proprietary drivers on this system so that means I can just slide the card in and I'm good to go then?
Yeah, and like I said, if you want to be extra cautious, ditch your xorg.conf file for booting.
```
sudo mv /etc/X11/xorg.conf{,~}
#shutdown, install new card
sudo dpkg-reconfigure -phigh xserver-xorg
```

Oh. It'd probably be useful to disable the onboard video in the BIOS if its not done automatically.

---

### Post by JBAlaska on 2009-10-28
Well, yea but your going to want to install the new Nvidia drivers after your system boots. I'm using v.185.18.36  from the Nvidia website with no problems.

But that card IS going to get HOT even at idle and especially playing HD content. My integrated 8200 went straight up to 80c at idle and shutdown, I had to add a Thermaltake active chip-set cooler, so be prepared for that expense, you might find it more cost effective to use a active cooled card in the same price range...just a thought.

---

### Post by FadedReality on 2009-10-28
Thanks for the help, linux has a great community here. I already set the bios to auto, unfortunately it doesn't have an off option on my pc. :)

---

### Post by JBAlaska on 2009-10-28
Sorry, after re-reading your post I just now understand you already have the card.

Please do watch the GPU temp until your sure it will be ok. The Nvidia driver I mentioned has a temp monitor in it's x server settings software and I use a little panel applet "Gnome Sensors Applet" that works with lm-sensors to monitor my GPU temp in real-time, both are in the repository.

Good luck and enjoy your new card.

Gnome Sensors Applet=[IMG]http://img21.imageshack.us/img21/3985/snapshot1sj.png[/IMG]

---

### Post by cascade9 on 2009-10-28
> **JBAlaska said:**
> Well, yea but your going to want to install the new Nvidia drivers after your system boots. I'm using v.185.18.36  from the Nvidia website with no problems.

But that card IS going to get HOT even at idle and especially playing HD content. My integrated 8200 went straight up to 80c at idle and shutdown, I had to add a Thermaltake active chip-set cooler, so be prepared for that expense, you might find it more cost effective to use a active cooled card in the same price range...just a thought.

Probably more related to intergrated chipsets (I avoid them myself) and low case air-flow. I've got a 8600GT, it runs at pretty much the same core, very similar TDP to the 9400GT and I've never seen it go over 80C. The only time its even got close was on a hot day, 40C and I played a few hours of FPS games.

---

### Post by JBAlaska on 2009-10-28
Integrated chip-sets yes I agree (I bought the MB for a HTPC and decided to use it for a Karmic test box), Low case air flow..nope. Mistique server case with 3 160mm fans and 2 120's LOL.

But I would be interested to here from the OP when he has his Card up and running as to the temp's.. I was certainty not bashing Nvidia cards..far from it. I just would hate to see anyone have a meltdown as I almost did.

---

### Post by 3rdalbum on 2009-10-28
It depends what passive-cooled card you have - my old 8600GT Silent was advertised as running 7 degrees Celcius cooler than a reference design card.

Just chuck it in and it should work with the "nv" driver; if it doesn't, then it will probably ask you if you want to run in low graphics mode. Do that, and then edit your xorg.conf file so it doesn't specify a driver to use; and then you can install the Nvidia driver.

---

### Post by haemulon on 2009-10-28
What is considered "too hot"?

Mine usually run around 50-55C all the time.

---

### Post by FadedReality on 2009-10-28
After re-installing Ubuntu it recognized the card was having trouble without a fresh re-install. Have all the cool effects now. The Nvidia program that came with the driver has a temp gage. My thresh hold is 105c at least thats what the program says. If I open up the case with a fan blowing I get 35c. The card Idles at 65c without the fan. With normal desktop use it levels off at around 70c. I'll definitely have to buy a fan for this card for more intensive stuff. 

Thanks for all the help. :)

---

