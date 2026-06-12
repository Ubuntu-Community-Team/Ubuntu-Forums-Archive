---
title: "custom kernel build"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by DGINSD on 2011-07-07
I've decided to try out building my own custon kernel, mostly for learning purposes. I must say wow hell of alot of options to go through and select is there any way to auto select just the options you really need, then go back and grab the extras needed for your perifirals?

---

### Post by Toz on 2011-07-07
make localmodconfig?

From **make help**
> localmodconfig  - Update current config disabling modules not loaded


See also: [http://kernelnewbies.org/Linux_2_6_32#head-11f54cdac41ad6150ef817fd68597554d9d05a5f]("http://kernelnewbies.org/Linux_2_6_32#head-11f54cdac41ad6150ef817fd68597554d9d05a5f")

You need to keep in mind that this will also disable those devices that you may use occasionally that are not currently plugged in/attached whose drivers are built as modules.

---

### Post by DGINSD on 2011-07-09
Thanks for the tip. Its hard to find info that's suitable for beginners here's the tutorial I'm following these instructions; [[COLOR="Blue"]http://blog.avirtualhome.com[/COLOR]]("http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10-10-maverick-kernel/") but where in the process should I enter that command you gave me to weed out all the un-needed options. I mean perferably it would be before I use the "debian/rules editconfigs" command, so i could then go in and add all the extra options I want for extra equipment and what not, but how and where to use it. my next issue adds even more confusion?

The other thing that has me frustrated and stumped is the instructions have you use this "[COLOR="Red"]git tag -l | sort -V[/COLOR]" command which pulls up a list of all these available kernels in the source package, it yields this output;

> david@david-Inspiron-1150:~/Linux/source$ git tag -l | sort -V
Linaro-2.6.35-1000.2
Linaro-2.6.35-1000.3
Linaro-2.6.35-1001.5
Linaro-2.6.35-1002.6
Linaro-2.6.35-1003.7
Linaro-2.6.35-1004.8
Linaro-2.6.35-1004.9
Linaro-2.6.35-1005.10
Linaro-2.6.35-1006.11
Linaro-2.6.35-1006.12
Linaro-2.6.35-1007.13
Linaro-2.6.35-1008.14
Linaro-2.6.35-1008.15
Linaro-2.6.35-1010.17
Ubuntu-2.6.33-0.0
Ubuntu-2.6.33-lucid-sync
Ubuntu-2.6.34-1.1
Ubuntu-2.6.34-1.2
Ubuntu-2.6.34-1.3
Ubuntu-2.6.34-1.4
Ubuntu-2.6.34-1.5
Ubuntu-2.6.34-1.6
Ubuntu-2.6.34-2.7
Ubuntu-2.6.34-2.8
Ubuntu-2.6.34-2.9
Ubuntu-2.6.34-3.10
Ubuntu-2.6.34-4.11
Ubuntu-2.6.34-5.12
Ubuntu-2.6.34-5.13
Ubuntu-2.6.34-5.14
Ubuntu-2.6.34-900.1
Ubuntu-2.6.34-901.2
Ubuntu-2.6.34-901.3
Ubuntu-2.6.34-901.4
Ubuntu-2.6.34-901.5
Ubuntu-2.6.34-902.6
Ubuntu-2.6.34-903.7
Ubuntu-2.6.35-1.1
Ubuntu-2.6.35-2.2
Ubuntu-2.6.35-2.3
Ubuntu-2.6.35-3.4
Ubuntu-2.6.35-4.5
Ubuntu-2.6.35-5.6
Ubuntu-2.6.35-6.7
Ubuntu-2.6.35-6.8
Ubuntu-2.6.35-6.9
Ubuntu-2.6.35-7.10
Ubuntu-2.6.35-7.11
Ubuntu-2.6.35-7.12
Ubuntu-2.6.35-8.13
Ubuntu-2.6.35-9.14
Ubuntu-2.6.35-10.15
Ubuntu-2.6.35-11.16
Ubuntu-2.6.35-12.17
Ubuntu-2.6.35-13.18
Ubuntu-2.6.35-14.19
Ubuntu-2.6.35-14.20
Ubuntu-2.6.35-15.21
Ubuntu-2.6.35-16.22
Ubuntu-2.6.35-17.23
Ubuntu-2.6.35-18.24
Ubuntu-2.6.35-19.25
Ubuntu-2.6.35-19.26
Ubuntu-2.6.35-19.27
Ubuntu-2.6.35-19.28
Ubuntu-2.6.35-20.29
Ubuntu-2.6.35-21.30
Ubuntu-2.6.35-21.31
Ubuntu-2.6.35-22.32
Ubuntu-2.6.35-22.33
Ubuntu-2.6.35-22.34
Ubuntu-2.6.35-22.35
Ubuntu-2.6.35-23.36
Ubuntu-2.6.35-23.37
Ubuntu-2.6.35-23.38
Ubuntu-2.6.35-23.39
Ubuntu-2.6.35-23.40
Ubuntu-2.6.35-23.41
Ubuntu-2.6.35-24.42
Ubuntu-2.6.35-25.43
Ubuntu-2.6.35-25.44
Ubuntu-2.6.35-26.45
Ubuntu-2.6.35-26.46
Ubuntu-2.6.35-27.47
Ubuntu-2.6.35-27.48
Ubuntu-2.6.35-28.49
Ubuntu-2.6.35-28.50
Ubuntu-2.6.35-29.51
Ubuntu-2.6.35-30.52
Ubuntu-2.6.35-30.53
Ubuntu-2.6.35-30.54
Ubuntu-2.6.35-30.55
Ubuntu-2.6.35-903.8
Ubuntu-2.6.35-903.9
Ubuntu-2.6.35-903.10
Ubuntu-2.6.35-903.11
Ubuntu-2.6.35-903.12
Ubuntu-2.6.35-903.13
Ubuntu-2.6.35-903.14
Ubuntu-2.6.35-903.15
Ubuntu-2.6.35-903.16
Ubuntu-2.6.35-903.17
Ubuntu-2.6.35-903.18
Ubuntu-2.6.35-903.19
Ubuntu-2.6.35-903.20
Ubuntu-2.6.35-903.21
Ubuntu-2.6.35-903.22
Ubuntu-M-base
Ubuntu-N-base
Ubuntu-N-sync
Ubuntu-mvl-dove-2.6.32-409.25
Ubuntu-mvl-dove-2.6.32-410.26
Ubuntu-mvl-dove-2.6.32-410.27
Ubuntu-mvl-dove-2.6.32-412.28
Ubuntu-mvl-dove-2.6.32-414.30
Ubuntu-mvl-dove-2.6.32-415.32
Ubuntu-mvl-dove-2.6.32-416.33
Ubuntu-mvl-dove-2.6.32-417.34
Ubuntu-pre-2.6.33-rebase
v2.6.35


each of which also has it's flavor branches as well, how can one tell which version to use? The flavor options aren't that difficult, for the most part pick your architecture i386 generic to base it off of, but which version, how do you get information on which one best suits your needs? 

Then when you get into doing editconfigs the help info gives you some idea of what the options are for but how can you know if there's certain thing on your machine eeprom IC2 board level chips how could anyone ever find info about that?

---

### Post by Toz on 2011-07-09
Yes, I would probably run it before editconfigs as well. As for the kernel versions available, what kernel version are you currently running? As for myself, I stick with the Ubuntu-* kernels and use the latest prior to 900 series listed. In the case of your list, I'd use **Ubuntu-2.6.35-30.55**.

As for info about the specific kernel parameters and their functions, I could never find anything definitive - most of the work is done via googling.

---

### Post by DGINSD on 2011-07-09
yeah I believe the 2.6.30-35.55 was the one I tried the first time. The one I'm currently running is 2.6.30-35. So I guess I was on the right track.

How would I script a command to used make "localmodconfig." on my newly created branch. I guess I'd have to cd to where the branch .config is located but there will also be .configs for the other branches as well how woulds I specify?

Goggling all the options I am unfamiliar with could take a really long time, there could be a whole other kernel out by then. I guess if I can get the "make localmodconfig" to work should be easy to add the rest of the options needed.

---

### Post by DGINSD on 2011-07-10
Even more how can one get the nitty gritty details of my machine, beyond what limited info Dells web site gives. For example the models number of the motherboard, so I could further google that and find more details.

---

### Post by Toz on 2011-07-10
Here are a few commands that you can try:
```

hwinfo (hwinfo --short)
sudo lshw (sudo lshw -html | w3m -T text/html) 
sudo dmidecode
sudo lspci -vnn
sudo lsusb -v
sudo lspcmcia -v
```

You can also directly query the files in /proc. **hardinfo** is also a nice gui program (find it in the software centre).

---

### Post by DGINSD on 2011-07-13
excellent I'll  give some of those a whirl tonight, thank you.

I got a question about modules, if I add certain kernel options as modules ones I'm not sure of will they automatically be used if they are needed or do I have to individually load them?  For example there are options for board level components eeproms I2C and what not things that in my opinion the only person that would know is the boards designer. If I set those as modules will they be automatically loaded if needed?

Next question if theres something I know I need  for example the b44 and b43 drivers, better to build those in or st them up as modules. The kerneel I'm building is only for my machine and I'm tring to streamline it as much as possible, I gusss my question is do modules slow down the kernel any?

Next up the search function in "make editconfig" after you search for something and find it is there any way to jump to that item you searched for to either select or de-select it?

---

### Post by DGINSD on 2011-07-13
Duplicate Post

---

### Post by DGINSD on 2011-07-16
All right I'm working through editing my kernel build configs using debian/rules editconfigs, there's definately a lot more than one sessions worth of options to go through so I save my changes, exit the configuration editor, and decline to edit any of the other branches to continue my work later. The problem is the last time I did this I got an error which was as follows:

```
david@david-Inspiron-1150:~/Linux/source$ debian/rules editconfigs
dh_testdir
/bin/bash -e debian/scripts/misc/kernelconfig editconfig
Do you want to edit config: amd64/config.flavour.generic? [Y/n] n
Do you want to edit config: amd64/config.flavour.server? [Y/n] n
Do you want to edit config: amd64/config.flavour.virtual? [Y/n] n
Running splitconfig.pl for amd64

Reading config's ...
  processing config.flavour.virtual ... done.
  processing config.flavour.generic ... done.
  processing config.common.amd64 ... done.
  processing config.flavour.server ... done.

Merging lists ... 
   processing config.flavour.server ... done.
   processing config.common.amd64 ... done.
   processing config.flavour.generic ... done.
   processing config.flavour.virtual ... done.

Creating common config ... done.

Creating stub configs ...
  processing config.flavour.server ... done.
  processing config.common.amd64 ... done.
  processing config.flavour.generic ... done.
  processing config.flavour.virtual ... done.
Do you want to edit config: i386/config.flavour.dell_1150? [Y/n] y
make[1]: Entering directory `/home/david/Linux/source'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  GEN     /home/david/Linux/source/build/Makefile
  HOSTCC  scripts/kconfig/conf.o
/home/david/Linux/source/scripts/kconfig/conf.c: In function ‘conf_askvalue’:
/home/david/Linux/source/scripts/kconfig/conf.c:105: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
/home/david/Linux/source/scripts/kconfig/conf.c: In function ‘conf_choice’:
/home/david/Linux/source/scripts/kconfig/conf.c:307: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
  HOSTCC  scripts/kconfig/lxdialog/inputbox.o
  HOSTCC  scripts/kconfig/lxdialog/menubox.o
  HOSTCC  scripts/kconfig/lxdialog/textbox.o
  HOSTCC  scripts/kconfig/lxdialog/util.o
  HOSTCC  scripts/kconfig/lxdialog/yesno.o
  HOSTCC  scripts/kconfig/mconf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/mconf
scripts/kconfig/mconf arch/x86/Kconfig
#
# configuration written to .config
#


*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

make[1]: Leaving directory `/home/david/Linux/source'
Do you want to edit config: i386/config.flavour.generic? [Y/n] n
Do you want to edit config: i386/config.flavour.generic-pae? [Y/n] n
Do you want to edit config: i386/config.flavour.virtual? [Y/n] n
Running splitconfig.pl for i386

Reading config's ...
  processing config.flavour.virtual ... done.
  processing config.flavour.dell_1150 ... done.
  processing config.flavour.generic-pae ... done.
  processing config.flavour.generic ... done.
  processing config.common.i386 ... done.

Merging lists ... 
   processing config.common.i386 ... done.
   processing config.flavour.generic ... done.
   processing config.flavour.dell_1150 ... done.
   processing config.flavour.virtual ... done.
   processing config.flavour.generic-pae ... done.

Creating common config ... done.

Creating stub configs ...
  processing config.common.i386 ... done.
  processing config.flavour.generic ... done.
  processing config.flavour.dell_1150 ... done.
  processing config.flavour.virtual ... done.
  processing config.flavour.generic-pae ... done.
Do you want to edit config: armel/config.flavour.omap? [Y/n] n
Do you want to edit config: armel/config.flavour.versatile? [Y/n] n
Running splitconfig.pl for armel

Reading config's ...
  processing config.common.armel ... done.
  processing config.flavour.omap ... done.
  processing config.flavour.versatile ... done.

Merging lists ... 
   processing config.common.armel ... done.
   processing config.flavour.omap ... done.
   processing config.flavour.versatile ... done.

Creating common config ... done.

Creating stub configs ...
  processing config.common.armel ... done.
  processing config.flavour.omap ... done.
  processing config.flavour.versatile ... done.
Reading config's ...
  processing config.common.amd64 ... done.
  processing config.common.armel ... done.
  processing config.common.i386 ... done.

Merging lists ... 
   processing config.common.i386 ... done.
   processing config.common.armel ... done.
   processing config.common.amd64 ... done.

Creating common config ... done.

Creating stub configs ...
  processing config.common.i386 ... done.
  processing config.common.armel ... done.
  processing config.common.amd64 ... done.

Running config-check for all configurations ...

check-config: /tmp/tmp.D84Ia4TOFF/CONFIGS/amd64-config.flavour.generic: loading config
check-config: /home/david/Linux/source/debian.master/config/enforce: loading checks
check-config: 28/28 checks passed -- exit 0
check-config: /tmp/tmp.D84Ia4TOFF/CONFIGS/amd64-config.flavour.server: loading config
check-config: /home/david/Linux/source/debian.master/config/enforce: loading checks
check-config: 28/28 checks passed -- exit 0
check-config: /tmp/tmp.D84Ia4TOFF/CONFIGS/amd64-config.flavour.virtual: loading config
check-config: /home/david/Linux/source/debian.master/config/enforce: loading checks
check-config: 28/28 checks passed -- exit 0
check-config: /tmp/tmp.D84Ia4TOFF/CONFIGS/i386-config.flavour.dell_1150: loading config
check-config: /home/david/Linux/source/debian.master/config/enforce: loading checks
[COLOR="Red"]check-config: FAIL: !exists CONFIG_CC_STACKPROTECTOR | value CONFIG_CC_STACKPROTECTOR y[/COLOR]
check-config: 27/28 checks passed -- exit 1
check-config: /tmp/tmp.D84Ia4TOFF/CONFIGS/i386-config.flavour.generic: loading config
check-config: /home/david/Linux/source/debian.master/config/enforce: loading checks
check-config: 28/28 checks passed -- exit 0
check-config: /tmp/tmp.D84Ia4TOFF/CONFIGS/i386-config.flavour.generic-pae: loading config
check-config: /home/david/Linux/source/debian.master/config/enforce: loading checks
check-config: 28/28 checks passed -- exit 0
check-config: /tmp/tmp.D84Ia4TOFF/CONFIGS/i386-config.flavour.virtual: loading config
check-config: /home/david/Linux/source/debian.master/config/enforce: loading checks
check-config: 28/28 checks passed -- exit 0
check-config: /tmp/tmp.D84Ia4TOFF/CONFIGS/armel-config.flavour.omap: loading config
check-config: /home/david/Linux/source/debian.master/config/enforce: loading checks
check-config: 28/28 checks passed -- exit 0
check-config: /tmp/tmp.D84Ia4TOFF/CONFIGS/armel-config.flavour.versatile: loading config
check-config: /home/david/Linux/source/debian.master/config/enforce: loading checks
check-config: 28/28 checks passed -- exit 0

*** ERROR: 1 config-check failures detected

rm -rf build

```

What would cause  this error and how would I go about correcting it? I searched [COLOR="Blue"]CONFIG_CC_STACKPROTECTOR[/COLOR] in the configuration editor and it comes up with this option; Enable -fstack-protector buffer overflow detection (EXPERIMENTAL). I had this option turned off.

---

### Post by DGINSD on 2011-07-23
I am kind of stumped and need a few questions answered, first with regaurds to the "lsmod" command, does this command list **all** of the modules loaded on my system?

Next is the configuration files listed in the boot directory accurate as to the build of the current kernel, for example there is a file in my boot directory called "config-2.6.35-30-generic" which is the current kernel I'm running. Does that configuration file along with the output of "lsmod" contain everything that's running on my current machine?

Next if the above is true I didn't find an entry for "CONFIG_BT" which is the general bluetooth kernel option which seemed kind of odd for a generic kernel. My machine has no Bluetooth devices so it's not really an issue but it brings up the question, does the generic kernel when set up on a machine get configured for the specific its being installed on.

Two areas I'm having a great deal of difficulty deciding on how to set up is Networking and Memory Technology Devices. With networking there's some options that the help files say are necessary for functionality  of IPtables which by my understanding is the basis of the Linux firewall (UFW), then after stating that it says if unsure say; no. So what are some options listed under networking that I need to be sure to keep active and what are some truly unnecessary options?

With Memory Technology Devices I think RAM, but in the above listed configuration file almost all the MTD entries are set up as modules but lsmod doesn't show any of them as being loaded. Is this standard RAM or does this refer to a different type of device?

Lastly with regards to power management I guess you can only run the APM or ACPI daemon which I believe currently I'm using the ACPI. I have a few minor power management issues which are a completely in accurate power icon it won't accurately depict if the charger is plugged in or not or how much of a charge the battery has, the other issue is the machine won't do anything upon closure of the lid no suspend hibernate (both work with software invocation) or display off. In my research I read that in some Dell laptop models this may be an issue caused  by using the operating systems ACPI software interface rather than the Bios' built in APM functions. I don't know enough about these systems to determine if this is true or possible nor could I find definitive information regarding my perticular model.

---

