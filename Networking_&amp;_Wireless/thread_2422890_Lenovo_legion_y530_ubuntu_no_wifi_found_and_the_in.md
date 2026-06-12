---
title: "Lenovo legion y530 ubuntu no wifi found and the internet is very slow."
date: 2019-07-14
forum: Networking &amp; Wireless
---

### Post by phanthaiduong22 on 2019-07-14
As the tittle. I have this problems.
I tried this about 4 days ago.
"
sudo apt-get install build-essential dkms git
git clone -b 4.18 [https://github.com/jeremyb31/ideapad-laptop.git](https://github.com/jeremyb31/ideapad-laptop.git)
sudo dkms add ./ideapad-laptop
sudo dkms install ideapad-laptop/1.0
echo "options ideapad_laptop override_has_hw_rfkill_switch=0" | sudo tee /etc/modprobe.d/ideapad_laptop.conf"

it worked .But now, no wifi adapter found again.

By the way. Sometimes, The internet will be very slow after not using the internet about 10 minutes.

Some one said that because of the wifi driver of lenovo. And recommend me buy intel 9560 . But in window, it works very well.

Does anyone have idea?

Thanks a lot.

---

### Post by jeremy31 on 2019-07-14
See the wireless script link in my signature and post results, also post results from terminal for ```
dkms status
```

---

### Post by phanthaiduong22 on 2019-07-15
dkms staus return:
```

ideapad-laptop, 1.0, 4.18.0-25-generic, x86_64: installed
nvidia, 390.116, 4.18.0-25-generic, x86_64: installed

```
and here is wireless script:
```

http://paste.ubuntu.com/p/4B8SsRSC7s/

```

---

### Post by praseodym on 2019-07-15
Run

```
sudo apt-get install git build-essential dkms linux-headers-$(uname -r)
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
Reboot

---

### Post by phanthaiduong22 on 2019-07-16
It still not found.so i have to use lan to connect the internet. but it is still slow interne
[IMG]https://i.postimg.cc/c4rBDYpn/Screenshot-from-2019-07-16-15-07-22.png[/IMG]

And the internet still slow like this.

Image : [https://postimg.cc/Fffr4ZST](https://postimg.cc/Fffr4ZST)

And i notice that. When i just open the laptop ,the internet is good. But after not using the internet. Like coding (don't need internet) it becomes so slow. Furthermore, reload facebook page so fast but the others.

---

### Post by phanthaiduong22 on 2019-07-16
It still not found. so i have to use lan to connect the internet. but it is still slow internet<br>
<img src="https://i.postimg.cc/c4rBDYpn/Screenshot-from-2019-07-16-15-07-22.png" alt="" border="0"><br>
<br>
And the internet still slow like this.<br>
<img src="https://postimg.cc/Fffr4ZST" alt="" border="0"><br>
<br>
And i notice that. When i just open ,the internet is good. But after not using the internet. Like coding (don't need internet) it becomes so slow. Furthermore, reload facebook page so fast but the others.

---

### Post by praseodym on 2019-07-16
Please run the wireless script again

---

### Post by phanthaiduong22 on 2019-07-17
Sorry.
```
http://paste.ubuntu.com/p/rt8d6V8PmT/
 
```

---

### Post by praseodym on 2019-07-17
Lets try

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by phanthaiduong22 on 2019-07-18
It still not found wifi. 
```
http://paste.ubuntu.com/p/Z5Z22bMr4j/
```

---

