---
title: "How to set up a DNS server with the domain name &quot;open-ims.test?&quot;"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by ainigma on 2007-11-21
I follow this step....

"""""""""""""""""""""""""""""""""""""""""""""""""" """"""""""""""""""""""""""""""""""""""""
Step 3: Configure your DHCP and DNS settings

If you are running the DNS on your own machine then edit the file /etc/dhcp3/dhclient.conf and uncomment this line: prepend domain_name_servers 127.0.0.1;

Copy the open-ims DNS file to the bind folder:

sudo cp /opt/OpenIMSCore/ser_ims/cfg/open-ims.dnszone /etc/bind/

Add these lines to /etc/bind/named.conf.local

zone “open-ims.test” {

type master;

file “/etc/bind/open-ims.dnszone”;

};



You will need to restart bind for these changes to take effect.

sudo /etc/init.d/bind9 restart

Check that this all works. Try a ping and see if you get a response.

ping pcscf.open-ims.test
"""""""""""""""""""""""""""""""""""""""""""""""""" """"""""""""""""""""""""""""



But the result is this.....

"""""""""""""""""""""""""""""""""""""""""""""""""" """""""""""""""""""""""""""""
mtsagaro@Linux Testbed:~$ ping open-ims.test
ping: unknown host open-ims.test
"""""""""""""""""""""""""""""""""""""""""""""""""" """"""""""""""""""""""""""""

When i do restart bind, the connection says that it was failed.This command "./pcscf.sh" works just fine.All i want is to complete the steps of this address below.......
"http://uctimsclient.berlios.de/openimscore_on_ubu ntu_howto.html".The ony problem is the "ping" one.I cannot solve this problem.How to set up a DNS server with the domain name "open-ims.test?".Please help.....
i need your help

---

