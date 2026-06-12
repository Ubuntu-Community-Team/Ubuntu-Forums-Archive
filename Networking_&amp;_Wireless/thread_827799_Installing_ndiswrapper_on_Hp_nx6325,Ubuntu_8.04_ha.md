---
title: "Installing ndiswrapper on Hp nx6325,Ubuntu 8.04 hardy"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by nickdbliss on 2008-06-13
(Note: If you are using other card, this may work for you as well.)
Ok this worked for me on Hp nx6325 

Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

But i had to search n struggle a lot.wheww. So to make it easier for rest of you, here is the guide.
I used ndiswrapper because b43-fwcutter doesnt work for me. Installing ndiswrapper like i did in Ubuntu 7.10 gutsy didnt work. 



**Here are the steps i followed:**

Firstly, connect to internet using wired connection, and remove the b43-fwcutter package. 
#sudo aptitude remove b43-fwcutter

2)Now follow the procedure as we used in gutsy to install ndiswrapper. Just skip the blacklisting part.
(Here are the steps how i did.

1)Download ndiswrapper from Synaptic

    * System -> Administration -> Synaptic Package Manager
    * Search for ndiswrapper
    * Download "ndiswrapper-utils-1.9" and "ndiswrapper-common" 

2)Get windows drivers and install them

    * A) Download and extract windows drivers to a folder of your choice.
   
    * Install them in ndiswrapper:
      Code:

      sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf

    * Check to see if hardware found
      Code:

      sudo ndiswrapper -l

3)Setup ndiswrapper to load driver (and itself) at startup

    * Edit the following file:
      Code:

      sudo gedit /etc/modules

    * Add a line which says:
      Code:

      ndiswrapper

    * Restart


 )

3)After you are done, run
#sudo gedit /etc/init.d/ndiswrapperfix.sh
and paste the following

#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

into the file. Save and close (It will stop causing ssb and ndiswrapper interference)

4)Then run
#cd /etc/init.d/ && sudo chmod 755 ndiswrapperfix.sh

5)Lastly run
#sudo update-rc.d ndiswrapperfix.sh defaults


Restart and enjoy your wireless.I am enjoying hope u ll too.;)

---

### Post by Corrupt3d on 2008-06-13
Hi,
In order to make your post more complete, perhaps you could include:

1)The manufacturer & chipset of your card, so that others who don't have the exact computer but have the same chipset can use this.

2) Maybe a link to your second step, theres several guides on how to install ndiswrapper--however some of them include more steps or different procedures than others--it would be best if you linked or listed the steps you used.

---

### Post by nickdbliss on 2008-06-13
> **Corrupt3d said:**
> Hi,
In order to make your post more complete, perhaps you could include:

1)The manufacturer & chipset of your card, so that others who don't have the exact computer but have the same chipset can use this.

2) Maybe a link to your second step, theres several guides on how to install ndiswrapper--however some of them include more steps or different procedures than others--it would be best if you linked or listed the steps you used.

THanks for the reply yeah that will be good.

---

### Post by Don9307 on 2008-11-09
I just used your suggested fix and it got my Broadcom BCM4318 wireless network card working under Ubuntu 8.10 (Intrepid) as well.  I was having a horrible time getting the card working until I found your help.  Thanks a bunch; I can breathe again!

---

### Post by nickdbliss on 2008-11-11
> **Don9307 said:**
> I just used your suggested fix and it got my Broadcom BCM4318 wireless network card working under Ubuntu 8.10 (Intrepid) as well.  I was having a horrible time getting the card working until I found your help.  Thanks a bunch; I can breathe again!

Thanks for informing it worked in Intrepid buddy. Glad it worked for you. Cheers.

---

### Post by flakeparadigm on 2008-11-29
Thank you so much! I was setting up a laptop for someone and this solution worked perfectly!

---

### Post by nickdbliss on 2008-11-29
> **flakeparadigm said:**
> Thank you so much! I was setting up a laptop for someone and this solution worked perfectly!

your welcome sir.

---

### Post by ormingtrude on 2009-12-28
Please help i am very new to this linux thing and only installed it today

i have a hp nx6325 and i think i installed the ndiswrapper but i don't know where it is to startup to go to the next stage of your help......

please help me

edited.....

somehow i got the wlan button working without using the ndiswrapper. now i can see wifi connections available but i can't access mine because there doesn't appear to be the option available for my mac address filtering or wep-open 8 digit password???

---

### Post by The_Cougar_Kid on 2012-01-19
Just to say several years on from the original posting I have just tried this advice.  I now have Ubuntu 11.10 installed, and, hey, it worked for me!!!  I found an alternative approach to step 2: In 'Dash' I searched for 'ndis' and was offered 'Windows Wireless Drivers'.  I ran that and I was able to install the driver directly from the original CD after navigating through the CD file structure to find bcmwl5.inf.  Then I followed (both) steps 3, followed by 4 and 5 - and I achieved immediate success!  Thanks very much for the tips.

---

