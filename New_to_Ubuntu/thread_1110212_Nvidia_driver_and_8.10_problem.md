---
title: "Nvidia driver and 8.10 problem"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by BrianV on 2009-03-29
I upgraded from 8.04 to 8.10 with no problems, then changed out an old ATI Rage video card and replaced it with an nvidia NV6 (Vanta/Vanta LT) rev 15 card. I expected to have better performing graphics, but Preferences > Appearance > Visual Effects gives an error message "Desktop effects could not be enabled" when I try to select "Normal". Also, Administration > Hardware Drivers indicates "No proprietary drivers are in use on this system".

I used Synaptic to download the nvidia-glx-71 package and checked that all dependencies are present.

I have several questions:

Firstly, should I do something to ensure the nvidia driver is installed, or is that automatic?

Then, is there a source that will educate me on what the graphics capability should do for me? Terms like Compiz, 3D graphics, Visual Effects, etc. mean very little to me at present.

As always, any help will be much appreciated.

Thanks, Brian

---

### Post by BrianV on 2009-03-31
Maybe I posted this in the wrong place. Can anyone at least suggest where it would be better to ask these questions?

Thanks, Brian

---

### Post by kestrel1 on 2009-03-31
Have you enabled Hardware Drivers?
System -> Administration -> Hardware Drivers.

---

### Post by daft crunk on 2009-03-31
Downgrading to 8.04 worked for me.

---

### Post by CRIMPS on 2009-03-31
Same for me... I just couldn't get NVidia drivers to work for me in 8.10.  I even tried a clean install and spent hours trying to get the card to work.  So I downgraded to 8.04.  I will test Jaunty out and hope for the best after a couple weeks of stability and keeping my ear to the ground for common problems.

Good luck.

---

### Post by hanif raj on 2009-03-31
> **daft crunk said:**
> Downgrading to 8.04 worked for me.
any body in the world who love linux must try Ubuntu and for this purpose i have got a good book of Ubuntu Linux that is Ubuntu Kung fu just any one can download it free of cost from 4shared.com and enjoy the great fun of Ubuntu. I think it's not bad to get an OS just replacement of Windows Vista free of cost either from Ubuntu.com or from shipit.com .

---

### Post by BrianV on 2009-04-01
kestrel1: Hardware Drivers indicates no proprietary drivers on the system.

daft crank: How do you downgrade to 8.04?

---

### Post by eragon100 on 2009-04-01
> **BrianV said:**
> I upgraded from 8.04 to 8.10 with no problems, then changed out an old ATI Rage video card and replaced it with an nvidia NV6 (Vanta/Vanta LT) rev 15 card. I expected to have better performing graphics, but Preferences > Appearance > Visual Effects gives an error message "Desktop effects could not be enabled" when I try to select "Normal". Also, Administration > Hardware Drivers indicates "No proprietary drivers are in use on this system".

I used Synaptic to download the nvidia-glx-71 package and checked that all dependencies are present.

I have several questions:

Firstly, should I do something to ensure the nvidia driver is installed, or is that automatic?

Then, is there a source that will educate me on what the graphics capability should do for me? Terms like Compiz, 3D graphics, Visual Effects, etc. mean very little to me at present.

As always, any help will be much appreciated.

Thanks, Brian

The driver version you mentioned only supports the newer nvidia cards.
Go to the [www.nvidia.com](www.nvidia.com) to download the correct legacy driver for your card, you can find it by selecting your card name from the drop down menu.

Install it manually, instructions are on the download page.
The 3d support means you could play games if your card was better, and if you're lucky, you might actually be capable of seeing a preview of the windows when you use alt-tab.

In other words: not much, until you buy a better card. A 256 MB GeForce 8 8400 GS is 100 times better, and only costs 30$. Even tough that's still a **very** low end card, it does give great desktop effect performance and can play games on low.

---

### Post by BrianV on 2009-04-10
> **eragon100 said:**
> The driver version you mentioned only supports the newer nvidia cards.
Go to the [www.nvidia.com](www.nvidia.com) to download the correct legacy driver for your card, you can find it by selecting your card name from the drop down menu.

Install it manually, instructions are on the download page.
The 3d support means you could play games if your card was better, and if you're lucky, you might actually be capable of seeing a preview of the windows when you use alt-tab.

In other words: not much, until you buy a better card. A 256 MB GeForce 8 8400 GS is 100 times better, and only costs 30$. Even tough that's still a **very** low end card, it does give great desktop effect performance and can play games on low.

Thanks for the suggestions. They do raise some more questions:
1. The nvidia install instructions ask me to A. Exit the X server and B. Set default run level to boot to a vga console, before running the NVIDIA-Linux-x86-71.86.09-pkg1.run program I downloaded. How do I accomplish A. and B?
2. The instructions say to edit the X config file after installation. I have checked /etc/X11 and find Xorg.config, plus several variants that seem to be back-up copies, perhaps automatically generated during my various attempts. All these display as empty in gedit, even though they consist of 800+ to 1.4K bits. The man pages for Xorg config speak of a search hierarchy to find the config file, but I cannot understand it. How do I find the Xorg.config file that needs editting?

---

### Post by kestrel1 on 2009-04-10
The correct xorg.conf file is in /etc/X11/
If they are showing up blank in gedit try using vi to open them.```
vi /etc/X11/xorg.conf
```
to edit the file use```
sudo vi /etc/X11/xorg.conf
```

---

