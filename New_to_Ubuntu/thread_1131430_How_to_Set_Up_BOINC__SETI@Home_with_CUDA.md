---
title: "How to Set Up BOINC / SETI@Home with CUDA"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-20
If you have a fast CPU and / or a fast nvidia GPU in your graphics card, you may like to lend the awesome power of your computer to help find aliens!

SETI@home and other projects can use your processors whilst they would otherwise be relatively idle.

THE EASY WAY (But it doesn´t let your GPU  do processing)

The easiest way to get this going is in a terminal:

```
sudo apt-get install boinc-manager boinc-client boinc-app-seti
```

or by using Synaptic:

> System - Administration - Synaptic Package manager

Then in Quick Search look for:
> BOINC

Right click the following packages for installation:

boinc-manager boinc-client boinc-app-seti

++++++++++++++++++++++++++++++++++++++++++++++++++++++++

That will get BOINC installed. Launch it from Applications System Tools and follow instructions.

Unfortunately, to get your GPU working when it is idle, newer packages need to be installed. Not all GPUs are supported. Supported GPUs are listed [here]("http://www.nvidia.com/object/cuda_learn_products.html"). 


++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

THE COOL WAY (Your CPU and GPU will be using their awesome power!)

This is cool, but the files are bleeding edge and some features may not work properly on your machine, however, you will be cool and aweome :) 

You will need recent nvidia drivers running on your system:
tinivole has a great [howto]("http://ubuntuforums.org/showthread.php?t=1125400") showing the way to get these drivers running.

Get the nvidia drivers going, then...

Download and install the BOINC Manager:

Go to the Debian site [here]("http://packages.debian.org/sid/boinc-manager") and download the file appropriate for your architecture from the Download boinc-manager table.

Do this by right clicking on the architecture name and saving the file.

Once the file has downloaded, you can merrily double click it and package manager should install it. A BOINC folder will appear.

Download the BOINC Client:

Go [here]("http://packages.debian.org/sid/boinc-client") and select the appropriate file for your architecture.

Right click the file and save it to the newly created BOINC folder.

You are nearly in the space age! :D

At the top of your desktop, click on places and choose home and then navigate to the BOINC folder. Inside you should be able to see boincmgr.

Double click boincmgr

Hopefully this will launch your GPU enabled search for little green men! ):P

Congratulations :) \\:D/



If you would like sensible words on how to get it all going, try here or [here]("http://www.spy-hill.net/~myers/help/boinc/unix.html").

---

### Post by Paqman on 2009-08-29
> **yeehi said:**
> 
THE EASY WAY (But it doesn´t let your GPU  do processing)

The easiest way to get this going is in a terminal:

```
sudo apt-get install boinc-manager boinc-client boinc-app-seti
```

or by using Synaptic:


FYI, the CUDA-capable version of BOINC (6.4.5) will be in the repos for Karmic. So once you update/reinstall in October, you'll be automatically using CUDA if your GPU is supported.

---

### Post by MC707 on 2009-09-30
> **Paqman said:**
> FYI, the CUDA-capable version of BOINC (6.4.5) will be in the repos for Karmic. So once you update/reinstall in October, you'll be automatically using CUDA if your GPU is supported.

Holy mother.... that's the best news I've heard since... I don't even remember!! Thanks for the heads up, I'm HATING to have my GPU idle in Linux (worked like a charm back when I used MS Windows regularly) BTW, do you know if the newest and latest nvidia/ati drivers will be available in Karmic? The last time I tried to install the nvidia drivers manually, my xserver ****ed up *sigh*. [-(

---

### Post by miha72 on 2009-11-22
How do I get libcudart on karmic koala?
It was in none of the driver packages from the repository. 
I can find libcuda, libicudata, but no libcudart.
Maybe I am not the only one, but I would like to have a working system with updates. Because of that I would like to use packages not the driver from nvidia site. It is not excluded way but I would like to go the official ubuntu path first.

---

### Post by mercury80 on 2009-11-30
> **Paqman said:**
> FYI, the CUDA-capable version of BOINC (6.4.5) will be in the repos for Karmic. So once you update/reinstall in October, you'll be automatically using CUDA if your GPU is supported.

I've just installed Karmic on a new PC with cuda ready nVidia card. For what reason does it not work? I have not installed anything extra than the proprietary drivers from nVidia. Not quite sure what "reports" i should post for anyone to know why, but here is what i can think of:
* Ubuntu 64bit Karmic
* nVidia card: GeForce 9500 GT
* Vbios: 62.94.29.00.50
* Memory: 1 GB
* nVidia driver version: 185.18.36
* X server info:[INDENT]Server Version: 11.0
Vendor version: 1.6.4
NV control version: 1.18[/INDENT]* Prosessor: Intel quad core.
* RAM: 4 GB

---

### Post by XCan on 2009-11-30
What does the message window say? If it detects your card it should say something like "Cuda supported device enabled". Also, you may need to add whichever user that runs boinc to the group "video". Last, which project are you trying to run? Some of the projects require certain versions of the driver and also a rather new version of boinc.

---

### Post by mercury80 on 2009-12-01
> **XCan said:**
> What does the message window say? If it detects your card it should say something like "Cuda supported device enabled". Also, you may need to add whichever user that runs boinc to the group "video". Last, which project are you trying to run? Some of the projects require certain versions of the driver and also a rather new version of boinc.

Messages of interest from boinc:
* Can't load libcudart
* No coprocessors

A search for cuda (or libcuda...) in synaptic yields no results. Should i add a repo of some sort? I only have medibuntu & canonical. I don't really want to download any drivers outside synaptic either...

adding my username to the group "video" did not change anything. (should i change it back or leave it like that?)

I am trying to run GPUgrid. (i am aware my graphics card is not really fast enough but i was keen on trying it out (with my quad core), and at least making cuda available)

---

### Post by NoonienSoong97 on 2009-12-10
Hi,

I noticed that no one has updated boinc in the repositories for sometime. I tried downloading the package directly from berkley. It is in .sh format. I am trying to figure out what program uses .sh.

Also I came across packages at the debian package site. As far as I know I can use the packages at the debian package site since ubuntu came from debian. I just want to be sure about that before I do download from debian.

Thanks

---

### Post by rbroom on 2010-04-03
Noonien,  .sh files are shell scripts.  Open a shell in the folder where the file is, and make the script executable with ```
chmod +x filename.sh
``` Then you can run it by typing ```
./filename.sh
```

Hope that helps.

---

