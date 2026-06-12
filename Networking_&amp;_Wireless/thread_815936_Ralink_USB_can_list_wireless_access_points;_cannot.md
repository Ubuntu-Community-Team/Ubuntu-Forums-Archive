---
title: "Ralink USB can list wireless access points; cannot connect"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by FSHero on 2008-06-02
Before I begin describing my problem, I just wanted to say that the wireless card I mention below came "integrated" with my computer (A Medion 8383XL (I think!)) -- so despite it being described as a USB network card, there is no "USB stick" -- it is all inside the computer case. Peculiar, if you ask me!

Basically... I am able to get the wireless network card working in Kubuntu 7.04 (Feisty), but not in Hardy (or Gutsy -- but I'm not interested in Gutsy anymore). In Feisty, I can't remember the exact procedure, but I remember that KNetworkManager didn't work. Thus, I went to System Settings --> Network settings. I select rausb1 from the list, click Configure interface... and fill in all my details (ssid, wep key etc.) I then apply the settings in the Network Settings page, and click "Enable Interface". Then, it is assigned the IP address 192.168.0.3 and my internet and LAN works.

In the Hardy live-cd environment, I can right-click on KNetworkManager to see a list of wireless network access points near me (my own one included). (Note: I haven't done a hard-disk install of Hardy yet due to this problem -- I need the internet critically.) Thus, I click on my one (whose SSID I shall refer to as "MY_ESSID") and am given a prompt. I type in my hexadecimal WEP key, choose "WEP 40/104-bit hex" from the Authentication drop-down list. I click "OK". A yellow 'tooltip' appears in the System Tray (bottom RHS; is this the correct name?), with a percentage bar. It seems to stall at "57%: IP configuration started". After about a minute, I am prompted again for my WEP key.

So, even if I keep trying to enter my WEP key, I cannot connect to my wireless network. I tried to adopt my 'Feisty' approach, by right-clicking KNetworkManager and clicking on "Manual configuration". I select wlan0 from the list (no rausb1!) and click "configure interface". Under TCP/IP settings I choose "Automatic", dhcp. Under Wireless Settings, I enter my SSID, my WEP key and I choose "hexadecimal" from the "key type" drop-down list. I click OK, then in the KDE control module, I click apply. In the KDE control module, it says that wlan0 is enabled... but unlike in Feisty, there is no IP address assigned to wlan0.

I am stuck!!! I know from [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660) that ralink-based cards (including my own) had problems with Gutsy. I remember reading in some forum posts, however, that compiling the latest drivers would work. I was kind-of hoping that Hardy would have such updated drivers, but alas... no result.

How am I so sure that my wireless chipset is Ralink-based, you say? If I do a lspci in Feisty, one of the lines is the following:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660)

As described on [http://ubuntuforums.org/showthread.php?t=106846&highlight=rt2570](http://ubuntuforums.org/showthread.php?t=106846&highlight=rt2570) I tried to compile the rt2570 driver from serialmonkey/sourceforge ([http://sourceforge.net/project/showfiles.php?group_id=107832&package_id=144813&release_id=426215](http://sourceforge.net/project/showfiles.php?group_id=107832&package_id=144813&release_id=426215)). This was done from the Kubuntu Hardy live-cd. It failed at the "make" stage. (I can't remember the exact messages).

Again from my live-cd, I tried to sneakily copy the file /media/feisty/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko to my live-cd's /lib/modules/`uname -r`/drivers/, then tried to "sudo insmod /lib/modules/`uname -r`/drivers/rt2570.ko". This failed -- I can't remember the error message.

I also tried Knoppix 5.3.1 -- on the "Penguin" on the KDE Panel, I went to Network setup (correct name?) and tried to setup the wireless connection. I selected my router's SSID from a list and typed a WEP key in, but some sort of error came up.

I have run lsmod, lsusb, lspci, lshw (Kubuntus) and lshal (Knoppix) in all three aforementioned environments, for reference. Briefly, I noticed that in Feisty, the kernel module loaded was "rt2570", but in Kubuntu Hardy, there were rt2500usb, rt2x00usb, rt2x00lib, rfkill, input_polldev, crc_itu_t, mac80211.

Thus... how can I get my wireless network card working in Kubuntu Hardy? But perhaps more importantly, is there a <b>good chance</b> that, after installing to hard disk, I can get this working? That way, I can be confident in installing Hardy -- I want to reinstall Windows XP, then (fresh non-upgrade) install Kubuntu Hardy and Fedora 9 onto my computer. I wouldn't happen to need some firmware from Ralink's website, would I?

Attachments: the files attached to this post are from Kubuntu 8.04. (output of lsusb -v is compressed to avoid the file-size limit of the forum!)

Thanks to everyone in advance -- and I apologise if I have failed on something easy!

---

### Post by FSHero on 2008-06-02
Attached to this post: the output of various commands from my Kubuntu 7.04 Feisty (hard-disk installed) environment. Again, .tar.gz files contain text files, but are compressed to avoid the forum's file size limits on .txt files.

---

### Post by FSHero on 2008-06-02
Attached to this post is the output of various commands run in the Knoppix 5.3.1 live-cd environment. Again, .tar.gz files are used to overcome the file size limit posed by this forum.

I would also like to say: if anyone wants the short output of commands (e.g. "lspci" instead of "lspci -v"), I have them in text files and can upload them.

---

### Post by FSHero on 2008-06-03
I just got my wireless network interface card working with Hardy! I have a Medion 8383 computer with a Ralink USB network adapter (but it is *inside* the case). I am running a hard-disk install of Kubuntu 8.04 i386. My wireless network interface worked out-of-the-box in Feisty (7.04) -- it used the module "rt2570", so this is the module I sought to compile.

Basically, I shall go over the procedure that I think got the network card working. Then, I shall go over some of my pitfalls. Do not hesitate to correct me / contact me if I have made an error in my explanations, or if I have done something 'dangerous'!

All the following was done on a fresh install of Kubuntu. After downloading the file from a different computer and putting it onto a USB disk, I compiled the driver from SerialMonkey: rt2570-cvs-daily.tar.gz (retrieved on 2008-06-01). I copied it to a folder where my data is kept (you could use your home folder) and to compile it, I ran, from Konsole, in the rt2570-cvs-2008060113/Module directory:
```

make
sudo make install

```

This resulted in the file "rt2570.ko" being created in the current directory. I made a directory and copied it there:
```

sudo mkdir /lib/modules/`uname -r`/drivers
sudo cp rt2570.ko /lib/modules/`unamme -r`/drivers

```

I "regenerated" the module dependency list:
```

sudo depmod -a

```

I then edited /etc/modprobe.d/blacklist -- to do this, I did K-menu --> Run command... --> typed in "kdesudo kate" --> Opened the file /etc/modprobe.d/blacklist. I typed in at the end:
```

blacklist rt2500usb

```
(I did this because this module was automatically loading on my computer, and was useless (see [http://ubuntuforums.org/showthread.php?t=815936](http://ubuntuforums.org/showthread.php?t=815936)) -- other people may need to blacklist a different module.)


Now, I did two things that could have had a positive effect (they both appear to do identical things):
(1) I went to K-menu --> System Settings --> Network Settings (icon). I clicked "Administrator Mode", selected "rausb0" from the list and clicked "Configure interface". I selected DHCP, filled in my ESSID and typed in my hexadecimal WEP key.

(2) In the file /etc/network/interfaces, I added:
```

auto rausb0
iface rausb0 inet dhcp

	pre-up ifconfig rausb0 down
	pre-up iwconfig rausb0 essid "MY_ESSID"
	pre-up iwconfig rausb0 mode managed
	
	wireless-essid "MY_ESSID"
	wireless-key WEP_KEY_HERE

```

Anyways... upon rebooting, the wireless connection was established and I had internet access! (And I was welcomed by a >100MB update...) Please note: I did not put "rt2750" in my /etc/modules file. I hoped that upon rebooting, the module would automatically load due to hardware detection -- and it did (confirmed with lsmod)!

By 'pitfalls', I mean that I tried various things along the way that failed to get my wireless connection working. These are:
1) Using KNetworkManager seemed useless throughout -- although it detected the wireless networks in range using the rt2500usb module (bizarre). Also, I didn't use it after that -- I jumped straight to System Settings --> Network Settings as described above.
2) The post [http://ubuntuforums.org/showthread.php?p=594575](http://ubuntuforums.org/showthread.php?p=594575) described compiling the driver from SourceForge ([http://sourceforge.net/project/showfiles.php?group_id=107832&package_id=144813&release_id=345856](http://sourceforge.net/project/showfiles.php?group_id=107832&package_id=144813&release_id=345856)). However, on my Kubuntu 8.04 it failed to compile (at the "make" command).
3) Unloading the module rt2500usb using ```
sudo modprobe -r rt2500usb
``` then loading the module rt2570 using ```
sudo insmod /lib/modules/`uname -r`/drivers/rt2570.ko
``` did not work. I tried to enter my wireless configuration settings in System Settings --> Network Settings, but then rausb0 always failed to be "enabled". This suggests to me that the rt2570 module must be loaded at the same time as the other modules, before anything else (I don't know what) loads.
4) There is no 4. (I can't think of anything else to put down!)

I hope this helps someone. It is largely identical to other posts on the Ubuntu forums. I would attach my rt2570.ko as a .tar.gz, but on my computer it is 1.1MB, and is over ubuntuforum's 976KB file size limit :(

References:
[http://ubuntuforums.org/showthread.php?p=594575](http://ubuntuforums.org/showthread.php?p=594575)
[http://ubuntuforums.org/showthread.php?p=3588610](http://ubuntuforums.org/showthread.php?p=3588610)
[https://bugs.launchpad.net/134660](https://bugs.launchpad.net/134660)

---

### Post by FSHero on 2008-06-03
I just wanted to say that I went ahead with the hard-disk install, and obviously I got the network card working -- but my previous post reads as if it were out of context because I was planning to post it in a different thread.

---

### Post by FSHero on 2008-06-03
D'oh! The kubuntu updates included a different kernel! Hence, I had to recompile the driver!! And I had to redo my /etc/network/interfaces file!!! It goes like this:
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto rausb0
iface rausb0 inet dhcp
	pre-up ifconfig rausb0 down
	wireless-essid MY_ESSID
	wireless-key WEP_KEY_HERE
	wireless-mode managed

```
I think it was the interfaces file that was responsible for the successful connection of the wireless network card: after the kernel update I tried to enter the details through System Settings --> Network settings, but only after I put the stuff in /etc/network/interfaces did the wireless NIC connect to my router. Joy! (Until the next kernel update)

---

### Post by FSHero on 2010-08-17
Sorry to revive this thread... but the installation of Kubuntu 10.04 Lucid means that my Ralink problem has returned to haunt me, and I need the help of the awesome Ubuntu community!

Some facts:

[LIST]
[*]After 8.04 was released, something big happened: namely, the support for the SerialMonkey legacy (rt2400) drivers has sadly been discontinued (stopped in 2009).
[/LIST]

[LIST]
[*]Also, in Feisty (7.04), I was able to connect to a WEP (not WPA - reason unknown) access point with driver rt2570, but 8.04 onwards I was unable to connect to anything using default configuration (rt2500usb driver).
[/LIST]
[LIST]
[*]In 8.04 I was successful in compiling and loading an rt2570-cvs-daily driver. I even managed to get WPA working, with no bandwidth problems and minimal, reproducible disconnection problems.
[/LIST]

[LIST]
[*]Using clues from "lsusb" (manufacturer and device ID: 148f and 2570 respectively) and [http://linux-wless.passys.nl/query_chipset.php?chipset=Ralink](http://linux-wless.passys.nl/query_chipset.php?chipset=Ralink), I believe I have a Zonet ZEW2500P adapter in my computer.
[/LIST]

This leads me to ask some questions:

[LIST=1]
[*]1 Why does rt2500usb not work for me, despite being the supported driver in all modern Linux distros?
[/LIST]
[LIST=1]
[*]2 If these legacy drivers that myself (in 8.04) and so many others have been using are discontinued, is it worth using the very last release of the legacy drivers, despite being unsupported? Else, should we get the drivers the kernel ships with working?
[/LIST]
[LIST=1]
[*]3 Has *anyone* successfully used the rt2500usb (or other) drivers? Just curious...
[/LIST]

I would be extremely grateful for any replies, as it will help me get my WLAN card working once again, or at least explain to me why I can't.

---

