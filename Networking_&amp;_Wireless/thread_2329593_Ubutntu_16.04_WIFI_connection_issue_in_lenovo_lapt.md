---
title: "Ubutntu 16.04: WIFI connection issue in lenovo laptop with qualcom wifi adapter"
date: 2016-07-03
forum: Networking &amp; Wireless
---

### Post by kpsaravu on 2016-07-03
i bought a new lenovo laptop last year and I am not able to connect to my home wifi with it.

i found a script to grab the network info :

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && chmod +x wireless-info && ./wireless-info

I have attached the wireless-info.txt file along with this post.

Any help in getting wifi enabled is appreciated.

Note: i have 15.04 installed as dual boot. wifi is not getting enabled. this wireless-info.txt is from a 16.04 live cd.  just trying if 16.04 works or not.

I have a qualcomm atheros wifi adapter it looks like:

Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
	Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
	Kernel driver in use: ath10k_pci
	Kernel modules: ath10k_pci

---

### Post by kpsaravu on 2016-07-03
i fixed my problem after installing new QCA6174 drivers...

---

### Post by ajgreeny on 2016-07-03
Great. Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by jeremy31 on 2016-07-03
New drivers or just firmware?  I haven't seen any driver issues with the QCA wifi cards in 16.04 just missing firmware

---

### Post by kpsaravu on 2016-07-03
Sorry, yeah they were just missing firmware. 

I used this thread as reference: [http://askubuntu.com/questions/763080/no-wifi-in-qualcom-atheros-ubuntu-16-04-acer-aspire-e-15](http://askubuntu.com/questions/763080/no-wifi-in-qualcom-atheros-ubuntu-16-04-acer-aspire-e-15)

(used QCA6174 instead of QCA9377)

---

