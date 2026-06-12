---
title: "How to transfer all wifi connections to new laptop"
date: 2018-03-21
forum: Networking &amp; Wireless
---

### Post by matrooswolf on 2018-03-21
Hi,

I just got a new laptop from work. Is there a way to transfer all my wifi connections from the old laptop (ubuntu 16.04.3 LTS) to my new one (Ubuntu 17.10).

I travel a lot, so I have hundreds of connections with stored passwords, from hotels, universities, bars, etc... I could of course look up all the connections and the passwords one by one, but that is very tedious. Is there a way to transfer them all at once?

---

### Post by hrsetrdr on 2018-03-21
Only thing I can think of is taking your exported browser data(in an HTML file) and copy to a USB stick, then transfer to your new setup.  But, to my knowledge that would only work with Chrome browser.

---

### Post by matrooswolf on 2018-03-21
Thank you hrsetrdr, but I'm not talking about browser settings, but about my stored wifi connections...

---

### Post by Hadaka on 2018-03-21
Hi all the connections and passwords should be in..

/etc/NetworkManager/system-connections

To Copy, you must be at root level..
```
sudo su
cp /etc/NetworkManager/system-connections/*
exit 0
``` 
To view connection...
```
sudo cat /etc/NetworkManager/system-connections/[COLOR=#ff0000]**ssid-name**[/COLOR]
```
Does that work for you ?

---

### Post by matrooswolf on 2018-03-22
Thank you Hadaka, 

I will try it this afternoon. But a quick question: isn't the mac-address stored in each of the ssid-name settings. So, if I just copy them, will I have to manually change the mac-address in each ssid-name setting? (There are more then hundred ssid's...)

---

### Post by Hadaka on 2018-03-22
Hi, to change the Wifi MAC address from the old computer to the new computer connections file.
First issue this command to each computer and get the Wifi card address.
```
ifconfig | awk '{if (/Bcast/){print x}x=$5}'
```
Then on the new computer AFTER copying the files over, simply do a substitution with sed.
```
#sudo sed -i 's/OLD-Mac-Address/NEW-Mac-Address/g' /etc/NetworkManager/system-connections/*
```
#Example.
```
sudo sed -i 's/00:11:22:33:44:55/AA:BB:CC:DD:EE:FF/g' /etc/NetworkManager/system-connections/*
```
~OR~ Use your favorite editor [ROOT] and do a find and replace.
Hope that helps.

---

### Post by matrooswolf on 2018-03-23
Hi  Hadaka,

That worked. Thanks.

The ifconfig command didn't work by the way. I first had to install net-tools because ifconfig was not installed. But even then the command returned a blank. But I looked up the mac-address in one of the ssids.

But the sudo sed command did work and replaced all the mac-addresses. So thanks.

But I do think there should be an easier way to do this. I suppose I'm not the only one replacing an old laptop and wanting to transfer all my wifi connections...

---

### Post by Hadaka on 2018-03-23
Hi , please accept my apology for being unaware that IFCONFIG command
is not valid in Ubuntu 17.10. The current method is to use the ' IP ' command.
#Ref-information and ip commands...
[https://insights.ubuntu.com/2017/07/07/if-youre-still-using-ifconfig-youre-living-in-the-past](https://insights.ubuntu.com/2017/07/07/if-youre-still-using-ifconfig-youre-living-in-the-past)
Thank you for marking your thread Solved.

---

