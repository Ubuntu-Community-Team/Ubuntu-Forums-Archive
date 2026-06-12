---
title: "Desktop effects could not be enabled."
date: 2009-02-20
forum: New to Ubuntu
---

### Post by diwas on 2009-02-20
My system config is in my signature. I have compiz-core installed and Xorg is not modified. Almost every effects could be enabled in 8.04 but not here(8.10). I am not a huge fan of compiz, but just curious abt why is this happening. 

Thank you.

---

### Post by overdrank on 2009-02-20
> **diwas said:**
> My system config is in my signature. I have compiz-core installed and Xorg is not modified. Almost every effects could be enabled in 8.04 but not here(8.10). I am not a huge fan of compiz, but just curious abt why is this happening. 

Thank you.

Hi and what is the model of the integrated graphics?
Have you tried [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070") ?

---

### Post by diwas on 2009-02-21
Hmm I havnt Im afraid, but compiz worked well in Ubuntu 8.04, simply not in 8.10. 

I dont know. The board is D845GVSR...thats all i know. It is Intel thats for sure hehe.

---

### Post by JerichoKru on 2009-02-21
> **diwas said:**
> Hmm I havnt Im afraid, but compiz worked well in Ubuntu 8.04, simply not in 8.10. 

I dont know. The board is D845GVSR...thats all i know. It is Intel thats for sure hehe.

Board has an Intel 845GV chipset with "Intel Extreme Graphics"

You do have the Intel driver package installed and enabled, correct?

---

### Post by diwas on 2009-02-22
> **JerichoKru said:**
> Board has an Intel 845GV chipset with "Intel Extreme Graphics"

You do have the Intel driver package installed and enabled, correct?
Isnt it enabled by default? I know 8.04 did.

---

### Post by osopotusi on 2009-03-02
am having the same problem i tried compiz and got this,

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) 

I've download the driver from the intel website for linux but am unable to install it, is on some sort off rpm format, i alos look into this,

alexander@alexander-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
alexander@alexander-desktop:~$ cat /etc/X11/xorg.conf | grep Driver
	Driver		"vesa"
alexander@alexander-desktop:~$ my resolution is fine everything looks okay. I just can't seem to be able to enable effects i guess do to the graphics card driver, my motherboard is d845gvsr like the guy above me, please advise on how to get the driver to install properly enable and checked in order to be able to use visual effects. Thanks

---

### Post by sandyd on 2009-03-02
> **osopotusi said:**
> am having the same problem i tried compiz and got this,

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) 

I've download the driver from the intel website for linux but am unable to install it, is on some sort off rpm format, i alos look into this,

alexander@alexander-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
alexander@alexander-desktop:~$ cat /etc/X11/xorg.conf | grep Driver
    Driver        "vesa"
alexander@alexander-desktop:~$ my resolution is fine everything looks okay. I just can't seem to be able to enable effects i guess do to the graphics card driver, my motherboard is d845gvsr like the guy above me, please advise on how to get the driver to install properly enable and checked in order to be able to use visual effects. Thanks


this could be dangerous but try this

save the rpm to desktop and run this.....

```

sudo apt-get install alien
alien -d filename.rpm
sudo dpkg -i *.deb

```

That should get you your deb

---

### Post by osopotusi on 2009-03-02
hey thanks for replying so quick i appreciated am gonna try it right now, a'l post back my results.

---

### Post by osopotusi on 2009-03-02
okay it didn't take very long, finally it extracted the files and now i have the folder contain the drivers.? is how do i install them, it may sound like dumb question but am just getting started here so please have mercy on me.

---

### Post by Vantrax on 2009-03-02
that command should have given you a file called filename**.deb**

Just double click on the deb file and it should come up with a window with an install button.

---

### Post by osopotusi on 2009-03-02
it extracted alot files I've being going tru them but i can't seem to find one with the deb extension, could someone upload the executable driver to make matters easier if this isn't to much to ask, thanks.

---

### Post by osopotusi on 2009-03-09
updated! i switch over to kubuntu 8.04.2 everything is running just fine. I've notice that kubuntu seems to run a little slower, compare to ubuntu 8.10 but not by much, 3d rendering is working great i didn't have screw around much with intel drivers all i did was install i new version of compiz and bamm everything work with minor tweaks, it would be cool if kubuntu had a build in weather widget,i know i can install plasoid i think is call am not to sure but, i know that ubuntu 8.10 had the weather widget build in. I hope that some day they come with an intel driver for ubuntu 8.10 for the motherboard which is mention here >D845gvsr, i know is said that theres one out there right now but i don't think thers is

---

### Post by diwas on 2009-03-10
Kubuntu has intel drivers u mean?

---

### Post by High Camp on 2009-03-10
Hi

In case anyone else is looking for help on this. On my other puter, which is a laptop with a nvidia card, I had to download the nvidia linux proprietary driver, kill the wm, then install the driver via command line, then reboot. By the sounds of it the op here may have had the same problem. 

Happy to provide more information if required.

---

### Post by diwas on 2009-03-10
The problem is actually there's no driver available for my internal graphics chip. I have Intel Extreme Graphics chip not NVIDIA.
But, thank you for your help!

---

### Post by bailbath on 2009-03-10
You maybe better sticking to 8.04 until the intel graphics module has caught up with 8.10. 
Sometimes it's better to stick with something that works for your main machine or do as I do and dual boot the 8.04 long term support and the latest development ubuntu. Then you will always have a stable version for all important work and a less stable version for messing around with. Plus you will be able to feedback any bugs to the Ubuntu developers to solve. It's a win win situation! 
All the best
Ian

---

### Post by diwas on 2009-03-10
> **bailbath said:**
> You maybe better sticking to 8.04 until the intel graphics module has caught up with 8.10. 
Sometimes it's better to stick with something that works for your main machine or do as I do and dual boot the 8.04 long term support and the latest development ubuntu. Then you will always have a stable version for all important work and a less stable version for messing around with. Plus you will be able to feedback any bugs to the Ubuntu developers to solve. It's a win win situation! 
All the best
Ian
Probably you are right.
But well, I think i had seen my driver's software somewhere in the Intel's website, but its not there now. 
And again, I am not a big fan of compiz and all decorations, i was just curious why wudnt it be enabled thats it. If it works though, it would be sweet ;)

---

### Post by abn91c on 2009-03-10
intel 845 video and compiz will not work in ubuntu/kubuntu 8.10 due to a known bug in the driver, the only wokraround is to disable desktop effects or removing compiz. see this post #26
[http://ubuntuforums.org/showthread.php?t=966436&page=3](http://ubuntuforums.org/showthread.php?t=966436&page=3)

---

### Post by diwas on 2009-03-10
> **abn91c said:**
> intel 845 video and compiz will not work in ubuntu/kubuntu 8.10 due to a known bug in the driver, the only wokraround is to disable desktop effects or removing compiz. see this post #26
[http://ubuntuforums.org/showthread.php?t=966436&page=3](http://ubuntuforums.org/showthread.php?t=966436&page=3)
:D
Got it, thank you.
Is there any chance that this bug will be fixed in 9.04? :s

---

### Post by abn91c on 2009-03-10
> **diwas said:**
> :D
Got it, thank you.
Is there any chance that this bug will be fixed in 9.04? :s
don't thing so, but check the jaunty posts to be sure

---

### Post by diwas on 2009-03-10
Oh thats bad :(
No compiz for me then..:(

---

### Post by osopotusi on 2009-03-10
well let me put it to you this way, you don't even need to load such driver as for the operating system will automatically do it for you, it did for me anyways, ones the operating system was install. I went on to install the latest compiz,till date everything is running just fine 3d rendering works fine the cube roates left,right top and bottom.I still have to do some more tweaking to get everything running to mi liking but really everything is running just fine no major driver here and there crap, i personally like ubuntu 8.10 it seems to boot faster i think i don't know if anyone and here could chime in and further say more, but this is what i have notice also the what am looking into here now is a weather widget to run I've come across several am thinking of going with plasmoid.

> **diwas said:**
> Kubuntu has intel drivers u mean?

---

### Post by diwas on 2009-03-10
I did just that, installed the latest compiz, but still no progress. The effects could not be enabled.

---

### Post by osopotusi on 2009-03-10
what are you running kubuntu or ubuntu? cuz am referring to kubuntu.


> **diwas said:**
> I did just that, installed the latest compiz, but still no progress. The effects could not be enabled.

---

### Post by diwas on 2009-03-11
Ubuntu here.
My bad! Sorry.

---

### Post by sdowney717 on 2009-03-24
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833/comments/8](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833/comments/8)

try this, it has worked for others

[http://ubuntuforums.org/showthread.php?t=965846&highlight=82845G+video](http://ubuntuforums.org/showthread.php?t=965846&highlight=82845G+video)

---

### Post by diwas on 2009-03-24
Thank you..i will try it ASAP

---

