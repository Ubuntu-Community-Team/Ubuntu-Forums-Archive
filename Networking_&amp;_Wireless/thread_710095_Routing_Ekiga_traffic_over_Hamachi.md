---
title: "Routing Ekiga traffic over Hamachi"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by llevering on 2008-02-28
I'm a Dutchmen living for a year in South-Africa. To stay in touch with family/friends I have a dutch VOIP telephonenumber. I use Ekiga to connect to the VOIP service and everyone in Holland can call me on a Dutch PSTN number that is being redirected to my VOIP account. The problem is that in my internet provider here does not give public IPs to their end users. So I have an IP adress in the 10.0.x.x range and than the router gives computers internal IPs with as range 192.168.x.x. The trouble is that with all these NAT translations Ekiga has troubles to keep up a good connection with my dutch VOIP provider. Also it has troubles with setting up bi-directional audio connections, often I do not hear the other party.

So I thought of a solution and probably I have one, but I don't know how to set it up, as I am not familiar with Linux networking. In Holland I have an old Windows XP machine that is in a DMZ and that is mainly used by my father as backup PC. On that machine is Hamachi installed. If I would be able to redirect all my Ekiga traffic to my computer in Holland which can directly connect to a public IP address the problem would probably be solved. I only want to route my Ekiga traffic this way, because otherwise visiting website in South Africa would use a very complicated and slow route via Holland. 

I did some investigation and probably I need IpTables and ipforward or something, but I am not sure and I do not have a clue how I should configure it for this purpose. I hope you can help me out.

---

### Post by maulakai on 2008-03-01
I live in Japan and have tried similar setups to the East Coast of the USA.  

Although many companies sell you a service, as though people back home could simply dial a number and have it ring on your computer, the bottom line is that it will never be as reliable as a standard telephone line.  Often times I have connection problems when I'm not routing my traffic half way aroudn the world. 

It's hard to imagine that routing your traffic through your home pc would help.

After spending countless hours on similar efforts, i finally resolved to accept that I moved so far away that not even the internet can overcome the physical boundary to make me "just a phone call away."

Do tell if you find the magic setup

---

### Post by Giannis68 on 2008-03-01


**[SIZE=2][http://www.ekiga.org/index.php?rub=3&pos=0&faqpage=x161.html](http://www.ekiga.org/index.php?rub=3&pos=0&faqpage=x161.html)[/SIZE]**



**How can I easily use Ekiga behind a NAT/PAT gateway?**

 Ekiga has extensive and improved NAT support thanks to STUN. In 99% of the cases, you do not have any configuration to do, and you can even be reachable from the outside without any port forwarding. 
   *SIP only:* The following explanation is valid only for SIP. Please read below for H.323. The first thing to do is to run the configuration assistant NAT test: 
[LIST]
[*] If it reports "Cone NAT" or "Port Restricted NAT" you just have to answer "yes" to the dialog asking you to activate STUN support. You do not have to do anything else. You will be reachable from the outside. 
[*] If it reports "Symmetric NAT" and that you are using GNU/Linux, please use the script (or a variation of it) given below. You can run the NAT test again, you will notice that your NAT will behave as a "Cone NAT" or "Port Restricted NAT" as in case 1). That script is safe, it does not forward any port and the default POLICY is to DROP everything. 
[*] If it reports "Symmetric NAT" and that you are not using GNU/Linux, then you are not part of the 99% of lucky users. You will have to [COLOR=Red]forward UDP ports 5000 to 5100 to your internal machine[/COLOR]. Run the test again, it should report "Cone NAT" or "Port Restricted NAT" and it will work. 
[/LIST]

---

