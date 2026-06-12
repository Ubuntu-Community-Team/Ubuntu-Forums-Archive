---
title: "Problems getting L2TP VPN Connection to work from Ubuntu Server to local Router"
date: 2022-01-11
forum: Networking &amp; Wireless
---

### Post by johnquestioneer on 2022-01-11
[COLOR=#1A1A1B][FONT=&quot]Hi Ubuntu Friends,[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]I am currently struggling to get a VPN Connection up from a cloud hosted ubuntu VPS to my local Network.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]I have tried finding any good guides on how to connect, but all of them fail for me. I want to connect the box to my router (which is running a vpn server using L2TP PSK) and have all of the ubuntus traffic routed exclusively through that tunnel. And also of course have that tunnel start up when the machine restarts.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]I have tried it with [https://linuxscriptshub.com/configure-l2tp-ipsec-vpn-ubuntu-1604/](https://linuxscriptshub.com/configure-l2tp-ipsec-vpn-ubuntu-1604/) this tutorial (which is for 16.04, I am running 20.04 LTS) as well as with this one here [https://github.com/jabas06/l2tp-ipsec-vpn-client](https://github.com/jabas06/l2tp-ipsec-vpn-client) which is the only one that at least worked "a little". It won't connect but give me the following error when trying to connect[/FONT][/COLOR]
```
parsed INFORMATIONAL_V1 request 2675422485 [ HASH N(NO_PROP) ]
received NO_PROPOSAL_CHOSEN error notify
establishing connection 'L2TP-PSK' failed

```[COLOR=#1A1A1B][FONT=&quot]an ike-scan of my routers IP gave me the following output[/FONT][/COLOR]
```
 Notify message 14 (NO-PROPOSAL-CHOSEN) HDR=(CKY-R=c0879b9d1cd790ba, msgid=a53578d1)

```[COLOR=#1A1A1B][FONT=&quot]My Router uses 2 Phases for the ipsec authentication[/FONT][/COLOR]
```
Phase 1: 3des-md5-modp1024!

Phase 2: 3des-md5!

```[COLOR=#1A1A1B][FONT=&quot]Of which I added the 3des-md5! to the config.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]Now I got another problem... When I ty to start the connection again with[/FONT][/COLOR]
```
sudo ipsec up L2TP-PSK

```[COLOR=#1A1A1B][FONT=&quot]I get the error[/FONT][/COLOR]
```
no config named 'L2TP-PSK'

```[COLOR=#1A1A1B][FONT=&quot]Even though it's configured in my /etc/ipsec.conf...[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]My config files look exactly like in this github example [https://github.com/jabas06/l2tp-ipsec-vpn-client](https://github.com/jabas06/l2tp-ipsec-vpn-client)[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]Also additional questions, my VPN Server has a dynamic IP but I am using a DDNS Service. So I can always connect to it using myname.ddnsservice.net . Can I replace the IPs in the config with domain names? Or how can I do it?[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]I am completely lost... Grateful for any help! :-)[/FONT][/COLOR]

---

