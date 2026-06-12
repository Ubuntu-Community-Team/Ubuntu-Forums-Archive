---
title: "Evolution Mail Gmail Settings"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by Shie6meepo on 2011-01-29
I've tried about five different settings provided by different sites to get Gmail to work in Evolution, but none of them are working. Are there any settings that have worked pretty much all the time?

---

### Post by geek-at-heart on 2011-01-29
On mine I set the e-mail server as IMAP .  Evolution auto-completed the rest of it. I didn't enter anything in the encryption types. When I got to the finish it asked me for my password to login to my gmail and logged in fine.

---

### Post by darkstaar on 2011-01-29
Have you tried [https://help.ubuntu.com/community/UsingGmailWithEvolution](https://help.ubuntu.com/community/UsingGmailWithEvolution) ?

---

### Post by Shie6meepo on 2011-01-29
I have tried both of those and neither worked. Anybody else got any ideas?

---

### Post by ben889 on 2011-01-29
you need to log in your gmail go to setting and go to forwarding and pop/imap andenable the on that your setting up.
imap settings

imap.gmail.com

smtp.gmail.com

out going serve check box =My outgoing server (SMTP) requires authentication
use same setting as incoming mail

This server requires an encrypted connection (SSL)' under **Incoming Server (IMAP)**. Also, enter [FONT=Courier New, Courier, mono]993[/FONT] in the **Incoming server (IMAP)** box

Check the box next to 'This server requires an encrypted connection (SSL)' under **Outgoing Server (SMTP)**, and enter [FONT=Courier New, Courier, mono]465[/FONT] in the **Outgoing server (SMTP) **box.
set time out for five minutes

pop3
pop.gmail.com

smtp.gmail.com

Check the box next to **My outgoing server (SMTP) requires authentication** and select **Use same settings as my incoming mail server.** 

heck the box next to **This server requires an encrypted connection (SSL)** under **Incoming Server (POP3). Enter 995 in the 'Incoming Server' box.**

Check the box next to **This server requires an encrypted connection (SSL)** under **Outgoing Server (SMTP),** and enter [FONT=Courier New, Courier, mono]465[/FONT] in the **Outgoing server (SMTP) **box. 

set time out for 1 minute

this works for out look not sure where you plug this stuff in on you client, but its the right info

---

### Post by Shie6meepo on 2011-01-29
> **ben889 said:**
> you need to log in your gmail go to setting and go to forwarding and pop/imap andenable the on that your setting up.
imap settings

imap.gmail.com

smtp.gmail.com

out going serve check box =My outgoing server (SMTP) requires authentication
use same setting as incoming mail

This server requires an encrypted connection (SSL)' under **Incoming Server (IMAP)**. Also, enter [FONT=Courier New, Courier, mono]993[/FONT] in the **Incoming server (IMAP)** box

Check the box next to 'This server requires an encrypted connection (SSL)' under **Outgoing Server (SMTP)**, and enter [FONT=Courier New, Courier, mono]465[/FONT] in the **Outgoing server (SMTP) **box.
set time out for five minutes

pop3
pop.gmail.com

smtp.gmail.com

Check the box next to **My outgoing server (SMTP) requires authentication** and select **Use same settings as my incoming mail server.** 

heck the box next to **This server requires an encrypted connection (SSL)** under **Incoming Server (POP3). Enter 995 in the 'Incoming Server' box.**

Check the box next to **This server requires an encrypted connection (SSL)** under **Outgoing Server (SMTP),** and enter [FONT=Courier New, Courier, mono]465[/FONT] in the **Outgoing server (SMTP) **box. 

set time out for 1 minute

this works for out look not sure where you plug this stuff in on you client, but its the right info

You name both port 993 and 995 for incoming mail. Which one should I use?

---

### Post by lisati on 2011-01-29
> **ssrock64 said:**
> You name both port 993 and 995 for incoming mail. Which one should I use?

It depends. Are you using IMAP or POP access?

---

### Post by ben889 on 2011-01-30
i have both settings

imap is 993 for outgoing


pop3 is 995 for out going

---

### Post by ben889 on 2011-01-30
if you choose imap you can view through your email client but cant delet messages pop3 downloads to your email client and you can delete from there too

---

