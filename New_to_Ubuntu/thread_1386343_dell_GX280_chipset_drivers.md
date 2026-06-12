---
title: "dell GX280 chipset drivers"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by crazyavery4444 on 2010-01-20
does anybody know where i can find drivers for the chipset on a dell GX280? my resolution is stuck at 800x600 and my sound is horrid.

---

### Post by lykwydchykyn on 2010-01-20
Are you using onboard graphics?  The Intel graphics chips on the 280 have their drivers built into the kernel.  There's no separate driver download.

You might need to update your BIOS; I've had issues with this on various Dells that went away after a BIOS upgrade.  See this page for how to do this with Linux:

[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

I used to run Linux on a gx280 years ago, but I don't remember having problems with either sound or graphics.

---

### Post by crazyavery4444 on 2010-01-20
> **lykwydchykyn said:**
> Are you using onboard graphics?  The Intel graphics chips on the 280 have their drivers built into the kernel.  There's no separate driver download.

You might need to update your BIOS; I've had issues with this on various Dells that went away after a BIOS upgrade.  See this page for how to do this with Linux:

[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

I used to run Linux on a gx280 years ago, but I don't remember having problems with either sound or graphics.

Trying that right now, lets hope this works.

---

### Post by crazyavery4444 on 2010-01-20
> **lykwydchykyn said:**
> Are you using onboard graphics?  The Intel graphics chips on the 280 have their drivers built into the kernel.  There's no separate driver download.

You might need to update your BIOS; I've had issues with this on various Dells that went away after a BIOS upgrade.  See this page for how to do this with Linux:

[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

I used to run Linux on a gx280 years ago, but I don't remember having problems with either sound or graphics.

well no. when i try to use the update_firmware command i get the following error

Config Error: Plugin "firmware_addon_dell.dellbios" cannot be loaded: No module named firmware_addon_dell.dellbios

what i get out of that is ubuntu 9.10 cant detect my BIOS.

when i boot, under the dell logo it has BIOS revision A04, could that be the reason it cant find my BIOS? also just to clarify, that O is a zero

---

### Post by lykwydchykyn on 2010-01-21
> **crazyavery4444 said:**
> well no. when i try to use the update_firmware command i get the following error

Config Error: Plugin "firmware_addon_dell.dellbios" cannot be loaded: No module named firmware_addon_dell.dellbios

what i get out of that is ubuntu 9.10 cant detect my BIOS.

when i boot, under the dell logo it has BIOS revision A04, could that be the reason it cant find my BIOS? also just to clarify, that O is a zero

The newest BIOS listed in synaptic is A08.  There are two different gx280 packages listed, one tagged "0x0179" and one tagged "0x0197".  I couldn't tell you which one to install, I don't know the difference.

In any case, you need to install one or the other of those packages (system-bios-optiplex-gx280-<something>), then run the command "sudo dellBiosUpdate".  That should get it.

---

### Post by pricetech on 2010-01-21
Failing that, the GX280 BIOS is just over half a meg, plenty small enough to fit on a floppy.  You'll need a basic DOS or win9x boot floppy to copy it to.

I think the BIOS is indeed your problem though.

---

### Post by crazyavery4444 on 2010-01-21
> **lykwydchykyn said:**
> The newest BIOS listed in synaptic is A08.  There are two different gx280 packages listed, one tagged "0x0179" and one tagged "0x0197".  I couldn't tell you which one to install, I don't know the difference.

In any case, you need to install one or the other of those packages (system-bios-optiplex-gx280-<something>), then run the command "sudo dellBiosUpdate".  That should get it.
would i go about doing that through synaptic? or is there a terminal command to enter?

---

### Post by lykwydchykyn on 2010-01-21
> **crazyavery4444 said:**
> would i go about doing that through synaptic? or is there a terminal command to enter?

You can install the package either way, whatever you're comfortable with.

The "sudo dellBiosUpdate" command needs to be done at the terminal.

---

### Post by crazyavery4444 on 2010-01-21
i've been trying to flash my BIOS since 4 o'clock and i cant seem to do it properly. I think its best that i just stop before i mess up my board. Is there a way to just replace the chip?

---

### Post by lykwydchykyn on 2010-01-21
> **crazyavery4444 said:**
> i've been trying to flash my BIOS since 4 o'clock and i cant seem to do it properly. I think its best that i just stop before i mess up my board. Is there a way to just replace the chip?

Um, no.  Chip replacing went out with breakdancing and the Soviet Union.  

Can you explain where you're getting fouled up? It should be a straightforward process.

---

### Post by crazyavery4444 on 2010-01-22
> **lykwydchykyn said:**
> Um, no.  Chip replacing went out with breakdancing and the Soviet Union.  

Can you explain where you're getting fouled up? It should be a straightforward process.
I cant seem to find the BIOS image file. Only an executable file, I read somewhere that you can extract it to get the image file, but it didnt work.

---

### Post by lykwydchykyn on 2010-01-22
Can you tell me the output of:
```

aptitude search system-bios-optiplex-gx280

```

---

### Post by crazyavery4444 on 2010-01-24
> **lykwydchykyn said:**
> Can you tell me the output of:
```

aptitude search system-bios-optiplex-gx280

```

it just takes me back to the basic command. sorry for the long response time, I was in new york all weekend

---

### Post by lykwydchykyn on 2010-01-24
> **crazyavery4444 said:**
> it just takes me back to the basic command. sorry for the long response time, I was in new york all weekend

That means the repository was not added.

Apparently instructions on that dell site don't work, but here are some that I know work:

[http://ubuntuforums.org/showpost.php?p=8701237&postcount=4](http://ubuntuforums.org/showpost.php?p=8701237&postcount=4)

See if that works out for you.

---

### Post by crazyavery4444 on 2010-01-25
> **lykwydchykyn said:**
> That means the repository was not added.

Apparently instructions on that dell site don't work, but here are some that I know work:

[http://ubuntuforums.org/showpost.php?p=8701237&postcount=4](http://ubuntuforums.org/showpost.php?p=8701237&postcount=4)

See if that works out for you.

well it says that the 'deb' command is not found. this is causing alot of trouble for just a video and sound problem:lolflag:

---

### Post by lykwydchykyn on 2010-01-25
> **crazyavery4444 said:**
> well it says that the 'deb' command is not found. this is causing alot of trouble for just a video and sound problem:lolflag:

Those are not commands to run.  You need to add those lines to your software sources.  Instructions here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by crazyavery4444 on 2010-01-25
> **lykwydchykyn said:**
> Those are not commands to run.  You need to add those lines to your software sources.  Instructions here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


ugh now i get the failed to install message when installing the BIOS update through synaptic, here is the info where it ran into the error

```

```config error: plugin "firmware_addon_dell.dellbios" cannot be loaded: no module named "firmware_addon_dell.dellbios"```

```

---

### Post by lykwydchykyn on 2010-01-26
> **crazyavery4444 said:**
> ugh now i get the failed to install message when installing the BIOS update through synaptic, here is the info where it ran into the error

```

```config error: plugin "firmware_addon_dell.dellbios" cannot be loaded: no module named "firmware_addon_dell.dellbios"```

```

Open a command line.  Enter "apt-get -f install" and post the output here.

---

### Post by crazyavery4444 on 2010-01-26
> **lykwydchykyn said:**
> Open a command line.  Enter "apt-get -f install" and post the output here.

i had to be root for this to work, but here is the output

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

---

### Post by ncubede on 2010-02-07
> 
sudo ln -svf python2.5 /usr/bin/python


the above changes the system default to python 2.5 which is what the firmwaretool is using.  Your may want to edit firmwaretools to use /usr/bin/python2.5 instead /usr/bin/python.

I'd think a bug might be correct to make sure firmwaretool and e.g. pitivi explitictly reference the python version they are locked to be using.

---

### Post by lykwydchykyn on 2010-02-07
Can you post the complete output when you try to install the system-bios-optiplex-gx280 package?  I'm not getting a clear picture of what's happening here.

---

### Post by crazyavery4444 on 2010-02-10
> **lykwydchykyn said:**
> Can you post the complete output when you try to install the system-bios-optiplex-gx280 package?  I'm not getting a clear picture of what's happening here.

changes not applied, not all changes and updates successful for further details about of this failure please expand the 'details' panel below

when i expand the details panel i get this (oh boy, i cant copy and paste this. this may take a while)

(reading database ... 173525 files and directories currently installed.)
preparing to replace system-bios-optiplex-gx280-0x0197 0.a08-1 (using .../system-bios optiplx-gx280-0x0197_-.a08-1_all.deb) ...
unpacking replacement system-bios-optiplex-gx280-0x0197 ...
Setting up system-bios-optiplex-gx280-0x0197 (0.a08-1) ...

processing triggers for firmware-tools ...
config error: pluging "firmware_addon_dell.dellbios" cannot be loaded: no module named firmware_addon_dell.dellbios
dpkg:subprocess installed post-installation script returned error exit status 1
E: sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
processing triggers for python-support ...
setting up firmware-tools (2.1.7-0ubuntu1) ...

processing triggers for python-support...

then it just stops, nothing after that. i've left it open overnight and nothing still happens

---

### Post by lykwydchykyn on 2010-02-11
So, what happens if you run this at a command prompt now:

```

sudo dellBiosUpdate

```

---

### Post by crazyavery4444 on 2010-02-11
> **lykwydchykyn said:**
> So, what happens if you run this at a command prompt now:

```

sudo dellBiosUpdate

```
sudo: dellbiosupdate: command not found

---

### Post by lykwydchykyn on 2010-02-12
ok, how about:
```

sudo aptitude install firmware-addon-dell

```

I'm getting to where I'm stumped here. I've never had this much trouble with it.

---

### Post by crazyavery4444 on 2010-02-12
> **lykwydchykyn said:**
> ok, how about:
```

sudo aptitude install firmware-addon-dell

```I'm getting to where I'm stumped here. I've never had this much trouble with it.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


i think that did it. not rebooting until im sure

---

### Post by lykwydchykyn on 2010-02-12
> **crazyavery4444 said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


i think that did it. not rebooting until im sure

The output indicates that aptitude did nothing, because that package is installed.  I'm pretty stumped at this point, because this method has always worked fine for me.

Can you double check that the file /usr/sbin/dellBiosUpdate does not exist?  maybe /usr/sbin just isn't in your $PATH.

Or maybe just try running:
```

sudo /usr/sbin/dellBiosUpdate

```

If the packages are indeed installed, this should work.  If it does nothing, I don't know what else to say.

---

### Post by crazyavery4444 on 2010-02-12
> **lykwydchykyn said:**
> The output indicates that aptitude did nothing, because that package is installed.  I'm pretty stumped at this point, because this method has always worked fine for me.

Can you double check that the file /usr/sbin/dellBiosUpdate does not exist?  maybe /usr/sbin just isn't in your $PATH.

Or maybe just try running:
```

sudo /usr/sbin/dellBiosUpdate

```If the packages are indeed installed, this should work.  If it does nothing, I don't know what else to say.
well nothing is exactly what it does. Thanks for all your help but looks like im stuck with **** resolution.

---

### Post by crazyavery4444 on 2010-02-13
> **lykwydchykyn said:**
> The output indicates that aptitude did nothing, because that package is installed.  I'm pretty stumped at this point, because this method has always worked fine for me.

Can you double check that the file /usr/sbin/dellBiosUpdate does not exist?  maybe /usr/sbin just isn't in your $PATH.

Or maybe just try running:
```

sudo /usr/sbin/dellBiosUpdate

```If the packages are indeed installed, this should work.  If it does nothing, I don't know what else to say.
ok, well it turns out it wasnt the BIOS. I went rooting through my attic and found a newer and bigger monitor (dont know why I wasnt using this one in the first place) and now I get a cool 1280x1024 and nice refresh rate of 80 Hz. I still have a slight sound problem, but meh I dont really listion to music through my Pc anyway.

---

### Post by lykwydchykyn on 2010-02-13
> **crazyavery4444 said:**
> ok, well it turns out it wasnt the BIOS.

I think I need a tall, strong beverage about now...

:D

Ok, well, glad it works well.

---

### Post by crazyavery4444 on 2010-02-13
> **lykwydchykyn said:**
> I think I need a tall, strong beverage about now...

:D

Ok, well, glad it works well.
lol, same.

---

