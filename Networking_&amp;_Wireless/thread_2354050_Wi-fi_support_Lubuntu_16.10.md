---
title: "Wi-fi support? Lubuntu 16.10"
date: 2017-02-27
forum: Networking &amp; Wireless
---

### Post by jbdelta66 on 2017-02-27
Hello, 

I am new to forums and Ubuntu and I have a couple of questions a couple of questions about drivers and hardware. I am running Lubuntu with LXDE, 16.10 yaketty on a very old Dell Precision 340 from 2002. It has a 1.8GHz Pentium 4 and 512MB of PC-800 RDRAM. 
Also aboard is an Nvidia GeForce 3 ti200 and a SoundBlaster Live! 

Anyhow I'm trying to get an ( also old ) USB Wireless-B wlan adapter to work but Ubuntu will not recognize it.
I have the drivers downloaded from the OEM and it's a CNet CNUSB-611 device from 2003 or so. 802.11b USB 1.1 chipset made by Atmel . I have in the driver package a folder for Linux, which says Redhat and Mandrake. Nothing else,.

Can anyone tell me a way to make Ubuntu recognize my device?

---

### Post by r.stiltskin on 2017-02-27
Have you installed atmel-firmware package?
e.g.:

sudo apt-get install atmel-firmware

---

### Post by chili555 on 2017-02-27
May we see:```
lsusb
dmesg | grep at76
```Thanks!

----------

Possible reference: [https://wikidevi.com/wiki/CNet_CNUSB-611](https://wikidevi.com/wiki/CNet_CNUSB-611)

---

### Post by mörgæs on 2017-02-28
Are you aware of how narrow a bandwidth you will get with 802.11b compared to, say n?

---

### Post by jbdelta66 on 2017-02-28
> **r.stiltskin said:**
> Have you installed atmel-firmware package?
e.g.:

sudo apt-get install atmel-firmware

This works! 

Atmel drivers are installed. Adapter is working but now am having problem getting WPA2 security to work.

PC will connect to an unsecured network but refuse to connect to WPA2 ?

---

### Post by jbdelta66 on 2017-02-28
Lol. I seriously doubt this behemoth would be able to talk to an N wi-fi adapter, let alone benefit from its functionality. My USB ports are 12mb/s usb 1.1

---

### Post by chili555 on 2017-02-28
> **jbdelta66 said:**
> Lol. I seriously doubt this behemoth would be able to talk to an N wi-fi adapter, let alone benefit from its functionality. My USB ports are 12mb/s usb 1.1I'm looking forward to the details I requested in post #3.

---

### Post by jbdelta66 on 2017-02-28
> **mörgæs said:**
> Are you aware of how narrow a bandwidth you will get with 802.11b compared to, say n?

Slower than a three legged turtle in the snow &#128514;

I know, but it's the only one I could find that works.
Besides my motherboard only supports USB 1.1 so I'm limited to 12Mb speed. Unless I install a PCI card.

I got the adapter working in Ubuntu but now it will not connect to any secured network. Open networks connect fine but will not connect with WPA2. Have tried this with 3 different routers today

---

### Post by jbdelta66 on 2017-02-28
> **chili555 said:**
> I'm looking forward to the details I requested in post #3.

Sorry, I'll have to manually type in and screenshot the output. 
I'm on my phone ATM

---

### Post by jbdelta66 on 2017-02-28
> **chili555 said:**
> I'm looking forward to the details I requested in post #3.

When I type the code, I get:

---

### Post by jbdelta66 on 2017-02-28
Sorry. I didn't do that right

Try this:[ATTACH=CONFIG]273934[/ATTACH]

---

### Post by r.stiltskin on 2017-02-28
That adapter is certainly not WPA2-capable.  According to the specs I found [here]("https://www.cnet.com/products/wireless-usb-adapter-wep-802-11b-11mbps-128bit/specs/") you could use WEP -- not as good but better than nothing.

Oh, and regarding the output that chili555 requested, those are two separate commands.  First run
lsusb

then run
dmesg | grep at76

---

### Post by jbdelta66 on 2017-02-28
OK so it's not anything wrong, it's just B wireless can't do WPA2?

Also I corrected the commands. See my post above ^

---

### Post by chili555 on 2017-03-01
> **jbdelta66 said:**
> OK so it's not anything wrong, it's just B wireless can't do WPA2?

Also I corrected the commands. See my post above ^Many devices that do 802.11B will do WPA and WPA2. The two are separate. 

However, many devices were manufactured, that is, the chips were designed and fabricated,* before *the advent of WPA and WPA2. You can check to see what the hardware and driver combination are capable of with the terminal command:```
iw list
```Here is an example from my machine:```
<snip>
Supported Ciphers:
		* WEP40 (00-0f-ac:1)
		* WEP104 (00-0f-ac:5)
		* TKIP (00-0f-ac:2)
		* CCMP-128 (00-0f-ac:4)
		* CMAC (00-0f-ac:6)

```TKIP and CCMP (also known as AES) are parts of WPA and WPA2. I doubt that your old device will do encryption that was developed *after* the device was sold. Frankly, WEP is so insecure and is almost never used and so I think that your device is useless except as an antique.

It is remarkable, however, that Ubuntu provides the driver and firmware by default for all these old-timers.

---

### Post by jbdelta66 on 2017-03-01
> **chili555 said:**
> Many devices that do 802.11B will do WPA and WPA2. The two are separate. 

However, many devices were manufactured, that is, the chips were designed and fabricated,* before *the advent of WPA and WPA2. You can check to see what the hardware and driver combination are capable of with the terminal command:```
iw list
```Here is an example from my machine:```
<snip>
Supported Ciphers:
		* WEP40 (00-0f-ac:1)
		* WEP104 (00-0f-ac:5)
		* TKIP (00-0f-ac:2)
		* CCMP-128 (00-0f-ac:4)
		* CMAC (00-0f-ac:6)

```TKIP and CCMP (also known as AES) are parts of WPA and WPA2. I doubt that your old device will do encryption that was developed *after* the device was sold. Frankly, WEP is so insecure and is almost never used and so I think that your device is useless except as an antique.

It is remarkable, however, that Ubuntu provides the driver and firmware by default for all these old-timers.

So I guess I'm going to look for another adapter :/

Indeed,
 It makes me wonder how the OS can be so widely adaptable for various hardware. On a slightly off topic thought; why are PC operating systems, especially Linux so flexible yet mobile, i.e Android has such difficulty making their newer kernels and libraries etc, run on old hardware? Why does my phone get denied major software updates yet I'm running the absolute latest version of Ubuntu Linux on a Pentium 4? Lol

---

### Post by chili555 on 2017-03-01
> why are PC operating systems, especially Linux so flexible yet mobile, i.e Android has such difficulty making their newer kernels and libraries etc, run on old hardware? Why does my phone get denied major software updates yet I'm running the absolute latest version of Ubuntu Linux on a Pentium 4? LolAhh! Android! I suspect that a big part of the reason is that phones reserve just a tiny space for the heavily modified and adapted kernel while PCs have plenty of space to include drivers and features for nearly everything. 

Of course, the cynics will claim that updates are not forthcoming for older phones in order to encourage us to get a newer phone in order to get the latest feature$.

---

