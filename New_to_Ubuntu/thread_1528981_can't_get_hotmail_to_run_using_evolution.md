---
title: "can't get hotmail to run using evolution"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by pvirobik on 2010-07-11
the program first one is my signon one.    that’s ok. 

  the second one  expects this one i can’t indentify. 

then the tries and just time out i  get: 
 

Error while Sending message.


 "Could not connect to smtp.live.com:   Connection timed out"
  

the program first one is my signon one.  that’s ok. 

  the second one  expects this one i can’t indentify. 

 then the tries and just time out i  get: 


do the second pw is for?

---

### Post by Gone fishing on 2010-07-11
I found these settings which may help you:

    *  POP server: pop3.live.com (Port 995)
    * POP SSL required? Yes
    * User name: Your Windows Live ID, for example [email]yourname@hotmail.com[/email]
    * Password: The password you usually use to sign in to Hotmail or Windows Live
    * SMTP server: smtp.live.com (Port 25) {Note: If port 25 has been blocked in your network or by your ISP, you can set SMTP port to 587 with TLS or SSL Encryption depending on the client in use}
    * Authentication required? Yes (this matches your POP username and password)
    * TLS/SSL required? Yes

Hope that helps

---

### Post by pvirobik on 2010-07-12
where do i get the: 

i get only: "Password, APOP, Login, NTLM / SPA, GSSAPI, DIGEST-MDS, CRAM-MDS"

i don't a place for "Hotmail or Windows Live"!

---

### Post by Gone fishing on 2010-07-13
Sorry not to reply earlier but I use Thunderbird - which I find a little easier to setup.

However, this is how:

Open Evolution the Edit > preferences and then edit the account

Select the receiving mail tab make the Server type POP3 and the server pop3.live.com

Use secure connection SSL encryption it will then check for supported types and leave you with Password make sure your username has the @msn.com or @hotmail.com or whatever.

Now select the Sending email tab

Server type SMTP and server smtp.live.com

use secure connection TLS type PLAIN add the username including the @hotmail.com

and your done (you probably want to tick the remember passwords)

---

