---
title: "[SOLVED] wireless breaks down whenever wpasupplicant drops connection"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by alphacrux on 2008-03-26
Ok, so my problem is that my wireless device goes down whenever wpa_supplicant loses a connection. Basically I can always tell because my system slows down considerably for quite a bit of time (usually about 10 minutes) and when I can finally access a terminal iwconfig shows my device but without my connection settings. If I try to run any commands with wlan0 (such as setting an essid for my card or scanning for networks) they dont work, and after issuing a failed command and looking back at iwconfig the wlan0 device is no longer showing at all! If I try to issue an ifup anytime after the connection is dropped it says that it cant find the wlan0 device. When I type lsmod it shows that hostap is still loaded and in fact will not let me unload it because it is being used. Basically I have to reboot to get my wireless working again. I never seem to lose my connection at home, but if the signal is weak or if there's alot of interference in the area then I usually get about 10-20 minutes before the signal drops and I have to reboot my computer.

Here's some information about my wireless experience: Network Manager will handle wireless connections fine as long as they're not encrypted and /etc/network/interfaces has'nt been configured. Configuring /etc/network/interfaces or using iwconfig commands will connect to encrypted wireless (WEP at least). But to setup a configuration to connect to different types of encrypted wireless and to connect to my university's PEAP connection PERIOD required using wpa_supplicant. Now to get it to connect automatically to whatever wireless connection is in the area upon startup required writing a startup script calls wpa_supplicant and then dhclient. I tried using wpa-roam or pre-up and post-down commands in /etc/network/interfaces, but neither ever worked correctly.

Here is some info about my system: I am running a fresh install of gutsy 7.10 on a thinkpad a31 laptop. I have a prism 2.5 wavelan card which uses the hostap driver to run. I have tried ndiswrapper extensively and have not been able to get it to work with my card. I already have the orinoco and hermes drivers blacklisted which don't seem to work anyways. The logical name for my wireless is wlan0 which seems to be routed through wifi0, effectively wlan0 is what i use in config files and whatnot.

I would appreciate it if anyone could help me out with this, or just let me know if they are having the same problem. I believe the problem lies either with the hostap driver or with wpasupplicant itself. Some other information that might be helpful is that when I call wpa_supplicant I have to use the -Dhostap parameter in order to connect to my university. -Dwext doesn't seem to work. Also the firmware on my prism 2.5 card is pretty old. I've been looking at upgrading it as the current firmware does not support WPA. I haven't updated it yet cause I don't want to screw up my system and because I don't have any WPA networks to connect to. Although now its the only thing that I can think of that might actually fix the problem.

At the very least I would like to bring my wireless device back up so I can connect again without having to reboot each time. [COLOR="Red"]**So if anyone has some commands to bring disabled cards back up or to help debug the problem I would certainly appreciate them**[/COLOR]. I have spent so much time getting this all to work properly it would be a shame if i come this far for it all to fail, Please Help :(

---

### Post by alphacrux on 2008-04-05
Ok so I messed around with my wireless connection a lot I finally got it figured out, and it didn't require any firmware upgrades :guitar:. I figured out two things: First how to bring my card back up. I found if I took the device down: "ifdown wlan0" and then removed my wireless drivers in a specific order (the drivers were hostap, hostap_pci, ieee80211, and ieee80211_wep, and ieee80211_wep_crypt though I can't remember the order) that I was then able to re-add the drivers back on and that would bring my card back up again, i.e. no problems listed in "lshw -C network". What I then found was that I still couldn't use iwconfig or iwlist however. Eventually I figured out that I needed to kill wpa_supplicant: "killall -q wpa_supplicant" before I could scan or reconnect again. Once I figured this out I could reconnect without causing my card to be brought down in the first place. Then i just had to reissue wpa_supplicant and dhclient and I was back in business. It still freezes for like 10 min when it happens but whatever I can deal with that.

---

### Post by sfgreenwood on 2008-04-15
That still seems a horrible hack to fix it. I have the same problem with a Dell XPS M1330 running gutsy. I connect to an Airline 101G AP which is WEP encrypted, and which works most of the time. However the connection drops occasionally, mostly when the machine falls idle but sometimes when the signal drops on the AP. At this point wpa_supplicant tries to reconnect but fails, and only really responds to a reboot, or as you have found by removing all the drivers and putting them back. On the whole a reboot is less hassle. Trying to kill wpa_supplicant more often than not results in the whole system hanging and then shutting down requires physical intervention and more often than not needs fsck to recover. As you found, switching off roaming and specifying an AP probably works - an additional problem in this case is that on boot, wpa_supplicant chooses a more distant AP (a swisscom AP in the Holiday Inn next door - I suspect that there some reason for that at the protocol level), but as I regularly use the machine in two or three locations it would be nice to have roaming working. The wireless card is the Intel PRO/Wireless 3945 running through the restricted drivers manager.

---

### Post by alphacrux on 2008-04-17
sfgreenwood maybe I can help you out a little. First I know there is a priority variable for wpa_supplicant.conf where inside each network{} you set a numerical value to tell which connections to try in what order. ```
priority=1
``` Also there is a way to configure wpa_supplicant to connect to unsecured networks ```
network={
        ssid=""
        key_mgmt=NONE
        priority=7
}
``` However for some reason wpa_supplicant will not connect to ANY unsecured network for me, even when i give it the essid, but alot of other people use this configuration. You can then set up a pretty easy startup script to automatically connect to any of your networks on startup. The only problem with this configuration is that you have to kill wpa_supplicant, then restart it and dhclient to connect to another network without having to reboot. Considering our mutual problem, I would make sure to issue this kill wpa_supplicant command *before* walking out of range. To make things more automated you could easily make a launcher icon on your desktop, top, or bottom panel that points to the startup script bin file. This way you only have to click to connect to the new network. Again this is not an ideal hack as new networks will not be automatically detected but you work with you got right? You can use: ```
iwlist wlan0 scan
``` to manually see if your card detects any networks. Hopefully this helps out. To tell the truth man I'm totally burnt out on this whole wireless thing,  time to start thinking about buying new hardware. BTW other than the wireless card how's that laptop? I've been eyeballing it on [www.dell.com/open](www.dell.com/open), it looks really badass! How's the battery life? with or without video card?

---

