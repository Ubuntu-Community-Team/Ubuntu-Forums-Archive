---
title: "Wireless works, not internet"
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by bbtwin on 2005-05-17
Hello,
 I am new to Linux but I am doing my best... reading the forums.
I have a laptop Acer 1681 WLMi with a intel 2200 BG wifi card.
I have managed to configure access to my wifi network with the iwconfig tool. In Mozilla, I have access to my DLink G604T router through [http://192.168.1.1](http://192.168.1.1)
I thought I had won ! :smile:  It proves that my connexion is working... but no internet connexion... no access to web sites.
Isn't that strange ? Any ideas ?  :?

---

### Post by wildtiger23 on 2005-05-17
In gnome, in the menu System/administration/network

Have you set your dns and gateway for your wlan0 card?

---

### Post by AndyM on 2005-05-17
bbtwin,

I have a Dell laptop with an Intell 2200BG Wifi card and I've been having the same problem.  I haven't found a solution yet, but for some reason this workaround allows my ethernet card to function:  I open System>Administration>Networking and then I deactivate the Wireless connection. (Make sure your ethernet connection is active while you're at it.)  For some reason, the ethernet card only works when wireless is deactivated.  Watch out though, because sometimes the wireless connection seems to reactivate itself, so I've actually de-configured it temporarily.  If you want to use wireless again you'll have to open up Network Settings again and reactivate it.

Hope this helps your situation!  I'm gonna keep looking for a permanent solution.

Anyone have any ideas?

AndyM

---

### Post by bbtwin on 2005-05-18
Thanks for the answer. No I have not set up DNS and gateway because I do not know what to put in there. !!! I said I was a beginner ...  ;-)

---

### Post by luca_linux on 2005-05-18
You have to put there the IP address of your router, that is 192.168.1.1.

---

### Post by bbtwin on 2005-05-20
I did that but it didn't work so I found the DNS address for my provider 212.27.32.176
and put free.fr in the search domains and it works !!! I don't know why though...
and every 5 minutes, the DNS addresses are changed back to 192.168.1.1 and the connexion is broken until I put the DNS address back. Very frustrating .
I tried to change the drivers of my BG2200 to the 1.0.4 but I get an error on the make instruction. I have read a lot of things on the forum but it doesn't work.

I get ; 

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/usr/src/ipw2200-1.0.4 MODVERDIR=/usr/src/ipw2200-1.0.4 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2

Any ideas anyone ?

---

### Post by testingubuntu on 2005-05-20
I have the identical wireless in my notebook 
Here is what I did 

the install has the required drivers to use this card with out having to get anything..
open the terminal 
type cat /etc/resolv.conf
you should see your ISP and DNS servers
If not  There is your problem! 

How to Fix

System--> Administration--> Networking

You should see your card  
See Cxcn image below 
deactivate it 
Click[COLOR=Blue] Hosts [/COLOR]tab at the top 

Clear out everything in there  [COLOR=Red]EXCEPT[/COLOR]  [B]127.0.0.1 localhost.localdomain
[/B]See HOSTS image below
Click the [COLOR=Blue]DNS[/COLOR] tab   

Here you'll need info from your router page 
So open your router page and look for your basic status page. 
 It should show your Public IP Address and DNS Servers and you ISP

Type in the IP addresses of the DNS servers
 into the **DNS servers Box**

Type in the the  Search Domain Box the name of your **ISP**
See DNS image below

---

### Post by bbtwin on 2005-05-21
Thanks,
I solved the driver problem by reinstalling ubuntu and following a faq to the letter. :) 
I just tried your solution of erasing all the hosts, the internet still works, hope it lasts.
Why do I have to reconfigure iwconfig key and channel every time I reboot ?

---

### Post by bbtwin on 2005-05-21
Actually, the problem persists. I type in the DNS for free.fr
and .. .5 minutes later the address is replaced by 192.168.1.1 (the router)
and I lose my internet connexion. Very frustrating. ](*,)  ](*,)

---

### Post by bbtwin on 2005-05-22
Hi again,
I seem to be talking to myself a lot lately, but I have found an answer that might help someone out there.
I updated my firmware with an ethernet connexion, and there I found I could program some DNS addresses. (I took the router off automatic DNS &I logged on with windows XP to experiment as it works ok.)
The DNS I got on the web for my provider didn't work so I looked up the log of the router and found some there. I  typed those in instead. Now the windows connection works ok still, and on ubuntu .... I type in 192.168.1.1 for the DNS foIIr the wireless setup and the internet works... How's that ?
By the way I changed to an open wep key because that seems to work better on Ubuntu.
 :smile: 

I'll keep posted if I find something else.

---

