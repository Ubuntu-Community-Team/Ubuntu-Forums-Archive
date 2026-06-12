---
title: "Breezy Badger (5.10) pre-compiled sl-modem binaries?"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by eliaz on 2005-10-25
A simple question: Does anyone has pre-compiled sl-modem binaries for Breezy (2.6.12-9-386) that supports Agere AC97 (SiS) softmodem on Acer Aspire-laptop directly?

I can't compile that because I do not have internet connection to get build-essentials, kernel-source, gcc-3.4.5-packages and so on that are described by scanModem utility...
 
My problem is just funny like thread "breezy badger - cannot compile Lucent modem drivers." 

Please, help me pass this complex compilation maneuver!

---

### Post by mlomker on 2005-10-25
I don't know if they work with your modem, but the sl-modem-daemon package is in breezy.  You can grab it at packages.ubuntu.com if you don't have apt-get access.

---

### Post by mplexus on 2005-10-25
I don't think you can use the Lucent drivers for soft modems anyway. I have an acer laptop as well, with agere soft modem, and i installed the sl-modem-daemon. It works with alsa drivers, module snd_via82xx_modem. The device is /dev/ttySL0..

---

### Post by eliaz on 2005-10-26
Thanks for mlomker and mplexus.

The tip for newbie Breezy Badger 5.10 users (kernel-2.6.12-9-386) to set up sl-modem (e.g. Agere AC97 SiS) easily:

1. If you do not have internet access to run apt-get you can download the package sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb by using another computer from the nearest mirror (e.g. [http://debian.charite.de/ubuntu/pool/multiverse/s/sl-modem/](http://debian.charite.de/ubuntu/pool/multiverse/s/sl-modem/))

2. Package installation: dpkg -i sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb

3. Dialer configuration: sudo wvdialconf /etc/wvdial.conf

4. Edit your /etc/wvdial.conf (Dialer Defaults): Add your isp phone, username, password and "Carrier Check=No"

5. Start your internet access: sudo wvdial    

That's all.

---

### Post by xbaez on 2005-10-26
Hey guys with Hoary I was able to hear the sound of the modem while dialing (especially usefull in Ecuador since many times lines are busy and you like to hear what's going on while dialing)

I use kppp, but I suppose that if I use other programs it will be the same

How can I configure this to actually hear what's going on while dialing?

---

