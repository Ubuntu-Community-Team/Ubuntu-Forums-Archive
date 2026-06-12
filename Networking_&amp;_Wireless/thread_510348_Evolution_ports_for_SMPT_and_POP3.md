---
title: "Evolution ports for SMPT and POP3"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by CHFFriday on 2007-07-26
I use Evolution as my e-mail client.
Here is my problem: My ISP is going to change over to SSL for POP and SMTP. They are going to also change FROM the standard POP and SMTP (25 & 110). 

Is there somewhere in Evolution or Ubuntu 7.04 that I can change the ports?

CHFFriday

---

### Post by obrient on 2007-07-26
In Evolution you should be able to change this. Go to **Edit>Preferences** and then choose your account, and click edit. You should then be able to change the POP3 settings and IMAP to use SSL. 


In regards to the port change I am not totally sure, but if indeed they are changing ports, but not addresses you should be able to add **:port#** to the end of the address.

---

### Post by CHFFriday on 2007-07-26
Thanks for the response. I have changed the accounts to SSL. The reason I ask the question is they sent directions on how to change Outlook setting. I checked and you can change the ports. I tested and if the port is not right, you can not send e-mail. Maybe in Evolution you do not need to set the ports. 
Do you know anything about this?

I did not know about adding the port number. I will test this.

CHFFriday

---

