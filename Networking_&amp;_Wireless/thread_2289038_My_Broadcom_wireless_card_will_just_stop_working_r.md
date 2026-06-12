---
title: "My Broadcom wireless card will just stop working randomly."
date: 2015-07-31
forum: Networking &amp; Wireless
---

### Post by grady3 on 2015-07-31
Well I don't exactly know if that's the problem, but that's what makes sense to me. I will be using my laptop and suddenly, out of the blue, I will be disconnected from the internet. I have tried some terminal commands for turning on and off the card manually but that doesn't seem to work. The only surefire way of getting reconnected is to reboot my laptop. This is really frustrating me. I am running 14.04.

Here is what I get when I enter in  ```
lspci | grep Wireless
```

```
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```


If you need any more information pleas ask. I don't really know what is going on. My hardware is really old. It might just be dying on me. The results from this code are attached below.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info

```


Thanks for your time.

---

### Post by Hadaka on 2015-07-31
Hi,please copy and paste..
```
sudo rm /etc/modules
echo -e "lp\nrtc\nb43" | sudo tee -a /etc/modules
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```

did you enter a wake on lan command to deal with this issue?
/etc/pm/power.d/disable_wol ?????

---

### Post by grady3 on 2015-07-31
Hey. So I entered that stuff you gave me to try. I don't know if it worked yet. This is what I got.

```
grady@Tha-Ressurection:~$ sudo rm /etc/modules
grady@Tha-Ressurection:~$ echo -e "lp\nrtc\nb43" | sudo tee -a /etc/modules
lp
rtc
b43
grady@Tha-Ressurection:~$ sudo iw reg set US
grady@Tha-Ressurection:~$ sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```

And I have no idea what a wake on lan command is. I am pretty new at this. Sorry.

---

### Post by Hadaka on 2015-07-31
ok,please do..
```
sudo mv /etc/pm/power.d/disable_wol /etc/pm/power.d/disable_wol.old
```
and post the output of..
```
sudo iw reg get
cat /etc/modules
```
and run and repost another script info file
thanks.

---

### Post by grady3 on 2015-07-31
Ok so I ran your commands and got this.

```
grady@Tha-Ressurection:~$ sudo mv /etc/pm/power.d/disable_wol /etc/pm/power.d/disable_wol.old[sudo] password for grady: 
grady@Tha-Ressurection:~$ sudo iw reg get
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)
grady@Tha-Ressurection:~$ cat /etc/modules
lp
rtc
b43
grady@Tha-Ressurection:~$ 

```

The second wireless info script results will be attached below. Thanks.

---

### Post by Hadaka on 2015-08-01
is it still dropping out?
and please post
```
sudo iwlist wlan0 scan
```
thanks

---

