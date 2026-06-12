---
title: "What should I do?"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by Friend-Atish on 2010-06-14
Hello everybody,
I would like to step into the world of the Linux. Someone suggested me to try the UBUNTU, cause it will be helpful & easy for me as a first time Linux user. 
I have managed a computer with,
Processor : Intel Pentium4(2.4Ghz)
Memory    : 256MB DDR RAM
Monitor   : Generic (Windows XP runs in 1024x768 ) 
HDD       : 40GB
to experience the UBUNTU for first time.
I have tried "UBUNTU 8.04LTS", "UBUNTU 9.10". But, 8.04 is showing a blank screen after installation, and 9.10 is running in 800x600 resolution and getting hanged frequently.  

Pls. suggest me what should I do, to step into the world of the UBUNTU ???? 

:confused::confused::confused:

---

### Post by guthix0009 on 2010-06-14
I'd say deffinatly get more RAM not sure why you have that proccesor with that much ram... after that got Ubuntu 10.04 
once you DL the ISO get PowerISO and burn it to a disk at lowest burning speed.
after that boot up from CD/DVD by going into your BIOS and make it boot up by disk first 
then install next to your current OS so you can still use it if it doesnt work out

once succseffully installed go to your terminal
applications>Acerioes>terminal

in that type
sudo apt-get install

it will then ask for your root password then let it do its stuff
):P

hope that helped Private message me if it does or doesnt

---

### Post by QIII on 2010-06-15
With your system specs, you will likely have to use Xubuntu (Ubuntu with the lightweight Xfce interface).  Your memory is the limiting factor.

Because of your processor, you will have to use the 32 bit version of whatever you choose.

Xfce may not be as feature-rich as GNOME (the default desktop for Ubuntu) or KDE (which makes Ubuntu Kubuntu).

Xubuntu should run comfortably on your machine, but don't expect it to be fast enough to knock your socks off.


guthix009:  Please don't encourage using private messages for off-line help.  Others who might benefit from the discussion will miss out.

---

### Post by 3rdalbum on 2010-06-15
Use Ubuntu 10.04, not 9.10 or 8.04; and you really should have more RAM.

---

### Post by pastalavista on 2010-06-15
> **guthix0009 said:**
> I'd say deffinatly get more RAM...
+1

512MB=sufficient, 1GB=efficient, 2GB=speed demon

Your XP would even WOW you...

---

### Post by QIII on 2010-06-15
> **pastalavista said:**
> +1

512MB=sufficient, 1GB=efficient, 2GB=speed demon

Your XP would even WOW you...

I'm trying to get the "accountant" (some 19 year-old girl I picked up in a bar several decades ago and can't seem to shake...) to cut loose enough of my allowance so that I can get one of the new Phenom II x6 processors and a board with 16GB of RAM.  THAT would be speed demon, folks.

Seriously, though.

Depending on the OP's hardware, increasing RAM may be a stretch.  And it costs money.

Xubuntu won't cost him a dime, and he'll be happy until he can do something different.

---

### Post by Friend-Atish on 2010-06-16
THANKS A LOT.......

Right now I am using "Ubuntu 8.04 LTS". Finally I have made a successful installation. 

I had selected the "Safe Graphics Mode" and started the installation, and finally it installed (but in 800x600 resolution).

And a special thanks to "QIII". You have understood that, right now arrange a new RAM, is quit difficult for me.  

Now I have a little question, should I upgrade the Ubuntu with this much of RAM, or should I keep it as it is?

Once again thanks to you all.......:p:p:p

---

### Post by QIII on 2010-06-16
You have until April 2011 to continue to get support for that LTS.  If  it works, then you can continue to use it.  But by then you will probably want to have a more powerful machine if you want to use GNOME or KDE (Ubuntu or Kubuntu).

Again, Xfce (Xubuntu) should run comfortably.

Since you are just starting out, at this point I would go with what is working.

With regard to your screen resolution, could you tell us what graphics card you are using and whether you have installed a driver?

---

### Post by akelsall on 2010-06-16
Invest in a graphics card that has an Nvidia chipset (there are a lot out there). Any card with the Nvidia chipset works well with Ubuntu. 

Once you do that, you can download the drivers to tweak it better (I can't recall where to get them. It might actually come with the Ubuntu 10.04 software). 

Andy

---

### Post by QIII on 2010-06-16
Despite the FUD, ATI cards not legacied by ATI work fine.  Those that have been legacied can be used with legacy drivers or with the open source driver.

Just as a history lesson, which I like to give to dispel FUD:

When ATI was ATI, Linux support was limited to non-existent. 

AMD bought ATI (now AMD/ATI) in 2007.  It took them something between a year and a year and a half to rectify this situation.

AMD/ATI is committed to Linux support, with a special interest in Ubuntu.

In fact, with each of the last several releases of Ubuntu, AMD/ATI has made its newest driver available exclusively in the Ubuntu repos to coincide with the Ubuntu release.  Other distros have had to wait until it was made available for general consumption.

Phoronics has had smart-mouthed headlines like "More candy for Ubuntu from AMD/ATI" quite often.

"But AMD/ATI legacied their older cards!"  So did nVidia.  Each made legacy drivers available.  Each will also run with open source drivers.  Admittedly, AMD/ATI only made legacy drivers available after a huge hue and cry.

The question now is no different than a Ford/Chevy argument.  It's a matter of taste.

---

### Post by Friend-Atish on 2010-06-18
I am using the onboard graphics.

The Display adapter of my motherboard is 

Intel(R) 82845G/GL/GE/PE/GV Graphics Controller.

And I have not installed any driver separately.

Should I have to install any? If yes, then how ?




Once again thanks to you.......

---

