---
title: "intermittent problems with wireless D-Link  DWL-G122"
date: 2005-08-23
forum: Networking &amp; Wireless
---

### Post by kikito on 2005-08-23
Hello all,

Im new to linux so bear with me if Im making a silly mistake.  I have been having all sorts of issues while trying to set up my wireless network with USB adapter DWL-G122 (H/W version B1).  Im using ndiswrapper for the driver.  After playing with it for couple of days I managed to get it working with the following setting:

essid: default
keymode: open
key: XXXXXXXXXX
broadcast on

if I disable broadcast forget it, I will never get connection.  and in order to get a connection I have to keep playing with the following commands:
sudo iwconfig wlan0 key open XXXXXXXXXX
sudo iwconfig wlan0 essid default
sudo ifconfig wlan0 up
..............

Yesterday I had it working.  So I decided to test it by shutting down the machine and restarting.  to my surprise it worked!!!!!! I was quite happy after a week of pain.  I turned it on this morning and guess what! didnt work.  the machine stalled at hotplug.  So I had to take the device out, login, put device in, then start typing the commands I mentioned above.

Any help on how to get this to work on startup will be appreciated.  Im in the edge of giving up.  considering the fact that I had it working in windows in less than an hour.

Thanks in advance,
kikito

---

