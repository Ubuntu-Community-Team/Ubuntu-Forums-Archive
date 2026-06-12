---
title: "combining gsm modems,wifi and ethernet"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by vinaymcp on 2013-12-04
Hello all,

Before i ask a question let me apologize for my bad english.

I would like to use this for a Medical Transmission unit , where patient data  has to reach the doctor at a priority basis. In this case the system  will be in rural area where there may be some network available in one or more network interfaces (gsm modem/wifi).

Is there a  way to combine the internet of GSM/CDMA modem, WIFI Conncetivity and Ethernet and make a fault tolerant internet line. So that depending upon what ever is available it can just combine it and send the data.

I tried with UbuntuBonding and ISPUnity none of them helped as they are not allowing me to combine GSM modems . Can any suggest anything ?

I am using UBUNTU 12.04

Any help will be appreciated.

Thanks

---

### Post by varunendra on 2013-12-04
Hello Vinay, Welcome to the forums !

I think there are many issues with GSM modems that prevent them from integrating well with connection automation methods.

As far as I have experienced, the GSM modem connections always need to be initialized manually when using default methods. Unless you can formulate a script to detect the device/connection and initialize the connection automatically, it would always require manual intervention. You can take a look at "nmcli" command options (man nmcli) to see how to use Network Manager from commandline if you wish to try it in a few scripts.

Also, it is quite often that the modem gets 'hung' if the connection fails before or after connecting, and it needs to be 'Physically' disconnected - reconnected to reset it. This can be a major problem in areas where service quality is not very good.

Assuming you can somehow overcome these issues, a simple script can be created to detect available network and connection types, and use whichever is available or seems optimal.

Please correct me if I misunderstood your problem.

**PS:**
My English is not good enough to judge yours, but your English seems better than fine to me. :)

---

### Post by vinaymcp on 2013-12-07
Hi Varunendra,

Thanks so much for your help!

I have already written a manual script for it, but it seems like when ever i have a new modem, i need to rewrite a code for it. 

I was thinking if i can do something which can automate this things, so was looking into ISPUnity.


But i guess i need to live with manual code changes for every new modem integration.


Best Regards
Vinay



> **varunendra said:**
> Hello Vinay, Welcome to the forums !

I think there are many issues with GSM modems that prevent them from integrating well with connection automation methods.

As far as I have experienced, the GSM modem connections always need to be initialized manually when using default methods. Unless you can formulate a script to detect the device/connection and initialize the connection automatically, it would always require manual intervention. You can take a look at "nmcli" command options (man nmcli) to see how to use Network Manager from commandline if you wish to try it in a few scripts.

Also, it is quite often that the modem gets 'hung' if the connection fails before or after connecting, and it needs to be 'Physically' disconnected - reconnected to reset it. This can be a major problem in areas where service quality is not very good.

Assuming you can somehow overcome these issues, a simple script can be created to detect available network and connection types, and use whichever is available or seems optimal.

Please correct me if I misunderstood your problem.

**PS:**
My English is not good enough to judge yours, but your English seems better than fine to me. :)

---

