---
title: "Lubuntu 13.10 Lost Intel 2200bg Wifi"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by kjacobs on 2013-11-19
Hi folks,

I recently upgraded from Lubuntu 12.10 to 13.10 on my HP NX6110 Laptop with a Intel Pro 2200BG wifi adapter. The wifi worked fine on 12.10.....at first it worked fine on 13.10 as well. This afternoon after running for a hour or so, the wifi adapter just quit working. I cannot figure out what happened to it, although the system still sees the adapter....I cannot enable it. If I put my old Lubuntu 12.10 cd back into the laptop and run the live cd, the wifi works just fine.

So, hoping somebody has some ideas why the Intel 2200bg adapter is no longer working on 13.10????

Thanks in advance.....

Ken

---

### Post by Farfrae on 2013-11-20
I have exactly the same problem with lubuntu and the 2200BG. I posted here yesterday, but no-one has been able to offer any advice yet:
[http://ubuntuforums.org/showthread.php?t=2188725](http://ubuntuforums.org/showthread.php?t=2188725)

Makes me feel more confident that this is a software problem and not a hardware issue (my laptop is nearly 8 years old, but worked perfectly until I upgraded).

Have you tried entering this and then rebooting: 
```
sudo rfkill unblock all
``` 

That worked for me in terms of getting the wi-fi working, but I then got freezes.

Andrew

---

### Post by chili555 on 2013-11-20
Would both of you please run and post:```
rfkill list all
dmesg | grep ipw
```Thanks.

---

### Post by kjacobs on 2013-11-20
Here is the results for my sudo rfkill list and dmesg | grep ipw. I have tried the sudo rfkill unblock all...which causes the wifi light to start blinking, but am still not able to enable it in the connection window.


kenneth@kenneth-HP-Compaq-nx6110-PC419AV:~$ sudo rfkill list
[sudo] password for kenneth: 
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

kenneth@kenneth-HP-Compaq-nx6110-PC419AV:~$ dmesg | grep ipw
[   12.980069] libipw: 802.11 data/management/control stack, git-1.1.13
[   12.980072] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   13.007222] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   13.007228] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.146548] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   13.365531] ipw2200: Radio Frequency Kill Switch is On:
[   13.370226] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)


Then I tried to unblock all ..................


kenneth@kenneth-HP-Compaq-nx6110-PC419AV:~$ sudo rfkill unblock all
kenneth@kenneth-HP-Compaq-nx6110-PC419AV:~$ sudo rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
kenneth@kenneth-HP-Compaq-nx6110-PC419AV:~$ 

kenneth@kenneth-HP-Compaq-nx6110-PC419AV:~$ dmesg | grep ipw
[   12.980069] libipw: 802.11 data/management/control stack, git-1.1.13
[   12.980072] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   13.007222] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   13.007228] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.146548] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   13.365531] ipw2200: Radio Frequency Kill Switch is On:
[   13.370226] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
kenneth@kenneth-HP-Compaq-nx6110-PC419AV:~$ 


After the unblock all command, my wifi light flashes...still no way to enable the wifi adapter again. From the second dmesg | grep ipw, it almost appears like radio frequency kill switch is not being turned off????? Also...upon reboot, the rfkill list goes back to blocked again.

Any ideas???? Still baffled how this worked for a day and then quit...........

Ken

---

### Post by Farfrae on 2013-11-20
And here's mine:

andrew@andrew-laptop:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
andrew@andrew-laptop:~$ dmesg | grep ipw
[   20.996940] libipw: 802.11 data/management/control stack, git-1.1.13
[   20.996945] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   20.999993] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   20.999997] ipw2200: Copyright(c) 2003-2006 Intel Corporation

---

### Post by chili555 on 2013-11-20
> **Farfrae said:**
> And here's mine:

Yours ought to work fine. Does it scan?```
sudo iwlist eth1 scan
```If it scans, it ought to connect. Does Network Manager see networks? Does it try?

My old 2200 was not capable of WPA and WPA2; is yours?```
sudo iwlist eth1 auth
```

---

### Post by Farfrae on 2013-11-20
I'll also mention that mucking about with various options in ROM setup, I can occasionally get the wifi working, but everything locks up after a minute or two. The circumstances when it works and doesn't work don't seem to be consistent.

With a wire in it from the modem, all is well and the computer behaves impeccably.

Thanks for your help - and to Ken for my tagging along on this thread.

Andrew

---

### Post by chili555 on 2013-11-20
> **kjacobs said:**
> Here is the results for my sudo rfkill list and dmesg | grep ipw. I have tried the sudo rfkill unblock all...which causes the wifi light to start blinking, but am still not able to enable it in the connection window.



After the unblock all command, my wifi light flashes...still no way to enable the wifi adapter again. From the second dmesg | grep ipw, it almost appears like radio frequency kill switch is not being turned off????? Also...upon reboot, the rfkill list goes back to blocked again.

Any ideas???? Still baffled how this worked for a day and then quit...........

KenThe dmesg is the same as before, see the timestamp?> [ [COLOR="#FF0000"]13.365531[/COLOR]] ipw2200: Radio Frequency Kill Switch is On:You just read the file again from the start, not forward from where you left off.

Let's try a thing or two:```
gksudo gedit /etc/rc.local
```Right above exit 0, add a new line:```
rfkill unblock all
```Proofread, save and close gedit. Now do:```
sudo rfkill unblock all
sudo iwlist eth1 scan
```You don't have to post all the results, just tell me if you got results. If not, what was the message?

---

### Post by Farfrae on 2013-11-20
At the moment the options Network Manager is not seeing anything to connect to. Not even an option to connect to Wifi but I booted with the wire in, so perhaps that's why.

$ sudo iwlist eth1 scan


eth1      Interface doesn't support scanning.

$ sudo iwlist eth1 auth

eth1      no authentication information.




I'll reboot without the wire and see if that makes a difference.

---

### Post by Farfrae on 2013-11-20
No same as above without the wire. No recognition of wireless although my wireless light is lit on the hard button (it's a button rather than a switch - showing on).

---

### Post by chili555 on 2013-11-20
> **Farfrae said:**
> I'll also mention that mucking about with **various options in ROM setup**, Meaning what? Is this a virtual machine, a blade server, a katana, a Raspberry, a....what??? Do you mean the machine's BIOS? Usually, these devices are found in old laptops. I've had and happily used a few myself!

---

### Post by chili555 on 2013-11-20
> **Farfrae said:**
> No same as above without the wire. No recognition of wireless although my wireless light is lit on the hard button (it's a button rather than a switch - showing on).Let's see:```
sudo modprobe ipw2200
dmesg | grep -e ipw -e eth
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by Farfrae on 2013-11-20
I am no expert, and I might be using the wrong terminology - I mean in the BIOS settings. It is a HP NC6220 laptop. It has worked perfectly with Lubuntu for a couple of years until I upgraded to 13.10 last week, and suddenly it is all a bit flaky.

If it is any use, there is more info on my post here:[http://ubuntuforums.org/showthread.php?t=2188725](http://ubuntuforums.org/showthread.php?t=2188725)

andrew@andrew-laptop:~$ sudo modprobe ipw2200
andrew@andrew-laptop:~$ dmesg | grep -e ipw -e eth
[    1.565214] tg3 0000:10:00.0: eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:12:79:be:10:0d
[    1.565223] tg3 0000:10:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.565227] tg3 0000:10:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.565231] tg3 0000:10:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   19.762757] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.884568] libipw: 802.11 data/management/control stack, git-1.1.13
[   19.884572] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.887776] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   19.887781] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.544092] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.548233] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.759907] tg3 0000:10:00.0: eth0: Link is up at 100 Mbps, full duplex
[   54.759914] tg3 0000:10:00.0: eth0: Flow control is off for TX and off for RX
[   54.760192] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
andrew@andrew-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


andrew@andrew-laptop:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false

---

### Post by Farfrae on 2013-11-20
I have tried a fresh install and reverting back to 12.04 & 12.10 but no better. 

Thanks again

Andrew

---

### Post by chili555 on 2013-11-20
> **Farfrae said:**
> I am no expert, and I might be using the wrong terminology - I mean in the BIOS settings. It is a HP NC6220 laptop. It has worked perfectly with Lubuntu for a couple of years until I upgraded to 13.10 last week, and suddenly it is all a bit flaky.

If it is any use, there is more info on my post here:[http://ubuntuforums.org/showthread.php?t=2188725](http://ubuntuforums.org/showthread.php?t=2188725)

andrew@andrew-laptop:~$ sudo modprobe ipw2200
andrew@andrew-laptop:~$ dmesg | grep -e ipw -e eth
[    1.565214] tg3 0000:10:00.0: eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:12:79:be:10:0d
[    1.565223] tg3 0000:10:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.565227] tg3 0000:10:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.565231] tg3 0000:10:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   19.762757] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.884568] libipw: 802.11 data/management/control stack, git-1.1.13
[   19.884572] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.887776] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   19.887781] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.544092] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.548233] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.759907] tg3 0000:10:00.0: eth0: Link is up at 100 Mbps, full duplex
[   54.759914] tg3 0000:10:00.0: eth0: Flow control is off for TX and off for RX
[   54.760192] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
andrew@andrew-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


andrew@andrew-laptop:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=falseI see nothing wrong here at all, except that Network Manager will prefer ethernet over wireless and ethernet is up and evidently connected. Please detach the ethernet, reboot and do:```
dmesg > andrew.txt
rfkill list all >> andrew.txt
sudo iwlist eth1 scan >> andrew.txt
iwconfig >> andrew.txt
```Now connect the ethernet, get a coonection and then find the file andrew.txt in your user directory and copy and paste it here, giving us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

I am surprised we don't see an eth1 here; it's the interface usually created by ipw2200.

---

### Post by Farfrae on 2013-11-20
i now have an interesting new symptom in that, without the ethernet cable plugged in it took 10+ attempts to boot before finally managing it.

I was definitely seeing eth1 last week - and it reappears in the second of these pastes booted when I had the ethernet cable plugged in (it was the only way I could get the PC to boot - I pasted to andrew1.txt  the second time so should not gave affected the first one. It has hard blocked the WLAN again without me doing anything.

Paste 1 with no cable and no eth1: [http://paste.ubuntu.com/6448959/](http://paste.ubuntu.com/6448959/)

Paste 2 with cable - eth1 reappears: [http://paste.ubuntu.com/6448963/](http://paste.ubuntu.com/6448963/)

Paste 3 another reboot with cable in and different results eth1 gone again: [http://paste.ubuntu.com/6448994/](http://paste.ubuntu.com/6448994/)

---

### Post by kjacobs on 2013-11-20
I did the above and then tried this....

sudo iwlist eth1 scan

I got the interface does not support scanning error...although, after a reboot it appears I may have the wifi back again. I will test this for a bit and see what happens....

Ken

---

### Post by Farfrae on 2013-11-20
Mine comes and goes after reboots seemingly at random. If the wireless is working, it all seems good, and then everything will freeze up and require a slow shutdown after a few minutes.

I hope you've managed to solve your issue anyway. I notice someone else has posted tonight with Lubuntu 2200BG problems. I can't help but think that something has gone wrong here.

---

### Post by kjacobs on 2013-11-20
Yes....I did find it strange. For me, I could go back to 12.10 on the live cd and everything worked fine. Switching to 13.10 caused it to disappear. I actually have two of these identical laptops, so my first try was to switch wifi cards....which, of course, did not help. The other laptop running xubuntu 11.10 worked great with either card. So it is definitely something in 13.10 for sure.....

I will leave this open for a bit and see if you can resolve yours....adding "rfkill unblock all" to the rc.local seems to have worked for me, but did not until after the reboot.

---

### Post by chili555 on 2013-11-20
> **Farfrae said:**
> i now have an interesting new symptom in that, without the ethernet cable plugged in it took 10+ attempts to boot before finally managing it.

I was definitely seeing eth1 last week - and it reappears in the second of these pastes booted when I had the ethernet cable plugged in (it was the only way I could get the PC to boot - I pasted to andrew1.txt  the second time so should not gave affected the first one. It has hard blocked the WLAN again without me doing anything.

Paste 1 with no cable and no eth1: [http://paste.ubuntu.com/6448959/](http://paste.ubuntu.com/6448959/)

Paste 2 with cable - eth1 reappears: [http://paste.ubuntu.com/6448963/](http://paste.ubuntu.com/6448963/)

Paste 3 another reboot with cable in and different results eth1 gone again: [http://paste.ubuntu.com/6448994/](http://paste.ubuntu.com/6448994/)Wow! You have a busy and unhappy system! I see a ton of these in the first paste but not the second:```
[    5.072009] mmc1: Controller never released inhibit bit(s).
[    5.083166] mmc1: Reset 0x2 never completed.
[    5.083166] mmc1: Reset 0x4 never completed.
[    5.284006] mmc1: Controller never released inhibit bit(s).
[    5.295170] mmc1: Reset 0x2 never completed.
[    5.295170] mmc1: Reset 0x4 never completed.
[    5.496044] mmc1: Controller never released inhibit bit(s).
[    5.508732] mmc1: Reset 0x2 never completed.
[    5.508732] mmc1: Reset 0x4 never completed.
[    5.708005] mmc1: Controller never released inhibit bit(s).
[    5.719785] mmc1: Reset 0x2 never completed.
[    5.719785] mmc1: Reset 0x4 never completed.
```I see this as well in both #1 and #2:```
[   31.739000] ACPI Warning: 0x00001060-0x0000107f SystemIO conflicts with Region \_SB_.C002.C003.C092 1 (20120320/utaddress-251)
[   31.739008] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   31.739010] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   31.739015] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \_SB_.C002.C003.C08A 1 (20120320/utaddress-251)
[   31.739021] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   31.739025] ACPI Warning: 0x00001100-0x0000113f SystemIO conflicts with Region \_SB_.C002.C003.C09A 1 (20120320/utaddress-251)
[   31.739031] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   31.739033] lpc_ich: Resource conflict(s) found affecting gpio_ich
```In #2, although I assume you didn't touch the wireless switch or key combination, I see this:```
[   20.944640] ipw2200: Radio Frequency Kill Switch is On:
[   20.944640] Kill switch must be turned off for wireless networking to work.
```As well as:```
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```In #3, the ACPI warnings are there, and rfkill is there. The mmc lines look pretty normal.

Usually, the BIOS can safely be set to defaults and Ubuntu will work properly. Where is yours set? Do you think you did bump the wireless switch or no? 

Is it possible there is another issue with the laptop?

---

### Post by Farfrae on 2013-11-20
Thanks for taking a detailed look.

I definitely didn't touch the wireless switch for the first boot.

The only bits of BIOS I messed with (a few days ago) were the LAN/WLAN switching (this got my WIFI light back on after it first went wrong) and the LAN Power saving. When I first went in there, the LAN power saving was on and the LAN/WLAN switching was off. Switching that on restored Wifi intermittently, but with freezing screen.

I experimented with every possible combination of those two settings (on/on on/off off/on and off/off) and most made it worse. The default is off/off but that gives no wireless capability. Those two settings are currently set on/on.

It is possible that there is another issue with the laptop as I am now getting booting issues, although I thought this was probably connected. I had to press power on and slow shutdown a few times before each of the pastings above. Could that have caused the errors?

Another thing I did a couple of days ago was to add ipw2200 to the /etc/modules. I found it as a suggestion on another post (from you coincidentally but probably for an issue particular to that poster). I removed it again tonight after the pastings above. It made no difference either way.

It is old and probably wearing out a bit, but I treat it as a matter of great pride that I have such an old machine operating so quickly and usefully using Lubuntu. 

Do you have any other thoughts? Is it time to go at it with a screwdriver? My Mum has an identical one she doesn't really use any more, so I could retrieve it and swap the wireless bits around, although I think Ken has done that without any luck.

Thanks again

Andrew

---

### Post by chili555 on 2013-11-20
I have few suggestions. You might try the rc.local step I suggested above in post #8. Aside from that, I am baffled that there are alarming messages having nothing to do with wireless that seem to come and go with no explanation or provocation. I am suspicious that there is an electrical fault that also comes and goes. If I were going to try a swap from another machine, I'd try swapping the harddrive. Then you could see in dmesg if mmc, ACPI and wireless are better, worse or the same. Unlike that other operating system, you can swap drives easily and have the system work well after a reboot or two.

---

### Post by Farfrae on 2013-11-21
rc.local made no difference (I had to make the change using nano - I hope that achieves the same effect).

I will put another hard drive in and do a fresh install and see where that leaves me. The hard drive was making some funny noises a few months ago so perhaps it now has a scratch on it. I did a check at the time, and it said it was OK (although it also mentioned bad sectors and an improbably high number).

It might be time to get a new one, although I have been fearing the Windows 8 machine issues I've seen people have had.

Thank you for all your help chili555. I really just wanted someone more knowledgeable to rule out driver issues etc, before I assumed hardware problems. I think we've got there now.

Ken - please feel free to mark your thread as solved and thanks for letting me use your thread too.

Andrew

---

### Post by kjacobs on 2013-11-21
Hi Andrew,

I am afraid I cannot mark this thread as solved....LOL. I have been running the laptop now today for a couple hours and lost the wifi connection twice. Each time I reboot it comes back on (with the rfkill unblock all in the rc.local), but then it still quits after running for a bit. The sporadic loss of wifi is very disturbing.....any other ideas???

Ken

---

### Post by chili555 on 2013-11-21
> **kjacobs said:**
> Hi Andrew,

I am afraid I cannot mark this thread as solved....LOL. I have been running the laptop now today for a couple hours and lost the wifi connection twice. Each time I reboot it comes back on (with the rfkill unblock all in the rc.local), but then it still quits after running for a bit. The sporadic loss of wifi is very disturbing.....any other ideas???

KenAre there any clues as to why it drops?```
cat /var/log/syslog | grep -e eth1 -e etwork | tail -n20
```Please run this just after a drop and post the result.

---

### Post by kjacobs on 2013-11-26
Well not sure what to make of the wifi issue. I tried for two days at home to get a log after a wifi dropped, but it never did drop. Took the laptop back to work today and it dropped a number of times. Seems to be selective of which signals it drops....LOL. Not sure what to do with it from here with these intermittent dropping.......

Ken

---

### Post by chili555 on 2013-11-27
> **kjacobs said:**
> Well not sure what to make of the wifi issue. I tried for two days at home to get a log after a wifi dropped, but it never did drop. Took the laptop back to work today and it dropped a number of times. Seems to be selective of which signals it drops....LOL. Not sure what to do with it from here with these intermittent dropping.......

KenSometimes, in corporate environments, these devices, most actually, drop because there are many access points with the same SSID and the wireless device tries to roam to what it supposes is a stronger signal. You can check this with:```
nm-tool
```Do you see several access points with the same name? You can attempt to force the system to stay on your preferred access point with this method:  [http://ubuntuforums.org/showthread.php?t=2188216&highlight=BSSID](http://ubuntuforums.org/showthread.php?t=2188216&highlight=BSSID)

You can also try to get the driver to not roam:```
sudo modprobe -r ipw2200
sudo modprobe ipw2200 roaming=0
```If the latter works, we will need to write a file to make it persistent.

---

### Post by kjacobs on 2013-12-05
Hi again,

SSID is not a problem here....this is a small business location with only 1 wifi router. There a few other wifi hot spots arond, but none with the same SSID. So I am guessing that removing roaming will not help this situation.

---

### Post by chili555 on 2013-12-05
> **kjacobs said:**
> Hi again,

SSID is not a problem here....this is a small business location with only 1 wifi router. There a few other wifi hot spots arond, but none with the same SSID. So I am guessing that removing roaming will not help this situation.I suggest you try anyway. It's easy enough to reverse.

---

### Post by zblace on 2014-01-01
Running HP50 laptop with Lubuntu 13.10 since few days and can report same issues... first it worked then it stopped and it still works from USB stick but not from HD install which was upgraded since with latest updates... I think I will revert to original clean install and avoid updates for a while :-/

---

