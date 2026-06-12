---
title: "Correct way to disable wifi adapter"
date: 2020-07-19
forum: Networking &amp; Wireless
---

### Post by aboka on 2020-07-19
hi, im using Ubuntu 20.04 and like to know how we could disable the wifi adapter. i need to re-enable it when needed.

this command will disable the adapter - ifconfig wlan1 down. so i think adding a script and run at system boot will solve this.

so i add 'disablewifi.sh' with the command below, add the script into '/etc/init.d' folder and make it executable by running 'chmod +x disablewifi.sh'
```
#!/bin/bash
sudo ifconfig wlan1 down
```

but the system lockup when rebooting with this repeating message-
```
...mmc0: timeout waiting for hardware interrupt.
```

luckily its an external wifi adapter so i unplug it and switch off the power and reboot. then all ok and back to CLI

p/s - it is wlan1 bcoz its an external adapter. i only hv wifi connection, so jus to be safe, i test on an external adapter

p/ss - hv tried adding this into /etc/rc.local file, but it doesn't seem to do anything so i try this instead

Please advice.

Thank you,

---

### Post by pcfan1234 on 2020-07-20
Why don't use rfkill?
```
root@celsius:~# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@celsius:~# 


```
```
sudo rfkill block 0
```

---

### Post by aboka on 2020-07-22
> **pcfan1234 said:**
> Why don't use rfkill?
```
root@celsius:~# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@celsius:~# 


```
```
sudo rfkill block 0
```

hi, sorry for late reply as dont know why i dind't rcv any notification. i hv install and run the rfkill utulity and here is the output:
```

0: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no

```

but after reboot, the wifi is still showing when i run iwconfig:
```

wlan0     IEEE 802.11  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

or we hv to run it whenever system boot? if yes, how? add the line below to [COLOR=#242729][FONT=Consolas]/etc/rc.local[/FONT][/COLOR]?
```

sudo rfkill block 0

```

Thank you,

---

### Post by pcfan1234 on 2020-07-22
rc.local should work, although that is not made for systemd.
You can also try to disable you WiFi adapter in the laptop's BIOS.

---

### Post by TheFu on 2020-07-22
Using the BIOS method, should save battery.  Other methods probably do not.

I haven't seen a working rc.local without extra steps since systemd became the init system. How to accomplish that has many how-to guides that a web-search will easily find.

I usually use a wired ethernet connection and don't have the wifi enabled or set to automatically connect. Just use wicd-curses to manage that connection with wired-ethernet given priority.  To prevent any Bluetooth, I hard lock it and remove all the blu* packages.  I've been hacked over a bluetooth connection on a freshly installed and patched Ubuntu. Never again. No BT here, ever. The security is just terrible, but can be fun in hotels if you are slightly evil. ;)

---

### Post by aboka on 2020-07-22
hi, i think its rfkill not really working. as i enable and disable it using block and unblock, the wifi is still shows(iwconfig) or it needs a reboot whenever there is changes? using rfkill list, it show 'yes/no' means it has successful on/off the adapter

sorry i didn't mention this earlier - im on a Raspberry Pi 3. so is this the correct and best way to disable its built-in wifi?

p/s - is it bcoz this is a Pi and no way to disale its built-in wifi? as i try ifconfig wlan0 down, but it is still showing....

thank you,

---

### Post by aboka on 2020-07-22
p/ss- initially i was using wifi to setup the Pi so i change some settings in the netplan file. now im using LAN connection, so i remove the wifi entry and put in this:
```

network:
        version: 2
        ethernets:
                eth0:
                      dhcp4: no
                      addresses: [192.168.0.13/24]
                      gateway4: 192.168.0.1
                      nameservers:
                              addresses: [8.8.8.8,8.8.4.4]

```

---

### Post by praseodym on 2020-07-24
Blacklist the driver

---

### Post by TheFu on 2020-07-24
r-pi is pretty important to mention.  I'm out.  Good luck.

---

### Post by aboka on 2020-07-25
> **praseodym said:**
> Blacklist the driver

hi, could you guide us on how to do that?

p/s - sorry didn't mention about Pi as only thought of the OS - Ubuntu. and i believe this might be relate to why its so tricky. as the solution i search online either is on Raspberry Pi(Raspbian), or 'normal Ubuntu'

thank you,

---

