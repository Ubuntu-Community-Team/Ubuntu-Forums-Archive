---
title: "WiFi is very finicky and almost non-functional?"
date: 2017-02-11
forum: Networking &amp; Wireless
---

### Post by Matt_Boling on 2017-02-11
I am currently having a problem with my WiFi on my laptop, most likely related to the software, as my Windows partition works flawlessly with the Wi-Fi, and I didn't have any issues with Ubuntu 16.04.
I installed Ubuntu Budgie 16.10 (The same problem, however, occurs with my Ubuntu Gnome USB). The WiFi will take forever to connect, only after stubbornly disconnecting and reconnecting several times, and after finally reaching a connection, the internet works for about 10 seconds and then, even though it is connected, cannot load up any webpages.
I tried manually connecting an Ethernet cable, but to no avail- the same problem happens.
I also tried to disable IPV6 (both via network manager and via sysctl.conf) and to disable IPV4 (via network manager), but the same problem happens.
I'm using an HP Notebook, and after Pinging it in terminal, what ends up happening is that my computer cannot access any data repeatedly, and then after 6 lines of text it will connect for three lines, and this process repeats indefinitely.

I do want to stress that my Windows partition works flawlessly with the internet, with no issues at all, so I suspect it is a software related issue.

Anybody else having this issue, and has anybody come up with a solution?

Thanks,
-Matt

---

### Post by jeremy31 on 2017-02-11
See the wireless script link in my signature and post results using code tags or you can paste the contents of the wireless-info.**txt** file at paste.ubuntu.com and post the URL

---

### Post by Matt_Boling on 2017-02-11
OK, I ran your script, and have attached the compressed folder.

I've also pasted the contents on the Ubuntu Pastebin.

[http://paste.ubuntu.com/23978493/](http://paste.ubuntu.com/23978493/)

---

### Post by Hadaka on 2017-02-11
Hi, please open a terminal.../ctrl/alt/t..and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
Then Copy and paste..
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
Boot and test wireless
Thanks

---

### Post by Matt_Boling on 2017-02-12
After performing your steps, nothing has seemingly changed and I am encountering the same problem.

---

### Post by Hadaka on 2017-02-12
Hi, please post the output of..
```
/etc/rc.local.orig
/etc/rc.local
```
Then do..
```
echo options rtl8188ee swenc=1 msi=1 fwlps=0 ips=0 | sudo tee /etc/modprobe.d/rtl8188ee.conf
```
boot and test wireless
Thanks.

---

