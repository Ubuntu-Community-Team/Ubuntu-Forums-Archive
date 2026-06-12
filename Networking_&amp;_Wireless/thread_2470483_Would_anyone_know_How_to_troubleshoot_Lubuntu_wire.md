---
title: "Would anyone know How to troubleshoot Lubuntu wireless network 20.04 Lts"
date: 2021-12-31
forum: Networking &amp; Wireless
---

### Post by espectro2 on 2021-12-31
Hello friends Can anybody help me How can I be connected with ip valido but I can't browse the internet? why? I'm via wired internet at the moment I'm using Lubuntu **nm-tray**** ****nm-tray **is a simple Qt-based frontend for NetworkManager. I'm using **Lubuntu 20.04 lts**** **thank you for your attention happy new year to everyone in the community :smile::smile:

---

### Post by guiverc on 2021-12-31
Happy new year.

Sorry I don't understand your issue, but I'll provide some thoughts.

If I have network connection issues, I firstly explore my network condition using

```

ip link
ip addr
ip route
ping -c 2 192.168.15.16
ping -c 2 8.8.8.8
ping -c 2 iinet.net.au

```

The first command (`ip link`) is where I just check devices are recognized by the linux kernel, on this device it's 

```

guiverc@d960-ubu2:/de2900/xubuntu_64$  ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 00:26:b9:78:23:96 brd ff:ff:ff:ff:ff:ff

```

which looks normal (device enp0s25) & what I expect "state UP"

Next command (`ip addr`) checks to see an IP address is valid; I see addresses here as I'd exect.

Next is `ip route` to check I'm routed somewhere useful (DHCP will route unknown MAC addresses to a *sink* & not correctly); I recognize I'm going to 192.168.15.16 which is correct

```

guiverc@d960-ubu2:/de2900/xubuntu_64$   ip route
default via 192.168.15.16 dev enp0s25 proto static metric 100 
169.254.0.0/16 dev enp0s25 scope link metric 1000 
192.168.15.0/24 dev enp0s25 proto kernel scope link src 192.168.15.138 metric 100 
192.168.15.0/24 dev enp0s25 proto kernel scope link src 192.168.15.139 metric 100 

```

Next I send an echo request (ping) to the router with `ping` & I get my two replies as expected.

I'm now ready to go external of this address.

My first external ping (echo request) is to 8.8.8.8 which is google; I use that purely as it's easy to remember, and I get replies.  I needn't use the count of 2; just habit I think; I could give no value & and just quit it with ^C (Ctrl+C).  This confirms the internet is working correctly & I can send traffic everywhere.

My final ping is to my ISP, but it could be any external address, ie. `ping -c 2 iinet.net.au` for me.   This echo request (ping) checks the DNS is working, ie. what converts human web addresses to the numbers the internet uses. I get replies here, so I believe any traffic should be good for me (ie. browser should work).   If certain programs aren't working, this has confirmed the box is connected to the internet & so I can rule out network issues; and I've hopefully got more information.

Can you ping external (8.8.8.8)? which confirms your network & internet are good?  As we humans don't remember numbers so well the final ping confirms DNS is working (ie. conversion of human-names to ip-addresses occurs).


FYI:  Why do I use terminal?   It's quick & easy; hit Ctrl+Alt+T & Qterminal opens for me. (I didn't even need that; I leave a qterminal open anyway) and terminal commands provide instant & valuable feedback without the need to look for it in logs.

Sorry I don't know what 'valido' is so I ignored that.

---

### Post by espectro2 on 2021-12-31
I think my explanation was a bit confusing in short ping happens normally via network cable via wifi when i connect it stays connected for a second and shows **Lost Connection nm tray**** **but in connection information there is a normal ISP IP address as if i was connected

---

### Post by guiverc on 2021-12-31
If you're having issues with connections dying.. and needing to NetworkManager to be reset to get it working again (*even if only temporary*), these thoughts come to mind.

- did you *release-upgrade* or *fresh* install Lubuntu 20.04 LTS.  I've seen what you describe occur on a system that was upgraded from an earlier Lubuntu 18.04 LTS (the upgrade path from 18.04/LXDE to later/LXQt is *unsupported* due to problems with the change of desktop)

- which kernel stack are you using?

Ubuntu LTS releases have two kernel stack choices, with Lubuntu 20.04 LTS the stack chosen is controlled by the ISO used for install; with 20.04 & 20.04.1 media defaulting to the GA or *stable* kernel choice, and 20.04.2 & later media defaulting to HWE or *hardware enablement* stack which is better for newer gpu/video cards primarily.  Which are you using?

The quickest way to find out is with `uname -r` which will show your current running linux kernel detail; with 20.04 it'll be 5.4 if using the GA stack (any upgrade level), but with HWE it's 5.8 at 20.04.2, 5.11 at 20.04.3, 5.13 at 20.04.4....

If you're not using any closed-source proprietary drivers, I'd very likely install the other stack as you can have both installed and select which you use at boot (ie. `grub`) allowing you to try the other out.  I'd have both installed; as the only consequence of this is a larger disk footprint (ie. *both will be installed but it's not that big*) and more bandwidth used in upgrades (*both will be upgraded*).  If you decide one is better than the other, you can remove the unwanted stack.

See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Note: As I don't know which stack you're using, I've not provided specific advice. The document was modified to match Ubuntu Desktop (which defaults to HWE for all 20.04 releases; Lubuntu 20.04 LTS acts more like the 18.04 Ubuntu Desktop as I described above)

If you don't want to install anything (*fair enough, esp. if you're using 3rd party video drivers as they may prevent both stacks co-existing easily*) I'd suggest exploring this via *live* media.. ie. you can write
- Lubuntu 20.04/20.04.1 media to thumb-drive to test 5.4 kernel (*it won't be updated as live media doesn't allow easy reboots*)
- *Lubuntu 20.04.2 media will allow testing a different stack; 5.8 kernel, but I'd use only for comparison purposes and likely skip this anyway*
- Lubuntu 20.04.3 media will allow testing the 5.11 kernel  

The benefit of exploring with *live* media is that it'll be without any configuration changes you've made, or where made during install (*Lubuntu's installs don't allow for many config changes anyway so this isn't very likely but wifi passwords can be set*) and if it occurs there, it's not a change you made and related to the Ubuntu stack itself; and may show one stack (GA or HWE) is better for your hardware than the other.

On older hardware I often find the GA stack is better, but esp. if using newer video/GPU hardware the HWE/newer stack maybe required.

(*Lubuntu 20.04.4 media doesn't yet include the 5.13 kernel from a quick script I ran at terminal if I read the results correctly.. it didn't last QA-test I performed with it a few days ago though either; it's due for release till [24 February]("https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule")*)

---

### Post by espectro2 on 2021-12-31
uname -r
5.11.0-43-generic

5.11.0-43-generic #47~20.04.2-Ubuntu

---

### Post by chili555 on 2022-01-01
Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get

```
If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

   ```
 sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    sudo nano /etc/default/crda

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.    

Is there any improvement?

---

