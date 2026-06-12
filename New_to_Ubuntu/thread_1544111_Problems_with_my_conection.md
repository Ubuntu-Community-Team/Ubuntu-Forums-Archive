---
title: "Problems with my conection"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Jen-SG on 2010-08-02
I have just installed Ubuntu 9.10 Karmic Koala.
I have a Huawei SmartAX MT880 - ADSL CPE
I would like to have an ethernet conection without making my modem a router (to allow me to have a dynamic ip).
Normally, in Win xp I choose the conection and it's done (log in with user and pass).
I tried using the command pppoeconf as a root user but it didn't ask for the log in stuff as I read in an other thread in spanish in ubuntu-es.
When I typed that command it recognized all well but when I choose etho-1 it finishes with a screen saying it's not possible.
I forgot to mention that when I plug the ethernet cable a notification that says "Conected"  appears but I tried browsing and there's a problem.

Ask If you need more data.
Thanks for your answers!:grin:

---

### Post by jtarin on 2010-08-02
Post your results from the command```
 ifconfig -a
```
Have you tried acessing your modem and setting it up for PPPoE? I assume that is your prefered connection?
[I found this.]("http://www.appaji.net/get/dataone/bdah.html#mt800-config")

---

### Post by Jen-SG on 2010-08-02
Thanks for your response :).
I use the spanish version so I translated this.

**eth0**
Link encap:Ethernet addressHW 00:1e:ec:77:25:2f
Addr. inet:192.168.1.4 Difus.:192.168.1.255 Masc:255.255.255.0
Address inet6: fe80::21e::ecff:fe77:252f/64 Reach:Linked
multicast difusion activated and working mtu:1500 Metric:1
  RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 log.colaTX:1000 
          RX bytes:1329 (1.3 kb)  TX bytes:10201 (10.2 kb)
After this there is a **lo**, a **wlan** and a **wmaster0**
Do you need me to copy that too?

---

### Post by jtarin on 2010-08-02
Ok so your ethernet connection is visible and you have an address.Try the link I gave in my last post. It gives directions for setting up so your connection is on when you boot.

---

### Post by Jen-SG on 2010-08-02
Yes I have PPPoE.
When I tiped the adress this came:
[http://desmond.yfrog.com/Himg828/scaled.php?tn=0&server=828&filename=subirx.jpg&xsize=640&ysize=640](http://desmond.yfrog.com/Himg828/scaled.php?tn=0&server=828&filename=subirx.jpg&xsize=640&ysize=640)

At this moment I'm reading the "BSNL DateOne ADSL HOwto"

---

### Post by jtarin on 2010-08-02
> **Jen-SG said:**
> Yes I have PPPoE.
When I tiped the adress this came:
[http://desmond.yfrog.com/Himg828/scaled.php?tn=0&server=828&filename=subirx.jpg&xsize=640&ysize=640](http://desmond.yfrog.com/Himg828/scaled.php?tn=0&server=828&filename=subirx.jpg&xsize=640&ysize=640)

At this moment I'm reading the "BSNL DateOne ADSL HOwto"
By looking at your picture I see you have enabled to login to the modem. You should be able to go to the ADSL tab on the menu to set things up. If you need any help and the guide I gave you a link too is not enough...post back.

---

### Post by Jen-SG on 2010-08-02
Well that didn't work, I guess that The MT800(the tutorial one) and the MT880(mine) are different but I don't really know how much.
I don't have any ATM option and in my case I can do exactly that and I have more options

> Under, SmartAX MT800->ATM Settings, change the       following: 
In the pull down menu ...  
[INDENT]Select PVC 0 and
Set VPI/VCI: 0/35 (Default) 
[/INDENT]Operation Mode
[INDENT]Connection Type->PPP
PPPoA/PPPoE->PPPoE
Service Name->DataOne (Don't know how this name is used). 
[/INDENT]

I'm starting to hate my internet provider, 
When I asked about Ubuntu or Linux suport they answer with "I'm Sorry, what? err... I may pass you with an other employee" Srly.
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by jtarin on 2010-08-02
These normally don't need to be changed```
Select PVC 0 and
Set VPI/VCI: 0/35 (Default) 
```

Select PPPoE or PPPoA (normally PPPoE)
Service name you can leave blank normally.
```
Operation Mode

    Connection Type->PPP
    PPPoA/PPPoE->PPPoE
    Service Name->DataOne (Don't know how this name is used).
```

---

### Post by Jen-SG on 2010-08-02
Before this** I didn't have a PVC 0** so I will add this one.
[http://img814.imageshack.us/img814/3935/subida2.jpg](http://img814.imageshack.us/img814/3935/subida2.jpg) 
Here are my actual options,
 This is now that I reseted the modem.

I create the PVC 0 anyway and do something

> **2.3.2.4. Diagnostics (dialing out)**

Navigate to SmartAX MT880->Status->Diagnostics on the left       panel.  
Click on Submit.  After this, a few       tests will be carried out to test the connection.  The first three       test results should be a PASS. (The rest of the tests will either       be SKIPPED or FAILED.  It is safe to ignore those.  
After the above step, you should be able to use the router without a dialer on your machine.  

[http://img844.imageshack.us/img844/3310/preocu.jpg](http://img844.imageshack.us/img844/3310/preocu.jpg)
It didn't pass this test as you can see and I checked the PVC 0 and this camed out:
[http://img695.imageshack.us/img695/4011/preocupante.jpg](http://img695.imageshack.us/img695/4011/preocupante.jpg)

Now I'm going to try it.
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by Jen-SG on 2010-08-02
Ok. Still no internet on Ubuntu.
I still don't get why *pppoeconf* didn't worked the first time.
In windows still with the PVC 0 "enabled" I have to log in clicking in the conection icon so I guess I did something wrong because the modem should be in router mode not in bridge from what I read so far  :confused:[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by dineshs on 2010-08-02
Since you are using `modem inbridge mode' you need to configure your connection via the DSL tab in Network manager
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
But the following link says NM in 9.10 has bug
[http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10](http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10)
So it is better to configure your connection as `modem in PPPoE mode'
This link explains how to do it
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html)
You hsould tick both [COLOR="Blue"]enable NAT[/COLOR] and [COLOR="Blue"]default route[/COLOR]
Also if you are using BSNL broadband you should do configurations with VPI/VCI = 0/35.

---

### Post by jtarin on 2010-08-02
> I tried using the command pppoeconf as a root user but it didn't ask for the log in stuff as I read in an other thread in spanish in ubuntu-es.
When I typed that command it recognized all well but when I choose _[COLOR="Red"]etho-1[/COLOR]_ it finishes with a screen saying it's not possible.Try with interface eth0

---

### Post by soldier1st on 2010-08-03
also it seems your not running 10.04 so perhaps that is your issue.

---

