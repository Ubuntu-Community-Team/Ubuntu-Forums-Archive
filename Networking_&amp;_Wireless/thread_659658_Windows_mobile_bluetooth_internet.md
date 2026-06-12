---
title: "Windows mobile bluetooth internet"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by daleus on 2008-01-05
I got bluetooth connectivity to work to the pocket pc. My laptop is given an IP via dhcp, I can ping the phone, I can ping internet hosts (news-europe.giganews.com is a good low-pinger from UK)
but as soon as I try BROWSE, i.e open Firefox or Konq, the bluetooth connection just drops out and I have to do the pand command again to get it to work.

I seem to be able to ping internet hosts just fine the dns looks up host names correctly and I get a ping response. What could possibly be allowing pings to work but killing the connection upon web-browsing use?

I had the exact same problem on PcLinuxOS summer 2006 with a different bluetooth device (laptop) and older OS on my PocketPC

I am currently using Ubuntu 7.10 on the same laptop with a USB Bluetooth card and a MDA Vario PocketPC with Windows Mobile 6 (different software to what I was using in 2006)

if there was some kind of hardware fault, why are pings working perfectly and normal web traffic just killing the connnection?

here is how I connect to the pocketpc

sudo pand --connect [bluetooth mac address]
[bnep0 is given an IP address by the internet sharing software built into pocketpc]

I have also tried other methods I found on the forums such as
sudo pand --role PANU --connect [BT mac address] but this doesn't even let me ping the phone, nevermind the internet websites.

*edit*

managed to wget a small .txt document from the internet.
then tried to download something small from the repo's (lynx, to be exact) and it died, as soon as it tried to recieve headers.

*edit again*

Works in windows, Must be something I'm doing wrong in Linux.

---

### Post by daleus on 2008-01-06
bit of a bump really, I seem to be able to wget all I want.

Why would standard web traffic kill the bnep0 interface?

On an unrelated note I tried to ssh out and just use a tunnel, but as soon as you try connect, the connection dies.
[note, tried both internet domain name and IP, domain resolution is just perfect before the connetion dies]



*EDIT*

an update of sorts.

I can make an SSH connection to the internet via the bluetooth connection on port 22, I can get logged in. I disconnected from ssh and restarted the connection with -D 7070, so I had a proxy (of sorts) and I set firefox to use that and I got further than ever before, I got the title of the webpage in firefox's application banner, then the connection died again, because ssh traffic is encrypted this leads me to believe the problem is with the amount of data being sent, it must be killing the conncetion somehow.

The GPRS connection from my phone is awfully low anyway, does anyone have a clue how I can throttle bnep0 bandwidth to stop the connection being killed?

my second update is the difference between "sudo pand --connect MAC" and "sudo pand --role PANU --connect MAC", the PANU one just tells me my connection died quicker (if doing a constant ping and then trying to browse) where as the ping program wouldn't do anything for about 15 seconds on the other one.

---

