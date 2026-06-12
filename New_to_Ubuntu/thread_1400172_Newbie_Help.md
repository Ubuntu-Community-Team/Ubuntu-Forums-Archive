---
title: "Newbie Help"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Bahlman on 2010-02-06
Alrighty.. Let's see here.

This is my first Linux machine ever, I have always wanted and just have now officially installed it.

System:
Dell Inspiron 8600
1.5GB 333Mhz DDR RAM
GeForce FX5200
1.8Ghz Intel Celeron

A few questions (I'm sorry if these are absolutely stupid for those Ubuntu Gurus out there)
1: When I go to the Ubuntu Software Center and look for some software (such as the Flash software, things like Audacity as well) it says "Not available in the current data." I am unable to find any software that I am able to install.
2: I went to try installing a program off the internet (two actually) both of which ask me to open with a program before installing. I have no programs on here and have no idea where to start to install this stuff.
3: Drivers. I hate drivers. When I go to use the built in driver finder, it doesn't find anything. I tried installing these drivers for my video card (one of the two items from question 2) and I cannot get it to install. 

I am deeply confused but want to learn. Sorry to be an Ubuntu newbie  =(

---

### Post by mushwars on 2010-02-06
if you want flash and the like you need to do this.
```
gksudo gedit /etc/apt/soruces.list
```
and uncomment all the repositories that have a #infront of them especially the restricted ones.

then you need to do this
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

as far as your non-free graphics drivers, you just need to click system and administration and click the one that says something about drivers.

This will search your hardware for available proprietary drivers and ask you if you would like to install, do so.

Other than that you shouldn't have any other drivers you need to install they are all automatic, unlike winblows.

---

### Post by Linux000 on 2010-02-06
go to system/administration/software sources in the top bar on the desktop, check main. universe, restricted, multiverse. Then close it, that is the same as ```
gksudo gedit /etc/apt/soruces.list
``` then look for "ubuntu-restricted extras" in software center.

---

### Post by Bahlman on 2010-02-06
> **mushwars said:**
> as far as your non-free graphics drivers, you just need to click system and administration and click the one that says something about drivers.

This will search your hardware for available proprietary drivers and ask you if you would like to install, do so.

Other than that you shouldn't have any other drivers you need to install they are all automatic, unlike winblows.

So if nothing shows up in that search, I don't have any to install?

---

### Post by snowpine on 2010-02-06
Hi Bahlman, welcome to the forums! You will get some good advice and some bad advice (see above), so be selective choosing which advice to follow. :)

1. You probably need to update your list of available applications. This terminal command should do the trick:

```
sudo apt-get update
```

Does that make more apps appear in your software center?

This should install Flash:

```
sudo apt-get install flashplugin-installer
```

2. I do not recommend that beginners install random software from the internet. That is kind of a "Windows way" of doing things, and as you know, Windows is buggy, insecure, and crashes a lot. :) Stick with the Ubuntu Software Center and you'll have access to trusted and tested applications.

3. Assuming your system is working OK, no "drivers" are necessary (that's a Windows thing). Ubuntu is very good at auto-detecting hardware. (If not, be specific).

Good luck and welcome to the forums!

---

### Post by mushwars on 2010-02-06
I HIGHLY recommend installing ubuntu-restricted-extras. it will install flash, I have had bad experience with flash and *buntu the restricted extras package will install it and it WILL work for sure.

(it is sad how hard getting flash to work is.)

---

### Post by Bahlman on 2010-02-06
I installed the unrestricted extras, and all the plugins work now. This makes me happy. And snowpine, that you very much for making all that make sense to me. When they put the box around the code, I assumed it was for terminal use, but you were the first actually mention where it belongs. And I also don't install "random" software from the internet, I install what I know I can trust. I got spyware once, and I will never install something I don't know.

I'm sure I will discover something else I am having trouble with, and I will see you again sometime!

Thanks!

---

### Post by Bahlman on 2010-02-06
Whoops, uno mas something.
I want to install the Steam Client so I can chat to my friends, not play games (I don't know how well that'll work on Linux).

I download the files and it says "open with..."
What do I open that with?

Edit: it's an .msi file

---

### Post by pirateghost on 2010-02-06
i dont know if this page is still relevant or not:
[https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam)

---

### Post by mushwars on 2010-02-06
steam itself works PERFECTLY in wine, just dont try to start the games. for that you need P[s]G[/s]OL (play [s]games[/s] on linux)

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by Paqman on 2010-02-06
> **Bahlman said:**
> 
I download the files and it says "open with..."
What do I open that with?


You need to install Wine first. It's a compatibility layer that lets Windows apps run (well, sort of run...) on Linux. You can get Wine from Software Centre or Synaptic.

After that, Wine should open .msi and .exe's automatically.

---

### Post by theozzlives on 2010-02-06
I went back to Jaunty so I'm not 100% sure but I think you have a drop down box in the Software Center where you can select "All Available Applications". You want to choose that. And be sure to install ubuntu-restricted-extras as posted above.

---

### Post by admiralspark on 2010-02-06
> **theozzlives said:**
> I went back to Jaunty so I'm not 100% sure but I think you have a drop down box in the Software Center where you can select "All Available Applications". You want to choose that. And be sure to install ubuntu-restricted-extras as posted above.


For a second there, I thought you meant to have him/her download all 20,000 applications...
It's not a drop-down box in 9.10; go to View-->All Applications for what he was talking about. Then, you can simply search "restricted" and find what you're looking for.

Welcome!

---

### Post by Bahlman on 2010-02-07
I already installed restricted extras and I am installing Wine as we speak. 
Once again, I don't want toslashdont think my computer can handle games. That's why I have this behemoth of a computer (It was Windows 7 on it, I am sorry...) But I will check out how Steam works and whatnot and get back to you guys.

Thanks again for helping me out!

---

### Post by Bahlman on 2010-02-07
Why doesn't it work!!!!

---

### Post by Bahlman on 2010-02-07
bump!

---

### Post by Merk42 on 2010-02-07
> **Bahlman said:**
> bump!

Do you have Windows installed on a different partition? If not, that's why that step doesn't work, if you do have it installed then you're not pointing to the correct partition.

Also check the [WINE Application Database](http://appdb.winehq.org/) to get a rough idea how well a game will work in WINE

---

### Post by Bahlman on 2010-02-07
> **Merk42 said:**
> Do you have Windows installed on a different partition? If not, that's why that step doesn't work, if you do have it installed then you're not pointing to the correct partition.

Also check the [WINE Application Database]("http://appdb.winehq.org/") to get a rough idea how well a game will work in WINE

Oh, ok. Yeah, I do not have Windows installed. Do I still need this font?

---

### Post by Bahlman on 2010-02-07
I've downloaded the files and tried a BILLION different commands to copy it to that directory. Is there a way I can open the last file in the path "~/.wine/drive_c/windows/fonts/" so I can just drag and drop the file?

I can't figure out how to get there through the file browser...

---

### Post by Bahlman on 2010-02-10
So I got it working and installed, I launched it (it took awhile) but it worked.

I opened my friends list, I moved it, and it just disappeared. Any idea what happened to it?

---

