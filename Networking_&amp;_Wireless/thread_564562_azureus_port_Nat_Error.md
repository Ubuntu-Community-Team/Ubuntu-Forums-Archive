---
title: "azureus port Nat Error"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2007-10-01
I followed the advice in this wiki


> According to the Azureus Wiki page: NAT problem:

Port Forwarding on Linux, specifically Ubuntu
[http://www.azureuswiki.com/index.php...fically_Ubuntu](http://www.azureuswiki.com/index.php...fically_Ubuntu)

Firstly the earlier notes on port forwarding for your router apply as before. Computers running Ubuntu, by default, come with all the ports locked down and you need to open the ports in ubuntu by using the iptables command. Other flavours of linux behave similarly

The commands below can be entered in a root terminal session to open the ports (TCP and UDP)

iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT

<your_port_number> is the port number you have used for port forwarding (Avoid 6881-6999, any from 49125-65535 is fine)

Once you've established the port is open you need to make the change persist through a reboot

create a file /etc/init.d/iptables_azureus and add the lines below
(sleep 220
/sbin/iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
/sbin/iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT ) &

The (sleep 220 is there to make the script wait a few minutes to allow subsequent firewall configuration scripts to run. 220 seconds is a large value and you may choose to configure a lower value. The key is that the opening of the azureus port is not countermanded by the firewall initialisation which runs later. At the end is a ) & which allows the script to let the rest of the boot continue, while the script waits.

chmod +x /etc/init.d/iptables_azureus make the file executable
update-rc.d iptables_azureus start 51 S . links the file into the startup sequence


Your configuration change will then persist through reboots. 

Having opened port 53000  in my nat router (Thompson SpeedTouch 780) the following part of the above worked in Azureus in that there was no NAT error on testing the port 53000 from within Azureus:

iptables -I INPUT -p tcp --dport 53000 -j ACCEPT
iptables -I INPUT -p udp --dport 53000 -j ACCEPT

Making the script did not work in that when I reboted Fiesty and tested the port in Azureus the NAT failed for 53000.



I did the following:
create a file /etc/init.d/iptables_azureus and add the lines below
(sleep 220
/sbin/iptables -I INPUT -p tcp --dport 53000 -j ACCEPT
sbin/iptables -I INPUT -p udp --dport 53000 -j ACCEPT ) &

Then run:

chmod +x /etc/init.d/iptables_azureus
update-rc.d iptables_azureus start 51 S .

iI wonder if the script should change for Fiesty? Does anyone know what I should do to keep 53000 openable between boots?

Robin

---

### Post by beyboo on 2007-10-01
thats a lot of code here. I use firestarter as it is GUI based and I know what I am doing. 

Second, When I was in Windoze, I chucked Azy for utorrent  and now on Ubuntu I chucked it for deluge and transmission. both rock and do the job damn better than Azy.

Azy is too bloated, takes too much memory/cpu and sucks big time. BTW - atleast go to some web site (Deluge has an option inside it), which will tell u if the port is open or not. It goes thru the brower to the deluge site and points ur port. The site responds back with a check on ur router if it is open or not. 

This will help you know if the port is open properly or not as well.

Give Firestarter a try.

---

### Post by Robbyx on 2007-10-01
Thank you for that advice. I went for Az because i want to set up a private tracker on my machine so that I can send the tracker file to a friend and he can download the file from my machine using BT. 

The online manual for Firestarter would not open. Presumably I go to the policy tab, add a rule that I allow a service called say BT, port 53000-53100, for everyone, on inbound traffic policy and same for outgoing policy?

Robin

---

### Post by WaySensei on 2008-02-04
I have a question related to this thread. I am following the Azureus Wiki on how to create a startup script that will allow the iptables change to persist through a reboot. 
The Wiki instructs me to: ```
update-rc.d iptables_azureus start 51 S . links the file into the startup sequence
```
Now, here comes my question. At the command line, every character matters and typing characters incorrectly can cause huge issues. The Wiki instructions seem to include a period after 51 S as so: ```
start 51 S . 
```
Is that correct, or a stray mark? Should the command instead be: ```
update-rc.d iptables_azureus start 51 S
```
I want to make sure I am typing the correct command before I do anything with sudo privileges...

---

