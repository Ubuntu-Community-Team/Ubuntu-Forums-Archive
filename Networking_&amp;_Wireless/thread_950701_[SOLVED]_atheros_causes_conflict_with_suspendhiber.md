---
title: "[SOLVED] atheros causes conflict with suspend/hibernate"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by gusanto on 2008-10-17
Hi all,
I have experienced this problem after upgrading to Hardy Heron, my Sony Vaio VGN-NR120E couldn't suspend/hibernate anymore. Today, after I upgraded my kernel (2.6.24-21) and it caused wireless connection, I tried to suspend and it worked. So it looks like that my wireless device (atheros) causes conflict with suspend? (I apologize if this terminology is incorrect - I am just an average linux user). I found out that in OpenSuse ([http://en.opensuse.org/Atheros_madwifi]("http://en.opensuse.org/Atheros_madwifi"), this atheros does conflict with suspend utility.  I have tried with uswsusp to try the alternative way of suspend, but also no luck.  
So I request some help from experts out there to solve this problem. I can post (later) my booting error message if necessary.
Thanks.

---

### Post by gusanto on 2008-10-28
After following this link [http://ubuntuforums.org/showthread.php?t=792158]("http://ubuntuforums.org/showthread.php?t=792158"), both the wireless and suspend have been resolved.  Now my Sony Vaio VGN-NR120E laptop is wirelessly connected and suspend peacefully. Thanks to bmartin who wrote the detail of the guide.

Below is the summary:
> 
sudo aptitude update && sudo aptitude -y install build-essential linux-headers-$(uname -r)
cd ~
wget -O driver.tar.gz [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar xf driver.tar.gz
cd madwifi-*
make
sudo make install
echo ath_pci | sudo tee -a /etc/modules
sudo modprobe ath_pci

---

