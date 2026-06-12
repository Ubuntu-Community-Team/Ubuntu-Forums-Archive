---
title: "Liferea or other RSS reader for a forum thread?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by MaindotC on 2010-02-05
Is there a way to subscribe to a thread on a forum so that my reader will populate with any replies?  For example, suppose I wanted to subscribe to a thread and watch all replies populate.  I know in the case of many forums you get an email stating a new reply has been posted.  I don't mean to be ungrateful of this functionality but I was wondering if there's some way to get my rss reader to show replies to a specific THREAD and not the sub-forum in which all the threads reside.

I found [this thread](http://ubuntuforums.org/showthread.php?t=171291) which talks about favourite RSS readers.  I downloaded and installed liferea which seems pretty cool, but if I subscribe to a forum, I get ALL the postings on that forum and not just one particular thread in which I'm interested.  What I'm seeking is something like twitter where the minute someone posts a reply I see it pop-up, kind of like how tweets pop up in [TwitKit](https://addons.mozilla.org/en-US/firefox/addon/6845).

Anyone know of how to do this in Liferea or other RSS viewer?  Thanks!

---

### Post by lovinglinux on 2010-02-06
That would be a nice feature. I currently use RSS to read new posts on my favorite sub-forums and the user CP to see which threads have new messages. I don't set it up to send e-mail warnings, because it's kind of annoying. So all I need to do is visit the [Subscription](http://ubuntuforums.org/subscription.php?do=viewsubscription) page and it will show all threads with new replies.

BTW, this question would better placed at the [Forum Feedback & Help](http://ubuntuforums.org/forumdisplay.php?f=48).

You could also create a RSS feed using [Dapper]("http://www.dapper.net/dapp-factory.jsp"). It has been a while since I used that service, but I guess it has some sort of template that you can copy after you create a RSS for the first thread, otherwise it wouldn't be very practical if you want to follow several threads.

---

### Post by mushwars on 2010-02-06
thats the thing, rss feaders read rss ( xml pages ) that are generated upon a blog post, etc. I am a php web developer and I wrote a little script that would output with GD the most recent post on my forum, so I could have it in my signature. I had to preg match the html tags on the page, it is really harder than you would think, the source of an html page is nothing like how it appears. therefore you cant just tell the program to read the top right line of text, you have to tell it EXACTLY how to find it.

As far as a program that does this goes, I can tell you that you are not going to find one. They are impracticle and they would have to be coded differently for EVERY forum, even so much as a different theme on a forum would change how the script would have to be coded for that to work :D

---

### Post by MaindotC on 2010-02-06
> **lovinglinux said:**
> BTW, this question would better placed at the [Forum Feedback & Help](http://ubuntuforums.org/forumdisplay.php?f=48).

This was really meant for any forum, not UF, and I wasn't sure if it was a function that would be developed on the client or server side.

Edit:I don't know if this is what either of you were saying, but it's a server-side issue and per [this thread on HFBoards](http://hfboards.com/showthread.php?t=713230) which is really where I could best use this suggested functionality, it seems that the RSS for an individual thread would have be enabled by forum administration.

---

### Post by lovinglinux on 2010-02-06
> **strAlan said:**
> This was really meant for any forum, not UF, and I wasn't sure if it was a function that would be developed on the client or server side.

Oh, then I'm afraid you will be limited to something like dapper.

---

