---
title: "Fan issue on Ubuntu 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by sylvainrb on 2010-05-01
Hello,

I installed lucid on my laptop (dual boot with W7) and noticed that when the fan turns on, it won't stop. It is not a noisy fan but I don't it's good for it to run for that long... Looking at htop, it seems that the CPUs are working more than they should but I'm not sure which processes are what... Does anyone run into the same issue? Thanks!

Let me know if you need some sort of output to help :)

---

### Post by cis.ash on 2010-05-01
same me, i use Toshiba satellite L300, and my laptop fan never stops ! any help ??

---

### Post by fatigue on 2010-05-02
please help us. i have a same issue
Toshiba satelite

---

### Post by bombel on 2010-05-02
The same problem on HP 4710s.Please help.

---

### Post by cis.ash on 2010-05-02
well i fixed it :D 
first u have to go to package manager and remove pacage called (acpid) i dont know if this step is necessary, but this is wt i did 

then install a packages called "toshutiles",  "toshset" and "fnfxd",, this fixed the fan issue for me 

i use Toshiba satellite pro L300

---

### Post by sylvainrb on 2010-05-02
Ok here's an update: searching around last night, I found that apparently you need to apply a patch to the kernel to be able to manually control the fan... They even had a gui app to make it easier once patched. That being said though I have a Thinkpad X200 and it seems to be widely known problem on Thinkpads even with previous releases...

You guys should Google something like "your_computer_brand fan control issue ubuntu"...

Hope that helps a little. I'll post the links later and any other updates/solutions I find (feel free to do the same!!)

---

### Post by cis.ash on 2010-05-02
i think a program called ACPI tool is what are you talking about :) 
[http://sourceforge.net/projects/acpitoolgui/](http://sourceforge.net/projects/acpitoolgui/)


tell me if u know how to get this software work :(

---

### Post by sylvainrb on 2010-05-02
No the tool I was referring to is something that has been developed just for Thinkpads and their fan problem.

I think acpi is just a tool to give you information about your system's running status... I don't know about that GUI but if you want to use acpi and don't mind using the terminal, you can install it with
```
sudo aptitude install acpi
```
For example to see the battery status:
```
acpi -b
```
Or CPUs temperatures:
```
acpi -t
```

You can do
```
man acpi
```
to find out about the other commands.

Hope that helps... :)

---

### Post by cis.ash on 2010-05-03
Ohh thx alot,, but i have fixed the issue there was some utility packages that needs to be installed for toshiba laptops, u could search for packages for ur think pad :d

---

### Post by UbuNoob001 on 2010-05-03
Same problem of CPU spikes in Dell Inspiron 1545 with subsequent high temps/fan usage.

---

### Post by fatigue on 2010-05-03
This is how I fixed it.
Most of recent toshiba laptop have a problem with 9.04,9.10 and 10.04
Fan runs all the time and they never turn fan them off even though cpu  temerature is less 30C

Here is a solution


open /boot/grub/menu.lst with a text editor 

For instance, if you use gedit
```
sudo gedit /boot/grub/menu.lst
```Scroll down and find your  ubuntu

"
## ## End Default Options ##

title Ubuntu 10.04, kernel 2.6.28-11-generic
uuid 55b3c634-36c5-4a06-b8ec-8d51a8cb97d4
kernel /boot/vmlinuz-2.6.28-11-generic  root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

Add acpi_osi="Linux" after
"kernel /boot/vmlinuz-2.6.28-11-generic  root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash "

Fixed line should be 

kernel /boot/vmlinuz-2.6.28-11-generic  root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash  acpi_osi="Linux"

and then save and restart
This should fix fan problem in toshiba laptops

---

### Post by cis.ash on 2010-05-03
maybe this could help [http://wiki.archlinux.org/index.php/Fan_speed_control](http://wiki.archlinux.org/index.php/Fan_speed_control)

---

### Post by sylvainrb on 2010-05-03
> **cis.ash said:**
> maybe this could help [http://wiki.archlinux.org/index.php/Fan_speed_control](http://wiki.archlinux.org/index.php/Fan_speed_control)

Thank you for the link! I did find other info on how to fix it but just haven't had the time to get around trying it (finals week!!). I will post any result if I succeed later! :)

---

### Post by cis.ash on 2010-05-03
> **sylvainrb said:**
> No the tool I was referring to is something that has been developed just for Thinkpads and their fan problem.

I think acpi is just a tool to give you information about your system's running status... I don't know about that GUI but if you want to use acpi and don't mind using the terminal, you can install it with
```
sudo aptitude install acpi
```For example to see the battery status:
```
acpi -b
```Or CPUs temperatures:
```
acpi -t
```You can do
```
man acpi
```to find out about the other commands.

Hope that helps... :)

> **fatigue said:**
> This is how I fixed it.
Most of recent toshiba laptop have a problem with 9.04,9.10 and 10.04
Fan runs all the time and they never turn fan them off even though cpu  temerature is less 30C

Here is a solution


open /boot/grub/menu.lst with a text editor 

For instance, if you use gedit
```
sudo gedit /boot/grub/menu.lst
```Scroll down and find your  ubuntu

"
## ## End Default Options ##

title Ubuntu 10.04, kernel 2.6.28-11-generic
uuid 55b3c634-36c5-4a06-b8ec-8d51a8cb97d4
kernel /boot/vmlinuz-2.6.28-11-generic  root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

Add acpi_osi="Linux" after
"kernel /boot/vmlinuz-2.6.28-11-generic  root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash "

Fixed line should be 

kernel /boot/vmlinuz-2.6.28-11-generic  root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash  acpi_osi="Linux"

and then save and restart
This should fix fan problem in toshiba laptops


menu.lst is empty !

---

### Post by natravis on 2010-05-03
> **cis.ash said:**
> menu.lst is empty !

If you are on Lucid or Karmic and did a clean install you are on either grub version 1.98 or 1.97b4 respectively. The file that you change in Grub2, which encompasses both of those versions, you can find out by running ```
grub-install -v
``` is located at ```
/etc/default/grub
```. Use Gedit or Nano or Vim to edit that file then run ```
sudo update-grub
``` afterwards to get the actual boot file located at ```
/boot/grub/gub.cfg
``` to be updated. If you make changese to /boot/grub/grub.cfg manually, the changes will be overwritten anytime the kernel is upgraded. The specific fix from looking at this thread appears to be adding ```
acpi_osi="Linux"
``` to the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` to be changed to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi="Linux""
```

I'm not sure about the double quotes there or not.

---

### Post by cis.ash on 2010-05-04
Solution : go to suspend and then come back, this will stop the fan hahahahha

---

### Post by dynamics on 2010-05-04
Friends.
My laptop details are in the signature (at the bottom of this post).
For  me, installing the 'xserver-xorg-video-radeon' solved this issue. 
So those who have the ATI Radeon graphic card can try this solution.....
Hint: search for 'radeon' in synaptic package manager

---

### Post by cis.ash on 2010-05-05
i once read that if we removed the ACPI programs the OS it self will not control some of the hardware configurations (laptop fan for example ), these hardware will be controld from the Bios, dont u think so guys ?

---

### Post by natravis on 2010-05-06
> **cis.ash said:**
> i once read that if we removed the ACPI programs the OS it self will not control some of the hardware configurations (laptop fan for example ), these hardware will be controld from the Bios, dont u think so guys ?

No, they will probably just stop working.

---

### Post by eldragon on 2010-05-06
> **natravis said:**
> 
I'm not sure about the double quotes there or not.

they will definately break something. 
if double quoting. use " b 'a' "

---

### Post by docfreed on 2010-05-06
OK, Installed Toshutils - now how do I use it?  I can see that the program is installed but I don't see anywhere to access it

---

### Post by suncanoe on 2010-05-08
> **bombel said:**
> The same problem on HP 4710s.Please help.

The same problem on HP 6530s

---

### Post by suncanoe on 2010-05-12
> **suncanoe said:**
> The same problem on HP 6530s

this is the infomation of acpi on my laptop

$acpi -t
Thermal 0: ok, 50.0 degrees C
Thermal 1: ok, 29.8 degrees C
Thermal 2: ok, 47.0 degrees C
Thermal 3: ok, 47.0 degrees C
Thermal 4: ok, 49.0 degrees C


But, fan is always running. what's the promble?
who can help me?

---

### Post by hovrashko on 2010-10-14
same here, Toshiba Satellite l505-S69

tried everything, above (editing grub, installing Toshiba Utills e.t.c)

does anybody knows how to remedy this BIG ubuntu issue? :confused::confused::confused:

Regards, :(

---

### Post by hovrashko on 2010-10-28
anybody?????

---

