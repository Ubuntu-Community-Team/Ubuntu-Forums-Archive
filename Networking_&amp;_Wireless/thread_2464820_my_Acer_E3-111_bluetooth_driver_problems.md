---
title: "my Acer E3-111 bluetooth driver problems"
date: 2021-07-13
forum: Networking &amp; Wireless
---

### Post by j0hn7 on 2021-07-13
The bluetooth was on and no devices detected after the bluetooth was on 


This is what it happend?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288814&stc=1[/IMG]


I tried some commands found in thread post
[https://superuser.com/questions/1289782/bluetooth-stopped-working-correctly-after-possible-update](https://superuser.com/questions/1289782/bluetooth-stopped-working-correctly-after-possible-update)

it cannot work too,


this is what happend when i tried this

sudo dmesg | grep Blue 

[   20.452853] Bluetooth: Core ver 2.22
[   20.455473] Bluetooth: HCI device and connection manager initialized
[   20.457910] Bluetooth: HCI socket layer initialized
[   20.457921] Bluetooth: L2CAP socket layer initialized
[   20.457939] Bluetooth: SCO socket layer initialized
[   54.656940] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   54.656955] Bluetooth: BNEP filters: protocol multicast
[   54.656970] Bluetooth: BNEP socket layer initialized
[31146.281284] Bluetooth: hci0: BCM: chip id 70
[31146.282254] Bluetooth: hci0: BCM: features 0x06
[31146.298216] Bluetooth: hci0: BCM43142A
[31146.298245] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[31146.715531] Bluetooth: hci0: BCM: firmware Patch file not found, tried:
[31146.715568] Bluetooth: hci0: BCM: 'brcm/BCM43142A0-04ca-2009.hcd'
[31146.715586] Bluetooth: hci0: BCM: 'brcm/BCM-04ca-2009.hcd'
[31148.750167] Bluetooth: hci0: command 0x1003 tx timeout
[31148.751149] Bluetooth: hci0: unexpected event for opcode 0x1003
[31152.943104] Bluetooth: RFCOMM TTY layer initialized
[31152.943148] Bluetooth: RFCOMM socket layer initialized
[31152.943165] Bluetooth: RFCOMM ver 1.11
[33079.177791] Bluetooth: hci0: BCM: chip id 70
[33079.178789] Bluetooth: hci0: BCM: features 0x06
[33079.194801] Bluetooth: hci0: inspire-koto0127
[33079.194811] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[33079.195875] Bluetooth: hci0: BCM: firmware Patch file not found, tried:
[33079.195883] Bluetooth: hci0: BCM: 'brcm/BCM43142A0-04ca-2009.hcd'
[33079.195887] Bluetooth: hci0: BCM: 'brcm/BCM-04ca-2009.hcd'
[33081.199512] Bluetooth: hci0: command 0x1003 tx timeout
[33081.200815] Bluetooth: hci0: unexpected event for opcode 0x1003
[40765.659639] Bluetooth: hci0: BCM: chip id 70
[40765.660638] Bluetooth: hci0: BCM: features 0x06
[40765.676627] Bluetooth: hci0: inspire-koto0127
[40765.676641] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[40765.677797] Bluetooth: hci0: BCM: firmware Patch file not found, tried:
[40765.677812] Bluetooth: hci0: BCM: 'brcm/BCM43142A0-04ca-2009.hcd'
[40765.677821] Bluetooth: hci0: BCM: 'brcm/BCM-04ca-2009.hcd'
[40767.705367] Bluetooth: hci0: command 0x1003 tx timeout
[40767.705430] Bluetooth: hci0: sending frame failed (-19)
[40769.721515] Bluetooth: hci0: command 0x1001 tx timeout
[40769.721616] Bluetooth: hci0: sending frame failed (-19)
[40771.737613] Bluetooth: hci0: command 0x1009 tx timeout
[40776.151641] Bluetooth: hci0: unexpected event for opcode 0x1003
[40776.259626] Bluetooth: hci0: BCM: chip id 70
[40776.260634] Bluetooth: hci0: BCM: features 0x06
[40776.276676] Bluetooth: hci0: inspire-koto0127
[40776.276693] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[40776.277837] Bluetooth: hci0: BCM: firmware Patch file not found, tried:
[40776.277851] Bluetooth: hci0: BCM: 'brcm/BCM43142A0-04ca-2009.hcd'
[40776.277856] Bluetooth: hci0: BCM: 'brcm/BCM-04ca-2009.hcd'
[40778.297614] Bluetooth: hci0: command 0x1003 tx timeout
[40778.298673] Bluetooth: hci0: unexpected event for opcode 0x1003
[40841.531588] Bluetooth: hci0: command 0x1003 tx timeout
[40841.532593] Bluetooth: hci0: unexpected event for opcode 0x1003

 and this







[   20.455473] Bluetooth: HCI device and connection manager initialized
[   20.457910] Bluetooth: HCI socket layer initialized
[   20.457921] Bluetooth: L2CAP socket layer initialized
[   20.457939] Bluetooth: SCO socket layer initialized
[   54.656940] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   54.656955] Bluetooth: BNEP filters: protocol multicast
[   54.656970] Bluetooth: BNEP socket layer initialized
[31146.281284] Bluetooth: hci0: BCM: chip id 70
[31146.282254] Bluetooth: hci0: BCM: features 0x06
[31146.298216] Bluetooth: hci0: BCM43142A
[31146.298245] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[31146.715531] Bluetooth: hci0: BCM: firmware Patch file not found, tried:
[31146.715568] Bluetooth: hci0: BCM: 'brcm/BCM43142A0-04ca-2009.hcd'
[31146.715586] Bluetooth: hci0: BCM: 'brcm/BCM-04ca-2009.hcd'
[31148.750167] Bluetooth: hci0: command 0x1003 tx timeout
[31148.751149] Bluetooth: hci0: unexpected event for opcode 0x1003
[31152.943104] Bluetooth: RFCOMM TTY layer initialized
[31152.943148] Bluetooth: RFCOMM socket layer initialized
[31152.943165] Bluetooth: RFCOMM ver 1.11
[33079.177791] Bluetooth: hci0: BCM: chip id 70
[33079.178789] Bluetooth: hci0: BCM: features 0x06
[33079.194801] Bluetooth: hci0: inspire-koto0127
[33079.194811] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
^C0841.532593] Bluetooth: hci0: unexpected event for opcode 0x1003d'tried:

so i tried again fix this 
sudo apt update

sudo apt-get update
Hit:1 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease
Hit:2 [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) focal InRelease           
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hirsute-security InRelease                  
Ign:4 [http://ppa.launchpad.net/bluetooth/bluez/ubuntu](http://ppa.launchpad.net/bluetooth/bluez/ubuntu) hirsute InRelease             
Hit:5 [https://atl.mirrors.clouvider.net/ubuntu](https://atl.mirrors.clouvider.net/ubuntu) hirsute InRelease         
Hit:6 [https://atl.mirrors.clouvider.net/ubuntu](https://atl.mirrors.clouvider.net/ubuntu) hirsute-updates InRelease 
Hit:7 [http://ppa.launchpad.net/hardware-certification/public/ubuntu](http://ppa.launchpad.net/hardware-certification/public/ubuntu) hirsute InRelease
Hit:8 [https://atl.mirrors.clouvider.net/ubuntu](https://atl.mirrors.clouvider.net/ubuntu) hirsute-security InRelease
Hit:9 [https://atl.mirrors.clouvider.net/ubuntu](https://atl.mirrors.clouvider.net/ubuntu) hirsute-backports InRelease
Hit:10 [http://ppa.launchpad.net/obsproject/obs-studio/ubuntu](http://ppa.launchpad.net/obsproject/obs-studio/ubuntu) hirsute InRelease
Err:11 [http://ppa.launchpad.net/bluetooth/bluez/ubuntu](http://ppa.launchpad.net/bluetooth/bluez/ubuntu) hirsute Release
  404  Not Found [IP: 91.189.95.85 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/bluetooth/bluez/ubuntu hirsute Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


i try this 


rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
7: hci0: Bluetooth
    Soft blocked: no
[COLOR=var(--highlight-color)][FONT=var(--ff-mono)]    [/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=var(--ff-mono)]Hard blocked: no


this is what happend but i cant detect devices near me.[/FONT][/COLOR]


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288815&stc=1[/IMG]

---

### Post by mIk3_08 on 2021-07-13
There is always this "[31146.715531] Bluetooth: hci0: BCM: firmware Patch file not found, tried:" in the result of your Bluetooth query.
There can be something error with the driver you are using. Maybe installing the Bluetooth Manager might help you. And try to using another driver might also help you to work with your Bluetooth Hardware device. If you want Linux to recommend you for your right hardware device driver just visit to Hardware Probe and submit your hardware so they recommend the right driver for your machine. [Click here.]("https://linux-hardware.org/")

---

