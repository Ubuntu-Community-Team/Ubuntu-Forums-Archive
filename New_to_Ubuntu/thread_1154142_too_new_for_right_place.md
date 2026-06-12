---
title: "too new for right place"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Godzeye on 2009-05-09
I try to find out what to do with my nvidia driver and then there's something else that won't work or I can't figure out how to do...I upgraded to 9.04, and have never got the integrated graphics card to do anything in either of my desktop pc's....i did something screwy to my xorg and tried dling the drivers from synaptic, i should have been a bit more patient b4 trying to edit xorg but I think i need to and cant seem to get there. this is fun but a lot of work!!! thanks in advance but please remember am a newbie when it comes to these commands etc etc (although am proud to say got clam av to work how I wanted- I think although i don't even need it! :)))

---

### Post by nothingspecial on 2009-05-09
The way to fix xorg - or get it back to where you started from is running

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Never tried it myself though so you might want to wait for confirmation.

---

### Post by jbruced on 2009-05-09
I fought with nvidia drivers a year or so ago. What worked for me, was to install drivers and nvidia-settings from the repositories, and run nvidia-settings as sudo.

at the terminal:

sudo nvidia-settings

Then make your setting choices in a the gui program, choose save settings, and reboot. 

This program is from nvidia, and they know thier drivers better than most of us who try to help.


 GL
Bruce

---

### Post by Godzeye on 2009-05-10
Screen 0: minimum 640 x 480, current 800 x 600, maximum 1280 x 1024
default connected 800x600+0+0 0mm x 0mm
   1280x1024       0.0  
   1024x768        0.0  
   800x600         0.0* 
   640x480         0.0  
joe@joe-desktop:~$ xrandr--output lvds --mode 1024x768
bash: xrandr--output: command not found
joe@joe-desktop:~$ sudo nvidia-xconfig
[sudo] password for joe: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'



what???maybe been playing too much with it... step by painstaking step please...lspci



lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2)
00:04.0 Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)
00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
02:08.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

---

### Post by Godzeye on 2009-05-10
Well i got it to work!! Thank you all 4 your help! now maybe I will try it on the other puter after trying compiz on this one!!!:P

---

### Post by ikisham on 2009-05-10
> **Godzeye said:**
> 
VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'



what???maybe been playing too much with it... step by painstaking step please...lspci


Yeah, you had been playing 'too much' with it but the reconfiguration tool wrote a brand new xorg.conf for you;-)

---

