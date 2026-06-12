---
title: "Aghhh!!!!!!! Where are all my emails!!!!"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-01-02
I installed Thunderbird 3, when I uploaded all accounts, then cleared out my emails so I could go back into my gmail accounts to clean them up.
But freaking Thunderbird deleted them from both my Thunderbird AND gmail!!!!

I have several years of email...lost.....I have just lost every correspondence with my girlfriend from 4 years(which I need for Immigration proof of time together), every work, and personal email, all email address', EVERYTHING!!! WTF!!! I have never had this problem before. I checked my Gmail accounts, and after download it was check to leave it on gmail, there was nothing checked on Thunderbird to delete from the server.....
OMG OMG OMG OMG!!!! Please some one tell me I can retrieve these somehow!

---

### Post by ajgreeny on 2010-01-02
Are you sure it's gone from gmail and not simply been archived in your gmail account?

If it really has gone, then that is one good reason for me not to try TB3 just yet.  I did look at it a while back, but never used it to get any mail, just to see what it looked like.

---

### Post by WinterWeaver on 2010-01-02
I believe the Option in TB is "Leave a copy of the mail on the server" ??

not too sure havent used TB in aaages... if you are using gmail, why even bother with a stand alone client... the browser is awsome.

First try searching for mail in your gmail account. chances are they are archived.

Secondly: Look on the bright side Now you have a good starting point for your [Inbox Zero]("http://inboxzero.com/") ^_^

---

### Post by QIII on 2010-01-02
Not sure about the gmail stuff, but...

Try going to your /home, clicking CNTL+H and displaying your hidden folders.  There should be one called .mozilla or .thunderbird (or the like.  I'm not at home right now, so I can't check my /home).

See if a previous profile exists with all of your original tbird emails.

---

### Post by AndyP79 on 2010-01-02
They are not archived in Gmail. Nothing, it looks like a brand new account. Nothing anywhere. I had about 20 contact emails in the various gmail accounts that i was able to save, bu that is out of about 200 that I had in thunderbird.. 
I need to use a client because I travel so much, it is easy to write an email and send it later, I can go back and review, and all the other stuff.
This is not the first time I used TB3, I used it on a previous build of Karmic that got thrashed from another project gone wrong.

Okay, so, back to my original question, how do I get all my email back?

---

### Post by WinterWeaver on 2010-01-02
I'm sorry for not being able to tell you how to get your email back. I guess you can try asking google for support? I do believe however that once the email is deleted from the google servers, they are probably gone forever, unless google support is somehow able to resurrect them. Maybe someone else has some info on this?

On another note... Install Google Gears and you can still access your gmail, write and read emails while offline and travelling. I have both my gmail accounts working this way and it's great. This is why I say there is no need for a client really.

---

### Post by benerivo on 2010-01-02
This probably won't work, but i would still try to treat this as a file recovery situation. From now on i would not use the disk or partition that thunderbird used -- if this is possible for you. I would then find out where in the the /home directory, thunderbird stores emails. It might have be something like /home/fred/.thunderbird/account5.db. Then i would install a file recovery program such as [foremost]("http://www.unixmen.com/linux-tutorials/135-recover-deleted-files-with-foremost") and try to search the drive/partition for the thunderbird email storage file(s). Also, check if your girlfriend has kept the emails sent between yourselves.

---

### Post by sgosnell on 2010-01-02
Go to gmail, and look in the Trash. Deleted emails should stay there for 30 days or so.  You should be able to recover everything from there.  Next time, be careful how you configure your email client.  You can also set up gmail for offline use, and download everything to your computer for saving, without even using a client.  I just use the browser, because email clients can be quirky, and do absolutely nothing the web client won't do, and actually less.

---

### Post by AndyP79 on 2010-01-02
Thanks everyone. I managed to find a few of them, about 2500 emails, mostly junk, out of about 15,000. 
So, At least I have most of the contacts, and can email some people to forward the emails to me again from us. But some were only correspondance through the one that I can't recover at all. Damn,

This sucks. I have a sweet set up at them moment, and now I am just kinda sitting here like...WTF do I do now. Man, talk about sucking the fun outta the day right.

---

### Post by sgosnell on 2010-01-04
GMail doesn't just delete email like that, suddenly.  They should all be either in All Mail or Trash, if they're not in your inbox, unless you have already deleted them sometime in the past.  With 7+GB of storage, there is no need to delete anything you might ever need.  I leave everything on the server, and delete only stuff I know is trash, and there is a lot of that.

---

### Post by Seq on 2010-01-04
> **sgosnell said:**
> GMail doesn't just delete email like that, suddenly.  They should all be either in All Mail or Trash, if they're not in your inbox, unless you have already deleted them sometime in the past.  With 7+GB of storage, there is no need to delete anything you might ever need.  I leave everything on the server, and delete only stuff I know is trash, and there is a lot of that.

Thunderbird 3 appears to understand gmail, and has an archive mode. So if you hit 'a' for archive, it goes to 'All Mail', and delete moves it to the Trash. The trash in thunderbird will be the same as the trash in gmail, so deleted means deleted, not archived.

For future reference, and for anybody else who is curious, I'd go to gmail's Labs section and enable "Advanced IMAP Controls". Then go to your labels and uncheck 'Trash' (I also uncheck 'Spam' and 'Starred'). Also make sure your IMAP settings are to archive the message, not trash or delete. This way your mail client won't be able to permanently delete any mail.

Also consider looking into a program called offlineimap. It will allow you to keep a local copy of your mail, and you can include that in your backup scheme.

---

### Post by llawwehttam on 2010-01-04
Thunderbird if configure to IMAP, deletes the email on your server when you delete it in thunderbird. Also if you don't set up POP3 to leave a copy on the server then you will permenantly delete emails. 
Haven't you got a 'recently deleted' folder?

Also with IMAP you can tell thunderbird to 'download mail for offline use' and then backup your .mozilla_thunderbird folder.

I wrote a script to do this on a weekly basis.

---

### Post by camaron1 on 2010-01-04
It has happened to me too. This might help:
When I installed Thunderbird 3 it wasn't a clean upgrade as there isn't repositories for it. This means that I installed it alongside Thunderbird 2. This kept my **.thunderbird** folder still in my **home** folder, alongside **.thunderbird-3.0** folder. All your emails up until you stopped using Thunderbird 2 should be there as they were for me. Look for heavy files called INBOX, SENT, and things like that.

Problem is: thunderbird doesn't want to open these emails for some reason, so if you find yours and find out how to access them, please let me know

---

