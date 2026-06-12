---
title: "Broadcom BCM4321"
date: 2015-03-16
forum: Networking &amp; Wireless
---

### Post by nick.hughes on 2015-03-16
Recently I got an old computer, today I got around to installing Edubuntu on it like I had planned. The problem is that I don't know how to set up my wi-fi. 

Sorry if this seems like an easy question, I've never used Ubuntu or Linux before. :(

---

### Post by Bucky Ball on 2015-03-16
Welcome. Please open a terminal and issue this command:

```
sudo lshw -C network
```

You can copy/paste it in, safest. Post the output back here.

Which release of Ubuntu/Edubuntu are you using?

---

### Post by nick.hughes on 2015-03-16
After typing that in I got this: [ATTACH]260675[/ATTACH]

I'm running 14.04

---

### Post by Bucky Ball on 2015-03-17
Try, in a terminal:

```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```

... then:
```

sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
sudo modprobe wl
```

From [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"). Do you now have wireless? You could look in 'Additional Drivers' prior to doing any of this and see if you have the STA driver offered for wireless.

A heads up: Please post output from the terminal on the forum between [code] tags (see the last link in my signature for how) rather than a link to a file. Most users are reluctant to download random files and it is much more convenient posting it, in full, here, between code tags. Thanks.

---

### Post by nick.hughes on 2015-03-17
Thank you so much, that worked. :p

I'll be sure to use code tags if I ever have problems in the future.

---

### Post by Bucky Ball on 2015-03-17
Great news and thanks for marking the thread as solved. ;)

Which worked? The code or looking in Additional Drivers? (for the benefit of others)

Any further issues just ask in a new thread. Until then, enjoy the OS, the forums and the learning curve.

---

