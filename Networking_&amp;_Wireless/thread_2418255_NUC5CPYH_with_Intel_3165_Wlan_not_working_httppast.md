---
title: "NUC5CPYH with Intel 3165 Wlan not working: http://paste.ubuntu.com/p/q5FjkfnKBX/"
date: 2019-05-04
forum: Networking &amp; Wireless
---

### Post by zgadgeter on 2019-05-04
Hello,
i have above system and have searched the net for a solution, finding many claims but no success. Nothing has worked so far.
I've followed bapoumba directions and have created the wireless-info.txt file at the link above.
Perhaps someone can give me some help here?
Thanks.

---

### Post by praseodym on 2019-05-04
Put the /etc/network/interfaces to normal via
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
Reboot.

BTW: That is one line, you better c/p it

---

### Post by zgadgeter on 2019-05-04
Hello and thanks for the help.
I've done this and received the following:
```
auto loiface lo inet loopback

```
Then tried to configure the adapter with the following:
```
sudo iwconfig wlp2s0 essid TBH enc s:XXX
```
and tried this:
```
sudo iwconfig wlp2s0 essid TBH enc XXX

```
and this:
```
sudo iwconfig wlp2s0 essid TBH key XXX

```
But usually get the error:
```
invalid arguement
```
Any chance i'm doing something obvious wrong?
thanks again.

---

### Post by praseodym on 2019-05-04
The output should be 2 lines
```

auto lo
iface lo inet loopback
```

Open that file and correct it, if applicable
```

gksudo gedit /etc/network/interfaces
```
Save and reboot

---

### Post by zgadgeter on 2019-05-04
Hello, sorry i did not format the responce correctly, i did in fact get this as an output:
```
[COLOR=#000000][FONT=&amp]auto lo
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]iface lo inet loopback[/FONT][/COLOR]
```

My interfaces file has following content:

```
auto lo
iface lo inet loopback
```

Anything else i can try?
thanks.

---

### Post by praseodym on 2019-05-05
Why dont you use the network manager?

---

### Post by zgadgeter on 2019-05-05
> **praseodym said:**
> Why dont you use the network manager?
I did attempt that, but likely did it wrongly. Is there somewhere (tutorial) on how to do it? Or maybe just some brief instructions?
Thanks.

---

### Post by chili555 on 2019-05-05
> sudo iwconfig wlp2s0 essid TBH enc s:XXXThis implies that you are using WEP, not WPA2 and that the encryption key is a WEP passphrase. I highly doubt that that is what you intend.

> I did attempt that, but likely did it wrongly. Is there somewhere (tutorial) on how to do it? Or maybe just some brief instructions?
Thanks.Usually, you click the icon, see your network, select it and supply the WPA2 password and connect.

We notice this: > 
TBH7590            <MAC 'TBH7590' [AC1]>  Infra  6     2437 MHz  260 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no             
TBH7590            <MAC 'TBH7590' [AC7]>  Infra  116   5580 MHz  540 Mbit/s  95      &#9602;&#9604;&#9606;&#9608;  WPA2      no             

Your router has the 2.4 gHz and the 5 gHz segments with the same SSID or name; i.e. TBH7590. When you connect, your device will likely roam (disconnect and reconnect) between them. I recommend that you rename at least one of them; for example TBH7590_2.4.

---

