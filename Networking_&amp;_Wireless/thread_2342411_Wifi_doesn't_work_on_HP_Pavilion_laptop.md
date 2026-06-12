---
title: "Wifi doesn't work on HP Pavilion laptop"
date: 2016-11-06
forum: Networking &amp; Wireless
---

### Post by dtommy79 on 2016-11-06
Hi,

I have a HP Pavilion 15-ab208nh Notebook and I can get the Wifi to work on it. 

The strange thing is that it works when I put the laptop right next to the router, but when I take it a few meters away from it, the connection dies. 

I'm sure it's not the router, becuase with my other laptop it works fine. 

I also bought a [Wireless-N USB Adapter]("https://www.amazon.com/RELPER-300Mbps-Wireless-Network-Internet/dp/B00UJEOTXQ/ref=sr_1_1?ie=UTF8&qid=1478441857&sr=8-1-spons&keywords=Wireless-N+USB+Adapter&psc=1") (300Mbps), but I'm not sure how to install it. 

Any help is appreciated

---

### Post by kc1di on 2016-11-06
hi dtommy79 , 
Can you go to a terminal and type this command and post the results here so we can see what your dealing with?
```
inxi -F
```

---

### Post by dtommy79 on 2016-11-07
Hi, 

Thanks for the reply.

It says:
> The program 'inxi' is currently not installed. You can install it by typing:
sudo apt install inxi

should I install it?

---

### Post by Hadaka on 2016-11-07
Hi, please connect your computer with a wired connection to your router and then
copy and paste...
```
sudo apt-get update
sudo apt-get dist-upgrade
rfkill unblock all
```
Then please copy,paste and post the output off..
```
lspci -n | awk '/0200|0280/{print$3}'
```
thanks.

---

### Post by kc1di on 2016-11-07
I would go ahead and install it.  It good to have.  Strange I thought it was installed by default.  

Which version are you running?

Also Hadaka's suggestion is a good one.

---

### Post by dtommy79 on 2016-11-07
This is the result:

10ec:b723
10ec:8136

---

### Post by Hadaka on 2016-11-07
Hi your first post you state..
"The strange thing is that it works when I put the laptop right next to  the router, but when I take it a few meters away from it, the connection  dies."

This is because your wireless card [10ec:b723] rlt8723be has 2 wifi antenna connections and is set to the incorrect one.
please go here...
[http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904](http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904)
and do [COLOR=#ff0000]only [/COLOR]the commands to select the antenna.
Start where it says...
'Reboot and then'
```
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be ant_sel=1
```

If you have any questions or are unsure, dont issue any commands..just post back your concerns.
*Be sure to remove the usb wifi.
thanks.

---

### Post by dtommy79 on 2016-11-07
Thank you, thank you.... :)

It worked like charm

---

### Post by Hadaka on 2016-11-07
Great ! glad that worked for you.
Please log back in to your first post of the thread,
click **Thread Tools **and then select **Solved**.
this will help searchers.
Thanks.

---

### Post by dtommy79 on 2016-11-08
There is one issue still remaining. I have to run those commands everytime I turn on my laptop.

---

### Post by Hadaka on 2016-11-08
Hi, did you do this command??
```
echo "options rtl8723be ant_sel=[COLOR=#ff0000]X[/COLOR]" | sudo tee /etc/modprobe.d/rtlbtcoex.conf
```

First replace [COLOR=#ff0000]X [/COLOR]with 1 and test...if it drops when you move away from the router....issue the command again
and change it to 2

please copy and paste the command but change the [COLOR=#ff0000]X [/COLOR]to either 1 or 2

*Note...it is usually 2..please try that first.
thanks

---

### Post by dtommy79 on 2016-11-08
Darn.. yeah that was the problem. Thanks

---

