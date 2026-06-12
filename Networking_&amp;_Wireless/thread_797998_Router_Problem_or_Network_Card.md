---
title: "Router Problem or Network Card??"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by treeclimber on 2008-05-17
I updated to Hardy about 3 weeks ago and haven't been able to access the Internet since.  I have a Dell E1505 with an Intell Corporation Pro/Wireless 3945 ABG Network Connection (rev02).  I connect to my ISP with a wireless broadband modem.  I tried hooking it up directly and my computer couldn't find the internet that way at all, but I probably don't know how to get it set up properly.  I used to access the Net through my wireless router, a Network Everywhere Wireless-B Broadband Router, Model NWR11B.

My computer seems to recognize my network card.  When I click on Network Manager, it senses the wireless connection.  But when I click on it it just can't connect.  Is this a network card problem (aka driver missing or something) or is this a router problem?  I haven't been able to figure it out.  I seem to remember reading somewhere that Hardy doesn't work well with some cheap routers.  Can anybody help me?  Thanks!

---

### Post by SpaceTeddy on 2008-05-18
as far as i know, network manager in ubuntu will only keep a connection open if it is able to receive a proper ip-configuration from the network or it is conifgured with a manual ip. If neither of those condition are met, network manager refuses to connect to the network. This is possibly a bug in nm, as it makes it impossible for wireless modems to work. 

I only know (or so i think) how to do this manually in the command line. First off, turn network manager off! it will only get in the way of what you are trying to do. 

Now, with nm off, turn on a console and do a manual configuration of your wireless card. For that you will need to know which card is your wireless one. You can find that out with the following command:
```
iwconfig
```

it should give you a listing of devices and one of them should have a wireless extension. Note down the name of the card (possibly wlan0 or something like that)

With that name, manually attach your wireless card to the wifi network. For this you need the name of the card, and the name of the network. Armed with both, run the following command
```
sudo iwconfig %networkcard essid %networkname
```
where you replace the %networkcard with the proper device name (wlan0 ??) and the %network name with your networks name (duh :) )

now, this command will ONLY work if the encryption on your network is OFF. If you have an encryted network - there is more to it :(

Lastly, now configure your modem normally (pppoeconf ?) through the commandline and you should be able to get into the net... or so i think :)

if something does not work, just ask.

hope it helps :)

---

### Post by treeclimber on 2008-05-26
I tried your suggestion and it didn't work.  It seems I have a problem with a proprietary driver.  I re-installed Feisty with the CD supplied by Dell and I can get on the Internet now.  It had a restricted driver on it and it works with that. But when I was doing all the updates again, something took this driver away again!  I had to re-install again to get the driver back.  If I put in the Hardy CD, it will not recognize this driver and will not connect.  I have read where others with the same laptop have had no problem at all.  I don't know what to do to get Hardy to recognize the proprietary driver and not take it away.  Can anybody tell me how to do this or direct me to an answer that will tell me how to re-install it?  Where are the driver's listed on the CD or in the system?  How do I re-enable the driver?

---

### Post by SpaceTeddy on 2008-05-28
sorry - i have absolutly no idea about drivers - someone else will need to help you there... sorry :(

---

