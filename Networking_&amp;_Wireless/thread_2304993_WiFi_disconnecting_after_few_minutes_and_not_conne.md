---
title: "WiFi disconnecting after few minutes and not connecting again"
date: 2015-12-01
forum: Networking &amp; Wireless
---

### Post by vasanth4 on 2015-12-01
Hi All,
I recently bought new laptop HP 15-ab028TX with Windows 8.1.
Along with windows, I installed UBUNTU 14.04 LTS.
My problem here is, When I log in to ubuntu it shows all the WiFi connections.
After connecting to anyone, it get disconnected after few minutes.
Later it does not show any.

Can anyone please help me here?

Note:
Everything works fine in windows.

Thanks in advance.

---

### Post by scoutchorton on 2015-12-01
This isn't much help, but what kind of a network are you on?

Home, school, work, public place (McDonalds or something)?

Also, does it have some login or security addition?

My school has a internet security (of course, because, hormone filled teenagers can't be trusted on internet), and when I brought my Ubuntu 15.10/Windows 10 laptop to school, the server blocked Ubuntu from loging in. It is some glitch with Linux that the IT's might figure out, but this may help.

If you are an administrator on your home network, play around and see if it blocks Linux operating systems.

I wish you luck! :D

---

### Post by styx4 on 2015-12-01
Vasanth4,

Howdy! I recently had a similar issue but not the exact same(disconnect after suspend and never shows up again). Unfortunately, after extensive searching, I could not find a long-term solution. However, I do know a temporary fix. It requires you to restart the
network manager in terminal.
> sudo service network-manager restart
However, I have discovered that it could be related to a power saving feature that you have to turn off with the following command:
> sudo iwconfig wlan0 power off
To make it permanent, just follow [this quick guide]("https://itechscotland.wordpress.com/2011/09/25/how-to-permanently-turn-off-wi-fi-power-management-in-ubuntu/") (assuming it fixes your problem) so that you don't always have to type it
in when you log in.

Tell us how it goes. The previous post could be right too. It might just be a network security problem. But give this a shot and we can figure it out together from there. There might be a few more things we could try.

Cheers,
Styx

---

