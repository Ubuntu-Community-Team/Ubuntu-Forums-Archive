---
title: "Lost ethernet connection"
date: 2016-07-26
forum: Networking &amp; Wireless
---

### Post by jeffhobson on 2016-07-26
Installed Ubuntu 16.4.1. added Gnome synaptic. Synaptic did not come up but was in the startup applications. I re-booted. When Ubuntu came back up, there was no Ethernet connection. I have NO Linux internals knowledge. Please advise what commands I need to enter to diagnose and/or restore the Ethernet connection. The network icon at the top of the desktop says networking is enabled but no network devices available. 'edit connections' shows nothing in 'Network Connections". I installed Ubuntu on the advice of a friend who said it did not need any 'tweaking' and would run right out of the box. I am stumped but can bring up a terminal screen and type commands. This post came from a Windows Machine since I have no Ubuntu network connection. Any commands I need to enter will have to be typed in from any response to this thread.

Thank you for the help

---

### Post by chili555 on 2016-07-26
Let's start with a terminal command:```
lspci -nnk | grep 0200 -A2
```Thanks.

---

### Post by jeffhobson on 2016-07-26
02:00.0   ethernet controller [0200]: Broadcom Corp BCN4401-B0 100Base-TX [14e4:170c] (rev 2)
                subsystem: Dell BCM4401-b0 100Base-TX [1028:01D4]
                Kernel Modules: b44

=================End of terminal output------------
BTW: is there a way to copy what the command returns to a usb flash that I  can then upload to the windows screen? I typed in the response to the command by looking and typing.

Thanks for the help

---

### Post by chili555 on 2016-07-26
You can certainly highlight the output from the terminal and select 'Copy.' Then paste it into a text document; gedit, kate or similar. Save it as output.txt or output2.txt or whatever is convenient. Drag and drop the text document to the USB and post it here.

Is the module loaded at this time? ```
lsmod | grep b44
```If not, load it and see what happens:```
sudo modprobe b44
ifconfig
```Any errors, warnings, etc. from the terminal? Any clues in the message log?```
dmesg | grep b44
```I have a suspicion that I'd like to clear up. Do you have a wireless card? What is it?```
lspci -nnk | grep 0280 -A2
```Also a Broadcom, by chance??

---

### Post by jeffhobson on 2016-07-26
```
lsmod  |grep b44 <no output, returned to prompt>
sudo modprobe b44   <never returned to prompt>

jeff@jeff-Dell520:~$ lsmod|grep b44

jeff@jeff-Dell520:~$ sudo modprobe b44

^C

jeff@jeff-Dell520:~$ lsmod | grep b44

jeff@jeff-Dell520:~$ ifconfig

lo        Link encap:Local Loopback
  
          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:65536  Metric:1

          RX packets:298228 errors:0 dropped:0 overruns:0 frame:0

          TX packets:298228 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1

dmesg |grep b44         <No output; returned to prompt>

jeff@jeff-Dell520:~$ lspci -nnk |grep 0280 -A2

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

	Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]

	Kernel driver in use: wl
jeff@jeff-Dell52
```

================= End of terminal output ==================
Yes, there is a wireless adapter which is not enabled (by pressing "Alt-f2)

Sorry it took so long, I had to perfect the copy of the terminal output ==>USB==>Windows==>USB==> Editor==>Forum Reply



 
```
          RX bytes:22089568 (22.0 MB)
           TX bytes:22089568 (22.0 MB)


jeff@jeff-Dell520:~$ gedit
```

---

### Post by jeremy31 on 2016-07-26
jeffhobson please use code tags when posting terminal commands or output from terminal as it preserves formatting and prevents smilies from popping up.  See the code tags link in my signature for one method, in advanced reply you can use the # to insert code tags and paste the info between the [noparse]```
 
```[/noparse]

---

### Post by chili555 on 2016-07-26
> 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

	Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]

	Kernel driver in use: wlAh, haaaa! A Broadcom with the wrong driver installed and a driver that blacklists b44. Please do:```
sudo apt-get purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```The conf file may be gone as a result of the purge step; if so, that's fine.

Reboot and tell us if the ethernet has returned. If it has, as we suspect, now let's install the correct wireless driver:```
sudo apt-get install firmware-b43-installer
```You will probably be all set.

---

### Post by jeffhobson on 2016-07-26
Thank you! Thank you! I now have IP address 192.168.1.4 (DHCP assigned)


Quick knowledge building question: Who is blacklist and why does it not like the Broadcom interface?

---

### Post by chili555 on 2016-07-26
Awesome! Glad it's working.

Please use Thread Tools at the top to mark Solved.

---

