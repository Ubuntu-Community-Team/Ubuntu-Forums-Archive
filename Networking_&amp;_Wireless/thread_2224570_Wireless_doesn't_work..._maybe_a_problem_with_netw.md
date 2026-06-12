---
title: "Wireless doesn't work... maybe a problem with network-manager?"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by Number703 on 2014-05-16
Currently running Ubuntu 14.04, but this problem has persisted through different versions as well as in Mint. I'm using an HP 2000 Notebook PC 2000-2c20DX, wireless card is Ralink RT5390R 802.11bgn Wi-Fi Adapter. Ethernet works fine but I have limited wireless abilities, in Windows I get around 40Mbps, in Ubuntu now I get ~5 if I'm lucky, often it slows to less than 1Mbps, so basically useless. This problem has come and gone, wireless seemed to work a little better in Mint but right now Mint has other problems, and wifi isn't working great there anyway. In the past I had issues with it cutting out completely and "sudo service network-manager restart" would fix it temporarily (though it would still be slow). Sometimes, upgrading to a new version would fix it for a few weeks. Now, it's not cutting out but it's still incredibly slow, and service network-manager restart doesn't help. 

So what's the problem? Is this a driver problem? If it were a driver issue I don't know why it would come and go like that though, and why some weeks it's worked pretty well. At any rate, I'm not really sure how to go about installing proprietary drivers, I tried looking into it but it seems a bit more complicated than anything else I've done with linux. Since service network-manager restart has helped some in the past, maybe it's just something with network-manager? It reminds me of when I had sound issues and "killall pulseaudio" was a temporary fix, and then eventually removing pulseaudio solved it permanently. Would removing network-manager help? Is there a good alternative?

I tried getting an external wireless adapter, Belkin F7D2102 N300 Micro Wireless N USB Adapter, apparently it uses a Realtek RTL8192CU chipset. However, it hasn't been any better (it works fine on Windows). So, either I need drivers for that too, or it is something with network-manager.

Thanks for any help you could give on this.

---

### Post by varunendra on 2014-05-17
For the realtek USB adapter, try what is suggested in this post : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)

For the internal Ralink card, please follow the instructions in this post to give us a detailed diagnostics report : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by Number703 on 2014-05-17
I'll take a look at the realtek stuff when I have more time, but for now here's the output for the Ralink card: [http://textuploader.com/95d2](http://textuploader.com/95d2)

---

### Post by varunendra on 2014-05-18
Please change the encryption type in your router/access-point to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode with TKIP, which is meant only for backwards compatibility and should be avoided as long as possible. Reboot the router after saving changes.

Apart from the above change in the router, try this in Ubuntu (reboot > try the following commands > try connectivity without rebooting again) -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
This would be a temporary change that would be lost on next boot. It is likely to help and works best with the AES encryption as suggested above. If it seems to help, we can make it permanent.

Do not insert the USB adapter while trying this, since its respective driver may conflict over resources.

---

### Post by Number703 on 2014-05-28
Sorry I didn't respond, I've been really busy lately. I never even thought about it being a problem with my router. I know when I was having problems the other times before this it was happening with all wifi spots, but I just moved to a different place for the summer and it seems to be working well enough so maybe this time it is just a router problem. When I move back to my apartment after the summer I'll look at changing the settings on my router, thanks.

---

