---
title: "Can't add Facebook to Gwibber"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2010-10-11
Hey everyone,
I'm trying to add my Facebook account to Gwibber. Currently, I only have Twitter. 

I go through the steps and after I enter my login info, there is no button to add the account. Right now, I have no idea what else I can do.

BTW, I just installed 10.10 (Maverick). Could this just be a glitch in the new version?

---

### Post by andymorton on 2010-10-11
Hi

I'm using Maverick and it seems to be working ok here. After you've entered your username and password and clicked on login the Gwibber client should open up. 

Can you describe exactly what you did, step by step?

andy :)

---

### Post by Ranger_Joe on 2010-10-11
In Gwibber, I select Edit > Accounts, then click the add button.

A new screen comes up. I then select Facebook from the drop-down menu and hit the new add button.

A new screen comes up. I then click the Authorize button.

A new screen comes up. I then enter the email and password I use to login to Facebook and hit the Login button.

A new screen comes up. THIS IS THE PROBLEM. It says that my Facebook is authorized but there is no button to finish the process. The only button is the Close button.

---

### Post by koperry on 2010-10-11
I was having the same issue. I went to home folder in nautilus, then checked view hidden files, opened the .config folder, then the gwibber folder, deleted the gwibber.sqlite file. I rebooted then went to broadcast accounts and I was able to login to facebook with an add button along with twitter and flickr. 

I can't say this is a proper fix but it worked great for me.

---

### Post by Ranger_Joe on 2010-10-11
I'm a TOTAL newbie to Ubuntu or any Linux distro for that matter. I'm coming from Windows, which has really jacked me up. This seems a tad ambitious for my skill level... maybe not.

What do people think about this? Should I do it?

---

### Post by koperry on 2010-10-11
The way I described is very simple, at least I thought anyway :)

---

### Post by inkFTW on 2010-10-11
> **koperry said:**
> I was having the same issue. I went to home folder in nautilus, then checked view hidden files, opened the .config folder, then the gwibber folder, deleted the gwibber.sqlite file. I rebooted then went to broadcast accounts and I was able to login to facebook with an add button along with twitter and flickr. 

I can't say this is a proper fix but it worked great for me.

This didn't work for me.  I still can't save a Facebook account.  It says it's authorized but it never gets saved to the list.  Twitter works fine.

---

### Post by Ranger_Joe on 2010-10-11
See? That's my EXACT problem. Although, I haven't tried koperry's fix. Probably because I'm scared of an "unproper" fix. Mainly because if something breaks, I don't yet know how to put it back together in Ubuntu.

Koperry, I'm not nearly as adventurous as you.

---

### Post by inkFTW on 2010-10-11
I also tried this from another thread, but it didn't fix the problem.  The issue is that the final Add button never appears.

> go to facebook -> account -> privacy settings -> applications and websites settings -> "Remove unwanted or spammy applications" -> remove Gwibber
launch gwibber, manage accounts, add facebook, enter your login (email address works here)/password to authorize Gwibber as if it was the first time
the "Add" button does *not* appear yet
close the Gwibber's account window, open it again and redo the facebook connexion process

---

### Post by slooksterpsv on 2010-10-11
[https://bugs.launchpad.net/gwibber/+bug/614742](https://bugs.launchpad.net/gwibber/+bug/614742) - its a known reported bug.

---

### Post by Linye on 2010-10-11
I had that problem and after several times it worked when I unchecked option to "connect automatically" or something like that.

---

### Post by inkFTW on 2010-10-11
> **slooksterpsv said:**
> [https://bugs.launchpad.net/gwibber/+bug/614742](https://bugs.launchpad.net/gwibber/+bug/614742) - its a known reported bug.

Yea, I found that right after my previous post.  Going through it now and so far none of the workarounds have fixed it although they seem to have worked for some other people so maybe they'll work for Ranger_Joe.

---

### Post by slooksterpsv on 2010-10-11
Ok this is weird, want to know how I fixed it? I created a new account, logged into the new account, created the gwibber facebook account and it worked! Ok odd, I migrated my previous user account over and it had old rc, lts, etc. information in it (i'd migrate that stuff too), so I dunno.

---

### Post by nicfallenangel on 2010-10-11
I had the same issue on a live CD. I was able to quit Gwibber and re-open it and add the account. May be worth a try.

---

### Post by eshm on 2010-10-12
I just wanted to let you know what my workaround seemed to be not checking "Remember me on Gwibber" option when you Login to Facebook.  I tried deleting the SQL file under /.config/gwibber but that didn't seem to work.  I don't know why this simple checkbox allows it to work, but as its been said this a known issue.

Hope this helps!

---

### Post by inkFTW on 2010-10-12
> **eshm said:**
> I just wanted to let you know what my workaround seemed to be not checking "Remember me on Gwibber" option when you Login to Facebook.  I tried deleting the SQL file under /.config/gwibber but that didn't seem to work.  I don't know why this simple checkbox allows it to work, but as its been said this a known issue.

Hope this helps!

Just tried this and it also worked for me.

---

### Post by nlsthzn on 2010-10-12
Just for some more info, I had the exact same problem in 10.04 actually... after attempting in a few times a day it just worked one day (not a great solution I know)...

---

### Post by Ranger_Joe on 2010-10-12
Eshm has the perfect solution. If you DO NOT check the "remember me on Gwibber" box, you'll be fine. You'll get the add button you're looking for at the end! 

Thank you!

---

### Post by hesapotman on 2010-10-13
Well, I see about 10 different ways that some people say they were able to fix this ... But none of them worked for me.

Here is the solution that DID WORK for me. It was posted on Gwibber's Facebook page by Michael Contreras.

> **It only works in version 2.33.0 on 32bit Ubuntu 10.10.**
Delete the folder "desktop-couch" in these 3 folders:
~/.cache
~/.config
~/.local/share

And that's what worked for me. What would be really nice is if the developer of Gwibber fixed this (or perhaps did some regression testing prior to committing this release). But this is a workaround in the meantime.

---

### Post by mrkeef on 2010-10-13
None of these solutions work for me :(

---

### Post by nlsthzn on 2010-10-13
> **mrkeef said:**
> None of these solutions work for me :(

I wonder if this is a bug in Gwibber, or in Ubuntu (and if anyone has filed a bug report)?

---

### Post by slooksterpsv on 2010-10-13
> **nlsthzn said:**
> I wonder if this is a bug in Gwibber, or in Ubuntu (and if anyone has filed a bug report)?

*Double Face Palm*

Yes it's been reported, I posted the link to the bug report on page one of this thread I believe.
[https://bugs.launchpad.net/gwibber/+bug/614742](https://bugs.launchpad.net/gwibber/+bug/614742)

Yup post #10 lol, no worries dude no worries haha.

---

### Post by nlsthzn on 2010-10-13
> **slooksterpsv said:**
> *Double Face Palm*

Yes it's been reported, I posted the link to the bug report on page one of this thread I believe.
[https://bugs.launchpad.net/gwibber/+bug/614742](https://bugs.launchpad.net/gwibber/+bug/614742)

Yup post #10 lol, no worries dude no worries haha.

Sorry about that... thats what happens when you are reading and replying to way to many posts (and a thread has been going for a few days)...

Cheers on reporting the bug (to everyone else feel free to add your weight to the bug by marking it as affecting you!)

---

### Post by Ranger_Joe on 2010-10-13
I'm going to call this one solved everyone. Just don't click "keep me signed in on Gwibber."

I'm now having another problem though. If would really appreciate it if you guys took a look at it:

[http://ubuntuforums.org/showthread.php?t=1594518](http://ubuntuforums.org/showthread.php?t=1594518)

---

### Post by msmx5s on 2010-10-14
I know you marked this solved, but I tried everything here and on other threads until I found the following:

set FireFox as your default browser
open firefox and go to [http://facebook.com/username](http://facebook.com/username)
log in using your username, not your email address
open gwibber and sign in using your username, not your email address

I followed this to the letter, but I have suspicions that all you need to do is have FF as your default browser and make sure you are logged in to your account on there.

Please try my theory out as opposed to what actually worked for me, and let us know. :)

---

### Post by JustinR on 2010-10-14
All I did was this:

```

sudo apt-get purge gwibber

```

Go to [www.facebook.com](www.facebook.com) (I did this in Opera)
Login with Email + Password
Go to Account > Application Settings > Remove Gwibber
Stay logged in.

```

sudo apt-get install gwibber

```

(While logged into facebook)

Start Gwibber
Click 'Add', click 'Facebook', click 'Authorize'. Type in email + password, keep 'Keep logged in' unchecked, Authorize Gwibber to have access to your account, when the Facebook window dissappears and the new 'Add' and 'Cancel' buttons appear, click 'Add'. And now it just works. (The browser window with facebook will say 'Not Logged In' but thats fine, just exit out of the browser/tab.) 

Gwibber works fine for me now.

---

### Post by encho on 2010-10-15
Problem for me is that 'Add' button never appears. I just have white background frame saying 'Success', but no buttons :-(

---

### Post by timgood on 2010-10-16
> **koperry said:**
> I was having the same issue. I went to home folder in nautilus, then checked view hidden files, opened the .config folder, then the gwibber folder, deleted the gwibber.sqlite file. I rebooted then went to broadcast accounts and I was able to login to facebook with an add button along with twitter and flickr. 

I can't say this is a proper fix but it worked great for me.

And it worked for me too. Thanks mate!

---

### Post by mjbennison on 2010-10-16
Didn't work for me. Just updated to 10.10 and I now can no longer login to Facebook. Mind you, I had the same issue on the 10.04 update which I resolved by deleting couchdb in some config file or other. I have tried the advice in this thread and none of it works. I tried the same fix as for 10.04, no joy.

So... goodbye Gwibber. As an Ubuntu default application, this really sucks! :mad:

---

### Post by nlsthzn on 2010-10-16
> **mjbennison said:**
> Didn't work for me. Just updated to 10.10 and I now can no longer login to Facebook. Mind you, I had the same issue on the 10.04 update which I resolved by deleting couchdb in some config file or other. I have tried the advice in this thread and none of it works. I tried the same fix as for 10.04, no joy.

So... goodbye Gwibber. As an Ubuntu default application, this really sucks! :mad:

Shame when there are issues in certain applications like this (and trying to get MXIT to work in Empathy)... really drops the whole experience a couple of notches (at least in the case of Empathy there is Pidgin that works, but that doesn't integrated so well into the top bar and thus is not ideal...)

---

### Post by mjbennison on 2010-10-16
Indeed. 

I have an Android based mobile phone. Facebook just works there - login is automatic and the app is reasonable. I have had no end of problems with Gwibber - posts not being sent, posts being duplicated, login issues. Guys, the problem has been solved, why is it so difficult in Gwibber? ](*,)

In all, my experience in moving from 10.04 to 10.10 was a lot more pleasant than that from 9.10 to 10.04 - but the little irritations are still there...

---

### Post by hesapotman on 2010-10-17
Well here's a strange tidbit ... So today I totally screwed up my distro playing around with crap I shouldn't have been playing with. To fix it, I did a clean re-install of Meerkat. After that I added the PPA for the "gwibber-daily" release and updated to the latest version of gwibber (latest as of the time I'm posting this). Then I did a reboot to commit all changes.

Then I opened gwibber to add my Facebook account, and it just WORKED. No editing the hosts file, no deleting the desktop-couch folders, no nothing ... just worked.

So maybe the developer is getting closer to fixing this? I don't know. But I found it strange that it just worked as-is today.

I will reiterate, however, that letting this regression slip into a default application is really quite sloppy.

---

### Post by adamn on 2010-10-17
@hesapotman

Were you going to add the ppa info?

To add the "gwibber daily" ppa to get the newest gwibber updates follow these instructions:

You can update your system with unsupported packages from this untrusted PPA by adding ppa:gwibber-daily/ppa to your system's Software Sources.

Open a terminal and enter:

```
sudo add-apt-repository ppa:gwibber/daily
```

Now, you should tell your system to pull down the latest list of software from each archive it knows about, including the PPA you just added:

sudo apt-get update

For more info visit: [https://launchpad.net/~gwibber-daily/+archive/ppa]("https://launchpad.net/~gwibber-daily/+archive/ppa")

---

### Post by escaflowne on 2010-10-18
Finally I have managed to add facebook account to gwibber.

Login your facebook.com account. Go to privacy setting. At the bottom there is Applications and websites, click Edit your settings. Click Edit settings and remove gwibber.

Then add facebook in Gwibber.

---

### Post by rotten777 on 2010-10-18
I've tried every solution listed here with no dice. This is frustrating for a big release touting itself as "social from the start" and not being able to use the default social client on the biggest social website on the Internet...

I have the PPA setup and updated, I've removed the couch files, I've deleted the SQL lite stuff, I've removed the app from my FB account, still nothing. Not entirely sure that this is "solved" either

---

### Post by Ranger_Joe on 2010-10-18
Hey everyone, you're right. This is definitely NOT solved. As the author, I've changed the status back to unsolved. I was able to add Facebook once but wasn't able to update my status. It seems as though Gwibber has all sorts of problems with Facebook.

This needs to be fixed ASAP. It can't be that hard. My HTC Droid Incredible syncs with Facebook flawlessly.

---

### Post by rotten777 on 2010-10-18
I'll put up a bounty for this to get fixed. Time to put money where your mouth is I guess...

---

### Post by nlsthzn on 2010-10-18
I would just like to point out to all those crying about this issue to keep in mind FB is fickle and prone to problems even if you use it from a web browser many times and it doesn't surprise me if applications that try and interact with it does sometimes have issues...

I am not trying to make excuses for Gwibber or Ubuntu just saying there is a high likely hood the fault is not on their side...


Neil

---

### Post by rotten777 on 2010-10-18
> **nlsthzn said:**
> I would just like to point out to all those crying about this issue to keep in mind FB is fickle and prone to problems even if you use it from a web browser many times and it doesn't surprise me if applications that try and interact with it does sometimes have issues...

I am not trying to make excuses for Gwibber or Ubuntu just saying there is a high likely hood the fault is not on their side...


Neil

It works wonderfully on my Android based phone 99% of the time.

---

### Post by jpepin on 2010-10-20
> **hesapotman said:**
> After that I added the PPA for the "gwibber-daily" release and updated to the latest version of gwibber (latest as of the time I'm posting this). 
Thanks...this worked for me!  THis is the only troubleshooting step I took, and it worked great.  I guess the daily build has already worked out this bug.  

> **adamn said:**
> @hesapotman

```
sudo add-apt-repository ppa:gwibber/daily
```



This  should be:

```
sudo add-apt-repository ppa:gwibber-daily/ppa
```

---

### Post by hubutm20 on 2010-10-21
today i had the same problem and i found this on Launchpad bug report site.

"Not sure if I had the same problem, but try to open this page: [http://http://www.facebook.com/username]("http://http://www.facebook.com/username") , go back to gwibber and use your username instead of your email when you login to your account. After that the Add button appeared for me."

btw,i'm using LinuxMint8 (ubuntu 9.10) whit gwibber 2.33.0

---

### Post by segphault on 2010-10-21
Facebook's broken application-wide rate limit is preventing Gwibber from operating properly. The problem is entirely on Facebook's end and there isn't a lot that we (the Gwibber developers) can do to fix it ourselves. We have reported the issue to them and they are aware of it: [http://bugs.developers.facebook.net/show_bug.cgi?id=13040](http://bugs.developers.facebook.net/show_bug.cgi?id=13040)

For more details, you can refer to these blog posts:
[http://blogs.gnome.org/kenvandine/2010/10/19/gwibber-and-facebook-call-for-help/](http://blogs.gnome.org/kenvandine/2010/10/19/gwibber-and-facebook-call-for-help/)
[http://bugs.developers.facebook.net/show_bug.cgi?id=13040](http://bugs.developers.facebook.net/show_bug.cgi?id=13040)

---

### Post by parselsc on 2010-11-03
Hi there, this may be helpful, but I ran:

cparsels@desktop:~$ strace -o "log.txt" gwibber

on my desktop that was experiencing the issue of no "Add" button following the
successful login and authorization of my facebook account through the Gwibber
desktop application.

Here is what was returned:

** (gwibber:1775): WARNING **: Trying to register gtype 'WnckWindowState' as
enum when in fact it is of type 'GFlags'

** (gwibber:1775): WARNING **: Trying to register gtype 'WnckWindowActions' as
enum when in fact it is of type 'GFlags'

** (gwibber:1775): WARNING **: Trying to register gtype
'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'

** (gwibber-accounts:1783): WARNING **: Trying to register gtype
'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber-accounts:1783): WARNING **: Trying to register gtype
'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber-accounts:1783): WARNING **: Trying to register gtype
'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'

The Gwibber application opens, completed authorization (again) and then there
was an "Add" button. At least this worked for me.

---

### Post by Ranger_Joe on 2010-11-05
I have deleted and added my Facebook account on Gwibber several times to test it. That and I was working on a workaround for updates using Twitter. 

Regardless, I've deleted and added both several times. I've had a few hangups but it's always worked the second time. For the purposes of this thread, I'm going to mark this thing solved.

I will be un-subscribing to this thread. If there is someone who is still having huge problems, send me a PM and I'll re-subscribe and re-mark it unsolved.

Thanks!

---

### Post by hesapotman on 2011-08-09
> **adamn said:**
> @hesapotman

Were you going to add the ppa info?

To add the "gwibber daily" ppa to get the newest gwibber updates follow these instructions:

You can update your system with unsupported packages from this untrusted PPA by adding ppa:gwibber-daily/ppa to your system's Software Sources.

Open a terminal and enter:

```
sudo add-apt-repository ppa:gwibber/daily
```

Now, you should tell your system to pull down the latest list of software from each archive it knows about, including the PPA you just added:

sudo apt-get update

For more info visit: [https://launchpad.net/~gwibber-daily/+archive/ppa]("https://launchpad.net/~gwibber-daily/+archive/ppa")

I didn't want to steal your thunder. How did you find the info anyway? Did you Google "gwibber daily ppa"? :confused:

---

### Post by slooksterpsv on 2011-08-09
> **hesapotman said:**
> I didn't want to steal your thunder. How did you find the info anyway? Did you Google "gwibber daily ppa"? :confused:

Well they may have checked the bug reports and seen it was a bug and found that a newer version (in a PPA) fixed the issue. Generally that's what I've seen, or if there's a feature I want from a new version, I find a PPA for that new version (e.g. Firefox) and install the updated version from that.

We had tons of people trying to solve this puzzle for why it wouldn't add, quite a few threads. So I'm sticking with bug -> reply saying ppa fixed -> found said ppa -> installed from ppa.

EDIT: Ubuntu doesn't do rolling releases for programs, mainly it releases what's on the CD, and does security fixes or patches. To get the new programs you have to upgrade to a newer version of the OS or use a PPA.

---

