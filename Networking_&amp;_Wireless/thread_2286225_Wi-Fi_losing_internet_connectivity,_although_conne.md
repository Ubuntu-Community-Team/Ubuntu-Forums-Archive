---
title: "Wi-Fi losing internet connectivity, although connection still detected."
date: 2015-07-10
forum: Networking &amp; Wireless
---

### Post by Ben_Evans on 2015-07-10
Hi all,

I just got my Wi-Fi internet connection up & running earlier today using [this thread ]("http://ubuntuforums.org/showthread.php?t=1964173&page=2")on Ubuntu 14.04 LTS (64bit). Unfortunately, even though my connection appears to be up & running, I seem to have  difficulties staying connected to the internet. Shortly after beginning downloads or high volume browsing, my connection appears to lose connection to the internet. However, in the connection window I still appear to have bars to the connection, although I am no longer able to access the router settings, nor the internet (via web browsers, or the terminal). The only way to  restore the connection is by restarting my computer, as disconnecting  & reconnecting via the Network Manager seems to have no effect. 

If it helps I ran the wirless info script, the results are [here]("http://paste.ubuntu.com/11857879/").
My Wi-Fi USB stick is a Netgear wnda3100.

None of my other devices, or flatmates seem to have this issue, and I can't see in the router settings any  reason why my computer would be treated differently!

Any help would be greatly appreciated.

---

### Post by Vladlenin5000 on 2015-07-10
Hi and welcome.

Using Windows drivers via *ndiswrapper* always has its pitfalls and you may have stumbled in one.
I won't be of much help with that hardware and I doubt anyone can... 

I strongly recommend you use an already supported device, as cheap has $10 or even less. You're the one to decide how valuable is your time.

---

### Post by chili555 on 2015-07-11
There are some things you might try. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Finally, does this sound familiar? [http://ubuntuforums.org/showthread.php?t=2264020](http://ubuntuforums.org/showthread.php?t=2264020) It is a similar device that also depends on ndiswrapper.

---

### Post by Ben_Evans on 2015-07-11
Thanks for the response all. I've done what you suggested Chilli, and have changed the setting from WPA/WPA2 to just WPA2 and it at least appears to have done the trick for now... 

Also reading that thread you posted towards the end does seem eerily familiar. But I'll take hourly drops, over the current drops I have right now (i.e. whenever I begin any form of high bitrate download).

I'll post back in a day or when the connection drops (whichever comes first), as that's my benchmark for whether it's just going to be a painful driver issue, or whether it has in fact been resolved. Either way, I appreciate all the help!

---

### Post by Ben_Evans on 2015-07-14
So just an update. My connection seems to be a lot stronger since switching over to WPA2 only on my router, even allowing me to download at reasonable speeds for 20-30 minutes at a time. However, I still experience disconnects when I download a lot, and some activities such as playing Minecraft online will almost instantly disconnect me. Bizarrely, playing DotA 2 doesn't do the same, so I guess the bit rate for that must be drastically lower.

In summary, it's not perfect, but it's working - and in my current predicament, job hunting, working is enough.

Thanks for the help all.

---

