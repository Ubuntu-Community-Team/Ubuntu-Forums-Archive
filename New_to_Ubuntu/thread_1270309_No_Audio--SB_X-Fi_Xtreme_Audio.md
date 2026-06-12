---
title: "No Audio--SB X-Fi Xtreme Audio"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by Rachel Evans on 2009-09-19
```
08:00.0 PCI bridge: Creative Labs Device 7006
        Flags: bus master, fast devsel, latency 0
        Bus: primary=08, secondary=09, subordinate=09, sec-latency=64
        Memory behind bridge: feb00000-febfffff
        Capabilities: <access denied>
        Kernel modules: shpchp

09:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
        Subsystem: Creative Labs Device 0010
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```It's recognized but I have no audio! Help!

---

### Post by HappyFeet on 2009-09-19
Check your sound levels by right clicking your speaker icon and selecting **open volume control**.

---

### Post by Rachel Evans on 2009-09-19
> **HappyFeet said:**
> Check your sound levels by right clicking your speaker icon and selecting **open volume control**.
locked at full.

---

### Post by j.bell730 on 2009-09-19
Have you followed [these]("http://ubuntuforums.org/showthread.php?t=870001") instructions?

---

### Post by Rachel Evans on 2009-09-19
> **j.bell730 said:**
> Have you followed [these]("http://ubuntuforums.org/showthread.php?t=870001") instructions?

I now have, with no errors to the best of my knowledge. restarted and everything However, it is still not showing it under the drop down list.

---

### Post by j.bell730 on 2009-09-19
Post output of
```
lspci -v | grep Subsystem
```

Look for the line that says something like this (this is what mine says):
```
Subsystem: Creative Labs Device 0031
```

---

### Post by Rachel Evans on 2009-09-19
> **j.bell730 said:**
> Post output of
```
lspci -v | grep Subsystem
```

Look for the line that says something like this (this is what mine says):
```
Subsystem: Creative Labs Device 0031
```
Subsystem: Creative Labs Device 0010

---

### Post by j.bell730 on 2009-09-19
Ok, I think I see the problem. You'll have to do this all over again, because I made a fix in the original file for you.

**1)** Download my attachment.

**2)** *Run command*:
```
tar -xf XFiDrv_Linux_Public_US_1.00.tar.gz
```
**3)** *Run command*:
```
cd XFiDrv_Linux_Public_US_1.00
```
**4)** *Run command*:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```
**5)** *Run command*:
```
make
```
**6)** *Run command*:
```
sudo make install
```

I had to edit a file within the original file for your particular card numbers. Hope this helps.

---

### Post by Rachel Evans on 2009-09-19
> **j.bell730 said:**
> Ok, I think I see the problem. You'll have to do this all over again, because I made a fix in the original file for you.

**1)** Download my attachment.

**2)** *Run command*:
```
tar -xf XFiDrv_Linux_Public_US_1.00.tar.gz
```**3)** *Run command*:
```
cd XFiDrv_Linux_Public_US_1.00
```**4)** *Run command*:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```**5)** *Run command*:
```
make
```**6)** *Run command*:
```
sudo make install
```I had to edit a file within the original file for your particular card numbers. Hope this helps.

Firefox is not allowing me to download it fails it with the error attached.

---

### Post by sandyd on 2009-09-19
right click on atachment and save it to desktop

---

### Post by j.bell730 on 2009-09-19
**Right click** attachment > **Save Link As...** > **Desktop**

---

### Post by Rachel Evans on 2009-09-19
> **j.bell730 said:**
> Ok, I think I see the problem. You'll have to do this all over again, because I made a fix in the original file for you.

**1)** Download my attachment.

**2)** *Run command*:
```
tar -xf XFiDrv_Linux_Public_US_1.00.tar.gz
```**3)** *Run command*:
```
cd XFiDrv_Linux_Public_US_1.00
```**4)** *Run command*:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```**5)** *Run command*:
```
make
```**6)** *Run command*:
```
sudo make install
```I had to edit a file within the original file for your particular card numbers. Hope this helps.

argh!! it seemed to have worked flawlessly... but it's still not showing up on the menu! [see attachment]

---

### Post by Rachel Evans on 2009-09-19
..?

---

### Post by Rachel Evans on 2009-09-19
Anyone?

---

### Post by Rachel Evans on 2009-09-20
Is anyone able to help me? I'd really like to get this setup working!

---

### Post by Rachel Evans on 2009-09-21
Anyone able to help :-)?

---

### Post by Perfect Storm on 2009-09-21
Just in case. Have you disable the onboard audio in your BIOS?

---

### Post by Rachel Evans on 2009-09-21
I don't think so, still works in Vista.

---

### Post by Ciceronius on 2009-11-12
Ugh, I have the exact same card that Ms. Rachel Evans does...  I tried to compile the modified drivers (after trying with the original ones), and I get this message =(

```
linux-headers-2.6.31-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.31-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```What's that all about?

---

### Post by kostkon on 2009-11-12
> **Ciceronius said:**
> Ugh, I have the exact same card that Ms. Rachel Evans does...  I tried to compile the modified drivers (after trying with the original ones), and I get this message =(

```
linux-headers-2.6.31-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.31-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```What's that all about?
I can see that you are using 9.10. Thus, your X-Fi may/should work after installing the package
```
linux-backports-modules-alsa-karmic-generic
```
and then rebooting.

If you like, give it a try.

Hope that helps.

---

### Post by Ciceronius on 2009-11-12
Thanks for the help.  Unfortunately, after I tried:

```
$ make
```

I get this error:

```
make -C /lib/modules/2.6.31-14-generic/build M=/home/ahw/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/ahw/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/ahw/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/ahw/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/ahw/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/ahw/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/ahw/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/ahw/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2

```

I'm completely new to Ubuntu.  I probably didn't install something correctly (or at all) during this whole ordeal of trying to get my sound working.

---

