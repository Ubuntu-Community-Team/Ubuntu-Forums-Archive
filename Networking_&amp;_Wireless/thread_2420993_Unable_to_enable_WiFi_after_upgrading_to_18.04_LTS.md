---
title: "Unable to enable WiFi after upgrading to 18.04 LTS on an HP 550"
date: 2019-06-14
forum: Networking &amp; Wireless
---

### Post by boxcorner on 2019-06-14
Hello
I upgraded my wife's HP 550 from 14.04 LTS to 16.04 LTS yesterday, successfully.
Today I tried to upgrade it from 16.04 LTS to 18.04 LTS but now have a problem.
Settings > Details > About shows Ubuntu 18.04.2 LTS
When I click on 'Check for updates', I get:
Unable to download updates from "extensions.gnome.org ...", etc.
When I run Software Updater it says there is 138kB to be downloaded ... but it fails to do so.
Ok it took me a while but I now I realize that the HP 550 is not connected.
At the top of the screen where the WiFi icon is usually located, I see a ?.
When I click on the ? a drop-down menu shows the name of my network, with a ? alongside.
When I open WiFi settings I see my network name, and on the right a WiFi icon.
When I click on the WiFi icon, the icon at the top of the screen changes from ? to the WiFi icon,
It stays like that for a while, then changes to 3 dots, then back to ?.
Ubuntu is unable to connect, however the laptop is dual-boot with Windows Vista,
So, I started Windows, configured WiFi, then it connected and I was able to get online to websites.
But when I boot into Ubuntu, it does not connect.
So, the problem appears to be specific to the installation of Ubuntu 18.04 on this HP 550.
I'm guessing that this is a driver problem, which is specific to the modem in the HP 550. 
How can I configure 18.04 to recognize the modem in the HP 550, without WiFI enabled?
I would be grateful if someone good give me some tips on how to solve this problem.
Thanks in advance.

---

### Post by Autodave on 2019-06-14
Any upgrade can break things that worked perfectly before.  And you upgraded 2 release levels.  Hopefully someone here will have an answer for you, but you may have to end up doing a fresh install of 18.04.

---

### Post by boxcorner on 2019-06-15
Thank you. 
I will make a bootable USB drive and try re-installing 18.04 from that.

**Addendum: **I have tried what was suggested in the following threads, without success:
[URL="https://ubuntuforums.org/showthread.php?p=12489467"]https://ubuntuforums.org/showthread.php?t=2191347
[https://ubuntuforums.org/showthread.php?p=12489467](https://ubuntuforums.org/showthread.php?p=12489467)
[/URL]
[URL="https://ubuntuforums.org/showthread.php?p=12489467"]
[/URL]

---

### Post by garvinrick4 on 2019-06-18
Link to thread under garvinrick4. NetworkManager give it a go

[https://ubuntuforums.org/showthread.php?t=2420987](https://ubuntuforums.org/showthread.php?t=2420987)

If you run this line to check out your network all three should say yes. 
> gedit /var/lib/NetworkManager/NetworkManager.state 			 		

---

### Post by boxcorner on 2019-06-27
[SIZE=3]Many thanks for you reply. 
Sorry about the delay in replying. 
I have now done a clean install from a bootable USB key/drive with 18.04 LTS iso on it.
I opted to remove the previous dual boot Windows Vista & 18.04 LTS installation, which was not working.
18.04 LTS installed without any issues.
Currently, at the top right-hand corner of the screen, the icon to the left-hand side of the speaker icon
ie which was previously a '?' now resembles flashlight with the arcs above it grayed out.
When I run the line ```
gedit /var/lib/NetworkManager/NetworkManager.state
```[SIZE=3] in Terminal, a blank gui window opens.
 It seems that Ubuntu is not recognizing the hardware.[/SIZE]

**Addendum: **I have found how to fix this. I went into the BIOS settings and discovered that *Embedded WLAN Device Radio* was enabled, but *LAN/WLAN Switching* was disabled. I enabled [/SIZE][SIZE=3][SIZE=3]*LAN/WLAN Switching*[/SIZE] and Firefox now connects to our network. 
BTW -  There is a hardware switch, above the keyboard, which was lit blue, before I changed the BIOS setting. This seems to signify Internet connection ON. Pressing it causes the color to change to orange and the network icon to change to an airplane symbol. Pressing the switch again changes the color back to blue, but the Internet connection icon changes back to '?'. In order to reconnect, click on the '?' then click on the network name and the connection is  usually re-established automatically. If not, then click on Select Network. This works for me. I hope someone else finds it helpful!
[/SIZE]

---

### Post by wildmanne39 on 2019-06-27
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by boxcorner on 2019-06-27
Many thanks for your reply. 
I found how to fix it. 
Please see my addendum.

---

