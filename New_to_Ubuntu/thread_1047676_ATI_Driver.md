---
title: "ATI Driver"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by rp181 on 2009-01-22
I am running Ubuntu Intrepid [?].
I am trying to install an ATI graphics card for a Radeon 300x SE. When i do  fglrxinfo i get:

phani@phani-desktop:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10


What do i do?

---

### Post by coyotito on 2009-01-22
Do you need Intrepid?
I tried to install it two days ago, worst experience ever installing linux and i do have some experience..
It could not set up my totally ordinary webcam because of a kernel issue (this is apparently an unstable kernel), neither my sturdy old Soundblaster Audigy, this because ubuntu insists on messing with pulseaudio before it's ready for general use. I got no sound at all.
The 3g connect utility was great but this also works from command line so..

I installed Hardy which works fine.

I tried the ATI driver for my HD4670 but neither fglrx or radeon worked.
Then i used the driver from ATI's site and it worked out of the box.
However I've put the card up for sale because it does not have the kind of driver support you get from nvidia --I'm getting a geforce 9600 w passive cooling.

---

### Post by rp181 on 2009-01-22
No, i haev ubuntu installed, but i need the ATI Graphics driver installed. I downloaded from the website but that isnt doing anything.

---

### Post by Daveth on 2009-01-22
download EnvyNG from Synaptic, which runs off and get the driver for you; I'm not up on ATI cards so I assuming this is a newish one.It has an older version for legacy cards as I recall.

---

### Post by coyotito on 2009-01-22
> **rp181 said:**
> No, i haev ubuntu installed, but i need the ATI Graphics driver installed. I downloaded from the website but that isnt doing anything.
what do you mean isnt doing anything? you have to set the file permissions as executable, at least i had to.

---

### Post by bwang on 2009-01-22
Check System>Administration>Hardware Drivers for drivers. It may be that your card is detected automatically, which makes installing the drivers a lot easier.

---

### Post by rp181 on 2009-01-23
When i execute the driver, i get a pop up window with the title 'Error' but a message 'Succes'. Even then, i dont have any drivers, even in the Hardware Drivers window.

---

### Post by Michael.Godawski on 2009-01-23
hi,

try to install the drivers via envy as described here:


[LIST]
[*][http://ubunturesources.ub.ohost.de/envyngt.html](http://ubunturesources.ub.ohost.de/envyngt.html)
[/LIST]

---

### Post by rp181 on 2009-01-23
yes, i did what that site did, but nothing.

---

### Post by Michael.Godawski on 2009-01-23
Can you please post the output of this terminal command:

```
sudo lshw -C display
```

It will give us some info about your graphic card.

---

### Post by rp181 on 2009-01-23
I typed that in and it restarted my computer, ile try it again now. For envy ng, i get the same options BUT installed as candidate, and the  2 right boxes have '-' in them

---

### Post by rp181 on 2009-01-23
So i did it again, any it said:
PCI (sysfs)
then ubuntu froze up. I did ctrl-alt-backspace to restart.

---

### Post by Bonsanto on 2009-02-16
Epic Fail.

---

### Post by malathion on 2009-02-16
Getting this error too inexplicably since today. More info here: [http://ubuntuforums.org/showthread.php?t=1071693](http://ubuntuforums.org/showthread.php?t=1071693)

---

### Post by Bonsanto on 2009-02-28
My Video card Ati Radeon 300x, works perfectly in WIndows I can play games for example Battlefield 2, VBattlefield 1942, COunter Strike, and in UBuntu I can't play warsaw :(

---

