---
title: "Can't get sound to work in ubuntu"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Jad_ime on 2010-01-08
After i installed ubuntu and dual booted it with windows vista, the sound does not work while in ubuntu but does in vista.

---

### Post by derekmbarnes on 2010-01-09
Have you checked to see if you have a Linux-compatible driver running your sound card? Open Terminal, run the code below and get back to us with the results:

```
lspci -v | less
```

---

### Post by Jad_ime on 2010-01-09
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file

---

### Post by markjensen on 2010-01-09
Jad, you didn't type the command in properly.

Here's a neat little Linux trick.

Open up a terminal.   Now, in your firefox browser, go back to the command that derek posted, and drag/select it with your mouse so the whole line is selected.

Now, mouse over to your open terminal and middle-click in there, and the exact text is pasted without error.  :)

You may have to hit ENTER to make the command run.

---

### Post by Jad_ime on 2010-01-09
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
        Subsystem: Gateway 2000 Device 7201
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
        Subsystem: Gateway 2000 Device 7201
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 50100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 20e0 [size=8]
        Memory at 40000000 (32-bit, prefetchable) [size=256M]
        Memory at 50180000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Gateway 2000 Device 7201
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 501c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
:

---

### Post by Jad_ime on 2010-01-09
alright thankx thats what i got.

---

### Post by Jad_ime on 2010-01-10
yo this suck wit no sound anybody??? help

---

### Post by markjensen on 2010-01-10
Well, the Intel chipset is supported.  Do you have it muted?  Does it work if booting the Ubuntu CD as a "liveCD"?

---

### Post by garvinrick4 on 2010-01-10
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][SIZE=4]**art A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)**[/SIZE]
*All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ rm -r ~/.pulse ~/.asound* [/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo rm /etc/asound.conf[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#ff0000]**Warning:**[/COLOR][COLOR=#ff0000] As always, use caution when removing files on your system. Any typos can potentially cause data loss.[/COLOR]
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Don't worry if some of these files did not exist on your system.[/COLOR]


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000] [FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio[/SIZE][/FONT][/COLOR] [[COLOR=#444444][FONT=Verdana, Arial, Tahoma][SIZE=2]_3_[/SIZE][/FONT][/COLOR]]("https://bugs.launchpad.net/bugs/192888")[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]. Ensure the evil "libflashsupport" library is [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]**not**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2] installed: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/COLOR]

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:[/COLOR][/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ pulseaudio & pavucontrol[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ alsamixer [COLOR=#0000ff]-Dhw[/COLOR][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.[/COLOR][/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]REBOOT
[/COLOR][/SIZE][/FONT][/COLOR]

---

### Post by Jad_ime on 2010-01-10
Nothing is muted and I don't have a cd i downloaded and installed through the demo mode. i don't know if i'm a karmic user but I am unable to do step 4 b/c there is no such option. 

 would any of this matter if the rear connection does not work for some reason so I am using the headphone jack in the front. I built the computer from scratch and the sound card i had isn't supported by the board i'm using.

[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/COLOR]
[/SIZE][/FONT][/COLOR]
this is what i got after I did the steps and no sound worked so i repeated after i rebooted.

jacob@jacob-desktop:~$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/ $ rm -r ~/.pulse ~/.asound*  $ sudo rm /etc/asound.conf
mkdir: cannot create directory `/home/jacob/pulse-backup': File exists
jacob@jacob-desktop:~$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
[sudo] password for jacob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2-plugins is already the newest version.
padevchooser is already the newest version.
libsdl1.2debian-pulseaudio is already the newest version.
The following packages were automatically installed and are no longer required:
  knetwalk libopenal1 kpat kolf kshisen linux-headers-2.6.31-14 kjumpingcube
  kblocks katomic kdegames-card-data kgoldrunner kblackbox kiriki
  libwxgtk2.8-0 ksame xdotool kdiamond ksirk ksquares tremulous-data
  kdegames-mahjongg-data cairo-dock-data kbreakout kbounce kfourinline
  python-ogg kollision ktron kspaceduel libwxbase2.8-0 ksudoku klines kdesnake
  lskat kubrick killbots kapman kbattleship cairo-dock-plug-ins-data
  linux-headers-2.6.31-14-generic kmines libgtkglext1 konquest
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
jacob@jacob-desktop:~$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not installed, so not removed
Package flashplugin-nonfree-extrasound is not installed, so not removed
The following packages were automatically installed and are no longer required:
  knetwalk libopenal1 kpat kolf kshisen linux-headers-2.6.31-14 kjumpingcube kblocks katomic kdegames-card-data kgoldrunner
  kblackbox kiriki libwxgtk2.8-0 ksame xdotool kdiamond ksirk ksquares tremulous-data kdegames-mahjongg-data
  cairo-dock-data kbreakout kbounce kfourinline python-ogg kollision ktron kspaceduel libwxbase2.8-0 ksudoku klines
  kdesnake lskat kubrick killbots kapman kbattleship cairo-dock-plug-ins-data linux-headers-2.6.31-14-generic kmines
  libgtkglext1 konquest
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
jacob@jacob-desktop:~$ pulseaudio & pavucontrol 
[1] 2894
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
[1]+  Exit 1                  pulseaudio
jacob@jacob-desktop:~$ pulseaudio & pavucontrol 
[1] 2897
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
alsamixer

---

### Post by markjensen on 2010-01-11
If you are using the headphones, you might want to go to your output tab and make sure you select your headphones.  It is in a drop-down select box.  I'll attach a screenshot.
[ATTACH]143284[/ATTACH]

---

### Post by Jad_ime on 2010-01-11
the headphone output is already selected... but still no sound could it be a program malfunction??? or could i have something not hooked up right inside the computer?

---

