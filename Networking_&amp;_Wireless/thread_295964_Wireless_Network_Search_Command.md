---
title: "Wireless Network Search Command?"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by gustolove on 2006-11-08
just wondering if there is a command to search for wireless networks...


i use the ```
sudo iwconfig essid "SSID" enc "encryption" 
```
to configure my wireless because i did not like the tool that was installed at first to search and configure the wireless.

please help i need to scan for networks!

---

### Post by calx on 2006-11-08
Checkout wifi-radar or kwifimanager, they are in the repos.

---

### Post by gustolove on 2006-11-08
i guess the kwifimanager will work but i was wondering if there was a console command to scan for networks...

bleh oh well..

---

### Post by jakethesnake on 2006-11-08
> **gustolove said:**
> just wondering if there is a command to search for wireless networks...


i use the ```
sudo iwconfig essid "SSID" enc "encryption" 
```
to configure my wireless because i did not like the tool that was installed at first to search and configure the wireless.

please help i need to scan for networks!
I've got a question for you what does that code do?
I'm gettting an error for wireless request ....

---

### Post by gustolove on 2006-11-08
that command is made to configure the wireless device...

i forgot the whole line.. it is

```
sudo iwconfig ra0(youradaptername) essid SSID(the network name u want to connect to) enc 1234567890(your wep encryption for the network)
```

so it should look something like this:

```
sudo iwconfig ra0 essid MYNETWORK enc 2134784497
```

---

### Post by LeslieL on 2006-11-08
Try 
     iwlist scan
to get a list of available wireless networks.

---

### Post by jakethesnake on 2006-11-09
That's strange when I use the ```
sudo iwconfig ra0 essid MYNETWORK enc 2134784497
```
Of course using my essid and wep encrypted key

I get
```
Error for wireless request "Set ESSID" (8B1A)  :
   SET failed on devise ra0 ; No such device.
```

I haven't been able to get my connection running with my wireless network since I installed ubuntu. Just looking for some help.

---

