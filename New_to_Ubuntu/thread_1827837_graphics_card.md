---
title: "graphics card"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by inxs1111 on 2011-08-18
my nvidia gt 430card does not work on ubuntu 10.04,the screen wont go to full hd resolution.ive got normal resolution and black line about quarter of screen all around desk top,but it works perfectly on 11.04,reason im asking is i want to run ultimate ubuntu 2.9 which im having same problem:(

---

### Post by 23dornot23d on 2011-08-18
Compare the logs between both versions

Go to Administration >>> Log Viewer

look for Xorg.0.log

It may give you a clue as to what is happening .....

Its possible the driver is not loading  go in the menu to

Preferences >>> Additional Drivers

---

### Post by seawolf167 on 2011-08-18
Do you have the latest drivers for your video card? Either through "Hardware Drivers" (or in 11.04 "Additional Drivers").

Additionally, you can manually install the full driver suite available from Nvidia [here]("http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html").

---

### Post by 3rdalbum on 2011-08-18
> **inxs1111 said:**
> my nvidia gt 430card does not work on ubuntu 10.04,the screen wont go to full hd resolution.ive got normal resolution and black line about quarter of screen all around desk top,but it works perfectly on 11.04

That would be because Ubuntu 10.04 predates the release of that card. Ubuntu 11.04 came afterwards.

You could try installing the latest version of the Nvidia driver from the Nvidia website, but that's a bit of a pain to keep rebuilding the driver every time there's a kernel update.

You realise that Ubuntu Ultimate Edition is just regular Ubuntu but with some extra packages installed, and you can get those packages installed on normal Ubuntu?

In other words, why not just use Ubuntu 11.04? It works with your card, and you haven't explained why you specifically want an older version of Ubuntu on newer hardware.

---

### Post by beew on 2011-08-18
You may try adding the x-swat ppa to your sources list and then update the Nvidia packages. It has the latest driver (280.13).

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates?field.series_filter=lucid")

Do not install the driver from Nvidia's site. You are likely to get into problems and everytime when you have a kernel update you will have to reinstall.

---

