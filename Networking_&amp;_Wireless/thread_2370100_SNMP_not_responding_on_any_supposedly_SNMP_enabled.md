---
title: "SNMP not responding on any supposedly SNMP enabled device"
date: 2017-08-30
forum: Networking &amp; Wireless
---

### Post by kandresen on 2017-08-30
I am trying to monitor my internet router using SNMP, but cannot get it to work despite the unit stating it is SNMP enabled in the datasheet: [https://www.multicominc.com/product/zhone-6618-w1-vdsl2adsl2-wireless-gateway/#tab-common_tab](https://www.multicominc.com/product/zhone-6618-w1-vdsl2adsl2-wireless-gateway/#tab-common_tab)

For doing this, I installed the following: 
apt install snmp perl-tk libterm-readkey-perl snmp-mibs-downloader

I then ran 
mibs-downloader

I then tried several commands such as 
  snmpwalk -c public  -v1 192.168.20.1 
  snmpwalk -c public  -v2c 192.168.20.1 

All resulting in Timeout errors. 

I thus tried setup my own SNMP server for testing purposes - only additional dep package: "snmpd". The new virtual server got IP: 192.168.20.11
I can get snmpwalk to work on the SNMP server, but only on if using the ip 127.0.0.1 or localhost. 
It fails if using the same command but with the eth0 address from the same snmp server, and it fails when connecting from my machine too. 
  snmpwalk -c public  -v1 127.0.0.1 # SUCCESS
  snmpwalk -c public  -v1 localhost  # SUCCESS
  snmpwalk -c public  -v1 192.168.20.11  # FAILURE by Timeout from all machines including the snmp server itself

So what am I doing wrong? Why can I not connect to any snmp devices over my localnet?

---

