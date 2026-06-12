---
title: "downloading from APT is unbearably slow..."
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by MONODA on 2008-03-19
I am pretty sure that this is not a bug or APT's fault, but recently I have realized that whenever I install an application and APT needs to download files, the download is very slow! The speed can go down to about 50 Bytes/second and a high of 10 kbps. This is very unusually considering that I have a 256 kpbs connection and usually download at 40 kbps. Could this be a problem with my ISP? could they be blocking the ports for APT? Is there an solution or should I try to contact my ISP?

---

### Post by spd106 on 2008-03-21
Apt uses the http protocol for downloading packages, so unless they've blocked all web traffic I don't think that is your problem.

The most likely cause of slow updates is the local mirror that you are using. By default apt will be set-up to use the nearest mirror based on your time zone/country selection during install. You should try using a different mirror or switch to the official repository in the System -> Administration -> Software Sources utility or Synaptic.

Useful link: [http://www.ubuntu.com/getubuntu/mirror](http://www.ubuntu.com/getubuntu/mirror)

---

### Post by MONODA on 2008-03-21
i have chosen, select best server several times and each time i get a different one and the problem remains.

---

### Post by MONODA on 2008-03-22
it is just as slow in Debain.

---

