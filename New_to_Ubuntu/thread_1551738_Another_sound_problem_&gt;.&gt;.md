---
title: "Another sound problem &gt;.&gt;"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by ibe2fly4chu on 2010-08-12
So i was here trying to use my soundblaster xfi card in hope of actually getting higher volume in ubuntu. Anyone i installed the drivers for it and still couldnt get it to work. It turns out knocked out my on-board sound drivers as well, and now i cant hear anything. I tried following this guide [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
but nothing worked :(

Can anyone tell me how to get my on board sound card to work again, it was working fine before i installed the drivers. From lspci -v this is what is shows:

Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: nVidia Corporation MCP51 High Definition Audio
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

unfortunately lspci cant detect the sound card :(

---

### Post by jtarin on 2010-08-12
> **ibe2fly4chu said:**
> So i was here trying to use my soundblaster xfi card in hope of actually getting higher volume in ubuntu. Anyone i installed the drivers for it and still couldnt get it to work. It turns out knocked out my on-board sound drivers as well, and now i cant hear anything. I tried following this guide [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
but nothing worked :(

Can anyone tell me how to get my on board sound card to work again, it was working fine before i installed the drivers. From lspci -v this is what is shows:

Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: nVidia Corporation MCP51 High Definition Audio
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

unfortunately lspci cant detect the sound card :(

For your onboard sound.....Have you tried going into the bios and see if it is disabled?
You will also have to uninstall the drivers you previously installed for the other sound card. Then you should be able to follow that guide to get your onboard working again.

---

### Post by ibe2fly4chu on 2010-08-12
yea i did check the bios. Everything there seems to be working fine. The name of the driver i used is "oss-linux-4.2-2003_i386.deb"...do i just do a sudo purge and that package name to remove it?

---

### Post by jtarin on 2010-08-12
> **ibe2fly4chu said:**
> yea i did check the bios. Everything there seems to be working fine. The name of the driver i used is "oss-linux-4.2-2003_i386.deb"...do i just do a sudo purge and that package name to remove it?
OSS is deprecated, ALSA is advanced, PulseAudio is more advanced.
Switching from Pulse to ALSA is a step backward.
Switching from ALSA to OSS is a further step backward.

To find out which modules (drivers) are loaded, you run these commands:

lsmod | grep snd

lsmod | grep oss

------------------------------
EXPLANATION:

snd - ALSA modules (drivers)

oss - OSS4 modules, or ALSA modules (ALSA emulation of OSS)


----------------------------------------------------------

This command may show error messages for OSS4

dmesg | grep oss

It will show if there are any errors on the device.


--------------------------------------------------------------------------

You can get a more exact error message with this command

dmesg | grep HDA

---

### Post by ibe2fly4chu on 2010-08-12
ok i ran both commands. The output it produced are :

s7even@Edward:~$ lsmod|grep snd
snd_page_alloc          7076  0 
s7even@Edward:~$ lsmod | grep oss
oss_usb               104132  0 
oss_hdaudio           140744  0 
osscore               557781  2 oss_usb,oss_hdaudio

So it seems i am on the oss module (which is older i am presuming from what you said)...still not clear how to purge it though. Do i do a sudo purge oss?

Thanks for the quick response by the way ^^

---

### Post by jtarin on 2010-08-12
> **ibe2fly4chu said:**
> ok i ran both commands. The output it produced are :

s7even@Edward:~$ lsmod|grep snd
snd_page_alloc          7076  0 
s7even@Edward:~$ lsmod | grep oss
oss_usb               104132  0 
oss_hdaudio           140744  0 
osscore               557781  2 oss_usb,oss_hdaudio

So it seems i am on the oss module (which is older i am presuming from what you said)...still not clear how to purge it though. Do i do a sudo purge oss?

Thanks for the quick response by the way ^^

Go ahead and purge it as you won't need it. Then issue the command ```
modprobe -r oss
```this should remove the module. Then runn the two previous commands again to check.

---

### Post by ibe2fly4chu on 2010-08-12
hmm...the command modprobe -r oss gives me the following messege:

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: Failed to open config file alsa-base.save: Permission denied
FATAL: Module oss not found.

i also tried modprobe -r osscore and oss_hdaudio both resulting in a warning and error.

---

### Post by jtarin on 2010-08-12
> **ibe2fly4chu said:**
> hmm...the command modprobe -r oss gives me the following messege:

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: Failed to open config file alsa-base.save: Permission denied
FATAL: Module oss not found.

i also tried modprobe -r osscore and oss_hdaudio both resulting in a warning and error.Just try the purge command and see if it removes.

---

### Post by jtarin on 2010-08-12
I don't have any more time at present to help but I will try to be back on in about 3 hours...I'm at work and I'll be home by then. Just purge your package for now and bone up or try [this]("https://wiki.ubuntu.com/PulseAudio") documentation.

---

### Post by ibe2fly4chu on 2010-08-12
ok got it to removed. For those of you who are following and or having same problem, i simply used the "sudo apt-get remove --purge oss" command.

I also ran previous commands and this was the output:

s7even@Edward:~$ lsmod | grep snd
snd_page_alloc          7076  0 
s7even@Edward:~$ lsmod | grep oss
s7even@Edward:~$ 

next you suggest to follow the guide i first mentioned ?

---

### Post by ibe2fly4chu on 2010-08-12
k

---

### Post by ibe2fly4chu on 2010-08-12
anyoneone else with any ideas?

---

### Post by ibe2fly4chu on 2010-08-12
ok i think i am missing hda-intel module...for some reason i cant find it. anyone know where i could download it from?

---

### Post by jtarin on 2010-08-12
Why do you think your missing that module?
What is the output from ```
lspci
``` now?

---

### Post by ibe2fly4chu on 2010-08-12
when i try to run aplay -l it said no sound card is found. So i figured i typed lspci -v in order to know exactly what soundcard was on the mobo. It said it was the MCP51 definition audio. From what i read the intel-hda drivers were recommended for this card. I just figure if i could get the hda drivers it might fix it. I am just trying random things since no one had reply since you left :P

no clue if it would work or not

---

### Post by jtarin on 2010-08-12
Start with ```
sudo apt-get alsa-base
```what does that return?

---

### Post by ibe2fly4chu on 2010-08-12
that command returns " Invalid operation alsa-base
"

---

### Post by jtarin on 2010-08-12
Reboot and then run the command ```
sudo apt-get install alsa
```

---

### Post by jtarin on 2010-08-12
I WANT TO MAKE SURE YOU HAVE ALSA INSTALLED FIRST THEN.....
 The command:
 ```
which alsa

 which pulseaudio
```Results?????

Possibly fix for that chip:
The MCP51 mixer gets muted unless you specify correct model option.

The file /usr/share/doc/alsa-base/driver/ALSA-configuration.txt.gz lists different options for driver snd-hda-intel. For instance, my mobo is ASUS M2NPV-VM, and model alsa-dig seems to work on it.

You can try different model names until you get mixer unmuted.

Remove snd-hda-intel module and reinstall it with correct "model", e.g.,

sudo rmmod snd_hda_intel
sudo modprobe snd_hda_intel model=alsa-dig

If the module is in use, see which process keeps it open with

sudo lsof /dev/snd/*

and kill the processes.

As permanent fix, add line with correct module option to /etc/modprobe.d/options:

options snd-hda-intel model=alsa-dig

Also, make sure that you don't already have an incorrect options line.

---

### Post by ibe2fly4chu on 2010-08-12
just posting the results of the which commands so you could see them. 
s7even@Edward:~$ which alsa
/sbin/alsa

s7even@Edward:~$  which pulseaudio
/usr/bin/pulseaudio
s7even@Edward:~$

i am looking over what you suggested, and will attempt it after a another full re read. Want to make sure i understand fully

---

### Post by jtarin on 2010-08-12
Your module for that chip is Module ```
snd-ali5451
```so do a ```
modprobe snd-ali5451
``` to load it.then try aplay.

---

### Post by ibe2fly4chu on 2010-08-12
After running sudo modprobe snd-ali5451, the output i received was:

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting snd (/lib/modules/2.6.32-24-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.32-24-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ac97_bus (/lib/modules/2.6.32-24-generic/kernel/sound/misc/ac97_bus.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.32-24-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ali5451 (/lib/modules/2.6.32-24-generic/kernel/sound/pci/ali5451/snd-ali5451.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by jtarin on 2010-08-12
Enter the command sudo gedit /etc/modprobe.d/alsa-base.conf 

The file should open then just scroll all the way down and add at the end:

options snd-ali5451 model=laptop (yes as it is just copy/paste the line)

Reboot...then rerun the command aplay -l.

---

### Post by ibe2fly4chu on 2010-08-13
After reboot, the aplay -l command still returns:
"aplay: device_list:223: no soundcards found..."

---

### Post by jtarin on 2010-08-13
Run and post```
cat /proc/asound/version
```

---

### Post by ibe2fly4chu on 2010-08-13
Results after running cat/proc/asound/version:

s7even@Edward:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory

---

### Post by jtarin on 2010-08-13
Run it several times until there's a result.....there should be you have alsa installed.

---

### Post by ibe2fly4chu on 2010-08-13
yea thats what i thought too. I ran it a mabey like 30 times now and it still says no file or directory though :(

---

### Post by jtarin on 2010-08-13
Then lets try to reinstall alsa..... sudo apt-get install alsa

---

### Post by ibe2fly4chu on 2010-08-13
okay. Tried installing alsa, the output i received was x.x : "Note, selecting alsa-base instead of alsa
alsa-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded"

---

### Post by jtarin on 2010-08-13
Then uninstall it with purge and reinstall.

---

### Post by jtarin on 2010-08-13
What is the other soundcard you have?

---

### Post by ibe2fly4chu on 2010-08-13
purged alsa. Tried to then run Cat /proc/asound/version 
but still got the "no such file or directory " messege

Edit:
The other sound card i have is a soundblaster x-fi sound card. I couldn't find any drivers that work with Linux though...the only one i found was the oss one which made my on board soundcard stopped working; it didnt even work for the soundblaster card either ; ;

---

### Post by jtarin on 2010-08-13
> purged alsa. Tried to then run Cat /proc/asound/version 
but still got the "no such file or directory " messegeThere shouldn't be until you reinstall it

---

### Post by jtarin on 2010-08-13
Reinstall then run Cat /proc/asound/version. You should reboot before running this command after a fresh install of alsa.

---

### Post by ibe2fly4chu on 2010-08-13
well at least now it says something different. 

s7even@Edward:~$ Cat /proc/asound/version
No command 'Cat' found, did you mean:
 Command 'dat' from package 'liballegro4.2-dev' (universe)
 Command 'bat' from package 'bacula-console-qt' (universe)
 Command 'iat' from package 'iat' (universe)
 Command 'cat' from package 'coreutils' (main)
 Command 'rat' from package 'router-audit-tool' (universe)
 Command 'rat' from package 'rat' (universe)
 Command 'at' from package 'at' (main)
 Command 'pat' from package 'dist' (universe)
 Command 'lat' from package 'lat' (universe)
Cat: command not found

---

### Post by jtarin on 2010-08-13
Cat is capital......change

---

### Post by ibe2fly4chu on 2010-08-13
changed it to lower case....and we are back to "no such file or directory"...

ugh...something simple as installing a driver is this complicated...its looking more and more that i have to reformat, this is getting a tad bit fustrating. sigh...

---

### Post by jtarin on 2010-08-13
I'm with ya on that...it seems your missing something from the install. If you have nothing to lose....reinstall and don't add any new software with the exception of updates during the install. Get my PM address from my username and let me know when your back on. It's evening here so I won't be back on for another 12 hours or so...if you come back on PM me with the topic url and I'll try to help. Keep all the information about your module to load next time and some of the more important links to trounleshooting.Good Luck.

---

### Post by lidex on 2010-08-13
Once you've removed OSS, boot into a lower numbered kernel and re-install your latest kernel and kernel-header packages. Reboot into the re-installed kernel and post these outputs:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```

---

