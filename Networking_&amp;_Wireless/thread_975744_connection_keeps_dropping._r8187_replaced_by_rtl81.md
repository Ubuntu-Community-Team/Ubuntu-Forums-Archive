---
title: "connection keeps dropping. r8187 replaced by rtl8187 with newest intrepid ipex kernel"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by Orkun Sensebat on 2008-11-08
Thanks to some hardy update I was able to ditch ndiswrapper for my wlan card's native driver.

> orkun@orkun-laptop:/etc/modprobe.d$ lspci |grep RTL
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

> orkun@orkun-laptop:/etc/modprobe.d$ lsmod | grep 8 | grep 1
_r8187_                  93956  0 
ieee80211_rtl          80520  1 r8187
ieee80211_crypt_ccmp_rtl     8064  1 ieee80211_rtl
ieee80211_crypt_tkip_rtl    11648  1 ieee80211_rtl
ieee80211_crypt_wep_rtl     6400  1 ieee80211_rtl
ieee80211_crypt_rtl     6788  4 ieee80211_rtl,ieee80211_crypt_ccmp_rtl,ieee80211_crypt_tkip_rtl,ieee80211_crypt_wep_rtl
r8169                  33156  0 

> orkun@orkun-laptop:/etc/modprobe.d$ uname -r
2.6.24-21-generic

This is my working set-up which uses r8187. I keep my old kernel running, which works fine.

**Since intrepid introduced kernel 2.6.27, my wireless connection drops after a minute. This is caused by the module rtl8187, which seems to have replaced r8187.** I somewhere googled, that this is due to a bug with r8187. Now I can use the old kernel without any problems, but what after reinstalling ubuntu? the old kernel wont be there.

can i and if so how...

a) ... continue using the old kernel, even though i want to change to a clean intrepid installation?

b) ... get this solved with rtl8187b

c) ... get r8187 installed with latest intrepid kernel? i know how i would use modprobe's blacklist to disable rtl8187 - but where can i get the r8187 driver and get it compiled? will i have to recompile a custom kernel, so that the ieee architecture will be used instead of the mac, which is being introduced with latest intrepid kernel?

if none of these will work, how can i expect this kernel thing to develop in the future? i mean, if worst comes to worst, i can stick to hardy for a release schedule, although i really enjoy updates of x.org, nm, gnome and especially vlc.


best regards

o

---

### Post by Tom--d on 2008-11-08
Simple.

Run is command while connected:
```
sudo iconfig wlan0 rate 5.5M fixed
```
and if that keeps the connection, put it in your /etc/rc.local file.
```
gksu gedit /etc/rc.local
```
put it BEFORE exit 0

---

### Post by Orkun Sensebat on 2008-11-09
NOT working :(
any **other ideas**?

---

### Post by Orkun Sensebat on 2008-11-16
bump...
c'mon guys!

some1 should be able to tell me, whether a) i will have to somehow save and hold on to this one very precious kernel, b) have to compile a whole new one in the long run or c) can somehow make this work on any kernel!


best regards and ty in advance!

---

### Post by abhinavg90 on 2008-11-16
Got the exactly same problem.
Connection drops after some time. Network manager reports as connected but no data is transferred. No site opens. And it won't connect to the same or other network. I have to either restart or unload and reload the module ( *sudo rmmod rtl8187 && sudo modprobe rtl8187* ). Then it gets back to working till it drops again.

I went for a clean install so I don't have the old kernel and the old cuervo drivers don't seem to be compiling on the new one.

I tried Tom--d's solution and it doesn't seem to be working. It still drops after some time, though maybe might be lasting longer. So I have that in my rc.local.

I even considered compiling a new kernel. Tried doing it to the latest git one ( though I think I should've gone for an old one - but don't wanna loose WPA which seems to work with this driver ). After configuring it, I left it to compile and when I checked after 2 hours, there was some error. Didn't bother looking it up and deleted the kernel source directory. 

Because of this problem I am stuck using XP most of the time.

Hope its fixed soon.

**UPDATE**
Tom--d's solution is working **perfectly**!! 5 hours+ and still no dropped connections.
I ran *watch -n3 iwconfig wlan0* in a terminal and kept it running minimized. Read that on cuervo's blog.
Not sure if that + Tom--d's solution is keeping my connection going or only his solution.

**Another update**
Tom--d's solution working alone. Without the watch. Thanks!

**And another update**
I was wrong. Tom--d's solution is **not** working. Connection still drops occasionally. I even reduced the tx-power to 20dBm ( *sudo iwconfig wlan0 txpower 20* ). Doesn't seem to have helped.

---

### Post by Orkun Sensebat on 2008-11-18
Okay, tried it 2 times(without too many effort i admit)

I will try again some times - I even think the last kernel update made things better. I will update again on this topic the next couple of days.

---

### Post by abhinavg90 on 2008-11-19
Yes you are right. Not working. Seems it works normally with minimal amount of connection drops when I am just surfing the internet. But any heavy use like downloading something and it drops off after some time.

---

