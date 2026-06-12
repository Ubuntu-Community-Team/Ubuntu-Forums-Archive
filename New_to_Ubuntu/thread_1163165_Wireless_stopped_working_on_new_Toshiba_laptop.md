---
title: "Wireless stopped working on new Toshiba laptop"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Zachx65 on 2009-05-18
Hello again. New computer, new problems, ever more grateful UbubtuForums exists. ;)

 Yesterday I bought a Toshiba Satellite L305D-S5934. I got it home, burned a fresh copy of 9.04(desktop edition), installed it as my only OS and everything was well. This morning, for what seemed like no reason at all, the wireless stopped working. It just kept trying to connect to my network, after about 45 seconds a dialog would appear prompting for a network key. I had already entered the key when I first connected to the wireless network, but for some reason Ubuntu was automatically filling in a very long key that did not match anything in my router config.

 I had/have no clue what went wrong, so I tried downgrading to 8.04. Now it shows no wireless networks in the task bar, compared to the six or so networks(apartment complex) that 9.04 was showing.

Here is lspci
```
zach@zbox:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

``` 


and iwconfig
```
zach@zbox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

please let me know if there are other command outputs I need to post, thanks!

---

### Post by anewguy on 2009-05-18
First, 9.04 I believe has driver support for the Atheros AR242x built-in, where 8.10 and 8.04 don't.  For those releases you need to install the driver.  If you use the search function on the forum and ar242x you will find many post on getting that part working.

Second, and only after you have installed your wireless driver (or gone back to 9.04 - I would recommend that), keep the following in mind:

your network passwords are stored on a logical keyring in the system.  There is a password required just to get at that keyring.  Normally, the first time you connect to a network requiring a network password, it will also ask you for a password for the keyring.  Always use your logon password for this or you will be prompted each time for that password.

be sure you know the actual network password - wep, wpa, etc., and it's format - password, passphrase, type - usually something like text or hex, the number of bits.  You must match this when prompted for the actual network password.

So, get your wireless driver installed, or just go back to 9.04, then watch the passwords - 1 password for the keyring, a different one and type for the actual network security.

Dave :)

---

### Post by Zachx65 on 2009-05-19
Well I just got back from work and reinstalled Jaunty. Wireless is working, we'll see if it stays that way. I wasn't prompted for any key ring PW, just the network key.

---

### Post by daemon3 on 2009-10-30
Same problem here. I even tried downloading the driver via the instructions from the Atheros site.  For one session, the wireless was visible, but not functional; the next session the wireless was not visible.
I just upgraded to Karmic Koala...didn't seem to fix anything.
```

user@host:~$ lspci | grep Wireless
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

---

### Post by pbateman on 2009-10-30
That  Atheros card is a pain....i should know.
Quick question, is your SSID being broadcasted? One thing I noticed after months of trial and error with 9.04 is that if my SSID was not being broadcasted it caused me a lot of issues (took forever to connect, no automatic reconnection after reboot, loss of connection etc..) after I enabled SSID broadcasting, everything was much smoother.
I just installed 9.10 and tried again with the hidden SSID and  seems this time around its acting much better...

---

### Post by ses717 on 2009-11-05
Had same problem on Toshiba laptop after a crash with 9.10.
 
Ran this command:
 
sudo nm-applet --sm disable &
 
It restarted the applet and the wireless and it worked.  Got help from a co-worker.
 
Don't know much more but thought I'd pass this on.
 
SS

---

