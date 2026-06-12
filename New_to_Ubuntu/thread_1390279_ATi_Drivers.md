---
title: "ATi Drivers"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Lord Stig on 2010-01-25
I have a new machine with a fresh install of Mint 7 XFCE.
I want to install the proprietary video driver for my ATi Radeon Xpress 200 (on-board) card but am confused about how to do this.

I downloaded the file from the AMD website. The instructions it gives are for me to navigate to where it's stored and then enter this in the Terminal:
sh ./ati-driver-installer-9.2-x86.x86_64.run
But when I do so I get this:
```
carl@CPDualCoreDesktop ~/Desktop $ sh ./ati-driver-installer-9.2-x86.x86_64.run
sh: Can't open ./ati-driver-installer-9.2-x86.x86_64.run
carl@CPDualCoreDesktop ~/Desktop $ 
```
Right clicking the file on the desktop doesn't give me the option to install/execute and selecting its properties by right clicking doesn't give me the option to run in terminal or similar.
Can anyone help?

---

### Post by TomyVk on 2010-01-25
I had no problem installing the driver manually.

You have to unpack the driver from the .tar.gz first

open a terminal and cd to the location where youve downloaded the driver.
Then type

sudo sh ./ati-driver-installer-9-12-x86.x86_64.run


Dont forget to change the filename to your needs.

after that it should work.

---

### Post by Lord Stig on 2010-01-25
Thanks for the quick reply.
There isn't a .tar.gz that I've downloaded - I literally have this one file and nothing else.

Could I trouble you to post a link to the right file or give me more instructions?

Much appreciated

---

### Post by halitech on 2010-01-25
The driver listed on the ATI website ( [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English) ) does not work in Ubuntu 9.04 or above due to ATI dropping support and Xorg making changes at the same time. I believe Mint 7 is based on Ubuntu 9.04 so I don't think it will work.

The file is not in a tar.gz format but you need to make sure it is executable by right clicking it and going to permissions and allowing it to run.

---

### Post by TomyVk on 2010-01-25
Go to [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

Download the .run file

Open the konsole and cd to your desktop or wherever you've downloaded the file.

Type

sudo sh ./ati-driver-installer-9-3-x86.x86_64.run

That should be it, you'll get a setup screen.

---

### Post by TomyVk on 2010-01-25
> **halitech said:**
> The driver listed on the ATI website ( [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English) ) does not work in Ubuntu 9.04 or above due to ATI dropping support and Xorg making changes at the same time. I believe Mint 7 is based on Ubuntu 9.04 so I don't think it will work.

The file is not in a tar.gz format but you need to make sure it is executable by right clicking it and going to permissions and allowing it to run.

It did work for me without problems, but i'm using the 64 bit version tho.

---

### Post by theozzlives on 2010-01-25
you could try ```
chmod +x ati-driver-installer-9.2-x86.x86_64.run
./ati-driver-installer-9.2-x86.x86_64.run
```
worked with my nVidia drivers.

---

### Post by halitech on 2010-01-25
> **TomyVk said:**
> It did work for me without problems, but i'm using the 64 bit version tho.

do you have the same card as the OP?

---

### Post by TomyVk on 2010-01-25
> **halitech said:**
> do you have the same card as the OP?

Nope. But i dont think there should be problems.

---

### Post by halitech on 2010-01-25
> **TomyVk said:**
> Nope. But i dont think there should be problems.

shouldn't wouldn't couldn't but are. The latest Catalyst drivers only support cards above the HD2400 so using the current drivers in 9.04 or above only work with the HD2400 and above. All the Radeon and X-series are unsupported so you can only use the OpenSource driver with those cards.

Read the section were it states the following cards have been moved to Legacy support

---

### Post by tom.swartz07 on 2010-01-25
> **TomyVk said:**
> Nope. But i dont think there should be problems.

I have an X1270, and it doesnt work. As far as I know- any of the 'legacy' drivers for ATI cards WILL NOT WORK. Ive tried installing the driver several times on multiple OS environments, and the only one that I could get to work is 8.04.


I should warn you- if you do install it, it *might* wreck your xorg.conf file- you could just fall back to an old one if that happens though.

you should be able to try installing it by changing the directory in the terminal to the download location and running ```
sh ./ati-driver-installer-9.2-x86.x86_64.run
```

You need the sh to tell the terminal that its a shell script.

Hope this helps!

---

### Post by halitech on 2010-01-25
> **tom.swartz07 said:**
> I have an X1270, and it doesnt work. As far as I know- any of the 'legacy' drivers for ATI cards WILL NOT WORK. Ive tried installing the driver several times on multiple OS environments, and the only one that I could get to work is 8.04.


I should warn you- if you do install it, it *might* wreck your xorg.conf file- you could just fall back to an old one if that happens though.

you should be able to try installing it by changing the directory in the terminal to the download location and running ```
sh ./ati-driver-installer-9.2-x86.x86_64.run
```

You need the sh to tell the terminal that its a shell script.

Hope this helps!

I have the x1200 on My board and same here, Ubuntu 8.04 and Debian Sarge would work but anything above that killed it when trying to use the ATI drivers.

> **tom.swartz07 said:**
> "Windows 7 was my idea"- I guess Microsoft enjoys copyright infringement? 

I almost busted a gut laughing when I saw your tagline ~L~

---

### Post by tom.swartz07 on 2010-01-25
> **halitech said:**
> I have the x1200 on My board and same here, Ubuntu 8.04 and Debian Sarge would work but anything above that killed it when trying to use the ATI drivers.



I almost busted a gut laughing when I saw your tagline ~L~

HAHA! yep, thats the first thing I thought of when I saw the commercial. :popcorn:

To the OP- before you try installing it, look up and PRINT OUT how to restore your xorg.conf file- if something borks, you wont have easy access to the internet to find it after that.


Have fun! :P

---

### Post by Lord Stig on 2010-01-26
Thanks for all your advice, guys. I think it's not worth the risk of messing up my display (I hadn't mentioned it previously but I installed an ATi driver that was on the EnvyNG app provided by Mint and that screwed it up - was left with lots of coloured lines across the screen and two small screenshots of the Mint loading screen side by side).

I don't know if it was even the right driver that I installed (it was a fresh install so I thought 'why not?') but perhaps if I dig out my Intrepid Ibex CD I'll get the driver working on that.

---

### Post by halitech on 2010-01-26
It should work on 8.04 and 8.10 fine. The Catalyst 9.3 driver is still supported until they made the changes in 9.04.

---

### Post by Lord Stig on 2010-01-26
Thanks Halitech. I'll dust off my old Intrepid CD and give it a try tonight.

In this case I think the solution turned into an answer!

---

### Post by clhsharky on 2010-01-26
HI

I have a Radeon X1650pro card, and I like the radeon drivers. I use  launchpad PPAs and everything works, composite, 3D. Any release from Hardy to Lucid, and on any kernel from .27 to .33. This is a desktop and I don't run Windows apps. on this machine. So I dont need fglrx, and radeon has better 2D.

Sharky

---

### Post by Lord Stig on 2010-01-28
Thanks to everybody who replied. I installed Kubuntu Hardy (8.04) and it detected my card and gave me the option to install the proprietary ATi driver. I can now play OpenArena, TORCS and run Compiz, and scrolling is smooth and responsive. Hurrah! :-) :-) :-)

I realise from Wikipedia that Hardy stopped being supported in October 2009; however, I still had the option to install the updates (just over 200) and the software repository was still available (to install those games I mentioned). What's the significance of Hardy not being supported anymore? Is it that I don't get security or software updates? Could I use it indefinitely, in theory, and still be able to download those programs available for the Hardy release?

---

### Post by clhsharky on 2010-01-28
HI

Glad to hear of your success. Ubuntu supports Hardy till April 2011 (Desktop). I beleave fglrx quit supporting legacy chips in October 2009.

Sharky

---

### Post by Lord Stig on 2010-01-28
Thanks, clhsharky.
What happens when I get to April 2011? Canonical will stop supporting it, so will I lose any ability to add programs from the Hardy repositories?

---

### Post by clhsharky on 2010-01-28
HI Lord Stig

  You will have to upgrade to newer version and run the 'open source stack' driver. Theres a Gallium driver in OSS  for our card all ready, but is not activated yet. It need testing and should be default before 4/11. It is usable but not stable, already.

Sharky

---

### Post by Lord Stig on 2010-01-28
Thanks clhsharky.
I'll keep a eye out for developments with the new driver. In the meantime I'm still using this one on old school Hardy and very happy with it. Thanks for your help.

---

