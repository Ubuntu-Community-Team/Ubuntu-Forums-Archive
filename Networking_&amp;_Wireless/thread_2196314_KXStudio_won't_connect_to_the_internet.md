---
title: "KXStudio won't connect to the internet"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by de Bacon on 2013-12-28
Hi out there,
I loaded a copy of KXStudio 12.04.3 on my desktop machine.  It has a direct ethernet connection through PPPOE to my ISP via wireless radio.  There is no router in the mix here.  

I have been playing with this for a few days without any success, using both the GUI and the CLI interfaces to attempt to gain connection.  I have (on a different HDD a working Kubuntu 12.04 setup, that I don't use, but I replicated all the settings in the Network Management GUI by making screenshots of each tab in both the Wired Connection and the DSL tabs of the system.  It doesn't work on KXStudio but it works on Kubuntu.  

Having gone through the GUI process unsuccessfully, I deleted the GUI setups then went on to the CLI.  I made sure that all was off by entering 

>$ poff -a

then checked that all was off with 

>$ ifconfig 
>$ plog

Then I set it up with 

>$ pppoeconf  

and 

>$ pon

I then confirmed a connection with 

>$ plog  

 I can't get any browser to load a url.  

I checked with my ISP to confirm that I was really connected, confirming that I was able to log in there. It is connecting there.  I can get a ping out to google successfully, but a browser won't connect.  

I have done the same with the KXStudio Live Disk with the same results.  

Something is not correct, but I don't know.  Of course with Linix my ISP support folks don't know anything, sigh!

Any ideas?

---

