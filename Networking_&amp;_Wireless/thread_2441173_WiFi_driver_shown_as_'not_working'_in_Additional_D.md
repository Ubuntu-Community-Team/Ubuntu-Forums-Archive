---
title: "WiFi driver shown as 'not working' in Additional Drivers despite working fine"
date: 2020-04-20
forum: Networking &amp; Wireless
---

### Post by djdelarosa25 on 2020-04-20
Hi there! I'm new to the Linux community after using my free time this quarantine going distro hopping for the past couple of weeks. I decided on Ubuntu as it seems really polished and beginner-friendly. After dual-booting it with Windows 10 and finishing my setup, I noticed this while updating my drivers:

[ATTACH=CONFIG]285560[/ATTACH]

I got the same issue when I tried out Mint. WiFi and Bluetooth seem to work fine, though. How should I proceed from this? Thanks to anyone who will help! :)

---

### Post by chili555 on 2020-04-20
It is a known bug. You can gather some additional insight here: [https://askubuntu.com/questions/1217466/why-is-there-an-uninstallable-wifi-driver-where-my-video-driver-should-be/1219111#1219111](https://askubuntu.com/questions/1217466/why-is-there-an-uninstallable-wifi-driver-where-my-video-driver-should-be/1219111#1219111) I suggest that you file a report against ubuntu-drivers-common here: [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

I have the same message on my system using an Intel wireless device that works perfectly.

I suggest that you ignore it.

---

### Post by slickymaster on 2020-04-20
@djdelarosa25:

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by djdelarosa25 on 2020-04-20
> **chili555 said:**
> It is a known bug. You can gather some additional insight here: [https://askubuntu.com/questions/1217466/why-is-there-an-uninstallable-wifi-driver-where-my-video-driver-should-be/1219111#1219111](https://askubuntu.com/questions/1217466/why-is-there-an-uninstallable-wifi-driver-where-my-video-driver-should-be/1219111#1219111) I suggest that you file a report against ubuntu-drivers-common here: [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

I have the same message on my system using an Intel wireless device that works perfectly.

I suggest that you ignore it.

Thank you very much!

> **slickymaster said:**
> @djdelarosa25:

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

My apologies. I'll keep that in mind from now on.

---

### Post by mehmetyldz87 on 2020-11-26
Hi @djdelarosa25

How did you fix this problem? Thanks for help.  

Edit: The problem was solved when I switched from the local [Turkey] server to the main server and performed the updates. :p

---

