---
title: "Evolution + gmail + imap, download all mail"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by Ck.asdf on 2008-08-29
Hello, I just set up Evolution with my gmail account, and it downloaded the subject line for all of my emails, but each email I click on, it is having to connect to the Internet to show me the body of the email.  Is there an option somewhere that I can set so that all of the mail is downloaded in bulk?

---

### Post by arch0njw on 2008-08-29
I suspect you are downloading only headers.

1. Edit | Preferences
2. Edit your Gmail account settings
3. Choose the IMAP Headers tab.
4. Select "Basic and Mailing List Headers (Default)"

See if that works.  It works for me.  But that's every programmers excuse:  "works on my machine"

---

### Post by Ck.asdf on 2008-08-29
That was already selected, so I tried "all headers."  I hit send/receive, it only took a couple seconds, and then ... hm, never mind.  I just tried something, and it seems that all new mail (after I did the initial setup) is automatically downloaded, which seems to make sense (if I want to read older messages, I could read them at that point, or whatever).

New question: why is the mail not updating itself?  I got several new emails this morning, and I read a few of them, then hit send/receive in evolution, but evolution still shows them as unread.

Thanks!

---

### Post by arch0njw on 2008-08-29
Do you have your "check for email every X minutes" enabled?

Also, Evolution might have a "feature" specifying when an email should be considered read.  For example, Outlook has a setting that an email is only marked as read when you say "Mark as read".

Sorry... not in front of Ubuntu right now.  Thought I'd share those as options to explore.

---

### Post by Ck.asdf on 2008-08-29
Yes, I have it check every two minutes.

As for the feature you speak of, are you talking in reference to POP3, or IMAP?
From what I understand, IMAP and the web interface of gmail are synced, as far as read, deleted, etc.  In fact, I have used Thunderbird in the past, and it kept things synced, but I figured I would try evolution, since it's pre-installed on ubuntu.  Another note: all the mail downloaded the first time shows as either read or unread, depending on its actual status at gmail.  But new mail, whether I read it at the web interface or evolution, the other place (the one I didn't read it at) still shows it as unread, which is the behavior of POP3.  But I'm sure the server setup I have set up is imap.gmail.com

---

### Post by arch0njw on 2008-08-29
DOH!  You are right.  I was thinking POP.  I will take a look at this tomorrow.  I configured Evolution to work with Gmail early this morning, but don't have it available to me right now.

Update: I have Thunderbird under Kubuntu checking my GMail account.  I just noticed it is behaving exactly as you mention.  I wonder if there is something wonky with GMail today.

---

### Post by arch0njw on 2008-08-29
> **Ck.asdf said:**
> Yes, I have it check every two minutes.

As for the feature you speak of, are you talking in reference to POP3, or IMAP?
From what I understand, IMAP and the web interface of gmail are synced, as far as read, deleted, etc.  In fact, I have used Thunderbird in the past, and it kept things synced, but I figured I would try evolution, since it's pre-installed on ubuntu.  Another note: all the mail downloaded the first time shows as either read or unread, depending on its actual status at gmail.  But new mail, whether I read it at the web interface or evolution, the other place (the one I didn't read it at) still shows it as unread, which is the behavior of POP3.  But I'm sure the server setup I have set up is imap.gmail.com

Try this...

1. Edit | Preferences
2. Choose "Mail Preferences" on the left
3. on the right there is a "Mark messages as read..." selection -- is that checked?  What's the delay?  I find if I move away from a message before that delay, the message is not marked as read.  If I uncheck that, it *never* marks a message as read.

---

### Post by Ck.asdf on 2008-08-29
It's checked, and the time is 1.5 seconds. 
Whenever I read a message in the web interface, it's marked as read ON the web interface.  When I read it in evolution, it marks it read there.  But it doesn't mark both places read when I read it in one place, which seems to be what IMAP is for.

---

### Post by arch0njw on 2008-08-30
I think this qualifies as a known problem:
[http://ubuntuforums.org/showthread.php?t=600880](http://ubuntuforums.org/showthread.php?t=600880)

Good news: when you exit Evolution, it will mark the messages as read.
Bad news:  see "Good news".

---

### Post by nbcthreat on 2008-10-02
The real good news is that the latest version of Evolution seems to have finally fixed this damn IMAP mark-read bug. You'll just have to wait until it's rolled out to Ubuntu.

---

### Post by unikuser on 2009-06-13
For those looking for solution to make evolution download all mail(headers+body) before you click the mail:

* right click folder you want to download and select properties, check "copy folder contents locally for offline use"
* click file-> "download messages for offline use"

---

### Post by QwUo173Hy on 2009-12-26
Thanks unikuser, that solved my problem.

---

### Post by amarendra on 2011-03-20
> **unikuser said:**
> For those looking for solution to make evolution download all mail(headers+body) before you click the mail:

* right click folder you want to download and select properties, check "copy folder contents locally for offline use"
* click file-> "download messages for offline use"
But it's not downloading the messages. Especially the images and attachments. Though my entire Gmail is only 200 MB+ I want everything in my local machine too.

---

