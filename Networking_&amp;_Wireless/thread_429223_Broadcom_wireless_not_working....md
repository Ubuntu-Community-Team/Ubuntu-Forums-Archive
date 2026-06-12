---
title: "Broadcom wireless not working..."
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by zagarino on 2007-05-01
hey guys,

i downloaded Ubuntu 7.04 and ran it from the cd, everything loaded fine, its cool but i have one problem which is 

i cant get my wireless to work.

thank god i didn't wipe it clean and install before i check that so now i have the time to see if my wireless card is supported.

my wireless is built-in and needs a Broadcom 4.100.15.5 driver. which is off course supported by HP because i have a Compaq nx7300 laptop, so i was wondering, how can i get it to work on ubuntu.

any suggestions ??....

here is the link for the driver for further information if needed.

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=ca&prodTypeId=321957&prodSeriesId=3310301&swItem=ob-45290-1&prodNameId=3310302&swEnvOID=1093&swLang=8&taskId=135&mode=4&idx=0]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=ca&prodTypeId=321957&prodSeriesId=3310301&swItem=ob-45290-1&prodNameId=3310302&swEnvOID=1093&swLang=8&taskId=135&mode=4&idx=0")

---

### Post by Candace on 2007-05-01
I think this thread will be helpful: [http://ubuntuforums.org/showthread.php?t=419709&highlight=ethernet](http://ubuntuforums.org/showthread.php?t=419709&highlight=ethernet)

---

### Post by zagarino on 2007-05-01
thanks

---

### Post by atariman on 2007-05-01
What kind of Broadcom chip is it? If it is a 4318, try this link

[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5)

I know it says it is for Edgy, but just "sudo apt-get install" the most current versions of ndiswrapper-utils (which is 1.9 I believe) and ndiswrapper-common from the Feisty repos. It took me 6 days to get my BCM4318 working, and now it does thanks to the above post. Good luck.

---

