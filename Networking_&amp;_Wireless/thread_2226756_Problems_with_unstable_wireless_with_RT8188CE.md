---
title: "Problems with unstable wireless with RT8188CE"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by Christian_Poveda on 2014-05-28
Hello everybody!

I have not been able to connect to the internet from my desktop computer using ubuntu. my computer has a network card Realtek RT8188CE. time I install ubuntu 12.04 and when I tried to connect to the network ubuntu always asked me the password again and again as if the password were incorrect. Then I tried to update the distribution with apt-get and I could connect could not navigate though. Recently I installed debian 7.5 but I could not see the wireless networks available. 

Finally today I'm testing with ubuntu 13.04 live, I can connect, browse and ping, but the connection is slow and unstable. When I run "ping 8.8.8.8" sends packets with low latency, but to spend a few minutes I get the message "Destination host unreachable" over and over again. Something similar happens when I run "ping 192.168.1.1". Anyone could help me diagnose this problem?

---

### Post by praseodym on 2014-05-29
Which kernel do you use in 12.04?
```

uname -a
```

---

### Post by Christian_Poveda on 2014-05-30
Hey sorry for not answering, I was installing ubuntu 14.04 in my PC. I installed 12.04 a year ago so i don't remember the which kernel had. However the kernel of 14.04 is

```
Linux R2D2 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

I don't have internet on 14.04 either. It shows the networks but when I try to connect it asks me to write the password again and again.

---

### Post by praseodym on 2014-05-30
Does LAN work? If yes, update the driver via:

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot.

---

### Post by Christian_Poveda on 2014-05-31
Whoa! I updated the driver and don't know what happened but Ubuntu isn't booting now, when it tries to boot i get this:

[https://www.dropbox.com/s/l7dcty613g4b4sm/2014-05-31%2004.00.09.jpg](https://www.dropbox.com/s/l7dcty613g4b4sm/2014-05-31%2004.00.09.jpg)

---

### Post by praseodym on 2014-05-31
Run the above 7 commands one after another (copy/paste)

---

### Post by Christian_Poveda on 2014-05-31
I just did that, and now ubuntu is not starting

---

### Post by praseodym on 2014-05-31
Can you reach the recovery mode? Reboot (hard reset), press the SHIFT button during boot-up and choose it there. Try to "fix" broken packages there.

---

### Post by Christian_Poveda on 2014-05-31
I used recovery mode, selected dpkg to fix broken packages but the pc cannot download anything because there is no internet, i connected my smartphone and used it as hotspot via usb. But it doesnt worked either, then I tried to enable the network, but I got a kernel panic. Sould i reinstall ubuntu?

---

### Post by praseodym on 2014-06-01
Try to uninstall the driver in recovery mode:
```

cd /home/[COLOR="#FF0000"]YourName[/COLOR]/rtl8188ce-linux-driver
make clean
make
make uninstall
```
Replace "YourName" with your login name

---

### Post by Christian_Poveda on 2014-06-03
Ohh ok... It worked :) Ubuntu is back now, but still the same problem with the wireless conection

---

### Post by praseodym on 2014-06-03
Run this command and reboot:

```
echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```

---

