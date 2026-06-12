---
title: "1xEV-DO Verizon"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by meenxo on 2008-08-20
Hello All

I have a Lenovo Thinkpad X61s with Builtin 1xEV-DO Verizon, Sierra Wireless MC5720. 
Link to Vista driver for reference: [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-67954](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-67954)

I have tried many documentations on the Ubuntu forum and other linux forums but with no luck. 

I used Gnome PPP and it auto-detected device in /dev/ttyUSB0

I run lsusb and it shows me:
Bus 004 Device 002: ID 1199:9229 Sierra Wireless, Inc.


I am really desperate for a solution and I definitely do not want to go back to nasty Vista. Any help will be appreciated.

Thanks

---

### Post by meenxo on 2008-08-23
GOT IT WORKING!


If your having the same problem
Source: [http://elsa.berkeley.edu/~chad/thinkpad.html](http://elsa.berkeley.edu/~chad/thinkpad.html)

3. My Sierra Wireless card (MC5725) for WWAN now works. I had one major problem in getting it setup. In general, the instructions here work:

    [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601)

However, my card has a product id of 0220, not 0020 (try the command "lsusb"). The sierra.c module (1.06 or 1.26.b) assumes it is the latter. To fix this, I followed the instructions above but then edited the sierra.c file before compiling (with "make" and "make install" as in the instructions) to change the product id for all mc5725 entries (there were two) to 0220. Before that, my system did not recognize the aircard (no /dev/ttyUSB0 created). After that, it did.

To get it to load with every reboot, I added the following lines to /etc/rc.local

    cd /home/chad/Linux/SierraWireless (wherever you did "make")
    ./make install 

I'm sure there's a better way than this, but at least this works.

The only other issue in getting the aircard working was that its radio was off to start with. There are probably other ways to handle this, but I found that using "minicom" was convenient. This is a simple modem program that lets you enter the commands to the modem directly. In particular

    at!pcinfo

shows basic info. And to turn the radio on, I used

    at!pcstate=1

Other useful commands can be found here:

    [http://www.anotherurl.com/library/at_test.htm](http://www.anotherurl.com/library/at_test.htm).

---

### Post by meenxo on 2008-08-23
Here is another funny thing that took me about 2 hours to figure out!

I was pinged google.com and it was working fine. As for the browser it was displaying "Page Cannot Be Displayed" !

Solution: I disabled my local wifi to get the Verizon working; therefore, it automatically set firefox to WORK OFFLINE" 

So just uncheck "Work Offline" everytime. There is fix for that, just look for it.

Thanks for a Great OS and a Great Forum!

---

