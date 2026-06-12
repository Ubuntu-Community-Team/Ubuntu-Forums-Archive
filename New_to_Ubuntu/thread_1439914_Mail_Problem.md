---
title: "Mail Problem"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by oscarrodas on 2010-03-26
Hi there, can anyone hep? I&#7743; having problems with Evolution Mail, having the following message everytime I try to send/receive mail: "Error while fetching mail, failed to read a valid greeting from POP server Optusnet'
Optusnet is my mail server and it works ok with windows 7.

the settings are: Send mail: mail.optusnet.com.au (pop)
receive mail: mail.optusnet.com.au (smtp)
Evolution doesn give me the option of putting a password when checking mail which is required by the server.
The server is a POP3 but the only option I see is POP;
Any help will be appreciated.
Oscar

---

### Post by wojox on 2010-03-26
> **oscarrodas said:**
> 
the settings are: Send mail: mail.optusnet.com.au (pop)
receive mail: mail.optusnet.com.au (smtp)


You send mail with SMTP and receive with POP

---

### Post by oscarrodas on 2010-03-26
Yes, that&#347; the original option but it doesn work, I have tried every posible combination but it doesn work, the odd thing is that it actually worked with Karmic 9.1 but I had a lot of issues with it and eventually gave up.....

---

### Post by gmargo on 2010-03-27
> **oscarrodas said:**
> 
Evolution doesn give me the option of putting a password when checking mail which is required by the server.
The server is a POP3 but the only option I see is POP;


Evolution will prompt you for the password the first time that you connect.  There's a checkbox in the setup screen that says "Remember password" - if you hover the mouse over that text, a tooltip pops up which says "Note: you will not be prompted for a password until you connect for the first time."

Don't worry about POP vs POP3, evolution is using POP3.

The addresses you supplied look fine, and send vs receive is irrelevant since they are the same address.  I checked the addresses against this page: [http://help.optuszoo.com.au/help/dsl/connected](http://help.optuszoo.com.au/help/dsl/connected)

---

### Post by oscarrodas on 2010-03-27
Thank you, but it looks that it has to do with the network, when I look it gives me a generic network under Wired, if I set one under DSL, with all my details, it never shows as available.....

---

### Post by philinux on 2010-03-27
Try tsl and ssl and you might need to specify the correct port.

---

### Post by oscarrodas on 2010-03-29
Thanks Philinux, I did as you suggested and was able to enter all the information, the error messages are gone but for some reason Evolution is unable to fetch my mail, when I click the tab Send/Receive I see a dialog box but it flashes to quick to find out what it says. I now I have mail because my friends keep asking why I haven't answered...That is the only issue I have with Lucid 10.4 beta 1. Thank you...

---

