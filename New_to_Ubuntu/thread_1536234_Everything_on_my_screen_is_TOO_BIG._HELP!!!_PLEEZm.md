---
title: "Everything on my screen is TOO BIG. HELP!!! PLEEZmy screen is all out of whack. i cam"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by jwilliamsthatsme on 2010-07-21
my screen is all out of whack. i came  over from windows and i am truly frustrated with all the tideous task i  have to do to get started. Its like my screen  is on super zoom and everywindow thats open is half off the screen its so big.  anyone got any help for me. i couldnt have switched over for this?!

---

### Post by Zeike on 2010-07-21
> **jwilliamsthatsme said:**
> my screen is all out of whack. i came  over from windows and i am truly frustrated with all the tideous task i  have to do to get started. Its like my screen  is on super zoom and everywindow thats open is half off the screen its so big.  anyone got any help for me. i couldnt have switched over for this?!

Please post the video card you are using.

Have you gone to System->Prefences->Monitors and tried changing the screen resolution?

---

### Post by jwilliamsthatsme on 2010-07-21
forgive me if im a lil computer illiterate, but i think im using NXVIDIA X. Does that sound right? I've been to monitor settings, it says that my "... driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" that sends me to NXVIDIA X server settings. ive fooled around with the resolution but two things happen. I either make everything way too big. or it makes my desktop bigger than my screen i have drag the mouse to the corners to see the whole desktop.

---

### Post by Zeike on 2010-07-21
What screen are you using?

Can you open a terminal (Applications->accessories->terminal) and type "lscpi".  Copy and paste the output here, within code tags.

Try the following:

Press Alt-F2
-enter 'gksu nvidia-settings'
-enter your password
-navigate to the "X Server Display Config" Tab in the settings window
-Select "detect displays"
-Under "display" on the right look for "resolution", make sure it is set to "auto".
-Select "apply"
-Select "save to x configuration file" on the bottom.
-Select quit

---

### Post by jwilliamsthatsme on 2010-07-21
No command 'lscpi' found, did you mean:
 Command 'lscpu' from package 'util-linux' (main)
 Command 'lscp' from package 'nilfs-tools' (universe)
 Command 'lspci' from package 'pciutils' (main)
lscpi: command not found


i tried the second step. i had tried that before and still no change to my display. is there maybe another 
driver i should be using?

---

### Post by Zeike on 2010-07-21
Run the following in the terminal:

sudo apt-get install pciutils

You will be prompted for your password, type it & press enter (no characters will be displayed as you type).
The package 'pciutils' will be downloaded and installed.  You might be asked to confirm by typing "Y"

Try running 'lspci' again.


Also, try running this and posting the output:
lsmod | grep nvidia

Again, what screen are you using?

---

### Post by NFblaze on 2010-07-21
The command is supposed to be **sudo lspci**

Also, what version of Ubuntu did you install?

---

### Post by Zeike on 2010-07-21
> **NFblaze said:**
> The command is supposed to be **sudo lspci**

I'm able to run lspci as non-root.  I think this is now the default behavior.

---

### Post by jwilliamsthatsme on 2010-07-22
user@user-desktop:~$ sudo apt-get install pciutils
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pciutils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 243 not upgraded.
user@user-desktop:~$ lscpi
No command 'lscpi' found, did you mean:
 Command 'lscpu' from package 'util-linux' (main)
 Command 'lscp' from package 'nilfs-tools' (universe)
 Command 'lspci' from package 'pciutils' (main)
lscpi: command not found
user@user-desktop:~$ sudo lscpi
sudo: lscpi: command not found
user@user-desktop:~$ smod | grep nvidia
No command 'smod' found, did you mean:
 Command 'qmod' from package 'gridengine-client' (universe)
 Command 'smsd' from package 'smstools' (universe)
 Command 'smsd' from package 'gnokii-smsd' (universe)
 Command 'gmod' from package 'gmod' (universe)
 Command 'smbd' from package 'samba' (main)
 Command 'lsmod' from package 'module-init-tools' (main)
 Command 'mod' from package 'monodoc-base' (main)
smod: command not found

im using a (AL1706 by ACER)

---

### Post by cariboo on 2010-07-22
You have a typo in your command, it's **lspci**.

The command stands for list pci devices.

---

### Post by Zeike on 2010-07-22
Thats "lsmod" not "smod".

Whats the output of "locate lspci"

It seems like you might be missing some files.  Did anything go amiss during the install process?  What version did you install?

I'm off to bed for the night but will be on tomorrow.  Good luck in the meantime.

---

### Post by robert shearer on 2010-07-22
NOT lscpi

its 
```
lspci
```



edit...guess we can all read. Though others type faster.

---

### Post by jwilliamsthatsme on 2010-07-22
true. that is a typo.

user@user-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:03.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 04)

---

### Post by NFblaze on 2010-07-22
> **Zeike said:**
> I'm able to run lspci as non-root.  I think this is now the default behavior.

Yea you can run as non-root (at least I think so from passive usage I've never actually diff'd their results). Though, whenever I do that it gives me a warning about it working better if you run it as root.

---

### Post by robert shearer on 2010-07-22
> 01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

I use this card too and it runs fine in all Ubuntu installs I have.

So it is likely to be a setting/configuration that is off.

What version of Ubuntu are you running ? 
Can you run this in a terminal and post the output

```
lsb_release -a
```

---

### Post by jwilliamsthatsme on 2010-07-22
user@user-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid

---

### Post by robert shearer on 2010-07-22
Good.
Now following Zeike's posts what are the outputs from...

```
lsmod | grep nvidia
```

---

### Post by jwilliamsthatsme on 2010-07-22
[FONT=monospace]user@user-desktop:~$ lsmod | grep nvidia
nvidia               4701243  22 
agpgart                31724  2 nvidia,intel_agp

[/FONT]

---

### Post by Zeike on 2010-07-22
> **jwilliamsthatsme said:**
> 01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

I think this is an older card.  You might have better luck running version 173 of the nvidia driver rather than the newest version.


go to "System->Administration->Hardware Drivers"

Select "NVIDIA accelerated graphics driver (version 173)" and choose activate.  You'll have to reboot after you do this.

---

### Post by jwilliamsthatsme on 2010-07-22
thanks that worked.

---

