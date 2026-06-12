---
title: "How do I fix.... Update manager"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by ~CC~ on 2010-04-19
W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release.gpg](http://packages.medibuntu.org/dists/karmic/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.medibuntu.org http:

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.medibuntu.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by nhasian on 2010-04-19
i'm getting the same error with lucid.  i'm guessing the server is down :)  try again tomorrow.

---

### Post by barney385 on 2010-04-19
I started a thread about this yesterday also, but I can't find it.

But I ended up editing my source list and replacing the old site with a mirror...

---

### Post by ~CC~ on 2010-04-19
I tried to see if one had been started but didn't see one, and Thank you both....       Off to learn how to replace 'em

---

### Post by howefield on 2010-04-19
You have these two, and probably others...

[http://ubuntuforums.org/showthread.php?t=1457174](http://ubuntuforums.org/showthread.php?t=1457174)
[http://ubuntuforums.org/showthread.php?t=1457340](http://ubuntuforums.org/showthread.php?t=1457340)

The Medibuntu website is up, but anything to do with the packages isn't. No indication as to why, which isn't unusual for them.

---

### Post by tperwez on 2010-04-19
> **~CC~ said:**
> W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release.gpg](http://packages.medibuntu.org/dists/karmic/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.medibuntu.org http:

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.medibuntu.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

I have had the same problem with Update Manager since Saturday. I do not think it has anything to do with the server being down. I updated from 9.04 to 9.10 with an iso image on Friday and on Saturday morning the system started to freeze up. When I tried to update packages etc, I got those errors including the Index file(s) problem. I get he same errors when I use

sudo apt-get update

I even tried to use different server and also asked the system to find the best server. Even then I got those errors. That was Saturday morning and I had the same problem an hour ago (Monday late afternoon, USA EST).

Did you Upgraded to newer version also? 

Tariq

---

### Post by 2hot6ft2 on 2010-04-19
> **tperwez said:**
> Did you Upgraded to newer version also? 

I didn't do an upgrade and I'm getting it too like many people are.

---

### Post by howefield on 2010-04-19
> **tperwez said:**
> I do not think it has anything to do with the server being down.

Do you still get the problem if you comment out the Medibuntu servers.

---

### Post by ~CC~ on 2010-04-20
I'm to frustrated to try to fix it myself right now. Whats are the chance Ubuntu will fix it in time?

Thanks for everyone's responses. 

Not even up to postinng right now, so may not be around for a bit... but thank you and I will check back periodically to see if there is any new information...

no upgrade, just update for ubuntu 9.10, if that's what I still have........

---

### Post by howefield on 2010-04-20
> **~CC~ said:**
> I'm to frustrated to try to fix it myself right now. Whats are the chance Ubuntu will fix it in time?

Why do you think Ubuntu should fix a Medibuntu problem and in time for what ?

It isn't update manager that needs fixing. The issue is because a third party repository that you have added to your sources is down, it is Medibuntu who need to fix.

When they manage to sort it out, it might be worth downloading the debs for the files you want and saving them some place in case you need them again. Medibuntu have "frequent" outages and generally don't provide any indication as to the problem nor solution, at least not on the website.

I have the libdvdcss2 and w64codecs .debs saved from Medibuntu, just means periodically checking versions are current.

The threads linked up above contain mirrors that you can use to get what you want.

---

### Post by Paddy Landau on 2010-04-20
They expect to have it fixed on Wednesday.

Unless it's urgent, just wait a couple of days.

---

### Post by ~CC~ on 2010-04-20
What is Medibuntu? I have Ubuntu 9.10.
[CENTER]:confused:


[/CENTER]

---

### Post by Paddy Landau on 2010-04-20
> **~CC~ said:**
> What is Medibuntu?
All software for Ubuntu is stored on repositories (well, not all, but nearly all). This makes it dead easy to install, automatically update, and uninstall programs, unlike (say) Windows.

Medibuntu is one of those repositories.

At the moment Medibuntu isn't working, so the Update Manager can't reliably check for upgrades and will give an error when you try.

---

### Post by howefield on 2010-04-20
> **~CC~ said:**
> What is Medibuntu?

What you refer to in your opening post.

> W: Failed to fetch **[http://packages.medibuntu.org](http://packages.medibuntu.org)**/dists/karmic/Release.gpg Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

Try medibuntu.org to find out what it is.

---

### Post by evertmantel on 2010-04-21
ping packages.medibuntu.org
PING packages.medibuntu.org (88.191.82.11) 56(84) bytes of data.
^C
--- packages.medibuntu.org ping statistics ---
325 packets transmitted, 0 received, 100% packet loss, time 324715ms

Meaning it's still down...  :confused:

---

### Post by polly1 on 2010-04-21
Hi  evermantel

Please see this thread ["http://ubuntuforums.org/showthread.php?t=1458747&highlight=Morius1"].

Start Synaptic Manager, then Settings,and then Repositories. Take the action per Morius1`s post and your Update Manager problem should be solved.

It just worked for me on Karmic and (beta) Lucy and will presumably do so on previous Ubuntu s. 

Cheers

:guitar:

---

### Post by cgul1 on 2010-04-21
> **polly1 said:**
> Hi  evermantel

Please see this thread ["http://ubuntuforums.org/showthread.php?t=1458747&highlight=Morius1"].

Start Synaptic Manager, then Settings,and then Repositories. Take the action per Morius1`s post and your Update Manager problem should be solved.

It just worked for me on Karmic and (beta) Lucy and will presumably do so on previous Ubuntu s. 

Cheers

:guitar:

hey thanks, that worked for me in Karmic

cgul1 8-)

---

### Post by polly1 on 2010-04-23
Hi evertmantel

Happy to help-sorry about the missed "T". Should have been Lucid(beta), mind must have been elsewhere!

---

