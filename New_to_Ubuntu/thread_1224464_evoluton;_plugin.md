---
title: "evoluton; plugin"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by Dedi Landsman on 2009-07-27
hi everybody. i have installed Wubi, i need some help please.
 
1. configuring my gmail account into Evolution. i have tried to work out  the Wizard, but didn't succeed, when i tried to send an Email i get a notification: "error while performing operation
host lookup failed: google: name or service not known"
here are some information the way my Email setting is in Outlook [which works fine]:
pop E-mail [tab]
server information:
incoming mail server [pop3]: pop. gmail.com
outgoing  mail server [SMTP]: smtp. gmail.com

2. i have just installed a plugin called: cfce4-cellmodem-plugin
i have verified that is indeed installed.
how can i get in up and running and to see the info display it suppose to give?
thank you very much for any help.

---

### Post by hggdh on 2009-07-27
Hello,

There is not much information provided (apart from the Google servers, which are correct, BTW).

On the Preferences/Account entry you have for this account:

* on the "Receiving email" tab
  * make sure "Use Secure Connection" is set to "SSL encryption"
  * make sure "Authentication Type" is set to "Password"
  * "Remember password" should be checked if you want Evo to remember the password,

* on the "Sending email" tab
  * make sure "Use Secure Connection" is set to "SSL encryption"
  * make sure "Authentication" is set to "Plain"
  * "username" should be set to your GMail userId without the '@gmail.com'
  * check "Remember password" if you so wish.

This should do the trick. GMail requires SSL to access the servers.

Also: you *must* set your GMail account for POP. See [http://mail.google.com/mail/?shva=1#settings/fwdandpop](http://mail.google.com/mail/?shva=1#settings/fwdandpop)

---

### Post by fballem on 2009-07-27
> **Dedi Landsman said:**
> hi everybody. i have installed Wubi, i need some help please.
 
1. configuring my gmail account into Evolution. i have tried to work out  the Wizard, but didn't succeed, when i tried to send an Email i get a notification: "error while performing operation
host lookup failed: google: name or service not known"
here are some information the way my Email setting is in Outlook [which works fine]:
pop E-mail [tab]
server information:
incoming mail server [pop3]: pop. gmail.com[COLOR="Red"]:995[/COLOR]
outgoing  mail server [SMTP]: smtp. gmail.com[COLOR="Red"]:465[/COLOR]

2. i have just installed a plugin called: cfce4-cellmodem-plugin
i have verified that is indeed installed.
how can i get in up and running and to see the info display it suppose to give?
thank you very much for any help.

Please note that you must add the port address, as shown above in [COLOR="Red"]this colour[/COLOR].

Also both incoming and outgoing connections need to be specified as SSL and both need to use a Password login, which should be identical. Do not use login to incoming before outgoing option.

I have been able to get gmail through evolution without error.

Hope that this helps,

---

### Post by Dedi Landsman on 2009-07-28
Hi, thanks very much for helping.
i tried to follow the tips i got here, but still couldn't get evolution sending mail, what could be wrong? i put the numbers as given by fballem, no change. afterwards i checked how it is set in Outlook [which works fine], the numbers there, for the incoming mail server are the same:995 , but for the outgoing  mail server it is different: 587 [instead of 465 given by fballem], i changed that, and still no success- when i tried to send an email, the Send button in evolution was even turned off. what could be the problem?
thanks for any help.

---

### Post by hggdh on 2009-07-28
I still do not know what version of Evolution you are using, and this might be playing a role.

As fballem stated, putting the port numbers should work -- but they should not be needed (I have not used it for GMail since I moved to Evo).

Anyway, you state the Send buttom was turned off. 

* Can you download email from other accounts?
* Can you *send* email to Google?

You can always try the "Check for Supported Types", which should find the valid login option, and automagically set it.

Additionally: did you set your GMail account for POP/SMTP?

Finally, you can always check if the server is responding, by TELNET-ting to it:

$ telnet smtp.gmail.com 587
Trying 72.14.247.109...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP 26sm2175721aga.24
^]

telnet> quit
$ Connection closed.

---

### Post by Dedi Landsman on 2009-07-29
hi, thanks very much for helping.
one possible area where i can think the problem might be is [in the account editor/wizard] in the sending mail tab, under 'authentication', type: plain is chosen [which is probably the default]. could that be the problem, should i mark something else there?
thanks for any help.

---

### Post by hggdh on 2009-07-29
Please see my posts and questions above.

---

### Post by Noo 2 Ubuntoo on 2009-11-02
As far as I know gmail always wants a password (which you would have set when you first registered with google for gmail) so you would have to set "authentication type" to "password", but leave sending authentication as "plain". Check you have got your account name, user name and e mail address for gmail correct. Beyond that, you could try setting the receiving mail tab on the wizard to "imap" for the server type and naming the server as "imap.gmail.com" to see if it receives from the imap server and just retrieve your mail via imap leaving your mail on the google server if your'e happy with that.

---

### Post by Dedi Landsman on 2009-11-03
Hi, Evolution [along with the gmail account] works fine on my Ubuntu , long time ago.:D
> you could try setting the receiving mail tab on the wizard to "imap" for the server typemy choice was POP, it works fine. and it seems to keep mails on the server.
Thanks.

---

