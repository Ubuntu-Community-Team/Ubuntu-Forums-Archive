---
title: "Gigabyte GN-WI01GT Connection Help!"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by ssc351 on 2007-03-21
So to update from my previous post [http://www.ubuntuforums.org/showthread.php?t=384878](http://www.ubuntuforums.org/showthread.php?t=384878)

I assumed the gigabyte card and the atheros card are the same...maybe they maybe they aren't...anyone know.

Anyways, I went on the madwifi site and it said that the Gigabyte GN-WI01GT card should be compatible...that is the card I have in my Dell 640m Inspirion with Edgy.

I checked the windows driver and it points to C:\WINDOWS\system32\DRIVERS\ar5211.sys


I think I am totally screwed up on the wireless side of things so I probably need to start over.

Here are my questions:

1.) Do I need to start over?  What commands do you guys need to see to see where my computer stands?

2.) Has anyone gotten the gigabyte card working with Edgy?
3.) What steps can I use to get it working ie...
4.) Can install the latest madwifi tarball "madwifi-0.9.3.tar.gz" and how do I do that?
5.) Can I somehow point linux to the windows driver?


I would really really like to get this working as I don't want to buy another wireless card.  What do you guys think?

---

### Post by chili555 on 2007-03-21
I agree with the guy on the first post. If you see ath0 in iwconfig, you should be going, albeit with a tweak or two. Please let us see:```
sudo iwconfig
sudo iwlist ath0 scan
```We'll troubleshoot from there.

---

### Post by ssc351 on 2007-03-21
iwconfig:


lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:16:E6:3D:01:41   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-89 dBm  Noise level=-89 dBm
          Rx invalid nwid:10  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.



iwlist:;

ath0      No scan results

---

### Post by ssc351 on 2007-03-21
Also, I still have no "bars" up in network manager and it says nothing in there when I right click about wireless or ath0 or anything like that.

---

### Post by chili555 on 2007-03-21
Try: ```
iwconfig ath0 mode managed
sudo iwlist ath0 scan
```Thanks.

---

### Post by ssc351 on 2007-03-21
Here are the outputs:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Operation not permitted.




and:

ath0      No scan results

---

### Post by chili555 on 2007-03-21
Very sorry. I meant sudo. Please forgive me and try again.

-------------------
Memo to chili: sudo evrything!!!

---

### Post by ssc351 on 2007-03-21
Here it is:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.

---

### Post by janek87 on 2007-04-09
i have the same card...what Ubuntu you have...6.10 or 7.04 ?
The card works, or not ?
Maybe you coult try this...[http://snapshots.madwifi.org/madwifi-ng-current.tar.gz](http://snapshots.madwifi.org/madwifi-ng-current.tar.gz) 
its the madwifi latest snapshot..i have too installed madwifi 0.9.3 but this doesent work...i try install the snapshot...hope its working:)

---

### Post by ssc351 on 2007-04-10
I am running 7.04...I could not get it working with madwifi. If you use ndiswrapper it will work.

---

### Post by specv on 2007-04-14
> **ssc351 said:**
> I am running 7.04...I could not get it working with madwifi. If you use ndiswrapper it will work.

besides the added range of the atheros card using ndiswrapper you lose all the extended wireless features this card is best known for.


according to the madwifi wiki with  	v0.9.2.3 and the newest HAL it does work. I just ordered this card and hopefully by the end of this week I will myself be trying to get this to work.

Im not the biggest linus/ubuntu guru out there but this is what I think the problem(s) may be

If you had the old drivers with the old hal installed you would need to remove them 100% so that there is no conflict and it doesnt attempt to use them. 

Solution: blacklist the older driver, reinstall fresh edgy, or make sure the driver is not present. Another thing you might want to try is to download back track 2. From what I read this live bootable linux cd should contain all the required drivers including the patch to do packet injection(i cant wait to try that out). If you can boot into that and it works you will now the card is working but again you may run into an issue with drivers again.

My hopes is that I had never attempted an install so when i install the lastest  v0.9.2.3 it should just work according to what the madwifi wiki says

The other issue is the card is running in master mode, there was a user that mentioned switching the mode which did fail. You should look into this further, because if you can get the card working in master mode the driver should be working its just a matter of tweaking it a bit. Try kismet and see if you can do any raw data packet sniffing and see if you can get the card to work in master mode


I have been researching the atheros cards to replace in my dell e1405 for the past few days so ive read hundreds of posts and howtos and wiki's related to this card and just about every other atheros card available. 

"Had to change order of module insertion. Works when order is:modprobe wlan_scan_sta,modprobe wlan_wep,modprobe ath_pci" From the madwifi wiki about the atheros specific chipset.

This was not realted to this specific gigabyte card but one of the AR5005xxx and AR5006xxx cards. There must be about 6 or so different ones mainly the only thing different between models is AR5005 is 5th generation AR5006 is 6th generation. The specific xxx model only differs by super wireless G B/G, Super wireless G A/B/G, A/B/G, B/G. they are differently numbered chipsets but all very similar.


Ive researched mixed information about the exact model of this card. there is one on ebay that claims it is AR5005 GS with the model number of GN-Wi01gt from gigabyte. 

There is another selling selling a AR5006EGS with the GN-Wi01gt card pictured.

I purchased my card from eWiz.com which did not specify the chipset that it uses but it was only $26. It is possible that they are the same models but newer ones use the newest chipset. 

Hopefully this post had some useful information for anyone looking for the atheros card or has problems with one

---

### Post by athleticbum32 on 2007-04-17
I just put the same card into my HP dv6000. Im very happy with it and i should be because i spent a few days hacking the bios in order to get past the blacklist of cards hp prevents installing, but thats a different story. I agree that you have the driver working it may just need a little tweeking. I just did a fresh install of feisty and it worked right from the start so i am scratching  my head on that. I am also having a few problems getting it to work with kismet, but hope to solve that soon. good luck the best advise i can give is see if it works on the live cd and if it does start over.

---

### Post by jmoral on 2007-04-19
specv,

I was *just* about to order the card from ewiz when I saw your post.  Can you please confirm:

[LIST]
[*]if your card from ewiz is working with madwifi?
[*]which ubuntu you're using (edgy?)
[*]which chipset the card has?  AR5005 GS?
[/LIST]
Thanks!

---

### Post by specv on 2007-04-20
> **jmoral said:**
> specv,

I was *just* about to order the card from ewiz when I saw your post.  Can you please confirm:

[LIST]
[*]if your card from ewiz is working with madwifi?
[*]which ubuntu you're using (edgy?)
[*]which chipset the card has?  AR5005 GS?
[/LIST]
Thanks!

my card is installed and in 7.04 i can see the card. I just did the final update as I had the beta previously installed which i upgraded from 6.10. Im not sure exactly what chipset it is but i do plan to find out. I cannot connect to any AP's secured or none secured, and my wifi light does not show up on my e1405. 

So I hope by the end of the weekend it will be working, its certianly close but needs a bit more work

---

### Post by specv on 2007-04-20
> **specv said:**
> my card is installed and in 7.04 i can see the card. I just did the final update as I had the beta previously installed which i upgraded from 6.10. Im not sure exactly what chipset it is but i do plan to find out. I cannot connect to any AP's secured or none secured, and my wifi light does not show up on my e1405. 

So I hope by the end of the weekend it will be working, its certianly close but needs a bit more work

Atheros AR5007EG 'unknown device 001c' i beleive this is the card i recevied

according to the madwifi wiki this card is not yet supported

---

### Post by Chafnan on 2007-04-21
I have this card.  I just bought an ASUS Z84JP and have an Intel Core 2 Duo 2.0Ghz.   This card works for me right off the Live CD and works after I installed Ubuntu 7.04.

I have bought this card because of another OS that I am installing on my machine.  The only issue that I am researching right now is that I don't get a signal over 50%.  Whether I am right next to the wireless router or not.  It doesn't seem to effect any internet speeds that I am getting though.  I would think that it is going to be fixed in any updates in the future.

---

### Post by specv on 2007-04-21
> **Chafnan said:**
> I have this card.  I just bought an ASUS Z84JP and have an Intel Core 2 Duo 2.0Ghz.   This card works for me right off the Live CD and works after I installed Ubuntu 7.04.

I have bought this card because of another OS that I am installing on my machine.  The only issue that I am researching right now is that I don't get a signal over 50%.  Whether I am right next to the wireless router or not.  It doesn't seem to effect any internet speeds that I am getting though.  I would think that it is going to be fixed in any updates in the future.
confirmed my card does work from the live cd. I just need to install the madwifi tools to get the wireless extenstions to work. WEP and WPA are not working but they require special modules to be loaded.


So for anyone looking for this card hurry and get it at ewiz before it is sold out. It is a 5007 chipset and works with 9.3.0 mad wifi drivers and seems to work on a fresh install of 7.04 without any configuration but not from an upgrade from 6.10

::edit:: WEP works perfectly fine it was my own stupidity i forgot to change the authentication from passphrase to hex :)

---

### Post by ssc351 on 2007-04-22
so what is the best way to go about getting this thing to work it I already have fiesty installed from beta?  Can I get it working off of the live cd?  Do i need to reinstall fiesty...if so I will need help with that because I have never reinstalled ubuntu once it was already on the machine.

Thanks.

---

### Post by specv on 2007-04-23
> **ssc351 said:**
> so what is the best way to go about getting this thing to work it I already have fiesty installed from beta?  Can I get it working off of the live cd?  Do i need to reinstall fiesty...if so I will need help with that because I have never reinstalled ubuntu once it was already on the machine.

Thanks.

boot from the live cd
run this command..

'su modprobe ath_pci' will load the madwifi driver and you should now see the card. Simple as that, if that works I would suggest a clean install of fiesty.

You could also try that in your current install to make sure the madwifi drivers are present. Then install the madwifi tools from the repositories

---

