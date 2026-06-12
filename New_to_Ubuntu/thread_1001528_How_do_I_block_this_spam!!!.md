---
title: "How do I block this spam!!!"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by furoido on 2008-12-04
Hi guys,

Generally, the spam filter on Evolution works pretty well, with one exception. I keep on getting spam emails apparently sent by me to me! How on earth do I stop them? Marking them as spam doesn't seem to help.

Here are a couple of examples:

Return-Path: <3231273501@jcom.home.ne.jp>
Received: from mx12.m3.home.ne.jp ([220.152.44.12]) by mta21.m3.home.ne.jp with ESMTP id <20081203165029.WADU9558.mta21.m3.home.ne.jp@mx12. m3.home.ne.jp> for <3231273501@jcom.home.ne.jp>; Thu, 4 Dec 2008 01:50:29 +0900
Received: from amschool.edu.sv ([78.174.93.249]) by mx12.m3.home.ne.jp with SMTP id <20081203165027.JFNN4629.mx12.m3.home.ne.jp@amscho ol.edu.sv> for <3231273501@jcom.home.ne.jp>; Thu, 4 Dec 2008 01:50:27 +0900
To: [email]3231273501@jcom.home.ne.jp[/email]
Subject: Re: Order status
From: [email]3231273501@jcom.home.ne.jp[/email]
MIME-Version: 1.0
Importance: High
Content-Type: text/html
Date: Thu, 4 Dec 2008 01:50:28 +0900
Message-Id: <20081203165027.JFNN4629.mx12.m3.home.ne.jp@amscho ol.edu.sv>
X-Evolution-Source: pop://3231273501@mail/


and...

Return-Path: <3231273501@jcom.home.ne.jp>
Received: from mx22.m3.home.ne.jp ([220.152.44.15]) by mta21.m3.home.ne.jp with ESMTP id <20081204003604.BAOY9558.mta21.m3.home.ne.jp@mx22. m3.home.ne.jp> for <3231273501@jcom.home.ne.jp>; Thu, 4 Dec 2008 09:36:04 +0900
Received: from 24-217-194-118.dhcp.stls.mo.charter.com ([24.217.194.118]) by mx22.m3.home.ne.jp with SMTP id <20081204003603.ECMW24577.mx22.m3.home.ne.jp@24-217-194-118.dhcp.stls.mo.charter.com> for <3231273501@jcom.home.ne.jp>; Thu, 4 Dec 2008 09:36:03 +0900
To: [email]3231273501@jcom.home.ne.jp[/email]
Subject: Your order
From: [email]3231273501@jcom.home.ne.jp[/email]
MIME-Version: 1.0
Importance: High
Content-Type: text/html
Date: Thu, 4 Dec 2008 09:36:04 +0900
Message-Id: <20081204003603.ECMW24577.mx22.m3.home.ne.jp@24-217-194-118.dhcp.stls.mo.charter.com>
X-Evolution-Source: pop://3231273501@mail/

and...

Return-Path: <3231273501@jcom.home.ne.jp>
Received: from mx22.m3.home.ne.jp ([220.152.44.15]) by mta22.m3.home.ne.jp with ESMTP id <20081203133221.TODF8834.mta22.m3.home.ne.jp@mx22. m3.home.ne.jp> for <3231273501@jcom.home.ne.jp>; Wed, 3 Dec 2008 22:32:21 +0900
Received: from amada.com ([90.151.141.21]) by mx22.m3.home.ne.jp with SMTP id <20081203133219.RRPL24577.mx22.m3.home.ne.jp@amada .com> for <3231273501@jcom.home.ne.jp>; Wed, 3 Dec 2008 22:32:19 +0900
To: [email]3231273501@jcom.home.ne.jp[/email]
Subject: RE: Message
From: [email]3231273501@jcom.home.ne.jp[/email]
MIME-Version: 1.0
Importance: High
Content-Type: text/html
Date: Wed, 3 Dec 2008 22:32:20 +0900
Message-Id: <20081203133219.RRPL24577.mx22.m3.home.ne.jp@amada .com>
X-Evolution-Source: pop://3231273501@mail/

---

### Post by jgoguen on 2008-12-04
Do you know how to do message filters in Evolution based on specific headers?  You might be able to do a rule for the Message-Id header if a bunch of them all seem to match a certain pattern.

---

### Post by furoido on 2008-12-04
Sorry jgoguen, no idea..can u show me?!

---

### Post by cmay on 2008-12-04
i do not know where  you live but in Denmark where i live i would have a chance at reporting it to my internet provider which then in return would file reports the right places. also in some cases police. which i do not mind at all. consider also finding out how to do something like that so the spammers do not just get away with it. do not ever contact them your self however. they will think its great since they know its working then. good luck with it.

---

### Post by robalcorn on 2008-12-04
I have also had the same problem with different distibutions of linux. I have also asked the same question as you on various forums and also got the same or various answers.

---

### Post by oldsoundguy on 2008-12-05
your problem has nothing to do with your eMail client (program) or version of Linux or Windows or anything.  It has to do with a weakness in your eMail SERVER.  I have several accounts with different servers.  I get NONE of that on one server .. a few on another .. and another gets bombed!  There is absolutely NOTHING you can do about it except to use an on server eMail preview program (in Windows it is Mail Washer).  Not had the need to investigate for a program for Thunderbird as had no need .. the mail server I use stops all of that crap!

---

### Post by chewearn on 2008-12-05
Based on reading the headers, the spam email return addresses are spoofed/faked.

It's NOT because your email account is hacked, i.e. nobody is using your email account to send spam.

I wonder why the evolution spam filter is not working.  I also got such emails on a daily basis, and the filtering is near perfect.  Maybe you could clear the junk filter database, and let it relearn again.

Another thing you could do is to mark some ham to spam and back again to ham.  You see, a frequent problem is the filter algorithm don't get enough example of ham to learn from, so the results are not as good.

---

### Post by oldsoundguy on 2008-12-05
you really do NOT want to block your own addy in a spam filter or whatever.  I use sending myself an eMail to get items or messages I want to save that I pick up on sites like HERE .. and I am not at home! or I will forward an eMail I pick up when away from home so that it can be saved or acted on when I get back.

---

### Post by chewearn on 2008-12-05
The evolution spam filter is smarter than that.  When you mark it as spam, it will not blacklist your own address.

---

### Post by jgoguen on 2008-12-05
> **furoido said:**
> Sorry jgoguen, no idea..can u show me?!
Sure can.  I won't show you the Message-Id header since it appears they're all being sent from different areas, but I think we can come up with a fairly good rule by saying "block anything from me, to me, with Importance = High".  Here's how you would do that:


[LIST]
[*]In Evolution, go to the **Edit** menu and choose **Message Filters**.
[*]Make sure that *Show filters for mail* is set to **Incoming** (it should be by default).
[*]Click the **Add** button.
[*]Give your rule a name.  This can be anything you want, it's purely for your own convenience to identify it later.
[*]Change *Find items* to **If all criteria are met**.
[*]In the text box below that (it has two drop down boxes set to "Sender" and "contains") put your email address.
[*]Click the **Add Filter Criteria** button
[*]In the new line that appears, set the first drop down to **Recipients**.
[*]Put your email address in that box as well.
[*]Click the **Add Filter Criteria** button again.
[*]Change the first drop down to **Specific Header**.
[*]In the first text box, enter **Importance**
[*]Change the second drop down to **is**.
[*]In the second text box, enter **High**
[*]Below, where it says **Move to folder**, change this drop down to **Set Status** and choose **Junk** from the second drop down that appears
[*]Click the Add Action button
[*]In the line that appears, change the first drop down to **Delete**
[*]Press **OK** on that window and on the Message Filters window
[/LIST]

This should work for you.  If you have any of these messages in your inbox, select one and push Ctrl+Y to filter it.  If all is set up right, it should disappear and never be seen again (except possibly in your Trash).

I've attached a screenshot of my Evolution window after configuring it the way I said so you can see what it should look like.

---

