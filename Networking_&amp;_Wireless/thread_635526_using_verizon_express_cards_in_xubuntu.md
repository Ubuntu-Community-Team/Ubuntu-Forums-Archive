---
title: "using verizon express cards in xubuntu??"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by sky5564 on 2007-12-08
i have a problem im new to ubuntu so bare with me..

i am running a dual boot xubuntu and windows xp via wubi on my toshiba sattellite notebook .

my problem is i cant get my verizon wireless express card to work on xubuntu keep in mind im talking about a phone modem type card (not a wifi card) i have seen posts on this forum regarding the wifi pci cards but none about the vz broadband cards so i need help on trying to find a way to run the vzam (verizon wireless acess manager) on xubuntu or a way to use my card without it 

please help 

=(

---

### Post by sky5564 on 2007-12-14
so far i have found a few sites that adress this issue     [http://support.real-time.com/linux/dialup/wvdial.html]("http://support.real-time.com/linux/dialup/wvdial.html") 

[http://www.markmmanning.com/blog/2007/07/installing-verizon-wireless-evdo-card.html]("http://www.markmmanning.com/blog/2007/07/installing-verizon-wireless-evdo-card.html")


so i tried this stuff that it said but ran into a small problem 
when i tried to edit the file /etc/wvdial.conf   my mousepad text editor said cannot write to file ????????????

---

### Post by sky5564 on 2008-01-04
ok i finaly got my verizon evdo card working 
all you need to do is open your favorite text editor as root and open the /etc/wvdial.conf file and delete everything it says and replace it with this 


[Dialer Defaults]
Stupid Mode =on
modem = /dev/ttyACM0 
Baud =921600
Init =ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777
Username = [email]yournumbergoeshere@vzw3g.com[/email]       
Password = vzw
Init1 =ATZ
ISDN = 0
Modem Type =Analog Modem
Auto Reconnect = on
Carrier Check =no

[Dailer ssh]
Init3 = ATMO

[Dialer pulse]
Dial Command =ATDP


then save the file and exit .

then all you will need to do is whenever you want to get online just open your terminal and type wvdial and hit enter and it will connect 

bam problem solved

---

