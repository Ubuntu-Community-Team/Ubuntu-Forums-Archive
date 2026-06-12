---
title: "No wifi with Atheros AR9565 network card"
date: 2017-04-18
forum: Networking &amp; Wireless
---

### Post by antoinedba on 2017-04-18
Hello !

I installed ubuntu on my Acer Aspire ES 15 and it works good. 
One of the few issues is that the wifi is not working. My network card is an Atheros AR9565.
I searched the forums and I tried to do what was answered to the people who own the same card but it didn't work. :(

I executed the "wireless info" script and posted it [here]("https://pastebin.com/cZNxWxUs").

I hope someone who knows this problem can help me. 

Thanks for your help,
Antoine

PS : Please excuse my English, I am french (nobody's perfect...)

---

### Post by ajgreeny on 2017-04-18
From your wireless-info output it looks as if your wifi adapter is physically turned off by a hardware switch of some kind.
```
0: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    [COLOR="#FF0000"]Hard blocked: yes[/COLOR]
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```
I have no knowledge of that machine and a quick search has not shown what key combination is used to toggle wifi on/off, but you may be able to find what is needed; often Fn+F# will do it, so try as many as you can and you may be lucky.

---

### Post by kc1di on 2017-04-18
Hello antoinedba and Welcome to Ubuntu,

The rfkill read out in your script run says the both soft and harware blocks are present.
```
##### rfkill ############################
 
0: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
[B][COLOR="#FF0000"]1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes[/COLOR][/B]

```

The soft block you can change by running this code in a terminal ```
rfkill unblock all
```
but the hard block is a machine hardware switch - it may be an f key or combination of keys. or it may be an actual switch on the machine. 
but you'll have to find it and switch it on before your wireless card will be turned on. 
on my laptop (Lenovo) it is the F5 key. But yours will most likely be different.

---

### Post by antoinedba on 2017-04-19
Hi ! Thanks to both for your answers :D
I tried the combination Fn + F3 (there is an antenna on the F3 button) and "rfkill unblock all"

Then, I did "rfkill list all" and here is the result :


```
0: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

It changed the "Soft blocked" line but nothing changed on the "Hard blocked" one.

[U]:idea: - Edit : 
[/U]
I found the solution in [this thread]("https://forum.ubuntu-fr.org/viewtopic.php?id=2006391").
Here is what to do :
```
echo blacklist acer-wmi | sudo tee -a /etc/modprobe.d/blacklist-acer-wmi.conf
```
 and then reboot .

Thanks for your help, 
Antoine[URL="https://forum.ubuntu-fr.org/viewtopic.php?id=2006391"]
[/URL]

---

### Post by kc1di on 2017-04-19
Glad you found the solution, if it fixed it for you please mark this thread as solved. 
Thank You!

---

