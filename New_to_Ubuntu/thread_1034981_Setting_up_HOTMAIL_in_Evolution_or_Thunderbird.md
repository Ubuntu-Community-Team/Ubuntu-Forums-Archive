---
title: "Setting up HOTMAIL in Evolution or Thunderbird ???"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by delpol on 2009-01-09
I am a rookie exploring the wonderful world of LINUX. I finally got my sound card working. Thanks for everyones help.

Now my issue is setting up hotmail in the evolution / thunderbird. I have done step my step instructions for evolution but i keep in getting the "Unable to connect to the POP server 127.0.0.1. Error sending password".

Then i installed thunderbird and downloaded the latest webmail and hotmail plugins but in there i keep on getting the  "Negative vibes......" error. I tried webdav, hotmail and live settings for the plugin but still no help. I tried changing the port also for POP and SMTP from 110 / 25 to 2000/2500 and so on but still no luck in sending or receiving the emails.

i don't know which setting to test now.

please help as i would like to use the email functionality.

thanks
delpol

---

### Post by RobsterUK on 2009-01-09
127.0.0.1 is the default address for localhost, ie your PC which obviously isn't the mail server your trying to access

Assuming Hotmail support accessing your mail via POP, you need to check your settings to make sure the correct server is specified. If Hotmail does support POP then the address of the server should be somewhere on the hotmail/msn website.

---

### Post by Facetious Falcon on 2009-01-09
I think hotmail is one of few emails which can only be accessed via http which is annoying. If someone has got it working in Evolution that would be awesome, as I've been wanting to do that for a while but I believe it's most likely impossible due to restrictions by hotmail itself.

---

### Post by Captain_tux on 2009-01-09
Same thing with Yahoo... unless you pay for their premium service.

---

### Post by RobsterUK on 2009-01-09
You may want to have a look at the Webmail plugin for Thunderbird:
[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

On the download page right click and download the file then open it in Thunderbird otherwise it will try and install it in Firefox.

---

### Post by halovivek on 2009-01-09
> **Captain_tux said:**
> Same thing with Yahoo... unless you pay for their premium service.

You can yahoo zimbra and it is free and you can setup all accounts. i am using that one only. try it from this [link]("http://ubuntuforums.org/showthread.php?t=1030223&highlight=yahoo+zimbra")

---

### Post by delpol on 2009-01-09
> **RobsterUK said:**
> You may want to have a look at the Webmail plugin for Thunderbird:
[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

On the download page right click and download the file then open it in Thunderbird otherwise it will try and install it in Firefox.
i already tried doing that but still same error "getting negative vibes........" i even chnaged my hotmail password but still can't get to work. thunderbird used to work just fine when i had xp and vista.

please help

---

### Post by hyper_ch on 2009-01-09
[http://ubuntuforums.org/showpost.php?p=6443426&postcount=10](http://ubuntuforums.org/showpost.php?p=6443426&postcount=10)

---

### Post by delpol on 2009-01-09
> **hyper_ch said:**
> [http://ubuntuforums.org/showpost.php?p=6443426&postcount=10](http://ubuntuforums.org/showpost.php?p=6443426&postcount=10)
still no help, tried reinstalling thunderbird did everything step by step.

please help

---

### Post by delpol on 2009-01-09
its only saying for yahoo though, will it work for hotmail.
for me even evolution is not working after step by step instructions from the forums site.
please assist.
thanks

---

### Post by IBUA on 2009-06-06
I know this is a bit late  but :P

For Hotmail:

"POP3

POP3 access is now available for all Hotmail accounts, adding support to access Hotmail from any email client – most notably mobile devices.[5]
POP3 Settings:
POP server: pop3.live.com (Port 995)
POP SSL required? Yes
User name: Your Windows Live ID, for example [email]yourname@hotmail.com[/email]
Password: The password you usually use to sign in to Hotmail or Windows Live
SMTP server: smtp.live.com (Port 25 or 587)
Authentication required? Yes (this matches your POP username and password)
TLS/SSL required? Yes"

- from wikipedia :P

---

### Post by andersonluk on 2009-06-13
For hotmail.

Receiving Email setting is correct.  I can receive mails.

But Sending Email setting is not correct.  Any suggestion?

---

### Post by mike555 on 2009-06-13
make sure your sending (smtp) is set as smtp.live.com   port 587 , tls

---

### Post by Ms_Angel_D on 2009-06-13
Also it's in the community documentation: [https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution)

---

### Post by halitech on 2009-06-13
> **andersonluk said:**
> For hotmail.

Receiving Email setting is correct.  I can receive mails.

But Sending Email setting is not correct.  Any suggestion?

what happens when you try to send mail? ie what error message do you get?

it's possible that your ISP may have blocked port 587. Open a terminal and see if you can connect with telnet
```
telnet smtp.live.com 587
```

---

### Post by leonardo_neo on 2009-12-21
> **Ms_Angel_D said:**
> Also it's in the community documentation: [https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution)

@ Ms_Angel_D

Thanks a lot!! This helped me :)

---

### Post by gavin.duvall on 2010-01-09
how do i change the port info... i cant find port setting...

---

### Post by dwp0980 on 2010-02-23
> **gavin.duvall said:**
> how do i change the port info... i cant find port setting...

In Evolution, you just type it at the end of the pop/smtp address - e.g.

pop3.live.com:995

and

smtp.live.com:587

---

### Post by nuffink666 on 2010-12-01
If your using T-bird it is even easier just go to account settings - add account - type in your full hotmail address for the name and the email address - type in your password and mozilla searches its own ISP database for the settings - sorted - easy peasey lemon squeezy, no plugins needed just as it says on the tin =D>

---

