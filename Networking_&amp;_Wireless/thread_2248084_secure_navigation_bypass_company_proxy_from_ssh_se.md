---
title: "secure navigation: bypass company proxy from ssh server at home"
date: 2014-10-12
forum: Networking &amp; Wireless
---

### Post by paolo-marinelli on 2014-10-12
Hello, 

First of all, i am totally beginner in ubuntu as linux environment.. anyway, I have already installed on my hd since years because I am very attracted from this world, as i am curious person that likes to learn new things..
I would like to connect and surf in totally privacy and security when I am at work as I am out of my home, so I started to find more information about how to do this and now I am here. Today is the 3 day that I try without success.

I'll try to explain my scenario:

I have a computer in my company network with windows 8.1: this network is protected by proxy/firewall (forefront i think), under a domain ... for example, for to can navigate, I have to put the proxy string in internet explorer --> connection --> proxy  "srvtmg.domain.local:8080"



From what I have understood till now, I have to install ubuntu on a computer at my home (for example) and then to install the ssh function. Is it correct ?  

So I did 

code:

sudo apt-get install ssh



I have tried to configure it but without success i think because I am not able to navigate from my office by this ubuntu server at home. 

ANyway,
on my modem router at home I configured (portforward) the port 443 to my local IP address of home ubuntu computer that it is  192.168.1.100
So, If i open firefox and I try to open from another computer internal of my home network, a webpage start open and I can read:

*"***Index of /**

   [TABLE]
[TR]
[TH][IMG]http://192.168.1.100/icons/blank.gif[/IMG][/TH]
[TH][Name]("http://192.168.1.100/?C=N;O=D")[/TH]
[TH][Last modified]("http://192.168.1.100/?C=M;O=A")[/TH]
[TH][Size]("http://192.168.1.100/?C=S;O=A")[/TH]
[TH][Description]("http://192.168.1.100/?C=D;O=A")[/TH]
[/TR]
[TR]
[TH="colspan: 5"][HR][/HR][/TH]
[/TR]
[TR]
[TH="colspan: 5"][HR][/HR][/TH]
[/TR]
[/TABLE]
 Apache/2.4.7 (Ubuntu) Server at 192.168.1.100 Port 80
[I]"


----
[/I]yesterday, before to update the ubuntu to the 14.04 version, I had another result, probably becauase I modified the config files, i don't remember if config_ssh or config_sshd:
[I]
[I]"It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet."[/I]
[/I]


From what I understand, I have to configure the ssh to listening on port 443. Then I have to configure a proxy on this ubuntu computer, where it can be the "tunnel" when i will want surf from my office pc. Is it correct ?





Now, on the pc in my company network I downloaded, installed and tried to configure "putty.exe" for to try to connect and autenticate to my ubuntu pc (installed and on listening at my home); Using only putty, I couldn't connect to my home, I think because the firewall or proxy in my company network refuse the connection. 

I have found another program under windows: "Cntlm" .. i tried to configure it in some way, and now at least I am able to connect to my ubuntu pc at home. 

username: domainusername
domain: domainname
password: xxxxxxxxx

Proxy       proxycompany.domainname:8080

NoProxy  localhost, 127.0.0.*, 192.168.*

Listen  3128


I entered in putty the public IP of my ubuntu at home, the port 443 and SSH as "connection type"
then under the menu "tunnel" i set as source port "8888" and as "destination"  127.0.0.1:3128


The first start, putty asked me to click "ok" for a key.. i did "yes" and now if i start putty, i do "open" amd the terminal ask me for user and password, after it I am inside the terminal of my ubuntu. THis is the maximun result that I achieved till now. My brain is smoking so I would need help from somebody, if it is possible. 



Now I don't understand where I make errors, where I miss info and so on... How to continue? or better, can somebody advice me step by step, how to procede in this job ? 



I give you my excuse for my bad english and because I am not expert on linux and networking..
I hope that somebody will can help me kindly.. 


THanks you so much for your help..

Paolo

---

### Post by oldos2er on 2014-10-12
From the Code of Conduct: "Material that suggests illegal activity or contains illegal content is  also forbidden. We do not support circumventing TOS, EULA, etc here.  Such threads will be closed and offending users will be penalised with  infractions and warnings. Given that our forums could be used by people  at work and school we want to ensure they will not encounter material  that will cause them problems or cause their access to our site to be  limited, so all content should be safe for both."

Closed.

---

