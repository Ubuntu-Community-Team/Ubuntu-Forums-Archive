---
title: "Kubuntu problem or router problem with connectivity?"
date: 2014-05-17
forum: Networking &amp; Wireless
---

### Post by rwwood on 2014-05-17
I have a Toshiba Satellite C55-A on which I've installed Kubuntu 14.04. When first installed I couldn't get the Realtek 8188ee card to connect. After a lot of searching, I followed a recommendation to install 13.10, which gave no problems and recognized the card without a problem. Connectivity was decent, and after the install, whether I did it inadvertently or it was an automatic update, the version was upgraded to 14.04 and the card continued to work until at one point a couple weeks ago a recommended update caused the card to stop working.

Again I searched high and low and tried a couple of possible solutions, although most of them were for earlier versions than 14.04 and none of them resolved the problem. Additional searching suggested that an ASUS USB-N13 would work out of the box, so I decided to go that route. The install wasn't so out of the box as what I thought it would be and the only way I could get it to work was to downgrade the kernel per a post [here]("http://www.thheuer.com/2014/05/ubuntu-14-04-asus-n13-wireless-usb-adapter-problems-howto/"), and everything seemed to be working ok.

What I've encountered is that, if I'm sitting right next to the router, I get the following diagnostic output: 
```
root@ToshibaLaptop:/home/rww# iwlist wlan2 scan 
wlan2 Scan completed : 
Cell 01 - Address: 00:18:F8:4A:A2:E2 
ESSID:"Ourplace" 
Protocol:IEEE 802.11bg 
Mode:Master 
Frequency:2.412 GHz (Channel 1) 
Encryption key:off 
Bit Rates:54 Mb/s 
Quality=100/100 
Signal level=100/100
``` 

If I move in another room to the house, I get the following output: 
```
root@ToshibaLaptop:/home/rww# iwlist wlan2 scan 
wlan2 Scan completed : 
Cell 01 - Address: 00:18:F8:4A:A2:E2 
ESSID:"Ourplace" 
Protocol:IEEE 802.11bg 
Mode:Master 
Frequency:2.412 GHz (Channel 1) 
Encryption key:off 
Bit Rates:54 Mb/s 
Quality=99/100 
Signal level=67/100
```

Additionally, the connection only holds up for a short while and then drops. The connection manager shows the connection being activated and then immediately being deactivated. So, I don't know if the issue is actually the card or USB dongle, or if the wireless router is failing. Is there anything I can do to figure this out?

Thanks.

---

### Post by DhrSchap on 2014-05-17
You can trying setting the wifi router to another channel. Channel 1 is usually default so there may be a lot of interference from neighbours

---

### Post by rwwood on 2014-05-17
I'll try that, but my nearest neighbor is at least 100 yards away and I only rarely get a signal from their router.

Well, for whatever reason, that seems to have improved the situation. The diagnostics are no different as far as signal strength, etc, but the connection has been up for a couple of hours and through a reboot without a problem.

Thanks.

---

