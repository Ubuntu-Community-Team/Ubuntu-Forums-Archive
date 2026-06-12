---
title: "Cannot connect to wireless; no wireless card found? Lubuntu 13.04"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by larry23 on 2014-08-30
Hello.

I'll start off by saying the same hardware was working on Lubuntu 14.04, unfortunately I needed to drop back to Lubuntu 13.04 for support of specific programs.
It may also be important to note that the wireless device is built into the motherboard (gigabyte ga-z97n-gaming 5).

lspci |grep ireless:

```
04:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
```

iwconfig:

```
eth0 no wireless connection

lo no wireless connection
```

lshw does now show any device that could be a wireless device.

I will of course be happy to provide any additional info that I can.

Thank you!

---

### Post by chili555 on 2014-08-30
Please open a terminal and do:```
lspci -nn | grep 0280
lsusb
sudo modprobe iwlwifi
dmesg | grep iwl
```Thanks.

---

### Post by larry23 on 2014-08-30
Thank you for the quick reply, i appreciate it. Your command gave some interesting results (well, I get somewhat unsurprising!):

```
sedna@sedna:~$ lspci -nn|grep 028004:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
sedna@sedna:~$ lsusb
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 005: ID 04f2:0833 Chicony Electronics Co., Ltd 
Bus 003 Device 006: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
sedna@sedna:~$ sudo modprobe iwlwifi
sedna@sedna:~$ dmesg|grep iwl
[   11.267080] iwlwifi 0000:04:00.0: irq 46 for MSI/MSI-X
[   11.267975] iwlwifi 0000:04:00.0: request for firmware file 'iwlwifi-7260-6.ucode' failed.
[   11.267979] iwlwifi 0000:04:00.0: no suitable firmware found!



```

---

### Post by chili555 on 2014-08-30
> [   11.267080] iwlwifi 0000:04:00.0: irq 46 for MSI/MSI-X
[   11.267975] iwlwifi 0000:04:00.0: request for firmware file 'iwlwifi-7260-6.ucode' failed.
[   11.267979] iwlwifi 0000:04:00.0: no suitable firmware found!We're almost done! Let's get some firmware. Please do:```
cd /lib/firmware/
sudo wget https://dl.dropboxusercontent.com/u/58267392/7260.zip
sudo unzip 7260.zip
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```Is it working?

---

### Post by larry23 on 2014-08-30
Success!

Well, partial success...

I am able to connect to the wifi but unable to reach the internet through the browser.

ping [www.google.com](www.google.com) does get a response back.

Good to be on the network though!

---

### Post by chili555 on 2014-08-30
What does this tell us?```
nm-tool
dmesg | grep wlan
```I am counting the minutes before we install a newer driver and firmware, actually.

---

### Post by larry23 on 2014-08-30
```
sedna@sedna:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: wlan0  [<wifi name>] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        80:86:F2:1E:99:A2


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Hallnet2662:    Infra, 00:22:6B:7E:73:31, Freq 2412 MHz, Rate 54 Mb/s, Strength 57


  IPv4 Settings:
    Address:         192.168.1.122
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             209.18.47.61
    DNS:             209.18.47.62




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        74:D4:35:E7:CB:7C


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




sedna@sedna:~$ dmesg|grep wlan
[   14.605793] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.623310] wlan0: authenticate with 00:22:6b:7e:73:31
[   22.624024] wlan0: send auth to 00:22:6b:7e:73:31 (try 1/3)
[   22.625814] wlan0: authenticated
[   22.628957] wlan0: associate with 00:22:6b:7e:73:31 (try 1/3)
[   22.632485] wlan0: RX AssocResp from 00:22:6b:7e:73:31 (capab=0x401 status=0 aid=3)
[   22.635348] wlan0: associated
[   22.635360] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

---

### Post by chili555 on 2014-08-30
Looks pretty normal so far. Let's gather a few more details about your access point:```
sudo iwlist wlan0 scan
ping -c3 www.google.com
```Just show us the details for Hallnet2662.

---

### Post by larry23 on 2014-08-30
Well that's interesting, I'm unable to ping google now...

Results:

```
sedna@sedna:~$ sudo iwlist wlan0 scanwlan0     Scan completed :
          Cell 01 - Address: 00:22:6B:7E:73:31
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"Hallnet2662"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001cb4eed4a95
                    Extra: Last beacon: 17136ms ago
                    IE: Unknown: 000B48616C6C6E657432363632
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050600000000000000000000000000000000000000
                    IE: Unknown: DD820050F204104A0001101044000102103B000103104700102880288028801880A88000226B7E73311021000C4C696E6B73797320496E632E102300095752543136304E76321024000776322E302E3032104200033030381054000800060050F2040001101100114C696E6B737973205752543136304E7632100800020084103C000101
          Cell 02 - *<Removed from post>*


sedna@sedna:~$ ping -c3 www.google.com
ping: unknown host www.google.com



```

---

### Post by chili555 on 2014-08-30
>  Cell 01 - Address: 00:22:6B:7E:73:31
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"Hallnet2662"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:MasterThis implies *NO* encryption at all and this is quite dangerous. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, we will do some surgery.

---

### Post by larry23 on 2014-08-30
I agree with you on the wifi security, unfortunately I am at my family's place and do not have the power to change it. The wifi is a hidden network so it can only be connected to by name, hopefully that is some consolation for you. (my intent was removing the name from my posts but I missed a spot...)

I get stuck on the first step:

```
sedna@sedna:~$ sudo iw reg getsudo: iw: command not found
sedna@sedna:~$ iw reg get
The program 'iw' is currently not installed. You can install it by typing:
sudo apt-get install iw

```

And then to follow up with the next obvious step:

```
sedna@sedna:~$ sudo apt-get install iwReading package lists... Done
Building dependency tree       
Reading state information... Done
Package iw is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'iw' has no installation candidate
```

And for what it's worth:

```
sedna@sedna:~$ sudo apt-get updateIgn http://us.archive.ubuntu.com raring Release.gpg
Ign http://us.archive.ubuntu.com raring-updates Release.gpg
Ign http://us.archive.ubuntu.com raring-backports Release.gpg
Ign http://us.archive.ubuntu.com raring-security Release.gpg
Ign http://us.archive.ubuntu.com raring Release
Ign http://us.archive.ubuntu.com raring-updates Release
Ign http://us.archive.ubuntu.com raring-backports Release
Ign http://us.archive.ubuntu.com raring-security Release
21% [Waiting for headers]
```

It posts the *[Waiting for headers]* a few times, then throws several errors in the following fashions:

```
Err http://us.archive.ubuntu.com raring/restricted Sources  404  Not Found [IP: 91.189.91.15 80]



```

or

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources  404  Not Found [IP: 91.189.91.15 80
```

I've attempted to fix this issue on my own (aka through several hours of googling) over the past few days but to no avail; I figured I'd switch gears and try to get the wifi working but now they appear to be overlapping.

---

### Post by chili555 on 2014-08-30
Please tell your family that having no encryption is the equivalent of putting all your money, savings, IRAs, etc., in a shoebox on the front porch. Protecting (ha ha!) it with nothing but a hidden SSID is the equivalent of *NOT* writing "look for money here" on the box! If I ever connected to a network with no encryption, or even WEP, I'd drop off immediately and shut down my computer!> I've attempted to fix this issue on my own (aka through several hours of googling) over the past few days but to no avail; I figured I'd switch gears and try to get the wifi working but now they appear to be overlapping.Are you saying that the inability to surf the web is also a problem with ethernet? Can you get a reliable ethernet connection even temporarily? 

Please show us:```
ping -c3 192.168.1.1
ping -c3 209.18.47.61
ping -c3 8.8.4.4
```

---

### Post by larry23 on 2014-08-30
```
[COLOR=#000000]Please tell your family that having no encryption is the equivalent of putting all your money, savings, IRAs, etc., in a shoebox on the front porch. Protecting (ha ha!) it with nothing but a hidden SSID is the equivalent of [/COLOR]*NOT writing "look for money here" on the box! If I ever connected to a network with no encryption, or even WEP, I'd drop off immediately and shut down my computer!*
```

Duly noted.

```
[COLOR=#000000]Are you saying that the inability to surf the web is also a problem with ethernet? Can you get a reliable ethernet connection even temporarily?[/COLOR]
```

No, I can connect via ethernet. The problem I was referring to attempting to fix is successfully completing a** sudo apt-get update**&#8203;.

---

### Post by larry23 on 2014-08-30
[Removed duplicate]

---

### Post by chili555 on 2014-08-30
Please see my edit. What are the ping results, please?

---

### Post by larry23 on 2014-08-30
The three commands:

```
sedna@sedna:~$ ping -c3 192.168.1.1PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=0.829 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=0.456 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=0.436 ms


--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.436/0.573/0.829/0.182 ms
sedna@sedna:~$ ping -c3 209.18.47.61
PING 209.18.47.61 (209.18.47.61) 56(84) bytes of data.
64 bytes from 209.18.47.61: icmp_req=1 ttl=58 time=19.1 ms
64 bytes from 209.18.47.61: icmp_req=2 ttl=58 time=17.5 ms
64 bytes from 209.18.47.61: icmp_req=3 ttl=58 time=18.7 ms


--- 209.18.47.61 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 17.508/18.465/19.127/0.702 ms
sedna@sedna:~$ ping -c3 8.8.4.4
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.
64 bytes from 8.8.4.4: icmp_req=1 ttl=46 time=45.6 ms
64 bytes from 8.8.4.4: icmp_req=2 ttl=46 time=47.4 ms
64 bytes from 8.8.4.4: icmp_req=3 ttl=46 time=44.5 ms


--- 8.8.4.4 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 44.568/45.918/47.498/1.219 ms



```

---

### Post by chili555 on 2014-08-30
Those are awesome results. I wonder why surfing the web, updates, etc. aren't also awesome. ???

What is your running kernel version?```
uname -r
```

---

### Post by larry23 on 2014-08-30
```
sedna@sedna:~$ uname -aLinux sedna 3.10.1-031001-generic #201307131550 SMP Sat Jul 13 19:51:31 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by chili555 on 2014-08-30
Please get a temporary wired ethernet connection and do:```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
```Download this to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.8/backports-3.12.8-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.8/backports-3.12.8-1.tar.xz) Right-click it and select 'Extract Here.' Now open a terminal and do:

```
cd Desktop/backports-3.12.8-1/
make defconfig-iwlwifi
make
sudo make install
```
Now download the required firmware here: [https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode](https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode) Now open a terminal and do:

```
sudo cp ~/Desktop/iwlwifi-7260-7.ucode /lib/firmware/  <--or wherever you downloaded it if not desktop
sudo modprobe -r iwldvm  <--If it is not loaded, OK, please proceed
sudo modprobe -r iwlwifi <--If it is not loaded, OK, please proceed
sudo modprobe iwlwifi
```Your wireless should now be working much better.

I will be away for a bit. Post back any errors, roadblocks, etc.

---

### Post by larry23 on 2014-08-30
Here's what I get with the first set of commands:

```

sedna@sedna:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com raring Release.gpg
Ign http://us.archive.ubuntu.com raring-updates Release.gpg
Ign http://us.archive.ubuntu.com raring-backports Release.gpg
Ign http://us.archive.ubuntu.com raring-security Release.gpg
Ign http://us.archive.ubuntu.com raring Release
Ign http://us.archive.ubuntu.com raring-updates Release
Ign http://us.archive.ubuntu.com raring-backports Release
Ign http://us.archive.ubuntu.com raring-security Release
Err http://us.archive.ubuntu.com raring/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://us.archive.ubuntu.com raring/main Translation-en_US
Ign http://us.archive.ubuntu.com raring/main Translation-en
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring/restricted Translation-en
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring/universe Translation-en
Err http://us.archive.ubuntu.com raring-updates/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-updates/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-updates/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en
Err http://us.archive.ubuntu.com raring-backports/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-backports/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-backports/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-backports/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-backports/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-backports/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-backports/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-backports/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en
Err http://us.archive.ubuntu.com raring-security/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-security/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-security/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-security/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-security/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-security/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com raring-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://us.archive.ubuntu.com raring-security/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-security/main Translation-en
Ign http://us.archive.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com raring-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-security/restricted Translation-en
Ign http://us.archive.ubuntu.com raring-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-security/universe Translation-en
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
sedna@sedna:~$ sudo apt-get install linux-headers-generic build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'build-essential' has no installation candidate

```

Should I still continue on with downloading the file?

---

### Post by chili555 on 2014-08-30
Nope.

I think I get it. Raring, Ubuntu 13.04, is beyond its end of life and the repositories are closed so no updates, new software, etc. is available.

Would you care to try 12.04.4 LTS?

---

### Post by larry23 on 2014-08-30
Ahh okay I understand.

12.04 *might* be a solution, I will need to do some investigating on that front. Is it possible to update what I need to update without the repo?

---

### Post by chili555 on 2014-08-30
In order to compile the driver, you need several prerequisites. They need to match your kernel, gcc, etc. versions. Without them you are stuck.

---

### Post by larry23 on 2014-08-30
Rough, so it sounds like either 12.04 LTS or 14.04 LTS.

Okay, thanks a bunch for the help! You're a rockstar!

---

