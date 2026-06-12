---
title: "Mail Server Half Working"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by mgbolts on 2011-07-11
Hi,

I have just finished building my first mail server. I have installed postfix, dovecot and squirrelmail (plus Lamp).

Squirrelmail seems ok and so does lamp. These were tested in the lan and using the domain. Seems all good.

Question 1: I can send mail but cant receive mail? 

Question 2: Also, the mail received externally arrives from:

[email]user@servername.domain.com[/email] (as compared to [email]user@domain.com[/email])

(I can fix this by sending as through the client. Not sure if this correct or symptomatic of some other issue though).

My firewall port settings seem ok.

Any assistance would be appreciated.

Thanks

---

### Post by SeijiSensei on 2011-07-11
Have you read your ISP's Terms of Service?  Are servers prohibited on your connection?  Some ISPs block port 25 to enforce this rule.

If not, do you have port 25 forwarded from your router back to the server?

---

### Post by mgbolts on 2011-07-13
Hi,

Thanks for your response. These both appear to be ok (see explanation below)

I have a NAS box with built in mail server which I managed to get working. This required my ISP to deactivate the port 25 block. I also forwarded port 25 to the LAN IP.

BTW, I did this test command which was successful.

echo "Hello me" | mail -s "Dovecot test" $USER

---

### Post by skitter on 2011-07-13
Q1.  

Does your server have valid MX records in DNS?  In other words, can a machine on a network external to your mail server do a DNS look up on it? You can test MX records with a machine external to your network by opening a terminal (command line) and running:

NSLOOKUP -q=mx {YourDomain.com}

If the NSLOOKUP works, do the MX records point at your server? 

If you have DNS squared away, you can test connectivity. 

Assuming port 25 isn't blocked on either end, you can test connectivity from a machine external to the network your server like this:

Open a terminal (command line) and run:

telnet {your server's IP} 25
helo test
mail from: [email]TestAddress@TestDomain.com[/email]
rcpt to: [email]ValidAddress@YourDomain.com[/email]
data
.


Note that there is a space beween the server IP and port 25.
Also note that there is only one L in helo.

Replace test address and valid address with addresses that are valid for your situation.


I hope that helps.

---

### Post by mgbolts on 2011-07-13
Thanks, I will give it a go.

---

