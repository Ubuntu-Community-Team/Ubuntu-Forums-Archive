---
title: "Toshiba Satellite fan issue"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by DarkLoad on 2011-02-11
I recently installed Ubuntu 10.10 via WUBI on my Toshiba Satellite L505D-S9565, and I've had few issues except one: the laptop's fan does not run for any reason. I've talked back and forth with a few others and read some posts on similar issues. 

Here's what I do know:

1.) I looked at /proc/acpi/thermal_zone/*/trip_points . The only option for * there is THZN. This is the output:

critical (S5):           105 C
passive (forced):<not set>

2.) Trying to get ideas from another post I ran pwmconfig. This was the result:

# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

**/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed**

3.) $ sensors returns:
acpitz-virtual-0
Adapter: Virtual device
temp1:       +39.0°C  (crit = +105.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +47.5°C  (high = +70.0°C)    

As you can see there's not any data for my fan. (The temperature sensors seem to work fine, at least, which is a relief.)

However, /proc/acpi/fan/FAN1 is valid. There is one file in FAN1, state. sudo cat /proc/acpi/FAN1/state returned:
 status:                  off

I think the problem may be that whatever bit of software that's in charge of cooling has no idea how to control my fan at all, even though it does recognize that the fan exists. I tried to carry out one of the posts regarding how to change trip-points but the package it mentioned does not seem to exist any more, so I'm pretty much stymied at this point.

This wouldn't be a major problem except that I have to have a large fan  meant for cooling humans pointed at my laptop at all times. So currently  it is a desktop that I can put into my lap if I don't mind being  chilly. If I boot into Windows Vista, which currently only works in Safe Mode anyway ](*,) , the fan does turn on, although it would be doing a lot better job of it if I could get the thrice-cursed thing to boot normally. 

And despite the above infodump I'm really not sure what I'm doing beyond those few things, so if I ask a really dopey question...well, this IS the beginner forum.

Any help is appreciated.

---

### Post by robsoles on 2011-02-11
Welcome to UF.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1586606](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1586606) may be worth a look to you, just say how much it doesn't help and I'll try harder ;)


Checkout xsensors in the Ubuntu Software Centre - just an easier to read GUI wrapper for sensors if I didn't sleep through the bits I read.

---

### Post by DarkLoad on 2011-02-11
xsensors is nice, and thanks for pointing that out, but readability was not my concern. I expected from a post I read for there to be something returned from running sensors (or xsensors) regarding my fan, and there isn't. I know it's there, and on some level so does the software, but not enough to do anything.

[LEFT]That link to that thread seems to be highly dell-specific and doesn't refer to anything I can actually understand or use. It links to a bug report, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337 ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337") that seems to almost apply to my situation, except I'm nearly certain  given the above information that it wouldn't run the fan even if I  started warm, as that seems to be an issue with the temperature sensors. 
[/LEFT]
[ ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337")

---

### Post by robsoles on 2011-02-11
Sorry, should have looked at the results I got for my initial search and added 'toshiba' to it :roll:

How about dino99's advice from: [http://ubuntuforums.org/showthread.php?t=1473317](http://ubuntuforums.org/showthread.php?t=1473317) ?

---

### Post by DarkLoad on 2011-02-11
Oh, excellent. I'll try that and get back to you on whether or not it worked and what did the trick.

---

### Post by DarkLoad on 2011-02-12
Um. Well, I think it's working? I changed the setting in /etc/default/grub from

GRUB_CMDLINE_LINUX=""

to GRUB_CMDLINE_LINUX="acpi.power_nocheck=0"

as suggested in the post you linked to previously.
The problem is it's running very quietly, so I'm not sure if there was an actual change or if I'm just imagining it, and none of the other things have changed - no trip points, and it's still not able to tell my fan is there if I'm looking at xsensors. It may still overheat in the future, but it's a laptop, so that's a given anyway - but I'm not sure if the fan's going to contribute much.

Might it be possible (if costly) to take it in and get a fan installed that Linux will be able to work with properly?

edit: I forgot to mention: /proc/acpi/fan/FAN1/state is still "off". I tried using the echo commands provided later in that same thread with dino99's suggestions, but they didn't seem to do anything.

---

### Post by robsoles on 2011-02-12
> **DarkLoad said:**
> Um. Well, I think it's working? I changed the setting in /etc/default/grub from

GRUB_CMDLINE_LINUX=""

to GRUB_CMDLINE_LINUX="acpi.power_nocheck=0"

as suggested in the post you linked to previously.
The problem is it's running very quietly, so I'm not sure if there was an actual change or if I'm just imagining it, and none of the other things have changed - no trip points, and it's still not able to tell my fan is there if I'm looking at xsensors. It may still overheat in the future, but it's a laptop, so that's a given anyway - but I'm not sure if the fan's going to contribute much.

Might it be possible (if costly) to take it in and get a fan installed that Linux will be able to work with properly?

In reverse order:
It belongs to the Motherboard so I don't think there is a tenable solution where you can have something replaced on it to make it more compatible with Linux.

Right click a panel and choose 'add to panel', look for 'hardware sensors monitor' and add it up to three times: right click the first one and set it to monitor CPU temp, right click second one and set it to monitor GPU temp and right click last one and set it to GPU temp. Now you *should* have the three main temperatures to worry about in a computer on fairly well continuous display while you are computing - if suspicious then don't leave it running unattended more than you have to.

Very glad to hear the fan is moving, there is at least one way to override it and make it go faster, that I at least barely know of, but lets wait till you can confirm the way the system will run the fan now doesn't keep the CPU at a reasonable temperature.

---

### Post by DarkLoad on 2011-02-12
> **robsoles said:**
> 
Right click a panel and choose 'add to panel', look for 'hardware sensors monitor' and add it up to three times: right click the first one and set it to monitor CPU temp, right click second one and set it to monitor GPU temp and right click last one and set it to GPU temp. Now you *should* have the three main temperatures to worry about in a computer on fairly well continuous display while you are computing - if suspicious then don't leave it running unattended more than you have to.


I don't see that option anywhere (hardware sensors monitor). Do I need to install something else for that?

> 
Very glad to hear the fan is moving, there is at least one way to override it and make it go faster, that I at least barely know of, but lets wait till you can confirm the way the system will run the fan now doesn't keep the CPU at a reasonable temperature.
Unfortunately I realized later that if I actually put the darn thing under any amount of stress (to test it I started Minecraft and tried to play a bit) it doesn't increase speed at all. It got up to 80 C before I gave up on it. It is entirely too slow and doesn't really cool anything at all.

---

### Post by robsoles on 2011-02-12
Sorry```
sudo apt-get install sensors-applet
```should get it into your 'add to panel' dialog.

Does this help you with fan speed: [http://ubuntuforums.org/showthread.php?t=1456796](http://ubuntuforums.org/showthread.php?t=1456796)

---

### Post by DarkLoad on 2011-02-12
Excellent, the sensors are now shown in my panel.

But I have no idea how to implement any of what they are talking about in that post. pwmconfig, as stated before, can't find anything, and I've been on my BIOS screen enough times to know that it's not going to have an option for fan control. It's pretty basic. When I look through /etc/ I don't see a fancontrol. Is this something else I'd have to install? I think we're very near something that would help me but I don't know what that would be.

EDIT: Huh, this is interesting. I already have fancontrol installed but there's no config file in /etc/fancontrol. When I try to run it, it tells me "Error: Can't read configuration file."

---

### Post by robsoles on 2011-02-12
Lots of binaries come with a config file dependency that isn't automatically created by the installer but instead a 'template' of the file can be found either in it's documentation or it's binaries directories.

Have a squiz at 'man fancontrol' (pop it into terminal) and perhaps [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737) can help even though it is pretty old - Google returned it as the most relevant result to [www.google.com/search?q=howto+setup+fancontrol+in+ubuntu](www.google.com/search?q=howto+setup+fancontrol+in+ubuntu) when I tried it here.

---

### Post by DarkLoad on 2011-02-12
Oh, hey, I've seen that link before - but I never got down to where it mentioned the bug in pwmconfig. It sounds rather familiar! I'll work on it.

EDIT: The bug it talks about? I can't find that line it mentions at all. This only applied to "Hoary" and I'm running the latest version. So I seem to not have made any progress at all.

---

### Post by robsoles on 2011-02-12
Yes, that stuff is old and I much more linked to it regarding deriving a configuration for fancontrol - not so much regarding whatever else is discussed in that thread.

Please read the first post in that thread more carefully, look at what is being said and be aware that if it says stuff like> **remmelt said:**
> ...

**Patching pwmconfig** [COLOR=red]This is no longer needed if you run Dapper! Go to the next step unless you're running Hoary.[/COLOR]

...
Then it is old news and Lucid and later releases are not likely to be suffering what Hoary was if they fixed it by the time of the Dapper release.

From [www.google.com/search?q=fancontrol+howto+for+Lucid](www.google.com/search?q=fancontrol+howto+for+Lucid) the impression could be gained, from a couple of threads and posts, that fancontrol just won't work in Lucid (therefore probably not in later releases either) and a suggestion I derive from one thread is to search Synaptic Package Manager for 'toshiba fan control' - two entries in my list when I do it, maybe one or both of those can help you?

---

### Post by DarkLoad on 2011-02-12
There are three packages related to Toshiba hardware in Synaptic.

Toshset currently seems the most promising, but when I try to run it, it gives me "required kernel toshiba support not enabled." How do I enable it?

EDIT: Sorry I'm being so vague and just moving so quickly to reply before considering what I need to say. /usr/share/doc/toshset/README.Debian says:

In /usr/share/doc/toshset/toshiba-acpi you can find the experimental version of
the toshiba_acpi kernel module. You can run 'sh install.sh' for compiling and
install the module. (Ubuntu users don't need it)

I don't believe that last line for a minute, though.

---

### Post by robsoles on 2011-02-13
What an endless series of traps and run offs!

Have you checked if there is an update for your BIOS from Toshiba? Some clues in results to searches I have tried suggest it helps a great deal if your BIOS is the latest for your machine.

What do you get back from terminal if you try the following commands (supposed to supply 'required kernel toshiba support' but mixed reactions in search results so...)```
sudo modprobe toshiba_acpi
sudo modprobe toshiba
```

If nothing seems wrong about the terminal's response to those commands then it's worth trying toshset again - I'm not positive but I don't think this requires a restart...

The results of [www.google.com/search?q=how+to+enable+kernel+toshiba+support+in+ubuntu](www.google.com/search?q=how+to+enable+kernel+toshiba+support+in+ubuntu) don't look super encouraging as far as the first one goes, have a squiz: [http://ubuntuforums.org/showthread.php?t=737397](http://ubuntuforums.org/showthread.php?t=737397)

---

### Post by robsoles on 2011-02-13
> **DarkLoad said:**
> ...

EDIT: Sorry I'm being so vague and just moving so quickly to reply before considering what I need to say. /usr/share/doc/toshset/README.Debian says:

In /usr/share/doc/toshset/toshiba-acpi you can find the experimental version of
the toshiba_acpi kernel module. You can run 'sh install.sh' for compiling and
install the module. (Ubuntu users don't need it)

I don't believe that last line for a minute, though.

Sorry I didn't refresh the page before posting before.

If modprobe for toshiba-acpi doesn't work with 'no such' type error then try```
cd /usr/share/doc/toshiba-acpi
sh install.sh
```
If it bombs talking about permissions then try ```
sudo ./install.sh
``` straight-away, if that bombs maybe I can help with the response from terminal (error message details).

---

### Post by HermanAB on 2011-02-13
Howdy,

I have a similar Toshiba laptop.

There is no proper software solution.  You can add the kernel parameter: acpi="Linux" to the kernel boot string in /boot/grub/menu.lst, then the fan will sometimes work.

The best hardware solution is to rewire the fan so that it always runs at medium speed.  Doing so is very difficult.  You either need to totally disassemble the laptop, or use a Dremel to cut an opening in the bottom of the case in order to get to the fan.  Another solution is to buy a large 'laptop cooling tray' and put the machine on top of that, but the airflow through the machine will likely still be inadequate.

The best solution is to sell the Toshiba laptop on Ebay and buy a Lenovo laptop.

---

### Post by RJ12 on 2011-02-13
I have a Toshiba Satellite L455D-S5976 and found that appending this to the boot options makes the fan work better

```
acpi_os=!Windows 2006
```

Which I think is suppose to make the BIOS think your using Windows. I also got one of those cooling dock things and I haven't had any problems since.

---

### Post by DarkLoad on 2011-02-13
```

/usr/share/doc/toshset/toshiba-acpi$ sh install.sh
sh: Can't open install.sh

```

```

/usr/share/doc/toshset/toshiba-acpi$ sudo ./install.sh
sudo: ./install.sh: command not found

```

As a side note:
```

ls /usr/share/doc/toshset/toshiba-acpi
2.6.26  2.6.28

```

@RJ12: What file is that that I should add that to to try it?

---

### Post by RJ12 on 2011-02-13
> **DarkLoad said:**
> ```

/usr/share/doc/toshset/toshiba-acpi$ sh install.sh
sh: Can't open install.sh

```

```

/usr/share/doc/toshset/toshiba-acpi$ sudo ./install.sh
sudo: ./install.sh: command not found

```

As a side note:
```

ls /usr/share/doc/toshset/toshiba-acpi
2.6.26  2.6.28

```

@RJ12: What file is that that I should add that to to try it?

in /etc/default/grub change

GRUB_CMDLINE_LINUX=""

to GRUB_CMDLINE_LINUX="acpi_os=!Windows 2006"

---

### Post by DarkLoad on 2011-02-13
RJ12: Fan is running a little bit more but it's not going to be sufficient to keep this thing cool, I don't think. It has a prior chronic overheating problem that I admittedly need to resolve soon regardless of whether the fan can run at full speed or not.

HermanAB: The file you directed me at does not appear to exist. Will it hurt anything to create it?

EDIT: More to the point, will it HELP anything?

---

### Post by robsoles on 2011-02-13
> **DarkLoad said:**
> ```

/usr/share/doc/toshset/toshiba-acpi$ sh install.sh
sh: Can't open install.sh

``````

/usr/share/doc/toshset/toshiba-acpi$ sudo ./install.sh
sudo: ./install.sh: command not found

```As a side note:
```

ls /usr/share/doc/toshset/toshiba-acpi
**2.6.26  2.6.28**

```@RJ12: What file is that that I should add that to to try it?

Those are obviously folder names of version numbers - the instructions you posted before predate a second version

Try: ```
cd /usr/share/doc/toshset/toshiba-acpi/2.6.28
ls
```
If there is a blasted install.sh file then ```
./install.sh
```
If there are more directories then pick one and 'cd' into it, 'ls' again, got an install.sh?

Alternatively: ```
cd /usr/share/doc/toshset/toshiba-acpi/2.6.28
find -name install.sh
```will 'dig' it up if it exists.

---

### Post by DarkLoad on 2011-02-13
I managed to get it to start installing, and then, just as it was finishing...

```

ldconfig deferred processing now taking place
make -C /lib/modules/2.6.35-25-generic/build M=/usr/share/doc/toshset/toshiba-acpi/2.6.28 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
make[2]: *** No rule to make target `/usr/share/doc/toshset/toshiba-acpi/2.6.28/toshiba_acpi.c', needed by `/usr/share/doc/toshset/toshiba-acpi/2.6.28/toshiba_acpi.o'.  Stop.
make[1]: *** [_module_/usr/share/doc/toshset/toshiba-acpi/2.6.28] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [all] Error 2
cp: cannot stat `toshiba_acpi.ko': No such file or directory

```

You wouldn't happen to have any input on HermanAB's software advice? (Oh and from now on can we pretend we're handcuffed to our machines so that we remember "sell it and get a different one" is really a non-solution?)

---

### Post by robsoles on 2011-02-13
> **DarkLoad said:**
> I managed to get it to start installing, and then, just as it was finishing...

```

ldconfig deferred processing now taking place
make -C /lib/modules/2.6.35-25-generic/build M=/usr/share/doc/toshset/toshiba-acpi/2.6.28 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
make[2]: *** No rule to make target `/usr/share/doc/toshset/toshiba-acpi/2.6.28/toshiba_acpi.c', needed by `/usr/share/doc/toshset/toshiba-acpi/2.6.28/toshiba_acpi.o'.  Stop.
make[1]: *** [_module_/usr/share/doc/toshset/toshiba-acpi/2.6.28] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [all] Error 2
cp: cannot stat `toshiba_acpi.ko': No such file or directory

```

You wouldn't happen to have any input on HermanAB's software advice? (Oh and from now on can we pretend we're handcuffed to our machines so that we remember "sell it and get a different one" is really a non-solution?)

Wasn't it HermanAB's advice to sell it and get a different one? :p (just mucking around, this is all to serious and bogged down!)


Please try the same thing in the other directory, ie., you just did it in 2.6.28 - please try it in 2.6.26, when/if that fails we've exhausted the possibilities of that method and we should definitely move on.

My next stop will be HermanAB's advice regarding /boot/grub/menu.lst but I will probably be asking you to post your original file and accept changes via an attachment rather than just describing what to do and hoping you can nail it correctly.

---

### Post by Guilden_NL on 2011-02-13
For a short term workaround, have you considered buying a notebook cooler?  I bought a Zalman ZM-NC2000 Notebook Cooler for an HP EliteBook 8740w Mobile Workstation that has plenty of onboard cooling, but figured that a little help from the outside wouldn't hurt either.

There are plenty of much cheaper versions, I saw one for under US$10 this week at a computer enthusiast store.

It doesn't correct your root cause, but it could buy you some time and I think you'll like having one long term anyway.

---

### Post by DarkLoad on 2011-02-13
Whatever I buy has to be within walking distance, and the only store in range is Office Depot, which offers them for about $20-30 USD. I don't really have the money for it and my mother used to buy these for her laptop when she had overheating problems - they break pretty easily. I'll consider it, though.

I'll try the other - it didn't cross my mind to, sorry! And the file he mentioned did not exist. I can create it but that doesn't mean it will work. 

EDIT: Coughed up pretty much the same error, but sooner, since everything else had already been installed as the latest version. Still doesn't work.

---

### Post by heyho on 2011-02-13
Nothing to add of any help I'm afraid, just to say that this would explain the overheating problems I had with any 'buntu on my Toshiba A60.  The fan sometimes ran, and sometimes didn't.

Recently put XP back on and no problems since.

---

### Post by robsoles on 2011-02-13
> **DarkLoad said:**
> Whatever I buy has to be within walking distance, and the only store in range is Office Depot, which offers them for about $20-30 USD. I don't really have the money for it and my mother used to buy these for her laptop when she had overheating problems - they break pretty easily. I'll consider it, though.

I'll try the other - it didn't cross my mind to, sorry! And the file he mentioned did not exist. I can create it but that doesn't mean it will work. 

EDIT: Coughed up pretty much the same error, but sooner, since everything else had already been installed as the latest version. Still doesn't work.

/boot/grub/menu.lst appears deprecated (no longer used) so the direct application of HermanAB's advice doesn't seem applicable. 

/etc/default/grub does exist, here is a fairly vanilla copy:```
# **If you change this file, run 'update-grub' afterwards to update**
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

So maybe we can try a near match to HermanAB's suggestion into the GRUB_CMDLINE_LINUX="" line like this:
```
GRUB_CMDLINE_LINUX="acpi=Linux"
```I am probably wrong but the worst it will do is make you boot from LiveCD and remove the string. Note the bit of the 'vanilla' one I have made bold -```
sudo update-grub
```Is required to make changes come into effect - Restart is also required.

To get such a file open in gedit ```
gksudo gedit /etc/default/grub
```will do.

If that fails, seems crazy to me but let's try RJ12's advice (no offense intended RJ12, just doesn't seem right to mention Windows on these holy grounds!) so```
GRUB_CMDLINE_LINUX="acpi_os=!Windows 2006"
``` to replace the other attempt followed by the 'update-grub' and a restart again.

---

### Post by DarkLoad on 2011-02-13
I've done this before, don't worry. Kinda doubt it will cause problems. Will post again with results.

---

### Post by DarkLoad on 2011-02-13
Well, it didn't hurt anything, but it didn't help much either. I'm at a bit of a loss as to what to try next.

EDIT: Any chance of there being an existing program to play a system sound as an alarm when one of the sensors reaches a given temp? That might mitigate the situation a bit.

---

### Post by robsoles on 2011-02-14
Couldn't find valid info on setting an audible alarm but I was reading [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto) when I suddenly did this: :roll:

Have you tried```
sudo sensors-detect
```in terminal?

If not: Answer yes to all scans - should be fine, if it 'bombs' after selecting yes to a particular scan then notate that scan and answer no to it next time till it makes it through.

Sorry for posting in haste, do whatever it was that got the fan to go 'automatically' at all (albeit too slow) and reboot when this completes.

Any better?

---

### Post by DarkLoad on 2011-02-14
```

# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: TOSHIBA Satellite L505D (laptop)
# Board: TOSHIBA Portable PC

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           Success!
    (driver `k10temp')
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xfc11
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes  
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `k10temp' (autoloaded):
  * Chip `AMD Family 11h thermal sensors' (confidence: 9)

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK

```

The best one - 'best' not counting for much, they're all pretty weak -  seemed to be RJ12's modification to the grub file. I'll put it back that way and see what happens.

---

### Post by DarkLoad on 2011-02-14
It seems better than before, but I don't think it's any better than it has been. Certainly more so than HermanAB's suggestion - doubtful that it's even possible to implement that correctly any more. Barring the hardware suggestions of wiring it up to be constantly on, which seems unnecessary and potentially harmful, I would think the best solution would probably be that cooling tray, as much as it irks me to use one.

Any more suggestions are always appreciated - hate to leave something at "well it just doesn't work and there's nothing that can be done for it".

---

### Post by boxy333 on 2011-03-23
My Toshiba P100 is the same. The GPU fan ceased after an update to 10.10 about the time this thread got started.

There are a load of potential fixes and a load of affected people looking at these forums via Windows in it's many guises, hoping to find a way of running Ubuntu without frying their machines.

Is there an 'undo' on my last system update to get things back working the easy way? Will there be an Ubuntu update soon to unfix the fix? If I do boot up Ubuntu to check for an update, will my laptop burn before the update completes?

Horrible show stopper for Linux for me, this. To think that thousands of Ubuntu users' computers are just quietly disabling their cooling systems without warning.

---

### Post by miahotrod on 2011-04-24
I subscribed to this post I have a Toshiba Satellite A215-S4807 I have tried toshutils, toshset and even fnfxd. with toshutils, toshset I get required kernel toshiba support not enabled. My fan works but it runs much slower than when I boot to my vista partition. I have looked else where but I have not found a solution as yet if i do i will post it here. oh ya as for fnfxd I now have my hot keys working but it says it has fan controls but i could not find documentation and the forum was down for it so i do not know if there is a additional hot key for fan speed like synaptic manager descriptions indicated

---

### Post by pierreu1 on 2012-08-20
I ran into this problem too. I updated to Pangolin Penguin, but that did not clear any problems.

When I upgraded I had all kinds of error messages concerning linux-image 3.2.0.29-generic and others (15 to 20) giving error exit status 2 and 1 ...

Not sure what to do!

---

### Post by overdrank on 2012-08-20
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

