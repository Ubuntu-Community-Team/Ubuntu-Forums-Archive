---
title: "Wifi highly unstable worked fine before updating to 16.04"
date: 2016-09-20
forum: Networking &amp; Wireless
---

### Post by tippingbison on 2016-09-20
Hello! I am running Lubuntu 16, and having wireless issues. I'm new to Lubuntu, and Im trying my best to troubleshoot why my wireless isn't working. I could really use some help.

My wireless connection was fine before I updated from 14, but ever since, the wifi works fine for a few minutes after a boot, and then disconnects. I know my wireless card is the ralink rt2561, and I thought I might not have the correct driver, so I attempted to install firmware-ralink both from the terminal, and from debian.org. When I tried the terminal I got an error saying that Lubuntu couldn't find frimware-ralink. So, I tried to install the package from debian manually, but the installation failed, but didn't give me an error log.

I had this same wireless issue on my installation of Linux Mint, and I was never able to fix it. 

Thank you very much.

---

### Post by jeremy31 on 2016-09-20
Welcome to the forum.  Please post the results from terminal for ```
lspci -nnk | grep -iA2 net; iwconfig
```

---

### Post by tippingbison on 2016-09-20
I don't have an easy way to connect to the internet from my PC, so I hope it's okay to post the outputs through imgur. Here's the output: [http://i.imgur.com/ZD5uftD.jpg](http://i.imgur.com/ZD5uftD.jpg)

---

### Post by jeremy31 on 2016-09-21
I think my answer @ [http://askubuntu.com/a/818415/300665](http://askubuntu.com/a/818415/300665) may help as your power management is enabled for the wifi

---

