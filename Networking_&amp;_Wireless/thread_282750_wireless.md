---
title: "wireless"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by IslandGuy on 2006-10-23
Hello

i have an issue with wireless on a dell 8600, i am knew to linux so bare with me if i say the wrong termonology.

Ok, wired connection works fine on the laptop, but wireless no joy. i have tried to installed network manager, but can not find it in the apllication area.

can anyone please find advise the best way to proceed.

---

### Post by AAM on 2006-10-23
I have had googled around and not found much, unfortunately.

Do you have the Windows drivers for the chipset? If you have them, you can use ndiswrapper to install them and then use the network tool under Preferences|Networking to activate. If you don't the rest is just noise.

I use a Netgear WG111 USB access point, so I can only tell you the pattern that I follow and you will have to try yourself.](*,)! Almost the same procedure has worked for other USBs and for PCMCIA cards also.

Install ndiswrapper-utils from the CD or Synaptic. You will need the MAC of the wireless card later. In the console type the following:

[LIST]
[*]#sudo ndiswrapper -l
[INDENT][*][this looks for installed *.inf files][/INDENT]
[*]#cd /directory_where_the_INF_and_SYS_files_are_stored
[INDENT][*][note that you must have the INF and SYS files together in the same directory][/INDENT]
[*]#sudo ndiswrapper -i FILE.inf
[*]#sudo depmod -a
[*]#sudo modprobe ndiswrapper
[*]#sudo ndiswrapper -m
[INDENT][*][that installs the windows driver within the wrapper as part of the kernel][/INDENT]
[*]#sudo gedit /etc/modules
[INDENT][*]add ndiswrapper at the bottom of the list[/INDENT]
[*]#sudo gedit /etc/modprobe.d/blacklist
[INDENT][*]add the following at the bottom:[/INDENT]
[INDENT][*]blacklist islsm[/INDENT]
[INDENT][*]blacklist islsm_usb[/INDENT]
[INDENT][*]blacklist islsm_pci[/INDENT]
[INDENT][*]blacklist prism2_usb[/INDENT]
[INDENT][*](this blacklisting may very well be specific for my access point)[/INDENT]
[*]#sudo gedit /etc/iftab
[INDENT][*]add the following at the bottom:[/INDENT]
[INDENT][*]wlan0 mac (*insert mac number here*)[/INDENT]
[/LIST]

now close the machine down and reboot, go back to Preferences|Networking and the wireless should now be visible.

If this gives you no joy, then I have two further suggestions to see if you can get wireless working. 

Firstly download and try KANOTIX. It is a live CD and is the only distro to recognise my wireless cards on boot. It can be written to disk. The second is to try Mandriva 2006 or 2007 depending on your hardware. Mandriva has the easiest configuration tools in their Control Centre. I assume that PCLinuxOS will be the same having been based very closely on Mandriva.

Good luck!

---

### Post by IslandGuy on 2006-10-23
Thanks for the reply, i am at work at the moment and will rush home to try it out!!!!

---

### Post by squibT on 2006-10-23
You can also try to install using Wiki for bcmxx...just insert your driver with ndiswrapper there is a cutter install that works just fine...Install Network Manager from Synaptic first...just do a search for network manager....

---

