---
title: "Installing Ubutnu 10.10 from a usb flash drive."
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Skizzorp on 2010-11-15
I'm trying to install ubutnu to a  semi old work station i aquired from work as an experiment(always wanted to go windows free)  never had an extra pc to work with.. 

the trouble im having is it boots fine, then i choose to install ubutnu and it just sits there acting like its doin something but it does this for hours...  the screen never changes  

[www.pendrivelinux.com]("http://www.pendrivelinux.com") is where i got the usb set up program and the distro is ubutnu desktop 10.10 i386  

I don't know what im doing wrong any help will be appreciated

Skizzorp

---

### Post by LowSky on 2010-11-15
hi welcome to the forums


What do you consider semi-old? Do you know the systems specs?

> As the CD boots, the user can gain access to the main page and its options by pressing any key. The language selection screen is displayed and will remain until a selection is made or the ESC key is pressed. 

before installing try hitting F6 and choosing noapic or acpi=off

more help see this
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by laurenbanjo on 2010-11-15
Happened to me, too. I just gave up and took a nap. I woke up two hours later and it worked! So just keep trying... be patient. Really patient. I had to erase and reput Ubuntu on the flash drive THREE times, and with each of those, I tried 3 times before it just didn't recognize Ubuntu anymore and I had to wipe it and put it back on.

---

### Post by Skizzorp on 2010-11-15
Its a Dell Optiplex gx520  half a gig of ram roughly Intel celeron cpu..  um 80 gb hd  sata.. 

and no cd drive thats why im attempting the usb drive installation.  It lets me pick the 

language and whether i want to download updates while installing and then it just seems to 

take forever with the little moving clock icon.  I started it at 2 am last night and then when 

i got up today it was still doing the same screen.. like 8 hours later

---

### Post by sikander3786 on 2010-11-15
And if Lowsky's suggestion of noapic and acpi=off doesn't work, it would be worthy to check the integrity of the downloaded image itself. See here.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by sikander3786 on 2010-11-15
> half a gig of ram roughly Intel celeron cpu.

I fear your Ubuntu experience will not be that good with those specs.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Consider a light-weight fork such as Lubuntu.

[http://lubuntu.org](http://lubuntu.org)

---

### Post by amjjawad on 2010-11-15
I tried to install Ubuntu 10.10 on my 2nd PC (P4 - 480MB of RAM) and I got stuck at the final click when I'm supposed to press "Finish".
I knew immediately that there's a problem with the bootable USB I'm using so I went back to my 1st PC, formatted my USB and created a new LiveUSB using UNetbootin. 

Your first step before anything is [here]("https://help.ubuntu.com/community/HowToMD5SUM"). You need to make sure the iso file you downloaded is not corrupted.
I'm not sure which tools you used to create the LiveUSB but I suggest UNetbootin. [Here]("http://unetbootin.sourceforge.net/") where you can download it.

---

### Post by amjjawad on 2010-11-15
> **sikander3786 said:**
> I fear your Ubuntu experience will not be that good with those specs.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Consider a light-weight fork such as Lubuntu.

[http://lubuntu.org](http://lubuntu.org)

I'm afraid it's time to disagree with you, my friend :D
I just had Ubuntu 10.10 installed on my 2nd PC (RAM 480MB - P4) and I have no issues at all :)

---

### Post by sikander3786 on 2010-11-15
> **amjjawad said:**
> I'm afraid it's time to disagree with you, my friend :D
I just had Ubuntu 10.10 installed on my 2nd PC (RAM 480MB - P4) and I have no issues at all :)
```
free
             total       used       free     shared    buffers     cached
Mem:       1505464    1184568     320896          0     137440     528304
-/+ buffers/cache:     518824     986640
Swap:      2047996          0    2047996

```

Then why it is eating up more than 1GB RAM on my 10.10? With just firefox running 3 tabs. No other apps at all.

```
 1195 root      20   0  191m  75m  20m S  2.3  **5.1**   5:45.97 Xorg               
 1697 malik     20   0  685m  95m  31m S  2.3  **6.5**   6:16.31 firefox-bin        
 1359 malik     20   0  510m  92m  45m S  1.0  **6.3**   6:26.93 mutter             
 2337 malik     20   0  256m  16m  11m S  1.0  **1.1**   0:01.21 gnome-terminal 
```

Well it would be called thread hijacking. I better start a new thread regarding my own problem :-)

---

### Post by Skizzorp on 2010-11-15
I checked the downloaded file and the check was a match  so im sure thats ok im going to try to use that usb creator..  I'll let you know thanks all for your help.. I am looking for a ram upgrade..  hard to find so far..

---

### Post by amjjawad on 2010-11-15
> **Skizzorp said:**
> I checked the downloaded file and the check was a match  so im sure thats ok im going to try to use that usb creator..  I'll let you know thanks all for your help.. I am looking for a ram upgrade..  hard to find so far..

Good luck and hope UNetbootin will work better for you :)

You don't need to upgrade the RAM but if you're looking for a faster performance, there are many other Distributions perhaps you want to try them :)

Check [http://distrowatch.com/](http://distrowatch.com/) and search for Old Computers.

---

### Post by amjjawad on 2010-11-15
> **sikander3786 said:**
> ```
free
             total       used       free     shared    buffers     cached
Mem:       1505464    1184568     320896          0     137440     528304
-/+ buffers/cache:     518824     986640
Swap:      2047996          0    2047996

```Then why it is eating up more than 1GB RAM on my 10.10? With just firefox running 3 tabs. No other apps at all.

```
 1195 root      20   0  191m  75m  20m S  2.3  **5.1**   5:45.97 Xorg               
 1697 malik     20   0  685m  95m  31m S  2.3  **6.5**   6:16.31 firefox-bin        
 1359 malik     20   0  510m  92m  45m S  1.0  **6.3**   6:26.93 mutter             
 2337 malik     20   0  256m  16m  11m S  1.0  **1.1**   0:01.21 gnome-terminal 
```Well it would be called thread hijacking. I better start a new thread regarding my own problem :-)

The only distribution that really bothered me so far with my 2nd PC is Mint 9 GNOME. Fedora 13 GNOME was good and same with Ubuntu 10.10. Before I installed Ubuntu, I checked from the LiveUSB and when I opened ALL OpenOffice Programs + Firefox + not sure what else .. my RAM was 300MB used or a bit less. I'll double check again but I'm sure I had no lags, nothing.

---

