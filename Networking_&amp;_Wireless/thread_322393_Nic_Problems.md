---
title: "Nic Problems"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by Hav0ck on 2006-12-20
I hope someone can help me out. I have an older laptop that I would like to install Xubuntu on but the machine is currently running Ubuntu Dapper fresh install.
My PC card nic a 3com 3C589C is not working. This card doesn't appear in the Ubuntu wiki as a supported card. **However** according to this page [http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS](http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS) the card is supported (it's the first card listed actually) and doing a man tc589_cs shows that the device driver for this card is available in Ubuntu.

The card shows up fine in device manager and is listed in the Network screen as active.

I tried adding tc589_cs to my /etc/modules to include tc589_cs, maybe I am completely wrong on this one.

I cannot get a IP via DHCP and when I specify the IP i cannot ping outside the laptop nor can I ping to the laptop. The PC card functions just fine in Windows. 

I also tried echo 'blacklist ipv6' | sudo tee -a /etc/modprobe.d/blacklist thinking that there might be a problem with IPV6 and the card but it didn't change anything.

Can someone help me out before I install Windows on the laptop ](*,) 

Thanks

---

### Post by Iowan on 2006-12-20
See if the **modprobe** advice in this thread helps.
[http://ubuntuforums.org/showthread.php?t=16694]("http://ubuntuforums.org/showthread.php?t=16694")

---

### Post by Hav0ck on 2006-12-22
Thanks for the advice, I tried the steps in the thread and unfortunately it didn't work. I tried using the 3c589 module but Ubuntu is telling me that the module cannot be found. Did Dapper lose support for older hardware?

I guess Ill have to get rid of Ubuntu and go back to windows. Too bad, Ubuntu looked like it might be the Distro for me to make the switch with. :(

---

