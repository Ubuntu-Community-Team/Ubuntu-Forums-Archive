---
title: "Wireless agony: no connection"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by d3dtn01 on 2007-02-13
Yet another random event happened to throw a wrench into my blissful Ubuntu user experience. The end result of this event was that I had to get a new wireless router. So, I have it working with Windows. Now, I'm trying to get it to work with Ubuntu. In the past, every time I goofed around with the Networking settings, it would take several reboots and random changes to my wireless card's properties to get re-connected. This time, the magic is gone.

Here's what I know:

1. My network card is recognized and so is its driver (I verified these facts with lshw).
2. My router is sending out beacons (I see it in the list of networks when I run iwlist).

I'm using the Network Settings gui app to attempt to connect. I have entered my essid and my password correctly in the properties section. Automatic configuration is selected. Under DNS servers, 192.168.0.1 was originally listed. My first attempt to connect failed. So I deleted the DNS server listed and tried to connect again. This did not work. I have rebooted several times (the magical step that frequently worked in the past), but still no success. 

I've been trying to connect just using commands in the terminal, but I can't seem to get the syntax right. For instance, here are some of the commands I tried (the essid and key are just random, not the actual ones I use):

```
sudo iwconfig wlan0 essid meatloaf ap 00:18:39:C2:1D:BE key 4203243234e4242f mode Managed commit
```
```
sudo iwconfig wlan0 essid meatloaf key 4203243234e4242f mode Managed commit
```
```
sudo iwconfig wlan0 essid meatloaf key open 4203243234e4242f mode Managed commit
```

Where do I go next?

---

### Post by MCSE_Crossover on 2007-02-13
Along with configuring your ESSID, ensure that bitrate is configured correctly. I know that I personally have had to configure my "ndiswrapper" configured wireless card to recognize my wireless router as being 11M and not 54M.

Also, if you are using DHCP, I would execute a "sudo dhclient" after you ensure that all of your other settings are correct. This will prompt your wireless card to poll for a DHCP broadcast.

---

### Post by d3dtn01 on 2007-02-13
Thanks for the suggestion. I tried adding rate, but again I can't get the syntax correct for the iwconfig command (even after studying the man page). Here's what I entered:

```
sudo iwconfig wlan0 essid meatloaf mode Managed ap 00:18:39:C2:1D:BE rate 54M commit
```

I received the following error message:

```
Error : unrecognised wireless request 54M
```

By the way, I didn't enter a key because I removed security for the time being.

How do I properly write the command?

---

### Post by MCSE_Crossover on 2007-02-13
try inputting "sudo iwlist scan" which should scan for available access points and configure the appropriate settings. then you can input a "sudo iwconfig" to double check the settings. Then, if using DHCP, "sudo dhclient"

let me know...

---

### Post by d3dtn01 on 2007-02-13
Good news. I'm connected, though without any security.

First I tried typing the same iwconfig command as before (I checked the info from iwlist as you suggested). I had all the correct info, but not the correct order, apparently. When I moved the "rate 54M" nearer to the beginning of the command, I didn't get that strange error message. But I wasn't connected still. Not until I did the "sudo dhclient" did it work.

But now when I try to add encryption, I can't get it to work. First I tried WEP. It didn't work. Then I tried WPA (which is what I want to run). Again, I couldn't get it to work. I have wpasupplicant installed. What do I need to do to get the encryption working?

Thanks so much for your help thus far.

---

### Post by wej1971 on 2007-02-13
I have the same problem but even supplying the correct frequency (which seemed to be different from the access point) I still don't get any success.

dhclient ends with the following message: -

'No DHCPOFFERS received'

But I can see the access point with sudo iwlist scan: -

[B]wlan0  Scan completed
           Cell 01 - Address 00:0A:E9:02:1F:A6
           ESSID: "conexant"
           Mode: Master
           Frequency: 2.437 GHz
           Encryption key: off[/B]
       

Any ideas how I connect?

sudo iwconfig wlan0 gives: -

[B]IEEE 802.11g   ESSID: "conexant"
Mode: Managed     Frequency: 2.437 GHz    Access Point: 00:0A:E9:02:1F:A6
RTS thr: off   Fragment thr=2346 B
Encryption key: off[/B]

Any help gratefull received as I'm getting desperate with this!

---

### Post by MCSE_Crossover on 2007-02-13
Not sure what to tell ya as far as encryption...I don't use it. I just use static IP's and MAC filtering.

As far as the other poster, try changing your mode from "Master" to "Managed"

---

### Post by wej1971 on 2007-02-14
Unfortunately the mode 'Master' is the result from the scan, i.e. the access point - not sure how I change this.

---

### Post by gradedcheese on 2007-02-14
sudo iwconfig wlan0 mode managed

---

