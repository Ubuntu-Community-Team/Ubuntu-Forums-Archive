---
title: "Ubuntu 10.04 - Ati Radeon hd 5770"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by kaka224 on 2010-08-12
Hi, this is my second time using ubuntu, i tried ubuntu last year but i got fed up with it but i think its time to try again:D
but now i've run into a problem again :(

i wanted to enable those desktop effects because lets admit it they are awesome but i keep getting the "desktop effects could not be enabled". i have googled this error and i have found lots of suggestions on how to fix them. the problem is they all keep using these codes and it gets really confusing. I tried following some of these codes and i have no idea if i'm doing them right or if i'm messing up the computer,lol

i am reading an ebook called ubuntu pocket guide from this website [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
but before i start getting into it i want the desktop effects to be on :P

if you could also recommend any free ebooks or tutorials out there i will be grateful

---

### Post by akand074 on 2010-08-12
Do you have your proprietary drivers installed? If not, go to System > Administration and select Hardware drivers and select your graphics driver to have them installed. Then restart your computer and try enabling the  desktop effects. If you haven't already install compizconfig settings manager, a good way to play around with cool effects. 

```
sudo apt-get install compizconfig-settings-manager 
```

also there are some extras so if this isn't installed use this command as well

```
sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-extra
```

You could also run Synaptic Package Manager from System > Administration and just search those files and install them. After you install it the settings manager comes up in System > Preferences. 

I hope that helps.

---

### Post by kaka224 on 2010-08-12
> **akand074 said:**
> Do you have your proprietary drivers installed? If not, go to System > Administration and select Hardware drivers and select your graphics driver to have them installed.

i get an error saying "SystemError: installArchives() failed"

i also installed compiz and i dont get any effects

---

### Post by akand074 on 2010-08-13
> **kaka224 said:**
> i get an error saying "SystemError: installArchives() failed"

i also installed compiz and i dont get any effects

Weird.. I'm not sure why it does that. Try installing the drivers manually directly from the [ATI page]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English")? 

And also just to clarify I had you install the compizconfig settings manager so you could use it to enable particular effects (many aren't enabled by default) if you haven't done that already of course. But the reason they aren't working otherwise is likely because you don't have your graphics drivers enabled.

---

### Post by Zorgoth on 2010-08-13
With an ATI Radeon 5770, I would not recommend using System>Administration>Hardware Drivers because that is a very new card and the drivers you get from the tool are somewhat old.

First, if you used System>Administration>Hardware Drivers, use the same tool to REMOVE the drivers you installed.

Then download the appropriate hardware driver from ATI's website (I believe Catalyst 10.7 for linux right now) - they have a thing that asks you your OS, card, etc and gives you the best driver.

Then 

sudo sh <script-from-ati-website>
Select to install to your kernel, not to build a .deb (as I don't think the .deb actually works)
sudo ati-config --initial

Reboot.  Your card should work now.  Note that you will have to reinstall your drivers for your card every time your kernel is upgraded until Ubuntu's Hardware Drivers tool catches up with your card.

---

### Post by kaka224 on 2010-08-13
> **akand074 said:**
> Weird.. I'm not sure why it does that. Try 
And also just to clarify I had you install the compizconfig settings manager so you could use it to enable particular effects (many aren't enabled by default) if you haven't done that already of course. But the reason they aren't working otherwise is likely because you don't have your graphics drivers enabled.

yeh thats what i did went to the config and enabled some effects didnt work

> Then download the appropriate hardware driver from ATI's website (I believe Catalyst 10.7 for linux right now) - they have a thing that asks you your OS, card, etc and gives you the best driver.

Then 

sudo sh <script-from-ati-website>
Select to install to your kernel, not to build a .deb (as I don't think the .deb actually works)
sudo ati-config --initial

ok so when you say "<script-from-ati-website>" do you mean the name of the file if so i get an error on the terminal saying
```
sh: Can't open ati-driver-installer-10-7-x86.x86_64
```

---

### Post by ThomasTheTan on 2010-08-16
The file you are looking for has ".run" at the end.  Everything else is correct.

I just downloaded this driver myself, and the filename is

```
ati-driver-installer-10-7-x86.x86_64**.run**
```You need to put the ".run" to your command.

Also, [here]("http://www.overclock.net/linux-unix/509761-how-linux-ati-driver-installation.html") is a site that I have found really useful in the past when installing these drivers.

Hope this helps!

---

### Post by kaka224 on 2010-08-16
> **ThomasTheTan said:**
> The file you are looking for has ".run" at the end.  Everything else is correct.

I just downloaded this driver myself, and the filename is

```
ati-driver-installer-10-7-x86.x86_64**.run**
```You need to put the ".run" to your command.

Also, [here]("http://www.overclock.net/linux-unix/509761-how-linux-ati-driver-installation.html") is a site that I have found really useful in the past when installing these drivers.

Hope this helps!

yeh i did that run but it still didnt work

however i did find a solution so if anyone has the same problems then solution is on this website [http://www.overclock.net/linux-unix/793878-how-do-i-install-ati-drivers.html](http://www.overclock.net/linux-unix/793878-how-do-i-install-ati-drivers.html)

Thanks you guys for helping me :D

---

