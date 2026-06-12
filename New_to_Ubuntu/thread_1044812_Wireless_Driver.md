---
title: "Wireless Driver?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by jtsc on 2009-01-19
Greetings! I just installed Ubuntu on my Thinkpad Z61t after a pyrrhic conflict of epic proportions whose details are irrelevant. I'm loving a lot of the things that I can do with Ubuntu already after two hours, but there are still some kinks.

Most importantly, how do I install a driver? [This]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel") says that the driver I need for my wireless card is "iwl3945", but it doesn't say how to install that. "man -k drivers" also didn't turn up anything useful, nor can I see how to do it from the Network Tools display.

Second most importantly, how do I get back to "$" in the terminal? When I used unix in college, every command would either return to the "$" when I pressed return at the end of a document, or there would be commands for the program at the bottom of the screen. It seems like every time I want to, say, look at a new page in the manual I need to open a new tab and close the old one, which is silly.

Thanks so much!

---

### Post by Terl on 2009-01-19
Have you checked System>Administration>Hardware?  That menu selection lists hardware drivers you may require.

---

### Post by Titan8990 on 2009-01-19
Those drivers are modules that are loaded into the kernel. They should already be there but you can check with:

lsmod | grep 'iwl3945'


I am not quite sure what you mean about the kernel returning a: $. The $ in the terminal in linux indicates that the terminal is being use by a non-root user. The prompt is defined by the $PS1 variable and you should be able to change it in the .bash_profile file in your home directory.

Also, manual pages can just be scrolled through using pageup and pagedn keys.


If you liked old-school UNIX with a lot of CLI work than Ubuntu may not be your best choice. Ubuntu and OpenSuse are excellent Desktop OSes whereas Gentoo and FreeBSD are excellent "geek" OSes.

---

### Post by jtsc on 2009-01-19
Wow, this is an amazing community. Thanks for the quick help.

Terl: (Administration > Hardware Drivers) says "No proprietary drivers are in use on this system." (Administration > Hardware Testing) recognizes the wireless card that I have, but observes, quite correctly, that I'm not connected to the internet.

Titan8990: It returned ...
iwl3945   98894   0
rfkill    17176   4 thinkpad_acpi,iwl3945
mac80211  216820  1 iwl3945
led_class 2164    2 thinkpad_acpi,iwl3945
cfg8021   32392   2 iwl3945,mac80211

I assumed that means that the driver is there, but I don't know if that means its working.

On the question of "$", I wasn't concerned about which character was being used, I just mean that the command line doesn't reappear when a previous command was executed. (And I'm not really a huge fan of or proficient with unix, I'm just familiar with basics of how it works.)

---

### Post by Titan8990 on 2009-01-19
Yes, the driver is there. Report the output of the following:


lspci

ifconfig -a

iwconfig

---

### Post by linuxisevolution on 2009-01-19
> **jtsc said:**
> Wow, this is an amazing community. Thanks for the quick help.

Terl: (Administration > Hardware Drivers) says "No proprietary drivers are in use on this system." (Administration > Hardware Testing) recognizes the wireless card that I have, but observes, quite correctly, that I'm not connected to the internet.

Titan8990: It returned ...
iwl3945   98894   0
rfkill    17176   4 thinkpad_acpi,iwl3945
mac80211  216820  1 iwl3945
led_class 2164    2 thinkpad_acpi,iwl3945
cfg8021   32392   2 iwl3945,mac80211

I assumed that means that the driver is there, but I don't know if that means its working.

On the question of "$", I wasn't concerned about which character was being used, I just mean that the command line doesn't reappear when a previous command was executed. (And I'm not really a huge fan of or proficient with unix, I'm just familiar with basics of how it works.)

To get back to were the previous command was, type clear . I think typing history give all your previous commands. It should return to # symbol in Linux. If you wanted Unix, go to DesktopBSD ;)

---

### Post by jtsc on 2009-01-19
For lspci, it returns the important value...

03:00.0 Network Controller: INtel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

... along with 22 other components.

For ifconfig -a there is output for eth0, lo, pan0, wlan0, and wmaster0; the full output for wlan0 is...

Link encap:Ethernet HWaddr 00:1c:bf:b3:f4:fa
inet6 addr: fe80::21c:bfff:feb3:f4ffa/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:318 (318.0 B)

I'm really excited about iwconfig because it implies the card is working and found a connection.

wlan0 _ IEEE 802.11abg ESSID:"Chicago Rat Pack"
[INDENT][INDENT]Mode:Managed Frequency:2.412GHz Access Point 00:1F:33:2D:0F:66
BitRate=54 Mb/s Tx-Power+15 dBm
Retry min limit: 7 RTS thr:off Fragment thr=2352 B
Power management:off
Link quality=69/100 Singal level:-64 dBm Noise level=-127 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/INDENT][/INDENT]

(and lo and eth0 &c are also there, but say "no wireless extensions") "Chicago Rat Pack" is the most powerful signal right here, although I want to connect to a different one; but "network connections" doesn't link any working connections, let alone any available wireless networks. What am I doing wrong?

---

### Post by pastalavista on 2009-01-19
If you can, connect to the Internet via ethernet cable. Then let the update manager find what's missing. You may need something you don't have. Did you try it first with the live CD? Did wireless work then?

(Be sure to check third-party repos in System > Administration > Software Sources)

---

### Post by jtsc on 2009-01-19
Unfortunately, I don't have working ethernet in my apartment (although I might try that tomorrow at work). Just to summarize for those tuning in:

My laptop isn't connected to the internet, system>admin>network connections doesn't have any connections, and there are no wireless networks listed as found, BUT the driver is loaded, and iwconfig seems to indicate that the wireless card is talking to a network (although not my network). So I think I'm missing something pretty basic.

---

### Post by mrbiggbrain on 2009-01-19
ctrl + c (^c) will stop any command, and close your programs (man pages, ect)

---

### Post by jtsc on 2009-01-19
thanks mr. bigbrain! I've figured out my problems with terminal (it was q I needed, I'm afraid :( )

Further thoughts... I have a "Network Tools" under "System>Admin" but not "Network Manager," which the help file [refers to]("https://help.ubuntu.com/8.10/internet/C/wireless-connecting.html"). Is this why I'm not seeing the connection or the networks?

Also, "sudo lshw -C network" doesn't return any of, {CLAIMED, UNCLAIMED, ENABLED, DISABLED} next to my wireless card, as the help page implies it will. Is that a problem?

---

### Post by Titan8990 on 2009-01-19
It might be. Try the following commands (assuming your wireless ap is a DHCP server):


sudo ifconfig wlan0 up

sudo iwconfig wlan0 essid YOURWIRELESSNET

sudo dhclient wlan0


Then check ifconfig to see if you got an IP address.

Also a good test to see if you wireless is working properly is to scan for APs:

iwlist wlan0 scanning

---

### Post by jtsc on 2009-01-20
Titan - Thanks for sticking through this. It is, indeed, a DHCP network. I should mention, though, that the way my network works is that the network itself is unencrypted, but you need to authenticate on a browser you are actually connected to the internet. What I got was...

wmaster0: unkown hardware address type 801
wmaster0: unkown hardware address type 801
Listening on LFP/wlan0/00:1c:bf:b3:f4;fa
Sending on LFP/wlan0/00:1c:bf:b3:f4;fa
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

--- And indeed, I just checked network connections, network tools, and firefox, and nothing has changed.

---

### Post by jtsc on 2009-01-20
The iwlist wlan0 scanning result:

Cell 01 -
Address: 00:1F:6C:AB:65:A0
ESSID:"uchicago"
Mode:Master
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=59/100 Signal level:-72 dBm Noise level=-127 dBm
Encryption key:off
Bit Rates:1MB/s; 5.5 Mb/s; 11 Mb/s
Extra:tsf=00000b8085bf718b
Extra: Last beacon: 36m ago

---

### Post by jtsc on 2009-01-20
It's working! amazing. thanks to everyone who helped.

---

### Post by pastalavista on 2009-01-20
To bring your network manager up, hit Alt+F2 for a command interface (or in a terminal) type 'nm-applet'.. it should be installed by default.

edit: never mind... good show!

---

### Post by Titan8990 on 2009-01-20
> **jtsc said:**
> It's working! amazing. thanks to everyone who helped.

Excellent. Good to see you got it working.

---

