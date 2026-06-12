---
title: "Thunderbird - error message &quot;server is unknown&quot; when trying to send email"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by pariate369 on 2010-10-24
Grrrrr....  

Decided to switch from Evolution to Thunderbird.  Using v3.1.5 with Lightning calendar.  Tried to set up my another.com, 123-reg hosted sites, and zen.co.uk mail accounts with Thunderbird.  Followed the instructions provided by each of those sites and Thunderbird refuses to play nicely!  


Sending of message failed.
An error occurred sending mail: SMTP server xxxx.xxxxx.myzen.co.uk is unknown. The server may be incorrectly configured. Please verify that your SMTP server settings are correct and try again.

This is driving me nuts.  I can receive my messages, no problems there, but I can't send anything.  I've tried Googling, I've searched the Ubuntu forums and the Thunderbird Knowledge Base, and I'm getting nowhere.

Can anybody help me please?

P.S.  Am using Ubuntu 10.10 Desktop.  Am also not terribly skilled in the ways of Linux ;-)

---

### Post by peculiar penguin on 2010-10-24
In Thunderbird go to Edit > Account Settings... > Outgoing Server (SMTP). Add/edit one entry for every account with its own username/password combination, make sure all the settings are correct (looking at your error message, double check the server names and ports used). Then go to the main page of every account listed above and assign it the appropriate server by using the "Outgoing Server (SMTP):" dropdown menu at the bottom of the dialog.

---

### Post by pariate369 on 2010-10-24
> **peculiar penguin said:**
> In Thunderbird go to Edit > Account Settings... > Outgoing Server (SMTP). Add/edit one entry for every account with its own username/password combination, make sure all the settings are correct (looking at your error message, double check the server names and ports used). Then go to the main page of every account listed above and assign it the appropriate server by using the "Outgoing Server (SMTP):" dropdown menu at the bottom of the dialog.

Thank you for replying  :-)

I had already set up the outgoing smtp server details but after seeing your post went back and checked them all again.  Changed a couple of things in the security options and then tried to resend. It worked, after I also changed the location of my "Sent" items folder to the Local Settings.  

Now only one of the accounts is still playing up.  It's the Zen account.  I'm wondering if I have the wrong port numbers?  I used 587 for outgoing and 995 for IMAP as instructed by Zen.  Can't understand why this one still isn't working...  Have checked and double-checked my entries for the SMTP server.

**EDIT:  Now have all accounts working!  **Tried a string of different port numbers and eventually discovered that Zen works with 25 as SMTP port.

Thanks again for your help :-)

---

