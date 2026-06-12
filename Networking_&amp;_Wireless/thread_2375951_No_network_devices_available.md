---
title: "No network devices available"
date: 2017-10-29
forum: Networking &amp; Wireless
---

### Post by tpearce on 2017-10-29
I use a wired connection only in 16.04 and have no wireless card, but after a reboot today it says I have no connections available. Tethering via USB or Bluetooth works fine.

I've made sure everything is updated, reinstalling the kernel and loading previous kernel versions as per other solutions to the problem, but the problem persists. 

Here's the wireless-info.txt: [http://paste.ubuntu.com/25842309/](http://paste.ubuntu.com/25842309/)

---

### Post by tpearce on 2017-10-29
I've fixed the problem. Running 

```
sudo modprobe r8169
```

allowed the ethernet adapter to start, so the r8169 driver was not loading automatically. It seems the problem was coming from the r8168-dkms driver blacklisting r8169, removing it allowed the r8169 to load properly.

However now when I start Ubuntu I get an error message about r8168-dkms failing to install properly. I've run

```
 sudo apt-mark hold r8168-dkms
``` to prevent it for me trying, but if there is a more elegant solution feel free to let me know.

---

