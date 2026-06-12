---
title: "Please help me connect adsl"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by doducchinh86 on 2006-09-08
I installed ubuntu 6.06 yesterday. I realize that It can't connect directly internet because my adsl need to login with account and password. In windows XP, I create a wan miniport (pppoe) connection but in Ubuntu I can't find any way to do this.
Please help me.
thanks

---

### Post by Rui Pais on 2006-09-08
hi, 
check if [this one]("https://help.ubuntu.com/community/ADSLPPPoE") help you.

---

### Post by doducchinh86 on 2006-09-08
I tried the way you show and after I wrote this command sudo pppoeconf, it annouced "Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.
"
I don't know how to do????](*,) ](*,) ](*,)

---

### Post by tbonius on 2006-09-08
Very strange indeed.  Some PPoE providers require that you restart the modem connection when connecting a new device that directly accresses it.  Try restarting the DLS modem and then reboot the Ubuntu machine.

Are you connecting to the DSL modem via USB.. or ethernet?

If it is ethernet.. make sure your eth0 (ethernet network interface) is detected.

Run pppoeconf again to setup your accoutn username and password and such.

T

---

### Post by doducchinh86 on 2006-09-09
I tried a lot but the connection cannnot be established. I doubt that ubuntu cann't detect my lan card. Because I use a new mobo asus M2NPV-MX with chipset nvidia 430 and lan card onboard. The mobo has a driver disk included which have linux drivers. I don't know how to update drivers and configure the network card. 
Can you help me, please?

---

### Post by smittyhead on 2006-09-09
I'm having the same sort of problem but my ppoe login in on the router/modem.  I have a windows laptop going to the router as well and it works fine.  I have firefox on both systems and have them set up the same with proxy and whatnot but the linux one dosnt want to connect.  I can get to the router control panel easy enough though. Before I tried Ubuntu I had suse on and Konqueror got on but Firefox wasnt able to then either.

My specs: Ubuntu 6.06, Hp Pavillion zd7000a laptop

---

### Post by tbonius on 2006-09-09
As far as Ubuntu detecting your NIC.. just check in your Netowork Configuration under the Admin Tools .. (or look for a /dev/eth0 device)

Check "ifconfig" for your current settings
Check "dmesg" for any info about eth0

I assume from your reply that your Ubuntu computer connects to your DSL modem via the Ethernet interface.  Try the steps I mentioned before and post any error messages (use the command dmesg to see these).

T

---

### Post by smittyhead on 2006-09-10
I just found this topic and it helped me sort my problem out and it might help you out as well. [http://www.ubuntuforums.org/showthread.php?t=11544&highlight=connect+adsl](http://www.ubuntuforums.org/showthread.php?t=11544&highlight=connect+adsl)

---

