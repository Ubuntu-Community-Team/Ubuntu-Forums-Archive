---
title: "wireless and bridge-utils"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by ThUnD3rM0rPh on 2006-09-13
Hi i have an old computer i wanted to use to make a simple wireless bridge. Just to check i thought i would try ubuntu server for the task.

Well everything went smoothly, it found my Ralink Ra2500 based wireless pci nic and built-in ethernet with out any problems. So I got bridge-utils from the repos and read the howto document that came with the package. I made the bridge with three simple commands or so. Up to this point everything seems to  be in order. I configured the ralink card with ```
sudo iwconfig ra0 essid test channel 7 mode ad-hoc
```

Now I tried to connect too the ad-hoc network from my ubuntu laptop, No go.
So I figured I'd try to sse what happend if I booted winxp on my laptop. well something strange happend. Now I can find the ad-hoc network and I can connect, I even get an IP from my router/modem however I can't connect to the internet. So I try to ping some sites around the world. No go. I tried to ping the router/modem, no go. I can't even ping the server with the wireless bridge and it's supposed to be connected to it. pinging the rest of the world works from ther server btw

can anyone enlighten me?

---

