---
title: "flummoxed by audio woes"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by joonga on 2008-12-13
Greetings.

Recently installed xubuntu 8.10. In a nutshell, I can't play any sound files on my old intel-x86 350mhz box. I don't have a fancy sound-card installed neither, but the hardware I gather is integrated to the motherboard. I've scoured the many troubleshooting articles and knowledge-base information tid-bits, and tried many different experiments, but the bottom line is... still no sound. The one perplexing thing for me to figure out is the xfce4-mixer properties: the device is set to <default>, which I think should be okay, but, I don't know what to make of the <Wannabe Master> field. Methinks that my mixer is not setup properly. So, I was wondering if someone would please direct me to a resource(s) that would help me solve this now quickly-becoming-nagging issue. Also, what shell cmds can I use to determine if my sound hardware is up to speed (i.e to detect the hardware, etc.), before I waste anymore of my time.

Again, many thanks in advance for your help and time.
Cheers.
Joonga.

---

### Post by jbrown96 on 2008-12-13
not sure what you have tried, but a common problem is alsamixer. In a terminal, ```
alsamixer
``` and use the arrrow keys to adjust volume and m to mute/unmute channels.

---

### Post by joonga on 2008-12-13
Hello Jbrown96.

I ran the cmd, but got this as a result:

> alsamixer: function snd_ctl_open failed for default: No such file or directory

Thanks.
J.

---

### Post by jbrown96 on 2008-12-13
What's your hardware? ```
lspci | grep Audio
``` or if that doesn't return anything ```
lspci
```

---

### Post by joonga on 2008-12-13
Hello gain.

grep didn't work, so here is the results from lspci:

> joonga01@valis:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 43)
00:0f.0 SCSI storage controller: Future Domain Corp. TMC-18C30 [36C70]
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)


Thx.
J.

---

### Post by joonga on 2008-12-13
Little update: I scoured the discussion lists and found a few useful cmds to determine the status of my audio device:

**modprobe snd-** produced the following: "FATAL: Module snd_ not found."

**aplay -l**  produced: "aplay: device_list:215: no soundcards found..."

So, now, I can"t even determine what my sound device is?

BTW, I installed alsamixer and related files, but that didn't help either. Sort of stuck with this and don<t know what to try next^

Cheers.
J.

---

### Post by joonga on 2008-12-14
Me again... I'm deducing that since my audio device is of the integrated variety, it cannot be detected by the normally used cmds (at least the suggested ones in this and other threads). I guess I'll have to install an 'actual' audio device and take it from there.

Again, thanks to those who helped out.
All the best.
Joonga.

---

### Post by jbrown96 on 2008-12-14
You might need to install from source. It's not too hard, and provided nothing has changed you can follow these instructions that I wrote up quite a while ago. [http://ubuntuforums.org/showthread.php?t=612605]("http://ubuntuforums.org/showthread.php?t=612605") You will need to change the first configure line to ```
./configure --with-cards=intel8x0 --with-sequencer=yes
``` Also you don't want to use that version, so get the newest version of each of those from the Alsa website. Consequently, the tar commands are different as well.

---

### Post by joonga on 2008-12-14
Many thanks Jbrown96.

All was going well until I ran the <sudo make install> cmd at the end of the 1st section (of three). Of note: I had to use a new path to the driver (e.g.: <ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2>). Here is the verbose I got after executing <make install>:


> joonga01@valis:~/alsa-driver-1.0.15$ sudo make install
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/joonga01/alsa-driver-1.0.15/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1


What can I make of the error message?

Many thanks again!
Joonga.

---

### Post by joonga on 2008-12-14
BTW, /usr/include/sound is empty. Shouldn't there be a hidden file: <.h>? Perhaps I misread the script.

Thx, & cheers.
J.

---

### Post by jbrown96 on 2008-12-14
Not quite sure what that means. Don't use that version though. Use the same instructions, but use the current version. Use this site to get the files [http://www.alsa-project.org/main/index.php/Download]("http://www.alsa-project.org/main/index.php/Download")

---

### Post by joonga on 2008-12-14
Will try it again Jbrown96.

Enjoy the rest of the weekend.

Regards.
J.

---

### Post by joonga on 2008-12-15
Hahaha... I have to laugh at myself... I tried it again, and I still blocked at the 'sudo make install' point. So, in my infinite wisdom, I decided to uninstall all manner of files related to 'alsa' from the synoptic pkg manager, thinking that that might help, then rebooted. Here's the joke (which I'm taking rather well I might add), I've now lost my Nvidia graphics and am now left with the DOS environment. So, in my stupidity, I guess removed some key graphics files and such in the process. I guess I'll have to halt things for a few days. I'm now thinking of re-installing xubuntu... what the hell.

Thank you for your generous assistance Mr. Jbrown96.
Joonga.

---

### Post by jbrown96 on 2008-12-15
I'm not using ubuntu right now, so I can't check, but I think you should be able to restore it fairly easily. You will need to know tab completion for this. When you start typing a command, if you press tab it will auto-complete it. If there is more than one option that matches, then it will just complete until the option diverge. Try these commands and when typing the bits about xfce, try hitting tab twice to show options.

I believe the package you are looking for is called xfce-desktop

Try ```
sudo apt-get install xfce-desktop
``` and try tab completion after xfce

---

### Post by joonga on 2008-12-16
Hello again.

I finally got xubuntu and my graphics back up and running. However, after running the cmds and scripts, I still choke at the same spot: <sudo make install>. Here's essentially the same verbose as before:

> pierre01@valis:~/alsa-driver-1.0.18a$ sudo make install
[sudo] password for pierre01: 
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/pierre01/alsa-driver-1.0.18a/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1


I'm afraid a little too inexperienced to proceed any further with the t.shooting. 

Cheers & best.
Joonga.

---

