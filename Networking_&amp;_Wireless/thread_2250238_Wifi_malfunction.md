---
title: "Wifi malfunction"
date: 2014-10-27
forum: Networking &amp; Wireless
---

### Post by claraB.E on 2014-10-27
My wifi goes batshit crazy (on and off, asks for password, doesn't "see" the conexion...) on a daily basis. I've pasted the diagnosis wireless-info.txt so that someone can tell me what to do, because I have no idea how to fix it... I don't even know what the problem is.

[http://pastebin.ubuntu.com/8707662/](http://pastebin.ubuntu.com/8707662/)

---

### Post by kc1di on 2014-10-27
Hi claraB.E and welcome to Ubuntu,
Your wireless card is a little problematic at times. [ Here is a page ]("http://www.htpcbeginner.com/how-to-fix-atheros-ar9285-ar9287-wireless-problems-in-ubuntu-1104/")that may be of help. 
good luck :)

---

### Post by chili555 on 2014-10-27
@claraB.E- I would suggest you try the parameter that was linked. If, after a reboot, it is still not performing well, we'll dig deeper.

---

### Post by wildmanne39 on 2014-10-27
Hi, the wl driver is also loaded, so I believe it is conflicting.
Do:
```
sudo apt-get purge bcmwl-kernel-source
```

---

### Post by Hadaka on 2014-10-27
and.....TKIP is glaring in your router definitions,
please access your router..192.168.10.1 and change
to WPA2 CCMP no tkip. also change to channel 1 or 11
thanks.

---

### Post by claraB.E on 2014-11-03
I still have the same issues, I did everything except the TKIP thing because I didn't know if I should, seems dangerous.

---

### Post by chili555 on 2014-11-03
> **claraB.E said:**
> I still have the same issues, I did everything except the TKIP thing because I didn't know if I should, seems dangerous.He is not suggesting that you change the setting in the router from WPA2-TKIP to no security at all; he is suggesting, and I completely agree, that you change from WPA2-TKIP to the even *more *secure WPA2-AES. [https://en.wikipedia.org/wiki/Advanced_Encryption_Standard](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)

Please see: [http://i.imgur.com/RWmvGmq.jpg](http://i.imgur.com/RWmvGmq.jpg) In this example, we recommend that AES _only_ be selected as it is more secure and is quite often easier to get connected. Then reboot the router and tell us if performance is improved.

---

### Post by claraB.E on 2014-11-05
Ok, I did everything and I still have issues, I ran the diagnosis script again, here it is:

[http://pastebin.ubuntu.com/8837871/](http://pastebin.ubuntu.com/8837871/)

Thank you again for the help, Idk what I'd be doing without you people.

---

### Post by jeremy31 on 2014-11-05
Can you reboot and run the script again?```
./wireless_script
```

---

### Post by chili555 on 2014-11-05
We also notice that the router is still set to WPA and WPA2 mixed mode and not purely WPA2, which we recommend.

---

### Post by claraB.E on 2014-11-08
I haven't got that option, I have WEP, WPA/WPA2 - Enterprise and WPA/WPA2 - Personal. If it's not in wireless security, then I don't know where It can be.

---

### Post by claraB.E on 2014-11-08
Sorry, I forgot, I ran the script and this is the result

[http://pastebin.ubuntu.com/8890717/](http://pastebin.ubuntu.com/8890717/)

---

### Post by Hadaka on 2014-11-08
Hi, it's lookig much better but you still have a couple items that
need adjusting, click your network mgr. and edit your connection
to look like the attached,
[ATTACH=CONFIG]257835[/ATTACH][ATTACH=CONFIG]257836[/ATTACH]
then copy and paste these commnds into a terminal
```
sudo sed -i s'/false/true/' /etc/NetworkManager/NetworkManager.conf
sudo sed -i 's/"REGDOMANIN=00"/"REGDOMANIN=BG"/' /etc/default/crda
sudo iw reg set BG
```
boot and post a new script file please
thanks

---

### Post by claraB.E on 2014-11-13
Ok, did that and this is the result:

[http://pastebin.ubuntu.com/8988064/](http://pastebin.ubuntu.com/8988064/)

---

