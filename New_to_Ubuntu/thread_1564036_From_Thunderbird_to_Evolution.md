---
title: "From Thunderbird to Evolution"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by expatCM on 2010-08-30
I am planning on migrating from Thunderbird to Evolution.  I have multiple email accounts, folders, sub-folders of messages, rather a lot of filters. rss feeds and a couple of address books.

I am hoping to get some idea of the pain I am likely to encounter.

Has anyone successfully migrate from Thunderbird to Evolution with a less then simple setup or is it a matter of setting up everything from scratch?

---

### Post by expatCM on 2010-09-02
no responses at all .......  hmmm ... wonder if this means that everyone uses gmail and does not think evolution is necessary.

---

### Post by jtarin on 2010-09-02
> **expatCM said:**
> no responses at all .......  hmmm ... wonder if this means that everyone uses gmail and does not think evolution is necessary.
To the contrary....everyone is going the other direction...Evolution to Thunderbird. Why are you considering migrating may I ask? BTW Gmail has POP and IMAP configuration.

---

### Post by dmizer on 2010-09-02
I use both Evolution and Thunderbird. Evolution is really nice because it can sync with my google calendar and contacts list which is also synced to my phone. Fortunately, all but one of my email accounts supports IMAP. If IMAP is an option for you, then there is no need to migrate anything.

Otherwise, a quick google search turned this up: [http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_migrate_from_Thunderbird_to_Evolution](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_migrate_from_Thunderbird_to_Evolution) and it looks like that will probably work.

---

### Post by gradinaruvasile on 2010-09-02
If you use POP3: you will have to create your accounts, folders in Evolution, import your mailbox files (one per each folder), create your filters etc... Lot of work.
Also, Evolution didnt worked as well as Thunderbird for me at least.
If you have IMAP, just create the accounts and youre set.

---

### Post by cjv8888 on 2010-09-02
> **expatCM said:**
> I am planning on migrating from Thunderbird to Evolution.  I have multiple email accounts, folders, sub-folders of messages, rather a lot of filters. rss feeds and a couple of address books.

I am hoping to get some idea of the pain I am likely to encounter.

Has anyone successfully migrate from Thunderbird to Evolution with a less then simple setup or is it a matter of setting up everything from scratch?

Couple of years ago, I transferred all files from Outlook Express to Thunderbird in windows, then from Thunderbird in windows to Thunderbird in Ubuntu, then from Thunderbird in Ubuntu to Evolution.  The only thing that got a bit muddled up is foreign characters in the address book.  
It can be done quite easily.

---

### Post by dmizer on 2010-09-02
Let's keep this topic support related. ;)

---

### Post by expatCM on 2010-09-02
Thank you for all the replies.

I have become a bit disappointed with Thunderbird (I migrated a long time in the past when I used Eudora on Windows 2000) when out of the blue it decided to archive my messages.  I have a lot of messages and it was a big mess.  Once archived it cannot be unarchived.

I also feel that Thunderbird has not moved forward a lot, the filtering is still a bit limited and an add-on I like, BorderColors has been dropped from the latest release.  Why an add-on is needed for this suggests to me that the program is geared more to the user with a single account or it would be a built in feature.

So I am looking at the alternatives.  People on this forum do not generally have any negative views of evolution which makes me think that perhaps it is time to consider the move ...........

---

### Post by HermanAB on 2010-09-03
Howdy,

The solution to all mail migration problems, is to bounce your mail through an IMAP server.

If you are already using IMAP, then you need not do anything, since the mail resides on the server.  You only have a migration problem if the mail was downloaded to the local machine with POP or Outlook DCE.

The way to move mail around is to open a new Gmail account (or to install Citadel on one of your own machines - it takes about 20 minutes to install Citadel and it 'Just Works').  Then, use your new mail client and connect to the new server account using IMAP.  Open the old email client and select ALL your mail (highlight all with the mouse), then click drag and drop the mail from the old client to the new client.  This will copy the mail unaltered.  Note that if you have thousands of mails, then it may take a very long time.

What not to do: Do not Forward the mail to the new account, since then all the From headers will become yourself.

From now on, never ever use POP again.  IMAP works much better.

---

### Post by expatCM on 2010-09-03
so I take it that the filters are all going to need setting up again?

---

### Post by mastablasta on 2010-09-03
> **HermanAB said:**
>  
From now on, never ever use POP again. IMAP works much better.
 
 
how did you come up with this?
 
Ok lets say i have a company and i dont' want to use GMAIL as my company address. so i need to buy server space and that can get quite expencive if company if small and low budget. now in this case POP is much more logical.
 
Also what happens when your e-mail server goes broke? all your e-mail might be gone. while with pop you still have them on your ocmputer and if you did your backups they are still available.

---

### Post by QLee on 2010-09-03
[QUOTE=mastablasta]...
Also what happens when your e-mail server goes broke? all your e-mail might be gone. while with pop you still have them on your ocmputer and if you did your backups they are still available.[/QUOTE]

Well, if one does the backups of anything mission critical in their  lives or business as they should, then the method of transport they  choose for email checking doesn't affect that. Perhaps in your specific case, you find it easier and that's fine.

I guess my opinion is similar to Herman AB, the way many people use their computers these days, an IMAP server for email does make sense. But nothing is right for everyone, hence we have the choice.

---

### Post by dmizer on 2010-09-03
> **expatCM said:**
> so I take it that the filters are all going to need setting up again?
Take a good look at the filter settings, there should be an option for exporting them.

---

