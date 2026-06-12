---
title: "yet another pc card issue (buffalo)"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by samcoinc on 2006-12-20
So I am new at this whole linux thing so bear with me.  

I have a buffalo wli-cb-g54s pcmcia card in my portable.  I have done a lot of reading and it looked like I needed to use ndiswrapper which I installed.  then found the windows driver for my card here [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) that matched the pdiid.
#  Laptop: Acer Aspire 1511 LMi and Acer Aspire 1501 LMi

    * Chipset: Broadcom Corporation BCM4306 802.11g (rev 3)
    * pciid: 14e4:4320 (rev 3)
    * Driver: [[ftp://ftp.support.acer-euro.com/notebook/aspire_1500/drivers/80211g.zip]](ftp://ftp.support.acer-euro.com/notebook/aspire_1500/drivers/80211g.zip]) from [[12]]
    * Other: (using ndiswrapper 0.10-1 from debian repository) drivers from ndiswrapper card list didn't work (everything seemed to be fine, but no networks were found). same problem as reported here (with a HP nx9105): [[13]] 

I have it to the point where I can do a iwconfig and get this
samco@samco-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

But I cannot get the power light on the card to come on.

let me know what info you need,  I am new remember.

thanks 
sam

---

### Post by ingo on 2006-12-21
Broadcom, that usually spells trouble...

Take it out, reinsert and type

dmesg

and post the last few (10 or so) lines of output. It's been a while since I configured my wifi card, but it would also be useful to have a copy of your /etc/network/interfaces file.

Apart from that, what kind of network are you trying to connect to? Open, WEP or WPA? Dhcp or fixed IP addresses (is that too much?)?

Also, can you scan networks already? Try

iwlist scanning eth1

and post your output. 

That should give everyone (incl. me) something to chew on :)

---

### Post by samcoinc on 2006-12-21
Thank you.   

I actually followed the directions here 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
and uninstalled ndiswrapper and used fwcutter.

after a bit of fiddling - when I brought the interface up the power light came on. :)

so I am surfing on the wireless buffalo card now.

thanks again
sam




> **ingo said:**
> Broadcom, that usually spells trouble...

Take it out, reinsert and type

dmesg

and post the last few (10 or so) lines of output. It's been a while since I configured my wifi card, but it would also be useful to have a copy of your /etc/network/interfaces file.

Apart from that, what kind of network are you trying to connect to? Open, WEP or WPA? Dhcp or fixed IP addresses (is that too much?)?

Also, can you scan networks already? Try

iwlist scanning eth1

and post your output. 

That should give everyone (incl. me) something to chew on :)

---

### Post by ingo on 2006-12-21
Congratulations!!! but you don't get off that lightly...

I've got an ibook using the same card (I believe) and I am keen on getting rid of that click-happy OS on there and put linux on instead. However, I would like to know whether that driver can handle wpa! Well, can it from your experience? 

Any advice is welcome :)

---

### Post by samcoinc on 2006-12-21
Security?  What is that?  ;)  I have not gotten that far yet.   When I do I will post the results here.

thanks
sam


> **ingo said:**
> Congratulations!!! but you don't get off that lightly...

I've got an ibook using the same card (I believe) and I am keen on getting rid of that click-happy OS on there and put linux on instead. However, I would like to know whether that driver can handle wpa! Well, can it from your experience? 

Any advice is welcome :)

---

