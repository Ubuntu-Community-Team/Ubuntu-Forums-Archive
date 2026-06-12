---
title: "plz help me to setup mail server with postfix, dovecot, fetchmail and a catchall"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by kameelperdza on 2009-07-03
Can someone help me to setup mail server with postfix, dovecot, fetchmail and catchall.
 
Im trying to setup email server. Fetchmail will download email from remote mailserver using [EMAIL="catchall@mydomain.com"]catchall@mydomain.com[/EMAIL], and then put it in the local [EMAIL="catchall@mydomain.com"]catchall@mydomain.com[/EMAIL]. Then is will be processed and delivered to local repecients etc [EMAIL="jack@mydomain.com"]jack@mydomain.com[/EMAIL]
 
Can someone please guide me through the steps of doing this. When i try to setup the mailserver then it download all the email to the postmasters email address, and is i remove the postmaster command inside fetchmailrc then all mail is send to catchall@localhost.
 
Ive been trying to setup the mailserver for over w months now, im is still strugling to setup it. Im very frustraed and dont know what to do next.
 
Any help would be appreciated.
 
thanx

---

### Post by HermanAB on 2009-07-03
Howdy,

First configure your network properly.  Your hostname must resolve in DNS or in /etc/hosts, for example "mail.example.com".  Only then can you start to work on a mail server - else you are just wasting your time since nothing will work and you won't know why.

The easiest mail server to get to work is Citadel, so start with that one.  You can try other mail servers another day, once you learned a few more tricks - mail is incredibly complicated. 

Go to the Citadel web site and run their Easy Install script:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

More information here:
[http://aeronetworks.ca/citadel-basics.html](http://aeronetworks.ca/citadel-basics.html)

Once CItadel is running, you can easily configure it to fetch mail from another server and forward mail via another server, exactly as you want to do - all described in their FAQ.

---

### Post by kameelperdza on 2009-07-03
Thanx i will go and take a look at that.
 
i followed this example
 
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)
 
i am able to send internally and to the outside world, but does not get any email in. My mail.log shows that mail is download and dilivered to maildir([EMAIL="postmaster@mydomain.com"]postmaster@mydomain.com[/EMAIL])
 
If i make my dns [www.mydomain.com]("http://www.mydomain.com") then all mail is relayed back to the remote mailserver.

---

