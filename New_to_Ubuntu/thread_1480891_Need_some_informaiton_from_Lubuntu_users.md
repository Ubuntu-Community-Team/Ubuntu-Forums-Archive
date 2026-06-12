---
title: "Need some informaiton from Lubuntu users"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by mastablasta on 2010-05-12
I gave it a go on aging notebook with 1.2 Ghz AMD CPU and only 256Mb Ram (of which graphics card takes some). And i have to say WOW! for the speed.
I measured the start up with a stopwatch and within less than 6 minutes (from when i pressed the power button) Live CD came to a bootable system. As a comparison - current instalation on it of WinXp Sp3 takes about 10 minutes to boot to a usable system (because it needs to load firewall and antivirus).
 
I did some browsing of the system to see if all things work. And they do. Even the PCMCIA wifi card (with which i even connected to an unknown unlocked Lynsys router).
 
Most things work, and the GUI doesn't crash like 9.10 (Ubuntu, Kubuntu, Xubuntu). In fact nothing crashed, everyhting worked. However there is plenty of error messages. Could it be they are there because i was running a live session?
 
What i could not test was Flash & Java in Chromium for obvious reasons...
 
Anyway i have the following question - all programmes there are lightweight. However what i miss most is Ubuntu Software center and Open office. Open office to me is a must. Software center would also be very good since i am not so experienced with synaptic. Is it possible to install these two? And how does actually open office work on such a limited system (256MBram)?! Also what about evolution? does it integrate well into it? I will maybe also need a few other progammes such as compozer (or NVU - whichever works in Linux).
 
Just as a side info at the moment the WinXP installed there works reasonably well once it is booted (with occasional crash probably due to overheating?!). It can run reasonably well Office 2003, firefox, firebird, mediaplayer and divX movies, mp3 (only if you don't do anyhting else) and latest yahoo messanger. I would like to be able to run these with lubuntu (or their "alternatives").

---

### Post by FrPaulB on 2010-05-12
I ran lubuntu with a 600 Mhz PIII and 256 MB RAM. Installing software centre through synaptic caused a lot of hard disk thrashing - I suspect it was busy making a new index. I took it off and just used synaptic - which wasn't hard. I did install update manager, although that just automates updates that you can do using synaptic or the command line.

Installing Open Office is straightforward. Look through synaptic for the OpenOffice.org entry - that's a shell which when selected for installation will gather up all the components you need. Language settings in the main preferences (I think that's where it is) will tidy up spell checking. Open Office is a bit slow to load - say 60s, but seems to work OK - I wouldn't try lots of macros in a spreadsheet or anything too complex though.

I have CrunchBang 9.04 on the machine now, which I think I prefer.

---

### Post by Ozymandias_117 on 2010-05-12
> Most things work, and the GUI doesn't crash like 9.10 (Ubuntu, Kubuntu, Xubuntu). In fact nothing crashed, everyhting worked. However there is plenty of error messages. Could it be they are there because i was running a live session?
It would help if you said what some of the errors are.

> What i could not test was Flash & Java in Chromium for obvious reasons...
Just type in a terminal:
```
sudo aptitude install ubuntu-restricted-extras
```

> Anyway i have the following question - all programmes there are lightweight. However what i miss most is Ubuntu Software center and Open office. Open office to me is a must. Software center would also be very good since i am not so experienced with synaptic. Is it possible to install these two? And how does actually open office work on such a limited system (256MBram)?! Also what about evolution? does it integrate well into it? I will maybe also need a few other progammes such as compozer (or NVU - whichever works in Linux).
I believe you have to be running Gnome/KDE for Ubuntu Software Center. Open office should install fine... prob run kinda slow with only 256 MB of RAM. Might want to try something like AbiWord. No idea about Evolution.

> ... Office 2003, firefox, firebird, mediaplayer and divX movies, mp3 (only if you don't do anyhting else) and latest yahoo messanger. I would like to be able to run these with lubuntu (or their "alternatives").
Office 2003 = OpenOffice

Firefox = Firefox

Do you mean Thunderbird? if so = Evolution or Thunderbird

mediaplayer = tons... I would use VLC for movies, but it doesn't have a very good library feature on it, so you might want something different for music.

mp3 = the ubuntu-restricted-extras package will let you use mp3

yahoo messanger = empathy

---

### Post by mastablasta on 2010-05-12
> **Ozymandias_117 said:**
> It would help if you said what some of the errors are.

Unfortunatelly the screen scrolled really fast past them. Last one before shutdown it was something about dev0 not being able to shut it down. While in beginning it could not start some devices (though everything seemed to work just fine). 
 
 
 > 
Just type in a terminal:
```
sudo aptitude install ubuntu-restricted-extras
```
 
 
In a live session? Will it work?
 
>  
Office 2003 = OpenOffice
 
Firefox = Firefox
 
Do you mean Thunderbird? if so = Evolution or Thunderbird
 
mediaplayer = tons... I would use VLC for movies, but it doesn't have a very good library feature on it, so you might want something different for music.
 
mp3 = the ubuntu-restricted-extras package will let you use mp3
 
yahoo messanger = empathy 
I know the "alternatives" i just dont' know how good they would run on such a system. BTW the default messanger in Lubuntu is Pidgin not empathy :-)
 
[QUOTE=FrPaulB]Installing Open Office is straightforward. Look through synaptic for the OpenOffice.org entry - that's a shell which when selected for installation will gather up all the components you need. Language settings in the main preferences (I think that's where it is) will tidy up spell checking. Open Office is a bit slow to load - say 60s, but seems to work OK - I wouldn't try lots of macros in a spreadsheet or anything too complex though.[/QUOTE] 
 
Ugh it's just that synaptic is so confusing to me unless i know exactly the package/library i am looking for. then it is easy... Good to hear about open office. I don't plan any heavy duty tastks for it. i have two other computers for that. but most of it i need to be able to open a document. I know it probably loads slow. Well currently MS Word 2003 also loads a bit slow and later i can work on it providing i don't have any other programme running in the background (such as firefox or yahoo messanger).

---

### Post by ranch hand on 2010-05-12
There is little that anyone can tell you with out know ing what you have in mind as far as installation goes and what the size of your drive is.

I would encourage you to stick with synaptic but do not see any reason that you could not install the software center.

You can try anything you want on the live CD.  Need more codecs just install them.  They will stay right there on your ram until you shut down (or remove them) so watch how much you install.

Lubuntu is a very nice OS.  I have a copy on here that has been on since December (testing).  Have had very little trouble with it.  This box (see my sig) is a little over powered for it but boy does it run on here.

As far as what you want to install, if it is in syanptic you can install it.  Some things ment for Kubuntu will pull in a lot of extra files as dependencies.

This is why disk size matters here.  If you wipe MS off you probably have plenty of room.  Open Office is a big bugger.  If you do not use all of it I would not install the meta package but just the components you are going to use.

Leave Update Mangler off and use synaptic for that.  Not a good app at all.

---

### Post by mastablasta on 2010-05-12
Exactly what i was afraid with so little ram i doubt i would experience the flash propperly.
 
HDD is 20 GB of which 4 gb iis reserved as system restore partition for windows. if i could get a system restore CD then maybe this one would be unnecessary. But basically if i uninstall WinXP later off i woul dhave 16 GB, which is "plenty".

---

### Post by ranch hand on 2010-05-12
That system restore is to restore your MS installation not your computer so if you get rid of that albatros you can get rid of the restore too (its main function is to restore the boot loader).

I would try installing the package for flash;
```

apt-get install ubuntu-restricted-extras

```
on a Live CD live session.

It is a lot of load on the ram but it might work.  You have that stuff on there now and it must work, I suspect it will work under Lubuntu as well.

---

### Post by I2k4 on 2011-03-06
Maybe I misunderstand, but sounds as if you're using a CD and not a USB drive to boot Lubuntu.  I can't imagine the OS taking 6 minutes to boot with a USB, even at 250mb RAM, although you might have an old USB 1.0 socket on that old machine.  

Also on a USB installation (suggest 4GB with 2GB for the OS and 2GB for "Persistence") all your settings would be saved between boots.  Using a CD without "Persistent" memory would essentially prevent anything being added to the basic OS installation.  As I say, maybe I've misread your situation.

---

### Post by beew on 2011-03-06
@OP

You have problem with Synaptic because the default install of Synaptic in Lubuntu is not quite usable. In their infinite wisdom they decide to remove the search function so if you want it back you have to install it yourself by installing apt-xapian-index.

 I don't know how much that would make the distro lighter.

---

