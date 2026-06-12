---
title: "Rhythmbox Radio -- &quot;Cannot resolve proxy hostname&quot;"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by serpicojam on 2010-01-03
I'm a general user, not a developer. I'm not the guy, in other words, to write code to solve a problem, so I'm looking for help:

When I try to play any internet radio stations with Rhythmbox I get the following error message: "Couldn't start playback -- Cannot resolve proxy hostname."

My guess is that this issue has been solved elsewhere, but I haven't been able to find the solution. Any help would be appreciated.

---

### Post by overdrank on 2010-01-03
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by serpicojam on 2010-01-04
Thanks! Any insight on the issue I'm having?

---

### Post by joejk2 on 2010-02-03
**[Bump]**

Same symptoms on 9.10 (32 bit) for both 'Radio' and 'LastFM'.  

Any suggestions?

Thanks, 
Joe

---

### Post by WhiteHorse on 2010-02-20
I fixed this by going to System->Preferences->Network Proxy

And then set it to "Direct connection to internet"\
And then hit "Apply settings system-wide"

---

### Post by joejk2 on 2010-02-24
Of course!  Whoops...

Many thanks WhiteHorse, 
Joe

---

### Post by drpjkurian on 2010-09-12
Thanks whitehorse

---

### Post by networm on 2010-10-03
Greetings everybody,

I can't set my proxy conf to direct connection. I have to set it to Auto as it is required by my Uni library online database system. Is there any work around besides the one suggested here?

tq in advanced

ntwrm:(

---

### Post by Godspell on 2010-12-19
> **networm said:**
> Greetings everybody,

I can't set my proxy conf to direct connection. I have to set it to Auto as it is required by my Uni library online database system. Is there any work around besides the one suggested here?

tq in advanced

ntwrm:(

Hey, I know it's been a while you've asked this question (and not been replied to) but have you tried this in the Firefox?> Preferences -> Advanced -> Network -> Settings -> check "Auto-detect proxy settings for this network"
If you have and still doesn't work, another possible way around maybe (in the same setting area of Firefox) > choose "Automatic proxy configuration URL" and enter the proxy address manually for e.g proxy.uni.ac.uk
But of course, you'll have to ask around the actual proxy address at your Uni.

Hope it works, mate.

Regards,
GS

---

### Post by dumbledore3 on 2011-08-16
unfortunately, firefox isn't the issue here - the problem is that rhythmbox seems unable to parse the autoconfiguration file for proxy (i.e. wpad.dat).  i debugged this a little and the error message is being thrown from gstsouphttpsrc.c, i.e. the soup http plugin for gstreamer, but when i tried manually downloading the file using gstreamer it worked fine... so i'm guessing this is a RB bug.

---

### Post by mani2604 on 2011-11-28
> **WhiteHorse said:**
> I fixed this by going to System->Preferences->Network Proxy

And then set it to "Direct connection to internet"\
And then hit "Apply settings system-wide"

Hey thanx a lot... That worked without any second thought!@!

---

### Post by eldafani on 2012-05-17
I can't listen to radios with Rhythmbox 2.96 in Ubuntu 12.04. The error message is "Cannot resolve proxy hostname () ". I was able to find the network proxies with a search in system settings, but did not see the option to connect directly to the internet or apply system-wide.  Instead, I see method, and under it none, manual or automatic. Can someone please help me?

Thank you,
Daniel

---

### Post by Moriarty123456 on 2013-04-12
The location to Network Proxy has changed.

Try System Tools --> System Settings --> Network --> Network Proxy

Change it to "none" and you are done.

---

### Post by overdrank on 2013-04-12
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

