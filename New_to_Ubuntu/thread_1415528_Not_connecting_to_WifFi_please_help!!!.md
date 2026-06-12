---
title: "Not connecting to WifFi? please help!!!"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by yourcat on 2010-02-24
Ok soI start up my laptop (dell latitude D600) and log in. I click on the icon displaying the Network connections and 2 things pop up. The wired connection (which is disconnected) and the VPN connections. there is no wireless connection. 
 
can someone help me out here?

---

### Post by xxterry1xx on 2010-02-24
> **yourcat said:**
> Ok soI start up my laptop (dell latitude D600) and log in.  I click on the icon displaying the Network connections and 2 things pop up. The wired connection (which is disconnected) and the VPN connections. there is no wireless connection. 
 
can someone help me out here? because wireless driver is not installed go to terminal and LSPCI and copy it here

---

### Post by yourcat on 2010-02-24
Yeah i did that previouly and this came up
 
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Controler (rev 02) 
 
I private messaged someone and they told me a code. is it possible that it undid the driver? note it did not work yet in the first place unless i use a wired network
 
 
the code he told me was
 
sudo apt-get update && sudo apt-get install bcmwl-kernel-source

---

### Post by yourcat on 2010-02-24
sorry i spelled WiFi wrong with 2 f's

---

### Post by yourcat on 2010-02-25
can anyone help me with this

---

### Post by joshd2189 on 2010-02-25
1) do you have wired internet access?

2) what was the output of installing bcmwl-kernel-source?

have a read here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

since you have the bcm4306, try to run this command (you need to have wired internet):
```
sudo apt-get install b43-fwcutter
```

go to System -> Administration -> Hardware Drivers and enable it if needed

you may have to reboot somewhere along the line

---

### Post by yourcat on 2010-02-25
it says b43-fwcutter is installed to the newest version. i then went to hardwear drivers and
 there is nothing there

---

### Post by bkratz on 2010-02-25
YOUR CARD IS A BCM4306 REV 2, OR ONLY HAS 802.11B CAPABILITY, IT USES
B43LEGACY---the fw-cutter takes care of this also. I think if you look at the last half of this page it will help you.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

