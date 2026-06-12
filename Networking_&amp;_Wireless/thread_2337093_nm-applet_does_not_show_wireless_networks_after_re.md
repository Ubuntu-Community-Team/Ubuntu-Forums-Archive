---
title: "nm-applet does not show wireless networks after resuming from suspend"
date: 2016-09-14
forum: Networking &amp; Wireless
---

### Post by jeffhoogland on 2016-09-14
Recently upgraded to Ubuntu 16.04 base on my laptop. The wireless devices works as expected on first boot, but when I suspend the system / resume it the network manager no longer displays wireless networks - just empty. It does however reconnect to the wireless network I have stored on the system though - but the network icon displays a wired connection icon as opposed to the wireless icon.

Wireless card is:

```
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
```

And I am using the Enlightenment based Moksha desktop with nm-applet sitting in the system tray. 

Previously under an Ubuntu 14.04 base this worked as expected. I've tried changing kernels, but I am getting the same behavior under the 4.7.3 mainline kernel as I was getting under the default 4.4.0 kernel Ubuntu 16.04 has.

Any debugging suggestions to figure out why this is? Not a showing stopping issue but definitely a minor annoyance.

---

### Post by newbie-user on 2016-09-14
Had this problem a few months ago with an Intel 7265 card. I don't have a fix, but here's the workaround I used.

Create the file /etc/systemd/system/wifi-resume.service which contains the following:

```
[Unit]
Description=Restart networkmanager at resume
After=suspend.target
After=hibernate.target
After=hybrid-sleep.target

[Service]
Type=oneshot
ExecStart=/bin/systemctl restart network-manager.service

[Install]
WantedBy=suspend.target
WantedBy=hibernate.target
WantedBy=hybrid-sleep.target
```

Then enable the service:
```
systemctl enable wifi-resume.service
```

That put the wifi icon back up. A recent install of 16.04 doesn't show this problem with the Intel card.

---

### Post by jeffhoogland on 2016-09-14
So - that does allow it to properly reconnect after suspending, but now it isn't connecting when I first boot up until I restart the network-manager service.

---

### Post by tea for one on 2016-09-14
Good evening

@jeffhoogland

I am asking this out of curiosity:-

Are you the lead developer of Bodhi Linux and creator of the Moksha desktop?

---

### Post by jeffhoogland on 2016-09-14
I am. I am more the "maintainer" of the desktop than anything though. The core of the desktop was written by the enlightenment team and we have done fairly minimal changes - mostly bug fixing.

---

### Post by tea for one on 2016-09-14
Hello Jeff

Thanks for your reply

I note that you only joined the forums this month (September 2016), therefore I assume that The Ubuntu base for Bodhi Linux gave you very little difficulty in previous Bodhi releases. :)

Anyway, I wish i could help with your nm-applet query but my level of expertise is sadly lacking in network applications.

Good luck with Bodhi and I'm sure somebody will soon step in soon with some useful information.

---

