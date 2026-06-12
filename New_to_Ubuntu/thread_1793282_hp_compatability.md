---
title: "hp compatability"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by DarinB on 2011-06-29
does anybody know if ubuntu 10.04 lts. 

is compatible with an HP Pavilion p7z series. 

I am thinking of getting one but it has an onboard ATI radeon card and I have heard there maybe issues with it. I have installed ubuntu on other HP and had the best of success. but i don't want to buy a headache. 
I want to go with this because of the price and I don't need to over buy 
since i use 32bit ubuntu 10.04 lts 
thanks

---

### Post by kaldor on 2011-06-29
Depends on what you need to do. If you're not a gamer, AMD graphics should be fine. If you're a gamer, you might have better luck using a supported NVIDIA card.

What graphics card is in question?

---

### Post by seawolf167 on 2011-06-29
You should be good to go and get it. You'll need to install additional drivers for your video card. I googled the computer and got these [specs ]("http://www.shopping.hp.com/webapp/series/category/desktops/p7z_series/3/computer_store")(Integrated graphics - ATI Radeon HD 4200 [VGA, DVI]), and the proprietary driver suite for the integrated graphics card is [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English").

---

### Post by kaldor on 2011-06-29
Ah, that should be a fine card these days. I wouldn't worry much about it.

---

### Post by DarinB on 2011-06-29
will the drivers be a nightmare?
I had tons of difficulty in the Jaunty era, it made me crazy. 
I need to use a lower pixels so I can see the screen.

---

### Post by seawolf167 on 2011-06-29
> **DarinB said:**
> will the drivers be a nightmare?
I had tons of difficulty in the Jaunty era, it made me crazy. 
I need to use a lower pixels so I can see the screen.

No - they are quite easy to install. If you install via the "Additional Drivers" its simply a click, if you do it manually with the proprietary suite its just a matter of making it executable then running it.

---

### Post by DarinB on 2011-06-29
sorry I didn't explain. with the nvidia cards the proprietary software helps me switch to a better screen res for me. 
It is possible I am still shell shocked from the earlier problems.

but I have read over the last few years problems with radeon cards and ubuntu

---

### Post by DarinB on 2011-06-29
how would I? 
1. add additional drivers via synaptic?
2. how to i make a .run, that is what the link above has. file executable in ubuntu?

---

### Post by seawolf167 on 2011-06-29
> **DarinB said:**
> how would I? 
1. add additional drivers via synaptic?

System -> Administration -> Hardware Drivers, or in 11.04, click the power button in the upper right, select system settings, select Additional Drivers


> **DarinB said:**
> 2. how to i make a .run, that is what the link above has. file executable in ubuntu?

Download the .run file from the link. Open a terminal, change to the directory containing the download (default would be ~/Downloads)

```
cd ~/Downloads
```Mark as executable

```
sudo chmod +x ati-driver-installer-11-6-x86.x86_64
```Run the file

```
./ati-driver-installer-11-6-x86.x86_64
```It *may* error out saying you can't have x running, in which case hit [CTRL][ALT][F1] to enter tty1, then type

```
sudo service gdm stop
```and rerun the driver installer

```
cd ~/Downloads
./ati-driver-installer-11-6-x86.x86_64
```Once done, restart gdm

```
sudo service gdm start
```

---

### Post by owiknowi on 2011-06-29
don't know if this is useful information for you, but i own a hp pavilion dv6-3185ed,
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c02537266&prodTypeId=321957&prodSeriesId=4247579](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c02537266&prodTypeId=321957&prodSeriesId=4247579).

so far it has been the most difficult machine for me to use with any linux: (k)ubuntu 10.04 till 11.04, pardus kurumsal 2 enterprise, mint 9-11, scientific 6, sabayon 5.5 and 6, mageia 1, unity-linux 2010.2, just to name a few.

some of my troubles (of course all of them are just based on my personal experiences):
wifi doesn't connect to a hidden wireless network, the ati graphics card proprietary drivers make the computer freeze (only a hard power down remains), its bios is rather poor with just a few options, some function keys work on some distros and not on others, touchpad is really horrible to use (no more separate left and right buttons, but they're rather integrated in the touchpad itself), bluetooth not working (a logitech bt mouse), battery last only up to about 2 hours tops, for a led screen the quality is not what it could be, etc.

of course all os related troubles don't occur with w7-64, shipped with the hp dv6.

---

### Post by DarinB on 2011-06-29
Hmmm, I have converted many friends to ubuntu. 
and the only one that has been completely pain free was the HP. 

I just called her to get me the model number. 
I am using an old hp compaq and it has been running great with only 516mb of ram...I am running Linux mint 9 which is really ubuntu 10.04
with all the restricted drivers pre-added. I did have to add the nvidia drivers (sorry above I forgot about the sys > admin > hardware drivers)

but I have only had a great experience much better than dell. 
Although i just saved a friend"s old dell Inspiron 6000 laptop with ubuntu 11.04 [I]His xp died and the tech told him he needed a new HDD.
[/I] **Gotta love Ubuntu!**

---

### Post by kaldor on 2011-06-29
> **DarinB said:**
> Hmmm, I have converted many friends to ubuntu. 
and the only one that has been completely pain free was the HP. 

I just called her to get me the model number. 
I am using an old hp compaq and it has been running great with only 516mb of ram...I am running Linux mint 9 which is really ubuntu 10.04
with all the restricted drivers pre-added. I did have to add the nvidia drivers (sorry above I forgot about the sys > admin > hardware drivers)

but I have only had a great experience much better than dell. 
Although i just saved a friend"s old dell Inspiron 6000 laptop with ubuntu 11.04 [I]His xp died and the tech told him he needed a new HDD.
[/I] **Gotta love Ubuntu!**

I couldn't see anything wrong with the original model. But again, what do you intend on doing? AMD has great support for open source Linux drivers. If you don't play games, you probably won't even need the additional drivers and everything should work out of the box. That said, older games seem to run fine on the free (default) drivers. I know someone who plays Urban Terror without issues with a similar card.

---

### Post by seawolf167 on 2011-06-29
Regardless of vendor, the hardware is the issue. Provided it is supported by the linux kernel and available drivers you should be good to go with most distros. Cutting edge hardware can be an issue since it may or may not have been addressed yet, but the  majority of hardware you'll run into will be supported without issues.

---

### Post by kaldor on 2011-06-29
> **seawolf167 said:**
> Regardless of vendor, the hardware is the issue. Provided it is supported by the linux kernel and available drivers you should be good to go with most distros. Cutting edge hardware can be an issue since it may or may not have been addressed yet, but the  majority of hardware you'll run into will be supported without issues.

Yep, this is true.

Avoid new Sandybridge processors, NVIDIA Optimus technology, and new AMD cards.

---

### Post by mastablasta on 2011-06-29
also HP ships some computers with OpenSUSE preloaded. 
 
and soon they plant to start shipping them  WebOS (i wonder if and when they really will) which is linux based.

---

### Post by DarinB on 2011-07-01
to answer about use, I never game. 
I will use it as a business machine. open office. online research thats it. maybe an occasional Hulu show but that is it. 
All I really need in a video card is the ability to use a lower res so I can see the screen. poor vision but not bad enough for orca etc. 
Thanks I think it will work. 
will hp work with a none hp hmdi monitor?

---

