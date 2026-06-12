---
title: "how to  play MP3 - DIVX ...."
date: 2010-01-02
forum: New to Ubuntu
---

### Post by 0863588 on 2010-01-02
**[SIZE=4]hi .. [/SIZE]**
**[SIZE=4]How can I play MP3-Divx-DVDs-Quicktime-view Flash-Java web pages ???[/SIZE]**

---

### Post by LegendarySandwich on 2010-01-02
Applications > Ubuntu Software Center > Ubuntu-restricted-extras

---

### Post by sandyd on 2010-01-02
run this in the terminal
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update[FONT=monospace]
[/FONT]sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

```Then click [[here]]("apt://libdvdcss2,libdvdread4,ubuntu-restricted-extras,flashplugin-nonfree,libfaac0,libfaad0,libavcodec-extra-52,libavdevice-extra-52,libavformat-extra-52,gstreamer0.10-plugins-ugly,gstreamer0.10-plugins-ugly-multiverse") for dvd support + some codecs including mp3 + flash (use TAB key to accept the Sun Java Licence)
Then, click your Operating System Archetecture below
[[x86]]("apt://w32codecs")
[[x64]]("apt://w64codecs")

---

### Post by 0863588 on 2010-01-08
> **carlee said:**
> run this in the terminal
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

```Then click [[here]]("apt://libdvdcss2,libdvdread4,ubuntu-restricted-extras,flashplugin-nonfree,libfaac0,libfaad0,libavcodec-extra-52,libavdevice-extra-52,libavformat-extra-52,gstreamer0.10-plugins-ugly,gstreamer0.10-plugins-ugly-multiverse") for dvd support + some codecs including mp3 + flash (use TAB key to accept the Sun Java Licence)
Then, click your Operating System Archetecture below
[[x86]]("apt://w32codecs")
[[x64]]("apt://w64codecs")
 [SIZE=3][COLOR=black]Thank you for new information .[/COLOR][/SIZE]

---

