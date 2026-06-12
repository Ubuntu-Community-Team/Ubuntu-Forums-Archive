---
title: "sudo apt-get install envy DOESN'T WORK"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by p.schaerer on 2011-09-07
Hi everybody,
I tried to do 
sudo apt-get install envy
(because I need a quick way to get installed a proper video driver)
but I get
E: Package envy cannot be found (in German)

What could be the reason? 
- I have a newly installed German Ubuntu 11.04
- I have made sure that in the the sofware package sources main and universe are checked.
- I have an active internet connection.

---

### Post by saltmarshlamb on 2011-09-07
Envy is old - up to ubuntu 9.10 - what are you trying to do?

---

### Post by dodo3773 on 2011-09-07
[s]Is it "envyng-core" now? I think it was in Lucid. Did you search for envy and see what shows up?[/s] I prefer aptitude to search for packages as opposed to apt-get (aptitude search envy).


I do not think that this software is supported any more. Are you having a hard time finding out what your graphics card is?

---

### Post by gandaran on 2011-09-07
> **p.schaerer said:**
> Hi everybody,
I tried to do 
sudo apt-get install envy
(because I need a quick way to get installed a proper video driver)
but I get
E: Package envy cannot be found (in German)

What could be the reason? 
- I have a newly installed German Ubuntu 11.04
- I have made sure that in the the sofware package sources main and universe are checked.
- I have an active internet connection.
what brand video card do you have?
the proper way to install drivers in 11.04 is using additional drivers but only works for ATI and Nvidea cards.

---

### Post by saltmarshlamb on 2011-09-07
I searched wit apt and the ubuntu package search.

[http://packages.ubuntu.com/search?keywords=envy&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=envy&suite=default&section=all&arch=any&searchon=names)

It shouldn't be needed now though from memory, I know I've not used it for a few years.

---

### Post by Mark Phelps on 2011-09-07
The author of envy dropped support for it years ago.  Even if you do find it, it probably won't work now.

If you don't know the make and model video card, open a terminal and enter "lspci".  Look for the line containing "VGA" and post the results back here.

---

### Post by Frogs Hair on 2011-09-07
When I search Envy in the 11.04 software center ,  the result comes up as alsa-tools-gui  . If  this is the the package you are looking for it is still supported .

---

### Post by anewguy on 2011-09-07
Please, just do as Mark Phelps requested!  This will tell us what video adapter chipset you are using, and that's the only way anyone can ever give you valid advice on the driver to use.

Dave ;)

---

### Post by dodo3773 on 2011-09-07
@Frogs Hair      The envy program we are talking about is an obsolete script for installing graphics drivers. 

Please use Mark Phelps advice. Using grep may be easier:
```

lspci | grep VGA

```

The only two cards that are supported in envy / envyng are nvidia and ati anyways. The drivers should be in the repos already.

---

### Post by p.schaerer on 2011-09-12
Thanks for helping. lspci give me this information: 
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
Sorry, I don't know what I have to do in order to install a driver manually.

---

### Post by p.schaerer on 2011-09-12
The best thing I could find at the Ati web page was ati-driver-installer-9-3-x86.x86_64.run. I tried to do 
sudo sh ati-driver-... and it was working... However at the end I got
Error: ./default_policy.sh does not support version
default:v2:9686:lib::none:2.6.38-11-generic; make sure that the version is being correctly set by --iscurrentdistro. 
What now?

---

### Post by p.schaerer on 2011-09-12
I found a driver on the ATI Webpage, but got after installing: Error: ./default_policy.sh does not support version
default:vw2:i686:lib::none:2.6.38-ll-generic; make sure that the version is being correctly set by --iscurrentdistro
What now?

---

### Post by Mark Phelps on 2011-09-12
Well see, if you had told us what make/model video card you had at first, we could have saved you a lot of trouble -- because there is NO ATI driver you can download that will work with your card and recent versions of Ubuntu (newer than 8.10).

ATI dropped Linux restricted driver support for your card years ago and the only driver that works now is the open-source driver -- and THAT is installed by default when you setup Ubuntu.

Don't go trying to force the install of any other driver.  Not only will the driver trash your display, you will then  have to go to a lot of work removing it to reinstall the same driver you already have in place now.

---

### Post by Frogs Hair on 2011-09-12
> **dodo3773 said:**
> @Frogs Hair      The envy program we are talking about is an obsolete script for installing graphics drivers. 

Please use Mark Phelps advice. Using grep may be easier:
```

lspci | grep VGA

```

The only two cards that are supported in envy / envyng are nvidia and ati anyways. The drivers should be in the repos already.

Thank you , I found it later and their are no updates after 9.10 .:oops:

---

### Post by p.schaerer on 2011-09-13
> **Mark Phelps said:**
> Well see, if you had told us what make/model video card you had at first, we could have saved you a lot of trouble -- because there is NO ATI driver you can download that will work with your card and recent versions of Ubuntu (newer than 8.10).

ATI dropped Linux restricted driver support for your card years ago and the only driver that works now is the open-source driver -- and THAT is installed by default when you setup Ubuntu.

Don't go trying to force the install of any other driver.  Not only will the driver trash your display, you will then  have to go to a lot of work removing it to reinstall the same driver you already have in place now.
Ok, I'll obey. Well the present state seems not to be worse than before - anyway something I cannot use. They only choice for resolution ist 1280 x 1024 which I definitly cannot use, I need my 1600 as it is a development machine. So does your unfortunate message mean that I have either to decide for another laptop or for another operating system and return to Windows :-( ? (I actually installed ubuntu at this machine underneath because I wanted to save memory; anyway I need to run a VM with Win7 on top)

---

### Post by F W Adams on 2012-06-12
I have a very similar problem.

My card, lspci gives
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV630 [Radeon HD 2600XT]

In 2009 the only way I managed to get a driver to install properly for this card was by using envyNG. Recently, with a newer ubuntu 12.04, I have exactly the same problem. The appropriate AMD/ATI driver failed to install correctly, The official ububtu one didn't work either. Both messed up the dual monitor function in addition.

Any advice gratefully received, especially if it works.

---

### Post by Mark Phelps on 2012-06-13
Your problem is very different -- please don't hijack an old thread with a different problem.

Envy support was dropped a long time ago.

Please start a new thread in the Video forum section about your problem.

thanks

---

