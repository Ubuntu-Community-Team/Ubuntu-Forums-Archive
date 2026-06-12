---
title: "Slow Graphics"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by fixerman on 2009-10-09
Having installed Ubuntu only a few days ago I am very pleased indeed. I have put it on an old computer that I intend to give to my nephew as a gift. The only concern I have is that it sometimes struggles with rendering complex graphics. Google earth was a disaster. It just kept crashing so I uninstalled it.

Would the standard install have installed the most appropriate graphics driver automatically or should I be looking for a better driver.

Any ideas please.

---

### Post by allenbradley on 2009-10-09
Could you fire up google-earth from a terminal and post the output when it crashes>

---

### Post by HarrisonNapper on 2009-10-09
While you're at it, post the output of lspci.

When you say the computer is old; how old, exactly?

---

### Post by fixerman on 2009-10-09
> **HarrisonNapper said:**
> While you're at it, post the output of lspci.

When you say the computer is old; how old, exactly?


patrick@patrick-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
03:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
patrick@patrick-desktop:~$

---

### Post by fixerman on 2009-10-09
> **HarrisonNapper said:**
> While you're at it, post the output of lspci.

When you say the computer is old; how old, exactly?

It's a self build about 5 years old AMD Athlon 1gb RAM

---

### Post by fixerman on 2009-10-09
> **allenbradley said:**
> Could you fire up google-earth from a terminal and post the output when it crashes>


I have uninstalled Google Earth. It was causing too much grief.

---

### Post by dv3500ea on 2009-10-09
If you haven't installed the appropriate graphics drivers yet you should as this speeds graphically intensive programs up a lot (from my experience this is particularly noticable with even 2D fullscreen applications, particularly games). You can install the Nvidia drivers from synaptic package manager or you can do what I did and download the latest version from the Nvidia site. Save the *.run file from the site into a directory (I will assume /home) then press CTRL-ALT-F1 this should bring up a full screen black and white command line. 
Run these commands:
cd /home
  sudo /etc/init.d/gdm stop
  sudo chmod +x *.run
  sudo ./*.runIt should go through an installer where you need to accept the EULA then will return to the command line.
Enter this:
sudo /etc/init.d/gdm startto restart the graphical user interface.
To enable visual effects go to system->preferences->startup and add the command 'compiz' to the list. Next, open a terminal (ALT-F2 type 'gnome-terminal') and run:
sudo nvidia-xconfig --add-argb-glx-visuals

---

### Post by jeremyswalker on 2009-10-09
> If you haven't installed the appropriate graphics drivers yet you should as this speeds graphically intensive programs up a lot (from my experience this is particularly noticable with even 2D fullscreen applications, particularly games). You can install the Nvidia drivers from synaptic package manager or you can do what I did and download the latest version from the Nvidia site. Save the *.run file from the site into a directory (I will assume /home) then press CTRL-ALT-F1 this should bring up a full screen black and white command line.
Right, but I do not believe he has an Nvidia graphics card.

> 03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
03:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

You should go to System > Administration > Hardware Drivers and make sure it shows the proprietary driver for your graphics as being enabled.

---

### Post by HarrisonNapper on 2009-10-09
> **jeremyswalker said:**
> Right, but I do not believe he has an Nvidia graphics card.



You should go to System > Administration > Hardware Drivers and make sure it shows the proprietary driver for your graphics as being enabled.

jeremyswalker is right on this one for nVidia cards. Also, sometimes the latest driver will not work as well as an older driver. Make sure you restart after enabling your restricted driver.

---

### Post by halitech on 2009-10-09
with the video being a Radeon 9550, Ubuntu won't have anything in Hardware drivers and ATI doesn't support the card any longer. My suggestion would be dropping back to 8.04 where the video will work alot better.

---

### Post by HarrisonNapper on 2009-10-09
> **halitech said:**
> with the video being a Radeon 9550, Ubuntu won't have anything in Hardware drivers and ATI doesn't support the card any longer. My suggestion would be dropping back to 8.04 where the video will work alot better.

Oh, haha, this is actually correct--I was looking at RAM. You'd think with all of the times I've looked at lspci output... sheesh. Sorry, jeremy, we both got pwned by reality.

---

### Post by HarrisonNapper on 2009-10-09
Alternately, you can get another video card at newegg or your vendor of choice.

---

### Post by halitech on 2009-10-09
> **HarrisonNapper said:**
> Oh, haha, this is actually correct--I was looking at RAM. You'd think with all of the times I've looked at lspci output... sheesh. Sorry, jeremy, we both got pwned by reality.

we all get caught sometime ;)

actually, I've been dealing with the lack of support by ATI and the changes in XORG for a few months because I have an X1300 (onboard) that prevents me from upgrading as well so I know what cards are supported and whats not pretty well now :(

---

### Post by jeremyswalker on 2009-10-09
According to ATI's website, they offer a legacy driver for this card. Must be Ubuntu doesn't offer a package for it??

---

### Post by halitech on 2009-10-09
they are offering version 9.3 which doesn't work with the new version of Xorg that 9.04 is using. There is probably some way of downgrading xorg to whatever version 8.04 is using but I'm not sure how stable things would be afterwards

---

### Post by jeremyswalker on 2009-10-09
Now that you mention it, I think I do remember hearing something about that.
ATI graphics have given me nothing but problems, in the past. I will never use them again, until their drivers get better anyway.

---

### Post by halitech on 2009-10-09
there were alot of threads on here about 6 months ago when 9.04 came out when most peoples ati graphics went down the crapper. Personally I've used nothing but ati and they have always been good for me but my next card (which should be purchased next week) will be an Nvidia card because of this.

as an aside for this, anyone got a suggestion for a decent Nvidia card thats not expensive that will work, keeping in mind I don't use compiz and don't watch movies on my computer?

---

### Post by jeremyswalker on 2009-10-09
> **halitech said:**
> as an aside for this, anyone got a suggestion for a decent Nvidia card thats not expensive that will work, keeping in mind I don't use compiz and don't watch movies on my computer?

I bought a 512MB 9500GT about a year ago for less than $50 US. I don't have any complaints about it. It's not a top of the line card, but it does everything I need it to.

---

### Post by halitech on 2009-10-09
They don't have the 9500 512meg around here locally but do have the 1gig version for 79.00 (Cdn) but I'm thinking that might be overkill for me. For basic use, how does this card sound? XFX Nvidia Geforce 7200 GS 256MB PCI-Express Video Card for 39.00

[http://www.robotnik.com/product.php?productid=754&cat=180&page=1](http://www.robotnik.com/product.php?productid=754&cat=180&page=1)

> GPU Type 	7200GS
GPU Clock Speed 	450MHz
Shader Clock Speed 	
Stream Processors 	
Memory Type 	GDDR2
Memory Clock Speed 	533MHz
Memory Size 	256MB
Memory Interface 	64-bit
Interface Type 	PCI-Express 

or this one
XFX GeForce 8400GS 256MB DDR2 PCIe VGA DVI (1Year) $50.00

> 
# Bus Type: PCI-E
# GPU Clock MHz: 450 MHz
# Shader Clock (MHz): 900 - 1200 MHz
# Stream Processors: 16
# Texture Fill Rate (billion/sec): 3.6 Billion/Sec
# Memory Interface Bus (bit): 64 - 128
# Memory Type: DDR2
# Memory Size (MB): 256 MB
# Memory Clock (MHz): 533 - 800 MHz

I would prefer to buy locally over having it shipped

---

### Post by jeremyswalker on 2009-10-09
Well, I cannot claim to be an expert at graphic card specs. It seems like an ok card (better than integrated). And I just looked, I must have got my card on sale. They are like $60 now.

---

### Post by halitech on 2009-10-09
I'm not an expert either and just want to stop using this onboard (its set to 256meg) and free up the ram so I have my full 2gig back. I'm thinking the 8400 might be a better option for 10.00 extra

---

### Post by fixerman on 2009-10-10
Thanks for all your advice guys. I am going to leave well enough alone. It goes to my nephew tomorrow and it is good enough for school work and surfing the net plus photos and music.

I have uninstalled Google Earth.

I'm afraid to mess with the graphics settings in case I mess it up.:(

I am now going to install Ubuntu on my laptop and see how that goes. No doubt I will be back for more advice.

Thanks again.:P

---

