---
title: "WPA helped needed"
date: 2005-06-03
forum: Networking &amp; Wireless
---

### Post by alastair lewis on 2005-06-03
I have finally sorted out the wireless connection (thanks to this forum and its users)but only with encription turned off.

I am having problems with the wpa_supplicant.conf file.
```
sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && dhclient wlan0
```

returns

failed to read /etc/wpa_supplicant.conf

I do not want to go back to WEP (a couple of horror stories in the UK recently, probably urban myths, but...)

---

### Post by az on 2005-06-03
[http://test.wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA](http://test.wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA)

Is this what you have already tried?

---

### Post by alastair lewis on 2005-06-04
[QUOTE=azz][http://test.wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA](http://test.wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA)

Is this what you have already tried?[/QUOTE]
 Yep. That is where the first code came from. All my Ubuntu progress has come from thses fora.

What next?

---

### Post by dawizard on 2005-06-05
[QUOTE=alastair lewis]
failed to read /etc/wpa_supplicant.conf
[/QUOTE]

Does that file exist? Does it have the right permissions? Did you check that the syntax of the configfile is correct?

---

### Post by alastair lewis on 2005-06-05
[QUOTE=dawizard]Does that file exist? Does it have the right permissions? Did you check that the syntax of the configfile is correct?[/QUOTE]
 I t does exist. i created it and chmod 600'ed it.
```
cd /etc
ls -l
```
tells me /etc/wpa_supplicant has -rw------- access and root ownership

as the command was run as rsuperuser I would expect it to work.
I plan to revisit the original wpa_supplicant file and the wiki before resorting to WEP.
I would be gratefull for any pointers prior to this.

---

