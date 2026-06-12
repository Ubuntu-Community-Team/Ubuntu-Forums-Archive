---
title: "modem problem"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by jamil_1 on 2007-03-02
hi every one i have a problem with my modem i cannot connect to the internet . iuse kppp for the dialup connection .but whenever i try to connect to the internet  kppp says that modem is busy. my modem is win lucent modem and is shown in my pc info window i.e it is detected by the operating system.however the driver fiel is empty . ithink that it is a driver problem . if i am right then please tell me the way i can install the drivers for modem i have the manufacturer's cd  .else tell me what to do

---

### Post by techamed on 2007-03-02
Win-modems are funny that way...  Yes it is a driver issue...  Depending on the type of win-modem you have (the model and such) you might be able to get it going by downloading the lucent drivers... 

here is the link for that...

[http://www.physcip.uni-stuttgart.de/heby/ltmodem/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/)

you can find out what model of modem you have by going to a command shell and typing 'lspci -vvv'
Your modem will show in that list along with any other devices that linux can detect...

It's a starting point...  If your still having trouble once you have found your model and played with the lucent drivers then let us know.

---

### Post by jamil_1 on 2007-03-03
thnx for the attention. i have used the scan modem tool .it says that i have aegre/lucent winmodem. i have also got some binaries and some sources for the modem. but i don't know how to use these binaries. compiling the driver is too tedious for a user like me . 
plz tell the wawy i can use these binaries to configure the modem.more over plz donot give me the heavy doze of commands to be typed in the shell since i am a. ex windows user and u know that window can be used without punching keys . i hope the same holds for linux

---

