---
title: "Evolution not receiving mail, but sending ok."
date: 2011-06-03
forum: New to Ubuntu
---

### Post by grey1beard on 2011-06-03
On the 24th May, I discovered that my webmail box was full.
(I hadn't known that my Evolution settings were saving a copy of all mail on my server.)
Contacted my isp, Easyspace, who walked me through emptying the box, and unchecking the "save copy" box.

In the last few days, I now realise, that I am not receiving any mail at all, but I'm not sure when this started. As far as I recall, I made no changes to Evolution, other than the above.

I sent test messages to myself, and these appear on my webmail boxes on Easyspace server, but are not appearing in Evolution.
I contacted the support at Easyspace, who could not identify any problem, and again their mail to me appears in my webmail, but not in Evolution.

As I am now at a loss as to what I can do, I'd be grateful for any help and guidance.
John

EDIT Fairly certain this has only started in the last 72 hours, and so is not connected with my earlier problem of a full mailbox.

---

### Post by grey1beard on 2011-06-03
Update.

Reading the archive threads at Evolution, I noticed that someone had problems after updating to evo 3 (I currently run 2.22.3.1 in ubuntu 8.04), and he'd found he could receive mail only each time he closed Evo, then reopened it.

I closed mine, phoned my daughter and got her to send a test mail.
When I opened Evo, the test message appeared, accompanied with a sound, which it has never done before.
The same sound thing happened when I launched my webmail page, again, something that has never happened before.

I've looked in the System/Preferences/Sounds, but can't recognise any place to manage the sound settings for receiving new email. Neither can I find such a control anywhere else.

Can anyone advise please ?

I've just tried another test mail to myself, and this arrives in my webmail, but isn't opened by my Evolution.:confused:

John
EDIT tried closing for 1 hour. Reopened but nothing in box, even though there was a message in my webmail server, but no sound this time.
I've deleted all my message filters in case this is the problem, but no result.

---

### Post by grey1beard on 2011-06-03
Another curiosity.
Just opened Evolution and received a mail from daughter, but not one from another source. The second one had my catch-all address, the first an address that is forwarded by my web space provider.
Is this a clue ?
Getting daughter to send to all my mail boxes to see if that produces an effect.

---

### Post by grey1beard on 2011-06-04
I'm searching for any sort of pattern, but so far have not been able to detect one.
Opened webmail and observed seven emails.
Opened Evolution, and the first email in the list was downloaded, but no others.
Back to webmail and deleted seven(all junk), then went back to Evolution and found four of them in the "Deleted" folder !

Any brave soul like to offer a comment/idea/ conduct an exorsism on Evolution(Perhaps I need a neo-Darwinist)

---

### Post by gandaran on 2011-06-04
> **grey1beard said:**
> I'm searching for any sort of pattern, but so far have not been able to detect one.
Opened webmail and observed seven emails.
Opened Evolution, and the first email in the list was downloaded, but no others.
Back to webmail and deleted seven(all junk), then went back to Evolution and found four of them in the "Deleted" folder !

Any brave soul like to offer a comment/idea/ conduct an exorsism on Evolution(Perhaps I need a neo-Darwinist)
try disabling spamassassin in evolution preferences, maybe it is the problem preventing the downloading of junk mail.

---

### Post by grey1beard on 2011-06-04
Thanks gandaran.
It seems I have Bogofilter set as default, but I've removed all the junk filters in preferences as a temporary measure to see if that does the trick.
Interestingly, the notification from the Forum was delivered !

Regards
John

---

### Post by grey1beard on 2011-06-08
Gandaran, your idea seems to have been in the right direction.
Having at first stopped all the filtering, and manualy deleting for a couple of days, I then used the "ham and spam" to train the bogofilter, and it now seems to be behaving correctly.
As I've had neither false positives nor false negatives, I'll mark this thread solved, while keeping a check on my junk folder.

Regards
John

---

