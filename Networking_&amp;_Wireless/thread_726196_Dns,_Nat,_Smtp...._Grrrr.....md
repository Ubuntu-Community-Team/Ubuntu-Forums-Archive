---
title: "Dns, Nat, Smtp.... Grrrr...."
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by Zwack on 2008-03-16
Greetings,

A long time ago, in a galaxy..... Whoops....

I realise that this isn't strictly an Ubuntu problem...

Several years ago I used to work for an ISP... I had connectivity through them including my DNS...  Time passed, I changed jobs I got a DSL connection to home (in a different country) but because of my proximity to the CO (or lack of it) I had to get a business class SDSL connection.  Given the monthly cost they would let me do almost anything and would even be helpful by pointing reverse addresses for me...

Even later still I moved again (CO is less than a five minute walk away) got an ADSL connection and changed ISPs again.  So... my setup has moved once or twice and has some legacy "issues"...

The current problem...  SMTP traffic from my mail server is currently being bounced by some <controls himself> people because the domain name from the email address does not match the reverse that the service provider provides.  I realise I might be able to fix this by reconfiguring everything to account for other people's shortsightedness, but I cant see any alternative that would allow me to keep my domain name.  Is there one?

Current DNS resolution...

Mx record points to A record which gives an IP address.  The IP address has a reverse which points to a different name which resolves back to the IP address.  i.e. if you take the IP address and get the name and then take the name you get back to the IP address.  This works as it should.  However if you take the domain name from the headers of the e-mail and ask for the IP address of the mail server, and then reverse that you get a different name.

Yes, I realise that the MX record should point to the other name but as I said this is a legacy set up and to make that work I'd have to change the name on the mail server as well, and even then I'm not sure it would work with their mail set up.

(I hate spam, but so many anti-spam solutions seem to cause almost as many problems).

Z.

---

### Post by PhrygianCat on 2008-03-17
You should ask your ISP to create a reverse DNS lookup entry for your IP address, assuming you have business DSL. Knowing that you have ADSL, you might be out of luck, unless you use some DDNS.

---

