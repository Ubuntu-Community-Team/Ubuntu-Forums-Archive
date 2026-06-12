---
title: "Can't Print to Wireless Printer - ubuntu 1604"
date: 2017-05-13
forum: Networking &amp; Wireless
---

### Post by rocky3 on 2017-05-13
Hi,  I am unable to ping my wireless printer. 

                        1) Before this issue began,  I typed [fping -g 192.168.3.0/24].  and it resulted in [192.168.3.181 is alive], my printer wireless IP address. Then I went to my windows machine and typed in [ping -a 192.168.3.181]. This resulted in BRW . . . . FOD] designating that 181 was associated with my BROTHER printer.

2) Now, when I type [FPING -g 192.168.3.0/24]  I get my IP wireless addresses for the router 192.168.3.1 and this HP UBUNTU machine 192.168.3.102, and that is it . . . . no additional addresses that would indicate the printer.  Further, now, I can't even ping my windows machine 192.168.3.102.  However, I can print WIFI to the wireless printer via the windows machine but I can't ping the 181 from the windows machine.  Please see my WIFI info report at the link below.
  


 [https://paste.ubuntu.com/24567061/](https://paste.ubuntu.com/24567061/)

Turtlegeek

---

### Post by rocky3 on 2017-05-15
Bump

---

### Post by rocky3 on 2017-05-27
bump

---

### Post by Hadaka on 2017-05-28
Hi, dmesg indicates arp filtering...
```
#brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
```
Perhaps there is an error in the arp tables ? I have zero knowledge of arp filtering other than reading this...
[https://linux-audit.com/filtering-arp-traffic-with-linux-arptables/](https://linux-audit.com/filtering-arp-traffic-with-linux-arptables/)

The router ssid is showing.. wpa1, the preferred setting is wpa-2 aes...and NO tkip.
```
#Eldridge <MAC 'Eldridge'[AC1]> Infra 11 2462 MHz 54 Mbit/s 67 &#9602;&#9604;&#9606;_ WPA1 yes * 
```

There is no printout for your wireless printer ssid in the network scan..nothing indicating a brother printer.
```
#192.168.3.181[ BRW . FOD] designating that 181 was associated with BROTHER printer.
```

While  "fping" probably is effective, I would suggest a regular  "ping" command to the printer ip address 
192.168.3.181 also the "3" is a bit different for a US router assingment...was this a change or just the way
it is ??

Thanks.

---

### Post by rocky3 on 2017-05-28
SOLVED 
1) in the command line I typed [fping -g 192.168.3.0/24] This resulted in [192.168.3.104 is alive]. The last time I did this, the IP ADDRESS ended with 181.  Then I went to my windows machine and typed in [ping -a 192.168.3.104 - NOT 181]. This resulted in BRW . . . . FOD] designating that 104 was the new IP address associated with my BROTHER printer.
2) In went to the brother site and used the linix installer tool (DEB). Then I followed the instructions on the installer menu. When it came to URI I selected IP address (#12). Then I inserted the 192.168.3.104 and it printed the test page!!!!! 

NOTE: I was unable to print because I was assuming my old Printer IP address was still good. so  lesson learned. . . I needed to find out exactly what my IP address was before executing the linix installer tool on the brother site.

Rocky

---

### Post by kurt18947 on 2017-05-28
Is your printer I.P. static or set by DHCP? If static, the printer address should not change. I assign static IP addresses to stationary hardware such as printers, routers etc. I find that makes for less confusion.

---

### Post by Hadaka on 2017-05-28
Hi, Glad you found the cause and a solution !
Thank you for the explanation and thank you
for marking your thread solved.

---

