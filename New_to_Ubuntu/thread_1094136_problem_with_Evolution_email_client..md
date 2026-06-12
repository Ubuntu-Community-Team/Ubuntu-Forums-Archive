---
title: "problem with Evolution email client."
date: 2009-03-12
forum: New to Ubuntu
---

### Post by cptrohn on 2009-03-12
Hi, I hadn't really set up evolution until the other day and I have run into some kind of a problem..

I tried to set it up for my gmail account, I put in the pop and smtp settings that gmail had listed, but evolution won't get my new mail and I am also not able to send mail with it as well...


Did I do anything wrong or miss something in the setup process?

---

### Post by kanikilu on 2009-03-12
Obvious question, but is POP already enabled in your Gmail settings?

---

### Post by cptrohn on 2009-03-12
> **kanikilu said:**
> Obvious question, but is POP already enabled in your Gmail settings?

Maybe not so obvious, I really do not know.... I haven't used gmail all that long as my primary email account because I had an AT&T DSL connection and just changed providers..

I know I never had to enable pop with the other email account.. I will check this on gmail though.

---

### Post by cptrohn on 2009-03-12
OK..

Yes POP and IMAP were both enabled...

---

### Post by philinux on 2009-03-12
[http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)

---

### Post by cptrohn on 2009-03-12
> **philinux said:**
> [http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)

Thanks for the link, but that is how I set it up and still nothing...

I get an error retrieving messages and an error when I try to send a test email as well....

---

### Post by cptrohn on 2009-03-12
Is there a way to just clear the setting for evolution and start over and try again?

---

### Post by philinux on 2009-03-12
Edit>prefs>mail account>Delete.

However maybe it needs the ports setting up. For instance to get hotmail up and running I had to use this.
pop3.live.com:995 for receiving and ssl encryption. Not sure of the port for gmail though. And port 25 and tsl for sending.

---

### Post by Ms_Angel_D on 2009-03-12
> **cptrohn said:**
> Is there a way to just clear the setting for evolution and start over and try again?

Go into edit->preferences and delete the account then click add account to start over

I use evolution for gmail imap access and it doesn't require any port settings for me, so I would try starting over following the tutorial above first, then add ports if that doesn't work.

---

### Post by philinux on 2009-03-12
Here you go.

[http://mail.google.com/support/bin/answer.py?hl=en&answer=13287](http://mail.google.com/support/bin/answer.py?hl=en&answer=13287)

---

### Post by cptrohn on 2009-03-12
> **MetalHellsAngel said:**
> Go into edit->preferences and delete the account then click add account to start over

I use evolution for gmail imap access and it doesn't require any port settings for me, so I would try starting over following the tutorial above first, then add ports if that doesn't work.

Yeah, I'll just try it again... I might have just entered something wrong..

---

### Post by cptrohn on 2009-03-12
Thanks everybody who helped, it's working great now...


I entered a couple of things wrong at setup.

---

### Post by caco on 2009-05-09
Hello folks, [http://ubuntuforums.org/showthread.php?t=1143295](http://ubuntuforums.org/showthread.php?t=1143295) might be interesting to read.

---

