---
title: "evolution"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by albert s on 2010-04-09
very basic question I know,
but I know absolutely nothing about its counterpart outlook either, and my missus is wanting to get this working as well,
so far her transition to ubuntu has been, "WOW, this is really good.!"
so hopefully if I can get this working for her as well then all will be good in the world.
as her laptop is currently sole boot to ubuntu there is nothing to import, but I have no idea what Im supposed to put in for settings, at present a message has been trying to send for 3days with no success.
thanks for all the help so far.  :)

---

### Post by -humanaut- on 2010-04-09
What kind of account are you trying to configure it with? Gmail,yahoo?

---

### Post by albert s on 2010-04-09
one is a yahoo account, her private account is hotmail(Ive told her I dont hold out much hope on that one.), and the other is a private work account,(do I need to find out more info on that one?),
at least if I had the yahoo one working then she might hold some faith in getting the others to work.

---

### Post by -humanaut- on 2010-04-09
Yahoo the settings would look like this

Incoming mail: POP server: plus.pop.mail.yahoo.com
Use SSL


Outgoing mail: plus.smtp.mail.yahoo.com
Use SSL
Use authentication (username & password)

Dead simple setup.

I don't think hotmail supports POP3 or imap and the private work e-mail she'd have to configure

---

### Post by albert s on 2010-04-09
thanks [-humanaut-]("http://ubuntuforums.org/member.php?u=1049264")  , now how do I access these settings?
I know they appeared at the beginning but I/we had no idea what to do so just clicked continue.
you said username and password, is that the e.mail ones I assume, and not the OS username.
thanks for your time and help.

---

### Post by -humanaut- on 2010-04-09
open evolution and hit shift+ctrl+s or go to Edit-->Preferences you can add an account from there should be pretty straight forward

---

### Post by albert s on 2010-04-09
thank you,
thats deffo worked on the yahoo account, as so far as having pulled in all her existing messages anyhow, so I think its fine, will get her to check with IT at work on monday for settings for her work account. 
thank you.  :D

---

### Post by -humanaut- on 2010-04-09
No problem, Glad I could help.

---

### Post by albert s on 2010-04-09
i cant find a thanks tab....

---

### Post by lisati on 2010-04-09
> **albert s said:**
> i cant find a thanks tab....

There was one, but the system ran into problems with it.
You can, however, mark the thread as "solved" when you're satisfied that someone has answered your question. It can be found on the "Thread tools" link near the top of the page.

---

### Post by Didius Falco on 2010-04-09
I just saw this thread, and thought I'd add that you can get your hotmail via pop3 and smtp now - it's available worldwide.

I've never gotten the outgoing part to work, but my hotmail account is really just a spam trap anyway, so it's no big deal to me. This should be what you need to know:

 > **POP  server**: pop3.live.com (Port 995)   
**POP SSL required**? Yes
**User  name**: Your Windows Live ID, for example [email]yourname@hotmail.com[/email]
**Password**:  The password you usually use to sign in to Hotmail or Windows Live
**SMTP  server**: smtp.live.com (Port 25)   
**Authentication required?**  Yes (this matches your POP username and password)
**TLS/SSL  required?** Yes

Regards,

Didius

---

### Post by drs305 on 2010-04-09
I am able to access my Hotmail account, although I may have a 'legacy' account that permits it while others do not.

For me, the "Receiving Mail" inputs are **pop3.live.com** and SSL encryption. I don't use the send function of Hotmail via Evolution so I can't provide those.

---

### Post by mixint27 on 2010-04-19
what is for the send? i cant send emails. I have a hotmail account.

---

### Post by drs305 on 2010-04-19
> **mixint27 said:**
> what is for the send? i cant send emails. I have a hotmail account.

Try these settings for outgoing. I just tested them and they work for me on Lucid:

TYPE: SMTP
Server: smtp.live.com:587
Server requires authentication
Use Secure Connection: TLS
Authentication Type: PLAIN
[email]username@hotmail.com[/email]
Remember pw (optional)

---

### Post by mixint27 on 2010-04-19
Thank you so so much! I forgot to add the 587. One more question, is there a way for me to see my folders on evolution like i have on my hotmail account?

---

### Post by drs305 on 2010-04-19
> **mixint27 said:**
> Thank you so so much! I forgot to add the 587. One more question, is there a way for me to see my folders on evolution like i have on my hotmail account?

You can do it with Gmail, which supports IMAP. You use IMAP rather than POP in the evolution setting and think you have to set it up on the Gmail site as well. 

I don't know if IMAP is supported by Hotmail, but I think the IMAP capabilities are what you are looking for.

---

### Post by mixint27 on 2010-04-20
> **drs305 said:**
> You can do it with Gmail, which supports IMAP. You use IMAP rather than POP in the evolution setting and think you have to set it up on the Gmail site as well. 

I don't know if IMAP is supported by Hotmail, but I think the IMAP capabilities are what you are looking for.

I dont have a Gmail account. Only hotmail. But yeah, i want to see my folders on evolution too like i have them on my hotmail account.  I dont want to recreate every single folder i have.

Hey, thanks a lot for your help!

---

