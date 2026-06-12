---
title: "Ubuntu Running Slower than Vista?"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by mpl34 on 2009-02-07
I am having a bit of an issue with the running of kubuntu, its seems slugish. I am no guru but just navigating the desktop seems to be especially when compared to my vista partition.

I have attached a screenshot of my system, it says i have 134 processes running which seems ridiculous. The task bar is also present to show the applications i am running (konsole, Konqueror, Ktorrent, Amarok, System Monitor, Dolphin). I have a dual core processor, i assumed intrepid will be compatible with a dual core processor straight out of the packet. 

Please any help to speed up my system would be much appreciated. I vista usually runs at 10-15% of my total CPU.

---

### Post by taurus on 2009-02-07
Sluggish sounds like a graphic card problem.  Have you installed a driver for your graphic card and what is it?

```
lspci | grep VGA
```

---

### Post by mpl34 on 2009-02-07
```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
```
```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
        Subsystem: Dell Device 0228                                            
        Flags: bus master, fast devsel, latency 0, IRQ 16                      
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]               
        Memory at e0000000 (64-bit, prefetchable) [size=256M]                  
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]               
        I/O ports at df00 [size=128]                                           
        [virtual] Expansion ROM at fea00000 [disabled] [size=128K]             
        Capabilities: [60] Power Management version 2                          
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint, MSI 00                                    
        Capabilities: [100] Virtual Channel <?>                                        
        Capabilities: [128] Power Budgeting <?>                                        
        Capabilities: [600] Vendor Specific Information <?>                            
        Kernel driver in use: nvidia                                                   
        Kernel modules: nvidiafb, nvidia
```

---

### Post by mpl34 on 2009-02-07
Sorry here is the attachment

EDIT: The load average is peaking at 2.75, the cpu almost peaks at 100% at one spike, the physical memory is at 1GB (i have a total of 3), and nothing in swap memory

---

### Post by taurus on 2009-02-07
Run the top command from a terminal to see which process is taking up all the CPU (or use htop if you want the GUI but you have to install it first).

```
top
```

---

### Post by mpl34 on 2009-02-07
the top command showed that xorg and kwin were at time both using 30% CPU each (ie. 60% combined) with plasma also using 10% at times.

It is weird that kwin is here as i have selected compiz as my windows manager under session settings.

---

### Post by mpl34 on 2009-02-07
I have notice Xorg runs around 35-40% when navigating around the desktop and when minimizing, maximizing and moving windows around. Also when using konqueror it can use up to 60% of the CPU. Also there is something weird that occasionally spikes at 151% ksoftirqd/1.

I can't understand why my graphics card would slow down the system so much. Even in vista with all the eyecandy thats available including docks and widgets it runs smoothly.

---

### Post by mpl34 on 2009-02-07
Just installed opera and have noticed a huge improvement in the running of my system, i think that i will slowly replace the pre-installed kubuntu apps with ones i've previously been using with vista and will hopefully continue to see an imrovement. Next will be ktorrent.

---

### Post by mpl34 on 2009-02-08
I think the issue may be due to my laptop having a cual core processors and that ubuntu does not yet support dual core processors? Is this correct?

---

### Post by cariboo on 2009-02-08
Linux has had dual core/cpu support for a lot longer than windows. Your attachment was kind of small so I couldn't really see it properly, but it looks like you've got something running that is using a lot of cpu cycles

Could you open a terminal and run:

```
top
```

and paste the output in your next post, and please use the [noparse]```

```[/noparse] to enclose the output.

Jim

---

### Post by jimv on 2009-02-08
> I am having a bit of an issue with the running of kubuntu, its seems slugish.

Someone will flame me for this, but the problem is that KDE 4 (Kubuntu's desktop environment) IS slow.  That's been my main beef with it and it's why I'm sticking with Gnome (Ubuntu's desktop environment) for now.

---

### Post by emshains on 2009-02-08
Try gnome, xfce or e17. 

How much ram does your system have ? Because kubuntu eats a lot of it, because it preloads everything on startup. That makes it faster on fast systems, but makes it slower on slow systems. Although I don't think you should have problems, because 1gb< should be good enough for KDE, and I think that you could have that much ram.

---

### Post by mpl34 on 2009-02-08
Hey,

Sorry i haven't been quick in my reply but i will post the outcome of top later today (at work atm), also my cpu has 3gb of ram. And yer i kinda wished i had started off with gnome now but i dnt quite feel like giving up yet.

Is anything required to make sure that linux runs with dual core or should this be the default after install.

Cheers,

---

### Post by Bios Element on 2009-02-08
> **mpl34 said:**
> Hey,

Sorry i haven't been quick in my reply but i will post the outcome of top later today (at work atm), also my cpu has 3gb of ram. And yer i kinda wished i had started off with gnome now but i dnt quite feel like giving up yet.

Is anything required to make sure that linux runs with dual core or should this be the default after install.

Cheers,

duel core is default.

---

### Post by pbotros1234 on 2009-02-08
In my opinion, it is definitely a problem with your video card driver. Have you installed any restricted drivers yet? NVidia cards especially need special drivers, and there's tons of guides out there that tell you how to setup linux up with an nvidia.

---

### Post by Racecar56 on 2009-02-08
NVIDIA drivers from original website (nvidia.com) pwn the ones that come in the repos, unless your'e using Kubuntu 9.04a3. Don't even _try_ it on 9.04a3. If you're on 8.10 it's easy as pie to install the NVIDIA drivers. Here is a good way:

[LIST=1]
[*]1. Remove any NVIDIA drivers you have currently, including ones from the repo (hardware drivers a.k.a. jockey)
[*]2. Get the driver from nvidia.com.
[*]3. Once done downloading, close everything, save your work, and press CTRL+ALT+F1.
[*]4. You should see a bit terminal, if you didn't see it then press CTRL+ALT+F1 repeatedly until you see it, then stop.
[*]5. Assuming you downloaded it to your desktop, do 'cd ~/Desktop' without quotes.
[*]6. Do the 'ls' command (no quotes)
[*]7. You should see a file called 'NVIDIA-blah-blah-blah.run', do 'chmod +x NVIDIA*.run' (no quotes)
[*]8. Do the 'sudo /etc/init.d/kdm stop' (no quotes) command, if it don't work maybe try 'sudo /etc/init.d/kdm4 stop'. No quotes.
[*]9. You might see something that looks like the shutdown screen, don't worry, it's not actually shutting down. If you are stuck on a black screen shortly after, press CTRL+ALT+F1 repeatedly until you get back to that terminal.
[*]10. Do the './NVIDIA*.run' command (no quotes), this will run your setup you downloaded (finally!).
[*]11. Follow the instructions on screen, need help, tell me.
[/LIST]
[EDIT]I don't know for a fact, but this should work on any ubuntu version 8.10 and under (that includes 8.10).
If you want to be daring, you could try to install them on 9.x versions. I can help you with that, but it requires a good bit of work, and I don't think it's actually worth bothering to even _install_ 9.x, it's a bit frustrating, at lest you'd be getting pretty much the latest (at least recent) version of supposedly anything.[/EDIT]

---

### Post by mpl34 on 2009-02-08
Hey Racecar

Yes this is exactly what i did when i installed my driver for NVidia graphics card and it seems to have working perfectly. 

Also i have now installed utorrent using wine instead of using ktorrent and again i have seen an improvement. 

I am beginning to think that the main cause was konqueror. I am now running wobbly and transparent windows and seems to be working nicely however this still seems to be running through the kwin application and i would preferably like to use compiz. (Is there a difference between compiz and compiz-fusion now? ie. does updating compiz or installing the lastest compiz install compiz-fusion by default?)

Also kiba dock seems to consistently have errors but again i believe this is due to running kwin as my windows manager and not compiz. (but this is just a guess)

Also should i be worried that i have 150 processes running or is that just typical of ubuntu/kubuntu. If i wanted to install the gnome desktop environment i can just use something like ```
sudo apt-get ubuntu-desktop 
```correct? and my KDE apps should run fine with a gnome environment?

---

### Post by mpl34 on 2009-02-09
ell here's the output of top as you can obviously see the problem here is konqueror
```
Tasks: 151 total,   4 running, 147 sleeping,   0 stopped,   0 zombie
Cpu(s): 73.5%us,  6.8%sy,  0.0%ni, 18.9%id,  0.0%wa,  0.2%hi,  0.7%si,  0.0%st
Mem:   3110788k total,   788872k used,  2321916k free,    19668k buffers
Swap:  1775140k total,        0k used,  1775140k free,   324256k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
12319 michael   20   0  151m  66m  24m R   76  2.2   0:26.14 konqueror
 5365 root      20   0  149m  30m 8996 S   21  1.0   1:36.68 Xorg
12416 michael   20   0  134m  32m  20m R   21  1.1   0:13.30 nspluginviewer
 5773 michael   20   0  124m  61m  32m R   13  2.0   0:59.89 kwin
12277 michael   20   0  142m  53m  27m S    9  1.8   0:28.51 amarokapp
12551 michael   20   0 46280 9096 6144 S    4  0.3   0:00.12 kio_http
12553 michael   20   0 46280 9160 6204 S    4  0.3   0:00.12 kio_http
 2093 root      15  -5     0    0    0 S    1  0.0   0:00.42 scsi_eh_0
 5692 michael   20   0  3036 1268  628 S    1  0.0   0:00.88 dbus-daemon
 5761 michael   20   0 67076  16m  12m S    1  0.6   0:01.70 kded4
 5895 michael   20   0 31332  12m 9920 S    1  0.4   0:10.20 knetworkmanager
12353 michael   20   0 47660 9668 6288 S    1  0.3   0:00.42 kio_http
12381 michael   20   0 47468 9344 6272 S    1  0.3   0:00.36 kio_http
12382 michael   20   0 47468 9392 6272 S    1  0.3   0:00.36 kio_http
12385 michael   20   0 47468 9468 6268 S    1  0.3   0:00.32 kio_http
12482 michael   20   0 47632 9500 6256 S    1  0.3   0:00.54 kio_http
12526 michael   20   0  2416 1176  884 R    1  0.0   0:00.10 top
 5777 michael   20   0  143m  24m  11m S    0  0.8   0:03.12 knotify4
    1 root      20   0  3056 1888  564 S    0  0.1   0:01.34 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:00.54 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      15  -5     0    0    0 S    0  0.0   0:00.40 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1
   54 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/0
   55 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/1
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify
  146 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue
  150 root      15  -5     0    0    0 S    0  0.0   0:00.02 kseriod
  195 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  196 root      20   0     0    0    0 S    0  0.0   0:00.04 pdflush
  197 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0
  239 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0
michael@michael-laptop:~$
```

I decided to also give the output of top while running opera, On opera i am running 2 youtube videos and refreshing 6 pages i have 10 tabs open all together (ie. 2 pages are just idling)
```
top - 20:06:19 up 22 min,  1 user,  load average: 1.50, 1.28, 0.78
Tasks: 129 total,   2 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.7%us,  5.2%sy,  4.9%ni, 77.4%id,  0.0%wa,  0.3%hi,  1.5%si,  0.0%st
Mem:   3110788k total,   779020k used,  2331768k free,    20948k buffers
Swap:  1775140k total,        0k used,  1775140k free,   329036k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
12917 michael   39  19  110m  28m  18m R   18  0.9   0:05.80 operapluginwrap
12813 michael   20   0  176m  68m  16m S    9  2.3   0:07.84 opera
 5365 root      20   0  143m  31m 9004 S    9  1.0   3:07.14 Xorg
12277 michael   20   0  142m  53m  27m S    6  1.8   1:18.38 amarokapp
 5773 michael   20   0  128m  65m  36m S    5  2.1   1:56.65 kwin
 5789 michael   20   0  111m  40m  20m S    3  1.3   0:12.18 plasma
 5895 michael   20   0 31380  12m 9920 S    1  0.4   0:17.30 knetworkmanager
    4 root      15  -5     0    0    0 S    1  0.0   0:00.92 ksoftirqd/0
    7 root      15  -5     0    0    0 S    1  0.0   0:00.48 ksoftirqd/1
 5109 haldaemo  20   0  6468 4460 3644 S    1  0.1   0:02.52 hald
 5830 michael   20   0  118m  23m  14m S    1  0.8   0:08.90 konsole
 5841 michael   39  19 98764  30m  17m S    1  1.0   0:02.50 python
12330 michael   20   0 67020  22m  16m S    1  0.7   0:01.56 dolphin
12937 michael   20   0  2416 1164  884 R    1  0.0   0:00.12 top
 5836 michael   20   0  128m  44m  20m S    0  1.5   0:18.21 ktorrent
    1 root      20   0  3056 1888  564 S    0  0.1   0:01.34 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1
   54 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/0
   55 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/1
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify
  146 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue
  150 root      15  -5     0    0    0 S    0  0.0   0:00.02 kseriod
  195 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  196 root      20   0     0    0    0 S    0  0.0   0:00.06 pdflush
  197 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0
  239 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  240 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1
 1301 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd
 1328 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd
 1590 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt
 1808 root      15  -5     0    0    0 S    0  0.0   0:00.12 ata/0

```

---

### Post by emshains on 2009-02-10
Is this on a fresh install ?

---

### Post by crjackson on 2009-02-10
> **mpl34 said:**
> I think the issue may be due to my laptop having a cual core processors and that ubuntu does not yet support dual core processors? Is this correct?

No, that's not correct.

---

### Post by mpl34 on 2009-02-12
Yes this was a fresh install, I have now updated to kde4.2 after posting this thread

---

