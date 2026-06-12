---
title: "3d Hardware Acceleration Problems"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by wickedcultgod on 2009-02-13
I finally understand what the problem with my system is but I don't know how to fix it. I have an Acer Aspire One netbook that is not recognizing the 3d acceleration drivers. Here is a quote that explains what is going on:
QUOTE

Important gotcha that took me a while to figure out. The intel PIIX chipset can operate in several modes, IDE compatability, SATA and PATA. It is important that the SCSI-DISK subsystem and the PATA Intel drivers are compiled into the kernel, and not the Intel PIIX ones. If both drivers load, they will fail and you can fall back to IDE-generic drivers, which run in non-dma mode and will make the system extremely slow and unresponsive under heavy disk activity. I've experienced this in my own kernels as well as using live cd's that autoprobe and load modules.

Check your dmesg and be sure you are not falling back to ide-generic drivers. This problem is easy to fix, but since compiling a kernel under ide-generic mode on the AAO can take some considerable time, it took me a while to figure out. 
UNQUOTE

I do not understand how to utilize this information to fix this. If someone knows how to do this and can give me a rundown w/ command lines I will have everything working on this laptop. I understand some command lines but I am just learning. The Ubuntu Pocket Guide helps a lot and I am learning, but obviously I do not know enough. Please someone help me

---

### Post by RomeReactor on 2009-02-13
Hi. What video card does the system have? If it's ATI or nVidia, have you tried installing the drivers form 'System->Administration->Hardware Drivers'?

---

### Post by wickedcultgod on 2009-02-13
The only thing that it shows in the system hardwire driver is support for the wifi. I have an Intel chipset. It is the base that came with the notebook. Is there a command line that I could use to find out what kind it is?

---

### Post by wickedcultgod on 2009-02-13
When I run lsdci it says:
Intel Corporation 82801G (ICH7 Family)

---

### Post by RomeReactor on 2009-02-13
Just to be clear, run this:
```
sudo lshw -C display
```
It will list your video card, along with the driver it's using.

Since this is likely an Intel GPU, it won't show up in Hardware Drivers, as it's only used for restricted (proprietary) drivers, and the Intel driver is open source.

Are you able to reach the desktop?

---

### Post by wickedcultgod on 2009-02-13
This is what I get:

 *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GME Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---

### Post by wickedcultgod on 2009-02-13
And yes I can access the desktop.

---

### Post by RomeReactor on 2009-02-13
Post the output of:
```
glxinfo | grep rendering
```

Try booting in recovery mode (press ESC when grub prompts you to) and select XFIX to see if it can fix the problems.

---

### Post by wickedcultgod on 2009-02-13
It says yes. I am trying the xfix now.

---

### Post by wickedcultgod on 2009-02-13
The fix didn't work. I appreciate the help by the way.

---

### Post by RomeReactor on 2009-02-13
If you get "Yes" in glxinfo, it means you have hardware acceleration enabled; please post more details about the specific problem you have.

---

### Post by unused_bagels on 2009-02-13
I have an integrated intel 945G and I can't get any non-native 3D games to work....

---

### Post by RomeReactor on 2009-02-13
Please mention games in particular. I assume you're trying to run them using Wine?

---

### Post by wickedcultgod on 2009-02-13
I am trying to get tibia to play. When i open the Tibia file,it just opens and immediately closes.

---

### Post by Twitch6000 on 2009-02-13
That is sounding more like a wine problem then a graphics card problem I suggest this be moved to the right place.

I also suggest you look at the wine dldb for the game or program you trying to run.

---

### Post by RomeReactor on 2009-02-13
> **wickedcultgod said:**
> I am trying to get tibia to play. When i open the Tibia file,it just opens and immediately closes.

Have you tried the native Linux client?

---

### Post by wickedcultgod on 2009-02-13
I am running the linux client. In the folder that I extract, I open the Tibia client and it just closes.

---

### Post by RomeReactor on 2009-02-13
> **wickedcultgod said:**
> I am running the linux client. In the folder that I extract, I open the Tibia client and it just closes.

If the instructions say you can run the executable, drag it to a terminal, press ENTER, and if you get errors please post them.

---

