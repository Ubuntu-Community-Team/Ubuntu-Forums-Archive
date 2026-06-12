---
title: "New user, killer n1202 wifi card not connecting to wifi"
date: 2016-09-07
forum: Networking &amp; Wireless
---

### Post by jamesva3 on 2016-09-07
So all I can see under connections is [wired connection 1 (default0)] and [virbr0] which I have no idea what it is, google tells me it may have something to do with vmware, which I have installed but am not planning on using anytime soon. I have [enable wifi] checked but I don't see the killer network card. I should also note that my wifi would not turn on in windows before I installed Ubuntu, but I didn't bother checking it as I was uninstalling windows anyways (have never had issues with the card before, this is 3 year old laptop, w110er). I also have a pau06 panda wireless card plugged in, i don't see it under connections either.

I am on ubuntu 16.04.1 ubuntu LTS, just installed.

I have also looked for troubleshooting guides but the ones I have found are out of date.

---

### Post by ajgreeny on 2016-09-07
See if the information and wifi-info-script  me4ntioned at [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) are of any help.

Post back here the output of the script and someone who knows wifi better than I should help you.

---

### Post by jamesva3 on 2016-10-05
[ATTACH]271502[/ATTACH]

size was to big for the text file.

since you responded i have done a completely clean install of ubuntu 16.04, and bought another pcie express wireless adapter (with ar9462 chipset). i swapped it out and same result nothing is showing up and ubuntu doesnt recognize that i even have a card plugged in. maybe the pci slot is gone? i checked it visually and there is no liquid or burn marks around it. i tried using a plug n play wifi usb adapter and it worked fine(same one as before). the output text of the file was generated using the new wifi express card. thanks.

---

### Post by chili555 on 2016-10-05
Your new Atheros shows up very well, actually:> 03:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: AzureWave AR9462 Wireless Network Adapter [1a3b:2116]
	Kernel driver in use: ath9k
And here:> wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
But it will not work properly as long as the wireless switch or key combination is set to turn off the wireless radio:> 0: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]Please find it and switch it.

---

### Post by jamesva3 on 2016-10-05
Can you please end my life right now? I have spent days wondering what might be wrong, and have dished out (admittedly only $10) for a new wifi chip, only to find out that the wifi was disabled....by the function key...oh my god why. I have gone through 1 windows installation and two ubuntu installations and finally I just want to take a hammer to this freakin thing, god. Problem solved! My brain feels broken though... invaluable advice from this forum.

---

### Post by chili555 on 2016-10-06
> ***Reason***: *Removed bad language*LOLOL! I hear you!

No worries. All of us, including me *blush*, have made a mistake or two about the switch. I have a laptop with the switch on the front and I have, several times, nudged it with my beer-engorged belly! 

We're glad it's working now. Do an update, relax and have fun!

---

### Post by jamesva3 on 2016-10-06
Thanks for your help, it's a relief that the issue wasn't anything more than a switch.

---

