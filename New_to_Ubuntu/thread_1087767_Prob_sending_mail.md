---
title: "Prob sending mail"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by nnjond on 2009-03-05
Hi, i've switched isp but now when i try to send mail in Evolution i get an error mssge

Welcome response error: aamtaout01-winn.ispmail.ntl.com connection refused from [87.115.73.83

Anyone know what im doing wrong?

---

### Post by LowSky on 2009-03-05
you probalby need to reset up yor account. Any email adreses that yuo had from the old ISP will not work.

---

### Post by nnjond on 2009-03-05
thanks for your interest. ibelieve i completed the wizard correctly and recieve mail. but can't send any.

---

### Post by chamber on 2009-03-05
What are the SMTP settings then?

---

### Post by nnjond on 2009-03-05
thanks for your interst. I'm not sure what you mean by smpt settings.

I was only asked for server configuration under sending email.

---

### Post by avtolle on 2009-03-05
SMTP settings are the server settings for sending email, in most (if not all) instances.

---

### Post by linuxuser21 on 2009-03-05
SMTP is the server that it connects to send messages.  It'd be my first guess on why it's not sending messages.

---

### Post by chamber on 2009-03-05
Go to the account settings and go to the sending e mail or SMTP settings section, 

Check what the settings are, what is the server address, what is the port, is the authorisation required box ticked?

What is the mail account that your trying to set up?

---

### Post by nnjond on 2009-03-05
server type: SMTP
Server:  relay.plus.net
no encryption
Server requires authentication is ticked
authentication: PLAIN
ussername: XXXXX
remember password

---

### Post by chamber on 2009-03-05
Try changing the encryption.

---

### Post by nnjond on 2009-03-05
changing encrption doesnt work

---

### Post by avtolle on 2009-03-05
Taking a look at [http://www.plus.net/support/email/outlookexpress_mail.shtml](http://www.plus.net/support/email/outlookexpress_mail.shtml) (granted, it is for outlook express) suggests that if encountering difficulty with outgoing (SMTP), changing the name of the server to relay1.plus.net might help. Good luck.

---

