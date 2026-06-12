---
title: "Broadcom BCM4311"
date: 2014-03-05
forum: Networking &amp; Wireless
---

### Post by Buenadriver on 2014-03-05
Have a Dell 1501 with 12.04. Wired works ok, but no wireless. Tried commands on other posts but nothing is working yet. I guess we need to start from square one. Help appreciated.

---

### Post by joebutton64 on 2014-03-05
Just to cover the basics, have you :
1.) checked your network settings and are sure that wireless is enabled
2.) used the command (ifconfig wlan0 up)
3.) checked and made sure that your router's wireless is enabled

---

### Post by Buenadriver on 2014-03-05
```

``````
ubuntu@ubuntu:~$ ifcnfig wlan0 up
No command 'ifcnfig' found, did you mean:
 Command 'ifconfig' from package 'net-tools' (main)
ifcnfig: command not found
ubuntu@ubuntu:~$ 



```Don't know if this is what you wanted but here it is. Whoops, ubuntu@ubuntu:~$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
ubuntu@ubuntu:~$

---

### Post by ajgreeny on 2014-03-05
Let's see the output of **lspci** as well which will show us the chipset of your wireless card.

---

### Post by chili555 on 2014-03-05
Let's *really* get back to basics:```
lspci -nn | grep 0280
rfkill list all
uname -r
```You may safely copy and paste each command.

---

### Post by Buenadriver on 2014-03-05
```

``````

``````
ubuntu@ubuntu:~$ lspci -nn | grep 0280
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
ubuntu@ubuntu:~$ 


```ubuntu@ubuntu:~$ rfkill list all
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$ uname -r
3.8.0-29-generic
ubuntu@ubuntu:~$

---

### Post by chili555 on 2014-03-05
How about the others?

---

### Post by Buenadriver on 2014-03-05
```

```r (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
ubuntu@ubuntu:~$

---

### Post by chili555 on 2014-03-05
Your 14e4:4312 requires firmware. With the ethernet connected, please do:```
sudo apt-get install firmware-b43-installer  
```Detach the ethernet, reboot and give us your report.

---

### Post by Buenadriver on 2014-03-05
On desktop now, it gave me a error report and took out my wired connection.

---

### Post by chili555 on 2014-03-05
> it gave me a error reportWhat was it?```
dmesg | tail -n10
dmesg | grep b43
```

---

### Post by Buenadriver on 2014-03-05
what is that between the dmesg and the tail?
composite sync not supported.
will use DMA mode even though HW doesn't support it.

after grep b43 a bunch of data

---

### Post by Iowan on 2014-03-05
That would be the "pipe" character (or vertical bar).
On my keyboard, it's the shift-backslash.

---

### Post by chili555 on 2014-03-05
> **Buenadriver said:**
> what is that between the dmesg and the tail?Oops,sorry. That is the pipe symbol. On my US keyboard, it is on the right side on the same key with \. [http://i.stack.imgur.com/X8MpW.png](http://i.stack.imgur.com/X8MpW.png)

---

### Post by chili555 on 2014-03-05
> after grep b43 a bunch of data In order to know what went wrong and therefore what to fix, we need to know what it is. If it's easier for you, do:```
dmesg | grep -e wl -e b43  > wifi.txt
```Find the file wifi.txt in your user directory and transfer it on a USB key or similar so you can post it here.

---

### Post by Buenadriver on 2014-03-05
```
ubuntu@ubuntu:~$ dmesg | grep -e wl -e b43  > wifi.txt
ubuntu@ubuntu:~$ 


```will try to get back online may take 4-5 mins.

Back online but don't have a usb key.

---

### Post by chili555 on 2014-03-05
Well, I guess you'll have to type it all out by hand, then. We can't really just guess what the problem is and just start hacking away. Just start with any lines about *wl.* Are there any? What do they say?

---

### Post by Buenadriver on 2014-03-05
back online, what command to try next?

So sorry, don't understand what you are asking.

---

### Post by chili555 on 2014-03-05
We don't know what to do next since we don't know anything from the last commands. As I said, just start with any lines about *wl* from the text file wifi.txt. Are there any? What do they say?

---

### Post by Buenadriver on 2014-03-05
So sorry don't understand what you are asking about the w/ files.

---

### Post by chili555 on 2014-03-05
In the file wifi.txt that you created as above, are there any lines referring to a driver *wl*? Like this perhaps?> [COLOR="#FF0000"]wl[/COLOR]: module license 'MIXED/Proprietary' taints kernel.If so, what are yours?

---

### Post by Buenadriver on 2014-03-05
Sorry, I don't know where to look for that.

---

### Post by chili555 on 2014-03-05
> **Buenadriver said:**
> Sorry, I don't know where to look for that.In post #16, you created a file wifi.txt that now resides in your user directory. Find it. Right-click it and select 'Open with gedit.' When it opens, read it and see if there are lines regarding the driver *wl.* Summarize them and tell all of us what they are, please.

---

### Post by Buenadriver on 2014-03-05
```
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ dmesg | grep -e wl -e b43  > wifi.txt
ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$


```

---

### Post by chili555 on 2014-03-05
We already created it. There is no need to create it again. Do you see it in your user directory?

> ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ dmesg | grep -e wl -e b43  > wifi.txtYou copied the entire command prompt. It is not:```
 ubuntu@ubuntu:~$ dmesg | grep -e wl -e b43  > wifi.txt
```It is instead:```
dmesg | grep -e wl -e b43  > wifi.txt
```However, it is already there. Please find and read it.

---

### Post by Buenadriver on 2014-03-05
I am sorry but I don't know where to look.

---

### Post by chili555 on 2014-03-05
> **Buenadriver said:**
> I am sorry but I don't know where to look.I've explained the best way I know how. I regret I can be of no further assistance.

---

### Post by Buenadriver on 2014-03-05
Thank you kindly, I wish I knew more about this system.

---

### Post by Buenadriver on 2014-03-06
```

``````
/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: anewguy, chili555, llua
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the size limit of 19.5 kB for .txt files on the Ubuntu Forums.
#
############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

FILEBASE="wireless-info"
MODMATCHES="(air|ar5|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|8192cu|8192du|rt5|rt6|rt7|rtl|r818|r871|ssb|wl|b43|bcma|brcm|eth1|ndis|wlan0|firm|etork)[^[:punct:] ]*"
exec 3>&1 4>&2
exec 1> $FILEBASE.txt 2> /dev/null
if [ "$?" != "0" ]; then
    printf "\nCould not write target file \"$FILEBASE.txt\", aborting.\n\n"
    exit 1
fi
printf "\n*************** info trace ***************\n"
printf "\n***** uname -a *****\n\n"
uname -a
printf "\n***** lsb_release *****\n\n"
lsb_release -idrc
printf "\n***** lspci *****\n\n"
lspci -nnk | grep -iA2 net
printf "\n***** lsusb *****\n\n"
lsusb
printf "\n***** PCMCIA Card Info *****\n\n"
pccardctl info
printf "\n***** iwconfig *****\n\n"
iwconfig
printf "\n***** rfkill *****\n\n"
rfkill list all
printf "\n***** iw reg get *****\n\n"
iw reg get
printf "\n***** route -n *****\n\n"
route -n
printf "\n***** lsmod *****\n\n"
lsmod | egrep "(^|[[:punct:] ])${MODMATCHES}([[:punct:] ]|$)"
printf "\n***** nm-tool *****\n"
nm-tool
printf "\n***** NetworkManager.state *****\n"
cat /var/lib/NetworkManager/NetworkManager.state
printf "\n***** NetworkManager.conf *****\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "nm-system-settings.conf (used up to 10.04):\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi
printf "\n***** interfaces *****\n\n"
cat /etc/network/interfaces | sed -r 's/wpa-psk [[:graph:]]+/wpa-psk <WPA key removed>/'
printf "\n***** iwlist *****\n\n"
if [ -t 0 ]; then
    sudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/gksudo ]; then
    gksudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/kdesudo ]; then
    kdesudo iwlist scan || echo "Aquiring of root rights failed."
else
    echo "No way to aquire root rights found."
fi
printf "\n***** resolv.conf *****\n\n"
grep -v '^#' /etc/resolv.conf
printf "\n***** blacklist *****\n"
for CONFFILE in /etc/modprobe.d/*.conf; do
    if [[ -n $(egrep -v '/etc/modprobe.d/(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia)' <<< $CONFFILE) ]]; then
	BLACKLIST=$(grep '^blacklist' $CONFFILE)
	if [ -n "$BLACKLIST" ]; then
	    printf "\n[%s]\n%s\n" $CONFFILE "$BLACKLIST"
	fi
    fi
done
printf "\n***** modinfo *****\n\n"
MODULNAMES=$(lsmod | egrep "^$MODMATCHES" | awk '{print $1}')
for MODULE in $MODULNAMES; do
    modinfo $MODULE
    echo
done
printf "\n***** udev rules *****\n"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules
printf "\n***** dmesg *****\n\n"
dmesg | egrep "[[:punct:] ]${MODMATCHES}[[:punct:] ]"
printf "\n****************** done ******************\n\n"
exec 1>&3 3>&-
exec 2>&4 4>&-
sed -r -i 's/([[:alnum:]][[:alnum:]]:){5}[[:alnum:]][[:alnum:]]/<MAC address removed>/' $FILEBASE.txt
if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then
    tar -czf $FILEBASE.tar.gz $FILEBASE.txt
    rm -f $FILEBASE.txt
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.\n\n" "$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$FILEBASE"
fi

```ubuntu@ubuntu:~$ sudo apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$

---

### Post by varunendra on 2014-03-06
@Buenadriver,

You have posted the contents of wireless_script itself, that is not what we need. Assuming you have followed the instructions from **[this post]("http://ubuntuforums.org/showthread.php?p=12350385#post12350385")** to download it, please read carefully the full instructions to actually run it. We need the report file that this script generates.

If you followed the full instructions and also ran the script, it should have created a file named "wireless-info.txt" or "wireless-info.tar.gz" in the same place where you have downloaded the script (most probably your "Downloads" directory or your 'Home' directory, or the Desktop). Attach that file in your next post.

In the meanwhile, please try running these commands (out of a blind guess, since we are not sure yet without the info we need from you) -
```
sudo apt-get purge bcmwl-kernel-source
```
..and reboot. Does the wifi work now? If not, please post the file or its contents that the above script generated, or the one that was created (in you Home directory) by the '**dmesg | grep -e wl -e b43  > [COLOR="#0000CD"]wifi.txt[/COLOR]**' command suggested previously.

---

### Post by Buenadriver on 2014-03-07
Wifi not working, command and reboot took out wired connection as well. Message I got is posted above in edited post.Had to reinstall until I came to first quit button and then it booted with wired connection. Thanks.

---

### Post by varunendra on 2014-03-07
You are telling us everything except what can be useful and helpful - the reports you were asked to post.

Sorry, I am unable to understand most of what you wrote so far. If you can, please read my previous post again and try to understand what I wrote and asked for.

Unless you post the report file generated by the script I linked to, OR the file created by the commands suggested by Dr. chili555 earlier, we can not understand the problem, and so can not offer any help.

---

### Post by Buenadriver on 2014-03-07
```

``````

```Ok, will try to do that.
[   58.613493] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   58.656068] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   59.164272] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   59.164279] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   59.164284] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[11708.128159] Modules linked in: dm_crypt(F) dell_wmi joydev(F) dell_laptop sparse_keymap b43 dcdbas snd_hda_codec_idt dm_multipath(F) scsi_dh(F) bcma snd_hda_intel mac80211 snd_hda_codec kvm_amd(F) kvm(F) snd_hwdep(F) cfg80211 snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) ssb_hcd snd_seq_device(F) psmouse(F) snd_timer(F) k8temp serio_raw(F) snd(F) sp5100_tco soundcore(F) i2c_piix4 shpchp ohci_pci parport_pc(F) ppdev(F) mac_hid lp(F) parport(F) bnep rfcomm bluetooth squashfs(F) overlayfs(F) nls_utf8 isofs(F) dm_mirror(F) dm_region_hash(F) dm_log(F) pata_acpi radeon b44 sdhci_pci i2c_algo_bit sdhci ttm mii(F) drm_kms_helper pata_atiixp drm ahci(F) libahci(F) ssb ati_agp video(F) wmi      Is this the correct file?

```
ubuntu@ubuntu:~$ sudo apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 291 not upgraded.
ubuntu@ubuntu:~$ 


```or this?

---

### Post by varunendra on 2014-03-08
> **Buenadriver said:**
> ```
[   59.164272] b43-phy0 [COLOR="#FF0000"]**ERROR: Firmware file "b43/ucode5.fw" not found**[/COLOR]
[   59.164279] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
```

Hmm.. this is much better. So it is clear that you don't have the firmware installed yet. Now we have something to work on.

Please download the "linux-firmware-nonfree" package from this link : [http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

It will download a file named "linux-firmware-nonfree_1.14ubuntu1_all.deb". Copy this file onto your Desktop.

Then open a terminal (Ctrl-Alt-T) and run the following commands -
```
cd Desktop
sudo dpkg -i linux-firmware*.deb
```
Make sure you type the commands exactly as above. You may copy paste to avoid errors.

This will install the firmware required by the driver. After this, reboot and see if your wireless works now. If not, post back and we'll check what else remained to fix.

---

### Post by Buenadriver on 2014-03-08
```
ubuntu@ubuntu:~$ cd Desktop
ubuntu@ubuntu:~/Desktop$ sudo dpkg -l linux-firmware* .deb
dpkg-query: error: package name in specifier '.deb' is illegal: must start with an alphanumeric character
ubuntu@ubuntu:~/Desktop$ 

```

Did I miss something here?

---

### Post by varunendra on 2014-03-08
> **Buenadriver said:**
> Did I miss something here?
Yes you did -

```
ubuntu@ubuntu:~$ cd Desktop
ubuntu@ubuntu:~/Desktop$ sudo dpkg **[COLOR="#FF0000"]-l[/COLOR] linux-firmwar[COLOR="#FF0000"]e* .d[/COLOR]eb**

```
**1)** You typed small "L" (l), while it should have been small "I" (i).
**2)** There should be no gap between asterisk (*) and the dot (.) in ".deb"

Just correct these and you should be all set. Post back if you get any errors again - before, during or after the installation of the package.

---

### Post by Buenadriver on 2014-03-08
```

``````


```Yes, I saw that, corrected that, did the commands, rebooted but still no wireless.

ubuntu@ubuntu:~$ dmesg | grep -e wl -e b43
[   69.446871] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   69.488074] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   70.024955] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   70.024962] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   70.024966] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
ubuntu@ubuntu:~$

[   65.141188] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   65.184065] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   66.033486] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   66.033494] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   66.033498] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

---

### Post by varunendra on 2014-03-08
Please reboot, and post back the output of the same command again -
```
dmesg | grep -e wl -e b43
```

The command to redirect the above output to a file on your Desktop -
```
dmesg | grep -e wl -e b43  > Desktop/wifi.txt
```
This should create a file named "wifi.txt" on your desktop. Either attach or post back the contents of this file in your next post.

---

### Post by Buenadriver on 2014-03-08
Did that, posted in the edit above.

---

### Post by varunendra on 2014-03-08
Which still shows -
> ERROR: **[COLOR="#FF0000"]Firmware file "b43/ucode5.fw" not found[/COLOR]**
Which further means the "dpkg -i..." command I suggested didn't complete correctly.

Please try that again. That is, open a new terminal, and do -
```
cd Desktop
sudo dpkg -i linux-firmware*.deb
```
..and post back whatever is returned in the terminal afterwards. The installation may take a few seconds to a couple of minutes, so don't hurry. Just wait for it to finish and post back the entire contents of the terminal.

The fix that you need is as simple as copying a file in a particular location in your system. We can do it in many ways. The above is the one that we consider both safe and easy.

---

### Post by Buenadriver on 2014-03-08
```
ubuntu@ubuntu:~$ cd Desktop
ubuntu@ubuntu:~/Desktop$ sudo dpkg -i linux-firmware*.deb
dpkg: error processing linux-firmware*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-firmware*.deb
ubuntu@ubuntu:~/Desktop$ 



```

---

### Post by varunendra on 2014-03-08
> **Buenadriver said:**
> ```
ubuntu@ubuntu:~/Desktop$ sudo dpkg -i linux-firmware*.deb
dpkg: error processing linux-firmware*.deb (--install):
 cannot access archive: **[COLOR="#FF0000"]No such file or directory[/COLOR]**
Errors were encountered while processing:
 linux-firmware*.deb
```

Means the file "linux-firmware-nonfree_1.14ubuntu1_all.deb" was not present on your Desktop.

Did you download it?
Did you copy it to your Desktop before running the "sudo dpkg..." command?

The direct download link is : [http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

The downloaded file should be "**linux-firmware-nonfree_1.14ubuntu1_all.deb**"

---

### Post by Buenadriver on 2014-03-08
```
ubuntu@ubuntu:~$ cd Desktop
ubuntu@ubuntu:~/Desktop$ 
ubuntu@ubuntu:~/Desktop$ sudo dpkg -i linux-firmware*.deb
(Reading database ... 148949 files and directories currently installed.)
Preparing to replace linux-firmware-nonfree 1.14ubuntu1 (using linux-firmware-nonfree_1.14ubuntu1_all.deb) ...
Unpacking replacement linux-firmware-nonfree ...
Setting up linux-firmware-nonfree (1.14ubuntu1) ...
ubuntu@ubuntu:~/Desktop$ 


```  Now I have an OPENED linux-firmware nonfree 1.14ubuntu1_all.d...  on desktop which I hope returned the info you were asking for.

---

### Post by varunendra on 2014-03-08
Yup, it seems it was installed properly this time. Now the required firmware should be ready for the driver.

Now, please either reboot, or manually reload the driver with -
```
sudo modprobe -rv b43
sudo modprobe -v b43
```

Your wireless should be working now. If not, please post back the outputs of -
```
[s]dpkg | grep -e wl -e b43[/s]
dmesg | grep -e wl -e b43
rfkill list
```

---

### Post by Buenadriver on 2014-03-08
```
ubuntu@ubuntu:~$ dpkg | grep -e wl -e b43
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
ubuntu@ubuntu:~$ rfkill list
ubuntu@ubuntu:~$ 





```

---

### Post by varunendra on 2014-03-08
> **Buenadriver said:**
> ```
ubuntu@ubuntu:~$ **[COLOR="#FF0000"]dpkg[/COLOR]** | grep -e wl -e b43
dpkg: error: need an action option
```

Oops! Sorry, my mistake this time - it should have been "dmesg", not dpkg.

Have you rebooted? Is it still not working? If so, please try the corrected command -
```
dmesg | grep -e wl -e b43
```
..and post back the output.

---

### Post by Buenadriver on 2014-03-08
```
ubuntu@ubuntu:~$ dmesg | grep -e wl -e b43
[   68.868387] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   68.912058] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   70.306617] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   70.306625] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   70.306629] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  530.688083] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[  530.762855] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  530.762869] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  530.762877] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
ubuntu@ubuntu:~$ 


```

---

### Post by varunendra on 2014-03-08
Are you trying this on a Live CD/DVD/USB?

That is, Ubuntu running from a Live CD/DVD or Live USB, not the one "Installed" and running from hard disk.

If so, all the changes will be lost on reboot unless it is a Live USB with "Persistence". Hence the installed firmware will be lost too.

Please confirm and I'll let you know what can be done in that case.

---

### Post by Buenadriver on 2014-03-08
I have problems rebooting. To reboot from the hard puts up a grey screen with vertical lines and that sets there for about 15 mins. until it times out. Then I can tap the curser and it boots. But I then don't have ANY internet connection. So I put the install cd in the drive and start an install until I get to the first quit button. I click on the quit button and it boots. I understand now what you are saying about changes being lost. I don't have a usb stick yet, to work with.

---

### Post by varunendra on 2014-03-08
If you want to activate the wifi on a Live session running from the CD, you'll have to install the driver EVERY TIME you boot in that way. Then, instead of rebooting, run the two "modprobe.." commands I suggested. That will re-load the driver without rebooting. Your wifi will start working at this point, but you'll have to do it all again on next reboot.

In detail, the above process will go as follows -

[indent]**1)** Install the firmware : Download it from the link I gave > Copy it to the Desktop > Install it with "sudo dpkg -i linux-firmware*.deb" command as I suggested before.

**2)** Reload the driver : After the firmware package has been successfully installed as above, run the following commands to reload the driver without rebooting -
```
sudo modprobe -rv b43
sudo modprobe -v b43
```[/indent]

If you do this on the 'Installed' system, the one that is running from hard disk, not the CD, then the above process will be required only once. The driver will work automatically since next boot.

The grey screen + vertical lines problem you mentioned sounds like a graphichs issue. But once you have gone past it, do you get a usable desktop on which you can perform the above steps? If yes, it will be only one time process. The wireless should work afterwards (since next boot).

I would be glad to help with the installed version. I have already mentioned above how you can get wireless in Live session. Let me know what you need now.

---

### Post by Buenadriver on 2014-03-08
I have a ubuntu boot repair disk I downloaded. It took about 2 hrs. to download. Would I better off fixing my reboot problems first? And then go back thru the steps you listed? Or just go thru the steps you just mention.

---

### Post by varunendra on 2014-03-08
I suggest you perform the steps (download > copy > install firmware > reload the driver) anyway. Just make sure all the steps are done correctly and you should be good on wireless part.

However, the delay or freezing problem that you mentioned (the grey screen etc.) can also be *sometimes* caused by a wrong driver, including a wireless one. So just to make sure you don't have a wrong wireless driver on the installed one, run this command (on the 'Installed' Ubuntu) BEFORE going through above procedure -
```
sudo apt-get purge bcmwl-kernel-source
```
Then reboot and perform the procedure AFTERWARDS.

If it fixes the wifi (it should, unless there are other problems as well), good. If not, then get your rebooting problem fixed first, THEN return back to address the wifi.

**PS:**
If you think the graphics driver may be a possible reason for the reboot issue, you may try the usual "nomodeset" boot-option as mentioned in the first post of this thread : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Buenadriver on 2014-03-08
ok, trying the repair disk route. It sounds like it could be dangerous, any suggestions? Plus I have a install 12.04 icon on my desktop. Should I try that first?

---

### Post by varunendra on 2014-03-08
> **Buenadriver said:**
> Plus I have a install 12.04 icon on my desktop. Should I try that first?

That icon will just Install Ubuntu on your computer's hard disk. Have you not already installed it? Then what are you going to repair with the "Repair Disk" you are talking about?

And what exactly are you going to do with the repair disk?

---

### Post by Buenadriver on 2014-03-08
varunendra: I am deeply indebted to you. Thank you so much for your help. I clcked on the icon on the desk top, and that cured the reboot problem. Then I went back to to your post and then I am now wireless. I also have to say thanks to chilli555 for his efforts. You are a great group of guys. Thanks again.

---

### Post by varunendra on 2014-03-08
I'm glad our efforts finally paid off.

My only worry was if you lost patience before the problem was solved. But I appreciate your persistence despite things not always happening as expected. For us, it's just routine. :)

So from what I understand from your final post, you seem to have done a fresh install which fixed the booting problem. Then the wireless fix was easy to implement on a fresh install.

**One thing to remember -** _DO NOT install_ any other wireless driver if suggested by "**Additional Drivers**" option *(you don't need to worry about it if you don't know what it is)*. That driver will break the current one and will have to be removed (with the "*apt-get purge..*" command I suggested earlier). Just be careful about that, and the wireless will keep working from now on.

Hope you'd enjoy Ubuntu and our forums here. :)

---

### Post by Buenadriver on 2014-03-08
Thank you.

---

