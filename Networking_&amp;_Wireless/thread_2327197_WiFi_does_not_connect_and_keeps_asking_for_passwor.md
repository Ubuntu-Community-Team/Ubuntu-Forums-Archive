---
title: "WiFi does not connect and keeps asking for password"
date: 2016-06-08
forum: Networking &amp; Wireless
---

### Post by Neal_Gosalia on 2016-06-08
Hey everyone, new to the forums here and fairly new to ubuntu :)
My wifi was working initially after I installed Ubuntu but now it just does not connect. Wired internet works fine. Though I face this problem on all the linux distros I have tried (Linux Mint 17.3, Elementary OS Freya and a few others).
I have run sudo apt get upgrade and dist-upgrade.
Here is the output from wireless-info script: [http://hastebin.com/lawevevosa.vbs](http://hastebin.com/lawevevosa.vbs)
Please help me :) I went through a lot of other threads but couldn't find a solution~

---

### Post by X-RED_Tech on 2016-06-08
I know I read it somewhere that this device ```
[COLOR=#92A0A0][FONT=monospace]Network controller [[/FONT][/COLOR][COLOR=#2AA198][FONT=monospace]0280[/FONT][/COLOR][COLOR=#92A0A0][FONT=monospace]]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [[/FONT][/COLOR][COLOR=#2AA198][FONT=monospace]10[/FONT][/COLOR][COLOR=#92A0A0][FONT=monospace]ec:b723][/FONT][/COLOR]
``` needs either a different driver, tweaking the settings or both. Also you shouldn't be using TKIP.

That said, I don't see the point in troubleshooting a Ubuntu release that will be out of support in a few weeks. Perhaps you should try a live session with 16.04. Maybe it works better for your hardware and the issues are already corrected.

---

### Post by jeremy31 on 2016-06-08
Change the wifi encryption on the router to WPA2-AES, WPA2-PSK, or WPA2 Personal without enabling TKIP

Is this HP computer less than a year old?  How close is it to the wifi router?

---

### Post by Neal_Gosalia on 2016-06-09
I installed Ubuntu 16.04, but since I have an exam tomorrow, I will report back tomorrow once I am free. I will change it to WPA2-PSK(AES). And yes, my laptop is less than a year old. Bought in on Feb 29th :) Thank you for all the help!

EDIT: I am really close to the wifi router. Like 2 feet away from it.

---

### Post by Neal_Gosalia on 2016-06-09
Okay, I was impatient and I generated the wireless-info text. Here it is: [http://www.hastebin.com/elovuximuj.vhdl](http://www.hastebin.com/elovuximuj.vhdl)
Still problems connecting to WI-Fi. Keeps asking for password. I installed the latest drivers from lwfinger's git :)

---

### Post by jeremy31 on 2016-06-09
Post the result of ```
cd rtlwifi_new
git status
```

---

### Post by Neal_Gosalia on 2016-06-09
> **jeremy31 said:**
> Post the result of ```
cd rtlwifi_new
git status
```
```

On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean


```

---

### Post by jeremy31 on 2016-06-09
I can imagine you installed using the normal make, sudo make install commands.  You likely had a kernel update and the driver is no longer the one from github
```
cd ~
sudo dkms add ./rtlwifi-new
sudo dkms build -m rtlwifi-new -v 0.6
sudo dkms install -m rtlwifi-new -v 0.6
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Reboot and see if it is any better.  This module should give you the option ant_sel if you look at ```
modinfo -p rtl8723be
```

We can use the option to see if one antenna works better than the other
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|quality'
```

Then we can try the second antenna option and compare the results from iwlist scan to see if it is better or worse

```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|quality'
```

If ant_sel=1 had better performance use
```
echo "options rtl8723be ant_sel=1" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
```

If ant_sel=2 was better, then 
```
echo "options rtl8723be ant_sel=2" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
```

And you should be set

---

### Post by Neal_Gosalia on 2016-06-09
Thanks a lot for the help! But unfortunately, I am still facing the problem. I rechecked my Wi-Fi password and forgot the network and re-added it too but no change.
Here's what happened after I ran your commands:
Initially my signal got boosted and I could find more networks but since I still wasn't able to connect to my wifi, I thought I should try rebooting. But after the reboot I lost the signal range too. Then I re-ran the ant_sel=1 set of commands. Now I can see more networks again, but still cannot connect to my Wi-Fi. :(

---

### Post by jeremy31 on 2016-06-09
Run the wireless script again with the setting that gives you the better signal

---

### Post by Neal_Gosalia on 2016-06-09
> **jeremy31 said:**
> Run the wireless script again with the setting that gives you the better signal

[http://www.hastebin.com/ixugukomir.vhdl](http://www.hastebin.com/ixugukomir.vhdl)

---

### Post by jeremy31 on 2016-06-09
That does seem better than the original results, can you set the wifi router encryption to WPA2 only as it still seems to have WPA enabled

---

### Post by Neal_Gosalia on 2016-06-09
[http://www.hastebin.com/rabirojowi.vhdl](http://www.hastebin.com/rabirojowi.vhdl)

---

### Post by Neal_Gosalia on 2016-06-09
Hey! Wi-Fi seems to connect now! Thank you very much! Though is there a way to make those ant_sel lines permanent? Because it would be a pain entering them every time I boot!

EDIT: I seem to have made a modprobe.sh file out of those three commands and placed it in my home folder. That way I can execute it every time I boot. Though if you can give my a permanent fix, it would be great! Also, do point me to the Thanks button if there is any!

---

### Post by jeremy31 on 2016-06-09
If the ant_sel=1 was the better option then

```
echo "options rtl8723be ant_sel=1" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
```

And it will work after a reboot

---

### Post by Neal_Gosalia on 2016-06-09
Its not connecting again :(

---

### Post by Neal_Gosalia on 2016-06-09
[http://www.hastebin.com/vovetitixo.vhdl](http://www.hastebin.com/vovetitixo.vhdl)

EDIT: Its working again :) I had to apply router settings again. I guess it is safe to mark the thread solved for now?

---

### Post by X00btine on 2016-06-12
A [soft reset]("http://www.uukeys.com/reset-windows-8-password-without-disk.html") will solve this problem. I just tested it on my router two days ago.

---

