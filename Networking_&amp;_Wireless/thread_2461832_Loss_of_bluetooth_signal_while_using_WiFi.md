---
title: "Loss of bluetooth signal while using WiFi"
date: 2021-05-08
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2021-05-08
I use bluetooth to connect my headphone. I rarely transfer any files. While using my bluetooth headphone if I listen to a song which is stored locally on my hard drive there is no problem but if watch YouTube the bluetooth signal starts to deteriorate. I searched the web & found that changing the WiFi router's channel can help fix this issue so I changed it from automatic to 6 but unfortunately it didn't improve anything. My router doesn't allow changing the band.

If anyone knows a solution please reply.

```
$ lsusb 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 005: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 004: ID 2318:2808 Shining Technologies, Inc. [hex] 
Bus 001 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 001 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by hk42 on 2021-05-08
Hi
The first thing I would try is using different USB ports for the WIFI and BT dongles.
Depending on the number of USB ports you have it can be time consuming as you may have
to reboot between tries.

---

### Post by chili555 on 2021-05-08
> My router doesn't allow changing the band.Meaning what? Does your router have a 5 gHz band? I suggest that you try renaming the bands in your router to something like myrouter2.4 and myrouter5. Then connect to the 5gHz band and see if the interference is resolved.

---

### Post by linuxyogi on 2021-05-09
@hk42
I have tried all the USB ports but the interference didn't stop.

@chili555

My router supports 2.4 GHz only . No 5Ghz band. Please visit [this page]("https://www.flipkart.com/jiofi-jmr-1140-data-card/p/itmf6mch497kmnpp") & read the specs.

I am attaching a screenshot of my router's web interface.

[ATTACH=CONFIG]288436[/ATTACH]

---

### Post by linuxyogi on 2021-05-10
@chili555
Do you have any ideas ?

---

### Post by chili555 on 2021-05-10
> **linuxyogi said:**
> @chili555
Do you have any ideas ?Very few, actually. I might try low power, instead of high in the router. You might also try channel 11. Beyond that, I am stumped. Sorry.

---

### Post by linuxyogi on 2021-05-11
> **chili555 said:**
> Very few, actually. I might try low power, instead of high in the router. You might also try channel 11. Beyond that, I am stumped. Sorry.

Okay I will definitely try channel 11 but there is one point I must mention & I am eager to hear what you have to say. I usually connect my bluetooth headphone with my PC only.
Today just to make sure my headphone is not defective I connected my headphone with my Nokia phone while streaming Youtube on my PC. The signal was very strong. There was absolutely no interference. When I connect my headphone with my PC I cant leave my room coz if I leave my room there is no signal at all but while using my phone I played a song & I walked around my entire apartment & there was no signal loss. This proves that my bluetooth dongle is of a very very poor quality. I am not sure about that but that's what I think.

What's your opinion ?

Despite the fact that I don't have cash right now to buy a new dongle I searched on [Amazon.in]("https://www.amazon.in/") (not .com) but sadly didn't find a single bluetooth dongle which is compatible with Linux. This time I want to stick to TP-LINK coz I recently purchased a TP-LINK WiFi dongle & its working great. I had absolutely no problem finding a Linux compatible TP-LINK WiFi dongle on [amazon.in]("https://www.amazon.in/") but unfortunately I fail to find a Linux compatible TP-LINK bluetooth dongle.

---

### Post by chili555 on 2021-05-11
I just noticed this post: [https://askubuntu.com/questions/1208296/bluetooth-adapter-configuration-issue-id-0a120001](https://askubuntu.com/questions/1208296/bluetooth-adapter-configuration-issue-id-0a120001) Please notice that it is the same as your device.

Let's try two things from the post. First, create a new file:

```
sudo nano /etc/modprobe.d/bluetooth-usb.conf
```Add a single line:```
options btusb enable_autosuspend=n
```Proofread carefully, save (Ctrl+o followed by Enter) and exit (Ctrl+x followed by Enter).

Next, we'll modify one file:```
sudo nano /etc/bluetooth/main.conf
```Find the line that says:

```
# will fully work only on kernel version 4.1 and newer. Defaults to
# 'false'.
#FastConnectable = false
```Change it to:

```
# will fully work only on kernel version 4.1 and newer. Defaults to
# 'false'.
FastConnectable = true
```Save and exit the text editor.

Reboot and tell us if there is any improvement.> but unfortunately I fail to find a Linux compatible TP-LINK bluetooth dongle.I read conflicting reports, like here: [https://www.amazon.com/TP-Link-Bluetooth-Receiver-Controllers-UB400/dp/B07V1SZCY6/ref=sr_1_2?dchild=1&keywords=TP-LINK+bluetooth&qid=1620749641&sr=8-2](https://www.amazon.com/TP-Link-Bluetooth-Receiver-Controllers-UB400/dp/B07V1SZCY6/ref=sr_1_2?dchild=1&keywords=TP-LINK+bluetooth&qid=1620749641&sr=8-2)

> Q: does this work in ubuntu ?
A: It says in the description that it dosnt support linux or mac os. Ubuntu is a linux distribution so im assumeing no
By Codie Taylor on December 4, 2020
Q: As another customer asked, i want to know if this works with linux (ubuntu 20) as it sup.works with chromebook and macbk. these are both linux basedin
A: Yes, I use it on a computer that has Ubuntu.
By W. Sisco on October 21, 2020Since Amazon offers free returns, I'd try it.

---

### Post by linuxyogi on 2021-05-11
@chili555
Followed all those tweaks but no improvement. I did some research about bluetooth & I have decided to buy [this]("https://www.amazon.in/Portronics-14-POR-1153-Bluetooth-Transmitter/dp/B08LVH8P6H/ref=sr_1_2?dchild=1&keywords=portronics+auto+14&qid=1619197126&sr=8-2") instead of a usb dongle.

---

