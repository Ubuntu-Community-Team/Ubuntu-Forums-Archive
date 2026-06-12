---
title: "Wireshark detects no capture interfaces"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by amazingtaters on 2008-04-21
So, I've installed Wireshark, and would like to get it running, but it doesn't detect any network devices. I can't fathom the reason why, after all, I'm on a network right now using the internet.

Here is the output of lspci, which shows my Ethernet and Wireless adapters
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

```

---

### Post by chili555 on 2008-04-21
```
**sudo** wireshark
```Does that do it?

---

### Post by davidsrsb on 2008-04-21
In 7.10 wireshark and etherape both had double entries in the applications - internet menu with the second saying wireshark (as root) etc.
Selecting this entry immediately brought up a request for your password.
On upgrade to 8.10 these second entries vanished so maybe policykit is something to do with this

---

### Post by davidsrsb on 2008-04-21
The second entry properties has the command

gksu -u root /usr/bin/wireshark

---

### Post by amazingtaters on 2008-04-21
> **chili555 said:**
> ```
**sudo** wireshark
```Does that do it?

This did it. Many thanks.

---

### Post by davidsrsb on 2008-04-25
Running wireshark with sudo on the command line works fine.

Under 8.04 release using gksu -u root /usr/bin/wireshark in the menu does not work properly. It gets as far as the select capture interface window and the freezes when attempting to select the Ethernet I/F.
I reinstalled wireshark, no change.

---

### Post by TheSojourner on 2008-04-30
I can second this one. Under "Hardy Heron", if I run WireShark via the launcher under Applications>Internet>WireShark then nothing happens. Run it with a sudo command (*sudo wireshark*)from the CLI and everything works as it should. Run *gksu -u root /usr/bin/wireshark* from the CLI and it launches, but hangs after you open the "Capture Interfaces" window.

So sudo really is the answer. Create a new launcher (type: "Application in Terminal") with the command *sudo -S wireshark*. Clicking the new launcher will launch a terminal window prompting for sudo authentication. Type in your pass and everything works. Sure it's not the most elegant solution, you're stuck with a busy terminal window cluttering your desktop, but it DOES work. Now if someone would kindly tell me how to edit the launcher in the panel (Applications>Internet>WireShark), it would be appreciated.

---

### Post by chinaski on 2008-05-10
this works for me too, but a message pop up say running wireshark as sudo can be dangerous

---

### Post by hokuem on 2008-05-22
> **chinaski said:**
> this works for me too, but a message pop up say running wireshark as sudo can be dangerous

I have the same problem on 8.04.

When I run Wireshark normally and try to list available interfaces I have the error *dumpcap: There are no interfaces on which a capture can be done*.

If I start it with *sudo wireshark* everything works fine but I have this message at startup: > Running as user "root" and group "root".
This could be dangerous.

---

### Post by glOOps on 2008-05-24
Capturing and listing interfaces need root privileges.

read on [http://wiki.wireshark.org/CaptureSetup/CapturePrivileges]("http://wiki.wireshark.org/CaptureSetup/CapturePrivileges") :
> Running Wireshark (or any other network capture/analyzer, for that matter) on Linux needs root privileges. Therefore, you have to have root privileges when starting Wireshark, else you can't capture data. Please note that you don't have to login as root when starting your computer, you can use su(1) or sudo(8) for that purpose. However, this remains unsecure as the dissectors, the parts of Wireshark which parse the captured data, run with root privileges as they did before. A much safer solution would be to su(1) to root, then use the bundled dumpcap to dump the data (for example, you can evoke dumpcap by using "dumpcap -w ./dumpfile", which will dump the packets to the file "dumpfile" in the current working directory. See "dumpcap -h" for details). You could also use tcpdump for this purpose. The advantage of this solution is, while dumpcap/tcpdump still run as root, you can run Wireshark as a ordinary user and load the data you captured previously, so effectively this is kinda "privilege separation by hand".

About sudo : for graphicals applications who need root privileges, use gksudo:
gksudo wireshark
(edit Wireshark menu in System>Preferences>Main Menu)

---

### Post by hpklett on 2008-05-25
> **TheSojourner said:**
> I can second this one. Under "Hardy Heron", if I run WireShark via the launcher under Applications>Internet>WireShark then nothing happens. Run it with a sudo command (*sudo wireshark*)from the CLI and everything works as it should. Run *gksu -u root /usr/bin/wireshark* from the CLI and it launches, but hangs after you open the "Capture Interfaces" window.

gksu changes you environment variables, sudo doesn't.  It would be interesting to know why wireshark crashes with the root user's environment, and which variable is causing it.

---

### Post by jmacknmo on 2008-06-09
> **davidsrsb said:**
> Running wireshark with sudo on the command line works fine.

It doesn't work for me. I have tried all combinations suggested on this thread to no avail. No interface detected.

---

### Post by chk9 on 2008-06-11
> **TheSojourner said:**
> Now if someone would kindly tell me how to edit the launcher in the panel (Applications>Internet>WireShark), it would be appreciated.

Update the following file 
/usr/share/applications/wireshark.desktop
or create 
/usr/share/applications/wireshark-sudo.desktop
and put in the following content:
[INDENT]
[Desktop Entry]
Type=Application
Version=1.0
Name=Wireshark (as root)
GenericName=Network Analyzer
Comment=Network traffic analyzer
Icon=hi48-app-wireshark.png
TryExec=sudo
Exec=sudo -S /usr/bin/wireshark
Path=
Terminal=true
MimeType=
Categories=GNOME;Network;
X-KDE-SubstituteUID=true
[/INDENT]

And you should be good to go...
(At least I am :-D )

---

### Post by RAdams on 2008-06-19
Is there a way to allow it to work without running it as root:root?

---

