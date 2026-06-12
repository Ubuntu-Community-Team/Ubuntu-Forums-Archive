---
title: "ADSL doesnt work in feisty, worked fine in edgy"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by nipun_jain on 2007-04-22
Hi all. I have been using edgy before I clean installed feisty on my Acer aspire 5002 laptop.

I am using an adsl connection to connect to the internet (my modem is Beetel 220 BX, connected to my lan card). In edgy, I used

```
pppoeconf
```

to configure my adsl and then

```
pon dsl-provider
```

to get online.

After a clean install of feisty, when I give the ppoeconf command, it gives the following message.

> Looking for access concentrator

the looking goes on to 100% and then nothing happens. Sometimes I get the following error.

> Error Message: Sorry, I scanned 2 interface, but the Access
Concentrator of your provider did not respond. Please
check your network and modem cables. Another reason
for the scan failure may also be another running pppoe
process which controls the modem

I am able to ping to my modem at 192.168.1.1 and even log into the modem console using my browser. So it's not a connection issue, but rather a pppoeconf issue. Any help? Any way I can use the pppoeconf from edgy?

---

### Post by nipun_jain on 2007-04-22
Got it to work! For the benefit of anyone who might be facing a similar problem this is what I did.

While pppoeconf was looking for access concentrator (even though the progress bar was 100%), I opened up a new terminal and gave the following command.

```
sudu ifdown eth0
```

This disconnected my ethernet connection, and voila! ppoeconf now proceeds from the "looking" stage to the actual connection configuration stage. Before starting configuring my connection, I gave the following command in the other terminal.

```
sudo ifup eth0
```

Now I proceeded to configure my dsl connection, renamed my dsl-provider file and connected to the internet using pon. Now I am making this post from within feisty!:popcorn:

---

