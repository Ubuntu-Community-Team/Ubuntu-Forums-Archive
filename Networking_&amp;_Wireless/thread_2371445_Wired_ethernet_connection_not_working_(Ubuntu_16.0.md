---
title: "Wired ethernet connection not working (Ubuntu 16.04)"
date: 2017-09-14
forum: Networking &amp; Wireless
---

### Post by thekevinscott on 2017-09-14
Hi all, Ubuntu noob here (though I've used Ubuntu occasionally with virtual machines on my mac).

I've just built my own PC, with a GIGABYTE GA-Z170X motherboard and an NVidia GPU (among other hardware I can provide). I'm having issues booting into GUI, which I think are related to missing NVidia drivers that I need to apt-get, so I'm currently booting into a terminal and trying to get the ethernet working but running into issues. I'm largely leaning on this [great thread for advice]("https://ubuntuforums.org/showthread.php?t=25557").

First off, I tried plugging in ethernet and pinging google. The modem and router are working correctly for other devices in the household, but I get "unknown host google.com" back.

After some more reading, my **/etc/network/interfaces** looked like:

```
auto lo
iface lo inet loopback

```

Somehow I figured out that the ethernet on my system was **enp0s31f6**.

So I added that to **/etc/network/interfaces**:

```
auto enp0s31f6
iface enp0s31f6 inet dhcp

```

Here's a photo of the file in action.
[ATTACH=CONFIG]276724[/ATTACH]

I also restarted the network-manager after every edit.

(Note: I wasn't sure whether to use dhcp or a static IP. I don't need a static IP but thought I might need to configure one to get things working, but that didn't help. I'm also not sure how to get the right values for each of the values, but if dhcp is adequate I'd like to stick with that.)

**ifconfig -a** produces the following:

[ATTACH=CONFIG]276725[/ATTACH]

So **enp0s31f6** shows up, with some IP address, but pinging still fails.

I tried **sudo dhclient enp0s31f6** (I'm not sure what this command does but another poster recommended it), and the command just hangs.

**route** and **netstate** produce the following:

[ATTACH=CONFIG]276727[/ATTACH]

At this point I'm not sure what else to try. I'm at work all day today but happy to post any more information this evening when I get back.

Thanks for your help everyone!


(Apologies for the phone pictures; if I should retype the commands out for legibility I'm happy to do so.)

---

### Post by slickymaster on 2017-09-14
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2017-09-14
What is the result of:```
sudo ifdown enp0s3f16 && sudo ifup -v enp0s3f16
```

---

### Post by thekevinscott on 2017-09-14
Here's a photo of the output:

[ATTACH=CONFIG]276729[/ATTACH]

Let me know if any other information would be helpful, or if there are additional resources I can read / google!

---

### Post by thekevinscott on 2017-09-15
From what I can surmise, addresses in the 169 range are self-assigned IPs. Is it possible that could be a software issue? I've tried moving the ethernet to different ports in the modem with the same result (and the modem itself is working fine with other devices) so at this point it seems like it's either an issue with the motherboard hardware, or some software configuration area I'm not familiar with. Is that correct?

---

### Post by chili555 on 2017-09-15
What is the hardware?```
lspci -nnk | grep 0200 -A3
```

---

### Post by thekevinscott on 2017-09-15
Here is the output:
[ATTACH=CONFIG]276737[/ATTACH]

This morning I bought a wireless USB dongle, and after some troubleshooting with **iwconfig**, I'm able to ping google:

[ATTACH=CONFIG]276736[/ATTACH]

However, this being a desktop PC I'd much prefer to keep it hardwired via ethernet for speed, so I'm still very curious to learn how to debug this.

---

### Post by thekevinscott on 2017-09-16
Been googling around on this issue some more, and I just gotta say - @chili555, you're everywhere! I see your name all over the place whenever anyone's having network issues. Props to you for helping noobs enter the community.

---

### Post by alex04072000 on 2018-07-08
I am facing the same issue, did you figured out how to solve it?

---

