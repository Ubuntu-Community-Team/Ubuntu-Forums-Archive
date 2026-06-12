---
title: "Internet connection constantly dropping on home network"
date: 2019-07-17
forum: Networking &amp; Wireless
---

### Post by aqmbe on 2019-07-17
[COLOR=#242729][FONT=Arial]I have Dell XPS with Ubuntu 18.04. Whenever I am using my home network (and only this specific network), my internet connection keeps on dropping at random points in time. The network itself seems to be working as intended: other devices (as well as this same laptop when running Windows) work just fine.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]However, I still have the feeling that the problem lies in how my home network was set up. It consists of a wireless modem and two access points. Whenever I am close to the modem, the internet connection seems to be more stable. When I move further away (and nearer to one of the access points), the connection starts dropping more and more often. Again: this only happens when running Ubuntu.

Any ideas how to solve this? Thanks![/FONT][/COLOR]

---

### Post by TheFu on 2019-07-17
Use wired networking.  It that stable?  If so, then you've eliminated the upstream from the router to the internet.

Wifi is very difficult to troubleshoot remotely.   I would look at all the adaptor settings in Windows, write them down. ALL OF THEM.  Then I'd look at the adaptor settings under Linux.  What is different?  Can you alter the driver settings to make it the same?  Often, the Linux drivers aren't a feature rich as the Windows version because the vendor didn't actually make the driver.  Complain to them loudly.

---

### Post by him610 on 2019-07-17
Hell aqmbe,
Please read the advisory in this post, [https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")

---

