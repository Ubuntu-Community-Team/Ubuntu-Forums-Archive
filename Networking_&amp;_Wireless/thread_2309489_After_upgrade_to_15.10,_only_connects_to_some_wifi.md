---
title: "After upgrade to 15.10, only connects to some wifi networks"
date: 2016-01-11
forum: Networking &amp; Wireless
---

### Post by TeaFiend on 2016-01-11
[COLOR=#111111][FONT=Ubuntu]So I upgraded my Dell m3800 to Kubuntu 15.10, after which I'm only able to connect to my home wifi network. Every other network I try using doesn't work, including many that worked prior to upgrading. Points of potential interest:[/FONT][/COLOR]

[LIST]
[*]In this instance "doesn't work" means: it connects to the other networks, but it looks like no data is ever received (the network-manager icon says X KiB/s sent/received, and the sent will frequently show non-zero values but received seems never to show a non-zero value).
[*]I've tried the proposed solutions at [Wifi losing connection, weak signal, Intel 7260 adapter]("http://askubuntu.com/questions/660155/wifi-losing-connection-weak-signal-intel-7260-adapter")(various iwlwifi module options) and [http://ubuntuforums.org/showthread.php?t=2300362](http://ubuntuforums.org/showthread.php?t=2300362)(latest iwlwifi microcode).
[*]I've tried purging and reinstalling the network-manager package.
[*]I've tried connecting an external USB wifi adapter (with a Broadcom chip, not Intel like the internal wifi chip) and *got exactly the same result*. This is when I realised something very strange is going on.
[*]I've googled around and found various other "wifi not working after upgrade issues" but they all seemed specific to Broadcom chips.
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Here's the output of the wireless-info script when connected to a wifi network that my laptop used to work with but now doesn't: [https://www.dropbox.com/s/sz858edudvpzgjj/wireless-info.txt?dl=0](https://www.dropbox.com/s/sz858edudvpzgjj/wireless-info.txt?dl=0)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]And for comparison here's the output of the script when connected to (the one and only) wifi network that my laptop still works with: [https://www.dropbox.com/s/s8jfxut810c1r2d/wireless-info.working.txt?dl=0](https://www.dropbox.com/s/s8jfxut810c1r2d/wireless-info.working.txt?dl=0)

[/FONT][/COLOR]

---

### Post by TeaFiend on 2016-01-13
Inadvertently figured it out. After several months. Gah. The problem lay with the name resolution configuration (DNS settings). The settings I had worked with my home wifi but were incompatible with every other wifi network I tried. I only found out because I noticed that a service accessing a personal server of mine was working when my laptop was connected to some other wifi network, and the IP address for that server is set in /etc/hosts so no name resolution was required for it. After some digging around it turns out I needed to change the IP address for the name resolution service used by network-manager, defined in /etc/resolv.conf, from 192.168.1.1 to 127.0.1.1 (and then "sudo service network-manager restart").

---

