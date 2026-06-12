---
title: "thunderbird --&gt; webmail hotmail"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by James Dee on 2009-03-01
hello,
i don't know what is happening but my hotmail in thunderbird is not working anymore. it stopped one week ago.
text mail is empty when i want to read it. attachment mail is empty or text in the size of attachment.
i try to change properties in the webmail, reinstall webmail, but it didn't help.
does anybody have some idea?
tnx
:confused:

---

### Post by ubername on 2009-03-01
> **James Dee said:**
> hello,
i don't know what is happening but my hotmail in thunderbird is not working anymore. it stopped one week ago.
text mail is empty when i want to read it. attachment mail is empty or text in the size of attachment.
i try to change properties in the webmail, reinstall webmail, but it didn't help.
does anybody have some idea?
tnx
:confused:

Hi

I had the same problem. The good news is that Hotmail now supports POP email standards so you don't need to use the webmail, add-on.  Check out 
[http://windowslivewire.spaces.live.com/Blog/cns!2F7EB29B42641D59!32413.entry](http://windowslivewire.spaces.live.com/Blog/cns!2F7EB29B42641D59!32413.entry)
for settings etc.

---

### Post by James Dee on 2009-03-01
> **ubername said:**
> Hi

I had the same problem. The good news is that Hotmail now supports POP email standards so you don't need to use the webmail, add-on.  Check out 
[http://windowslivewire.spaces.live.com/Blog/cns!2F7EB29B42641D59!32413.entry](http://windowslivewire.spaces.live.com/Blog/cns!2F7EB29B42641D59!32413.entry)
for settings etc.

Hello,
I change the account properties:

POP server: pop3.live.com (Port 995)  
POP SSL required? Yes
User name: Your Windows Live ID, for example [email]yourname@hotmail.com[/email]
Password: The password you usually use to sign in to Hotmail or Windows Live
SMTP server: smtp.live.com (Port 25)  
Authentication required? Yes (this matches your POP username and password)
TLS/SSL required? Yes

But it didn't help.

Receiving the mail:
First asks for password. Then Alert appears: 
Sending the password did not succeed. Mail server pop3.live.com responded: user does not have pop3 access

Is the problem that the POP3 is available in these countries United Kingdom, Canada, Australia, France, Japan, Spain, Germany, Italy, and the Netherlands and not in the Switzerland?

thnx

---

### Post by philinux on 2009-03-01
> **ubername said:**
> Hi

I had the same problem. The good news is that Hotmail now supports POP email standards so you don't need to use the webmail, add-on.  Check out 
[http://windowslivewire.spaces.live.com/Blog/cns!2F7EB29B42641D59!32413.entry](http://windowslivewire.spaces.live.com/Blog/cns!2F7EB29B42641D59!32413.entry)
for settings etc.

This is interesting. I'll give it a go too.

---

### Post by philinux on 2009-03-01
Just set my hotmail account up in evolution and it works. Did not specify the port either.

---

### Post by James Dee on 2009-03-01
Hello,
Problem sovled...
I opened new account on gmail few minutes ago. It is working perfect.
Tnx for everything

:popcorn:

---

### Post by philinux on 2009-03-01
Can receive but not send, just times out.

Error while performing operation.

Welcome response error: Connection reset by peer

---

