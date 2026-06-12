---
title: "How to achieve automatic reconnection"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by O-pos on 2008-04-15
Hello,

We have free wireless here at my work but of low quality, it often drops connection for a short time. Then its'working again, but My Ubuntu does not do anything to reconnect automatically and I have to do it manually. I dislike it very much, especially if I start to download something and leave the room, only to come back later to see that nothing has been done.

Is there any way to make this guy keeping reconnection attempts automatically if it gets disconnected? (I want it to connect to the same and not the other wireless network, though).

Thanks in advance

---

### Post by Paris Heng on 2008-04-16
> **O-pos said:**
> Hello,

We have free wireless here at my work but of low quality, it often drops connection for a short time. Then its'working again, but My Ubuntu does not do anything to reconnect automatically and I have to do it manually. I dislike it very much, especially if I start to download something and leave the room, only to come back later to see that nothing has been done.

Is there any way to make this guy keeping reconnection attempts automatically if it gets disconnected? (I want it to connect to the same and not the other wireless network, though).

Thanks in advance

Honestly I never encounter this kind of problems. You might cache the AP MAC address in the Linux Kernel.

***Examples:***
> iwconfig eth1 ap <MAC Address>

Regards

---

### Post by O-pos on 2008-04-16
I tried, here is the output:

~$ iwconfig eth1 ap <MAC Address>
bash: syntax error near unexpected token `newline'

---

### Post by Siph0n on 2008-04-16
iwconfig eth1 ap <MAC Address>

Instead of eth1 , make sure you use your own interface. You can check this from iwconfig. Also, instead of <MAC Address>, use the mac address of your router. Mine for example is: 00:0F:3D:36:33:57 , and my interace is wlan0

So I would do:

```
iwconfig wlan0 ap 00:0F:3D:36:33:57
```

---

### Post by jelkimantis on 2008-04-16
You might want to ensure that, in network settings, you've selected roaming.  I know that on feisty this never worked right, but it seems to work well enough on Gutsy, and I'm sure there are more improvements on Hardy.

jsl

---

### Post by O-pos on 2008-04-16
the output of iwconfig is:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:19:12:72   
          Bit Rate:2 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/100  Signal level=-67 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1829  Invalid misc:3   Missed beacon:35

I tried and here's what I got:

$ iwconfig eth1 ap 00:1C:10:19:12:72
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device eth1 ; Operation not permitted.

---

### Post by Siph0n on 2008-04-17
try:
```
sudo iwconfig eth1 ap 00:1C:10:19:12:72
```

and btw, I dont know if this will/does work in helping u reconnect, but that is how you can get past that Operation not permitted error.

---

### Post by O-pos on 2008-04-17
But how would it help the computer to keep automatic reconnection attempts after disconnecting?

---

### Post by Siph0n on 2008-04-19
I dont know, that was Paris Heng's suggestion.... Maybe it wont have to search for an AP because it already has it saved? I really don't know tho...

---

