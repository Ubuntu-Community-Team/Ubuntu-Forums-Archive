---
title: "very slow down loaf speeds with update manager"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by ajlinzey on 2009-09-30
I'm getting very slow down load speeds with the update manager often as low as 1-2 kB/s. Should I be using a mirror site for the update manager? I'm currently using [http://us.archive.ubuntu.com. Thanks](http://us.archive.ubuntu.com. Thanks)
-Andy

---

### Post by mharrison on 2009-09-30
> **ajlinzey said:**
> I'm getting very slow down load speeds with the update manager often as low as 1-2 kB/s. Should I be using a mirror site for the update manager? I'm currently using [http://us.archive.ubuntu.com. Thanks](http://us.archive.ubuntu.com. Thanks)
-Andy

How often have you noticed this.  I have had this happen to me before, but usually I was able to cancel the download.  Wait a little bit and try again.  

You may have different results, but I am hitting the same server and the last time I updated it was pushing around 900 kb/s.

---

### Post by ajlinzey on 2009-10-02
It happens almost every time I run updates. I occasionally get bursts of 400kB/s
-Andy

---

### Post by Jive Turkey on 2009-10-02
I'm getting this today for the first time too.  It's probably some glitch on the net or something with the repositories.  I'm just going to try later on and hope that it is better then.

---

### Post by doas777 on 2009-10-02
somthing has been up over the last day or so. a number of people (myself included) have been complaining in a few other threads. check em out.

---

### Post by Inaia on 2009-10-02
Ah, so I can assume it's a server issue, not a client problem? Spent an hour researching slow net bugs, etc thinking it was my software >_>

---

### Post by Mutt77 on 2009-10-02
Right now it is everyone hitting the servers for the karmic beta upgrade, they share the same server. I have been trying to upgrade but no luck so far.

---

### Post by ArtLaForge on 2009-10-02
Try this site for beta: [http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/:P](http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/:P)

---

### Post by Inaia on 2009-10-02
Rawrharhar....you buggered that link with the smiley. Will that work with Jaunty?

EDIT: Never mind, thought it was a mirror for the software repositories, didn't read it all the way through.

---

### Post by lhb1142 on 2009-10-02
> **ajlinzey said:**
> I'm getting very slow down load speeds with the update manager often as low as 1-2 kB/s. Should I be using a mirror site for the update manager? I'm currently using [http://us.archive.ubuntu.com. Thanks](http://us.archive.ubuntu.com. Thanks)
-Andy

This is what I did: I went into System > Administration > Software Sources
and then clicked on the arrow (to choose server) Download from [mine is usually set to Main Server]. Click on Other... Then click on Select Best Server and let it do its thing. When the choice is shown, click on select server.

Then close and you will get a dialog telling you your sources are out of date. Choose Reload and you should get a new download of your software sources (though probably not as fast as normally).

Then go into Synaptics Package Manager and click on Mark All Updates, then, when they are shown, click on Apply.

You may have to stop the downloads once or twice (I did) but you will get all your updates, most of which appear to be OpenOffice ones.

I understand that the Karmic beta was released today and this is causing the problem. It's unfortunate that, on the same day the beta was released, we had so many (and so large) updates to Jaunty.

Once your updating is done, you can switch back to your preferred server location for your software sources.

I hope this helps you.

---

### Post by tgalati4 on 2009-10-02
I've noticed it as well.  It's running at 1/10th its normal throughput.  Are there any statistics pages that we can see to verify that the servers are being slammed?

---

### Post by the.phantom on 2009-10-02
i did what this poster did earlier today 

> his is what I did: I went into System > Administration > Software Sources
and then clicked on the arrow (to choose server) Download from [mine is usually set to Main Server]. Click on Other... Then click on Select Best Server and let it do its thing. When the choice is shown, click on select server.
and it failed several times ( the first thing it does is PING the servers)
and i only got 1/2 way when they started failing

but it does show what server it is PINGING, so i just picked one that was ok and after about the 3rd try it worked and could use one in New Zealand

(i'm in usa)

---

### Post by ulfj on 2009-10-02
I noticed that my updates were moving along at glacial speed and jumped on the forum here, I put 2 and 2 together,I'm just going to wait a couple of days till folks have slowed down with the Karmic Beta and all should be back to normal.

---

### Post by doas777 on 2009-10-02
22kBps on a 2400kBps link. wow

---

### Post by alexcckll on 2009-10-03
I've got similar issues... I hit "Check" on Update Manager, and instead of the 48 elemtns being pulled down (what does get pulled down anyway at the point?), only 30-something of 45 came down...

I expanded the twisty to see a whole load of "Fail" lines against the "Translation_GB" lines.

When will I be able to safely and reliably accept system updates again without the risk that it might break my machine?

I've also logged question 84600 in Launchpad - [https://answers.launchpad.net/ubuntu/+question/84600](https://answers.launchpad.net/ubuntu/+question/84600)

---

### Post by starcannon on 2009-10-03
9.10 beta released today(or was it yesterday), the extra server activity is slowing everything down. Things will be fairly slow for the next 45 days. I wish beta was released as a torrent, it would greatly reduce this problem.

GL and HF

---

### Post by alexcckll on 2009-10-03
> **starcannon said:**
> 9.10 beta released today(or was it yesterday), the extra server activity is slowing everything down. Things will be fairly slow for the next 45 days. I wish beta was released as a torrent, it would greatly reduce this problem.

GL and HF
Slow for the next MONTH AND A HALF???!!!  I hope you meant "next 4 to 5 days", and not "next forty-five"...

So I end up stacking about 100-150 security updates in that time?

---

### Post by Paqman on 2009-10-03
> **starcannon said:**
> I wish beta was released as a torrent, it would greatly reduce this problem.


Like all Ubuntu releases, [it is]("http://www.ubuntu.com/testing/karmic/beta"). However, just because it's available as a torrent, doesn't mean people will use it...

---

### Post by starcannon on 2009-10-03
> **alexcckll said:**
> Slow for the next MONTH AND A HALF???!!!  I hope you meant "next 4 to 5 days", and not "next forty-five"...

So I end up stacking about 100-150 security updates in that time?
Sad but true; after the beta comes the release, another big slam to the servers, then like the beta, another big pump of updates to fix issues. In the end, considering what we paid for our OS, this still works out to a minor inconvenience. You can still get your updates, just at a slower speed than usual.

P.S. 
If you go into software sources:

System>Administration>Software Sources:Updates tab> tick-Download all updates in the background

That specifies that it downloads updates automatically, if you ignore it till the next morning, then they are downloaded, and all you need to is click install.

---

### Post by alexcckll on 2009-10-03
Hmm - I paid £650 for my preinstalled-with-Ubuntu laptop.
I tried again at 8:50 - and everything came through fine..

---

### Post by Sidewinder1 on 2009-10-03
Well, it's still slow for me; slogged along at about 56 kB/s on a broadband connection :-(, welcome back to 'dial-up' ;-)

---

### Post by SlappyPappy on 2009-10-03
Well I'm at 8 kB/s.

They don't call it the World Wide Wait for nothing baby.

Rock on with your bad updating self. :guitar:

---

