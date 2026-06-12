---
title: "thunderbird"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by DarinB on 2009-05-15
I added gmail add on and set up a gmail account but i now have two set of folders can i combine the folders with the local folders????

---

### Post by kanikilu on 2009-05-15
Did you add it as POP3 or IMAP?

I use IMAP and it shows up as a second set of folders. I haven't tried it myself, but maybe if you use POP3 it will go to your existing local folders?

---

### Post by DarinB on 2009-05-15
i set it up as just gmail not gmail imap in add accounts it has two choices gmail and gmail imap i wonder if i add the smtp server and pop server manually along with the port maybe i can combine it all what do you think??????

---

### Post by kanikilu on 2009-05-15
That might work - make sure you've enabled POP in your GMail settings:

[http://mail.google.com/support/bin/answer.py?hl=en&answer=13273](http://mail.google.com/support/bin/answer.py?hl=en&answer=13273)

And then configure Thunderbird:

[http://mail.google.com/support/bin/answer.py?answer=86399](http://mail.google.com/support/bin/answer.py?answer=86399)

---

### Post by DarinB on 2009-05-15
ok I got the gmail account going put the smtp server is set for all of my other emails and that is the default can i set a different smtp server just for this account. 
i can't find the tab in accounts to change that????
the way it is now with the default smtp i can not send emails on the gmail account but i can receive emails to it

---

### Post by kanikilu on 2009-05-15
When you go to Edit > Account Settings, if you click on the "top level" of an account, you should see a drop-down menu at the bottom where you can set which SMTP server the account should use.

---

### Post by DarinB on 2009-05-15
yeah funny i have my screen res lower so i can see stuff and it was not seen but i noticed that accessing the pop.gmail.com freezes. i may have to go back to the seperate folders and live with it. any ideas i change the port back to 110 instead of the 995 that gmail set up as with the add on

---

### Post by DarinB on 2009-05-15
hey i have an idea how about a message filter that will move all messages into the local folders inbox????
how could i do that?????

---

### Post by DarinB on 2009-05-15
hey everyone i found a work around i set gmail up with the gmail add on
then set the sent mail folder to add to local sent folder and then set up a mail filter to put all messages to local inbox and there you go gmail as an extra email address and ever thing goes into my local folder inbox i just leave the gmail folders un expanded. I do notice that gmail is quite slower than my isp email and my web site email server. but hey it is free.

---

### Post by presence1960 on 2009-05-15
> **DarinB said:**
> I added gmail add on and set up a gmail account but i now have two set of folders can i combine the folders with the local folders????

In Thunderbird go to Edit > Account Settings. Under the gmail settings choose Server settings. This will bring up the screenshot I posted. Click Advanced ( my pointer is on the advanced button). This will bring up the advanced settings window (which is in the center of the screenshot). Choose Global Inbox (Local folders Account) This will put gmails downloaded mail in your local folders. Check screenshot to see what I am saying. Once you have verified gmail is downloading to Local folders you can delete the other folders not needed.

---

### Post by medic8ted on 2009-05-15
> **presence1960 said:**
> In Thunderbird go to Edit > Account Settings. Under the gmail settings choose Server settings. This will bring up the screenshot I posted. Click Advanced ( my pointer is on the advanced button). This will bring up the advanced settings window (which is in the center of the screenshot). Choose Global Inbox (Local folders Account) This will put gmails downloaded mail in your local folders. Check screenshot to see what I am saying. Once you have verified gmail is downloading to Local folders you can delete the other folders not needed.

Global inbox is not an option if account type is gmail.

---

### Post by DarinB on 2009-05-16
awesome!!!!!!! there is a global inbox section the last post was incorrect,,,, my problem was i have my screen res lower to make things bigger and my font at 20 so the advanced button was behind the ok button 
thanks i will delete the message filter i created now.

---

### Post by DarinB on 2009-05-16
one last thing i included a screen shot
we need to check the "include this server when getting new mail".
Also it is now as fast as my other emails when i was set up before it was slow,,,,although i am not sure if it was on  my app end or the gmail servers.[ATTACH]113998[/ATTACH]
NOTICE THERE IS A GLOBAL FOLDER CHOICE WITH A GMAIL ACCOUNT. 
funny you can see in the right corner my advanced button peeking out from behind the ok button because of my screen res and font size.

---

### Post by presence1960 on 2009-05-16
> **DarinB said:**
> awesome!!!!!!! there is a global inbox section the last post was incorrect,,,, my problem was i have my screen res lower to make things bigger and my font at 20 so the advanced button was behind the ok button 
thanks i will delete the message filter i created now.

you are welcome. Enjoy.

---

