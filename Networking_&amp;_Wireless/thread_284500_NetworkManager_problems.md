---
title: "NetworkManager problems"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by idiotboy on 2006-10-25
I'm a total newb to Ubuntu (just installed it two days ago), so be patient with me here.  After installer Dapper, I spent the last few days trying to get my wireless Nic card (a Linksys WMP54g V2.0) to work.  After much head banging, I finally got it connected to my router but with one problem.  In order to make it work I have to disable the WPA-Shared key security on the router and use no security.  So I set out today to try and get WPA to work.  

I'm following the WPAHowto directions, but I run into a little problem right at the begininng.  After installing (and verifying that it is installed), the NetworkManager package, it does not show up in my panel like the directions say it should.  Without it, I cannot go on to the next steps.  I have triple checked that it is installed and even uninstalled and reinstalled it twice, restarted, log'd out and back in, you name it I've tried it.

Would someone have any ideas as to why I am not seeing the NetworkManager icon?  The only network icon I see is the standard wireless icon with the green signal strength bar.  I thought maybe that was it, but when I click on it, I don't get the wireless options that the directions say I'm supposed to get.

Please help a newbie out if you can.

Joe

EDIT:  I finally got the Network Manager icon to show up, but unfortunately it says it can't detect any networks, which is funny considering the wireless is working.  I'm  really at a loss as to what may be wrong.

---

### Post by idiotboy on 2006-10-25
I finally got things worked out.  I'm going to post how I got it working just in case someone else may be having the same trouble I had.  

When I loaded my Linksys WMP54G v2.0 drivers using the wrapper utility, it named the card as wlna0.  In order to get the NetworkManager to detect my network, I had to edit my /etc/iftab file and change the eth0 :macaddress entry to wlan0 :macaddress, save it and reboot.  Once I did that, the NetworkManager picked up my network and allowed me to connect to it using WPA-SK encryption.  The only thing I still need to do is figure out how to get rid of having to enter my password key everytime I log in.  Not a big deal because I'm just glad I finally got it worked out, but if I can figure out how to eliminate this step it will only make things better.

Joe

---

