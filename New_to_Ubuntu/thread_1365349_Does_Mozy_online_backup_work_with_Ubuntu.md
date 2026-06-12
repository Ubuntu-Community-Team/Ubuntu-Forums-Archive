---
title: "Does Mozy online backup work with Ubuntu?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by mickeyjoe on 2009-12-27
Does Mozy online backup work with Ubuntu?  If not, please recommend a service that does.  I want to get started backing up online within the next few hours with a reputable service that costs around $5/month unlimited.

---

### Post by infinitejones on 2009-12-27
[Google is your friend]("http://www.google.com.au/search?q=mozy+online+backup+ubuntu")... looks like the short answer is no.

The longer answer is: I can't find a Linux client anywhere. I did some digging around on their site to see if the source code's available, but I very much doubt it.

If found [this Ubuntu Forums thread]("http://ubuntuforums.org/showthread.php?t=701712") where someone asked the same question and got a lots of answers, some useful, some not so much.

If there's a specific reason you want to use Mozy, you might be out of luck - you could try running the Windows client via Wine but don't bank on it working. 

If you just want general online backup facilities, [Dropbox works just fine]("http://www.ubuntugeek.com/howto-install-dropbox-in-ubuntu-9-10karmic9-04jaunty8-10intrepid8-04hardy.html") on Ubuntu as far back as Gutsy. It's free for up to 2GB storage and integrates well with Nautilus. Jeez, I should work for those guys.

Ubuntu One is great as well (as long as you're using Karmic).

---

### Post by mickeyjoe on 2009-12-27
> **infinitejones said:**
> [Google is your friend]("http://www.google.com.au/search?q=mozy+online+backup+ubuntu")... looks like the short answer is no.

The longer answer is: I can't find a Linux client anywhere. I did some digging around on their site to see if the source code's available, but I very much doubt it.

If found [this Ubuntu Forums thread]("http://ubuntuforums.org/showthread.php?t=701712") where someone asked the same question and got a lots of answers, some useful, some not so much.

If there's a specific reason you want to use Mozy, you might be out of luck - you could try running the Windows client via Wine but don't bank on it working. 

If you just want general online backup facilities, [Dropbox works just fine]("http://www.ubuntugeek.com/howto-install-dropbox-in-ubuntu-9-10karmic9-04jaunty8-10intrepid8-04hardy.html") on Ubuntu as far back as Gutsy. It's free for up to 2GB storage and integrates well with Nautilus. Jeez, I should work for those guys.

Ubuntu One is great as well (as long as you're using Karmic).

I have 51 gigs right now and will go much higher in gigs.  I'll check out your links now.  I hope to stay affordable.

---

### Post by mickeyjoe on 2009-12-27
> **mickeyjoe said:**
> I have 51 gigs right now and will go much higher in gigs.  I'll check out your links now.  I hope to stay affordable.

I just checked drop box.  I really like it; however, it is not going to be affordable for me at $20/month.  I am looking for something like Mozy that costs around $5/month unlimited.  I wander if Wine would allow Ubuntu to use Mozy or other services.  How much space on my HD would Wine take up?

---

### Post by infinitejones on 2009-12-27
I remember looking at [Amazon S3]("http://aws.amazon.com/s3/") when I was looking for somewhere to backup my /home partition - they charge $0.15 per GB so with 51GB you'd be looking at $7.85/mth.

Here's someone talking about their experiences backing up large amounts of data with S3 - [http://jeremy.zawodny.com/blog/archives/007624.html]("http://jeremy.zawodny.com/blog/archives/007624.html")

In the end I went with free Dropbox because I'm never going to go above 2GB, but there's definitely a client for S3 that works on Ubuntu - I remember trying it out.

The one thing that strikes me is that, as with everything, not all online backups are the same. Storing data costs money, full stop, so while it's great that Mozy are currently offering unlimited data for $5, you have to wonder about a couple of things - technical reliability and long-term stability from a business point of view. What will they do in a few years when everyone wants to back up 50GB of data and it costs more than $5 per user per month to keep running?

Personally if I had 50GB+ of data (which I assume is very important data if you're backing it up off-site) I'd pay the extra and go with someone like Amazon who you know are going to be weapons-grade when it comes to technical reliability and business stability.

OK, so I'm now waiting for the job offer from Amazon S3 as well as Dropbox...

---

### Post by infinitejones on 2009-12-27
> **mickeyjoe said:**
> How much space on my HD would Wine take up?

Not a lot. It's not like Virtualbox, you're not creating a virtual machine or anything. It's just doing something clever with the core Windows DLLs to enable you to run some Windows apps (note some - by no means all) on Linux.

I've just checked on the Wine website - [it's unlikely that Mozy will work]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8607&iTestingId=15626"). 

I suspect the difficulty comes from the fact that Mozy would need to run a service or a daemon or something on your local machine to check whether the contents of your backup folder has changed, and an application running via Wine can't do that. Dropbox, Amazon S3 etc run daemons too, but they use native Linux software.

---

### Post by mickeyjoe on 2009-12-27
> **infinitejones said:**
> Not a lot. It's not like Virtualbox, you're not creating a virtual machine or anything. It's just doing something clever with the core Windows DLLs to enable you to run some Windows apps (note some - by no means all) on Linux.

I've just checked on the Wine website - [it's unlikely that Mozy will work]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8607&iTestingId=15626"). 

I suspect the difficulty comes from the fact that Mozy would need to run a service or a daemon or something on your local machine to check whether the contents of your backup folder has changed, and an application running via Wine can't do that. Dropbox, Amazon S3 etc run daemons too, but they use native Linux software.

So will Amazon or this S3 work with Ubuntu that you speak of?  There certainly appears to be very very limited, if not any online services for backup for Ubuntu only users - ?

---

### Post by tom.swartz07 on 2009-12-27
> **mickeyjoe said:**
> So will Amazon or this S3 work with Ubuntu that you speak of?  There certainly appears to be very very limited, if not any online services for backup for Ubuntu only users - ?

Amazon does work very well with Ubuntu.

Heres a chart if you want to look up some alternatives:
[http://lifehacker.com/5064688/free-online-storage-feature+by+feature-comparison-chart](http://lifehacker.com/5064688/free-online-storage-feature+by+feature-comparison-chart)

---

### Post by mickeyjoe on 2009-12-27
> **tom.swartz07 said:**
> Amazon does work very well with Ubuntu.

Heres a chart if you want to look up some alternatives:
[http://lifehacker.com/5064688/free-online-storage-feature+by+feature-comparison-chart](http://lifehacker.com/5064688/free-online-storage-feature+by+feature-comparison-chart)


Amazon looks like the way to go.  I'm just curious, I can't figure out their pricing.  I attempted to use their online calculator, but got an error.  Does anyone have an estimate how much their pricing is?  I have about 51 gigs of photos right now.

---

### Post by Cuco3 on 2009-12-27
> **infinitejones said:**
> [Google is your friend]("http://www.google.com.au/search?q=mozy+online+backup+ubuntu")... looks like the short answer is no.lol be careful man I got a warning for suggesting the same thing. Telling people their answer is well documented via Google is a cardinal sin.

---

### Post by mickeyjoe on 2009-12-27
while i'm at it, how do i tell my control panel to mark each and every one of my posts to email notify me so that i don't have to go in and do it manually - ?

---

### Post by infinitejones on 2009-12-27
Apologies for adding another layer of complexity (and cost), but you'd need to also find/use some client software for Amazon S3 - they don't automatically provide a desktop client in the way that Dropbox or Mozy does.

So - have a look at Jungledisk - that's the software that lets you connect to Amazon S3. The relevant page is this one:

[www.jungledisk.com/personal/simply_backup/pricing/]("http://www.jungledisk.com/personal/simply_backup/pricing/")

That takes away some of the complexity of the Amazon pricing model too.

Basically - with 51GB of data you'd be looking at:

$2/mth flat fee
$0.15 x 46GB storage fees (because the first 5GB is free)

I make that $8.90/mth. 

Since it's a backup, you're not going to have worry about the $0.17/GB for downloading the data (unless you need to retrieve it, which hopefully you won't!). Also, until the end of June, you won't have to pay a fee to upload it, but after that it would be $0.10 per GB uploaded.

So if you're uploading an extra 2GB a month (you mentioned your data would be increasing over time), your cost would increase by $0.30/mth until the end of June, and then by $0.50/mth after that, because you'd also be paying an extra $0.20 for the 2GB extra you upload each month.

---

### Post by infinitejones on 2009-12-27
> **mickeyjoe said:**
> while i'm at it, how do i tell my control panel to mark each and every one of my posts to email notify me so that i don't have to go in and do it manually - ?

Near the top of the posts on each page - click on the arrow next to "thread tools" - select Subscribe To This Thread - then select "instant email notification" from the drop-down.

---

### Post by jwooton on 2010-01-19
another alternative...much better pricing.  Start out with the 100GB plan at only 2.99 a month

No native client...but good support for helping you find a client that works well for you.  There are plenty client choices out there...some GUI and some not.

[www.datastorageunit.com]("http://www.datastorageunit.com")

---

