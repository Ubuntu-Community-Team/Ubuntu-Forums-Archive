---
title: "laptop modem problem"
date: 2005-09-06
forum: Networking &amp; Wireless
---

### Post by newubuntuuser on 2005-09-06
Update: I looked at the modem driver source code and found in a header file a #define setting the country to "North America" (0x19). I changed this to New Zealand (0x9) and recompiled. After removing the old modules and replacing them with the new, the modem now responds to "ATI9" with "New Zealand". Hooray.

Now another issue has arisen.....
Unfortunately I still cant connect to the web. wvdial doesnt work so Im trying minicom. When I dial into my ISP (which I couldn't do before), minicom brings up the following message:
CONNECT 48000 V42bis
That looks good. then I get:
login:
I enter my login name.
Then I get:
password:
After I enter my password and press enter, nothing happens. I cant ping anything or surf the web.
It is probably a simple problem, I havent thought about it for long. I just wanted to update the post with my solution. I hope that helps someone else.

ORIGINAL POST:
Sorry if Im repeating a previous post. I had some connection problems and wasnt sure if it had been submitted. Also I have had one small development.

I can't connect to the internet with my Compaq evo n610c laptop. The modem is an LT winmodem.
I downloaded, compiled and installed a driver 

from [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)

It seemed to work fine, I can send AT commands to the modem from Minicom. However when I send ATA (answer), the modem waits for a while then responds "NO CARRIER". Same problem when I try to dial (ATDT). Same problem from wvdial.

After some googling I concluded that the country setting might be wrong.
And when I query the modem for the country setting ("ATI9"), I get "North America", but I live in New Zealand. Unfortunately when I try to change the country setting using "AT%T19,0,9" the modem says "OK" but doesnt change anything. The next ATI9 still returns North America. I stuck "AT%T19,0,9" followed by "ATI9" in an init string in wvdial.conf so it tries to change it every time but the output from wvdial still shows North America

VERY CONFUSINGLY,
I have actually managed to connect a couple of times after connecting under windows and then rebooting into linux and using wvdial. Howver mostly although it says connected I havent been able to surf the web (or load a single web page) and I get kicked off after a few minutes. Curiously, the output from wvdial still says North america, even though it has somehow managed to talk to my ISP. Please see the end of this post for some output from wvdial.

Can anyone please help me?
If Im successful I might throw my experiences onto a web page to help other compaq laptop owners.

Regards
newubuntuuser

output from wvdial when I successfully connected to the web but couldn't surf the web:

# wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT%T19,0,9
AT%T19,0,9
OK
--> Sending: ATI9
ATI9
North America
OK
--> Modem initialized.
--> Sending: ATDTxxxxxxxxxxxxxxxxx
--> Waiting for carrier.
ATDTxxxxxxxxxxxxxxx
CONNECT 52000 V42bis
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Sep  7 05:05:57 2005
--> pid of pppd: 7975
--> Using interface ppp0
--> local  IP address xxxxxxxxxxxxxxx
--> remote IP address xxxxxxxxxxxxxxx
--> primary   DNS address xxxxxxxxxxxxxxxxx
--> secondary DNS address xxxxxxxxxxxxxxxxxxx

---

