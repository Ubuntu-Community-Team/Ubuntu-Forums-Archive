---
title: "Wifi unable to connect after failed docer install attempt"
date: 2020-09-26
forum: Networking &amp; Wireless
---

### Post by Crazy01 on 2020-09-26
Hi,
I tried to install docker on my Ubuntu but unfortunately it was failed. After that, my wifi connect on start abut after few minutes, it's disconnect and don't show any WiFi option. 
I am providing my network info as follows:

[https://pastebin.com/wJ05Sj1R](https://pastebin.com/wJ05Sj1R)

I am unable to do anything as have only one syatem which is Laptop with Ubuntu,

---

### Post by CelticWarrior on 2020-09-28
Docker as nothing to do with WiFi.
And providing a password protected results file is obviously of no use.

---

### Post by Crazy01 on 2020-10-04
> **CelticWarrior said:**
> Docker as nothing to do with WiFi.
And providing a password protected results file is obviously of no use.

My bad, please find public  file:
[https://pastebin.com/wJ05Sj1R](https://pastebin.com/wJ05Sj1R)

---

### Post by CelticWarrior on 2020-10-04
Once again, no idea why you're even mentioning Docker at all.

The problems are:
[LIST=1]
[*]A crappy WiFi chip - RTL8723BE - know to have lots of problems in Linux and often requiring additional parameters regarding antenna selection to work properly. Google about it +Ubuntu and you find lots of information and things to try. Please note the Ubuntu release matters as things have changed over time.
[*]At the router AP you have mixed mode WPA/WPA2. It should be **WPA2 only**
[*]Also at the router you're using an old, extremely insecure and deprecated YEARS ago encryption method - TKIP -. It should be **AES/CCMP**
[*]Other settings may need adjustments.
[/LIST]

---

