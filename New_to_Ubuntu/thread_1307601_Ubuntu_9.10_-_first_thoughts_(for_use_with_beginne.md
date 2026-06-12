---
title: "Ubuntu 9.10 - first thoughts (for use with beginners)"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by drseuk on 2009-10-31
Hi,

Just a few first 9.10 impressions (especially as I believe they apply to beginners).

Firstly, it's highly unusual (in fact unique) for me to be so critical of an Ubuntu release having been an avid Ubuntu user since 5.10 (IIRC) (just so you all know I'm not trolling! :-) ).

The double boot logo sequence is IMHO a step back from 9.04 which had a very nice "KITT-style" progress bar.

The default theme is too dark and brooding - and highly inaccessible. The orange / yellow look of previous (Edu)buntus took a bit of getting used to years ago, but at least it was bright and clear. (Yes I know, change it - but beginners will tend to stick with the default). Specifically the WiFi indicator is now barely legible, the volume control icon looks similarly weird as well as the shutdown menu icons.

Pidgin seems more intuitive and friendly compared to Empathy (yeah, I know install Pidgin - but, again, beginners will tend to use what's installed by default). One especially annoying fact is that Empathy demands a password keyring be created (You don't have to with Pidgin) - this is arguably a bug.

On the positive side, performance is noticably improved - boot time on an Acer Aspire One is less than 20 seconds and shutdown time is so fast you might miss it if you blink! (less than 3 seconds).

The install was absolutely seamless and everything "just works" for all the machines I've tried it out on so far (this has been true for me since at least 7.04).

Anyway, I've just put a fresh install of 9.10 onto the above machine for a friend who's never used Ubuntu before (or even heard of it). As an experiment, I'm just going to give it back to her and leave her to it to see how she gets on. If any interesting results occur, I'll post back here.

---

### Post by humphreybc on 2009-10-31
Thanks for your feedback. Good to see you're enjoying the Koala on the whole :)

> **drseuk said:**
> Pidgin seems more intuitive and friendly compared to Empathy (yeah, I know install Pidgin - but, again, beginners will tend to use what's installed by default). One especially annoying fact is that Empathy demands a password keyring be created (You don't have to with Pidgin) - this is arguably a bug.

Just as a side note, Pidgin does not encrypt passwords (they're stored in clear text in a file somewhere), whereas Empathy does - hence why it requires access to the keyring. Also, Empathy supports video/voice chat, whereas Pidgin does not - one of the reasons it was chosen as the default IM client.

> 
On the positive side, performance is noticably improved - boot time on an _Acer Aspire One_ is less than 20 seconds and shutdown time is so fast you might miss it if you blink! (less than 3 seconds).

The install was absolutely seamless and everything "just works" for all the machines I've tried it out on so far (this has been true for me since at least 7.04).


I see you're on an Acer Aspire One, do you think you could help diagnose the problems being had by [this user?]("http://ubuntuforums.org/showthread.php?t=1307594")

Cheers!

---

### Post by enoughsaid05 on 2009-10-31
Let me put in some few cents worth of my thoughts about this new distribution as well...

I have been using ubuntu for past 2 years and though there has been a trend of improving over several distributions, this distro seems to be a little bit of disappointment for me.

After upgrading my system, my wireless can't work. I have to spend some time trying to figure out and realise that in the previous distro I have enabled proprietary drivers. So after the upgrade, my system seems to have forgotten about it and so it didn't activate any drivers for my wireless. I thought the upgrade had screwed up my system, and was tempted to reinstall the whole system when my friend, a long time linux user, told me that there is absolutely no need to do that unless I really screw up really big time. This problem is nothing.

So after searching the internet for answers, luckily I found one on first try. I removed the blacklist off from the modprod folder under etc and it worked.

There are some applets that are missing from the gnome setup. Also, I can't seem to disable the surround sound so that I can use my earpiece to listen to music without having to disturb other people.

I think there is still a lot of work to do. Nonetheless, all these ordeals have taught me to be calm during times of distress, and to think on my feet to come up with fixes for my system. On the whole I definitely learn much more than I would have had I been a Windows or a Mac user. (Perhaps that's a price to pay for using a free software!)

Overall, I would still rate this OS highly. There are people who are constantly worrying over the OS and coming up with the fixes, which is good since it shows that people still do care for ubuntu.

However, I wish the changes between the distribution wouldn't be so great. Perhaps I may consider Debian in future (definitely not now since things are working fine under ubuntu)

---

### Post by humphreybc on 2009-10-31
> **enoughsaid05 said:**
> There are some applets that are missing from the gnome setup. Also, I can't seem to disable the surround sound so that I can use my earpiece to listen to music without having to disturb other people.

What applets are missing? Some applets (such as "Volume Control") have been merged with current ones, in this case, Notification Area.

Have you tried right clicking on the volume icon, choosing Sound Preferences and changing your Output device?

---

### Post by enoughsaid05 on 2009-10-31
Hi there

I didn't know that. What about the "help" applet? 

I did as what you have suggested, I changed the output to analog headphones but no sound came out.

Do you have any other suggestions? Or have I not done things correctly?

Many thanks for the suggestion!

---

### Post by drseuk on 2009-10-31
Cheers.

I had read the reason for the change to Empathy in the new features bit or somewhere some-such! It's partly my own modus operandi of always carrying a Live Ubuntu image on some media for use on any machine I need to use when out and about or at "work". (When the Live Ubuntu boot is witnessed by MS Windows end-users needing support it usually results in the kind of Gollum "But you've destroyed the precious" look before they're amazed that "their precious" comes back better after all its malware and virii have been removed :D ).

I'll see you in the other thread in a minute to help out our fellow Acer Aspire One end-user.

---

### Post by 3rdalbum on 2009-10-31
The wifi indicator sometimes looks completely illegable - I agree on that.

I don't use Empathy or Pidgin.

The new Xsplash doesn't look good enough (the other proposed designs were much nicer), and the transition between Usplash and Xsplash is not smooth (the Usplash and Xsplash should be similar enough that you can't tell for sure where one ends and the other begins).

---

### Post by Norm24 on 2009-10-31
9.10 is a huge improvement in my case.This is the very first release that has sucessfully suspended/hibernated on any of my laptops.

---

### Post by NCLI on 2009-10-31
> **enoughsaid05 said:**
> Let me put in some few cents worth of my thoughts about this new distribution as well...

I have been using ubuntu for past 2 years and though there has been a trend of improving over several distributions, this distro seems to be a little bit of disappointment for me.

After upgrading my system, my wireless can't work. I have to spend some time trying to figure out and realise that in the previous distro I have enabled proprietary drivers. So after the upgrade, my system seems to have forgotten about it and so it didn't activate any drivers for my wireless. I thought the upgrade had screwed up my system, and was tempted to reinstall the whole system when my friend, a long time linux user, told me that there is absolutely no need to do that unless I really screw up really big time. This problem is nothing.

So after searching the internet for answers, luckily I found one on first try. I removed the blacklist off from the modprod folder under etc and it worked.

There are some applets that are missing from the gnome setup. Also, I can't seem to disable the surround sound so that I can use my earpiece to listen to music without having to disturb other people.

I think there is still a lot of work to do. Nonetheless, all these ordeals have taught me to be calm during times of distress, and to think on my feet to come up with fixes for my system. On the whole I definitely learn much more than I would have had I been a Windows or a Mac user. (Perhaps that's a price to pay for using a free software!)

Overall, I would still rate this OS highly. There are people who are constantly worrying over the OS and coming up with the fixes, which is good since it shows that people still do care for ubuntu.

However, I wish the changes between the distribution wouldn't be so great. Perhaps I may consider Debian in future (definitely not now since things are working fine under ubuntu)
If you want a very stable operating system, I'd recommend just install the LTS versions and updating to the next one every 2-3 years.

---

### Post by drseuk on 2009-10-31
Hi NCLI,

That's Fair Dinkums! We're the early-adopting whingers :-D

The same pattern of, basically, "panic" occurs every six months with each new release. We all moan about the bits we can't get to work, then we all work together on fixing / improving them - then we're all happy until the next release :-D

Glad I'm not the only one unhappy with the default theme and the USplash / XSplash.

Onwards and upwards eh!

---

### Post by inrig on 2009-10-31
I've just upgraded to 9.10, and I like most of what I've seen so far.  However I have encountered one irritant.  I occasionally want to mount my Windows XP partition, which I can easily do via "Places".  When I do this, I am asked for a password.  In 9.04, the password dialog included a "Remember authorization" checkbox, which enabled me to do subsequent mounts without having to enter the password each time.  This checkbox is not provided in 9.10.  Is there some other way to avoid having to repeatedly enter passwords?

Note: I'm new here, so please let me know if I should be posting this question elsewhere.  Thank you!

---

### Post by drseuk on 2009-10-31
Hi,

Welcome! You're fine posting such questions here (though unfortunately I don't know the answer to your question (not having been an MS Windows end-user for many, many years) , I'm sure someone else will!).

Another "gripe" with 9.10 I have is that the coloured indicator for packages marked for installation in Synaptic used to be green - now it's yellow - the same yellow as the indicator on those packages needing upgrading???

Overall 9.10's a great release and improvement on previous releases badly let down by some bizarre decisions regarding "eye candy" and theming IMHO.

---

### Post by drseuk on 2009-11-01
> **inrig said:**
> I've just upgraded to 9.10, and I like most of what I've seen so far.  However I have encountered one irritant.  I occasionally want to mount my Windows XP partition, which I can easily do via "Places".  When I do this, I am asked for a password.  In 9.04, the password dialog included a "Remember authorization" checkbox, which enabled me to do subsequent mounts without having to enter the password each time.  This checkbox is not provided in 9.10.  Is there some other way to avoid having to repeatedly enter passwords?

Note: I'm new here, so please let me know if I should be posting this question elsewhere.  Thank you!

Hi Inrig,

Since no-one's replied to your question yet, you may be better off starting a new thread within this forum with a title such as "Remembering passwords for Windows XP mounts seems broken in 9.10" - that should get their attention ;-)

---

