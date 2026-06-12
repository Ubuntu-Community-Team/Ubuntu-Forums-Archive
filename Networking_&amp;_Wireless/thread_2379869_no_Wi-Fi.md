---
title: "no Wi-Fi"
date: 2017-12-10
forum: Networking &amp; Wireless
---

### Post by spacecadettopps on 2017-12-10
So I'm new to Ubuntu and actually just decided to make the leap. 
Well for some reason my Wi-Fi isn't working and I'm not sure why.

---

### Post by jeremy31 on 2017-12-11
*Thread moved to **Networking & Wireless**.*
Please see the wireless script link in my signature and post results

---

### Post by spacecadettopps on 2017-12-11
is this what you're looking for?
33
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.184.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16828 (16K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  16.43K  --.-KB/s    in 0.04s   

Last-modified header missing -- time-stamps turned off.
2017-12-11 20:46:04 (393 KB/s) - ‘wireless-info’ saved [16828/16828]

[sudo] password for anon: 

Results saved in "/home/anon/wireless-info.txt".

Do you also want to post them to your default 'pastebinit' provider? [Y/n]: y

Pastebin successful:

[http://paste.ubuntu.com/26167327/](http://paste.ubuntu.com/26167327/)

anon@anon:~$ clear

anon@anon:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
> chmod +x wireless-info && \
> ./wireless-info
--2017-12-11 20:46:33--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 192.30.253.113, 192.30.253.112
Connecting to github.com (github.com)|192.30.253.113|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2017-12-11 20:46:33--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.184.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.184.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16828 (16K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  16.43K  --.-KB/s    in 0.04s   

Last-modified header missing -- time-stamps turned off.
2017-12-11 20:46:34 (375 KB/s) - ‘wireless-info’ saved [16828/16828]


Results saved in "/home/anon/wireless-info.txt".

Do you also want to post them to your default 'pastebinit' provider? [Y/n]: y

Pastebin successful:

[http://paste.ubuntu.com/26167329/](http://paste.ubuntu.com/26167329/)

---

### Post by jeremy31 on 2017-12-12
Go into BIOS/UEFI settings and disable secure boot as it prevents the module from loading that is needed for wifi

---

### Post by spacecadettopps on 2017-12-12
Dude you're awesome! Thank you so much! My Wi-Fi is working again

---

