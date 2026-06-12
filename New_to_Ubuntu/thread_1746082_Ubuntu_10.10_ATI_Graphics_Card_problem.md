---
title: "Ubuntu 10.10 ATI Graphics Card problem"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by Ajay Ramaseshan on 2011-05-01
Hello

I have Ubuntu 10.10 installed on a HP Pavillion dm4 which also has an ATI Radeon Graphics Card, I tried installing the Graphics Card Driver in Ubuntu from the section "Additional Drivers". It worked fine generally until I came across this problem in Matlab,

When I tried to open the Property Editor tool in Matlab, Matlab gives me this warning "OpenGL may not be installed correctly" and the Property Editor and figure window just hangs. 
Many other functionalities which involve the Graphics Card, like contour plots or histogram just do not work and Matlab simply hangs.

I am forced to deactivate the Proprietary Graphics Card Driver and use the chipset Graphics Card Driver. It is irritating to do this every time I work, thus I feel this could not be the only solution??

Is there any other method to make this Graphics card work in Ubuntu 10.10 , without using Proprietary Driver, maybe some good open-source driver?? 
can someone please clarify??

---

### Post by clhsharky on 2011-05-01
Ajay Ramaseshan


> "OpenGL may not be installed correctly" 
With Proprietary Driver installed
In terminal copy/paste
```
sudo aticonfig --initial -f
```
enter
password
restart computer

May correct installation.


What ATI chip do you have?
```
lspci -nn | grep VGA
```


Sharky

---

### Post by Blasphemist on 2011-05-01
Try running this and lets see what OpenGL version you have.

```
/usr/lib/nux/unity_support_test -p 
```

This is from the link that follows it.

> What drivers do you recommend?
AMD GPUs:

Fglrx driver: We have had some issues with the fglrx driver but we have been able to resolve them. With the fglrx driver, you will be missing features such as Kernel Mode Setting (KMS).
Open Source Radeon driver: can exhibit rendering artifacts on some systems. In the "System 3" configuration, Unity is not usable due to serious rendering issues.
NVidia GPUs: Nvidia propietary drivers.
Intel GPUs: Intel open source drivers.

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

A couple of systems with ATI are shown in the link.

---

### Post by Ajay Ramaseshan on 2011-05-02
@ clhsharky :

I activated the FGLRX Proprietary Driver and did "Restart to Complete Update". When I did this I noticed many problems:-
While booting , an error is thrown up which just stays for a fraction of a second :-
```
 ...intel:failed to get i915 symbols, graphics turbo disabled 
```

Then the Ubuntu login screen does not show up at all and it goes to a command prompt. Thus I restarted the system with the "sudo shutdown" command, and then booted in recovery mode 
While booting in recovery mode, also I get the same error as above, and then I have to run ubuntu in failsafe graphics mode and reconfigure Graphics for my desktop to appear.

You then askd me to run this command :
```
 sudo aticonfig --initial -f 
```
After running this and restarting , the old problems appear, same error message and no Desktop only command prompt.

By the way this is the output of the other command you asked me to run :-
```

milli@milli-PC:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] [1002:68e0]

```

so then I have a ATI Radeon 5000 card and Intel chipset card...

---

### Post by Ajay Ramaseshan on 2011-05-02
> **Blasphemist said:**
> Try running this and lets see what OpenGL version you have.

```
/usr/lib/nux/unity_support_test -p 
``` 

It says no such file or directory..!

---

### Post by Blasphemist on 2011-05-02
It should be there, if you have natty.

---

### Post by Blasphemist on 2011-05-02
Ajay, I found this on launchpad.

[https://answers.launchpad.net/ubuntu/+question/155405](https://answers.launchpad.net/ubuntu/+question/155405)

Asked for in troubleshooting is:

Can you give the output of:

```
sudo lshw -C display; cat /etc/lsb-release
```

I also found this and while the users could have been clearer in this thread, it looks like at the bottom a solution may have been found.

[https://answers.launchpad.net/ubuntu/+question/155405](https://answers.launchpad.net/ubuntu/+question/155405)

On this thread, it's eventually identified that a newer kernel solves it. I am not a good one for support on updating your kernel. I do know that if you upgrade to natty, your kernel will be updated.

[http://ubuntuforums.org/archive/index.php/t-1594981.html](http://ubuntuforums.org/archive/index.php/t-1594981.html)

---

### Post by Ajay Ramaseshan on 2011-05-02
@ Blasphemist :

This is the output of the command you had asked for:-
```

milli@milli-PC:~$ sudo lshw -C display; cat /etc/lsb-release
  *-display               
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5000 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:3000(size=256) memory:c4440000-c445ffff
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
       resources: irq:45 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:4050(size=8)
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

---

### Post by Blasphemist on 2011-05-02
This is the other thread mentioned in my previous post, that I didn't include and instead duplicated what I had already included.

[http://ubuntuforums.org/showthread.php?p=10729272](http://ubuntuforums.org/showthread.php?p=10729272)

There is a solution at the bottom it seems though I can't validate it.

---

### Post by clhsharky on 2011-05-02
Blasphemist

Did not know you had hybrid graphic Int/ATI, that is a problem with linux drivers in 10.10 and older.

ATI is working on it and with a switch in CCC. You will need latest FGLRX driver and Ubuntu release. I must tell you that its still not working correctly so not to bother yet. Hopefully soon.
Have seen work-rounds but its messy, maybe not to some but certainly a hassle.

Deactivate ATI Proprietary Driver and you should be back on Intel's driver, its OSS.


Sharky

---

### Post by Blasphemist on 2011-05-02
> **clhsharky said:**
> Blasphemist

Did not know you had hybrid graphic Int/ATI, that is a problem with linux drivers in 10.10 and older.

ATI is working on it and with a switch in CCC. You will need latest FGLRX driver and Ubuntu release. I must tell you that its still not working correctly so not to bother yet. Hopefully soon.
Have seen work-rounds but its messy.

Deactivate ATI Proprietary Driver and you should be back on Intel's driver, its OSS.


Sharky

I think he meant your config Ajay.

---

### Post by Ajay Ramaseshan on 2011-05-03
@clhsharky and @Blasphemist :

okay, I will deactivate the FGLRX Proprietary Driver and use the Intel Chipset Driver. Though that is not the ideal solution, it is what looks like to be the best one currently.

Meanwhile, you could keep me posted if there are any new developments !!

---

### Post by chkneater on 2011-05-03
Might I suggest this:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

Make sure to do the section on removing all old drivers first, then begin from the beginning.  And if you are using AMD64, there is an extra lib that you will have to make sure to download.

 So far Catalyst is working fine and I have only noticed choppiness on startup.

Hope it helps.

---

