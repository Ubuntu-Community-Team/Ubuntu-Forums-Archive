---
title: "Compiz Check Results"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by 949label on 2010-06-01
Hi I'm trying to get the desktop effects to work but i'm stuck this is what compiz check gave me 
Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G98 [GeForce G100] (rev a1)
 Driver in use:         nouveau
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
is my graphics card not good enough or what can i do?

---

### Post by Ozymandias_117 on 2010-06-01
Sounds like your graphics card's drivers aren't installed. Look in System -> Admin -> Hardware Drivers and see if you can install them there.

If not, post back the ouput of ```
sudo lspci | grep VGA
```

---

### Post by tom.swartz07 on 2010-06-01
> **949label said:**
> Hi I'm trying to get the desktop effects to work but i'm stuck this is what compiz check gave me 
Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G98 [GeForce G100] (rev a1)
 Driver in use:         nouveau
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
is my graphics card not good enough or what can i do?

HEY! Thats my script that I had posted a few days ago!

it appears that ozy was right, it seems to be that you dont have the proper drivers installed, and there is no assigned rendering method..



Also, if you want, run that script like this for a LOL
```
./compiz-check --banana
```:popcorn:

---

### Post by 949label on 2010-06-01
Thanks for the help 
here is what the sudo command game me 

02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce G100] (rev a1)

---

### Post by Ozymandias_117 on 2010-06-01
32-bit: [http://www.nvidia.com/object/linux-display-ia32-195.36.24.htmlhttp://www.nvidia.com/object/linux-display-ia32-195.36.24.html]("http://www.nvidia.com/object/linux-display-ia32-195.36.24.htmlhttp://www.nvidia.com/object/linux-display-ia32-195.36.24.html")

64-bit: [http://www.nvidia.com/object/linux-display-amd64-195.36.24.html]("http://www.nvidia.com/object/linux-display-amd64-195.36.24.html")

If you aren't sure if you need 32-bit or 64-bit post back the output of ```
uname -m
```

---

### Post by 949label on 2010-06-01
LOL Banana :)

---

### Post by 949label on 2010-06-01
i686

---

### Post by Ozymandias_117 on 2010-06-01
32-bit: [http://www.nvidia.com/object/linux-display-ia32-195.36.24.html]("http://www.nvidia.com/object/linux-display-ia32-195.36.24.html")

---

### Post by 949label on 2010-06-01
cant run the file

---

### Post by 949label on 2010-06-01
I ran compiz check and got this 

Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
but i still can't enable the desktop effects :confused:

---

### Post by Ozymandias_117 on 2010-06-01
Please don't make multiple threads on the same topic [http://ubuntuforums.org/showthread.php?t=1499321]("http://ubuntuforums.org/showthread.php?t=1499321")


After downloading the file, run these commands in a terminal:
```
cd ~/Downloads/
chmod +x NVIDIA-Linux-x86-195.36.24-pkg1.run 
sudo ./NVIDIA-Linux-x86-195.36.24-pkg1.run 

```

---

### Post by 949label on 2010-06-01
I'm sorry 
but the on the previous post i was on my friends computer but he left so I switched over to mine and this new thread is the problem i'm facing and thanks for the help man

---

### Post by overdrank on 2010-06-01
:oops:Threads merged. :)

Edit
> **949label said:**
> I ran compiz check and got this 

Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
but i still can't enable the desktop effects :confused:
It would appear you are using the intel chipset now since the change in systems.

---

### Post by Ozymandias_117 on 2010-06-01
> **overdrank said:**
> :oops:Threads merged. :)

Edit

It would appear you are using the intel chipset now since the change in systems.

Oops :oops: I'm glad you noticed that... I knew he said he switched machines but I didn't even think about it.

---

### Post by 949label on 2010-06-01
yes i'am its an old IBM Netvista :)

---

### Post by Ozymandias_117 on 2010-06-01
It looks like you're already using the Intel drivers. Try ```
glxgears
``` to see if OpenGL 3d is working.

---

### Post by 949label on 2010-06-01
The gears are up and running

---

### Post by Ozymandias_117 on 2010-06-01
Do you get any errors when you try to enable Compiz?

---

### Post by 949label on 2010-06-01
I just get "Desktop effects could not be enabled" when i try to enable visual effects 
and upon closing the gears i got 

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 245525 requests (245522 known processed) with 0 events remaining.

---

### Post by Ozymandias_117 on 2010-06-02
> **949label said:**
> I just get "Desktop effects could not be enabled" when i try to enable visual effects 
and upon closing the gears i got 

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 245525 requests (245522 known processed) with 0 events remaining.

I'm not sure what to tell you on the second computer... Install those drivers and your first one should be fine.

That's normal.

---

