---
title: "setting up mail with evolution"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by RememberWhenItRained on 2011-04-08
I'm kinda stuck on how to set up my mail with evolution. I have a live mail account that has an .edu domain (univ. email.) with outlook, it was easy to set it up, but i can't quite seem to figure out evolution. Where do i find the server type (default is IMAP) and the server?

---

### Post by QLee on 2011-04-08
[QUOTE=RememberWhenItRained]I'm kinda stuck on how to set up my mail with evolution. I have a live mail account that has an .edu domain (univ. email.) with outlook, it was easy to set it up, but i can't quite seem to figure out evolution.[/QUOTE]
Oh, what have you tried? Post any error message you received?

 [QUOTE=RememberWhenItRained]Where do i find the server type (default is IMAP) and the server?[/QUOTE]

The server type and the server would be the same as you used to set up outlook.

---

### Post by HermanAB on 2011-04-08
BTW, if you want a mail client that is super easy to set up, thanks to its advanced wizard that probes the server to find the most secure settings automatically, then you should try the latest version of Thunderbird.  I was totally amazed the last time I tried it.

---

### Post by RememberWhenItRained on 2011-04-08
> **QLee said:**
> Oh, what have you tried? Post any error message you received?

 

The server type and the server would be the same as you used to set up outlook.
yeah, i don't remember what i put on  outlook, that's the problem. no error message, just don't know server names and types; i tried to look that up, then had an error while sending (error connecting to IMAP). It's a university extension, but the mail is by Windows Live.

screenshots attached, if they help:

---

### Post by Rex Bouwense on 2011-04-08
> **RememberWhenItRained said:**
> I'm kinda stuck on how to set up my mail with evolution. I have a live mail account that has an .edu domain (univ. email.) with outlook, it was easy to set it up, but i can't quite seem to figure out evolution. Where do i find the server type (default is IMAP) and the server?

It has been a while since I set up a mail account but mine is a POP account.  The server type is POP and the server would be pop.gmail.com (or whatever your account is.)  If you are trying to set up an IMAP account the server would be imap.yahoo,com (or whatever your account is.)  To send email you need an SMTP account.  The server would be smtp.hotmail.com (or whatever your account is).  I think that is correct.

---

### Post by QLee on 2011-04-09
[QUOTE=RememberWhenItRained]...I have a live mail account that has an .edu domain (univ. email.) with outlook, it was easy to set it up, but i can't quite seem to figure out evolution. Where do i find the server type (default is IMAP) and the server?[/QUOTE]
Well, in my opinion the best approach would be to ask the IT department of the university for the server type and server address. If you are lucky enough to have someone look at this who goes to the same university and has already set up evolution for that then that would be fine, otherwise we would just be guessing and sometimes that isn't very productive. 

I do note from your screenshots that you tried to setup imap with a pop3 server address and that isn't likely to work, they are different protocols. I imagine you'll want to include the port numbers with the server address for the secure option but your IT department will have all the answers about that. Maybe they won't want to help with a GNU/Linux system if they don't understand it but they could still give you the necessary configuration data.

---

### Post by RememberWhenItRained on 2011-04-09
> **QLee said:**
> Well, in my opinion the best approach would be to ask the IT department of the university for the server type and server address. If you are lucky enough to have someone look at this who goes to the same university and has already set up evolution for that then that would be fine, otherwise we would just be guessing and sometimes that isn't very productive. 

I do note from your screenshots that you tried to setup imap with a pop3 server address and that isn't likely to work, they are different protocols. I imagine you'll want to include the port numbers with the server address for the secure option but your IT department will have all the answers about that. Maybe they won't want to help with a GNU/Linux system if they don't understand it but they could still give you the necessary configuration data.
ok so i managed to find a document in the recess of my university's tech support site with IMAP/pop3 information for configuring the email with other clients. So it gives me the server names and has both an IMAP and a pop3 option. do i choose one or the other?
Also, i assumed the encryption was SSL and TLS, which this document confirms, but it also gives me port numbers; do i enter these with a colon right after the server name? (There is not a separate field for ports.)

Got this error message: MAIL FROM command failed: Client was not authenticated

---

### Post by dmn_clown on 2011-04-09
> **RememberWhenItRained said:**
> do i enter these with a colon right after the server name? (There is not a separate field for ports.)

Yes.

Is that intuitive, no.  
Is it well documented, no.
Is it different from every single other email application, yes.

---

### Post by RememberWhenItRained on 2011-04-09
> **dmn_clown said:**
> Yes.

Is that intuitive, no.  
Is it well documented, no.
Is it different from every single other email application, yes.
yeah, it just seemed like something you might do in cmd or telnet so i took a guess. so apparently i can send email, but no receive it in the evolution client.
For instance, i sent a test email to myself which just sent, and then had someone else send me a test email. both emails i had to log on to microsoft live mail and log in from there to get both emails. i just don't know what i'm doing wrong.

---

### Post by QLee on 2011-04-10
> **RememberWhenItRained]ok so i managed to find a document in the recess of my university's tech support site with IMAP/pop3 information for configuring the email with other clients. So it gives me the server names and has both an IMAP and a pop3 option. do i choose one or the other?[/QUOTE]

Yes you choose one or the other, we can't choose for you, you have to decide which way you want to use your system. One thing you might do is check how you configured your Windows email client, pop3 or imap, perhaps you want them both the same or maybe not. I note from looking at a site that explains how to setup Live Mail that the configuration data is shown in Windows and can be setup manually as well as with the wizard.


[QUOTE=RememberWhenItRained]Also, i assumed the encryption was SSL and TLS, which this document confirms, but it also gives me port numbers said:**
> 

Well, seems like you figured this out all by yourself, good work.

[QUOTE=RememberWhenItRained]Got this error message: MAIL FROM command failed: Client was not authenticated

Yes, well to me, that is not too surprising since you seemed confused about pop3 or imap and probably didn't set that up completely. It might be helpful to detail what you entered into evolution, none of us can see your screen and thus can't tell what choices you made. A screenshot might be easier than explaining in words.

There is also this page from the community which is for "Hotmail" but which might be a useful reference for you. I think Live Mail is an evolution of Hotmail and probably is similar to setup.
[https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution)

---

### Post by rvchari on 2011-04-10
> **RememberWhenItRained said:**
> I'm kinda stuck on how to set up my mail with evolution. I have a live mail account that has an .edu domain (univ. email.) with outlook, it was easy to set it up, but i can't quite seem to figure out evolution. Where do i find the server type (default is IMAP) and the server?

evolution handles almost all type of mails...
at present i have pop as well as imap configured and its working just fine.

go to edit>preferences and add mail account.
choose imap as ur choice and configure the address of server correctly. password type, if u r aware then choose the right option, else its a jugglery u ll have to try by secure or plain text or something like that.

thunderbird is no doubt easier to configure, but its a huge software and i felt it as a resource hog... (its my opinion)

---

### Post by RememberWhenItRained on 2011-04-10
> **QLee said:**
> Yes you choose one or the other, we can't choose for you, you have to decide which way you want to use your system. One thing you might do is check how you configured your Windows email client, pop3 or imap, perhaps you want them both the same or maybe not. I note from looking at a site that explains how to setup Live Mail that the configuration data is shown in Windows and can be setup manually as well as with the wizard.




Well, seems like you figured this out all by yourself, good work.



Yes, well to me, that is not too surprising since you seemed confused about pop3 or imap and probably didn't set that up completely. It might be helpful to detail what you entered into evolution, none of us can see your screen and thus can't tell what choices you made. A screenshot might be easier than explaining in words.

There is also this page from the community which is for "Hotmail" but which might be a useful reference for you. I think Live Mail is an evolution of Hotmail and probably is similar to setup.
[https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution)

yeah, i was wondering if i set up IMAP/pop3 wrong. here's a screencap:
i know i didn't put the imap. prefix before outlook.com because the document told me not to; should that just be an assumption/common sense that you should do that?

---

### Post by RememberWhenItRained on 2011-04-10
i tried changing the sever name to pop3.live.com:995 as the link suggested but i still get an error: it keeps asking me to reenter my password saying: "Unable to connect to POP server pop3.live.com Error Sending Password: -ERR mailbox could not be opened."

---

### Post by QLee on 2011-04-11
Yes, the link about setting up "Hotmail" doesn't appear to be what you need. I went to the outlook.com site and found that there is a whole procedure detailed for the method of assessing your account by POP or IMAP.

The instructions have one signing on with the outlook web app and then a way to determine server settings for your POP or IMAP e-mail program. It seems they have non-intutive names like, **pod51000.outlook.com,** for example.There is a video showing how to do it. It is in the section down below where it has info for Windows and Mac.  

Here is the link I found to the instructions:
[http://207.46.16.237/en-us/140/cc875899.aspx](http://207.46.16.237/en-us/140/cc875899.aspx)

I also found this, "If your e-mail account is the type that requires registration, you must  register it the first time you sign in to Outlook Web App. Connecting to  your e-mail account through POP3 or IMAP4 will fail if you haven't  registered your account through Outlook Web App. After you sign in to  your account, sign out. Then try to connect using your POP3 or IMAP4  program."

I'm somewhat surprised that your IT department didn't suggest this stuff. You'd have to do the same to use Thunderbird on Windows or Mac. I think they could be more helpful even if they don't support Gnu/Linux systems.

Good luck, since I don't use Windows or Outlook or the web app I can't be of any help.

---

### Post by RememberWhenItRained on 2011-04-11
> **QLee said:**
> Yes, the link about setting up "Hotmail" doesn't appear to be what you need. I went to the outlook.com site and found that there is a whole procedure detailed for the method of assessing your account by POP or IMAP.

The instructions have one signing on with the outlook web app and then a way to determine server settings for your POP or IMAP e-mail program. It seems they have non-intutive names like, **pod51000.outlook.com,** for example.There is a video showing how to do it. It is in the section down below where it has info for Windows and Mac.  

Here is the link I found to the instructions:
[http://207.46.16.237/en-us/140/cc875899.aspx](http://207.46.16.237/en-us/140/cc875899.aspx)

I also found this, "If your e-mail account is the type that requires registration, you must  register it the first time you sign in to Outlook Web App. Connecting to  your e-mail account through POP3 or IMAP4 will fail if you haven't  registered your account through Outlook Web App. After you sign in to  your account, sign out. Then try to connect using your POP3 or IMAP4  program."

I'm somewhat surprised that your IT department didn't suggest this stuff. You'd have to do the same to use Thunderbird on Windows or Mac. I think they could be more helpful even if they don't support Gnu/Linux systems.

Good luck, since I don't use Windows or Outlook or the web app I can't be of any help.

that link was very helpful, and i entered all the information i found on my Outlook > About, (having to change the receiving server address) but still "Error While Fetching Mail." just can't figure out what i'm doing wrong.

---

### Post by RememberWhenItRained on 2011-04-11
I deleted the old profile and started anew again with link you provided QLee. It works now!

---

### Post by akakingess on 2011-04-12
+1 on Thunderbird, it is by far my favorite and a necessity for me considering my severe dislike for Evolution.

---

### Post by akakingess on 2011-04-12
+1 on Thunderbird, it is by far my favorite and a necessity for me considering my severe dislike for Evolution.

---

### Post by QLee on 2011-04-12
> **RememberWhenItRained said:**
> I deleted the old profile and started anew again with link you provided QLee. It works now!
Great, that would have been all that I could have suggested at the time, I'm glad that you were successful.

---

### Post by RememberWhenItRained on 2011-04-30
i got fed up with Evolution's lack of features and switched to Thunderbird. Felt a little  easier to use overall as well.

---

