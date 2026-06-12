---
title: "Gmail Notify - Secure Connection?"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by Noo 2 Ubuntoo on 2010-09-28
The title says it all really. I've been using mail notification and found out it does not support secure connection to my gmail account, so I've been looking at this Gmail Notify gadget in the software centre (the one written in python) but can't work out if this connects securely via ssl. Does any one know?

---

### Post by jtarin on 2010-09-28
Suggestion...I use Evolution GMAIL/IMAP receive mail notifications locally.

---

### Post by Noo 2 Ubuntoo on 2010-09-29
What does   "receive mail  notifications locally" mean in leyman's terms? How would I set this up and would it mean I had to run evolution to be notified of new  e mails?

---

### Post by KIAaze on 2010-09-29
Yes, I think he means setting up evolution to access your mail account and leave it running. There are probably some notification options somewhere in evolution.

Evolution is a mail client like Outlook on Windows.
Another popular alternative to Evolution is Mozilla Thunderbird.

Here are some links about setting up evolution or other mail clients with gmail:
-Using IMAP:
[http://mail.google.com/support/bin/answer.py?hl=en&answer=75725](http://mail.google.com/support/bin/answer.py?hl=en&answer=75725)
[http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml](http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml)
[http://ubuntuforums.org/showthread.php?t=641590](http://ubuntuforums.org/showthread.php?t=641590)

-Using POP (not recommended*):
[http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)
[https://help.ubuntu.com/community/UsingGmailWithEvolution](https://help.ubuntu.com/community/UsingGmailWithEvolution)

*You can use POP or IMAP. I recommend IMAP, as it makes sure your mails remain on the gmail server.

---

### Post by Noo 2 Ubuntoo on 2010-09-29
> **KIAaze said:**
> Yes, I think he means setting up evolution to access your mail account and leave it running. There are probably some notification options somewhere in evolution.

Evolution is a mail client like Outlook on Windows.
Another popular alternative to Evolution is Mozilla Thunderbird.

Here are some links about setting up evolution or other mail clients with gmail:
-Using IMAP:
[http://mail.google.com/support/bin/answer.py?hl=en&answer=75725](http://mail.google.com/support/bin/answer.py?hl=en&answer=75725)
[http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml](http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml)
[http://ubuntuforums.org/showthread.php?t=641590](http://ubuntuforums.org/showthread.php?t=641590)

-Using POP (not recommended*):
[http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)
[https://help.ubuntu.com/community/UsingGmailWithEvolution](https://help.ubuntu.com/community/UsingGmailWithEvolution)

*You can use POP or IMAP. I recommend IMAP, as it makes sure your mails remain on the gmail server.

Thanks for the links. I already have my gmail linked to evolution although one of the tutorials cleared up the question as to why my gmail drafts kept appearing under "My computer" so it was worth the read for me.

However, I currently use mail notification so I don't have to have evolution running all the time. Gmail Notify (the one written in python) appears to link directly to the gmail account like mail notification, which is what I want it to do, only, **securely ** unlike mail notification which does not make a secure connection. So, anyone know if Gmail Notify links to the gmail account securely?

---

### Post by jtarin on 2010-09-29
There is this from their site:> bear in mind that the Notifier checks your mail in the same way that you would if you logged into their site normally,You can contact one of the devolpers [here]("mailto:juan.grande@gmail.com")

---

### Post by Noo 2 Ubuntoo on 2010-09-29
Thanks jtarin, I can see the implication that if it connects like you do when logging in normally it should be secure since Google used a secure connection to their server as a default following the alleged Chinese hacking activity earlier this year.

Think I will contact that developer because mail notification should be connecting securely too if the Google server default is always a secure connection, but it doesn't.

I'll see what the developer says and post the answer back here, assuming I don't told off for wasting his time with dumb questions.

---

### Post by Noo 2 Ubuntoo on 2010-09-30
Ok so the developer didn't reply and I continued researching, to eventually establish that Mail notification (which I currently use) **DOES** connect to gmail securely via port 443 as Mail Notification connects in the same way as a browser and given that all Google mail accounts are automatically set to a secure connection via browser it transpires that I never had a problem in the first place. Doh!!!

---

### Post by jtarin on 2010-09-30
It's good that you have reolved this to your own satisfaction. When it comes to security only you know your level of acceptance or rejection.

---

### Post by pveurshout on 2010-10-30
Does anyone know of a Gmail notification client, other than Mail Notification, which allows to send passwords in a secure way? I'm constantly getting error messages with Mail Notification, so I'm looking for an alternative.

---

### Post by Noo 2 Ubuntoo on 2010-10-31
> **pveurshout said:**
> Does anyone know of a Gmail notification client, other than Mail Notification, which allows to send passwords in a secure way? I'm constantly getting error messages with Mail Notification, so I'm looking for an alternative.

No, in a word but what are your error messages? as I'm using mail notification linked to my gmail account securely with no problems.

---

### Post by pveurshout on 2010-10-31
After installing I'm getting this:

[INDENT]**A fatal error has occurred in Mail Notification**
The default configuration has not been installed properly. Please check your Mail Notification installation.[/INDENT]

Actually, I've had it installed in the past and it did run, though it didn't work properly.

---

### Post by Noo 2 Ubuntoo on 2010-10-31
Have you installed via synaptic/Ubuntu software centre or direct from the mail notification site? If direct from the site then you could try uninstalling and reinstalling via synaptic/Ubuntu software centre as that will be a .deb file but the site has a tarball (.tar) file signature. 

Beyond that I'm afraid I can't help - I thought you mean't mail notification was installed OK but there were problems with getting mail notification to connect securely with gmail.

If you do have an install problem it's probably best t start your own thread as people with the answer may not look atthis thread which is about trying to get the Gmail Notify app to connect securely to gmail.

P.S. When I downloaded  the Gmail Notify app and ran it, it promptly disabled my number keypad and scroll lock key. Be warned!!

---

### Post by MSPdwalt on 2010-10-31
Try this one [http://bleedingpaper.com/gm-notify/](http://bleedingpaper.com/gm-notify/)

Also, to the OP, a great way to determine how a program talks over the network is to use a packet sniffer like wireshark.

---

### Post by pveurshout on 2010-11-01
> **Noo 2 Ubuntoo said:**
> Have you installed via synaptic/Ubuntu software centre or direct from the mail notification site? If direct from the site then you could try uninstalling and reinstalling via synaptic/Ubuntu software centre as that will be a .deb file but the site has a tarball (.tar) file signature. 

Beyond that I'm afraid I can't help - I thought you mean't mail notification was installed OK but there were problems with getting mail notification to connect securely with gmail.

If you do have an install problem it's probably best t start your own thread as people with the answer may not look atthis thread which is about trying to get the Gmail Notify app to connect securely to gmail.

P.S. When I downloaded  the Gmail Notify app and ran it, it promptly disabled my number keypad and scroll lock key. Be warned!!

Yeah, actually I did get it installed a few days ago, then removed it because it didn't work properly, and now it won't work at all. Oh well. Thanks for your help anyway! :) I installed via Synaptic/Software Centre, btw.

---

### Post by pveurshout on 2010-11-01
OK, maybe I got this error message because Mail Notification had been running in the background all along.. :shock: It seems to work well now I found the Settings manager for it under System -> Preferences. However, I did notice that the keyring where the password is saved by Mail Notification says 'protocol: http'. Shouldn't this be https for it to be secure?

port: 443
protocol: http
user: pveurshout
server: mail.google.com
authtype: basic

---

### Post by ufugu on 2010-11-01
You could also try [Popper]("http://www.omgubuntu.co.uk/2010/09/email-notification-in-ubuntu-popper/"), and awesome notifier that lives in the Indicator Applet.  It's highly configurable for any kind of mail account and uses SSL.  Very slick.

---

### Post by KIAaze on 2010-11-01
> **pveurshout said:**
> Yeah, actually I did get it installed a few days ago, then removed it because it didn't work properly, and now it won't work at all. Oh well. Thanks for your help anyway! :) I installed via Synaptic/Software Centre, btw.

A good solution to fix those kinds of problems is:
```
# remove the program + its global configuration files
sudo apt-get remove --purge PACKAGE
# remove the program's local configuration files, usually stored in some directory of the form ~/.*
rm -rf ~/.LOCATION_OF_CONFIG_DATA
# reinstall
sudo apt-get install PACKAGE

```

---

