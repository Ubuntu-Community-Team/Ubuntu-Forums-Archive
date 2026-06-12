---
title: "Someone Help Me, Please..."
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Godsrycht on 2009-11-02
Ok, I'm beginning to feel a bit helpless. There seems to be no OS right for me. I've used Windows for the last few years but after the Abortion known as Windows Vista, I just don't trust them anymore. I tried Ubuntu 9.8 but they just do not have the drivers I need and spontaneously crashes shutting down my PC. I did some PC classes in College but not enough to know the answer to this. Mac is insanely pricey and there coorprate is absolutely garbage. I trust Linux above all but It just doesnt seem to be working for me. Does anyone know an OS, that can support my video games (Counter-Strike, WoW) hold my drivers and so on. Im using an Acer Aspire 5515 laptop.

Thanks
~Nathan

---

### Post by Locke_99GS on 2009-11-02
What devices are giving you issues in Linux?

---

### Post by NickJones on 2009-11-02
Ubuntu is awesome. Try 9.10, it should all work "out of the box". Ubuntu will let you play Counterstrike (1.6 & Source) and WoW.
Nick

---

### Post by unamanic on 2009-11-02
WoW will run using wine on virtually and linux distribution, check [http://appdb.winehq.org/](http://appdb.winehq.org/) for others.  Unfortunately, you are trying to run windows games, of course the easiest way to run them is on Windows and not all of them will work on linux through wine.

You mentioned missing drivers and spontaneous crashes.  Do you know which ones are missing?

---

### Post by kansasnoob on 2009-11-02
> **Locke_99GS said:**
> What devices are giving you issues in Linux?

+1! If you're able to run any Ubuntu live CD some computer specs would be helpful. From the Live CD you could go to Applications > Accessories > Terminal and then post the output of these commands:

```
lspci | grep VGA
```

```
lspci | grep Audio
```

```
lspci | grep Ethernet
```

```
cat /proc/cpuinfo
```

```
cat /proc/meminfo
```

---

### Post by sliketymo on 2009-11-02
> **kansasnoob said:**
> +1! If you're able to run any Ubuntu live CD some computer specs would be helpful. From the Live CD you could go to Applications > Accessories > Terminal and then post the output of these commands:

```
lspci | grep VGA
``````
lspci | grep Audio
``````
lspci | grep Ethernet
``````
cat /proc/cpuinfo
``````
cat /proc/meminfo
```

++1
Netbook re-mix?

---

### Post by Godsrycht on 2009-11-03
> **unamanic said:**
> WoW will run using wine on virtually and linux distribution, check [http://appdb.winehq.org/](http://appdb.winehq.org/) for others.  Unfortunately, you are trying to run windows games, of course the easiest way to run them is on Windows and not all of them will work on linux through wine.

You mentioned missing drivers and spontaneous crashes.  Do you know which ones are missing?

I've used Wine but both Counter-Strike and WoW the text overlaps and I don't think its getting full 32 gfx. I cant get drivers for my graphics. I listed my laptop brand and type to hopefully divulge the specs. The issues I have with the games are because the driver for my GPU is unavailable to me. I read up online about it. Aparantly I would need to revert from 9.8 to like 8.something to get it and when I do its like a 3 page step by step on how to install it. I have no idea why it crashes but I'll be playin a game or whatever and BAM my laptop turns off.

---

### Post by danastasio on 2009-11-03
Telling us you have an Acer is just about as helpful as telling us your car is black when it wont turn on. If you dont know your computer specs, then refer to kansasnoob's post to get us the nessicary information. Also, there is no "9.8" version of Ubuntu, so your either running 9.10 or 9.04, or not running ubuntu at all. we would -love- to help you, but your not giving us anything to go on!

---

### Post by NickJones on 2009-11-03
The power? That doesn't sound like a problem with the distro, it could be faulty solder on the power connector, on you battery, anything, and leaving it on your desk running may not cause the crash, but when you are gaming you franticly mash the keyboard and mouse, that causes the failure.

---

### Post by TheForumTroll on 2009-11-03
> **Godsrycht said:**
> I'll be playin a game or whatever and BAM my laptop turns off.

In Windows or Linux?
If it's in Windows you might have a BSoD that you can't see because Windows is set to restart automatically. I'm sorry but I can't remember where it is changed precisely but it is something like Right click "Computer" -> Properties -> Advanced -> Startup and recovery -> Automatically restart something something... and then remove the tick there.

---

### Post by bubbles99 on 2009-11-03
WoW is known 2 work under WINE (see package manager), not sure about the other one. problems with device may just be settings or OLD drivers. update them in windows 1st.

---

### Post by NickJones on 2009-11-03
> **TheForumTroll said:**
> In Windows or Linux?
If it's in Windows you might have a BSoD that you can't see because Windows is set to restart automatically. .
I think he said that it shuts it down, not re-start, that would rule out the BSOD.

---

### Post by Xatolos on 2009-11-03
*from another page* You said it's an Acer Aspire 5515?
**Specs on Acer Aspire 5515**
15.4" WXGA Acer CrystalBrite
AMD Athlon 64 Processor 2650e (512KB L2 cache, 1.6GHz) < --- not dual core
ATI Radeon x1200 Graphics
3GB DDR2 667MHz SDRAM
160GB SATA hard drive, 5400RPM
DVD Super Multi Double Layer Optical Disc Drive
Wireless LAN  -802.11b/g
Windows Vista Home Basic SP1
Six-cell battery

To start with, I would suggest putting the Ubuntu disk in the laptop and booting off it. Run a Cd Check for errors on the disk during burning. I had massive issues similar to what your describing since I didn't do that and found out it was from a bad burn.
As for your laptops spec's, you shouldn't have a problem playing your games unless Wine has an issue with the Windows game (you can check at [http://appdb.winehq.org/index.php](http://appdb.winehq.org/index.php)). I've found in the past that Linux tends to play games like WoW a little fast in Linux then in Vista due to less background programs running.
Once you have Ubuntu installed (I would suggest Ubuntu 9.10 which is the latest version) make sure to run the updater (it's found in System -> Administration -> Update Manager). After thats been completed go to System -> Administration -> Hardware Drivers, it should have a listing for the drivers for your graphic card which will be needed to run your games.
To play your games you'll need Wine (which isn't on Ubuntu by default) so go to Applications -> Ubuntu Software Centre and do a search for Wine, and Wine Microsoft Compatibility Layer should be the first option. Double click on it and click the Install button at the bottom of the description. This will install Wine version 1.0.1 (so you can tell which instruction set you want to read for help with your game. You can also download a newer version of Wine from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) which is a list of pretty much every version of Wine though some made certain games running better/smoother at the cost of other games. Read first. I'm also guessing that it would be safe to install the Ubuntu 9.04 version since they don't have any Ubuntu 9.10 options, but this is a risk you need to consider since I'm not sure what will truely happen. When in doubt stick with the one in Ubuntu Software Centre.)
Good luck

---

### Post by Godsrycht on 2009-11-03
> **Xatolos said:**
> *from another page* You said it's an Acer Aspire 5515?
**Specs on Acer Aspire 5515**
15.4" WXGA Acer CrystalBrite
AMD Athlon 64 Processor 2650e (512KB L2 cache, 1.6GHz) < --- not dual core
ATI Radeon x1200 Graphics
3GB DDR2 667MHz SDRAM
160GB SATA hard drive, 5400RPM
DVD Super Multi Double Layer Optical Disc Drive
Wireless LAN  -802.11b/g
Windows Vista Home Basic SP1
Six-cell battery

To start with, I would suggest putting the Ubuntu disk in the laptop and booting off it. Run a Cd Check for errors on the disk during burning. I had massive issues similar to what your describing since I didn't do that and found out it was from a bad burn.
As for your laptops spec's, you shouldn't have a problem playing your games unless Wine has an issue with the Windows game (you can check at [http://appdb.winehq.org/index.php](http://appdb.winehq.org/index.php)). I've found in the past that Linux tends to play games like WoW a little fast in Linux then in Vista due to less background programs running.
Once you have Ubuntu installed (I would suggest Ubuntu 9.10 which is the latest version) make sure to run the updater (it's found in System -> Administration -> Update Manager). After thats been completed go to System -> Administration -> Hardware Drivers, it should have a listing for the drivers for your graphic card which will be needed to run your games.
To play your games you'll need Wine (which isn't on Ubuntu by default) so go to Applications -> Ubuntu Software Centre and do a search for Wine, and Wine Microsoft Compatibility Layer should be the first option. Double click on it and click the Install button at the bottom of the description. This will install Wine version 1.0.1 (so you can tell which instruction set you want to read for help with your game. You can also download a newer version of Wine from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) which is a list of pretty much every version of Wine though some made certain games running better/smoother at the cost of other games. Read first. I'm also guessing that it would be safe to install the Ubuntu 9.04 version since they don't have any Ubuntu 9.10 options, but this is a risk you need to consider since I'm not sure what will truely happen. When in doubt stick with the one in Ubuntu Software Centre.)
Good luck

Thhhhhhhhhhhhank YOU
Now the question is will 9.10 HAVE my 1200x gpu driver I need because 9.04 didn't.

---

### Post by Darce on 2009-11-03
Linux drivers and installation instructions for your GPU are here :

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx)

Cheers,

Tim

---

