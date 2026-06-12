---
title: "Help with internet connection and webserver"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by AnthonyArde2 on 2008-04-01
Hi all, 
i have a question about my ubuntu 7.10 webserver i am setting up.

as i understand it i require a public static IP for my server, so when http requests come in i have to have my router set it to forward the information etc to my servers internal IP, is this correct?

Now my questions is, if i have to forward port 80 to this computer for example, will this make it so that other computer on my network wont be able to share this internet connection?

This is a serious question/problem for me, i have one satellite connection which is required to run a full webserver, with dns mail etc and have +-13 other computers sharing the same connection to use for regular internet,

is this possible?

---

### Post by stalker145 on 2008-04-01
> **AnthonyArde2 said:**
> Now my questions is, if i have to forward port 80 to this computer for example, will this make it so that other computer on my network wont be able to share this internet connection?

If I am understanding your question correctly...

Are you asking if the other computers will be able to browse the internet while your server serves web pages to people requesting them?

If that is what you are asking, then worry not. You will be fine. I currently have one computer serving my web page at port 80 and 4 other computers on my LAN that can do anything and everything (except serve to outside computers on port 80) without issue. Browsing will be fine.

---

### Post by AnthonyArde2 on 2008-04-01
That is excellent news, thanks very much!

i am going to try do this with bind9, what is your configuration, eg.

i would like to have my ubuntu server on my network along with +- 13 other computers running windows. 

do i have to have them on a local domain or can i simply have my router running dhcp with my server having a staic IP.

the webhost ubuntu computer will have to make use of mysql, host my websites domain name, and email for this domain name mail etc, is this ok?

also will i be able to run more than one web domain with this setup, eg: maybe host other peoples websites, and other domain names that my company owns and have mail handeled from it.

i`m new to what a server can actually hadle, if this is possible - how may wesites could i run off a computer like this running off a satellite connection at the speed of 2048Kbps and an upload of 128 Kbps?

Thanks for your assistance.

---

### Post by stalker145 on 2008-04-01
> **AnthonyArde2 said:**
> That is excellent news, thanks very much!

i am going to try do this with bind9, what is your configuration, eg.

i would like to have my ubuntu server on my network along with +- 13 other computers running windows. 

I don't use bind9 or any other DNS-type stuff on my network. For access to my server, I simply have ports 80, 22, and 443 forwarded (HTTP, SSH, HTTPS). My server is the only machine that has any forwarded ports and, as noted, is the only one running a static IP - all others are DHCP.

> **AnthonyArde2 said:**
> do i have to have them on a local domain or can i simply have my router running dhcp with my server having a staic IP. 

You do not *need* to have all of the computers on the domain. Heck, you don't even *have* to have your server on the domain depending on what you're serving (see my below disclaimer regarding email).

> **AnthonyArde2 said:**
> the webhost ubuntu computer will have to make use of mysql, host my websites domain name, and email for this domain name mail etc, is this ok?

I don't have experience with running an email server (I've failed miserably for years). I use Google Apps for my email. As for running MySQL and your domains, as long as you are familiar with the setup, it'll be rather painless to run this on your LAN/WAN.

> **AnthonyArde2 said:**
> also will i be able to run more than one web domain with this setup, eg: maybe host other peoples websites, and other domain names that my company owns and have mail handeled from it.

Yes. You will need to set up Apache to recognize the domain name requested by the browser and have those domains sent to your IP/DynamicDNS. In the past, I had three domain names run from a PII 233 without issue.

> **AnthonyArde2 said:**
> i`m new to what a server can actually hadle, if this is possible - how may wesites could i run off a computer like this running off a satellite connection at the speed of 2048Kbps and an upload of 128 Kbps?

This all depends on what you are hosting. If you're hosting video, audio, or large files through email, you will probably want to keep the number of domains to a minimum. If you're only hosting web pages, then you will be good for several domains. Just make sure to keep in mind the number of possible users multiplied by the number of domains and factoring in the types of files and your server's abilities.

---

### Post by AnthonyArde2 on 2008-04-01
thanks for the advice, i require to be completely self sufficient, so i`ll let you know if i get the mail server right :)

thanks again.

Anthony

---

