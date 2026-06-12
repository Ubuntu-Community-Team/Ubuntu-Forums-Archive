---
title: "Launchpad hijacked Firefox!"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-08-08
A few days ago I tried to register at Launchpad as a member/user. I aborted the process when Firefox gave me a warning message that the certificate being presented didn't match the site - that, someone might be spoofing to gain my info. I remember there was a box on the page that had the name of Google in it. I sent an email to them, and received a reply that they would be looking into it.

What is incredibly annoying, is that now every time I start up this computer, the first thing that happens in every profile upon entering either KDE or Gnome, is Firefox starts up and goes to a Launchpad login screen.

(For those who've been reading my discussions about the Toshiba notebook, I need to specify that this computer with this problem isn't that. This computer is a Dell Inspiron 9400 I've been setting up w/ Ubuntu v10.04 LTS.)

I haven't been able to figure out exactly what Launchpad did to hijack my browser like this, but I REALLY, REALLY want to stop it. Can anybody explain to me what they did, and how I can make this stop?

If you can, then thank you, thank you, thank you in advance!

---

### Post by SalHelder on 2011-08-08
In Gnome try opening:

gnome-session-properties

And remove/uncheck firefox if you see it there.

---

### Post by doas777 on 2011-08-08
Bleachbit (in the repos) is a good cache and settings cleaner that works with firefox. I'd install it (via softwarecenter perhaps? )and use it to clean up FF.

---

### Post by beew on 2011-08-08
Check Edit > Preference > General and see what your startup page is set to.

It would be interesting to find out how that could happen in the first place.

---

### Post by scruffyeagle on 2011-08-08
> **beew said:**
> It would be interesting to find out how that could happen in the first place.

Thanks for the replies and suggestions!

As for how it could happen - **_[COLOR="Red"]JAVASCRIPT[/COLOR]_**.

Both my startup page & home page are still the way I'd set them. My startup page is still set as a blank page (how I set it).

---

### Post by scruffyeagle on 2011-08-08
> **SalHelder said:**
> In Gnome try opening:

gnome-session-properties

And remove/uncheck firefox if you see it there.

I found the file, but it's in /user/bin! How can I see its contents, much less edit that?

---

### Post by scruffyeagle on 2011-08-08
> **doas777 said:**
> Bleachbit (in the repos) is a good cache and settings cleaner that works with firefox. I'd install it (via softwarecenter perhaps? )and use it to clean up FF.

Found & installed it. I'll need to really understand its settings before using it though. I NEVER delete a file just because it's old, and the program description indicated that this program is capable of doing exactly that.

---

### Post by beew on 2011-08-08
> **scruffyeagle said:**
> I found the file, but it's in /user/bin! How can I see its contents, much less edit that?

I think that is just to set startup applications and has nothing to do with your problem. Your problem is that Firefox starts at the wrong page, not that it starts automatically. That's why I asked you to open FF and go to Edit > Preference > General and see what your startup page is set to.

If you type "gnome-session-properties" in the terminal it would bring up the window for Startup Applications (which you can find by clicking System Settings under the power button in the upper left corner on the "panel" in Unity).

---

### Post by doas777 on 2011-08-08
> **scruffyeagle said:**
> Found & installed it. I'll need to really understand its settings before using it though. I NEVER delete a file just because it's old, and the program description indicated that this program is capable of doing exactly that.
then a fix is a little reading away...

---

### Post by SavageWolf on 2011-08-08
Have you tried disabling the addon "ubuntu-firefox-addon"?

Also, JavaScript can't do this from a webpage...

---

### Post by beew on 2011-08-08
> **scruffyeagle said:**
> Found & installed it. I'll need to really understand its settings before using it though. I NEVER delete a file just because it's old, and the program description indicated that this program is capable of doing exactly that.


Bleachbit again has nothing to do with your problem. what it does is to clean the cache and remove history etc. As far as I know it doesn't alter your settings, but your issue is exactly that your startup setting get changed.You should be able to just reset it as I said in my last post.

If all else fail just delete the folder .mozilla (go to your home directory, click View > Show Hidden Files and you will find it) It stores all your FF settings so nuking it would definitely work, but it would be an overkill. If you have to do that just make sure you export all your bookmarks first (in html) so you can import them when you restart Firefox.

---

### Post by scruffyeagle on 2011-08-08
> **beew said:**
> I think that is just to set startup applications and has nothing to do with your problem. Your problem is that Firefox starts at the wrong page, not that it starts automatically. That's why I asked you to open FF and go to Edit > Preference > General and see what your startup page is set to.

If you type "gnome-session-properties" in the terminal it would bring up the window for Startup Applications (which you can find by clicking System Settings under the power button in the upper left corner on the "panel" in Unity).

I don't have that option under my power button. Perhaps, because I'm running Ubuntu v10.04 LTS 32-bit?

But your terminal advice worked like a charm. I found the startup list, unchecked some services I won't be using - AND unchecked then REMOVED(!) "Launchpad Reviews Notifier".

I'm guessing you just solved my problem. (THANK YOU, THANK YOU, THANK YOU!) I'm gonna go check. If it worked, I'll be back in a few minutes to mark this thread solved.

---

### Post by beew on 2011-08-08
> **SavageWolf said:**
> 

Also, JavaScript can't do this from a webpage...


My thought too. I think that kind of malware behaviour is not supposed to happen in Ubuntu, and the perpetrator is supposed to be lauchpad??? Someone should look into it.

---

### Post by scruffyeagle on 2011-08-09
> **SavageWolf said:**
> Have you tried disabling the addon "ubuntu-firefox-addon"?

Also, JavaScript can't do this from a webpage...

I've disabled the "ubuntu-firefox-addon",but that didn't fix it.

And, if it wasn't javascript, then what was it? I'm still too pissed off about this to contact Launchpad directly. For one, I don't think ripping them a new you-know-what will be condusive to obtaining assistance from them. For another, I'm not quite ready to go begging the perpetrators of installing this malware for assistance removing it. For now, I'd rather find some other solution, as vs. that.

But, I've remembered something that seems significant in figuring out exactly what they did to cause this. I've remembered there was one instance before I made FF the default browser, when it triggered Konqueror to go to the web page.

So, it's more likely than not, that uninstalling FF completely won't be enough to knock out this malware.

Unless somebody can come up with a good suggestion, I'm considering deleting this profile entirely and going through all the hassle of setting up a new one.

---

### Post by scruffyeagle on 2011-08-09
Update: I tried setting up an entirely new user level profile, and when I logged into Gnome using it for the first time, it triggered FF to go to Launchpad. Therefore, replacing the infected profile with a new one won't work - the infection is at a system level, afflicting any user level profile.

After discovering the infection was in the newly-made profile, I tried to use the other user level profile to come here and update about the result of my little experiment. The other user level profile wouldn't load in Gnome. There was a series of error message boxes on screen. They said:

*) Could not update ICEauthority file /home/wild_turtle/.ICEauthority

*) Problem with configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

*) Nautilus could not create folder /home/wild_turtle/Desktop, /home/wild_turtle/.nautilus.

*) Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.

The entire desktop remained blank with no bars at top or bottom of screen, after the message series ended. I had to use Ctrl/Alt/Del to reboot. At login, I chose to go into that same Gnome profile, to see if the problem persisted. It did. The series of warning boxes on screen were identical to the previous series, and I again had to use Ctrl/Alt/Del to reboot. I'm posting this update message now, using the Admin level profile.

I consider this to be a virus, and I only see one solution: I'm going to reinstall the OS from scratch, and NEVER, REPEAT NEVER!!! go to Launchpad again. And, because I'm a whiner and a blabber, and a person with a genuine social conscience, I'll be telling everybody and all their cousins what happened to me, and warning them to only go there at risk of it happening to them too.

---

### Post by Paqman on 2011-08-09
> **scruffyeagle said:**
> 
I consider this to be a virus, and I only see one solution: I'm going to reinstall the OS from scratch, and NEVER, REPEAT NEVER!!! go to Launchpad again. And, because I'm a whiner and a blabber, and a person with a genuine social conscience, I'll be telling everybody and all their cousins what happened to me, and warning them to only go there at risk of it happening to them too.

Surely you should get to the bottom of what's happened here before drawing any conclusions. I personally think it's extremely unlikely that Launchpad is the source of a virus infection. Launchpad is maintained by Canonical, the people who make Ubuntu. It's used daily by tens (hundreds?) of thousands of people, none of whom are describing a similar problem.

Something strange has happened to your system, but from what I can see it's not clear exactly what.

---

### Post by scruffyeagle on 2011-08-12
> **Paqman said:**
> Surely you should get to the bottom of what's happened here before drawing any conclusions. I personally think it's extremely unlikely that Launchpad is the source of a virus infection. Launchpad is maintained by Canonical, the people who make Ubuntu. It's used daily by tens (hundreds?) of thousands of people, none of whom are describing a similar problem.

Something strange has happened to your system, but from what I can see it's not clear exactly what.

The one thing I'm really sure about, is that my system's settings were hacked and damaged. I can't say with absolute certainty that it was someone at Launchpad - but, at the least it was someone who knew that I'd been at the Launchpad sign up page, because that's where the browser kept trying to send me back to.

Anyway, I wiped out the entire installation shortly after posting my message here. Then, I installed a new one, starting over from scratch. I intend to write it off, file it away, and focus on other things. I might go back to look at a list of bug reports, but I'll NEVER go to their sign up page again. And if the subject comes up, I'll readily describe as accurately as I can exactly what happened to me.

---

### Post by 3rdalbum on 2011-08-12
I think you're going a bit over-the-top; there's no way anything on Launchpad could have got so deep into your system that it causes your web browser (on multiple user accounts) to be redirected to Launchpad. It would need root permissions for what you're saying.

Ubuntu has a bug reporting system in it called Apport. Apport has the ability to report bugs to the user, and give them the option to report them to Launchpad. When clicking on this option, Firefox opens at the Launchpad login page so you can log in and file the bug report, pre-filled with lots of useful diagnostic data.

I'm wondering whether you've changed the Apport settings file, which should be system-wide, to "automatically" report bugs. If there was a program crash on startup, this would cause Apport to come to life on startup too. Or, possibly, you clicked the Report Bug button on one of those prompts and then did not actually log into Launchpad to file the bug, which I guess might possibly cause Apport to assume on login that it has to continue helping you report the bug.

This isn't Windows here. We don't get viruses just by visiting web pages. Launchpad is not malware. If this situation happens again on your fresh install, just try logging into Launchpad and filing a bug (if that's what it is directing you to do) and the behaviour should finish.

---

### Post by eveg on 2011-08-18
i seriously doubt your problem is launchpad. you said you checked the security certificate and it was wrong? you do realize that if so that means the site you were at wasn't launchpad, rather a phishing site posing as launchpad? if that actually happened, you may want to mention it in security discussions here.
 
you need to ask yourself what you did that exposed you to a phishing site. did you click on any links in the fora posted by anyone other than an administrator, or a moderator (someone whose name here is in red), especially links posted by anyone with a recent join date, or not a lot of beans? personally, i wouldn't click on any links posted by anyone not official (anyone without their name in red).
 
did anyone use your computer when you weren't watching everything they were doing, or is any 'friend' who uses your computer enough of a computer expert that you can be watching them and still not completely understand what they're doing? 
 
have you been anywhere dubious online with that computer such as facebook or especially a torrent site or something? is there any communication between that computer and a laptop? any shared programs or files, even music or something you haven't considered as a possible source of problems (and maybe should've depending on where you downloaded it, etc...)? have you used the same thumbdrive or musicplayer with that computer and a laptop, especially a laptop you've used on any network you don't have complete control of? 'free' wireless is usually way too expensive in security bother. even if you're only using the laptop at home (unusual as that usage pattern would be), it may not be properly secured. using a password, or even some forms of encryption, does not really qualify as secure wireless in these days of wardriving script kiddies.
 
even if you haven't done any of these things, simply being online, without topnotch security, is likely to cause trouble. i suggest you read the most recent edition of ubuntu unleashed, with particular attention to the chapter on securing your machine(s) --- i think that's ch. 32 or 33. it'll also refer you to the security discussions here in the fora, if i recall.
 
doing a reinstall is a good idea, if you suspect a security problem. only, if you back up your files, you need to be sure you aren't bringing your problem with you. it would be a nuisance to lose all your music and pictures, but you need to be careful not to reimport your problem. it can be a good thing to keep all your personal files, music pictures whatever, on a computer that doesn't even go online (more secure for personal privacy anyhow). then if you suspect there's anything wrong with your security, on a machine that does go online, a reinstalll is relatively easy and painless.

---

### Post by SavageWolf on 2011-08-18
EVERYBODY CALM DOWN!

It is very unlikely that this is a virus. Ubuntu and Launchpad are closely linked together, this is most likely a bug with the launchpad programs that are installed on the client by default. Also, launchpad was created and is managed by the same team as Ubuntu, I think.

> The one thing I'm really sure about, is that my system's settings were hacked and damaged.
What specifically was attacked?

Just a wild stab in the dark, but are you using Wubi?

---

### Post by scruffyeagle on 2011-08-19
> **eveg said:**
> i seriously doubt your problem is launchpad. you said you checked the security certificate and it was wrong? you do realize that if so that means the site you were at wasn't launchpad, rather a phishing site posing as launchpad? if that actually happened, you may want to mention it in security discussions here.
 
you need to ask yourself what you did that exposed you to a phishing site.<snipped>


Thank you, eveg. The contention that it was a phishing site is an excellent explanation for the discrepancies during my visit at what I thought was Launchpad.

As for what I did wrong, well, I'm fairly sure I can answer that: Being brand new to Ubuntu, I hadn't learned enough yet to make use of the security features, and as a result I didn't have a firewall active.

I don't know exactly what was done to my system, but given the two preceding items I'm fairly sure I should conclude that I was hacked and damaged by some 3rd party defective. I'd thought that visiting Launchpad was a relatively safe place to go - but, the idea that some distorted, warped charicature of a person with a grudge against Launchpad might victimize this person they'd never met by a phishing attack didn't even occur to me. Now that you suggest it as an explanation, I can see that it fits like a glove. Thank you again. Having a solid explanation that absolves Launchpad really evaporates my worries about that site, and changes my mind about being involved there. I'm going to mark this thread as "solved".

Just so you know, I didn't click on any links here at the forum beforehand. I'd been at Launchpad and read a huge number of their information pages about the bug reporting groups and procedures. The phishing site got its hooks into me when I clicked on one of the Launchpad site's links for becoming a member.

---

