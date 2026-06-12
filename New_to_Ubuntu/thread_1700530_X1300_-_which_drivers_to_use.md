---
title: "X1300 - which drivers to use ?"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by anotherdummhead on 2011-03-05
I don't know which one will work best with this card, i only did this :

> sudo apt-get fgrlx

and this :

> sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install fglrx-modaliases

So is this ok, and is it better to switch to another driver, and how ?

---

### Post by ikt on 2011-03-05
> **anotherdummhead said:**
> I don't know which one will work best with this card, i only did this :



and this :



So is this ok, and is it better to switch to another driver, and how ?

Are there any graphics driver options available in:

System > Administrator > Additional Drivers

?

---

### Post by anotherdummhead on 2011-03-05
Nope, no proprietary drivers used or displayed, nothing.

---

### Post by anotherdummhead on 2011-03-05
Can't install proprietary drivers, neither 8 version (X.server or somethin isn't detected) and neither 9 because of some error (i think it's not supported)

---

### Post by ikt on 2011-03-05
> **anotherdummhead said:**
> Nope, no proprietary drivers used or displayed, nothing.

Bugger.

It looks like you can manually install the driver from the AMD site, instructions here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20the%20fglrx%20Driver%20from%20AMD/ATI%20Catalyst%2011.2%20For%20Ubuntu%2010.10%20Maverick](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20the%20fglrx%20Driver%20from%20AMD/ATI%20Catalyst%2011.2%20For%20Ubuntu%2010.10%20Maverick)

and download file is located here:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

Just noticed should probably check out:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installation%20of%20the%20fglrx%20Driver%20from%20the%20Ubuntu%2010.10%20Maverick%20Repositories](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installation%20of%20the%20fglrx%20Driver%20from%20the%20Ubuntu%2010.10%20Maverick%20Repositories)

Just to make sure it's not already installed.

---

### Post by ikt on 2011-03-05
> **anotherdummhead said:**
> Can't install proprietary drivers, neither 8 version (X.server or somethin isn't detected) and neither 9 because of some error (i think it's not supported)

Which errors? What version of ubuntu are you running?

---

### Post by anotherdummhead on 2011-03-05
Xubuntu 10.10, this is the error when i want to install 9.3 driver which you gave me :

> 
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro                                              

Removing temporary directory: fglrx-install.V4Vja4

and this is what i get when trying to install 8.24 :

> /etc/X11/xinit/xserverrc: line 51: exec: **X: not found**

---

### Post by anotherdummhead on 2011-03-05
I'm reinstalling Xubuntu now, and i'll try following this instructions, what's the difference between these drivers and fglrx ?

---

### Post by ikt on 2011-03-05
> **anotherdummhead said:**
> Xubuntu 10.10, this is the error when i want to install 9.3 driver which you gave me :



and this is what i get when trying to install 8.24 :

D:

After some quick reading it looks like you're using the open source driver already, what is the output of:

fglrxinfo

?

---

### Post by anotherdummhead on 2011-03-05
Haha i'll tell you right after i finish installing Xubuntu, again :P

---

### Post by ikt on 2011-03-05
> **anotherdummhead said:**
> I'm reinstalling Xubuntu now, and i'll try following this instructions, what's the difference between these drivers and fglrx ?

Proprietary drivers generally have better performance for games etc

Just found this:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

> See the complete list here. **If your card is on that list, you are limited to open-source drivers on Ubuntu Lucid/10.04 (and later)**

[http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4)

> ATI Radeon X1300 Series 

Well there ya go, the drivers for your card haven't been updated to support the latest versions of x.org, so it won't run on ubuntu 10.10

So you're stuck with the opensource driver, not horrible but not fantastic either :/

---

### Post by anotherdummhead on 2011-03-05
Mate so if i install Xubuntu 10.04, i would be able to run these drivers, right ? (really stupid question, but i'm gonna download it right now if that's the case)

---

### Post by klytu on 2011-03-05
> **anotherdummhead said:**
> I don't know which one will work best with this card, i only did this :



and this :



So is this ok, and is it better to switch to another driver, and how ?

I think you'll need to use the open source driver (which should be installed automatically). FYI, I have a Radeon X1650 and I haven't been able to get ATI's proprietary driver to work since upgrading from Ubuntu 8.04. If I recall correctly, the last version of ATI's catalyst drivers to support our cards (which are in legacy status for ATI..) was 9.3. However, the version of Xorg that Ubuntu currently uses is incompatible with that catalyst driver version.

So, my advice is save yourself some time and headaches and don't try to install any drivers for your card; use the open source driver.

---

### Post by ikt on 2011-03-05
> **anotherdummhead said:**
> Mate so if i install Xubuntu 10.04, i would be able to run these drivers, right ? (really stupid question, but i'm gonna download it right now if that's the case)

Even further, you'll have to go back to 8.10 or 8.04 I believe.

> **klytu said:**
> So, my advice is save yourself some time and headaches and don't try to install any drivers for your card; use the open source driver.

Indeed, I'm not so sure the x1300 would be that fantastic for games anyway.

---

### Post by anotherdummhead on 2011-03-05
> **ikt said:**
> Even further, you'll have to go back to 8.10 or 8.04 I believe.



Indeed, I'm not so sure the x1300 would be that fantastic for games anyway.

Sry mate, well on XP i even got WoW to run on medium details :D but in time i'll get it to work here also :P And i didn't have time to edit my post, returning back to 8.04 will give me even more headaches than this..

> **klytu said:**
> I think you'll need to use the open source driver (which should be installed automatically). FYI, I have a Radeon X1650 and I haven't been able to get ATI's proprietary driver to work since upgrading from Ubuntu 8.04. If I recall correctly, the last version of ATI's catalyst drivers to support our cards (which are in legacy status for ATI..) was 9.3. However, the version of Xorg that Ubuntu currently uses is incompatible with that catalyst driver version.

So, my advice is save yourself some time and headaches and don't try to install any drivers for your card; use the open source driver.

Ah our cards really suck :(

So basically you're suggesting me to boot up my system, run the Update Manager, and that's it ? I'll have the latest open source drivers ?

---

### Post by klytu on 2011-03-05
> **ikt said:**
> Proprietary drivers generally have better performance for games etc

Just found this:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)



[http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4)



Well there ya go, the drivers for your card haven't been updated to support the latest versions of x.org, so it won't run on ubuntu 10.10

So you're stuck with the opensource driver, not horrible but not fantastic either :/

Correct on all counts. IMO, the open source driver performs adequately although the old proprietary driver provide faster acceleration.

---

### Post by anotherdummhead on 2011-03-05
> **klytu said:**
> Correct on all counts. IMO, the open source driver performs adequately although the old proprietary driver provide faster acceleration.

Well i don't need it that much for the games itself, the pc runs slow when opening youtube clips etc. (on basic things)

Update Manager > Apply > and i have the latest open source drivers ?

---

### Post by klytu on 2011-03-05
> **anotherdummhead said:**
> Sry mate, well on XP i even got WoW to run on medium details :D but in time i'll get it to work here also :P And i didn't have time to edit my post, returning back to 8.04 will give me even more headaches than this..



Ah our cards really suck :(

So basically you're suggesting me to boot up my system, run the Update Manager, and that's it ? I'll have the latest open source drivers ?

Correct.

---

### Post by klytu on 2011-03-05
> **anotherdummhead said:**
> Well i don't need it that much for the games itself, the pc runs slow when opening youtube clips etc. (on basic things)

Update Manager > Apply > and i have the latest open source drivers ?

Hmm ... It shouldn't be running slowly because of the graphics card; our cards suck but they aren't ***that*** bad! :-) Are you running Compiz? If so, you might want to skim through this thread which documents some issues I had when I upgraded from 8.04 to Lucid (10.04):

[http://ubuntuforums.org/showthread.php?t=1563123](http://ubuntuforums.org/showthread.php?t=1563123)

At that time, my troubles were caused by a saved Compiz configuration file that was incompatible with the version of Compiz in the upgrade.

---

### Post by ikt on 2011-03-05
> **anotherdummhead said:**
> Well i don't need it that much for the games itself, the pc runs slow when opening youtube clips etc. (on basic things)

Have you tried chrome?

[http://www.google.com/chrome](http://www.google.com/chrome)

It may possibly help, flash performance is generally woeful depending on which version of flash you have installed, chrome has it's own version built in, which is usually the latest and works quite snappy.

---

### Post by anotherdummhead on 2011-03-05
> **klytu said:**
> Hmm ... It shouldn't be running slowly because of the graphics card; our cards suck but they aren't ***that*** bad! :-) Are you running Compiz? If so, you might want to skim through this thread which documents some issues I had when I upgraded from 8.04 to Lucid (10.04):

[http://ubuntuforums.org/showthread.php?t=1563123](http://ubuntuforums.org/showthread.php?t=1563123)

At that time, my troubles were caused by a saved Compiz configuration file that was incompatible with the version of Compiz in the upgrade.

Dunno. I formated my root partition, left home untouched, and probably i've deleted all of my display drivers, right ? So it should be able to update it now from update manager..how can i verify if i'm running open-source drivers only and which version am i running ?

> **ikt said:**
> Have you tried chrome?

[http://www.google.com/chrome](http://www.google.com/chrome)

It may possibly help, flash performance is generally woeful depending on which version of flash you have installed, chrome has it's own version built in, which is usually the latest and works quite snappy.

No i haven't tried out chromium, i'm avoiding it because on XP it suffocated my system, it couldn't breathe :D so basically opera or mozzila :) 

And flash plugin caused me so much trouble, i tried installing gnash (fail!) because adobe kept on crashing. Thanks for all the info guys :) 

EDIT : I booted up my Xubuntu, again ! :D So what should i type in terminal to see which drivers am i using after the restart ?

---

### Post by anotherdummhead on 2011-03-05
How can i see which drivers am i using atm ?

---

### Post by ikt on 2011-03-05
> **anotherdummhead said:**
> 
No i haven't tried out chromium, i'm avoiding it because on XP it suffocated my system, it couldn't breathe :D so basically opera or mozzila :) 

=o 

I have to suggest giving it another try, for a lot of us it's by far the lightest, quickest, browser, as a former opera user I know fast when I see it :D

> **anotherdummhead said:**
> 
And flash plugin caused me so much trouble, i tried installing gnash (fail!) because adobe kept on crashing. Thanks for all the info guys :)

Yeah, adobe flash on linux has been fail for quite a while, only a couple of months ago did they even release a fix to be able to run youtube videos on full screen, before that if you went full screen it would go all choppy and lag and then crash :/

> How can i see which drivers am i using atm ?

If you go into Jockey(System > Admin > Additional Drivers) and there's nothing enabled, you're using the open source drivers, if you use the proprietary drivers it will show up there.

---

### Post by anotherdummhead on 2011-03-05
Well that was on XP, maybe here Chromium is lighter :P I'll try it :)

OK, so i'll have to download the flash player and that fix, because sometimes i see red clips, sometimes it crashes.

Thanks for the info :) I'll look at that, and keep you informed of the performance. And the thing you wanted me to type, fglrxinfo, that should tell me which version am i using, right ?

EDIT : Have i made a mistake when i selected not to delete the /home partition ?

---

### Post by anotherdummhead on 2011-03-05
.

---

### Post by anotherdummhead on 2011-03-05
So if i got this right, fglrx are the proprietary drivers, and the  drivers that the system is using are the open source drivers, right ?

Should i install fglrx for x1300 or it's better to stick with only these ?

Cheers and thanks for your help :)

---

### Post by Mark Phelps on 2011-03-05
> **anotherdummhead said:**
> Should i install fglrx for x1300 or it's better to stick with only these ?

You can't install fglrx drivers from the X1300 because there are no such drivers that will work with recent versions of Ubuntu (later than 8.10). Doesn't matter where you get them from, they simply won't work.

The open-source drivers you currently have installed are the only ones that will work.

---

### Post by anotherdummhead on 2011-03-05
So basically it's the same thing, installed them or not, they won't work...ok thread solved :)

---

