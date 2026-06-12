---
title: "Graphics and google earth"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-09-04
I have tried all the fixes to get google earth working with no luck. I am wondering if I need a graphic driver update. I am attaching a screenshot of the info I could pull on my machine. If anyone knows how to fix this or update it please answer

---

### Post by fooman on 2011-09-04
is it already installed?  if yes,  what exactly happens when you try to run it?

try running it from a terminal to see what errors get spit out.  open a terminal and run:

```
googleearth
```

post back with any errors that you see.

---

### Post by alegomaster on 2011-09-04
I remember that Intel Graphics are sometimes finicky with which applications you choose. Like for example, minecraft can't work on systems with Intel graphics, but it works great with every other vendors GPU's. If the command above does not provide useful information, then try to use a different gpu.

---

### Post by cmcanulty on 2011-09-05
As I said I've done lots of searches and install fixes for google earth but it opens to the splash screen and crashes immediately.This is a known bug in 10.10 but I need a fix. It worked fine in 10.04. The other graphics issue is when I right click a link in firefox  about half the time I get cascading pages opening like a hundred or so and I then left click and they disappear.

---

### Post by Paddy Landau on 2011-09-05
It sounds as though you have two problems: graphics, and Google Earth.

I'd recommend you first open a new thread to deal with your graphics problem.

Once that is done, retry Google Earth. Unfortunately, Google Earth is a finicky program. You don't say how you installed it. If you installed from the repository, try doing this:

[LIST=1]
[*]Completely uninstall Google Earth.
[*][FONT=Courier New]sudo apt-get install googleearth-package[/FONT]
[*][FONT=Courier New]make-googleearth-package --force[/FONT]
[*]Double-click on the resulting .deb file -- if I remember correctly, it lands on your Desktop -- and follow the instructions. (Once installed, you can delete the .deb file.)
[/LIST]

---

### Post by cmcanulty on 2011-09-05
I have probaly installed it like 50 times trying new things each time always crashes after splash screen for a second or less.

---

### Post by Paddy Landau on 2011-09-05
> **cmcanulty said:**
> I have probaly installed it like 50 times trying new things each time always crashes after splash screen for a second or less.
As I say, start a new thread to get your graphics working first. Google Earth, unfortunately, is excruciatingly sensitive to graphics problems.

---

### Post by cmcanulty on 2011-09-05
OK everything else works OK though, youtube, pictures etc

---

### Post by alphacrucis2 on 2011-09-05
> **cmcanulty said:**
> OK everything else works OK though, youtube, pictures etc


As already said run it from a terminal window and report back with the output.

---

### Post by cmcanulty on 2011-09-05
Here it is I have searched synaptic but no Xlib GLX is listed I tried installing libxcb-glxo but that didn't help.I don't know how to fix, thank you
```
cmcanulty@HP:~$ googleearth
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/cmcanulty/.googleearth/crashlogs/crashlog-4e654c66.txt

Please include this file if you submit a bug report to Google.
cmcanulty@HP:~$ 
```

---

### Post by alphacrucis2 on 2011-09-05
What is output of:

```
glxinfo | grep render
```

---

### Post by beew on 2011-09-05
> **cmcanulty said:**
> As I said I've done lots of searches and install fixes for google earth but it opens to the splash screen and crashes immediately.This is a known bug in 10.10 but I need a fix. It worked fine in 10.04. The other graphics issue is when I right click a link in firefox  about half the time I get cascading pages opening like a hundred or so and I then left click and they disappear.

That was a known bug in a very old version of GE that was fixed long ago, I have been running GE6 flawlessly on Ubuntu10.10 and 11.04 for quite sometimes now. What version of GE are you running?

---

### Post by beew on 2011-09-05
> **Paddy Landau said:**
> It sounds as though you have two problems: graphics, and Google Earth.

I'd recommend you first open a new thread to deal with your graphics problem.

Once that is done, retry Google Earth. Unfortunately, Google Earth is a finicky program. You don't say how you installed it. If you installed from the repository, try doing this:

[LIST=1]
[*]Completely uninstall Google Earth.
[*][FONT=Courier New]sudo apt-get install googleearth-package[/FONT]
[*][FONT=Courier New]make-googleearth-package --force[/FONT]
[*]Double-click on the resulting .deb file -- if I remember correctly, it lands on your Desktop -- and follow the instructions. (Once installed, you can delete the .deb file.)
[/LIST]


Actually the .deb file from GE works just fine. 
[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

Need to install lsb-core first though.

---

### Post by alphacrucis2 on 2011-09-05
> **beew said:**
> Actually the .deb file from GE works just fine. 
[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

Need to install lsb-core first though.

Yep. I had trouble with it until I installed via the google provided deb file.

---

### Post by cmcanulty on 2011-09-06
```
cmcanulty@HP:~$ glxinfo | grep render
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
cmcanulty@HP:~$ 

```

---

### Post by cmcanulty on 2011-09-06
Here is a screenshot and I do have lsb-core installed. I run 8 Ubuntu machines at our library and people want google earth my home computer needs it also . All are new this winter HP G72 laptops with 4 GB RAM. OK I reinstalled from the posted deb file and now I get this
```
cmcanulty@HP:~$ googleearth
googleearth: command not found
cmcanulty@HP:~$
```

---

### Post by MrSpike16 on 2011-09-06
The .deb you downloaded installed into a different location.  I have the same .deb installed so try:

```
/opt/google/earth/free/googleearth
```

The installer put a menu entry in Applications > Internet on mine.

---

### Post by cmcanulty on 2011-09-06
Same crash issue 
```
cmcanulty@HP:~$ /opt/google/earth/free/googleearth
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/cmcanulty/.googleearth/crashlogs/crashlog-4e664725.txt

Please include this file if you submit a bug report to Google.
cmcanulty@HP:~$ 

```

---

### Post by MrSpike16 on 2011-09-06
The glxinfo command shows that you have a video driver issue involving opengl.  There is a issue with having Intel Integrated Graphics and libraries being used from Nvidia modules.

I searched and found this: [https://theiszm.wordpress.com/2010/06/27/glx-missing-on-display/](https://theiszm.wordpress.com/2010/06/27/glx-missing-on-display/)

These instructions remove the Nvidia stuff.

Search for Nvidia in Synaptic Package Manager to see if you have any modules installed for starts.

Warning: I don't know what Intel chipset your computers are using, and messing with video can cause a crash and a blinking cursor on reboot. 

I don't know your experience level, but this is in Absolute Beginner Talk, and I don't want you to get over your head.  Know how to get to desktop from Grub menu recovery mode etc, do a purge and reinstall of packages etc... 

At the very least, hopefully this will get you started on a solution.

---

### Post by cmcanulty on 2011-09-06
I have sysinfo installed but all it shows for graphics is in the screenshot on my 1st post. How can I get exact graphics info, thanks
Before I remove the nvidia stuff is there anyway to go back if it turns my machine black or unusable?
Here are screenshots of the synaptic search for nvidia I covered everything that was installed under nvidia in the screenshots. I just want to be sure removing them all is OK and should I install some other driver? Thanks all

---

### Post by migs73 on 2011-09-06
To find out what graphics card you have type this into terminal;

```
lspci
```

It'll list all hardware on your PCI bus including 'VGA compatible controller' which is your graphics card.

---

### Post by MrSpike16 on 2011-09-06
You can find the computer's specifications from your Brand's site and from the manual if all else fails.
From Post #16 >  I run 8 Ubuntu machines at our library and people want google earth my  home computer needs it also . All are new this winter HP G72 laptops  with 4 GB RAM  

The HP G72 manual states that the chipset is the H55 Express.  Assuming that the computer (your home?) in this thread that you are trying to get Google earth to run in is the same then:

  A quick Google search using h55 Xlib:  extension "GLX" missing on display ":0.0".
shows that the instructions I linked to previously did work for the H55 chipset and many others.  You may not need the steps involving Nvidia but doesn't hurt as long as you don't have a Nvidia graphics card or chip.

---

### Post by alphacrucis2 on 2011-09-07
To get graphics hardware and driver info:

```
sudo lshw -C display
```

---

### Post by cmcanulty on 2011-09-07
OK Thanks here's what it gives
```
cmcanulty@HP:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:b0000000-b03fffff memory:a0000000-afffffff ioport:3050(size=8)
cmcanulty@HP:~$ 

```

---

### Post by MrSpike16 on 2011-09-07
Still doesn't tell us the chipset model name. but the most important part is you are using Intel Integrated Graphics and the standard i915 driver.

My netbook doesn't have the "GLX" problem but uses Intel Integrated Graphics and the standard i915 driver but I tried the fix in the link I provided anyways.  There was no ill effects from doing this on my netbook.

I beleive that this fix will probably work for you and in a previous post I wanted you to realize that there is always a risk when running commands such as this.

Here is the commands from that site to be run in order (use copy and paste to Terminal) if you wish to try:

```
sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel  libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf
```

---

### Post by StephenWoods69 on 2011-09-07
My google earth crashed on start-up until I disabled tool-tips. 
This thread explains how [http://ubuntuforums.org/showthread.php?t=1594462](http://ubuntuforums.org/showthread.php?t=1594462)

---

### Post by cmcanulty on 2011-09-07
I tried the tooltips fix long ago no help, thanks anyway. I really need a fix as the library wants google earth on all their machines. If this helps here is a link to the specs page.[http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Screen+size&v1=Over+16.9&series_name=g7t_series&jumpid=in_R329_prodexp/hhoslp/psg/notebooks/Over_16.9/g7t_series]("http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Screen+size&v1=Over+16.9&series_name=g7t_series&jumpid=in_R329_prodexp/hhoslp/psg/notebooks/Over_16.9/g7t_series")

---

### Post by MrSpike16 on 2011-09-07
I have realized I have not been clear as to your problem and solution.  In the simplest terms your problem is a part of your video driver is broken, namely GLX.  With GLX broken your 3D (Opengl) video is broken, but 2D video like Youtube will still work.  All programs that require 3D like Google Earth will not work however.

First thing to try is to reinstall the video drivers and the commands I posted will do this for Intel Integrated Graphics.  People using this has gotten the GLX fixed and hence their various 3D programs working including Google Earth.

After reinstalling drivers, the desktop may need to be restarted before retrying Google Earth.  There are commands to do this but a log out then in again or a reboot does the trick.

I really can't help you further as my three desktop computers and others I have built for other people use Nvidia graphics so I have no real experience with the Intel drivers and issues.

If reinstalling Ubuntu or a back up image on one of the library laptops is not a big deal (in case something goes wrong) then try the fix I found if laptop uses the i915 driver.

---

### Post by cmcanulty on 2011-09-08
I guess I just need to know what driver mine uses but I don't know how to find that out.

---

### Post by MrSpike16 on 2011-09-08
If the outputs you posted from the commands that  alphacrucis2 gave you is not from a computer that was purchased along with the library computers, then you need to run the commands from a library computer and post them here.

I am talking about the glxinfo and lshw commands.

---

### Post by cmcanulty on 2011-09-08
All the computers are the same specs as I posted above. HP G72t 17" Laptop. I just had a thought. I have  desktop effects set to none. Could that be a problem?

---

### Post by MrSpike16 on 2011-09-08
I was a little confused because you posted a link to a HP G7t, thanks for clearing that up.

Desktop effects is just another 3D program (Compiz) so it will not work either, hopefully gracefully bailing out.

You are at a point where you need to reinstall the video drivers and the commands I posted for you is for your laptops and has successfully worked for the chipset you have.

Other than doing your own searching or posting your video (not Google Earth) problem in the Hardware & Laptops forum I really can't think of anything else to help you.

---

### Post by pqwoerituytrueiwoq on 2011-09-08
google earth requires the 32bit libraries for the gpu if that helps

---

### Post by cmcanulty on 2011-09-09
Do you have a package for the gpu 32 libs?

---

### Post by pqwoerituytrueiwoq on 2011-09-09
i had had a issue with google earth i as using the nvidia driver from there site i chose not to install the 32 bit compatible libraries and google earth crashed with exit code 11 till i reinstalled the driver and induced the 32bit libraries but you are using a Intel chip so search for lib32 in synaptic and see if anything stands out 
but based on a earlier post you made it looked like you need a driver update since it appeared to not have opengl (i could be wrong)

try this it will update the graphics driver
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get upgrade;
```this is normally used with nvidia cards but there is intel stuff in the ppa also as well as ati drivers

EDIT:
google earth was screwed up on my laptop
this fixed it
```
sudo rm -rf ~/.config/Google/
sudo rm -rf ~/.googleearth/
```

---

### Post by cmcanulty on 2011-09-10
Same result I will get back to this tomorrow too frustrated now. This and drivers issues for perifials is why more don't use Linux not the stupid fancy stuff that does nothing
```
cmcanulty@HP:~$ googleearth
googleearth: command not found
cmcanulty@HP:~$ google-earth
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/cmcanulty/.googleearth/crashlogs/crashlog-4e6b8b26.txt

Please include this file if you submit a bug report to Google.
cmcanulty@HP:~$ 

```

---

### Post by cmcanulty on 2011-09-10
Oh man I did above scripts and now my laptop is really dim, I hope it can be restored!

---

### Post by pqwoerituytrueiwoq on 2011-09-10
> **cmcanulty said:**
> Oh man I did above scripts and now my laptop is really dim, I hope it can be restored!
it is possible the dimed screen is your brightness setting (see power settings)
```
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness
```
if updateing the driver caused problems this will undo it
```
sudo apt-get install ppa-purge;sudo ppa-purge ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get upgrade;
```

---

### Post by cmcanulty on 2011-09-11
Whew thanks I undid it and restarted and now I can see the display as usual. Is it time to give up on google earth? This is a new laptop a few months old and I hate to lose google earth. It worked fine in 10.04.

---

### Post by waynefoutz on 2011-09-11
> **cmcanulty said:**
> Whew thanks I undid it and restarted and now I can see the display as usual. Is it time to give up on google earth? This is a new laptop a few months old and I hate to lose google earth. It worked fine in 10.04.

I've found that Google Earth is a finniky fella indeed. The drivers have to be just right or it won't run, or you'll see awful tearing in it. Sometimes you'll get an update and bang, it's broken for good. I had the same problem with the open source Radeon drivers on my old laptop. When you did a fresh install of 10.04, Google earth ran perfectly. After you pulled in all the updates, not at all. I'd say if it's that important to you, then I'd go back to 10.04. Since it's a long term release, it has a longer shelf life than 11.04 anyway. Or if you go to maps.google.com, you pretty much get 99% of Google Earth's functionality inside your browser running with Flash. 
I kind of skimmed through the thread ad I think you said you have an Intel card, which means you are using open source drivers, that's 99% of your problem, and not much you can do about it if that's what's in your laptop. Personally, if it were me, I go back to 10.04. It's far more stable, and supported until April 2013. The standard releases are more cutting edge, so problems like this are more commonplace.

---

### Post by pqwoerituytrueiwoq on 2011-09-11
i would file a bug report like google earth says to and use 10.04 (or try the 11.10 beta) and call it a day

---

### Post by cmcanulty on 2011-09-11
OK thanks. The trouble is I run 8 public laptops with 10.10 at our local library and people really want google earth. They are all the same specs as my laptop HP 17" G72t

---

### Post by MrSpike16 on 2011-09-11
If you haven't tried reinstalling the video drivers, then yes it is hopeless.

Once your drivers are fixed you will no longer see Xlib:  extension "GLX" missing on display ":0.0".

He has a problem with the 3D (GLX and OpenGL) drivers.  Something did not install properly.  First he needs to reinstall all the drivers and I posted the commands for him.
This has fixed the 3D video problem for others and got Google Earth, Compiz etc.. working.

I had a look at the X-swat packages for Intel and didn't see any packages for 3D so it didn't help.

Instead of trying Google Earth, try this demo/test program for testing the 3D
```
glxgears
```

If working, you will see a small 3D animation of three spinning gears.

If this doesn't work, try reinstalling the drivers, running one command at a time from top to bottom in my previous post.  Reboot the computer and try glxgears again.
If it now works then try Google Earth.

---

### Post by cmcanulty on 2011-09-11
```
cmcanulty@HP:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
cmcanulty@HP:~$ 

```
and I will also try the driver fix

---

### Post by cmcanulty on 2011-09-11
OK I searched for nvidia in synaptic and it shows the ones installed in the screenshots below. Is there any of them I need to leave installed?

---

### Post by MrSpike16 on 2011-09-11
A lot of Nvidia drivers sure got installed and none of it is necessary for Intel graphics. This  could be the reason your video is broken, it might be using a wrong library (file).

Only the packages starting with "Nvidia" are to be removed and is safe since you do not have Nvidia graphics.

Do not remove them through Synaptic, let the first command do this.  The * at the end will take care of this.

---

### Post by waynefoutz on 2011-09-11
> **cmcanulty said:**
> OK thanks. The trouble is I run 8 public laptops with 10.10 at our local library and people really want google earth. They are all the same specs as my laptop HP 17" G72t

If you are managing 8 laptops, then you probably should go with the stability and longevity of 10.04 anyway. 10.10 will no longer be supported after April 2012. 10.04's support  will last until  April 2013, an entire year longer. Once it goes past that date, you no longer receive security updates, and, on non-LTS releases like 10.10, they usually take down the repositories so you can no longer use Synaptic or Software Center. In my opinion, you're kicking a dying horse here.

---

### Post by Paddy Landau on 2011-09-12
> **cmcanulty said:**
> OK I searched for nvidia in synaptic and it shows the ones installed in the screenshots below...
For future note, if you click *Status* (bottom left side) then *Installed* (top left side), you will see only installed packages. This can make it easier to search for what is already installed.

> **waynefoutz said:**
> If you are managing 8 laptops, then you probably should go with the stability and longevity of 10.04 anyway.
Wise words. For public computers, always stick with the LTS version; and when a new LTS version comes out, wait at least a month before installing it. The first month after a release usually sorts out the majority of bugs.

The next intended LTS version is 12.04, which means you would upgrade from 10.04 to 12.04 in June or July 2012. (Hint: if you create a separate partition for the /home folder, you can do a clean installation without losing your settings.)

---

### Post by cmcanulty on 2011-09-12
OK I removed all the nvidia then reinstalled google earth. Same crash issue
```
cmcanulty@HP:~$ googleearth
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/cmcanulty/.googleearth/crashlogs/crashlog-4e6e32a5.txt

Please include this file if you submit a bug report to Google.
cmcanulty@HP:~$ ^C
cmcanulty@HP:~$ 

```

---

### Post by cmcanulty on 2011-09-12
Oh wow after a restart I have it up and working! Now to find where it is installed so I can put it on the menu. Thanks all I have been trying this for months and finally success.

---

### Post by cmcanulty on 2011-09-12
OK great I have it installed and working on all the library computers. I hate it when something doesn't work after  numerous searches fixes etc. Especially at the library as I don't want to give them any excuse to go back to windows.I have been troubleshooting this for months.Solved.Thanks everyone.

---

### Post by cmcanulty on 2011-09-16
I want to post a fix I found for the small how to read fonts on google earth. Install qt4-qtconfig from synaptic. Then find it in under system-preferences. Click the font tab and enlarge it-I picked 14. Then file-save & file-exit and presto it works and now google earth is much easier to use.

---

### Post by snowweb on 2012-05-19
I've got the same issue on a new laptop as the original poster and I want to try your fix of removing the nvidia drivers, but when I do, it tells me that ubuntu-desktop and kubuntu-desktop (along with a million applications which it says I'll nolonger by needing!) will also be uninstalled because the former, depend on nvidia-common.

I use kubuntu desktop all the time, so I can't really agree to it's removal right?

Is there a way around this please?

Thanks.

---

