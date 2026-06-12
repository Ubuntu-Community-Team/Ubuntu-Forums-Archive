---
title: "Yahoo Email Access w/ Thunderbird"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by ayelan on 2009-05-10
I am somewhat new to Ubuntu. I am attempting to setup my yahoo email account in Thunderbird on a Ubuntu 9.04 platform, and all of the web forums I have read, they stated that I need to install YPOPS in order to get yahoo mail thru Thunderbird. Is this true? If so, how do you edit a source list file?

Directions from site:
[COLOR=Black][B][I]First you need to add the following line to source list file by editing the /etc/apt/sources.list file

[/I][/B][/COLOR] [COLOR=Black]***$sudo gedit /etc/apt/sources.list***[/COLOR]

 [COLOR=Black]***Add the following line***[/COLOR]
 [COLOR=Black][B][I]deb [http://tskariah.000webhost.com/ubuntu](http://tskariah.000webhost.com/ubuntu) ubuntu main

[/I][/B][/COLOR]
[COLOR=Black]***Save and exit the file***[/COLOR]
 [COLOR=Black]***Add the PGP public key for the new repository***[/COLOR]

 [COLOR=Black]***$ wget [http://tskariah.000webhost.com/t_skariah.asc.gpg](http://tskariah.000webhost.com/t_skariah.asc.gpg)***[/COLOR]
 [COLOR=Black]***$ sudo apt-key add t_skariah.gpg***[/COLOR]

 [COLOR=Black]***Update the source list***[/COLOR]
 [COLOR=Black]***$ sudo apt-get update***[/COLOR]

I also attempted to add the following line : (*deb [http://tskariah.000webhost.com/ubuntu](http://tskariah.000webhost.com/ubuntu) ubuntu main) through systems sources --> Third Party -->* Add File.  That didn't work either.

---

### Post by MontelEdwards on 2009-05-10
1. that source is bad
2. GPG is bad,

---

### Post by Didius Falco on 2009-05-10
Welcome!!

Yahoo account settings:

[http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-14.html](http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-14.html)

These should work just fine in Thunderbird.

Regards,

Didius

---

### Post by sena-sena on 2009-05-21
ayelan: I've been trying to do the same thing, and using that method it just keeps saying connection refused.

Didius: that's fine if you've got yahoo mail plus, which I don't think ayelan's got. I haven't got ymail!plus but tried following those instructions anyway and said that my account couldn't connect.

Montel: could you recommend something better/somewhere better? As every tutorial I've come across relating to ymail in thunderbird says ypops is required and all link to the same website to get it from

---

### Post by ayelan on 2009-05-21
sena-sena, you are correct.. I don't have ymail plus. And I got the same error message when attempting to connect. "Your Account Could Not be Connect :(." Any more idea on how to get it to work.

---

### Post by spcwingo on 2009-05-21
I used to use ypops as you described, but I finally got fed up with Yahoo server changes breaking it all the time.  Ypops is great when it works, but it seems that the port maintainer hasn't updated since 0.9.5.9.  So, if I were you I would transfer everything to a gmail account if at all possible or if not pay <cringe> for pop access.

---

### Post by t0p on 2009-05-22
Okay, I've got some "good" news and some bad news:

The "good" news is that there are working instructions for how to install Ypops! on Ubuntu [here]("http://www.geocities.com/t_skariah/ypops/").  :)

The bad news is that I can't get Ypops! to work on my machine (running Hardy). :(  But just cos I can't do it, doesn't mean that no one can.  Please, if anyone *can* get Ypops! to work, please post instructions.

Other news is concerning **fetchyahoo**.  There's a new version out (fetchyahoo-2.13.4), which you can get from [here]("http://fetchyahoo.twizzler.org/").  I ran it, using my free uk yahoo accounts (xxx@yahoo.co.uk).  It logged in okay, but failed to download the mail.  I've sent the error output to the developer Ravi Ramkissoon.  Maybe I'll get it to work yet.  If anyone has more success, please post here.

---

### Post by HarshReality on 2009-05-24
Id be tickled to death if somebody who knew what they were doing could pick up the torch on this and hang a 64 bit deb somewhere...

---

### Post by jrz on 2009-05-29
I used ypops with windows, but found fetchyahoo to work very nicely under Ubuntu.
It's available in Synaptic, but due to Yahoo making changes frequently requiring changes to fetchyahoo (as well as ypops) I find it more reasonable to go to the D/L site and retrieve the program there, and subscribe to the change notification at the same time to be notified when changes have been made. I run the program from my home directory, scheduled under cron, and retrieve the mail finally with evolution.

---

### Post by philinux on 2009-05-29
> **Didius Falco said:**
> Welcome!!

Yahoo account settings:

[http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-14.html](http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-14.html)

These should work just fine in Thunderbird.

Regards,

Didius

Tried that and no joy. No errors messages though.

---

### Post by philinux on 2009-06-01
Anyone else got this working?

---

### Post by jrz on 2009-06-01
I assume you need free access to non paid yahoo account?
As best I can tell such access requires using something like Ypops or fetchyahoo, and fairly frequent updating of either program to keep up with yahoo changes. I'm not familiar with Thunderbird, but feel it likely has similar features to Evolution, which I use for free access to my yahoo email. In WinXP I used ypops, but found fetchyahoo much easier to work with in Ubuntu. Even so, it requires a little extra effort, but not too complicated. First off fetchyahoo retrieves the email to mbox, and must either be run manually or added to crontab for scheduled execution. Then to move the email to Evolution or I'm guessing, Thunderbird, I use the receive option "Local Delivery" which then moves the mail from the mbox to Evolution when it retrieves my other email accounts directly.

---

