---
title: "dropping WiFi connection Ubuntu 20.04 &gt;&gt; potential bypass solution?"
date: 2021-10-14
forum: Networking &amp; Wireless
---

### Post by fortifor44 on 2021-10-14
hi all,

For close to two years I have been suffering from an unstable/dropping wifi connection because of, I suppose, my network adapter (see for full details below). Like a pebble stone in your shoe, it was hard to live with, but bearable. I 'just' need to turn on/off airplane mode every so often and then wifi is back on. Still it is a horrific relationship, so I want a divorce. 

Searching for, and applying solutions over the past two years haven't come up with any results. This apart from that your last name needs to be Einstein if you are going through these tutorials to try to solve the issue. Last night I woke up with this miraculous idea (Einstein indeed isn't my last name): **An USB wifi adapter should bypass this whole issue!** 

So, what are your thoughts before I enter the operating theatre: Could this kind of device bypass both my issue AND the original Qualcomm Atheros QCA9377 adapter? If yes, could you girls and boys recommend me (1) what to purchase exactly, (2) should I disable the QCA9377 then in Ubuntu and if yes, how? (3) Anything else I haven't overlooked?

**my system details: Acer Aspire 3 A315-54-52UL, with Wireless Network Adapter: Qualcomm Atheros QCA9377 802.11ac, dual boot Windows 10 and Ubuntu 20.04**

If this works, this would help out not only me, but all the other blister sufferers out there!

so: thanks in advance!

---

### Post by mIk3_08 on 2021-10-14
can you post the result here in thread wrap with code for the result of this command below.
```
nmcli general
```
```
nmcli dev wifi list
```
```
nmcli dev status
```
```
sudo iwconfig wlp2s0
```
this could be a lot of commands but it might help to those people here in the community to make it more easy  to them to identify the issue of your device.
Regards and Welcome to Linux Ubuntu Forum.

---

### Post by fortifor44 on 2021-10-14
As requested (some of your requests were double):


```
nmcli general
```

STATE      CONNECTIVITY  WIFI-HW   WIFI      WWAN-HW   WWAN     
conectado  total         activado  activado  activado  activado 



```
nmcli dev wifi list
```

IN-USE  BSSID              SSID                   MODE   CHAN  RATE        SIGNAL  BARS  SECURITY    
38:35:FB:31:DE:62 WiFi-5.0-DE5B          Infra  100   540 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA2        
38:35:FB:31:DE:61 WiFi-2.4-DE5B          Infra  6     130 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2        
*       38:35:FB:2D:3C:E0  WiFi-2.4-3CDA          Infra  1     130 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2        
        38:35:FB:2D:3C:E1  WiFi-5.0-3CDA          Infra  100   540 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2        
2C:79:D7:65:F3:EE WiFi-2.4-F3E8          Infra  6     130 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2  


```
nmcli dev status
```

DEVICE          TYPE      STATE          CONNECTION    
wlp1s0          wifi      conectado      WiFi-2.4-3CDA 
p2p-dev-wlp1s0  wifi-p2p  desconectado   --            
enp2s0          ethernet  no disponible  --            
lo              loopback  sin gestión    --   


```
sudo iwconfig wlp2s0
```

wlp2s0    No such device

---

### Post by mIk3_08 on 2021-10-15
> **fortifor44 said:**
> As requested (some of your requests were double):
Can you please run this command below:
```
dmesg
```
Just paste the result here wrap with code. Thanks

---

### Post by fortifor44 on 2021-10-15
```
dmesg
```

not sure what you are looking for, but that results in an amount information comparable with the contents of the Oxford dictionary.


Any thoughts on my bypass solution?

---

### Post by chili555 on 2021-10-15
> **fortifor44 said:**
> ```
dmesg
```

not sure what you are looking for, but that results in an amount information comparable with the contents of the Oxford dictionary.


Any thoughts on my bypass solution?He really wants:

```
sudo dmesg | grep -e wlp -e ath

```Is your router set to a fixed channel or autoselect? Fixed is strongly preferred.

---

### Post by morrownr on 2021-10-16
> **fortifor44 said:**
> hi all,

For close to two years I have been suffering from an unstable/dropping wifi connection

**An USB wifi adapter should bypass this whole issue!** 



I don't want to see you suffer and it can be handy to have a good usb wifi adapter around anyway:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

That site will give you a LOT of information about usb wifi adapters and it has many links to adapters that work with in-kernel drivers. If you have specific capabilities or price range in mind I can probably help.

Good luck

---

### Post by mIk3_08 on 2021-10-16
> **fortifor44 said:**
> ```
dmesg
```
not sure what you are looking for, but that results in an amount information comparable with the contents of the Oxford dictionary.
Any thoughts on my bypass solution?
yes. its normal as it will give us the result of all your usb devices attach in your system hardware and it will also show us your wifi device information and etc.

---

