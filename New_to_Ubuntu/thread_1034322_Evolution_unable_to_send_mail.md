---
title: "Evolution unable to send mail"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by cjnkns on 2009-01-08
I am trying to configure Evolution to send/receive mail from my gmail account.

I have done this before following the same steps so this leads me to believe there are other issues. Anyway, I am able to download my email just fine but when I try to send I get an error at the bottom right of Evloution saying that 'Error while performing operation'

If I click on the little yield sign the message says. "Could not connect to smtp.gmail.com: Input/Output error"

Anybody else have this issue?

---

### Post by theinnercityhippy on 2009-01-08
Is it possible that you have a firewall running that is blocking the port that smtp is trying to send from, or that the portyou have specified differs from those given on he settings page for gmail.

If the worst comes to the worst, I would reccommend giving thunderbird a try as this has better intergration for add ons such as the excellent enigmail.

Also check that it is SSL encrypted fr outgoing mail in your settings.

-JimDog-

---

### Post by hermes0710 on 2009-01-08
> **theinnercityhippy said:**
> Is it possible that you have a firewall running that is blocking the port that smtp is trying to send from, or that the portyou have specified differs from those given on he settings page for gmail.

If the worst comes to the worst, I would reccommend giving thunderbird a try as this has better intergration for add ons such as the excellent enigmail.

Also check that it is SSL encrypted fr outgoing mail in your settings.

-JimDog-

Run this command on a terminal:
```
ping smtp.gmail.com
```
in order to find out if you have access to this server. If you get responses then press ctrl+c to end the ping command.

Did you select to use ssl for the outgoing messages? If yes, what type did you choose for the password manipulation?

---

### Post by WildeBeest on 2009-01-08
I have the exact same problem and started a thread on it a while ago with no resolution.

See: [http://ubuntuforums.org/showthread.php?t=951870](http://ubuntuforums.org/showthread.php?t=951870)

I have one gmail account and two aols.

Using Thunderbird now.

---

### Post by theinnercityhippy on 2009-01-08
In a terminal, try typing

user@ubuntu:~$ host smtp.gmail.com

This will tell you if your connection will resolve the adress, if not it is a connectivity problem or a problem at their end which should be resolved quickly. Make sure you follow these instructions carefully, as these are generic instructions and some of the options differ slightly or may not be obvious:

[http://mail.google.com/support/bin/answer.py?answer=13287](http://mail.google.com/support/bin/answer.py?answer=13287)

If you are still having problems I will try and walk through it with you step by step over IM.

(note, are you using pop3 or imap? ensure the relevent checkboxes in the gmail settings page are ticked to allow that kind of access)

-JimDog-

---

### Post by WildeBeest on 2009-01-08
So why does thunderbird work?

Same settings as I have in Evolution.

---

### Post by theinnercityhippy on 2009-01-08
> **WildeBeest said:**
> So why does thunderbird work?

Same settings as I have in Evolution.

Not sure but I have had similar problems myself in the past. In the end it all came down to the number of the port I was using to send mail. This is very important. Also, google and Mozilla tend to work very closely together and so thunderbird (Mozilla - makers of firefox) is officially supported by google as a mail client.

One thing to double check, daft as it sounds, there is a button in the bottom left corner of the screen which you sometimes have to manually click to connect to the internet as Network Manager sometimes fails to send it's online status to the program, making it think it is working in offline mode. This is a pasrticular problem with ppp connections such as those used by mobile broadband dongles, or if you are using another program to connect to the internet such as KPPP.

-JimDog-

---

### Post by WildeBeest on 2009-01-08
Have tried that, checked, re-checked, and re-checked my settings again and again no luck. I can receive mail fine with Evolution but not send with aol or gmail.

I give up on Evolution.

---

### Post by theinnercityhippy on 2009-01-08
> **WildeBeest said:**
> Have tried that, checked, re-checked, and re-checked my settings again and again no luck. I can receive mail fine with Evolution but not send with aol or gmail.

I give up on Evolution.

Make sure that your firewall isn't blocking the outgoing port, although if t's sending in other programs it probably isn't that. I reckon it's down to the authentication you are sending to the outgoing server being wrong somehow. I have mine set that I have to manually enter my password to send as well as receive mail as a security measure and this tends to work fine for me.

As I said though, I have switched to thunderbird because of the support for enigmail.

 Wouldn't blame you, it's a shame that evolution can be so frustrating sometimes as visually it is the best client for new users. Sigh.

Try these:

[http://ubuntuforums.org/showthread.php?t=793609](http://ubuntuforums.org/showthread.php?t=793609)

[http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)

---

### Post by greg.harvey on 2009-05-04
It is just the port. Set your SMTP server address to:

smtp.gmail.com:587

Error will go and all will be fine. This is not unique to Gmail - I have hosting with eApps who also have SMTP on 587 so require the same treatment.

I personally have nothing good to say about Thunderbird. I found the IMAP support extremely slow, the add-ons buggy and the application generally not fit for commercial use, which is why I switched BACK to Evolution, which has never given me any problems. Just for the record. :)

---

### Post by WildeBeest on 2009-05-04
I have just the opposite opinion. Thunderbird works great for me. Never any problems. Evolution OTH, is very problematic, clumsy, and just not a very good e-mail client.
Thunderbird should be the default mail appliction for Ubuntu.
 
JMHO

---

### Post by ene_dene on 2009-06-15
> **greg.harvey said:**
> It is just the port. Set your SMTP server address to:

smtp.gmail.com:587

Error will go and all will be fine. This is not unique to Gmail - I have hosting with eApps who also have SMTP on 587 so require the same treatment.
This problem arose two days ago by it self. This has solved my problem, thanks.

---

### Post by runesvend on 2010-02-24
> **greg.harvey said:**
> It is just the port. Set your SMTP server address to:

smtp.gmail.com:587

Error will go and all will be fine. This is not unique to Gmail - I have hosting with eApps who also have SMTP on 587 so require the same treatment.
This works for me as well. I haven't touched in of my mail settings for like a year and have been sending mails fine until this issue appeared. But for some reason this resolved the issue for me.

Thanks!

---

### Post by tonytiger on 2010-03-20
Ok,
Is started to use Evolution. Looks nice, but can't send email. I have tried to use the same smtp servers I have used successfully with Thunderbird.

In my case when I hit send/receive button emails are received nicely, but nothing happens with the sending email. No errors, nothing happens. I have double checked the account settings and defined correct port by smtp.welho.com:465 (also tried with out the :465) .

Any ideas, or should I just stick with Tbird? I'm using freshly installed Karmic Koala if that matters.

Thanks!

-Tony

---

### Post by damilaredavids on 2010-05-10
After so many frustrating weeks of research and tweaks, i finally was able to send mails using Evolution successfully without the input/output errors.

I included a screenshot of my SMTP setup page...

---

### Post by barnabasbarty on 2012-02-02
> **cjnkns said:**
> I am trying to configure Evolution to send/receive mail from my gmail account.

I have done this before following the same steps so this leads me to believe there are other issues. Anyway, I am able to download my email just fine but when I try to send I get an error at the bottom right of Evloution saying that 'Error while performing operation'

If I click on the little yield sign the message says. "Could not connect to smtp.gmail.com: Input/Output error"

Anybody else have this issue?
If all send and receive settings are good, I was finally able to send email in Evolution with my Gmail account when I made the Username for the Evolution email account the same as the Username I used to create the Gmail account.  Hope this helps.

---

