---
title: "firewall prevents connection to internet at start up"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by herwin on 2011-02-08
I have a problem with the firewall.

Some time ago I installed guarddog. I found it to complicated so uninstalled it without making any changes (as far as I am aware of). I reinstalled firestarter.

Since then I have a problem. The three main programs that access the internet are:

1. thunderbird
2. firefox
3. skype

wWhen I start up ubuntu thunderbird & firefox cannot access the internet. Skype can.

After I start firestarter and disable the firewall the problem is solved. If firestarter is uninstalled the same problem occurs and I have to do the same thing through ufw. 

I run the most recent release of Ubuntu.

Any suggestions what could be the problem and how I can fix it?

Thanks.

---

### Post by aeiah on 2011-02-08
all firewall software on linux usually just interfaces with iptables and ipchains. if iptables is creating a setting on boot, then that would explain why uninstalling guarddog doesnt revert the settings.

---

### Post by herwin on 2011-02-08
Thanks.

Is there a way of finding out what the settings is which causes the problem and delete it?

---

### Post by yashar on 2011-02-10
cammand this:

iptables -L

if it shows any rule, do this:

iptables -A INPUT -j ACCEPT
iptables -A OUTPUT -j ACCEPT

---

### Post by herwin on 2011-02-10
[SIZE=2]the result of the IPtables -L are different whether firestarter runs or not. If firestarter is disabled, the output is:

[/SIZE]            @font-face {   font-family: "Cambria Math"; }@font-face {   font-family: "Calibri"; }p.MsoNormal, li.MsoNormal, div.MsoNormal { margin: 0cm 0cm 10pt; line-height: 115%; font-size: 11pt; font-family: "Calibri","sans-serif"; }.MsoChpDefault {  }.MsoPapDefault { margin-bottom: 10pt; line-height: 115%; }div.Section1 { page: Section1; }     [SIZE=2]Chain INPUT (policy ACCEPT)[/SIZE]
  [SIZE=2]target     prot opt source               destination         [/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]Chain FORWARD (policy ACCEPT)[/SIZE]
  [SIZE=2]target     prot opt source               destination    
[/SIZE]
[SIZE=2]------------[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]If firestarter is running the output of the iptables -L command is:[/SIZE]
[SIZE=2]
[/SIZE]
            @font-face {   font-family: "Cambria Math"; }@font-face {   font-family: "Calibri"; }p.MsoNormal, li.MsoNormal, div.MsoNormal { margin: 0cm 0cm 10pt; line-height: 115%; font-size: 11pt; font-family: "Calibri","sans-serif"; }.MsoChpDefault {  }.MsoPapDefault { margin-bottom: 10pt; line-height: 115%; }div.Section1 { page: Section1; }     [SIZE=2]Chain INPUT (policy DROP)[/SIZE]
  [SIZE=2]target     prot opt source               destination         [/SIZE]
  [SIZE=2]ACCEPT     tcp  --  O2WirelessBox.lan    anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN [/SIZE]
  [SIZE=2]ACCEPT     udp  --  O2WirelessBox.lan    anywhere            [/SIZE]
  [SIZE=2]ACCEPT     all  --  anywhere             anywhere            [/SIZE]
  [SIZE=2]ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 [/SIZE]
  [SIZE=2]DROP       all  --  anywhere             255.255.255.255     [/SIZE]
  [SIZE=2]DROP       all  --  anywhere             192.168.1.255       [/SIZE]
  [SIZE=2]DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            [/SIZE]
  [SIZE=2]DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 [/SIZE]
  [SIZE=2]DROP       all  --  255.255.255.255      anywhere            [/SIZE]
  [SIZE=2]DROP       all  --  anywhere             0.0.0.0             [/SIZE]
  [SIZE=2]DROP       all  --  anywhere             anywhere            state INVALID [/SIZE]
  [SIZE=2]LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 [/SIZE]
  [SIZE=2]INBOUND    all  --  anywhere             anywhere            [/SIZE]
  [SIZE=2]LOG_FILTER  all  --  anywhere             anywhere            [/SIZE]
  [SIZE=2]LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' [/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]Chain FORWARD (policy DROP)[/SIZE]
  [SIZE=2]target     prot opt source               destination         [/SIZE]
  [SIZE=2]ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 [/SIZE]
  [SIZE=2]LOG_FILTER  all  --  anywhere             anywhere            [/SIZE]
  [SIZE=2]LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' [/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]Chain OUTPUT (policy DROP)[/SIZE]
  [SIZE=2]target     prot opt source               destination         [/SIZE]
  [SIZE=2]ACCEPT     tcp  --  pre-installed-laptop  O2WirelessBox.lan   tcp dpt:domain [/SIZE]
  [SIZE=2]ACCEPT     udp  --  pre-installed-laptop  O2WirelessBox.lan   udp dpt:domain [/SIZE]
  [SIZE=2]ACCEPT     all  --  anywhere             anywhere            [/SIZE]
  [SIZE=2]DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            [/SIZE]
  [SIZE=2]DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 [/SIZE]
  [SIZE=2]DROP       all  --  255.255.255.255      anywhere            [/SIZE]
  [SIZE=2]DROP       all  --  anywhere             0.0.0.0             [/SIZE]
  [SIZE=2]DROP       all  --  anywhere             anywhere            state INVALID [/SIZE]
  [SIZE=2]OUTBOUND   all  --  anywhere             anywhere            [/SIZE]
  [SIZE=2]LOG_FILTER  all  --  anywhere             anywhere            [/SIZE]
  [SIZE=2]LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' [/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]Chain INBOUND (1 references)[/SIZE]
  [SIZE=2]target     prot opt source               destination         [/SIZE]
  [SIZE=2]ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED [/SIZE]
  [SIZE=2]ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED [/SIZE]
  [SIZE=2]LSI        all  --  anywhere             anywhere            [/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]Chain LOG_FILTER (5 references)[/SIZE]
  [SIZE=2]target     prot opt source               destination         [/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]Chain LSI (2 references)[/SIZE]
  [SIZE=2]target     prot opt source               destination         [/SIZE]
  [SIZE=2]LOG_FILTER  all  --  anywhere             anywhere            [/SIZE]
  [SIZE=2]LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' [/SIZE]
  [SIZE=2]DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN [/SIZE]
  [SIZE=2]LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' [/SIZE]
  [SIZE=2]DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST [/SIZE]
  [SIZE=2]LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' [/SIZE]
  [SIZE=2]DROP       icmp --  anywhere             anywhere            icmp echo-request [/SIZE]
  [SIZE=2]LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' [/SIZE]
  [SIZE=2]DROP       all  --  anywhere             anywhere            [/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]Chain LSO (0 references)[/SIZE]
  [SIZE=2]target     prot opt source               destination         [/SIZE]
  [SIZE=2]LOG_FILTER  all  --  anywhere             anywhere            [/SIZE]
  [SIZE=2]LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' [/SIZE]
  [SIZE=2]REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable [/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]Chain OUTBOUND (1 references)[/SIZE]
  [SIZE=2]target     prot opt source               destination         [/SIZE]
  [SIZE=2]ACCEPT     icmp --  anywhere             anywhere            [/SIZE]
  [SIZE=2]ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED [/SIZE]
  [SIZE=2]ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED [/SIZE]
  [SIZE=2]ACCEPT     all  --  anywhere             anywhere   [/SIZE]
   
[SIZE=2]     [/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]Chain OUTPUT (policy ACCEPT)[/SIZE]
  [SIZE=2]target     prot opt source               destination  
[/SIZE]

[SIZE=2][/SIZE]

[SIZE=2][/SIZE]

[SIZE=2][/SIZE]
[SIZE=2]
[/SIZE]
   [SIZE=2]
[/SIZE]

---

### Post by perspectoff on 2011-02-10
For Firestarter, make sure ports 80 and 443 are allowed for "outbound" traffic.

Firestarter -> Policy -> Outbound traffic policy -> Allow service -> ''right-click'' on box -> Add Rule -> Allow Service: 80 -> When the source is: Firewall host -> Add  (Repeat for port 443)

To use Firestarter (and any firewall) you must be aware of which ports your applications use (each of them often uses something different).


Also make sure Firestarter is set to use the interface you are using.

It is set to use the wired port (eth0) by default. If you are using a wireless connections (wlan0) you must set it to use that instead.

Firestarter -> Edit -> Preferences -> Firewall -> Network Settings -> 
"Internet connected network device" -> Detected device(s): wlan0

Repeat for the "Local connected network device".

(Obviously, if you are using a wired connection leave it at eth0.)


Configuring iptables by hand through the command line is a very steep learning curve. Some people like UFW/GUFW.

---

### Post by herwin on 2011-02-11
thanks!

---

