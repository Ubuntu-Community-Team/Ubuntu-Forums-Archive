---
title: "can connect to WiFi, but not Internet"
date: 2017-02-07
forum: Networking &amp; Wireless
---

### Post by scott2162 on 2017-02-07
I'm running Ubuntu 10.04 (+Gnome) and I just installed an LB-Link BL-LW05-AR wifi USB adapter.  I ran an install.sh script that came with the adapter.  I can connect to my home WiFi network and I'm getting an IP assigned to wlan0.  But I can't get to any websites with my browser.  I can ping outside my network.  I tried pinging 8.8.8.8 (Google's DNS server) and it responded in 15mS.  Any suggestions?

--Scott

---

### Post by bearlake on 2017-02-07
Ubuntu 10.04 is no longer getting updates and hasn't for a long time.

Download 14.04.xx LTS or 16.04.xx LTS.

Likely your usb wifi adapter will be picked up on the installation.

---

### Post by gdesilva on 2017-02-07
If you can ping 8.8.8.8 then you do have access to the Internet - the problem could be in your browser settings. A quick test would be to try another browser but as bearlake suggests it is far better to upgrade your system to a supported version just from a security point of view.

---

### Post by scott2162 on 2017-02-08
> **bearlake said:**
> Ubuntu 10.04 is no longer getting updates and hasn't for a long time.

Download 14.04.xx LTS or 16.04.xx LTS.

Likely your usb wifi adapter will be picked up on the installation.

I should have been more clear, I have version [COLOR=#252525][FONT=sans-serif]10.04.4 LTS.  Also I can't upgrade the OS.  The PC is a controller for a CNC milling machine (Tormach PCNC 1100) which runs a custom version of LinuxCNC.  I wouldn't want to upgrade and take a chance it broke something with the CNC software.

I don't think it's the browser because if I plug an Ethernet cable into the PC, the internet works fine.  The Ethernet cable connection is on the same LAN as the WiFi.   Right now the computer is in my house, so I have both wired and wireless connections.  But when I put it back on the CNC machine, I only have wireless internet.

--Scott


[/FONT][/COLOR]

---

### Post by Hadaka on 2017-02-08
Hi, you state..
"[COLOR=#252525][FONT=sans-serif]computer is  in my house, so I have **both** wired and wireless connections.  But when I  put it back on the CNC machine, I **only** have wireless internet."
I suggest you check your router configuration at home where you state all is well and then compare it to your router with the CNC machine.
You loaded software for the wifi USB you installed, so it may have set the wireless connection as default. I dont know anything about Ubuntu 10.0
but currently the wired and/or the wireless can be set to "Connect Automatically" check that also.Disable wireless and test the ethernet connection.
Then if you havent already, carefully inspect your ethernet cable for damage ,corrosion,obstructions,possible metal shaving,oils or change it out
and inspect the input at the CNC machine. As you stated..the machine works fine at home..so something at the CNC machine connection has changed.
If that machine and its CNC software is stand alone without hardware and os backup, you may have shot yourself in the foot.If the machine decided
to  fail, and being loaded with 10.0 it is most likely an older machine.You may want to invest in a cloud server space or another hard drive and clone the
one you have with everything on it. Upgrading from one OS version to the next with Ubuntu almost always ends up a poor choice, because or errors.
The best way to upgrade the OS is to start fresh with a wiped drive and load new.
Please keep us updated on your progress.

[/FONT][/COLOR]

---

### Post by scott2162 on 2017-02-08
I'm not trying to solve a problem I'm having with my CNC machine.  The CNC machine is being moved to a new location.  The old location had a wired internet connection that worked fine.  The new location only has wireless.  So I brought the linux PC that runs the machine home so I could get the wireless setup on it.  I only brought it home because it's more convenient to set things up at my home office.

---

### Post by Hadaka on 2017-02-08
Hi, I am fully aware you are not having a problem with your CNC machine.
I can only speculate i some how missed the logic in the statement from you...
"[COLOR=#252525][FONT=sans-serif]computer is  in my house, so I have **both** wired and wireless connections.  But when I  put it back on the CNC machine, I **only** have wireless internet."
Reading that, my impression was that you only had WORKING wireless access and no WORKING hardwired ETHENET access...but instead and please correct me if i am 
still not understanding...I now "guess" you ment you only have access TO wireless and it is NOT working. ~ * IF this is correct *
Then if it works both wired and wireless at home, the configuration is different in the router where the CNC machine is and your home. Access
the router configuration and set it up exactly like the router at home. If it still fails, attach an ETHERNET cable to the router that is located where the CNC
machine is and then post the output of the wireless-info.txt that is generated in your home directory when you do... 
[CLOSE]wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && chmod +x wireless-info && ./wireless-info[/CODE]
Thanks.

[/FONT][/COLOR]

---

### Post by scott2162 on 2017-02-08
Sorry for the confusion.  I have not moved the CNC to the new location yet, I'm hoping once I get wireless to work at home, it will also work at the new location.  I have the linux PC at home right now.   At home my wired connection works fine.  I can browse to sites on the Internet.  But wireless isn't working properly.  I can get wlan0 to connect to my home wireless network, and I can even successfully ping out to the internet (I pinged 8.8.8.8).  But when I open the Firefox browser, I can't get to any web sites when using the wireless connection.  I have several other computers at home and they all work fine on my home's wireless network.

---

### Post by Hadaka on 2017-02-09
Thanks for clarifying your situation and what is and is not working.
There are several issues that at this time add to your situation, but we shall attempt
to provide some guidance. Thus far we have alot of dialog and no real data...Let's try to fix that.
From a WORKING wired connection..please COPY and PASTE..
Please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is ***wireless-info.txt***
From your directory please copy,paste and post the ***wirele*ss-info.txt**
*Additional information on the wireless script if needed..
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

*Possible issues.
1. You are attempting to get wireless working on a non supported OS 10.04
2. Diagnostic scripts and commands "may" not function correctly with your 10.04  OS
3. Your home router is likely different than the router you will be using when you move the CNC machine.
4. For precision control of your CNC machine and needed accurate input data, a wired connection is much faster,secure and stable.

Just pointing out the realities..We are more than happy to assist you anyway we can.
Thanks.

---

### Post by scott2162 on 2017-02-09
I got a certificate mismatch error when I tried that command.  See below.  I tried the--no-check-certificate suggestion, but I couldn't figure out how to use it properly. 


operator@tormachpcnc:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && chmod +x wireless-info && ./wireless-info
--2017-02-09 20:09:03--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com... 192.30.253.112, 192.30.253.113
Connecting to github.com|192.30.253.112|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2017-02-09 20:09:06--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com... 151.101.64.133, 151.101.0.133, 151.101.128.133, ...
Connecting to raw.githubusercontent.com|151.101.64.133|:443... connected.
[B]ERROR: certificate common name `[www.github.com](www.github.com)' doesn't match requested host name `raw.githubusercontent.com'.
To connect to raw.githubusercontent.com insecurely, use `--no-check-certificate'[/B]

---

### Post by Hadaka on 2017-02-09
Hi, It is probably due to your OS 10.04 so...let's do this.
From a working wired connection , open a terminal..ctrl/alt/t..and do...
```
lspci -nnk | grep 0280 -A2
uname -r
rfkill list all
lsmod | grep -v snd
```
please post the output and please use code tags.
thanks.

---

### Post by scott2162 on 2017-02-09
```
operator@tormachpcnc:~$ lspci -nnk | grep 0280 -A2
operator@tormachpcnc:~$ uname -r
2.6.32-122-rtai
operator@tormachpcnc:~$ rfkill list all
operator@tormachpcnc:~$ lsmod | grep -v snd
Module                  Size  Used by
8192cu                446078  0 
binfmt_misc             6587  1 
usbhid                 35772  0 
hid                    65804  1 usbhid
dm_crypt               11363  0 
ppdev                   5259  0 
parport_pc             25637  1 
psmouse                63213  0 
serio_raw               3978  0 
xhci                   35602  0 
lp                      7028  0 
parport                30764  3 ppdev,parport_pc,lp
dm_raid45              81157  0 
xor                    14673  1 dm_raid45
video                  17089  0 
fbcon                  35102  71 
tileblit                1987  1 fbcon
font                    7406  1 fbcon
bitblit                 4664  1 fbcon
softcursor              1151  1 bitblit
output                  1773  1 video
r8169                  33788  0 
mii                     4006  1 r8169
ahci                   31976  2 
vga16fb                11161  1 
vgastate                8760  1 vga16fb
ramzswap                6362  1 
xvmalloc                3794  1 ramzswap
lzo_decompress          2103  1 ramzswap
lzo_compress            1810  1 ramzswap
```

---

### Post by Hadaka on 2017-02-10
Hi, please use code tags when responding..it makes reading much easier.
click the "#" in the second row of icons on the response page..it will create
the tag..it looks like this -> [ CODE] [ /CODE] copy and paste your response
between those tags. [ CODE][COLOR=#ff0000]HERE[/COLOR][COLOR=#ff0000][/COLOR][COLOR=#000000][ /CODE]. 
Then please post the output of..
```
lsusb
```
then COPY and past one line at a time..*IF you get an error STOP[/COLOR],and post the error.
```
sudo apt-get update
sudo apt-get install git
```
then do..
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
thanks.

---

### Post by scott2162 on 2017-02-10
The install git didn't work  ```
 operator@tormachpcnc:~$ lsusb Bus 004 Device 004: ID 17ef:6018 Lenovo  Bus 004 Device 003: ID 046d:c069 Logitech, Inc.  Bus 004 Device 002: ID 2109:3431   Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub Bus 002 Device 002: ID 8087:8000   Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp.  Bus 001 Device 002: ID 8087:8008   Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
```  ```
 operator@tormachpcnc:~$ sudo apt-get update Hit http://linux.dropbox.com lucid Release.gpg Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US               Hit http://linux.dropbox.com lucid Release                                      Hit http://linux.dropbox.com lucid/main Packages                     Hit http://archive.canonical.com lucid Release.gpg                Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US Hit http://old-releases.ubuntu.com lucid Release.gpg Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US Hit http://old-releases.ubuntu.com lucid-backports Release.gpg Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US Hit http://archive.canonical.com lucid Release Hit http://old-releases.ubuntu.com lucid-updates Release.gpg Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US Hit http://old-releases.ubuntu.com lucid-security Release.gpg Hit http://archive.canonical.com lucid/partner Packages Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US Hit http://archive.canonical.com lucid/partner Sources Hit http://old-releases.ubuntu.com lucid Release Hit http://old-releases.ubuntu.com lucid-backports Release Hit http://old-releases.ubuntu.com lucid-updates Release Hit http://old-releases.ubuntu.com lucid-security Release Hit http://old-releases.ubuntu.com lucid/main Sources Hit http://old-releases.ubuntu.com lucid/restricted Sources Hit http://old-releases.ubuntu.com lucid/main Packages Hit http://old-releases.ubuntu.com lucid/universe Packages Hit http://old-releases.ubuntu.com lucid/restricted Packages Hit http://old-releases.ubuntu.com lucid/multiverse Packages Hit http://old-releases.ubuntu.com lucid/universe Sources Hit http://old-releases.ubuntu.com lucid/multiverse Sources Hit http://old-releases.ubuntu.com lucid-backports/main Packages Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages Hit http://old-releases.ubuntu.com lucid-backports/universe Packages Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages Hit http://old-releases.ubuntu.com lucid-backports/main Sources Hit http://old-releases.ubuntu.com lucid-backports/restricted Sources Hit http://old-releases.ubuntu.com lucid-backports/universe Sources Hit http://old-releases.ubuntu.com lucid-backports/multiverse Sources Hit http://old-releases.ubuntu.com lucid-updates/universe Packages Hit http://old-releases.ubuntu.com lucid-updates/main Packages Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages Hit http://old-releases.ubuntu.com lucid-security/universe Packages Hit http://old-releases.ubuntu.com lucid-security/main Packages Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages Hit http://old-releases.ubuntu.com lucid-security/restricted Packages Reading package lists... Done               
```  ```
 operator@tormachpcnc:~$ sudo apt-get install git Reading package lists... Done Building dependency tree        Reading state information... Done Package git is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source E: Package git has no installation candidate operator@tormachpcnc:~$  
```

---

### Post by Hadaka on 2017-02-11
Hi,I doubt you are going to get any driver to correctly compile with
Ubuntu 10.04 due to it no longer being supported. The rtl8192cu usb
module driver requires tweaking or modification. About the best i can
recommend is research and locate a chipset/usb wireless unit that is
known to "plug and play" with your current 10.04 and the exact type of
computer. The other option is to load an up to date OS like Ubuntu 16.04 .
Please keep in mind that attempting to "upgrade" from 10.04 to 16.04 will fail.
Ubuntu 16.04 will require a fresh new image and load.Sorry to say I have no
further suggestions.
Thanks

---

### Post by jeremy31 on 2017-02-11
[https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)

Then right click and see if you can "Save as" and save it as wireless-info in the home directory, then in terminal
```
chmod +x wireless-info && ./wireless-info
```

If it doesn't work post info from
```
cat /etc/resolv.conf
``````
cat /etc/network/interfaces
```

---

