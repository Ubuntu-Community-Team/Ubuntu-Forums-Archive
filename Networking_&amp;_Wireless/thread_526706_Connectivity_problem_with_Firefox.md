---
title: "Connectivity problem with Firefox"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by jswhite on 2007-08-15
INITIAL DISCLAIMER:
I have already been [here]("http://kb.mozillazine.org/Error_loading_websites#Error_loading_some_websites"), done everything, and none of it fixed the problem. I have also reinstalled Firefox, deleted my profile, created new profiles, and used alternate profiles. Still nothing.

[/disclaimer]

My setup:
Alienware Area51-m laptop
Ubuntu Fiesty Fawn
Firefox 2.0.0.6

When I attempt to access certain websites, I instantly get the following message:

```

The connection was reset         

The connection to the server was reset while the page was loading.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

```

Each of the websites that I get this error on are located on the same server. They're all from the State of Idaho (I work there, for those of you who are interested). Examples:

[The Idaho Department of Corrections]("http://corrections.state.id.us/").
[Idaho State Bar]("http://www2.state.id.us/isb/").

...and pretty much every other state run website that ends in "state.id.us". This is a bit of a pain for me, since I work for the government and regularly have to access them. I get that error from all instances of Firefox on this computer, all profiles, etc. If I use a different browser, like Opera, I can access them with no trouble. I can also access them without issue from both Firefox and IE on my wife's computer and my computer at the office.

Oddly, when experimenting last night, I discovered that if I download the official Firefox Linux build, untar it to opt, then run that, I can access the websites again. I can even move my current profile over to be used by the official build and still get access, thereby apparently proving that it's not a profile issue.

Any ideas on what might be causing this and how to fix it? I would also appreciate if a couple of people using the Fiesty repos version of Firefox could click on those links and post their results, maybe even some Edgy/Gutsy users as well. Any help would be most appreciated.

---

### Post by noob12 on 2007-08-15
I'll try this from my own network when I get home.  I confirmed I am seeing the same behavior where I am now on those two links with Ubuntu Feisty + Firefox 2.0.0.6 from the repository.  I don't have the direct distribution installed.

I wonder if these sites are looking for something in the User-Agent header and rejecting if it doesn't match.

UPDATE:  tried from my home network as well.  Same result.
BTW:  Feisty and Firefox 2.0.0.6 on two different sets of hardware.

---

### Post by jswhite on 2007-08-16
I guess the good news is at least I know it's not just because I did something to screw up my box...

---

### Post by jswhite on 2007-08-17
> **noob12 said:**
> 
I wonder if these sites are looking for something in the User-Agent header and rejecting if it doesn't match.


I think you may be right. I used the User Agent Switcher extension to change it to IE on Windows XP, and suddenly the sites work right. I'll have a discussion with our tech department and see if we can get the problem fixed.

---

### Post by jswhite on 2007-08-17
Dumbest. Error. Ever.

After some experimenting, I figured out the quickie solution. The server is apparently choking on the word "feisty" in my user agent string. So, I modified "general.useragent.extra.firefoxComment" to be "(Ubuntu)" instead of "(Ubuntu-feisty)", and suddenly everything works just fine.

Yeah, I'm DEFINITELY having a talk with our IT department.

---

### Post by noob12 on 2007-08-18
Yes.  Feisty is a very threatening word.   :)

---

### Post by dannemil on 2007-08-22
I am having exactly the same problem. I note here that it also happens with Opera, so I am thinking it might have something to do with the network connection per se rather than being specific to Firefox.

---

### Post by dennis1200 on 2007-09-30
I have just recently had a similar (related?) problem in Gutsy, where many, many unrelated websites will simply not load. A few include: google.com, yahoo.com, dell.com, comics.com, atomfilms.com, msn.com (one gets desperate for a search engine), and eventually time-out. My connection is fine; I can download Ubuntu updates at full speed, and most websites work perfectly.

I booted into Windows (must be a blue moon), and Firefox (2.0.0.7) loaded all of the "problematic" websites without a hitch, leading me to believe that it is something with the Firefox in the gutsy repos (2.0.0.6).

Then I tried installing Epiphany, and the same thing occurred.

I did try to download the latest Firefox (mozilla.com works), but it complains about a missing libmozjs.so, even though it is present in /usr/lib/firefox, and I copied it to the /opt/firefox directory where I had the 2.0.0.7 version.

Any ideas?

Yes Gutsy is still in beta, but I can't figure out why something like this would happen in Ubuntu and not Windows, when it is Firefox in both.

---

### Post by EnderTheThird on 2007-10-18
> **dennis1200 said:**
> I have just recently had a similar (related?) problem in Gutsy, where many, many unrelated websites will simply not load. A few include: google.com, yahoo.com, dell.com, comics.com, atomfilms.com, msn.com (one gets desperate for a search engine), and eventually time-out. My connection is fine; I can download Ubuntu updates at full speed, and most websites work perfectly.

I booted into Windows (must be a blue moon), and Firefox (2.0.0.7) loaded all of the "problematic" websites without a hitch, leading me to believe that it is something with the Firefox in the gutsy repos (2.0.0.6).

Then I tried installing Epiphany, and the same thing occurred.

I did try to download the latest Firefox (mozilla.com works), but it complains about a missing libmozjs.so, even though it is present in /usr/lib/firefox, and I copied it to the /opt/firefox directory where I had the 2.0.0.7 version.

Any ideas?

Yes Gutsy is still in beta, but I can't figure out why something like this would happen in Ubuntu and not Windows, when it is Firefox in both.

I've been having the same problem!  Reinstalling Gutsy worked at first, but now it just started doing it again today!  I'm reinstalling one last time with the final release version (64bit) and hopefully it doesn't happen again.  It's an extremely frustrating problem because I really have no idea how to diagnose and/or fix it.  If it happens again after this install, maybe we'll see if we can get to the bottom of this bug.

---

