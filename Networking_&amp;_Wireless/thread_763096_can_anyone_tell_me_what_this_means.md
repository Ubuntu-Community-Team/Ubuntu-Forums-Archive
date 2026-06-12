---
title: "can anyone tell me what this means"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by jmore9 on 2008-04-22
I leep getting the following on my windows box (winxp) and it still persists under ubuntu:

machine keeps trying to connect to 207.44.154.77:80

one line of traceroute that i have never seen before is :

13  * p64-2-2-0.r21.dllstx09.us.bb.gin.ntt.net (129.250.2.22) [MPLS: Label 657160 Exp 0] More labels  49 ms More labels  48 ms

Can anyone explain what that line means or direct me somewhere where i can find out ?

---

### Post by mister_pink on 2008-04-22
Not entirely sure why its connecting to it, but its [this](http://www.misec.net/) website. Mean anything to you? 

The other one doesn't look suspicious, seems like a random web server routing your request. Look at ntt.net

---

### Post by Monicker on 2008-04-23
> **jmore9 said:**
> I leep getting the following on my windows box (winxp) and it still persists under ubuntu:

machine keeps trying to connect to 207.44.154.77:80

one line of traceroute that i have never seen before is :

13  * p64-2-2-0.r21.dllstx09.us.bb.gin.ntt.net (129.250.2.22) [MPLS: Label 657160 Exp 0] More labels  49 ms More labels  48 ms

Can anyone explain what that line means or direct me somewhere where i can find out ?


Looks like a router to me.  MPLS is a routing protocol.

---

### Post by jmore9 on 2008-04-23
Here's some more strange stuff

Firestarter shows this in one of its entries :

time = Apr 22 22:47:59

port = 4899

source = 217.128.233.221

protocal = TCP

seervice = Radmin-Port

I have only had these strange things since being on comcast internet.  I never saw them on ATT dsl.  I'm learning something new everyday.

---

### Post by Ploppysator on 2008-04-23
1)
The "machine keeps trying to connect to 207.44.154.77:80". On a Windows PC should be checked with an AdWare stopper and a virus scanner, if there is some stupid thing installed or active. Otherwise, and if there is no result, check the registry, if the box still tries to connect after reboot
2)
The next line: "13 * p64-2-2-0.r21.dllstx09.us.bb.gin.ntt.net (129.250.2.22) [MPLS: Label 657160 Exp 0] More labels 49 ms More labels 48 ms" looks like the  normal routing/connection to AT&T PWLAN/authentication systems during a WLAN session on a public wireless LAN to me.
3)
This looks like the same as on 2), but to another public WLAN (Comcast). It shows the radius authentication reply from your login. You should find something similar or equal with the AT&T connection, too. The IP 217.128.233.221 and the Port 4899 show the response from the Radius server during your authentication. Are you in France ([http://www.dnsstuff.com/tools/whois.ch?ip=217.128.233.221&email=on](http://www.dnsstuff.com/tools/whois.ch?ip=217.128.233.221&email=on) -> Wanadoo)?

I think, that except to the point 1, there is nothing unusual and no reaction needed than :popcorn:.

Yours

Ploppysator

---

### Post by jmore9 on 2008-04-23
No i am in Grand Rapids, MI.  Nothing is found on the winxp machine so i will just reinstall it no bgi deal i have done it many times since 2002 when i bought it.  The firewall log in linux is where [ ubuntu 8.04 ] i first saw it zonealarm in windows doesnt show much at all.  But i am using ubuntu more and more about 70% of the time now so i get the hdtv tuner working that will go up to 100% . Thanks for your input i learned some new things today ..

jmore9

---

### Post by nicedude on 2008-04-23
The one that firestarter shows that you mentioned traces back to being this . 

inetnum:         217.128.233.0 - 217.128.233.255
netname:         IP2000-ADSL-BAS
descr:           LNSTA152 St Amand Bloc2
country:         FR
admin-c:         WITR1-RIPE
tech-c:          WITR1-RIPE
status:          ASSIGNED PA "status:" definitions
remarks:         for hacking, spamming or security problems send mail to
remarks:         [email]postmaster@wanadoo.fr[/email] AND [email]abuse@wanadoo.fr[/email]
mnt-by:          FT-BRX
source:          RIPE # Filtered

role:            Wanadoo France Technical Role
address:         FRANCE TELECOM/SCR
address:         48 rue Camille Desmoulins
address:         92791 ISSY LES MOULINEAUX CEDEX 9
address:         FR
phone:           +33 1 58 88 50 00
e-mail:          [email]abuse@orange.fr[/email]
admin-c:         WITR1-RIPE
tech-c:          WITR1-RIPE
nic-hdl:         WITR1-RIPE
mnt-by:          FT-BRX
source:          RIPE # Filtered


You could send an email to this address with a complaint [email]abuse@wanadoo.fr[/email]

---

