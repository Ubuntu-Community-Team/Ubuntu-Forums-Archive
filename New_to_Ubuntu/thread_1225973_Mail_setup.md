---
title: "Mail setup"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by hyperAura on 2009-07-29
Hey, i will try explain this as clearly as i can.. I have a hotmail account and i want to set it up on ubuntu to be able to read my mail using the mail command through shell and send messages through that.. if anyone knows how to do it help me please.. thnx!!

---

### Post by kkady32 on 2009-07-29
for that u need mutt and maybe fetchmail,but how cann setup i dont know,read documentation

---

### Post by t0p on 2009-07-29
I set up my desktop computer to do this with my gmail account.  Unfortunately I am not at home so I can't give you helpful links.  But the packages you will need to do it are **fetchmail** and (I think) **procmail** (to receive the email via pop3) and **exim4** (to send the email via smtp).  Google for docs, something like **+fetchmail+pop3** and **+exim4+smtp**.

---

### Post by hyperAura on 2009-07-29
thnx i will try ur recommendations i will come back to u if i have any problems..

---

### Post by hyperAura on 2009-07-29
so ive installed fetchmaill procmail and exim4..

ive also found the settings for my hotmail account

  POP server: pop3.live.com 
&#8226;    POP server port: 995 
&#8226;    POP SSL required? Yes 
&#8226;    User name: Your Windows Live ID, for example [email]yourname@hotmail.com[/email] 
&#8226;    Password: The password you usually use to sign in to Hotmail or Windows Live 
&#8226;    SMTP server: smtp.live.com 
&#8226;    SMTP server port: 25 
&#8226;    SMTP Authentication required? Yes (same as POP3 username and password) 
&#8226;    SMTP SSL required? Yes 

after reading the configuration section of fetchmail manual i used the command 

poll pop3.live.com protocol pop3 usename "smithsj" password "ucantfindit" ssl

but i get bash: poll: command not found

how should i start the setup? ive looked for the rc file of fetchmail but no luck..

also before installing fetchmail procmail and exim4 i tried sending test emails through the shell and i found all the messages now not sent in a file at  /var/mail/username..

should i delete the contents of that file?

---

### Post by t0p on 2009-07-29
Okay, here are some links to helpful webpages.  [This one]("http://linuxhelp.blogspot.com/2005/05/using-fetchmail-to-download-emails.html") tells you how to set up **fetchmail** to grab emails, while [this one]("http://wiki.debian.org/GmailAndExim4") says how to use **exim4** to send emails, via the command-line and pop3/smtp.  These howtos deal with gmail, but I'm sure it's the same principle with hotmail.  Follow these guides and you will be able to use the command-line **mail** program.

---

### Post by t0p on 2009-07-29
> **hyperAura said:**
> 
also before installing fetchmail procmail and exim4 i tried sending test emails through the shell and i found all the messages now not sent in a file at  /var/mail/username..

should i delete the contents of that file?

That file, /var/mail/*username*, is your mailbox.  Once you sort out fetchmail and exim4, that is where your new received mail will be found. You can delete its contents if you like - I don't think it is emptied automagically. You should read the mail manpage to find out all about the mailbox.

I have set up evolution to check my mailbox periodically for new mail.  So I can read my emails via the command-line or evolution's pretty gui.

---

### Post by hyperAura on 2009-07-29
cool thnx a lot i hope that i will manage to get thru with the links u gave me..

---

### Post by hyperAura on 2009-07-30
hey tOp is it by any chance that u might know up to how many messages can be held in evolution and how many in var/mail/username cause i didnt manage to get all messages neither in evolution or through the shell.. in shell i get about 963 messages whereas in evolution only 386 messages..

---

