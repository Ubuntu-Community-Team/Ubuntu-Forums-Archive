---
title: "bsnl wired connection"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by pj pol on 2010-07-26
im a noob and i cant setup the bsnl {internet india} connection using my cable and port

---

### Post by dineshs on 2010-07-26
BSNL broadband or dialup?What modem are you using?How you are connecting in windows?

---

### Post by vaibhav.dkm on 2010-10-01
Hey I have same Problem :
Bsnl internet Connection ( wired ) broadband .
In windows 7 first i enable the LAN then My Compuer > Network > I enable Conexant -IGD  
I m usin ubuntu 10.04

---

### Post by dineshs on 2010-10-03
Pl let us know the model name of your modem.Is it connected via ethernet(LAN card)?If yes pl also post the output of```
sudo lshw -C network
```

---

### Post by vaibhav.dkm on 2010-10-10
My model name is ZXDSL 83A11 . And it is connected by  via ethernet(LAN card) .

---

### Post by anand_30 on 2010-10-10
Try this thread 

[http://ubuntuforums.org/showthread.php?t=1538511](http://ubuntuforums.org/showthread.php?t=1538511)
Even this thread gives is about slow spped its core cause is improper modem configuration.

Hope this helps.

---

### Post by vaibhav.dkm on 2010-10-10
Thanks this forum is really fast

---

### Post by dineshs on 2010-10-10
> My model name is ZXDSL 83A11 . And it is connected by via ethernet(LAN card) . 
DSL modems can be configured in BRIDGE mode or PPPoE mode
_Bridge mode_
If the modem is in bridge mode you need a PPPoE dialler to connect/disconnect internet when required
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
_PPPoE mode_
If the modem is in PPPoE mode the connection will be always ON.Configuring BSNL modems in PPPoE mode is explained [here]("http://ernakulam.sancharnet.in/ernakulam/bbservice.html") under CPE /modem config
If you have any difficulty please let us know.Also post the output of
```
sudo lshw -C network
```and```
ping -c3 192.168.1.1
```and```
ping -c3 4.2.2.1
```

---

