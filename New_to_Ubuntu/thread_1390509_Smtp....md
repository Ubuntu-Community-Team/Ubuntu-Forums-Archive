---
title: "Smtp..."
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Hovercat on 2010-01-25
Hello, I'm trying to set up an SMTP server, but none of the postfix tutorials on the internet seem to help. I have the domain set up ( [http://smtp.asskickersunited.com](http://smtp.asskickersunited.com) ) but it just brings me to my forums. However, I think it's supposed to do that. But, how do I create an E-mail account on postfix? After I do so, what will be my username so I can use this SMTP server on my PHPbb3 board?

---

### Post by halitech on 2010-01-25
are you trying to setup the smtp server on your home server or a hosted site? Is the domain pointed to your home server or a hosted site?

Did you set up the subdomain to point to where ever you want the server to be hosted from?

---

### Post by Hovercat on 2010-01-25
Home server. The subdomain is pointed to my server, since using the company's server who registered my domain is too difficult, so I pointed everything to my IP.

---

### Post by halitech on 2010-01-25
did you setup the subdomain for smtp and point it to your home server?

---

### Post by Hovercat on 2010-01-26
Yes I did.

---

### Post by halitech on 2010-01-26
did you set up the info with the DNS servers or in apache or where?

---

### Post by Hovercat on 2010-01-27
I pointed "smtp" to "173.2.183.98" in my DNS form of the control panel of the company who registered my domain. I do not have a smtp record in apache. I suppose that's needed? But anyway, I have a question someone might be able to answer, I have E-Mails set up on the control panel, what is the username for that? I really need it for my PHPbb board.

---

### Post by halitech on 2010-01-27
I believe you would need to tell apache that if a request comes in for smtp.xxx that it is supposed to point it to /var/www/smtp or where ever you have the files located.

If you set up mails in your hosting companies control panel, you would need to get that info from them

---

### Post by Hovercat on 2010-01-27
Alright. Forget the custom mail server, I have no clues how to set up user accounts and it'll probably just be too much of a hassle.

---

