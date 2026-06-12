---
title: "Can't get wifi (AX200NGW) to work in Ubuntu 16 kernel 4.15, Acer Predator"
date: 2020-03-26
forum: Networking &amp; Wireless
---

### Post by Nicolas_Castro on 2020-03-26
Hi guys, hope someone can give me some help on this. I need to keep using this distro and same kernel for the main purpose of the laptop, but need wifi to work.
I've trying backporting iwlwifi but no luck.
Here's some output

```
~$ dmesg | grep iwl
[    3.360385] Loading modules backported from iwlwifi
[    3.360385] iwlwifi-stack-public:master:8324:9176b151
[    3.490997] iwlwifi 0000:40:00.0: Direct firmware load for iwl-dbg-cfg.ini failed with error -2
[    3.491012] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-55.ucode failed with error -2
[    3.491154] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-54.ucode failed with error -2
[    3.491160] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-53.ucode failed with error -2
[    3.491165] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-52.ucode failed with error -2
[    3.491296] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-51.ucode failed with error -2
[    3.491392] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-50.ucode failed with error -2
[    3.491396] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-49.ucode failed with error -2
[    3.491400] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-48.ucode failed with error -2
[    3.491404] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-47.ucode failed with error -2
[    3.492969] iwlwifi 0000:40:00.0: loaded firmware version 46.3cfab8da.0 cc-a0-46.ucode op_mode iwlmvm
[    3.492977] iwlwifi 0000:40:00.0: Direct firmware load for iwl-debug-yoyo.bin failed with error -2
[    3.500605] iwlwifi 0000:40:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[    3.678361] iwlwifi 0000:40:00.0: base HW address: 38:00:25:95:af:1f
[    3.695448] iwlwifi 0000:40:00.0 wlp64s0: renamed from wlan0
```

Any clues? much appreciated, cheers!

---

### Post by chili555 on 2020-03-26
Despite all the interesting messages, it seems that an acceptable firmware file is found and loaded and a wireless interface is created:

> iwlwifi 0000:40:00.0 wlp64s0: renamed from wlan0Does it scan and see networks?

```
nmcli device wifi list
```Is the switch set to enable the wireless radio?

```
rfkill list all
```Any other interesting clues?

```
dmesg | grep wlp
```

---

### Post by praseodym on 2020-03-27
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.183.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.183.2_all.deb)

Install this file and reboot. Missing fw "48" inside

---

### Post by Nicolas_Castro on 2020-03-27
Thanks for help guys

> Does it scan and see networks?

     Code:

     nmcli device wifi list 


Yes, it does show networks after the things I've tried before, but the system hangs when I click connect.

```
nmcli device wifi list
*  SSID                       MODE   CHAN  RATE       SIGNAL  BARS  SECURITY  
   2degrees Broadband - 46E2  Infra  11    54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2      
   2degrees Broadband - 46E2  Infra  52    54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2      
   SPARK-6NFHYY               Infra  11    54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2 
   vodafoneF0FA28             Infra  1     54 Mbit/s  29      &#9602;___  WPA2      
   SPARK-6NFHYY-5G            Infra  36    54 Mbit/s  20      &#9602;___  WPA1 WPA2 


```

> Is the switch set to enable the wireless radio?

     Code:
     rfkill list all 

this one looks allright 

```
 rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

> Any other interesting clues?

     Code:
     dmesg | grep wlp 


yes, maybe here we have some clues

```
 dmesg | grep wlp
[    3.723189] iwlwifi 0000:40:00.0 wlp64s0: renamed from wlan0
[    4.670969] IPv6: ADDRCONF(NETDEV_UP): wlp64s0: link is not ready
[    4.921696] IPv6: ADDRCONF(NETDEV_UP): wlp64s0: link is not ready
[    5.446005] IPv6: ADDRCONF(NETDEV_UP): wlp64s0: link is not ready

```


>                           [http://security.ubuntu.com/ubuntu/po....183.2_all.deb]("http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.183.2_all.deb")

Install this file and reboot. Missing fw "48" inside 


Did this but still hangs when trying to connect. Cheers!

---

### Post by chili555 on 2020-03-27
> 
2degrees Broadband - 46E2  Infra  11    54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2      
2degrees Broadband - 46E2  Infra  52    54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2I suggest that you rename one or both of these instances; perhaps 2degrees5 and 2degrees2.4. Then try to connect to one or the other and tell us if it still hangs.

---

### Post by Nicolas_Castro on 2020-03-28
I renamed one of the files in this directory.

```

/etc/NetworkManager/system-connections$ ls -al
total 36
drwxr-xr-x 2 root root 4096 Mar 28 19:41 .
drwxr-xr-x 8 root root 4096 Mar 19 07:04 ..
-rw------- 1 root root  434 Mar 28 19:40 2degrees2
-rw------- 1 root root  459 Mar 28 19:41 2degrees2.JL13H0
-rw------- 1 root root  475 Mar 27 01:00 2degrees Broadband - 46E2.14D4H0
-rw------- 1 root root  475 Mar 27 00:27 2degrees Broadband - 46E2.2CU5H0
-rw------- 1 root root  475 Mar 27 00:31 2degrees Broadband - 46E2.6XETH0
-rw------- 1 root root  475 Mar 27 00:48 2degrees Broadband - 46E2.MLFWH0
-rw------- 1 root root  475 Mar 28 12:34 2degrees Broadband - 46E2.Y1GMH0


```

then edited the file and changed the id field. Rebooted, tried to connect and hanged again. 
> 
I suggest that you rename one or both of these instances; perhaps  2degrees5 and 2degrees2.4. Then try to connect to one or the other and  tell us if it still hangs.


I don't know if I'm doing this right.
Thanks!

---

### Post by chili555 on 2020-03-28
> 
I don't know if I'm doing this right.
I'm sorry if I didn't explain the process carefully.

I am suggesting that you go into the administrative pages of the router and rename the name that is broadcast, like this:

[IMG]https://www.howtogeek.com/wp-content/uploads/2014/09/img_542aac3310201.png[/IMG]

Your routers setup or administration pages will no doubt look different, but I hope this illustrates the process.

---

### Post by Nicolas_Castro on 2020-03-29
> **chili555 said:**
> I'm sorry if I didn't explain the process carefully.

I am suggesting that you go into the administrative pages of the router and rename the name that is broadcast, like this:



I did it, tried to connect and the system hanged. Now can't boot. 
Tried recovery mode and it hanged when was booting the full mode.
Please, I appreciate your help.

---

### Post by chili555 on 2020-03-29
> I did it, tried to connect and the system hanged. Now can't boot.
Tried recovery mode and it hanged when was booting the full mode.
Please, I appreciate your help.Are you able to boot at all in any mode?

If so, you may get an idea of the trouble if you check the message log:```
cat /var/log/syslog | grep -i error
cat /var/log/syslog | grep etwork
```

---

### Post by Nicolas_Castro on 2020-03-29
I can't even boot in recovery now. At some point it was booting and the GUI hanged when trying to automatically connect to the network at startup. But now I'm only getting to this point (pls forgive the pic):

[IMG]https://iili.io/JfRWdP.jpg[/IMG]

---

### Post by chili555 on 2020-03-29
I haven't the knowledge to suggest a solution. I see nothing there that points to wireless.

You might ask here: [https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331) There may be a solution but I am not a boot specialist, but a wireless and networking journeyman.

If it were me, I'd run a live USB session and try, if I could, to back up my essential files and reinstall the entire system.

Possibly useful: [https://askubuntu.com/questions/1001351/uuid-xxx-does-not-exist-dropping-to-a-shell](https://askubuntu.com/questions/1001351/uuid-xxx-does-not-exist-dropping-to-a-shell)

---

### Post by Nicolas_Castro on 2020-03-29
> 
Possibly useful: [https://askubuntu.com/questions/1001...ing-to-a-shell]("https://askubuntu.com/questions/1001351/uuid-xxx-does-not-exist-dropping-to-a-shell")

I'm back after this... So now booted normally.
But now I can't see any wifi available.
Got this in the log:

[https://paste.ubuntu.com/p/6w8tPj34YX/](https://paste.ubuntu.com/p/6w8tPj34YX/)


Thanks for help.

---

### Post by chili555 on 2020-03-29
> But now I can't see any wifi available.
Got this in the log:I don't see anything remarkable there. The ethernet starts and connects.

Let's have a look at:

```
dmesg | grep -e wlp -e iwl
```

---

### Post by Nicolas_Castro on 2020-03-29
> **chili555 said:**
> I don't see anything remarkable there. The ethernet starts and connects.

Let's have a look at:

```
dmesg | grep -e wlp -e iwl
```

No output after that:

```
:~$ dmesg | grep -e wlp -e iwl
:~$ 
```

---

### Post by chili555 on 2020-03-30
Your case gets more interesting by the minute; and by interesting, I mean weird!

The driver iwlwifi seemed to load automatically at the start but appears not to now. Let's load it from the command line and see if any interesting messages appear that help us find the solution:

```
sudo modprobe iwlwifi
dmesg | grep -e wlp -e iwl
```

---

### Post by Nicolas_Castro on 2020-03-31
Hi, I'm back, finally I had to re-install my OS again, so here with a fresh ubuntu 16, kernel 4.15. 
So I haven't even tried backporting this time (as the last time was too messy cause I've tried so many things). Could you please guide me the correct way to do it all over? It's kindly appreciated.
I have to say also that I'm atm connected through an USB-Ethernet adaptor (as my ethernet card is not being recognized either)

Thanks chilli555 for all the help.

[ATTACH]285357[/ATTACH]

---

### Post by chili555 on 2020-03-31
Something is wrong here. Your wireless info says:> 
##### release ###########################

Distributor ID:	Ubuntu
Description:	[COLOR="#FF0000"]Ubuntu 14.04.3 LTS[/COLOR]
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux [COLOR="#FF0000"]3.19.0-25-generic[/COLOR] #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7
<snip>
Please claify.

---

### Post by Nicolas_Castro on 2020-03-31
> Please claify.

Something must be wrong with the data retrieved by the script.

```
uname -r
4.15.0-91-generic
:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="16.04.5 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.5 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial


```

---

### Post by Nicolas_Castro on 2020-03-31
Oh WTF that was not my wireless report lol. Sorry attaching the correct one now. Thanks again.  

[ATTACH]285360[/ATTACH]

---

### Post by chili555 on 2020-03-31
It will be a bit tricky in 16.04 and quite easy in 18.04 LTS. As you have modern hardware, I see no reason to install a 4-year-old version and kernel. Please consider reinstalling 18.04 LTS.

However, if you prefer, we can get out the plasma cutter and sledge and do it the long way.

What would you like to do?

---

### Post by Nicolas_Castro on 2020-03-31
Yes I've considered upgrading the distro, but as I have to work with custom made apps that were compiled for CUDA 10 with Ubuntu 16 and kernel 4.15 I am forced to stick with the current environment.

I don't mind going the long way, and could re-install everything again if somethings gets screwed, and again I appreciate a lot your support. 

So let's go for it pls!

---

### Post by chili555 on 2020-04-01
A smart guy wrote out the procedure here: [https://askubuntu.com/questions/1156167/unable-to-get-wifi-adapter-working-clean-19-04-install-network-unclaimed/1156246#1156246](https://askubuntu.com/questions/1156167/unable-to-get-wifi-adapter-working-clean-19-04-install-network-unclaimed/1156246#1156246)You may safely copy and paste the commands so as to avoid any typographical errors.

Post back any questions or if you get stuck.

---

### Post by Nicolas_Castro on 2020-04-01
Thanks very much, it isn't working yet, so here we are:

```
dmesg | grep iwl
[    3.067521] Loading modules backported from iwlwifi
[    3.067521] iwlwifi-stack-public:master:8324:9176b151
[    3.116927] iwlwifi 0000:40:00.0: Direct firmware load for iwl-dbg-cfg.ini failed with error -2
[    3.117062] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-55.ucode failed with error -2
[    3.117071] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-54.ucode failed with error -2
[    3.117173] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-53.ucode failed with error -2
[    3.117179] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-52.ucode failed with error -2
[    3.117525] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-51.ucode failed with error -2
[    3.117680] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-50.ucode failed with error -2
[    3.117688] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-49.ucode failed with error -2
[    3.117694] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-48.ucode failed with error -2
[    3.117699] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-47.ucode failed with error -2
[    3.117705] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-46.ucode failed with error -2
[    3.117711] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-45.ucode failed with error -2
[    3.117718] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-44.ucode failed with error -2
[    3.117724] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-43.ucode failed with error -2
[    3.117729] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-42.ucode failed with error -2
[    3.117735] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-41.ucode failed with error -2
[    3.117980] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-40.ucode failed with error -2
[    3.117989] iwlwifi 0000:40:00.0: Direct firmware load for iwlwifi-cc-a0-39.ucode failed with error -2
[    3.117990] iwlwifi 0000:40:00.0: no suitable firmware found!
[    3.117993] iwlwifi 0000:40:00.0: minimum version required: iwlwifi-cc-a0-39
[    3.117995] iwlwifi 0000:40:00.0: maximum version supported: iwlwifi-cc-a0-55
[    3.117996] iwlwifi 0000:40:00.0: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git

```

---

### Post by chili555 on 2020-04-01
Firmware, you say? Let's fix it.

```
wget http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.183.2_all.deb
sudo dpkg -i linux*.deb
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```If there is no wireless, repeat the steps above where we renamed certain firmware files and then:

```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```

---

### Post by Nicolas_Castro on 2020-04-01
> [COLOR=#000000]Firmware, you say? Let's fix it.[/COLOR]

[COLOR=#000000]Code:
wget [http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.183.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.183.2_all.deb)
sudo dpkg -i linux*.deb
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi

[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000] [/COLOR]

Did this and was able to see the wifi networks available, when trying to connect to one of them (I've already changed the names, since last time)the system froze. Now can't boot, everything freezes at some point while loading the xserver, sometimes I get to see the ubuntu desktop loading and it freezes, some other times just a blank screen after the manufacturers logo.

---

### Post by Nicolas_Castro on 2020-04-01
Apparently it has to do with graphics now, cause when booted in recovery y tried to resume the full boot and could read some xrandr problems before it froze. I can access the system setup as well but don't know what to do there. 

Also, I can re-install everything, but would like to have a clue on what's breaking my system when trying to connect to a wifi, weird.

---

### Post by chili555 on 2020-04-01
> Apparently it has to do with graphics now, cause when booted in recovery y tried to resume the full boot and could read some xrandr problems before it froze. I can access the system setup as well but don't know what to do therI recommend that you try to capture as many of the errors as you can. Take a photograph with your phone, if necessary. Then ask here: [https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331)

All I know about graphics at all is that mine work mysteriously.

---

### Post by praseodym on 2020-04-02
Why not trying 20.04? The official release is in 3 weeks, however, it should work anyway with rolling updates until release point 1

---

### Post by Nicolas_Castro on 2020-04-02
As I said before I need to run apps compiled for this distro and this kernel, and can't give that extra work of migrating to the people that developed the apps (at least not now). 
I have a fresh install (again) but of course no wifi, I'm a little bit affraid of doing the same steps again cause I'll get to the same point:
- I can see the wireless networks available.
- When I try to connect the system freezes. (and somehow this breaks my graphics)

Weird as.

---

### Post by praseodym on 2020-04-02
Virtualbox?

---

### Post by Nicolas_Castro on 2020-04-08
> [COLOR=#000000]Virtualbox?[/COLOR]

Oh, I don't think that would work, as the apps make full use of the GPU and resources.

---

