---
title: "Ubuntu 14.04 Ethernet connnection won't save password"
date: 2015-12-22
forum: Networking &amp; Wireless
---

### Post by brian110 on 2015-12-22
I am on ubuntu 14.04 LTS.  I am able to connect to network via wireless, but ethernet is not working.  I have tried a number of different "solutions" but none has helped.

I just updated my packages and distro using:

```

sudo apt-get update
sudo apt-get dist-upgrade
```

and then rebooted.

I ran the wireless info script provided in the forum stickied post.  I attached the wireless-info.txt file with the output.

I'm not sure if it helps, but the connection I am trying to establish is to a university protected network, which requires a username and password.  Previously I tried to set the network up myself, but this didn't work.  The connection would stall at the point of "getting IP configuration", and would continually ask me to re-enter the password.  I just tried deleting the wired-connection that I set up and tried to connect to "auto-ethernet", but this didn't work either, as it stalled at "getting IP configuration", and never asked me for a user name or password.

Thanks in advance, please let me know if I can give any further info.

---

### Post by praseodym on 2015-12-22
Hi,

change the driver via:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/50/3005217-r8168-dkms-8.041.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.041.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.041.00
sudo dkms build -m r8168-dkms -v 8.041.00
sudo dkms install -m r8168-dkms -v 8.041.00
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by brian110 on 2015-12-22
Thanks Praseodym!

Could you explain why I need to change the driver from r8169 to 8168?

---

### Post by Vladlenin5000 on 2015-12-22
There are known issues with the default driver so it makes sense to try another one. That said, your specific problem may not be driver related.

---

### Post by brian110 on 2015-12-22
Well I followed Praseodym's instructions exactly, but the issue persists.

I ran ifconfig, and it looks like r8169 is still the driver for eth0, so perhaps that is part of the issue?

I have attached the new  "wireless-info.txt" file so you can see what has changed since I ran Praseodyms commands.

Thanks!

---

### Post by praseodym on 2015-12-22
File is missing ;)

---

### Post by praseodym on 2015-12-22
Please run
```

sudo modprobe -rfv r8168 r8169
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u -k all
```

---

### Post by brian110 on 2015-12-22
Okay I ran the commands given by Praseodym, and then rebooted, but it still doesn't work.

It does appear that the driver has been switched now, though.

I attached the new wireless-info.txt file for  your reference.

Thanks for the help so far!

---

### Post by Vladlenin5000 on 2015-12-22
Perhaps now it's time to contact your Uni's IT department.

---

### Post by brian110 on 2015-12-22
Sadly, I contacted them yesterday, and they were no help.   I will likely have to go in in person and harass them, but they will be closed for the next few days.

Thanks for the help so far!

---

### Post by Vladlenin5000 on 2015-12-22
Oh, yes, it's that time of the year. I don't really care about it (philosophical reasons that should be obvious ;)) so I tend to forget.

The reason I suggested you contact IT is because there's usually much more that usernames/passwords involved in such accesses. Encryption type, certificates, etc. are usually required to be setup exactly as designed by the network admins. One wrong setting is enough to make the connection impossible.

---

### Post by brian110 on 2015-12-22
Ahh I see what you mean.   Yes, in fact my institution has an online guide for setting up the wireless connection for Ubuntu, but it lacks a similar guide for a wired connection.  I tried using the same settings from wireless as wired, but I had no luck.   I suppose I can wait until after the holidays to harass the IT department. I don't want to ruin anyone's Christmas afterall ;).

Thanks again.

---

