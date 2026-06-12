---
title: "No internet connection (both ethernet &amp; wifi) after 22.04 upgrade"
date: 2023-09-22
forum: Networking &amp; Wireless
---

### Post by stinktier2 on 2023-09-22
Hiya all, I just upgraded my Lenovo Thinkpad X220 to the latest Xubuntu 22.04 (from 20.04). After the reboot no internet connection is possible – neither wifi nor ethernet. In the network applet both Ethernet Network and Wi-Fi Networks just "disconnected". I can "see" the available WLANs, but the computer just won't connect successfully.

Something must have been broken during the upgrade, but for the life of me I just can't find out what. I don't even have an idea how and where to look...

Please help!

---

### Post by #&amp;thj^% on 2023-09-22
Not sure I can help but please give this shot:
```
sudo nmcli networking on

```

---

### Post by stinktier2 on 2023-09-22
> **1fallen said:**
> Not sure I can help but please give this shot:
```
sudo nmcli networking on

```

Nope, nothing changed. Even after a reboot.

---

### Post by #&amp;thj^% on 2023-09-22
One more:
```
sudo nmcli n on
```
If not try to use nmtui-tool
```
nmtui
```
If none of the above works, well I hate saying but a fresh install will be your only other option.
Good Luck

---

### Post by stinktier2 on 2023-09-22
> **1fallen said:**
> One more:
```
sudo nmcli n on
```
If not try to use nmtui-tool
```
nmtui
```
If none of the above works, well I hate saying but a fresh install will be your only other option.
Good Luck

Nothing worked. ```
nmtui
``` can not activate any Wired or Wireless connection. 
With my Wired connection the error is "[...] Connection 'Wired connection 1' is not available on device enp0s25 because device has no carrier"
With my Wi-Fi connection the error is "Activation failed: Secrets were required , but not provided" (This is with an open WLAN.)

---

### Post by #&amp;thj^% on 2023-09-22
Interesting, but that sucks I think your the third or forth poster to find this mishap:
```
systemctl status NetworkManager

```
Maybe?

---

### Post by stinktier2 on 2023-09-22
> **1fallen said:**
> Interesting, but that sucks I think your the third or forth poster to find this mishap:
```
systemctl status NetworkManager

```
Maybe?

This is the result:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292767&stc=1[/IMG]

What does that mean?

---

### Post by #&amp;thj^% on 2023-09-22
humm, a possible maybe:
```
sudo dhclient
```
Then if that works we need to look at other things to find why.

---

### Post by stinktier2 on 2023-09-22
> **1fallen said:**
> humm, a possible maybe:
```
sudo dhclient
```
Then if that works we need to look at other things to find why.
Nothing happens. I enter my password and then... nothing. No prompt, no error, nothing.

EDIT: After a couple of minutes the prompt became available and Ubuntu finished whatever it was doing in the background. The wired connection was established, but no actual connection (websites, updates) is happening. The Vivaldi browser simply states "No internet". Wireless still seems impossible.

---

### Post by #&amp;thj^% on 2023-09-22
> **stinktier2 said:**
> Nothing happens. I enter my password and then... nothing. No prompt, no error, nothing.

I'm not sure i under stand? did it show anything like:
```
 sudo dhclient
[sudo] password for me: 
RTNETLINK answers: File exists
Setting LLMNR support level "yes" for "2", but the global support level is "no".


```

---

### Post by stinktier2 on 2023-09-22
> **1fallen said:**
> I'm not sure i under stand? did it show anything like:
```
 sudo dhclient
[sudo] password for me: 
RTNETLINK answers: File exists
Setting LLMNR support level "yes" for "2", but the global support level is "no".

```

No, that's not how it works on the Thinkpad. It just shows the prompt again after a couple of minutes. No line with "RTNETLINK" or "LLMNR". As I said, it somehow builds a wired connection, which is useless (no DNS, nothing).

---

### Post by #&amp;thj^% on 2023-09-22
> **stinktier2 said:**
> No, that's not how it works on the Thinkpad. It just shows the prompt again after a couple of minutes. No line with "RTNETLINK" or "LLMNR". As I said, it somehow builds a wired connection, which is useless (no DNS, nothing).

Not interested in opinions, do you now have internet or not?
All my laptops are Lenovo

---

### Post by stinktier2 on 2023-09-22
> **1fallen said:**
> Not interested in opinions, do you now have internet or not?
All my laptops are Lenovo

No, not on the laptop. Everything there is "disconnected" (and won't connect).

---

### Post by #&amp;thj^% on 2023-09-22
> **stinktier2 said:**
> No, not on the laptop. Everything there is "disconnected" (and won't connect).

Thank You ;)
Now all I add is a reinstall.

---

### Post by stinktier2 on 2023-09-22
> **1fallen said:**
> Thank You ;)
Now all I add is a reinstall.

This sucks. :sad::sad::sad:

---

### Post by #&amp;thj^% on 2023-09-22
> **stinktier2 said:**
> This sucks. :sad::sad::sad:
Indeed, makes me sad as well, I love to see the [SOLVED]

---

### Post by stinktier2 on 2023-09-22
I will try to reinstall tomorrow. Hope I can do this without erasing the /home stuff. But I have a backup, so nothing is lost. But I hope this issue will not reoccur on the fresh system...

---

### Post by #&amp;thj^% on 2023-09-22
> **stinktier2 said:**
> But I hope this issue will not reoccur on the fresh system...
It has so far, so fingers crossed.
Let us know either way though please.
```
inxi -N
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169

```
I don't do WiFi on this machine by choice.
EDIT: For All who do a inline upgrade without a back-up solution/Plan>> is to me nothing short of Planing to Fail.

---

### Post by stinktier2 on 2023-09-22
> **1fallen said:**
> It has so far, so fingers crossed.
Let us know either way though please.

Will do. Thanks for all your help!

---

### Post by stinktier2 on 2023-09-23
> **1fallen said:**
> It has so far, so fingers crossed.

1fallen, one last thing:
I have just booted from an Xubuntu 22.04.3 Live-DVD and am about to install the OS. But curiously, although the laptop is still plugged to the wired internet and I have an open (no password) wireless network, I still cannot connect to either. It's the same problem as after the update &#8211; all networks are disconnected and I cannot get online (networking is enabled, of course). I am afraid that the problem persists after I format and install anew, and I have lost my everything... :sad:

EDIT: Same issue with a LiveDVD of Xubuntu 23.04...

---

### Post by stinktier2 on 2023-09-23
I FEEL REALLY STUPID!


I just discovered that the Wired connection DOES work – the cable was just not plugged into the router! :oops: (It must have slipped off some time in the past, the plug doesn't lock...)

However, the wifi/ethernet connection still doesn't work – the laptop does not connect. The connection is labeled with the lock icon, although it is open/password-free (what my smartphone calls "Enhanced Open"). When I create a wifi hotspot with my phone, the laptop connects to it and has proper internet. So what's happening with the regular WLAN? :confused:

---

### Post by #&amp;thj^% on 2023-09-23
You know it's always the simple things I over look when helping, but good find.
Will you now please run the syystem-info script found in my signature.
Please include the link it gives you here in your thread, and run it with the "--details" flag. ie:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info ''details
```
This way I'll have most of what I/we need to see first before proceeding.
BTW since you secured the the connection, have you rebooted yet? without the Hot Spot active.

---

### Post by stinktier2 on 2023-09-23
> **1fallen said:**
> You know it's always the simple things I over look when helping, but good find.
Will you now please run the syystem-info script found in my signature.
Please include the link it gives you here in your thread, and run it with the "--details" flag. ie:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info ''details
```
This way I'll have most of what I/we need to see first before proceeding.
BTW since you secured the the connection, have you rebooted yet? without the Hot Spot active.

I have rebooted the laptop a couple of times. The hotspot was active only for a short time. Still cannot connect to this specific wireless connection.

Pastebin: [https://paste.ubuntu.com/p/4FSY8BcRpk](https://paste.ubuntu.com/p/4FSY8BcRpk)

---

### Post by #&amp;thj^% on 2023-09-23
I'm looking at now, but I still do not see a net device.
I'm on Arch for a few hours today I have obligations to fulfill first, but in the meantime will you show this please:
```
sudo apt-get install --reinstall network-manager
```
EDIT Also show this as well:
```
sudo apt install --reinstall wpasupplicant
```
I'll be back.

---

### Post by stinktier2 on 2023-09-23
> **1fallen said:**
> I'm looking at now, but I still do not see a net device.
I'm on Arch for a few hours today I have obligations to fulfill first, but in the meantime will you show this please:```
sudo apt-get install --reinstall network-manager
```
EDIT Also show this as well:```
sudo apt install --reinstall wpasupplicant
```
I'll be back.

Take your time. This is no longer critical. Annoying, yes, but no longer a panic-inducing issue.

Did both reinstalls and rebooted, no change at all in the behaviour re: wireless.

---

### Post by #&amp;thj^% on 2023-09-23
Annoying indeed, what shows with:
```
rfkill list all
```
Also is this your provider: [https://freifunk.net/en/how-to-join/](https://freifunk.net/en/how-to-join/)

---

### Post by stinktier2 on 2023-09-24
> **1fallen said:**
> Annoying indeed, what shows with:```
rfkill list all
```
Result:```
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless WAN
    Soft blocked: no
    Hard blocked: no
```
> **1fallen said:**
> Also is this your provider: [https://freifunk.net/en/how-to-join/](https://freifunk.net/en/how-to-join/)
This is correct. I have a second router with custom "Freifunk" firmware that is connected to the one of my regular provider. The Freifunk router provides this free, anonymous internet for me and anybody who wants to connect.

---

### Post by #&amp;thj^% on 2023-09-24
> **stinktier2 said:**
> 

This is correct. I have a second router with custom "Freifunk" firmware that is connected to the one of my regular provider. The Freifunk router provides this free, anonymous internet for me and anybody who wants to connect.

Well wlan is not blocked so you might have to ask "Freifunk" for help here, as I know nothing about them or their firmware.
And just a thought, have you rebooted the router yet?

---

### Post by sandkalam on 2024-04-28
Try

sudo ufw allow 53
sudo ufw allow 67
sudo ufw default allow FORWARD

---

### Post by praseodym on 2024-04-28
sudo rfkill unblock all
rfkill list

Remove all wired profiles from the NWM and reboot

---

### Post by him610 on 2024-04-29
@stinktier2, you could do everyone with fading eyesight a favor by copy the contents of the command/response and pasting between code tags.
Example....
```

hugh@ma90:~$ systemctl status NetworkManager
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2024-04-20 17:58:16 EDT; 1 week 1 day ago
       Docs: man:NetworkManager(8)
   Main PID: 492 (NetworkManager)
      Tasks: 3 (limit: 18416)
     Memory: 10.5M
        CPU: 19min 37.811s
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;492 /usr/sbin/NetworkManager --no-daemon

Apr 29 09:25:20 ma90 NetworkManager[492]: <info>  [1714397120.9884] policy: set-hostname: current hostname was changed outside NetworkManager: 'ma90'
Apr 29 09:25:20 ma90 NetworkManager[492]: <info>  [1714397120.9889] policy: set-hostname: current hostname was changed outside NetworkManager: 'ma90'
Apr 29 09:25:23 ma90 NetworkManager[492]: <info>  [1714397123.9950] policy: set-hostname: current hostname was changed outside NetworkManager: 'ma90'
Apr 29 09:25:23 ma90 NetworkManager[492]: <info>  [1714397123.9955] policy: set-hostname: current hostname was changed outside NetworkManager: 'ma90'
Apr 29 09:25:24 ma90 NetworkManager[492]: <info>  [1714397124.0606] policy: set-hostname: current hostname was changed outside NetworkManager: 'ma90'
Apr 29 09:25:24 ma90 NetworkManager[492]: <info>  [1714397124.0615] policy: set-hostname: current hostname was changed outside NetworkManager: 'ma90'
Apr 29 09:25:27 ma90 NetworkManager[492]: <info>  [1714397127.0141] policy: set-hostname: current hostname was changed outside NetworkManager: 'ma90'
Apr 29 09:25:27 ma90 NetworkManager[492]: <info>  [1714397127.0149] policy: set-hostname: current hostname was changed outside NetworkManager: 'ma90'
Apr 29 09:25:27 ma90 NetworkManager[492]: <info>  [1714397127.0302] policy: set-hostname: current hostname was changed outside NetworkManager: 'ma90'
Apr 29 09:25:27 ma90 NetworkManager[492]: <info>  [1714397127.0307] policy: set-hostname: current hostname was changed outside NetworkManager: 'ma90'

```

---

