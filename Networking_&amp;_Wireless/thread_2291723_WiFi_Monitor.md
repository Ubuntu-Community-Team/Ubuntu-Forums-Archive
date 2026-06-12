---
title: "WiFi Monitor"
date: 2015-08-22
forum: Networking &amp; Wireless
---

### Post by cressrt2 on 2015-08-22
We get our internet via a WiFI link due to our very rural location. It is usually good but can be intermittent at times, I am looking for some sort of monitor that can record and display the connection history so I can prove to our supplier when it is bad. I have had a look in the Software centre but not rally sure what I need.
Any suggestions please, I am running 14.04.

---

### Post by Frogs Hair on 2015-08-22
A terminal based utility is wavemon , but may not work with all proprietary wireless drivers. ```
sudo apt-get install wavemon 
``` Then, run the start command and use the F keys to retrieve history  ```
wavemon
```

---

### Post by cressrt2 on 2015-08-22
I have installed and loaded it, but it appears only to give live data, I cannot see how it can record or display historic data?

---

### Post by Frogs Hair on 2015-08-22
I don't think it will display anything prior to installing the application , but as I recall F2 opens the history screen.

---

