---
title: "Audigy SE not found!!"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by Kaymeerah on 2009-10-02
hello, i got a problem with Audigy SE and dualbooting windows and ubuntu, each time i boot to windows it does find the soundcard, as the drivers install, however, at the same time it cant identify it after using ubuntu, and if i take the sound card out, then put it in again windows finds it and uses it, however then UBUNTU wont use it..

any ideas?

---

### Post by TheLions on 2009-10-02
it seems that your linux driver is not installed (you'll need this one:[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106))

this won't be easy, but you'll need to compile alsa yourself:
download all files:
[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)
Driver (alsa-driver)
Firmware alsa-firmware)	
Library (alsa-lib)	
Plugins (alsa-plugins)	 
Utilities (alsa-utils)	
Tools (alsa-tools)	

extract each of them to seperate directory
open terminal
go to extacted directory (eg. "cd /home/petar/ALSA/" )
type "./configure"

IF SOME ONE GOT BETTER IDEA PLEASE POST HERE!
beceause this could screw you Ubuntu instalation

---

### Post by Kaymeerah on 2009-10-02
> **TheLions said:**
> it seems that your linux driver is not installed (you'll need this one:[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106))

this won't be easy, but you'll need to compile alsa yourself:
download all files:
[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)
Driver (alsa-driver)
Firmware alsa-firmware)	
Library (alsa-lib)	
Plugins (alsa-plugins)	 
Utilities (alsa-utils)	
Tools (alsa-tools)	

extract each of them to seperate directory
open terminal
go to extacted directory (eg. "cd /home/petar/ALSA/" )
type "./configure"

IF SOME ONE GOT BETTER IDEA PLEASE POST HERE!
beceause this could screw you Ubuntu instalation

this is the first thing i did after it didnt work anymore, it caused windows to NOT find the soundcard again, until i ripped out the audigy and put it in again, then it works for windows.. but i have to reinstall drivers at ubuntu again , its an infinite loop with 1 way out i cant find (dont have OS disks available :/)

---

### Post by TheLions on 2009-10-03
I dont see a conection, how can each OS affect on behavior of some hardware...

maybe Win/Linux drivers are changing cards firmware? :confused:

---

### Post by advocate 21 on 2009-10-04
update everything.
then install wine
then install your audigy using the disc that came with it.
i had one at one point. i didnt need it afterwards.

---

### Post by Kaymeerah on 2009-10-04
buying a new sound card anyways, this one is actually failing misserably (noticing on how pulse and the windoze sound drivers act cocky)

---

### Post by TheLions on 2009-10-05
Haven't you have soundcard on your mainboard?

---

### Post by Perfect Storm on 2009-10-05
> **TheLions said:**
> Haven't you have soundcard on your mainboard?

+1

If your motherboard have an onboard sound card, you might want to disable it in the BIOS first.

---

### Post by Kaymeerah on 2009-10-05
it IS disabled in the BIOS, my computer skills are good (not to brag about myself)

---

### Post by TheLions on 2009-10-06
> **Kaymeerah said:**
> it IS disabled in the BIOS, my computer skills are good (not to brag about myself)

but why buy another if you have another on your mainboard? :confused::confused::confused:

---

### Post by Kaymeerah on 2009-10-09
> **TheLions said:**
> but why buy another if you have another on your mainboard? :confused::confused::confused:

the motherboard one can interrupt the booting sequence of both linux and windows (BSOD)

---

