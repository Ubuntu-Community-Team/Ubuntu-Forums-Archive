---
title: "Raspberry pi 4, bad wifi strength"
date: 2022-10-17
forum: Networking &amp; Wireless
---

### Post by nicknjg-11 on 2022-10-17
I am using version 20.10 brand new to Linux, and ever since i have been using my raspberry pi 4 to run Ubuntu, the signal strength has been either 24mb/s or 74mb/s (sometimes something in between). I believe this is causing me problems with the apt-get update and apt-install commands as i havent been able to install anything ive needed to do the tutorials I am going through. For everything I have tried to install, the terminal shows me that some parts are ran successfully, but it fails somewhere down the line for everything so far, I can provide more info if needed.

when i boot the system up, after i log into my user account i get the following errors
 [HTML]
[FAILED] failed to start system security services Daemon.
[DEPEND] dependency failed for SSSD NSS service responder socket.
[DEPEND] dependency failed for SSSD PAM service responder private socket.
[DEPEND] dependency failed for SSSD PAM service responder socket.
[DEPEND] dependency failed for SSSD AutoFS service responder socket.
[DEPEND] dependency failed for SSSD PAC service responder socket.
[DEPEND] dependency failed for SSSD Sudo service responder socket
[DEPEND] dependency failed for SSSD SSH service responder socket.
[/HTML]


I also tried this solution  [https://forums.raspberrypi.com/viewtopic.php?f=117&t=291688](https://forums.raspberrypi.com/viewtopic.php?f=117&t=291688)
out of the two commands listed in this solution i only did this one 
$ sudo cp brcmfmac43456-sdio.clm_blob /lib/firmware/brcm/

because I didnt know what the other command did, i also get a message which i believe to be related to me making this change, which is below
[HTML]brcmfmac: brcmf_cfg80211_set_power_mgmt: power save enabled[/HTML]

should I remove the " brcmfmac43456-sdio.clm_blob " from the brcm directory?

thank you for reading, any help apprechiated.

---

### Post by morrownr on 2022-10-19
Hi nicknjg-11

> I am using version 20.10 brand new to Linux

Welcome to Linux. I think I see your problem.

Ubuntu uses a 2 year dev cycle with 2 releases each year. The important releases and the one that most folks should use are the 04 releases on even years... 22.04, 24.04, etc. These are long term support releases. That means they are supported for many years. The other 3 releases in the 2 year cycle are more of less testing releases and are only supported for 9 months. You are using 20.10 which is no longer supported. It is likely that your 20.10 is not updating because the supporting repos may not be active anymore.

I recommend you burn a new sd with Ubuntu 22.04 LTS or 22.10 which should be available tomorrow.

Other subject: The internal wifi on the RasPi's is not strong, especially 5GHz. Many RasPi users, including myself, turn off the internal wifi and use a usb wifi adapter. More info at this site:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

The above url is also listed in the top sticky here in the forum.

Nick

---

### Post by TheFu on 2022-10-19
22.10 isn't meant for new users or non-developers.  Best to avoid it unless there isn't any other choice.  New is the enemy of stable and proven. Always remember that.

Start with 22.04 and consider using 20.04 instead if you want a more stable, more proven, release.  For are "LTS" releases. That's important.  Odd years and October releases are never LTS.

Reported speeds from any wifi tool is a lie.  Never trust those.  Use iperf3 or actually transfer data between 2 systems on the same LAN to see the real throughput.  Everything else is "marketing" and not worth using since from millisecond to millisecond, environmental conditions change for wifi.

Seriously, just use the wired ethernet and avoid the wifi junk.

With all that said, I've had r-pi zero, v2 and v3 devices.  I still use a v2 and v3 to run media centers around here. 1 of them is for use with a projection system and does an excellent job.  Both run mpd servers for audio.  Both don't use wifi. In a prior job, I did 1200+ wifi deployments for the company and learned very quickly all the issues. At home, I avoid wifi and put any wifi-only devices outside the secure LAN. They are treated like untrusted internet traffic, unless they use a full VPN to get to the trusted LAN.  Security of all wifi, even the latest is terrible. The only thing worse would be bluetooth.

---

### Post by nicknjg-11 on 2022-10-19
Thank you for an indepth response, i was considering a wifi dongle, but i may go for wired if i can. Ive been using this veraion for 5 days now, ive still managed to learn some basic commands. I will go for 20.04 to get something more stable.

---

### Post by nicknjg-11 on 2022-10-19
That was insightful thank you, mine seems to be 2.4GHz but still had some other issues, like youtube videos playing in slow motion, i suspect this is also down to the poor wifi capabilities.

---

### Post by TheFu on 2022-10-20
> **nicknjg-11 said:**
> That was insightful thank you, mine seems to be 2.4GHz but still had some other issues, like youtube videos playing in slow motion, i suspect this is also down to the poor wifi capabilities.

You shouldn't expect a pi4 to be a general purpose computer.  Any 5 yr old Intel CPU will be faster in almost every way ... and can be had for less money, if you watched the used market.  Heck, a $80 chromebook is more powerful, by far, than any raspberry pi.

Servers shouldn't use wifi .... er .... ever.  Ok, there are one or two exceptions, but they wouldn't be a "server" in those situations. They are leaf nodes in a network.  Wifi has all sorts of issues that just aren't worth the time to maintain or troubleshoot for a server.

Raspberry pi computers are great for what they are - small, cheap, devices for specific purposes.  Sadly, the raspberry pi v4 isn't even cheap.

---

