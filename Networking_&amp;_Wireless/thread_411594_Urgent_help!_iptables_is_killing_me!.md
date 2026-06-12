---
title: "Urgent help! iptables is killing me!"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by tomplast on 2007-04-17
Please help me, I have "played around" with iptables too much now so that nothing work. Can anyone please tell me how to set the rules to the default that comes with Ubuntu? Is there any package where I can find the default iptables rules???

Please help me, it's urgent.

---

### Post by Uriel2006 on 2007-04-17
> **tomplast said:**
> Please help me, I have "played around" with iptables too much now so that nothing work. Can anyone please tell me how to set the rules to the default that comes with Ubuntu? Is there any package where I can find the default iptables rules???

Please help me, it's urgent.

Hello Tomplast,

basically Ubuntu comes with no firewall settings, i mean there is not a standard setting for iptables.

What i did (if it may be useful for you) is to write two scripts and place them inside the /etc directory.

I called them /etc/firewall.sh and /etc/nofirewall.sh  , so it's very easy for me to actvate and stop my firewall.
Sorry for italian comments on the script. The path for iptables is due i recompiled the iptables from scratch, please use your own one.

The "nofirewall.sh" is very simple and you may use it to clean your firewall::

-------------------
#/bin/sh

IPTABLES_CMD="/usr/local/sbin/iptables" 

echo "Clean tables"
echo "    "
$IPTABLES_CMD -v --flush
echo "    "
echo "Clean chains"
$IPTABLES_CMD -v -X


#Policies for table mangle
echo "    "
echo "Policies for table mangle"
echo "    "

$IPTABLES_CMD -v -t mangle -P  PREROUTING ACCEPT
$IPTABLES_CMD -v -t mangle -P  INPUT ACCEPT
$IPTABLES_CMD -v -t mangle -P  FORWARD ACCEPT
$IPTABLES_CMD -v -t mangle -P  OUTPUT ACCEPT
$IPTABLES_CMD -v -t mangle -P  POSTROUTING ACCEPT


#Policies for nat table
echo "    "
echo "Policies for nat table"
echo "    "

$IPTABLES_CMD -v -t nat -P PREROUTING ACCEPT
$IPTABLES_CMD -v -t nat -P OUTPUT ACCEPT
$IPTABLES_CMD -v -t nat -P POSTROUTING ACCEPT

#Policies for filter table
echo "    "
echo "Policies for filter table"
echo "    "

$IPTABLES_CMD -v -t filter -P INPUT DROP
$IPTABLES_CMD -v -t filter -P FORWARD DROP
$IPTABLES_CMD -v -t filter -P OUTPUT ACCEPT

#Let's open everything:

$IPTABLES_CMD -A INPUT  -j ACCEPT
$IPTABLES_CMD -A OUTPUT  -j ACCEPT
$IPTABLES_CMD -A FORWARD  -j ACCEPT
$IPTABLES_CMD -A INPUT  -i eth0 -j ACCEPT
-----------


the firewall.sh is a bit silly(sorry for italian comments there):

--------------------
#/bin/sh

IPTABLES_CMD="/usr/local/sbin/iptables " 

echo "Ripuliamo le tabelle"

$IPTABLES_CMD -v --flush

echo "Ripuliamo le catene"
$IPTABLES_CMD -v -X

echo " "
#Definiamo le policy per la tabella mangle
echo "Definiamo le policy per la tabella mangle"

$IPTABLES_CMD -v -t mangle -P  PREROUTING ACCEPT
$IPTABLES_CMD -v -t mangle -P  INPUT ACCEPT
$IPTABLES_CMD -v -t mangle -P  FORWARD ACCEPT
$IPTABLES_CMD -v -t mangle -P  OUTPUT ACCEPT
$IPTABLES_CMD -v -t mangle -P  POSTROUTING ACCEPT


#Definiamo le policy per la tabella nat

echo "Definiamo le policy per la tabella nat"


$IPTABLES_CMD -v -t nat -P PREROUTING ACCEPT
$IPTABLES_CMD -v -t nat -P OUTPUT ACCEPT
$IPTABLES_CMD -v -t nat -P POSTROUTING ACCEPT

#Definiamo le policy per la tabella filter
echo "Definiamo le policy per la tabella filter"
$IPTABLES_CMD -v -t filter -P INPUT DROP
$IPTABLES_CMD -v -t filter -P FORWARD DROP
$IPTABLES_CMD -v -t filter -P OUTPUT ACCEPT

#Definiamo le catene che ci servono
echo " "
echo "Definiamo le catene e le policy che ci servono:"

echo "-Trafshape"
$IPTABLES_CMD -v -N trafshape
#Limito il burst 
echo -n " -Limite del burst"
$IPTABLES_CMD -A trafshape -m limit --limit 1/sec --limit-burst 3 -j RETURN
$IPTABLES_CMD -A trafshape -m limit -j LOG --log-prefix "fw-BURST: "
$IPTABLES_CMD -A trafshape -j DROP
echo "...ok."

echo "-Portscan"
$IPTABLES_CMD -v -N portscan
# Droppa i  port scanning packets
echo -n  " -No scanning"
$IPTABLES_CMD -A portscan -m limit --limit 1/sec --limit-burst 2 -j RETURN
$IPTABLES_CMD -A portscan -m limit -j LOG --log-prefix "fw-SCAN: "
$IPTABLES_CMD -A portscan -j DROP
echo "...ok."

echo "-Synflood"
$IPTABLES_CMD -v -N synflood
# Limita il  packet rate contro i  SYN flood attacks
echo -n " -No syn flood attacks"
$IPTABLES_CMD -A synflood -m limit --limit 12/sec --limit-burst 24 -j RETURN
$IPTABLES_CMD -A synflood -m limit -j LOG --log-prefix "fw-SYN-flo: "
$IPTABLES_CMD -A synflood -j DROP
echo "...ok."

echo "-Pingflood"
$IPTABLES_CMD -v -N pingflood
# Limita packet rate contro i flood attacks
echo -n " -No ping flood attacks"
$IPTABLES_CMD -A pingflood -m limit --limit 12/sec --limit-burst 24 -j RETURN
$IPTABLES_CMD -A pingflood -m limit -j LOG --log-prefix "fw-ICMP-flo: "
$IPTABLES_CMD -A pingflood -j DROP
echo "...ok."

echo "-Badpacket"
$IPTABLES_CMD -v -N badpacket
# Rejecta i  bad packets con un bel "connection refused"
echo -n " -No bad packets"
$IPTABLES_CMD -A badpacket -p tcp -m state --state NEW -j REJECT --reject-with tcp-reset
$IPTABLES_CMD -A badpacket -p tcp ! --syn -m state --state NEW -m limit -j LOG --log-prefix "fw-BAD: "
$IPTABLES_CMD -A badpacket -p tcp ! --syn -m state --state NEW -j DROP
echo "...ok."

#Andiamo giu' pesante con le regole
echo " "
echo "Andiamo giu' pesante con le regole:"
echo " "

# Poi andiamo a scrivere le regole
#
#Appuriamo che i syn siano per le nuove connessioni, se no droppiamo:
echo -n "-Syn solo su connessioni NEW."
$IPTABLES_CMD -A INPUT  -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "fw-NEW-no-syn: "
echo -n "."
$IPTABLES_CMD -A INPUT  -p tcp ! --syn -m state --state NEW -j DROP
echo  "..Ok"

# Adesso permettiamo le connessioni gia' stabilite con il flag established o related
echo -n "-Connessioni ESTABILISHED & RELATED."
$IPTABLES_CMD -A INPUT  -m state --state ESTABLISHED,RELATED -j ACCEPT
echo  "..Ok."

#Localhost
echo -n "-Traffico su localhost.." 
$IPTABLES_CMD -A INPUT  -i lo -j ACCEPT
$IPTABLES_CMD -A OUTPUT -o lo -j ACCEPT
echo "..Ok."


# Protegge il traffico in entrata da scanning e flooding usando le tabelle custom
echo -n "-Protezione contro scanning e flooding usando tabelle custom."
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags SYN,ACK,FIN,RST RST -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags ALL NONE -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags FIN,RST FIN,RST -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags ACK,FIN FIN -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags ACK,URG URG -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags ACK,PSH PSH -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type echo-request -j pingflood
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --syn -j synflood
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags SYN,ACK SYN,ACK -j badpacket
echo ".Ok."

#togliamoci dalle scatole sasser e stronzate windows
echo  "-Stronzate di windows:"
echo -n " -Porta  135"
$IPTABLES_CMD -A INPUT -p tcp  --dport 135 -j LOG --log-prefix "fw-WIN135-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp  --dport 135 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp  --dport 135 -j LOG --log-prefix "fw-WIN135-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp  --dport 135 -j DROP
echo ".Ok."

#137
echo -n " -Porta  137"
$IPTABLES_CMD -A INPUT -p tcp --dport 137 -j LOG --log-prefix "fw-WIN137-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --dport 137 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 137 -j LOG --log-prefix "fw-WIN137-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 137 -j DROP
echo ".Ok."

#138
echo -n " -Porta  138"
$IPTABLES_CMD -A INPUT -p udp --dport 138 -j LOG --log-prefix "fw-WIN138-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --dport 138 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 138 -j LOG --log-prefix "fw-WIN138-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 138 -j DROP
echo ".Ok."

#139
echo -n " -Porta  139"
$IPTABLES_CMD -A INPUT -p udp --dport 139 -j LOG --log-prefix "fw-WIN139-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --dport 139 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 139 -j LOG --log-prefix "fw-WIN139-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 139 -j DROP
echo ".Ok."

#445
echo -n " -Porta  445"
$IPTABLES_CMD -A INPUT -p udp --dport 445 -j LOG --log-prefix "fw-WIN445-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --dport 445 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 445 -j LOG --log-prefix "fw-WIN445-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 445 -j DROP
echo ".Ok."

#1434
echo -n " -Porta 1434"
$IPTABLES_CMD -A INPUT -p udp --dport 1434 -j LOG --log-prefix "fw-WIN1434-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --dport 1434 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 1434 -j LOG --log-prefix "fw-WIN1434-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 1434 -j DROP
echo ".Ok."

#Roba DHCP 
echo -n "-Roba DHCP."
$IPTABLES_CMD -A INPUT  -p udp --dport 67 --sport 68 -d 255.255.255.255 -j LOG --log-prefix "fw-DHCP: "
echo -n "."
$IPTABLES_CMD -A INPUT  -p udp --dport 67 --sport 68 -d 255.255.255.255 -j ACCEPT
echo "..Ok."


#Roba unicast di windows
echo -n "-Roba Unicast."
$IPTABLES_CMD -A INPUT -d 255.255.255.255 -j LOG --log-prefix "fw-UNICAST: "
echo -n "."
$IPTABLES_CMD -A INPUT -d 255.255.255.255 -j DROP
echo "..Ok."

#Roba per network zozzi
echo -n "-Network zozzi."

$IPTABLES_CMD -A INPUT -d 224.0.0.1 -j LOG --log-prefix "fw-224-NET: "
echo -n "."
$IPTABLES_CMD -A INPUT -d 224.0.0.1 -j DROP
echo "..Ok."

# Permette ICMP solo per ping, la risposta ed MTU Discovery Path & Co.
echo "-Icmp solo tipo 0,8  e 3:"
echo -n " -Logging ICMP.."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 0/0 -j LOG --log-prefix "fw-O-ICMP-E-O/0: "
echo -n "."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 8/0 -j LOG --log-prefix "fw-O-ICMP-R-8/0: "
echo -n "."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 3   -j LOG --log-prefix "fw-O-ICMP-H!-3: "
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 0/0 -j LOG --log-prefix "fw-I-ICMP-E-O/0: "
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 8/0 -j LOG --log-prefix "fw-I-ICMP-R-8/0: "
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 3   -j LOG --log-prefix "fw-I-ICMP-H!-3: "
echo "..Ok."
echo -n " -Accept ICMP.."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 0/0 -j ACCEPT
echo -n "."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 8/0 -j ACCEPT
echo -n "."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 3 -j ACCEPT
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 0/0 -j ACCEPT
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 8/0 -j ACCEPT
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 3 -j ACCEPT
echo ".Ok."
echo -n " -Reject ICMP.."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type any -j LOG --log-prefix "fw-ICMP-BAD: "
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type any -j DROP
echo ".Ok."

#Aggiustiamo l' mss (per tunnel idioti)
echo -n "-Aggiustiamo MSS per tunnels vari.."
$IPTABLES_CMD -A OUTPUT  -p tcp --syn -j TCPMSS --clamp-mss-to-pmtu
echo -n "."
$IPTABLES_CMD -A FORWARD -p tcp --syn -j TCPMSS --clamp-mss-to-pmtu
echo ".Ok."

#Non vogliamo attacchi basati sui frammenti:
echo -n "-Frammenti IP malvagi.."
$IPTABLES_CMD -A INPUT -f -j LOG --log-prefix "fw-FRAG-UH!: "
echo -n "."
$IPTABLES_CMD -A INPUT -f -j DROP 
echo ".Ok."

#Droppo tutto il resto
echo -n "-Non vogliamo nuove connessioni."
$IPTABLES_CMD -A INPUT -m state --state NEW -j LOG --log-prefix "fw-SLAM!: "
echo -n "."
$IPTABLES_CMD -A INPUT -m state --state NEW -j DROP
echo -n "."
echo ".Ok."
echo "-Fine configurazione."

------------


hope being useful. You may use the first script /etc/nofire

Uriel

---

### Post by Uriel2006 on 2007-04-17
Ok, ok, i before you say me, there are some duplicates rows there.

Uriel

---

### Post by wieman01 on 2007-04-17
Why don't you install "Firestarter" which you find in the repositories? It does all the configuration for you and way easier to handle.

[http://www.fs-security.com/docs/introduction.php]("http://www.fs-security.com/docs/introduction.php")

---

### Post by tomplast on 2007-04-17
> **wieman01 said:**
> Why don't you install "Firestarter" which you find in the repositories? It does all the configuration for you and way easier to handle.

[http://www.fs-security.com/docs/introduction.php]("http://www.fs-security.com/docs/introduction.php")

Sadly it just freezes when you try to change something. It worked for me in Edgy but noit in Feisty. Anyway, iptables is better to use :). Much more effecient and easier (imo) from a pow to work with.

---

### Post by tomplast on 2007-04-17
> **Uriel2006 said:**
> Hello Tomplast,

basically Ubuntu comes with no firewall settings, i mean there is not a standard setting for iptables.

What i did (if it may be useful for you) is to write two scripts and place them inside the /etc directory.

I called them /etc/firewall.sh and /etc/nofirewall.sh  , so it's very easy for me to actvate and stop my firewall.
Sorry for italian comments on the script. The path for iptables is due i recompiled the iptables from scratch, please use your own one.

The "nofirewall.sh" is very simple and you may use it to clean your firewall::

-------------------
#/bin/sh

IPTABLES_CMD="/usr/local/sbin/iptables" 

echo "Clean tables"
echo "    "
$IPTABLES_CMD -v --flush
echo "    "
echo "Clean chains"
$IPTABLES_CMD -v -X


#Policies for table mangle
echo "    "
echo "Policies for table mangle"
echo "    "

$IPTABLES_CMD -v -t mangle -P  PREROUTING ACCEPT
$IPTABLES_CMD -v -t mangle -P  INPUT ACCEPT
$IPTABLES_CMD -v -t mangle -P  FORWARD ACCEPT
$IPTABLES_CMD -v -t mangle -P  OUTPUT ACCEPT
$IPTABLES_CMD -v -t mangle -P  POSTROUTING ACCEPT


#Policies for nat table
echo "    "
echo "Policies for nat table"
echo "    "

$IPTABLES_CMD -v -t nat -P PREROUTING ACCEPT
$IPTABLES_CMD -v -t nat -P OUTPUT ACCEPT
$IPTABLES_CMD -v -t nat -P POSTROUTING ACCEPT

#Policies for filter table
echo "    "
echo "Policies for filter table"
echo "    "

$IPTABLES_CMD -v -t filter -P INPUT DROP
$IPTABLES_CMD -v -t filter -P FORWARD DROP
$IPTABLES_CMD -v -t filter -P OUTPUT ACCEPT

#Let's open everything:

$IPTABLES_CMD -A INPUT  -j ACCEPT
$IPTABLES_CMD -A OUTPUT  -j ACCEPT
$IPTABLES_CMD -A FORWARD  -j ACCEPT
$IPTABLES_CMD -A INPUT  -i eth0 -j ACCEPT
-----------


the firewall.sh is a bit silly(sorry for italian comments there):

--------------------
#/bin/sh

IPTABLES_CMD="/usr/local/sbin/iptables " 

echo "Ripuliamo le tabelle"

$IPTABLES_CMD -v --flush

echo "Ripuliamo le catene"
$IPTABLES_CMD -v -X

echo " "
#Definiamo le policy per la tabella mangle
echo "Definiamo le policy per la tabella mangle"

$IPTABLES_CMD -v -t mangle -P  PREROUTING ACCEPT
$IPTABLES_CMD -v -t mangle -P  INPUT ACCEPT
$IPTABLES_CMD -v -t mangle -P  FORWARD ACCEPT
$IPTABLES_CMD -v -t mangle -P  OUTPUT ACCEPT
$IPTABLES_CMD -v -t mangle -P  POSTROUTING ACCEPT


#Definiamo le policy per la tabella nat

echo "Definiamo le policy per la tabella nat"


$IPTABLES_CMD -v -t nat -P PREROUTING ACCEPT
$IPTABLES_CMD -v -t nat -P OUTPUT ACCEPT
$IPTABLES_CMD -v -t nat -P POSTROUTING ACCEPT

#Definiamo le policy per la tabella filter
echo "Definiamo le policy per la tabella filter"
$IPTABLES_CMD -v -t filter -P INPUT DROP
$IPTABLES_CMD -v -t filter -P FORWARD DROP
$IPTABLES_CMD -v -t filter -P OUTPUT ACCEPT

#Definiamo le catene che ci servono
echo " "
echo "Definiamo le catene e le policy che ci servono:"

echo "-Trafshape"
$IPTABLES_CMD -v -N trafshape
#Limito il burst 
echo -n " -Limite del burst"
$IPTABLES_CMD -A trafshape -m limit --limit 1/sec --limit-burst 3 -j RETURN
$IPTABLES_CMD -A trafshape -m limit -j LOG --log-prefix "fw-BURST: "
$IPTABLES_CMD -A trafshape -j DROP
echo "...ok."

echo "-Portscan"
$IPTABLES_CMD -v -N portscan
# Droppa i  port scanning packets
echo -n  " -No scanning"
$IPTABLES_CMD -A portscan -m limit --limit 1/sec --limit-burst 2 -j RETURN
$IPTABLES_CMD -A portscan -m limit -j LOG --log-prefix "fw-SCAN: "
$IPTABLES_CMD -A portscan -j DROP
echo "...ok."

echo "-Synflood"
$IPTABLES_CMD -v -N synflood
# Limita il  packet rate contro i  SYN flood attacks
echo -n " -No syn flood attacks"
$IPTABLES_CMD -A synflood -m limit --limit 12/sec --limit-burst 24 -j RETURN
$IPTABLES_CMD -A synflood -m limit -j LOG --log-prefix "fw-SYN-flo: "
$IPTABLES_CMD -A synflood -j DROP
echo "...ok."

echo "-Pingflood"
$IPTABLES_CMD -v -N pingflood
# Limita packet rate contro i flood attacks
echo -n " -No ping flood attacks"
$IPTABLES_CMD -A pingflood -m limit --limit 12/sec --limit-burst 24 -j RETURN
$IPTABLES_CMD -A pingflood -m limit -j LOG --log-prefix "fw-ICMP-flo: "
$IPTABLES_CMD -A pingflood -j DROP
echo "...ok."

echo "-Badpacket"
$IPTABLES_CMD -v -N badpacket
# Rejecta i  bad packets con un bel "connection refused"
echo -n " -No bad packets"
$IPTABLES_CMD -A badpacket -p tcp -m state --state NEW -j REJECT --reject-with tcp-reset
$IPTABLES_CMD -A badpacket -p tcp ! --syn -m state --state NEW -m limit -j LOG --log-prefix "fw-BAD: "
$IPTABLES_CMD -A badpacket -p tcp ! --syn -m state --state NEW -j DROP
echo "...ok."

#Andiamo giu' pesante con le regole
echo " "
echo "Andiamo giu' pesante con le regole:"
echo " "

# Poi andiamo a scrivere le regole
#
#Appuriamo che i syn siano per le nuove connessioni, se no droppiamo:
echo -n "-Syn solo su connessioni NEW."
$IPTABLES_CMD -A INPUT  -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "fw-NEW-no-syn: "
echo -n "."
$IPTABLES_CMD -A INPUT  -p tcp ! --syn -m state --state NEW -j DROP
echo  "..Ok"

# Adesso permettiamo le connessioni gia' stabilite con il flag established o related
echo -n "-Connessioni ESTABILISHED & RELATED."
$IPTABLES_CMD -A INPUT  -m state --state ESTABLISHED,RELATED -j ACCEPT
echo  "..Ok."

#Localhost
echo -n "-Traffico su localhost.." 
$IPTABLES_CMD -A INPUT  -i lo -j ACCEPT
$IPTABLES_CMD -A OUTPUT -o lo -j ACCEPT
echo "..Ok."


# Protegge il traffico in entrata da scanning e flooding usando le tabelle custom
echo -n "-Protezione contro scanning e flooding usando tabelle custom."
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags SYN,ACK,FIN,RST RST -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags ALL NONE -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags FIN,RST FIN,RST -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags ACK,FIN FIN -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags ACK,URG URG -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags ACK,PSH PSH -j portscan
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type echo-request -j pingflood
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --syn -j synflood
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --tcp-flags SYN,ACK SYN,ACK -j badpacket
echo ".Ok."

#togliamoci dalle scatole sasser e stronzate windows
echo  "-Stronzate di windows:"
echo -n " -Porta  135"
$IPTABLES_CMD -A INPUT -p tcp  --dport 135 -j LOG --log-prefix "fw-WIN135-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp  --dport 135 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp  --dport 135 -j LOG --log-prefix "fw-WIN135-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp  --dport 135 -j DROP
echo ".Ok."

#137
echo -n " -Porta  137"
$IPTABLES_CMD -A INPUT -p tcp --dport 137 -j LOG --log-prefix "fw-WIN137-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --dport 137 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 137 -j LOG --log-prefix "fw-WIN137-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 137 -j DROP
echo ".Ok."

#138
echo -n " -Porta  138"
$IPTABLES_CMD -A INPUT -p udp --dport 138 -j LOG --log-prefix "fw-WIN138-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --dport 138 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 138 -j LOG --log-prefix "fw-WIN138-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 138 -j DROP
echo ".Ok."

#139
echo -n " -Porta  139"
$IPTABLES_CMD -A INPUT -p udp --dport 139 -j LOG --log-prefix "fw-WIN139-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --dport 139 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 139 -j LOG --log-prefix "fw-WIN139-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 139 -j DROP
echo ".Ok."

#445
echo -n " -Porta  445"
$IPTABLES_CMD -A INPUT -p udp --dport 445 -j LOG --log-prefix "fw-WIN445-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --dport 445 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 445 -j LOG --log-prefix "fw-WIN445-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 445 -j DROP
echo ".Ok."

#1434
echo -n " -Porta 1434"
$IPTABLES_CMD -A INPUT -p udp --dport 1434 -j LOG --log-prefix "fw-WIN1434-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p tcp --dport 1434 -j DROP
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 1434 -j LOG --log-prefix "fw-WIN1434-SCAN: "
echo -n "."
$IPTABLES_CMD -A INPUT -p udp --dport 1434 -j DROP
echo ".Ok."

#Roba DHCP 
echo -n "-Roba DHCP."
$IPTABLES_CMD -A INPUT  -p udp --dport 67 --sport 68 -d 255.255.255.255 -j LOG --log-prefix "fw-DHCP: "
echo -n "."
$IPTABLES_CMD -A INPUT  -p udp --dport 67 --sport 68 -d 255.255.255.255 -j ACCEPT
echo "..Ok."


#Roba unicast di windows
echo -n "-Roba Unicast."
$IPTABLES_CMD -A INPUT -d 255.255.255.255 -j LOG --log-prefix "fw-UNICAST: "
echo -n "."
$IPTABLES_CMD -A INPUT -d 255.255.255.255 -j DROP
echo "..Ok."

#Roba per network zozzi
echo -n "-Network zozzi."

$IPTABLES_CMD -A INPUT -d 224.0.0.1 -j LOG --log-prefix "fw-224-NET: "
echo -n "."
$IPTABLES_CMD -A INPUT -d 224.0.0.1 -j DROP
echo "..Ok."

# Permette ICMP solo per ping, la risposta ed MTU Discovery Path & Co.
echo "-Icmp solo tipo 0,8  e 3:"
echo -n " -Logging ICMP.."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 0/0 -j LOG --log-prefix "fw-O-ICMP-E-O/0: "
echo -n "."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 8/0 -j LOG --log-prefix "fw-O-ICMP-R-8/0: "
echo -n "."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 3   -j LOG --log-prefix "fw-O-ICMP-H!-3: "
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 0/0 -j LOG --log-prefix "fw-I-ICMP-E-O/0: "
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 8/0 -j LOG --log-prefix "fw-I-ICMP-R-8/0: "
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 3   -j LOG --log-prefix "fw-I-ICMP-H!-3: "
echo "..Ok."
echo -n " -Accept ICMP.."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 0/0 -j ACCEPT
echo -n "."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 8/0 -j ACCEPT
echo -n "."
$IPTABLES_CMD -A OUTPUT -p icmp --icmp-type 3 -j ACCEPT
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 0/0 -j ACCEPT
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 8/0 -j ACCEPT
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type 3 -j ACCEPT
echo ".Ok."
echo -n " -Reject ICMP.."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type any -j LOG --log-prefix "fw-ICMP-BAD: "
echo -n "."
$IPTABLES_CMD -A INPUT -p icmp --icmp-type any -j DROP
echo ".Ok."

#Aggiustiamo l' mss (per tunnel idioti)
echo -n "-Aggiustiamo MSS per tunnels vari.."
$IPTABLES_CMD -A OUTPUT  -p tcp --syn -j TCPMSS --clamp-mss-to-pmtu
echo -n "."
$IPTABLES_CMD -A FORWARD -p tcp --syn -j TCPMSS --clamp-mss-to-pmtu
echo ".Ok."

#Non vogliamo attacchi basati sui frammenti:
echo -n "-Frammenti IP malvagi.."
$IPTABLES_CMD -A INPUT -f -j LOG --log-prefix "fw-FRAG-UH!: "
echo -n "."
$IPTABLES_CMD -A INPUT -f -j DROP 
echo ".Ok."

#Droppo tutto il resto
echo -n "-Non vogliamo nuove connessioni."
$IPTABLES_CMD -A INPUT -m state --state NEW -j LOG --log-prefix "fw-SLAM!: "
echo -n "."
$IPTABLES_CMD -A INPUT -m state --state NEW -j DROP
echo -n "."
echo ".Ok."
echo "-Fine configurazione."

------------


hope being useful. You may use the first script /etc/nofire

Uriel

It worked out fine for me :). But thanks for the script, this can be useful :)

---

