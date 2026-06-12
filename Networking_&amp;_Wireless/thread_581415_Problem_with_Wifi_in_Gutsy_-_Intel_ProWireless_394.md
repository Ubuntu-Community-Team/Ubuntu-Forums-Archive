---
title: "Problem with Wifi in Gutsy - Intel Pro/Wireless 3945ABG"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by psainsbury on 2007-10-19
HI,

Since upgrading to gutsy my Acer TravelMate 4220 has problems connecting to my wifi router.  Oddly enough if I plug in a network cable, then all of a sudden Network Manager can connect perfectly, so my current workaround is to carry my laptop to the wifi router every time I reboot so that I can plug it in and get the wireless network working.  (This is VERY much not ideal)

I've read a bunch of forum posts and have not found anything that works.  Eventually I found a link to [https://answers.launchpad.net/ubuntu/+source/linux-source-2.6.22/+question/13022](https://answers.launchpad.net/ubuntu/+source/linux-source-2.6.22/+question/13022) which seemed to give good instructions on how to change from the ipw3945 to iwl3945 drivers.

So I went ahead and tried that out but got shown the following error:
> 
root@paul-laptop:~# modprobe iwl3945
FATAL: Error inserting iwl3945 (/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I checked out dmesg and the contents are in the attached file.  Does anyone have any suggestions as to how I can try to get iwl3945 working?  Or any other suggestions on how to get my wifi working again?

From
  Paul

---

### Post by cyran on 2007-10-22
I have the exact same problem. dmesg indicates a great deal of symbols are unknown, but I can definitely find the same symbols it complains about in "modules.symbols", all as aliases for the new iwlwifi_mac80211. It's strange.

---

### Post by sreid on 2007-11-04
Same problem here, and I found this thread while googling for more info. Thanks to cyran's post I took a closer look at modules.symbols, which I don't know much about, but was able to infer that the "iwlwifi_mac80211" might need to be just "mac80211" instead. So I did this:

```

cd /lib/modules/2.6.22-14-generic
sudo perl -pi -e 's/ iwlwifi_mac80211$/ mac80211/' modules.symbols

```

Rebooted, and now I can load the module, and it detects my card. I don't really know, but the modules.symbols file looks like something that is auto-generated, so it's strange that it would be wrong like that...?

Trying to connect fails though, dmesg says authentication with AP times out (my AP requires WEP), so I'm back to ipw3945 until I can tinker some more.

Update: I'm now connected. Not sure why it didn't work the first time, but the second attempt worked fine.

Update2: **Now I'm getting unresolved symbols again.** It _did_ work for a while. Very strange. :(

---

### Post by cyran on 2007-11-17
Okay, this is actually *working* for me now based on the bug comment [here]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144501/comments/17").

> 
sudo modprobe -r ipw3945
sudo modprobe -r ieee80211
sudo modprobe -r ieee80211_crypt
sudo modprobe -r mac80211
sudo modprobe iwlwifi_mac80211
sudo modprobe iwl3945
sudo depmod

If all these symbols have been in iwlwifi_mac80211 the entire time, then why did the plain 'mac80211' command work for others? Eh. Now I just need to figure out how to avoid having to do this every time I reboot.

ETA: It looks like [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/158045") will eliminate this problem in Hardy, at least.

---

