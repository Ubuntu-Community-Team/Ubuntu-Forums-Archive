---
title: "Ubuntu 20.04 no ethernet, wifi, or audio after update"
date: 2021-01-07
forum: Networking &amp; Wireless
---

### Post by daninca on 2021-01-07
I just applied updates and now no kernel (5.8 or 5.4 in regular or rescue mode) comes up with networking.

I last updated 19 days ago.

It can see ethernet, wifi, and audio if I boot to the 20.04 USB install drive; so the hardware didn't just go bad.

Nvidia drivers are installed and it looked like a bunch of that got updated.  Removing all the nvidia packages didn't help (and now I only have text console).

dmesg doesn't show any errors or failure.
grepping for error|fail in /var/log/syslog does show some stuff, but it might be normal.  I'll upload the photo separately.

lspci does show the ethernet (Intel) and wifi (Intel) adapters.  No nonfree driver packages are install.

Opening network manager shows nothing.
The audio status icon shows no audio.
"ip link" just shows the loopback interface

---

### Post by dougbennett on 2021-01-07
Ubuntu 20.04.1 LTS, I updated yesterday and my desktop freezes after log in. I posted a youtube video how I got around this and my attempts to solve. [https://www.youtube.com/watch?v=smfKCRoaDK0](https://www.youtube.com/watch?v=smfKCRoaDK0) I have not heard anything from Ubuntu yet.

---

### Post by daninca on 2021-01-07
The one with the white text is a boot from the kubuntu 20.04 USB.  Notice that the network and audio icons are fine.
[IMG]https://photos.google.com/share/AF1QipPQMJh8Xwtc3gGbV0ZbPMJ0igaTJlAWzXqke6hBAimJd830vzlXJZLJ-GiEuHkudQ/photo/AF1QipOc3K6FLY_wAO3jonCQ5ArVOVa2j1Qfdi20wXLP?key=WElfYnBsVE1PM1p5aFNjR093bmNjYWQ2V29KcjdR[/IMG]

The ones with the greed text are booting from the failed upgrade.  The last one shows some errors/failures in syslog that might be relevant.
[IMG]https://photos.google.com/share/AF1QipPQMJh8Xwtc3gGbV0ZbPMJ0igaTJlAWzXqke6hBAimJd830vzlXJZLJ-GiEuHkudQ/photo/AF1QipO2QJZN1-b_sC8OdEvNmjtp2smWC532VuMqxi4d?key=WElfYnBsVE1PM1p5aFNjR093bmNjYWQ2V29KcjdR[/IMG]

If the above images don't work, look in this folder:
[https://photos.app.goo.gl/FiLNBjWKBnHRNmnn9]("https://photos.app.goo.gl/FiLNBjWKBnHRNmnn9")

---

### Post by daninca on 2021-01-07
@doughbennett is right that booting to 5.4.0-59 works.
I thought that I had tried all the older kernels, but I hadn't.

It appears that 5.8.0 has problems, so I purged the package

---

