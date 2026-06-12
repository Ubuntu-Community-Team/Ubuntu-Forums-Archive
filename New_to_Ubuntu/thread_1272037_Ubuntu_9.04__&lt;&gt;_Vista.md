---
title: "Ubuntu 9.04  &lt;&gt; Vista?"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by IamGibby on 2009-09-21
It seems my Fans run more and produce more heat on my tx2 in Ubuntu Compared to Vista... (Yes this is a tablet, but I'm using it in standard laptop mode, which in Vista I have  a ~1-5% CPU usage and seems to have no Fan activity (very seldom) and no heat... where as Ubuntu it seems my fans are always on and they always seem hot (atleast hotter then vista)....

Is this the Norm?

---

### Post by blur xc on 2009-09-21
What are you doing while this is happening?  Does it do this on a fresh boot w/ nothing running?  I'm not expert, but from what I've gathered both from the forums and my own experience, FF + flash + linux (I'm guessing any distro?) = high cpu usage and consequently extra fan operation...

BM

---

### Post by scorp123 on 2009-09-21
> **IamGibby said:**
> Is this the Norm? Not really. But some laptop makers don't fully adhere to standards such as ACPI and what not (the stuff that should regulate power-saving measures and so on) and it could therefore be that Ubuntu doesn't work properly with your specific model of tablet PC.

I'd recommend you Google around ... maybe someone posted instructions in a blog or in another thread here on how to get ACPI properly working with Ubuntu.

Another thing: Are you running 3D desktop effects? Those can cause a lot of heat too. What happens if you turn all effects off? Does it make a difference?

---

### Post by scorp123 on 2009-09-21
> **blur xc said:**
>  FF + flash + linux (I'm guessing any distro?) =  True. That too might be a reason. Firefox sometimes consumes more CPU and RAM than you would want to believe (hence why many people switch to leaner browsers such as Opera ... )

---

### Post by sandyd on 2009-09-21
what version of firefox and xorg are you using?
could be the old 100% CPU firefox+xorg issue.

---

### Post by blackmail on 2009-09-21
In my small experience using vista on a laptop, well you should know that it eats a lot of RAM, ann Ubuntu consumes the resources very carefully, at least that is my experience in using ubuntu, on many PCs, and on 3 laptops. The main trick is the vay you have it configured, and the number of programs running.

---

### Post by lukeiamyourfather on 2009-09-21
I've found that Linux in general (Debian, Ubuntu, and Fedora) has a shorter battery runtime on my ThinkPad X61 compared to the factory Vista install. My guess is the drivers and software that originally come on the system have power optimizations that might not be implemented in the Linux drivers.

---

### Post by rmb938 on 2009-09-21
if vista cam pre-installed it is usually optimized to work with your pc/laptop hardware. If you install any OS that didn't come with the computer it self it wont be as optimized so you will run into issues like you have.

---

### Post by LowSky on 2009-09-21
> **rmb938 said:**
> if vista cam pre-installed it is usually optimized to work with your pc/laptop hardware. If you install any OS that didn't come with the computer it self it wont be as optimized so you will run into issues like you have.

Not exactly true. My netbook came with Windows XP, it gets about 2.2hrs on XP, 1.8hrs on Ubuntu, and 2.7 hours on Windows 7 RC...
dont go around spreading lies. In all honestly its about driver support and how those operating systems use said drivers... Windows 7 has made my netbook work for longer than any other OS I have used.

---

### Post by IamGibby on 2009-09-21
Yea I have the original FF installed from Jaunty... I can't figure out the upgrade process for 3.5 or whatever, I've tried a few different Mozilla returns in the package manager... Both instances I explained (the vista vs Ubuntu) are at  Firefox and maybe a terminal in ubuntu.

(My firefox is optimized on vista so it gets alot better CPU/Memory usage)

---

### Post by scorp123 on 2009-09-22
> **lukeiamyourfather said:**
> I've found that Linux in general (Debian, Ubuntu, and Fedora) has a shorter battery runtime on my ThinkPad X61 Well, you might want to take a look at powertop ....
```
sudo apt-get install powertop cpufrequtils
```

Then open a terminal and let it analyse your laptop's power consumption:
```
sudo powertop
```

It will then auto-suggest measures that will in some cases drastically reduce power consumption. And if you Google around there are plenty of threads out there where gurus explain how to make those power optimisations permanent. (Yes: the changes "powertop" applies to your system are normally only temporary ... which is good. In case anything goes wrong, simply reboot ...)

With "powertop" I am able to squeeze out an additional hour of battery runtime out of my laptops.

One piece of advice though: If you decide to make some changes permanent -- please make notes. Just in case something doesn't work properly you will then be able to revert the change if ever necessary. A typical candidate would be the CD auto-play feature. If permanently turned off (via manipulating the "hald-storage" background process and its config files ...) you get to save power ... but then again CD's and DVD's won't show up automatically anymore when you insert them. For me that is no problem; I will simply mount the CD by hand like in the old days before people knew what "auto-play" is. But for others this might be a problem ...

Hence: If you make changes permanent ... take notes. Just in case.

Powertop infos & threads:
[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)
[http://www.lesswatts.org/projects/powertop/known.php](http://www.lesswatts.org/projects/powertop/known.php)

HOWTO: Improve battery life on a laptop
[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

---

