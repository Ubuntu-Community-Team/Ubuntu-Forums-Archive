---
title: "whether its ra0 or wlan0...and how to?"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by dreamerchawla on 2007-12-25
how to  know whether the card im using supports ra0 or wlan0 for connecting to the internet.....?????
im using ubuntu 7.10 and from the time i have installed it i have been trying to make wireless work on it but no success  till now. 

when it boots up ,then for sometime it shows the available networks available and asks for passphrase twice but thats it after that nothing happens .

its not getting connected and after sometime the available networks vanish too.......


can somebody show a way out of this please!!!!!!!!!!!!!!!!!!!!!!!!!! 

my card is DWL-G510 (rev.C)

---

### Post by dreamerchawla on 2007-12-26
hello!!!!
does anybody have the solution
i have done almost everything given in the posts regarding this ..... installed driver 
used ndiswrapper 
changed interfaces file but still no go

---

### Post by tiachopvutru on 2007-12-26
According to here:
[http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)
Your wireless device should work with a native driver so you probably don't need ndiswrapper. (since both the wireless adapters I have so far require ndiswrapper, I don't know how they differ)

As for what interface you should use, since it uses Ralink chipset, I'm pretty sure it's ra0, but type this into the terminal, but make sure your adapter is functioning properly first:

```
lshw -C network
```

find something like "description: Wireless Interface", then look down a few lines and check for "logical name"

---

### Post by dreamerchawla on 2007-12-26
lshw -C network


when i use this command then it returns something like 
no wireless interface  :(

i have used ra0 driver but when i give command for scanning then message comes 

device not found .....or something like that only

---

