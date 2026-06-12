---
title: "Ubuntu 8.10 Install Problem"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by bern1939 on 2008-12-05
I have been using 8.04 for quite sometime now....no problems.

Decided to upgrade to 8.10.

All goes well into one hard disk totally set aside for Linux except when I fill in the username & password at start-up the screen freezes.

I installed 8.10 from a net download and same thing happens as when I use a purchased CD for the installation.

Gone back to 8.04 and all works well.

Is there a problem with 8.10? installation process????

Thanks 



Bern

---

### Post by nhasian on 2008-12-05
can we get some information about your computer specs?

```
lshw -C cpu,memory,display,network
```

also when your a the graphical login prompt, if you press Control-Alt-F1 and login with your username and password at the shell prompt, do you log in okay?

---

### Post by bern1939 on 2008-12-05
> **nhasian said:**
> can we get some information about your computer specs?

```
lshw -C cpu,memory,display,network
```

also when your a the graphical login prompt, if you press Control-Alt-F1 and login with your username and password at the shell prompt, do you log in okay?

When I try that I get a screen with very large writing asking me to login etc. I have no mouse at that stage to do so properly so all fails.
Right now when I try normal login I can input the username and password ok but then get a blank orange and/or black screen and all activity stops!!!

Answer to your 2nd.Question

bernard@bernard-desktop:~$ lshw -C cpu,memory,display,network 
WARNING: you should run this program as super-user. 
  *-memory                
       description: System memory 
       physical id: 0 
       size: 510MiB 
  *-cpu 
       product: Intel(R) Pentium(R) 4 CPU 3.06GHz 
       vendor: Intel Corp. 
       physical id: 1 
       bus info: cpu@0 
       version: 15.2.9 
       size: 18EHz 
       width: 32 bits 
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr 
       configuration: id=0 
     *-logicalcpu:0 
          description: Logical CPU 
          physical id: 0.1 
          width: 32 bits 
          capabilities: logical 
     *-logicalcpu:1 
          description: Logical CPU 
          physical id: 0.2 
          width: 32 bits 
          capabilities: logical 
     *-cache:0 
          description: L1 cache 
          physical id: 0 
          size: 8KiB 
     *-cache:1 
          description: L2 cache 
          physical id: 1 
          size: 512KiB 
  *-display 
       description: VGA compatible controller 
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device 
       vendor: Intel Corporation 
       physical id: 2 
       bus info: pci@0000:00:02.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: vga_controller bus_master cap_list 
       configuration: driver=i810_smbus latency=0 module=i2c_i810 
  *-network 
       description: Ethernet interface 
       product: BCM4401 100Base-T 
       vendor: Broadcom Corporation 
       physical id: 9 
       bus info: pci@0000:01:09.0 
       logical name: eth0 
       version: 01 
       serial: 00:0d:56:6b:0a:6c 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes 
  *-network 
       description: Wireless interface 
       physical id: 1 
       logical name: eth1 
       serial: 00:17:3f:8d:b1:dc 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes ip=192.168.1.7 multicast=yes wireless=IEEE 802.11b/g 
the username & password but then get an orange screen (blank) and sometimes a black screen(blank) and there everything stops.

Thanks

Bern

---

### Post by miniyak on 2008-12-05
i had a similar problem,i upgraded from hardy and after login screen everything was blank with waiting cursor frozen, i will note that i didnt take any of the recommended upgrade precautions, however, like you, i tried to upgrade with a disc and still had no luck. i went back to hardy also. only to have basically the same problem when the kernel upgraded. (difference;login screen didnt even appear the second time) i solve that problem by booting in the older kernel version. 

i posted to someone esle who had a similar problem but im not sure how they made out.(i didnt know to subscribe to post yet and finding anything here is a pain)

my comp is a delldimension2350 2.2ghz 512mb no frills (btw, how can i make it so this shows up in every post? if any body knows)

---

### Post by Therion on 2008-12-05
> **miniyak said:**
> 

...(btw, how can i make it so this shows up in every post? if any body knows)

**User CP** (at the upper left of the forums page)

**Edit Your Details**

**Edit Signature**


Enter what you want in the text box, save and exit.

---

### Post by jyaan on 2008-12-05
I don't have the the exact same issue, but it's similar. I have an NVidia card, so it would seem that the new kernel just doesn't play well with dual head (or newer video cards?? I haven't tried single display). When I boot with the new kernel, it shows the console on both screens when a console normally is shown on the main screen only (although all the text is scrambled!), and I can still log in but I just get a cloned screen instead of TwinView. I haven't seen any fixes so far so I just use the older 2.6.27 kernel. You might want to make a bug report.

---

### Post by bern1939 on 2008-12-05
Thanks to all.....think it's best to go back to the old reliable 8.04. Pity but ......

Bern

---

### Post by nhasian on 2008-12-06
well if you can use the terminal then the problem is something in X or Gnome.  can you blacklist your video driver i2c_i810 and see if you can log into ubuntu without it freezing?

```
sudo gedit /etc/modprobe.d/blacklist 
```

then append the line

```
blacklist i2c_i810
```

reboot and see if you can log into ubuntu.

---

