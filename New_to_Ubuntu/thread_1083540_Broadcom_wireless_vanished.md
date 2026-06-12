---
title: "Broadcom wireless vanished"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Hygaphunkik on 2009-03-01
Firstly can I say that I have been using Kubuntu for about 18 hours so bear with me. As far as linux goes I am a nooby fool.

The actual installation was fine but I had problems trying to install a broadcom wireless card. A little hunting around and some hours of head scratching enabled me to finally get the card working at about 11pm last night. Great I thought wireless surfing in bed, I turned the system off and when I turned it on again I could not even get the pc to find the wireless card.

When I first connected a wallet device appeared and asked me to give it a password. This has now vanished, I have no idea where and cannot find any command to access it I was wondering if this had anything to do with the vanishing wireless.

Sorry about the jumbled way I have presented this.

I am using an elonex netbook to type at the moment.

Kubuntu has been installed on a dell latitude d531 and when I did the lspci command in Konsole I can see the Broadcom BCM 4311 Network controller at the end of the list.
 Adept Manager is telling me that b43-fwcutter is installed

The Hardware driver manager tells me that the broadcom wireless driver is not in use even though the box is ticked.

KDE Control Module can only find eth0 which I assume is the wired connection.

Thanks in advance for any help

---

### Post by bailbath on 2009-03-01
[http://billconner.com/techie/wireless_nic.html](http://billconner.com/techie/wireless_nic.html)
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
[http://wicd.net/punbb/](http://wicd.net/punbb/)

Found this it may help you or steer you in the right direction I have had laptops with broadcom and always use wicd instead of network manager.
Ian

---

### Post by Hygaphunkik on 2009-03-01
Thanks had a look through those links   but to be honest I did not really understand some of it. Will have another look at wicd.

---

### Post by Hygaphunkik on 2009-03-01
Just installed wicd but it has not found the wireless adaptor so it cannot configure a network.

Anyone got any other ideas?

---

### Post by Hygaphunkik on 2009-03-01
> **Hygaphunkik said:**
> Just installed wicd but it has not found the wireless adaptor so it cannot configure a network.

Anyone got any other ideas?


Problem now resolved. Went to hardware drivers unchecked the broadcom driver and then rechecked it. Then used the button on the front to turn the wireless on and presto was connected.

Have had to re jig the hardware drivers every time I boot up but at least I am up and running.

---

