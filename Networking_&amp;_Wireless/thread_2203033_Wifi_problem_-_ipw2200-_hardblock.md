---
title: "Wifi problem - ipw2200- hardblock"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by emanuela on 2014-02-01
```
[CODE]
```[/CODE]Hello, I have been struggling with this problem for days and I haven't find a solution yet, so I finally ask here. In first place, I was trying to solve the problem that, when the pc was suspended, once logged in again, the wifi network was disabled by hardware switch. Before suspension wifi worked correctly. So I tried to implement some solution to the same problem found on forums, but with the result that now wifi isn't working always, not only after suspension. 

From what I could understand, the wifi is hard blocked but the keyboard button for wifi never worked, so it is impossible to remove hardblocking pressing some button. rfkill doesn't work because is not softblocked.

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```

My idea is that the problem is linked to this dmesg excerpt:
```
[   25.852376] ipw2200: Radio Frequency Kill Switch is On:
[   25.852379] Kill switch must be turned off for wireless networking to work.
```

 
iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

ifconfig:
```
eth0      Link encap:Ethernet  IndirizzoHW 00:0a:e4:12:e6:fe  
          indirizzo inet:192.168.2.2  Bcast:192.168.2.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::20a:e4ff:fe12:e6fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2395 errors:3 dropped:4 overruns:3 frame:0
          TX packets:2223 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:1766381 (1.7 MB)  Byte TX:368751 (368.7 KB)
          Interrupt:11 Indirizzo base:0x3000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:12132 (12.1 KB)  Byte TX:12132 (12.1 KB)


```


I tried a lot of things but no one seems to be working, I think I need some guidance on this problem.
Thank you in advance

---

### Post by chili555 on 2014-02-01
There is often a helper module that translates key presses into action, such as 'turn on the wireless, please.' We suspect there is one for your laptop and that it isn't loading as expected. What is the make and model of your laptop?

Also, please try:```
sudo modprobe -r ipw2200
sudo modprobe ipw2200 disable=0
rfkill list all
```Finally, please do:```
tail -f /var/log/syslog
```Leaving the terminal open to see what happens, manipulate the wireless button and see if the kernel responds. What, if any, are the messages that appear in *syslog*? Get out of tail with Ctrl+c.

Please run the tests with the ethernet detached.

---

### Post by emanuela on 2014-02-01
My model is Acer TravelMate 382 (or 380). I found some hint about the packet acerhk being needed to make keyboard special keys working (the wifi power on button in particular), still I had problem compiling it, but in case is worth I would give it a thorough try.

First batch of code doesn't change things, in particular rfkill gives the previous result(soft block:no, hard block: yes).

Pressing keyboard button for wifi gives no change in syslog. Nevertheless, it possibly might be worth quoting some lines in syslog: 
```
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> enable requested (sleeping: no  enabled: no)
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> waking up and re-enabling...
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> WWAN now enabled by management service
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> (eth0): now managed
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> (eth0): bringing up device.
Feb  1 16:00:56 emiliano-TravelMate-380 kernel: [ 4876.130901] 8139too 0000:02:0a.0: eth0: link down
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> (eth0): preparing device.
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> (eth0): deactivating device (reason 'managed') [2]
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  1 16:00:56 emiliano-TravelMate-380 kernel: [ 4876.132685] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> (eth1): now managed
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> (eth1): bringing up device.
Feb  1 16:00:56 emiliano-TravelMate-380 NetworkManager[737]: <info> (eth1): deactivating device (reason 'managed') [2]


```

Thank you for your attention

---

### Post by emanuela on 2014-02-01
Still, I don't think the bug mentioned in syslog is linked to my problem, in first place because (eth0) is the Ethernet adapter, not the wireless one which if I am correct is (eth1). I thought it would be useful to know the device state change- unmanaged -> unavailable

---

### Post by chili555 on 2014-02-01
> I found some hint about the packet acerhk being needed to make keyboard special keys working (the wifi power on button in particular), still I had problem compiling it, but in case is worth I would give it a thorough try.So, were you able to get it compiled? I hope not. There is a newer module installed in all recent Ubuntu versions. Let's load it and see if it helps:```
sudo modprobe acer-wmi
rfkill list all
```Manipulate the wireless button once and then:```
rfkill list all
```We are interested in any changes at all.

May we see:```
cat /etc/modprobe.d/blacklist.conf | tail -n5
```> the wireless one which if I am correct is (eth1).Quite correct.

---

### Post by emanuela on 2014-02-01
No, I haven't succeded in installing acerhk because even the verbose make got stuck with no further response so I CRTL-C it and didn't go any further.

```
sudo modprobe acer-wmi 
```

gives 

```
FATAL: Error inserting acer_wmi (/lib/modules/3.0.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
```

Modprobe gives:

```
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


```

---

### Post by emanuela on 2014-02-01
If I am not wrong, Fatal error means the device is too old to support acer-wmi([https://code.google.com/p/aceracpi/issues/detail?id=63](https://code.google.com/p/aceracpi/issues/detail?id=63)); in this case is it really necessary to make keyboard button work (maybe with acerhk), or instead it is better to disable the hard blocking if it is anyhow possible?

---

### Post by chili555 on 2014-02-01
Hmmm. I'm not quite sure I understand the error. Let's see:```
modinfo acer-wmi
dmesg | grep -i -e wmi -e dmi
```I suspect if you upgrade to Ubuntu 12.04 LTS, it will be fixed. It is easy enough to try the live DVD or USB to find out.

---

### Post by emanuela on 2014-02-01
```
 modinfo acer-wmi
filename:       /lib/modules/3.0.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko
alias:          wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026
alias:          wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3
alias:          wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB
license:        GPL
description:    Acer Laptop WMI Extras Driver
author:         Carlos Corbacho
srcversion:     6810B80A05651A53BE0470F
depends:        sparse-keymap,wmi
vermagic:       3.0.0-32-generic SMP mod_unload modversions 686 
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)


```

```

[    0.000000] DMI: Acer TravelMate 380/TravelMate 380, BIOS V1.02      08/19/04  
[ 6424.990880] wmi: Mapper loaded
[ 6424.996437] acer_wmi: Acer Laptop ACPI-WMI Extras
[ 6424.996486] acer_wmi: No or unsupported WMI interface, unable to load
[ 6433.541180] acer_wmi: Acer Laptop ACPI-WMI Extras
[ 6433.541203] acer_wmi: No or unsupported WMI interface, unable to load


```

I have recently upgraderd to 12.04 LTS. As I mentioned before, the wifi was working, but giving me the wifi problem after suspension. Now I messed up the system trying to fix the suspension error, and unfortunately I got the problem all the time; still it was present also before no matter what the distribution.

---

### Post by chili555 on 2014-02-01
I think it would help to undo everything you did to try to fix the suspend issue. If you don't recall, you may get some help by recalling the last terminal commands:```
history
```If the commands scroll by too fast, try:```
history | less
```Use the arrow keys to scroll back and forth.

If you have any doubts about what to change, stop and ask first.

It may also help to update to the 3.2.0-xx kernel; you are now running 3.0.0-xx. [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop/UbuntuDesktop-12.04](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop/UbuntuDesktop-12.04)

You may be able to update with:```
sudo apt-get update && sudo apt-get -y upgrade
```And then reboot.

There is a technique to restore wireless after suspend that we can try (and easily undo if it doesn't help) but we need to get the wireless running first.

---

### Post by emanuela on 2014-02-01
One thing I might have messed up is ipw2200 firmware, is there a way to check if it is all right?

update & upgrade says:
0 updated, 0 installed, 0 to be removed and 0 not updated

---

### Post by chili555 on 2014-02-01
> **emanuela said:**
> One thing I might have messed up is ipw2200 firmware, is there a way to check if it is all right?

update & upgrade says:
0 updated, 0 installed, 0 to be removed and 0 not updatedIf the firmware were missing or corrupted, I doubt that the result would be hardblocked:yes. It is, however, easy enough to check:```
md5sum /lib/firmware/ipw2200*

```My system says:> 045a46163341514ef17490c76bd0c858  /lib/firmware/ipw2200-bss.fw
44cdedc8d5a0eb727466ed982db97a53  /lib/firmware/ipw2200-ibss.fw
ebc70dce66f876695fa8852b8ff757ee  /lib/firmware/ipw2200-sniffer.fw

---

### Post by emanuela on 2014-02-01
Ok firmware is the same. Also, I think I have the latest kernel for uname gives:
```
 uname -r
3.2.0-58-generic-pae


```

I try to go back in history, but I've already tried to understand what wrong I have done and didn't get out anything; maybe a second try would work.

---

### Post by emanuela on 2014-02-01
So it is ok for acer-wmi to give the Fatal error before?

---

### Post by emanuela on 2014-02-01
Also, I have installed and remove wicd, could it be a problem?

---

### Post by chili555 on 2014-02-01
```
3.2.0-58-generic-pae
```Excellent! 

To try to solve your suspend problems, did you edit system files? With gedit?```
history | grep edit
```With nano?```
history | grep nano
```

---

### Post by chili555 on 2014-02-01
> **emanuela said:**
> Also, I have installed and remove wicd, could it be a problem?I am 99.9% sure iit couldn't cause a hardblocked issue. What else have you tried?

---

### Post by emanuela on 2014-02-01
[LIST=1]
[*]/etc/NetworkManager/NetworkManager.conf

changed 
[ifupdown] 
managed: false 

to 
[ifupdown] 
managed: true
[*]Other files that I gedited, but I'm pretty sure I have replaced back the changes:

/var/lib/NetworkManager/NetworkManager.state
/etc/pm/config.d/config (which is empty)
 /etc/pm/sleep.d/wakenet.sh
/usr/lib/pm-utils/sleep.d/55NetworkManager
[/LIST]

---

### Post by emanuela on 2014-02-01
I see in history that I have run

sudo m-a -vt a-i acerhk

but this gives "Installation of acer-hk source failed, Ignoring this package"
so I don't think that's the problem.

I am having hard time finding what I have changed. Is there a way to bring back the system to the just upgraded moment? I haven't any backup image and I'd like to keep my files, but maybe reinstall all system files?

---

### Post by chili555 on 2014-02-01
> /etc/NetworkManager/NetworkManager.conf

changed
[ifupdown]
managed: false I believe this is managed=false not managed:false. Please check and change if needed.> /etc/pm/config.d/configPlease edit the file to add:```
SUSPEND_MODULES="ipw2200"
```Proofread carefully before you save and close the text editor. 

Then please let us see:```
cat /etc/pm/sleep.d/wakenet.sh
cat /usr/lib/pm-utils/sleep.d/55NetworkManager
```You got right down to the warp core, didn't you!?

---

### Post by emanuela on 2014-02-01
wakenet.sh is empty, i don't know if this is ok.

```


 cat /usr/lib/pm-utils/sleep.d/55NetworkManager
#!/bin/sh
# If we are running NetworkManager, tell it we are going to sleep.
# TODO: Make NetworkManager smarter about how to handle sleep/resume
#       If we are asleep for less time than it takes for TCP to reset a
#       connection, and we are assigned the same IP on resume, we should
#       not break established connections.  Apple can do this, and it is
#       rather nifty.

. "${PM_FUNCTIONS}"

suspend_nm()
{
    # Tell NetworkManager to shut down networking
        printf "Having NetworkManager put all interaces to sleep..."
    dbus_send --print-reply --system                         \
        --dest=org.freedesktop.NetworkManager  \
        /org/freedesktop/NetworkManager        \
        org.freedesktop.NetworkManager.sleep && \
        echo Done. || echo Failed.
}

resume_nm()
{
    # Wake up NetworkManager and make it do a new connection
    printf "Having NetworkManager wake interfaces back up..."
        dbus_send --print-reply --system                        \
        --dest=org.freedesktop.NetworkManager \
        /org/freedesktop/NetworkManager       \
        org.freedesktop.NetworkManager.wake && \
        echo Done. || echo Failed.
}

case "$1" in
    hibernate|suspend)
        suspend_nm
        ;;
    thaw|resume)
        resume_nm
        ;;
    *) exit $NA
        ;;
esac


```

I am not sure if I get your question right: in case it was if I scrolled down all the history, and not just the first page given by less, the answer is yes, I scrolled all.

---

### Post by chili555 on 2014-02-01
Please do:```
sudo touch /etc/pm/sleep.d/wakenet.sh
sudo chmod +x /etc/pm/sleep.d/wakenet.sh
gksudo gedit /etc/pm/sleep.d/wakenet.sh
```Add the following:```
#!/bin/bash
case "$1" in
thaw|resume)
nmcli nm sleep false
;;
*)
;;
esac
exit $?
```Be quite certain it is formatted as I have here and proofread carefully twice before you save and close gedit. 

Your /usr/lib/pm-utils/sleep.d/55NetworkManager looks correct so far. I will do some further checking.

Reboot with the ethernet detached and run:```
rfkill list all
```Press the wireless button and then:```
rfkill list all
```I have my fingers crossed.

---

### Post by emanuela on 2014-02-01
I have done all the steps, but before and after pressing wireless button I get the same:
```

rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
Hard Blocked: yes

```

I don't understand how changing a script in the sleep.d folder would affect wireless button behavior; aren't scripts in sleep.d folder ran only when the system is suspended?

---

### Post by chili555 on 2014-02-01
> I don't understand how changing a script in the sleep.d folder would affect wireless button behaviorI quite agree. However, since you said it all started when you tried to fix the sleep/resume behavior, all I know to do, at least so far, is to retrace your steps and see if we see anything wrong. If we do, correct it and keep trying.

Every time I think something is impossible and can't happen, this forum proves me wrong. 

Please do:```
dmesg > wifi.txt
```Find the file wifi.txt in your user directory. Paste it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

What does this tell us?```
cat /sys/class/rfkill/rfkill0/state
```If it returns 0, can you change it?```
sudo -i
echo 1 > /sys/class/rfkill/rfkill0/state
exit
```If there is no such directory, see what you do have that's similar:```
ls /sys/class/rfkill
```Try to find a state file and cat its contents. See if you can echo 1 into it. Then check:```
rfkill list all
```

---

### Post by emanuela on 2014-02-01
Link to the pastebin: [http://paste.ubuntu.com/6857786/](http://paste.ubuntu.com/6857786/). I also pasted my history in case you can glance what could be wrong [http://paste.ubuntu.com/6857790/](http://paste.ubuntu.com/6857790/).

There is only the directory rfkill3 instead of rfkill0, so I have done  echo 1 > /sys/class/rfkill/rfkill3/state.

rfkill list all changed the result a bit, now being the first output number 3 instead of 0:

```
 rfkill list all
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by chili555 on 2014-02-01
Remember when I said whenever something seems impossible, it happens on the forum? It may happen soon! I saw this in your pastebin:> ipw2200: Failed to send POWER_MODE: Command timed out.I Googled it and saw this: [http://forum.linuxmint.com/viewtopic.php?f=53&t=130897](http://forum.linuxmint.com/viewtopic.php?f=53&t=130897)> I solved this problem by DISABLING the wlan in the BIOS settings. Totally counter-intuitive, but all now works.Crazy! Would you please first try setting the BIOS to DEFAULT and then reboot and see if it changes? Then try disabling wireless in the BIOS (yes, I know, crazy) and boot into Ubuntu and see if things change.

---

### Post by emanuela on 2014-02-01
I had found too a post where was mentioned to set the BIOS to default, so I had already done that with no results. 
So I searched a way to disable the wireless in the BIOS, but there isn't. I have PhoenixBIOS setup Utility and I am pretty sure it is not possible to tweak with net tools.

---

### Post by emanuela on 2014-02-01
Hold on, I reset again the BIOS and now the wireless works again! A little strange indeed :)

The problem is still present after suspension, still I could bear it,  not being such an big hassle. 
Thank you very much for your help for now, it was crucial!

---

### Post by chili555 on 2014-02-01
> The problem is still present after suspension,Is the driver ipw2200 loaded after you resume?```
lsmod
```

---

### Post by emanuela on 2014-02-01
yes, it is the first module actually:

```
 lsmod
Module                  Size  Used by
ipw2200               146241  0 
libipw                 46732  1 ipw2200
cfg80211              178877  2 ipw2200,libipw
lib80211               14040  2 ipw2200,libipw
joydev                 17393  0 
snd_intel8x0           33455  2 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 38139  0 
psmouse                86546  0 
bnep                   17830  2 
parport_pc             32114  0 
soundcore              14635  1 snd
i915                  428248  2 
serio_raw              13027  0 
irda                  185517  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
binfmt_misc            17292  1 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
crc_ccitt              12627  1 irda
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
shpchp                 32265  0 
mac_hid                13077  0 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
8139too                23283  0 
8139cp                 26718  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


```

---

