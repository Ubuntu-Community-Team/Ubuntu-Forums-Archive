---
title: "My mouse and keyboard are  not working(in Ubuntu 10.04)"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by thedeadlock on 2010-05-01
Today I trying to install Ubuntu 10.04 but when I   installing 10.04 from CD my keyboard works only in the startup menu  when choosing whether to install or check for disk errors. but when I  get to the actual installation and need to choose time zone, partitions  and such, both keyboard and mouse are not working.

My pc configuration is: motherboard intel d102gcc2, processor Pentium D 2.8Ghz, ram 1gb.  keyboard a4tech(ps/2),mouse:eyesee(ps/2) optical 

waiting for reply :confused:

---

### Post by kylanmies on 2010-05-01
I upgraded my Ubuntu to lucid lynx this morning and the keyboard stopped working. It seems like a lot of people are having similar problems. I was thinking of waiting for some time in case someone fixes the problem. I'm using my other operating systems in the meantime.

---

### Post by Cliffystones on 2010-05-01
Just wanted to add that I'm having the same problem.  Did the upgrade from Karmic to Lucid, keyboard and mouse lock up whenever I either click on my user name or highlight the name and hit enter.

I was able to boot into rescue mode.  I chose repair packages and let the OS do it's thing.  Then I selected resume normal boot, entered username and password and "startx" and the mouse and keyboard worked. 

The I couldn't get on to the Internet. NIC seemed to be working, status showed eth0 connected.  IF config showed NIC was working, but trying to ping the router was unsuccessful.

Anyway, when I rebooted I had the same lock up of the mouse and keyboard as before. 

Asus Mobo
P4 @ 3Ghz
4Gb ram
Dual boot into XP.

I suppose I'll have to try a full install from scratch, or revert to Karmic if the Gurus are unable to find a fix. :(

---

### Post by chucksters on 2010-05-01
Similar problem here. A few of the keys work, most don't. 
 
Mine starts up with GRUB LOADER and it beeps for a while, then it makes me select which version to run. Keyboard doesn't work properly in any version
 
This stinks

---

### Post by RedNight on 2010-05-02
> **Cliffystones said:**
> Just wanted to add that I'm having the same problem.  Did the upgrade from Karmic to Lucid, keyboard and mouse lock up whenever I either click on my user name or highlight the name and hit enter.

I was able to boot into rescue mode.  I chose repair packages and let the OS do it's thing.  Then I selected resume normal boot, entered username and password and "startx" and the mouse and keyboard worked. 

The I couldn't get on to the Internet. NIC seemed to be working, status showed eth0 connected.  IF config showed NIC was working, but trying to ping the router was unsuccessful.

Anyway, when I rebooted I had the same lock up of the mouse and keyboard as before. 

Asus Mobo
P4 @ 3Ghz
4Gb ram
Dual boot into XP.

I suppose I'll have to try a full install from scratch, or revert to Karmic if the Gurus are unable to find a fix. :(

I have exactly the same problems.

For now, I will stay with 9.10...

---

### Post by amazing on 2010-05-02
> **RedNight said:**
> I have exactly the same problems.

For now, I will stay with 9.10...

My system was worked well with ubuntu 9.10, not keyboard and mouse locked up. When I install the ubuntu 10.04 from downloaded i386 Desktop in CD, I re-format the partition, from clean to install. However, the keyboard and mouse will be hanged when I boot up and need to re-boot several time then use the keyboard and mouse normally. I don't know how to proceed ???

---

### Post by RedNight on 2010-05-02
Any suggestion?

---

### Post by Babuloseo on 2010-05-02
> **Cliffystones said:**
> Just wanted to add that I'm having the same problem.  Did the upgrade from Karmic to Lucid, keyboard and mouse lock up whenever I either click on my user name or highlight the name and hit enter.

I was able to boot into rescue mode.  I chose repair packages and let the OS do it's thing.  Then I selected resume normal boot, entered username and password and "startx" and the mouse and keyboard worked. 

The I couldn't get on to the Internet. NIC seemed to be working, status showed eth0 connected.  IF config showed NIC was working, but trying to ping the router was unsuccessful.

Anyway, when I rebooted I had the same lock up of the mouse and keyboard as before. 

Asus Mobo
P4 @ 3Ghz
4Gb ram
Dual boot into XP.

I suppose I'll have to try a full install from scratch, or revert to Karmic if the Gurus are unable to find a fix. :(


I have the same computer hardware as you..
P$ @ 3GHZ
Asus Mobo
1.7gb RAM
Ubuntu Only



My wireless and mouse and any keyboard dont work..... and my pc's usb ports are not getting detected + my NIC does not work and my Partitions (NTFS) are not showing

---

### Post by Hartha on 2010-05-02
I downloaded the latest 10.04 version & try to upgrade, in the installing process several times my keyboard become freeze & mouse worked fine.After complete the installation non of my USB devices detected & every time I plugged any kind of USB device the system was freeze.Really sad to say that I had to switch back to the previous release 9.10.

---

### Post by Cliffystones on 2010-05-02
I haven't had time to experiment more, but from the looks of the other replies this would seem to not be an isolated problem.  With all of the millions of possible hardware and software configurations I suppose there are bound to be problems.

Since I'm typing this I want to say I'm not asking this to be critical, just inquisitive.  But how can something so basic to the operation of a PC work fine in release after release, and all of a sudden be "dead in the water"?  Again, I haven't a clue to writing and developing software. But a "laymans explanation" of what happens in these kinds of situations would be greatly appreciated for us non-programmers.

A further note, my mouse is wireless, Microsoft USB.  But my keyboard is still good old fashioned PS2.

And last, is there a quick way to "revert" to 9.10, or do I just wipe the partition and start over?

Thanks!

---

### Post by amazing on 2010-05-02
I have surfing the internet and still cannot find any solution to the keyboard/mouse abnormal/freeze. Did anyone submit these as bugs to ubuntu team or there have fixed already?

---

### Post by gkak on 2010-05-03
Only thing that worked fine (at least i can type and use my mouse) is under ubuntu 10.04 recovery mode (choose option from grub menu when pc starts) and then from the options given choose low graphics mode just for this session.

This worked for me and possible explanation is ATI (?) or old graphics card(?), because i use a prehistoric ATI 64 mb laptop graphics card.

The above IS NOT a final solution, just a temporary workaround to do your job for the day.....

If something new will come up i 'll let you know

---

### Post by TheOz on 2010-05-03
Same problem here with NVidia GeForce FX 5200 Graphic Card.

I can use mouse and keyboard for a few seconds in GDM, then they stop working.

The same for LiveCD Installation and 9.10 upgrade.

---

### Post by Meghnaad on 2010-05-03
I was able to sort this problem out 
on my DELL Inspiron Desktop 
check this:

> [http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/](http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/)

I am not sure if this is going to work for you 
Please let me know if it works (even if it doesn't)

---

### Post by RedNight on 2010-05-03
> **TheOz said:**
> Same problem here with NVidia GeForce FX 5200 Graphic Card.

I can use mouse and keyboard for a few seconds in GDM, then they stop working.

The same for LiveCD Installation and 9.10 upgrade.

Same graphic card here.

Can you connect to the internet?

---

### Post by WormiS on 2010-05-03
> **RedNight said:**
> Same graphic card here.

Can you connect to the internet?

same problem, mouse and keyboard freezed, no internet
and the same graphic card "nvidia GEforce fx 5200"
asus MB "p4s800d-X

---

### Post by RedNight on 2010-05-03
> **WormiS said:**
> same problem, mouse and keyboard freezed, no internet
and the same graphic card "nvidia GEforce fx 5200"
asus MB "p4s800d-X

Same MB. Great. :(

---

### Post by Ron on 2010-05-03
You need to edit /boot/grub/menu.lst to add " noapic" to the end of each kernel...vmlinuz line.

The first time, you'll need to follow the grub instructions to do it once as you boot, so you can get in with a working machine to do it to the grub file for a permanent fix.

Note: I don't have or use Ubuntu, this is just a deduction from the description of your problem.

---

### Post by RedNight on 2010-05-04
> **Ron said:**
> You need to edit /boot/grub/menu.lst to add " noapic" to the end of each kernel...vmlinuz line.

The first time, you'll need to follow the grub instructions to do it once as you boot, so you can get in with a working machine to do it to the grub file for a permanent fix.

Note: I don't have or use Ubuntu, this is just a deduction from the description of your problem.

I've tested that tip with ubuntu LIVE CD and everything was ok as it should be.

I've installed 10.04 again. Now,I need to deactivate that APIC permanently.

Any suggestion??

P.S.- I did it. Thanks for the help, Ron! ;)

---

### Post by tfleonard on 2010-05-04
I had the same problem with a Dell Inspiron 2650 laptop aafter upgrading from 9.10 to 10.04.  The solution was to add the following to the boot line:

acpi=off

You can also try:

acpi=off noapic


This fix allows the keyboard and touch pad to work in Gnome.  The down side is that the machine will not shut off without pushing the power button.  In addition, the battery monitor does not work.  

This problem is related to the kernel version and modules, not the Ubuntu version per se.  My 2.6.31.20 kernel from Ubuntu 9.10 is still available on my grub 2 menu.  This kernel boots without having to disable acpi and all of ubuntu 10.04 seems to work.  
You might also consider changing to the 2.6.33 kernel.

---

### Post by eredhil on 2010-05-04
Having the same issues with 10.04 in a vm on an imac.
earlier versions of 10.04 worked fine but the RC and then the final will install but when you restart no keyboard 

Steve

---

### Post by WormiS on 2010-05-04
it works...
Thx

---

### Post by amazing on 2010-05-05
Cited from wiki

[http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)

"It can be a cause of system failure, as some versions of some operating  systems do not support it properly. If this is the case, disabling I/O  APIC may cure the problem."

I have tried with this steps:
1) open Terminal by clicking Application->Accessories->Terminal
2) cd /etc/default
3) sudo vi grub
4) append noapic nolapic in GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" such that it looks
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic nolapic"
5) save it and run update-grub

I am still monitoring any abnormal if there.

---

### Post by amazing on 2010-05-06
> **amazing said:**
> cited from wiki

[http://en.wikipedia.org/wiki/intel_apic_architecture](http://en.wikipedia.org/wiki/intel_apic_architecture)

"it can be a cause of system failure, as some versions of some operating  systems do not support it properly. If this is the case, disabling i/o  apic may cure the problem."

i have tried with this steps:
1) open terminal by clicking application->accessories->terminal
2) cd /etc/default
3) sudo vi grub
4) append noapic nolapic in grub_cmdline_linux_default="quiet splash" such that it looks
grub_cmdline_linux_default="quiet splash noapic nolapic"
5) save it and run update-grub

i am still monitoring any abnormal if there.

a

---

### Post by amazing on 2010-05-06
> **amazing said:**
> cited from wiki

[http://en.wikipedia.org/wiki/intel_apic_architecture](http://en.wikipedia.org/wiki/intel_apic_architecture)

"it can be a cause of system failure, as some versions of some operating  systems do not support it properly. If this is the case, disabling i/o  apic may cure the problem."

i have tried with this steps:
1) open terminal by clicking application->accessories->terminal
2) cd /etc/default
3) sudo vi grub
4) append noapic nolapic in grub_cmdline_linux_default="quiet splash" such that it looks
grub_cmdline_linux_default="quiet splash noapic nolapic"
5) save it and run update-grub

i am still monitoring any abnormal if there.


it works for me and it solved my problem, no keyboard locked
==================================================
==================================================

---

### Post by dominics on 2010-05-07
> **Meghnaad said:**
> I was able to sort this problem out 
on my DELL Inspiron Desktop 
check this:

Quote:
[http://blog.ichinmay.com/2010/05/03/...mouse-problem/](http://blog.ichinmay.com/2010/05/03/...mouse-problem/)

I am not sure if this is going to work for you 
Please let me know if it works (even if it doesn't)

I've had no problems with the keyboard thankfully, but the mouse is dead and this fix didn't work for me. I have a Dell Precision 380, with standard HP PS2 Mouse, and HP PS2 Keyboard. 

Looks like back to 9.10.

---

### Post by grothag on 2010-05-07
> **amazing said:**
> Cited from wiki

[http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)

"It can be a cause of system failure, as some versions of some operating  systems do not support it properly. If this is the case, disabling I/O  APIC may cure the problem."

I have tried with this steps:
1) open Terminal by clicking Application->Accessories->Terminal
2) cd /etc/default
3) sudo vi grub
4) append noapic nolapic in GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" such that it looks
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic nolapic"
5) save it and run update-grub

I am still monitoring any abnormal if there.

Don't know if these settings work but will definitely destroy my processor, on core is constantly on 100%. I need some other solution.

---

### Post by yktula on 2010-05-16
The steps posted by amazing work for me.

---

### Post by eGelor on 2010-05-18
Solution was to first upgrade dpkg (apt-get install dpkg) then run a full upgrade (aptitude full-upgrade). This caused the util-linux error to go away and full-upgrade to hum along like normal.

I fix my problem today.

---

### Post by brerbridge on 2010-05-23
what eGelor said. worked like a charm!

---

### Post by yktula on 2010-05-23
The problem with this is (Amazing's steps) that, with ACPI disabled, Ubuntu recognizes only one core (check /proc/cpuinfo and the GNOME system moniter). Does anyone have a better/real fix?

---

### Post by edempco on 2010-05-24
I agree with "yktula", these thing that are being suggested do not address whatever the real problem seems to be. 

My system is hand-build and I know what is installed and what works. The problem seems to be with the graphics card. Mine is a ATI Diamond Radeon R9550 w/ 256 MB DD2. This is an AGP card. I believe that the focus of effort be directed to AGP-style cards and those other graphic cards that have been mentioned in this thread. 

After several attempts, I was able to replace (could not upgrade) my previous version of Ubuntu with Lucid. Since the installation, I am unable to consistently boot into Lucid before all human interface is locked up (keyboard and mouse). 

Disabling other parts of 10.04 do not seem to be the answer or a good  way of approaching the problem. I believe, what we are all looking for is a good explanation of the central problem and then some solid suggestions for a solution.

---

### Post by rockinroll on 2010-06-15
i have ubuntu 10.4 on my laptop and had similar issues with the mouse and usb devices during install unplug all your usb and it will go better for install as for the mouse not working i did the same (the mouse is usb) but i do notice that every now and then my mouse stops working i can move it but it wont click even thought the mouse changes to a hand or whatever when you mouse over links and so on.

---

### Post by mediate on 2010-07-08
Well, what worked for me (though I still have no idea how) is to install using wubi. It seems that I can use my mouse and keyboard in ubuntu now, but the reason why still escapes me ...

---

### Post by fultoodhamaal on 2010-07-22
> **tfleonard said:**
> I had the same problem with a Dell Inspiron 2650 laptop aafter upgrading from 9.10 to 10.04.  The solution was to add the following to the boot line:

acpi=off

You can also try:

acpi=off noapic


This fix allows the keyboard and touch pad to work in Gnome.  The down side is that the machine will not shut off without pushing the power button.  In addition, the battery monitor does not work.  

This problem is related to the kernel version and modules, not the Ubuntu version per se.  My 2.6.31.20 kernel from Ubuntu 9.10 is still available on my grub 2 menu.  This kernel boots without having to disable acpi and all of ubuntu 10.04 seems to work.  
You might also consider changing to the 2.6.33 kernel.
i am having the same issue on my 2650. I tried with noapic/nolapic but not acpi. Will try it out and see if it works. Fedora 13/openSUSE 11.3 are ok but Ubuntu/Linuxmint don't work. 

How do you change the kernel to 2.6.33 ?

---

### Post by GarthS on 2010-07-23
Well, for what it's worth, I installed 10.04LTS on the following machine 2 weeks ago and have had NO ISSUES since! :grin:

                                 Gnome: 2.30.2
 Kernel: 2.6.32-23-generic
 OS: Ubuntu 10.04LTS  (lucid)
 

 Computer Model: HP dc5000 Ut(pb470a)  
 Graphics: Intel Corporation 82865G Integrated Graphics Controller (clock: 33MHz)
 CPU: Intel Pentium 4 3.00GHz (clock: 800MHz) (32 bit) (L2 cache 1mb)
 Memory: 2x1GB DDR Synchronous 400 MHz (2.5 ns)
 Wireless interface : RT2561/RT61 802.11g PCI
 Hard Drive: IDE  WDC WD1600AAJB-0


I have taken all the updates from Update Manager since install. I don't  know if it's the pc I installed on, or if it's the updates, but for me  this issue seems to be resolved. Maybe this information can help some of  you. If not, good luck and don't give up! :wink:

---

### Post by fultoodhamaal on 2010-07-23
I tried out "noacpi pci=noacpi acpi=off" and that seem to have done the  trick. I was able to boot and use the keyboard and mouse.

---

### Post by dob99 on 2010-08-06
> **yktula said:**
> The problem with this is (Amazing's steps) that, with ACPI disabled, Ubuntu recognizes only one core (check /proc/cpuinfo and the GNOME system moniter). Does anyone have a better/real fix?

I can confirm that this is the case for me too - only one core shown in /proc/cpuinfo. I *didn't* add the options to turn off ACPI - just APIC.

I can't confirm if it actually solved the problem, since it is intermittent. However, I would prefer (but only just) to get my other three cores back, even if means I need to ssh in from another machine to do a (somewhat) clean reboot.

---

### Post by jfs3b4stian on 2010-08-13
For me seems to work (2 processor viewed - Pentium4 HT)
with this args:
noapic pci=assign-busses apicmaintimer idle=poll reboot=cold,hard

---

### Post by firefreak on 2010-08-25
You would think this would be a top priority issue. I just downloaded the latest Ubuntu 10.04 install cd and I have no keyboard support with it. Great.

Can't access my updated Kubuntu 10.04 installation either.

...and it's been like this since April. What the f-ck?

---

### Post by prabath_fun on 2010-09-06
Hi to all,
  After long search from Ubuntu10.04 released, now only I got this thread. 
  I checked Live CD Ubuntu 10.04 with APIC disabled. It works... But, I have not verified number of cores are in active. 

  But, I tried "noapic" with Ubuntu9.10 installed on my PC (Just to try before installing Ubuntu10.04). I am getting error message that no such command found. Whether, I am missing something? I am just Ubuntu user and not programmer / coder. Kindly explain me in detail....

   Today evening I will check the no of cores in active. If no problem I will go ahead for installation with wubi.....

---

### Post by prabath_fun on 2010-09-07
Hi,
  I checked live Ubuntu 10.04 boot with noapic and found only one core was detected. 
  Then, I tried with "noapic pci=assign-buses apicmaintimer idle=poll reboot=cold,hard" as suggested by jfs3b4stian and found both cores were seen in gnome moniter. Thanks to jfs3b4stian.....
  Can some one help me how to pass this command while installing with wubi..
With advanced thanks,
prabth

---

### Post by prabath_fun on 2010-09-07
bump...

---

### Post by prabath_fun on 2010-09-09
Hi, I tried by installing Ubuntu 10.04 and 10.10 beta with "noapic pci=assign-buses apicmaintimer idle=poll reboot=cold,hard" command. No improvement. Only live CD works with it.
   So, looks like Ubuntu 10.10 also may have same problem.
   Kindly some one help...

---

### Post by prabath_fun on 2010-09-15
Anybody have some update on this. Kindly guide me how to get LTS release to work.

---

### Post by parish on 2011-02-23
> **prabath_fun said:**
> I tried with "noapic pci=assign-buses apicmaintimer idle=poll reboot=cold,hard" as suggested by jfs3b4stian and found both cores were seen in gnome moniter. Thanks to jfs3b4stian.....

This worked for me also. P4 HT, both cores visible in System Monitor, but I had to attach the HDD to another box and edit /boot/grub/grub.cfg as the install went fine, it wasn't until I restarted that the problem showed up at the login screen where neither the keyboard and mouse worked.

My problem now is that the first thing that happened was that Ubuntu installed about 300 updates, including a new kernel and removed those options from grub.cfg - even from the entries for the old kernel.

This is not much use if it happens everytime the kernel gets updated. Is there any way to make these additional options permanent so they are retained across a kernel update?

---

