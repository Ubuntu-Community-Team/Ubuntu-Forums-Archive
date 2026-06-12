---
title: "How to connection my wifi network onto my laptop?"
date: 2017-12-06
forum: Networking &amp; Wireless
---

### Post by 88les on 2017-12-06
Hello guys,

Greetings to all. I am newbie here. I would like to use my phone onto my computer using a wifi or hotspot. HOw can I do that?

Please let me know. Thank you!

---

### Post by gordintoronto on 2017-12-07
I don't know what you mean by "use my phone onto my computer".

If you want to access pictures on your phone from your laptop, just plug it in using a USB cable.

What phone? What version of Linux?

---

### Post by litlesam on 2017-12-07
If your wanting to create a Hotspot on a Ubuntu system then this may help you.

For any other info, you will need to provide more details.

sudo apt-get install hostapd git build-essential
git clone [https://github.com/oblique/create_ap.git](https://github.com/oblique/create_ap.git)
cd create_ap
sudo make install

sudo create_ap wlp20s0 enp14s0 MyAccessPoint MyPassPhrase

sudo create_ap --stop wlp20s0

The above two lines are what I used in Hotels while traveling.

Examples:
  create_ap wlan0 eth0 MyAccessPoint MyPassPhrase
  echo -e 'MyAccessPoint\nMyPassPhrase' | create_ap wlan0 eth0
  create_ap wlan0 eth0 MyAccessPoint
  echo 'MyAccessPoint' | create_ap wlan0 eth0
  create_ap wlan0 wlan0 MyAccessPoint MyPassPhrase
  create_ap -n wlan0 MyAccessPoint MyPassPhrase
  create_ap -m bridge wlan0 eth0 MyAccessPoint MyPassPhrase
  create_ap -m bridge wlan0 br0 MyAccessPoint MyPassPhrase
  create_ap --driver rtl871xdrv wlan0 eth0 MyAccessPoint MyPassPhrase
  create_ap --daemon wlan0 eth0 MyAccessPoint MyPassPhrase
  create_ap --stop wlan0

---

### Post by 88les on 2017-12-08
I mean phone wifi network using a cable or hotspot.

---

### Post by litlesam on 2017-12-08
> **88les said:**
> I mean phone wifi network using a cable or hotspot.

I have Ubuntu on my laptop and setup as a hotspot in hotels and so on, then use that hotspot for all my hand held devices.

---

