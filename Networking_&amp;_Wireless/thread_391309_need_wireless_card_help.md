---
title: "need wireless card help"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by dangeresque on 2007-03-23
im pretty new to linux and i have been trying different distros to see which one i like. i am currently using ubuntu ultimate 1.3. i have a ipw 2200bg card and i cant get it to work. under the network manager it shows it as enabled put i can't see any networks or connections. any help would be welcome.

---

### Post by gradedcheese on 2007-03-23
I prefer to build the driver for the ipw cards (the drivers are quiet good and it's niceto have the latest one).  If you want to go that route, it's not terribly difficult.

However you might want to ensure that linux-restricted-modules is installed (check Synaptic for it).  Intel's cards require a proprietary regulatory domain daemon, hence the driver isn't 100% open source (well, sort of: the daemon is in user space) and thus distributions won't normally distribute it.  If you want to know why the regulatory daemon is there, you can check out [my article]("http://andrey.thedotcommune.com/wireless.html").

---

### Post by dangeresque on 2007-03-23
doesn't ubuntu already have the 2200 drivers? i mean it can see the card. i just can't connect to anything.

---

### Post by gradedcheese on 2007-03-23
It sure does.  But like I told you, it probably didn't come with the regulatory daemon (which you can/must add yourself) since that's a closed-source program.

---

### Post by dangeresque on 2007-03-23
how do i add it then?

---

### Post by gradedcheese on 2007-03-23
As I said in my first post, you need to install a package called "linux-restricted-modules", search for that in Synaptic or update your package list and and install it from the shell:

```

sudo apt-get update
sudo apt-get install linux-restricted-modules-`uname -r`

```

If, instead, you want to build the driver from source, you'll find the URL to grab the daemon from and what to do with it in the install instructions.

---

### Post by dangeresque on 2007-03-23
synaptic shows that i have linux-restricted-modules-2.6.17-10-generic
                                                                                               2.6.17-11-generic
                                                                                               common
                                                                                               generic

thanks for all the help

---

### Post by gradedcheese on 2007-03-23
Ah, alright.  Do you have an ipw2200 firmware file in /lib/firmware/2.6.17-11-generic ?  Do an ls on that directory and check...

If you don't have the firmware, you can get it here: [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)

Also, I think I'm thinking of ipw3945, ipw2200 doesn't need the daemon, so forget about that.

---

### Post by dangeresque on 2007-03-23
i have ipw2200-bss.fw, ipw2200-ibss.fw and ipw2200-sniffer.fw among other things in that file

---

### Post by gradedcheese on 2007-03-23
hmm... it should be working then.  Here are some quick troubleshooting steps:

1) make sure the module is loaded (it should be since the card shows up, but do check)
```

lsmod | grep ipw

```
should return something like ipw2200

2) try scanning manually, I'm assuming your wireless is eth1.  if you don't know which interface it is, run "iwconfig" to see what has wireless extensions:
```

sudo iwlist eth1 scan

```
do you see any results?

If not, then I really would recommend just building the driver from source.  Let me know if you need help/instructions.

oh!  Also some laptops with Intel WiFi have a wireless on/off switch (shuts off the RF).  Does yours have that?  You sure it's on?  I've noticed that a lot of people get nailed by this, either they forgot it exists or didn't know about it and had it 'off' by mistake.

---

### Post by dangeresque on 2007-03-23
got this from the first thing

ipw2200               115652  0 
ieee80211              35272  1 ipw2200

and this from the second

 Cell 01 - Address: 00:13:10:94:0A:D0
                    ESSID:"nuwireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=73/100  Signal level=-55 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 28ms ago
          Cell 02 - Address: 00:18:F8:C7:9B:1B
                    ESSID:"Home-net"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-75 dBm  
                    Extra: Last beacon: 260ms ago
          Cell 03 - Address: 00:13:10:94:0A:DC
                    ESSID:"nuwireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 320ms ago
          Cell 04 - Address: 00:13:10:94:0A:D9
                    ESSID:"nuwireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-61 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 92ms ago

---

### Post by gradedcheese on 2007-03-23
um... your card works fine then :)

Are you really using networkmanager?  

```

ps aux | grep NetworkManager

```

should show one or two processes (beside grep)

If not, consider installing it (search the forums for a howto guide).  The Gnome Network tool (network monitor) has some problem where it sometimes won't show scan results.  NetworkManager doesn't have that problem.

---

### Post by dangeresque on 2007-03-23
im running kde and using knetworkmanager. the same program worked fine for me when i was running suse 10.2

that command shows this

root      4507  0.0  0.3  12176  1928 ?        Ssl  Mar22   0:01 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      4522  0.0  0.2   2960  1248 ?        Ss   Mar22   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      8852  0.0  0.1   2804   772 pts/3    S+   00:24   0:00 grep NetworkManager

---

### Post by handaxe on 2007-03-23
An alternative to NetworkManager and Network Monitor is Wicd.  Some folk have found success with it.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There is a deb install (gdebi should run when you click on the downloaded deb file). Also installs a tray icon BUT does not put an entry is startup. You do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper).

See how this goes. Good on different encryption types. You might uninstall any other managers first.

HA

---

### Post by gradedcheese on 2007-03-23
Ok.  NetworkManager ignores any interfaces that are listed in /etc/network/interfaces, open that file (with sudo) in a text editor and ensure that eth1 (or whatever your WiFi interface is) is commented out.  Comment are lines that start with a '#'.  If you had to make changes to that file, save it and then reboot.  NetworkManager should now see your interface and show scan results.

Don't switch away from NetworkManager, the next Ubuntu is due in a few weeks and it standardizes on NetworkManager as the default way to do this.  This will also be the norm in just about any distribution.  NetworkManager is well integrated (uses dbus, etc) so applications like Banshee (and soon others) will take advantage of it.  Might as well use it then :)  Plus it's quiet good at what it does.

---

