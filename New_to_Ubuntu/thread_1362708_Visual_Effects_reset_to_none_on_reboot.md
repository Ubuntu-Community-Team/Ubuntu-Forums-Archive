---
title: "Visual Effects reset to none on reboot?"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by ptviperz on 2009-12-23
For some reason my visual effects keep getting reset every time I reboot. Never had this problem in Jaunty....only since the (clean) upgrade to karmic. 

Because of this I get error messages like these

"Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager."

Until I manually turn the effects back on. 

Anyone else had a problem like this? Is there any possibility I accidentally turned off something in rcconf?

---

### Post by ScottinSoCal on 2009-12-23
I've had this problem since I installed KDE to give it a try. Every time I go back into Gnome, compiz is shut off. I'm getting ready to remove KDE, and hope that solves the problem. If not, I'll wipe and reinstall 9.10, then restore my files.

---

### Post by ptviperz on 2009-12-23
I realized I'd shut off 'bluetooth' using rcconf because I never use the bluetooth function, apparently this has some kind of effect on other basic functionality. :confused:

I readded it to the rc.d and rebooted and voila

---

### Post by pizza-is-good on 2009-12-23
Do you have compiz installed?

I might be able to help you if I have more info....

---

### Post by EricDrijv on 2009-12-23
I had the same problem with compiz not saving my settings.
Until I discovered that my NVidea driver was not yet activated.
Now everything works

---

### Post by VastOne on 2009-12-29
> **pizza-is-good said:**
> Do you have compiz installed?

I might be able to help you if I have more info....

He never answered but I will.

I have compiz enabled and have used it for over 2 years and know its ins and outs

There has been some kind of update outside of Compiz and the nVidia drivers that has cause this to happen to several users here on the 4 or 5 threads I have found related to it.

Simply put, everything is fine until a reboot and then Visual Effects are disabled and need to be re-enabled. I then have to go back into compiz and reset my config so it appears compiz is at least related

I do use Emerald replace and AWN

If u need any more info let me know

---

### Post by ptviperz on 2009-12-29
Sorry I didn't reply before, my issue was (I believe) hardware related. Replaced the disk and reinstalled....everything is fine now.

---

### Post by VastOne on 2009-12-29
> **ptviperz said:**
> Sorry I didn't reply before, my issue was (I believe) hardware related. Replaced the disk and reinstalled....everything is fine now.

No problem. Glad you got yours fixed but I am still with the same issues

---

### Post by ScottinSoCal on 2009-12-29
On my system, removing KDE fixed the problem.

---

### Post by VastOne on 2009-12-29
> **ScottinSoCal said:**
> On my system, removing KDE fixed the problem.

Did you recently do this? And were you having the same issue recently?

Thanks

---

### Post by EricDrijv on 2009-12-29
In some cases it works to change the backend of the Compiz Settings Manager -> Preferences to Flat-file Configuration Backend.

---

### Post by VastOne on 2009-12-29
> **EricDrijv said:**
> In some cases it works to change the backend of the Compiz Settings Manager -> Preferences to Flat-file Configuration Backend.

OK, I will give this a try a bit later and report back

Thanks

---

### Post by VastOne on 2009-12-29
> **EricDrijv said:**
> In some cases it works to change the backend of the Compiz Settings Manager -> Preferences to Flat-file Configuration Backend.

Tried this and still having the same results.  It's as if the recommended 185 drivers are not actually activating even though it says it is.  When I go to Hardware Drivers or to enable Visual Effects, it takes it a full 45 seconds of "finding" the driver.

---

### Post by VastOne on 2009-12-29
> **ScottinSoCal said:**
> On my system, removing KDE fixed the problem.

I have never had KDE so therefore there is nothing to remove.

Thanks though :)

---

### Post by EricDrijv on 2009-12-29
Can it be that your graphics driver is blacklisted?
Some drivers do not work well with compiz so some are blacklisted
[http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)

or maybe you can find some answers in this thread?
[http://ubuntuforums.org/showthread.php?t=1109007](http://ubuntuforums.org/showthread.php?t=1109007)

---

### Post by VastOne on 2009-12-29
> **EricDrijv said:**
> Can it be that your graphics driver is blacklisted?
Some drivers do not work well with compiz so some are blacklisted
[http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)

or maybe you can find some answers in this thread?
[http://ubuntuforums.org/showthread.php?t=1109007](http://ubuntuforums.org/showthread.php?t=1109007)

Definitely not blacklisted as I have it in 4 other machines and have never had an issue and only on this one which is weird. And pure nVidia here

I have seen this issue in the past as a one and done deal after an update but not to this extent

As far as the other thread, that all indicates that Compiz is loading and then errors out. I never get that far. Compiz never loads until I go in and tell Visual Effects to enable again.  And if I am seeing this right, the restricted drivers (nVidia 185 recommended) are not really loading even though they say they are...

Thanks

---

### Post by VastOne on 2009-12-30
This is getting even stranger that I now do not even need to reboot and Compiz and Visual Effects are resetting themselves.

---

### Post by EricDrijv on 2009-12-30
> **VastOne said:**
> This is getting even stranger that I now do not even need to reboot and Compiz and Visual Effects are resetting themselves.

I think that you can try to remove the video card and dust it before sticking it back in. If compiz just does this while your computer is on, then maybe there is a contact a littile dusty?

---

### Post by VastOne on 2009-12-31
Reseating and change of the card to a new port and a change to the latest stable nVidia still with the same issue

Changing slots and cards pretty much eliminates a particle of dust theory and changing the nVidia driver speaks for itself.

Does anyone know where I can check a log to tell me when and what updates happened to try and trace this backwards?


Thanks

---

### Post by EricDrijv on 2009-12-31
I am lost too. I can't give you more advice, sorry about that. This is becoming a very interesting thread. I tried searching in Google for "compiz  breaks" this gives me lots of possibilities to try out. I will follow this thread, because I also want to know the answer!
Good luck with your quest!
Anyone?.....

---

### Post by VastOne on 2009-12-31
> **EricDrijv said:**
> I am lost too. I can't give you more advice, sorry about that. This is becoming a very interesting thread. I tried searching in Google for "compiz  breaks" this gives me lots of possibilities to try out. I will follow this thread, because I also want to know the answer!
Good luck with your quest!
Anyone?.....

I have googled it to death and back .. sounds like this happens about every blue moon.

It is also on 4 other current threads here now...

A new update of some kind will come along and make me forget all about it...I just do not like unresolved little ones like this...It makes the problem solver in me cringe

---

### Post by ScottinSoCal on 2009-12-31
> **VastOne said:**
> Did you recently do this? And were you having the same issue recently?

Thanks

Sorry, didn't see this question.

Yes, it was recently. I installed KDE to check out the interface, decided I preferred Gnome, but then found that my Compiz settings were gone every time I booted - not on restore from suspend (this is on a notebook), only on boot. I removed KDE and the problem went away. Compiz once again remembers my settings.

---

### Post by VastOne on 2009-12-31
> **ScottinSoCal said:**
> Sorry, didn't see this question.

Yes, it was recently. I installed KDE to check out the interface, decided I preferred Gnome, but then found that my Compiz settings were gone every time I booted - not on restore from suspend (this is on a notebook), only on boot. I removed KDE and the problem went away. Compiz once again remembers my settings.

Thanks...

I have nothing of KDE installed and never have had.

---

### Post by VastOne on 2010-01-08
Bump

Same issue for me, I have everything setup in Compiz and Visual Effects are enabled and all my tweaks to Compiz are set and I am happy....Until I reboot and find no Visual Effects enabled and I have to go back to Compiz and reconfigure it after I do.

This is on every reboot

Any one with any insight to this?

---

### Post by gundogar on 2010-03-06
I have the same issue and do not have a solution for the issue but you should try 

system->preferences-> appearance->visual effects->custom 

instead of going compiz all the time. At least it works for me. Now all I need is setting this in command line for the permanent workaround  but I have no idea how to do it.

---

### Post by Dan_Dranath999 on 2010-04-16
I installed Karmic a few weeks ago, the compiz settings reset often (not on every reboot but close)

---

### Post by rudihawk on 2010-04-18
I'm having this same problem! I can't find a way to fix it!

---

### Post by rudihawk on 2010-04-18
> **ptviperz said:**
> I realized I'd shut off 'bluetooth' using rcconf because I never use the bluetooth function, apparently this has some kind of effect on other basic functionality. :confused:

I readded it to the rc.d and rebooted and voila

+1

I was having the same issue, just renabled the bluetooth at startup(which I had disabled), restarted the x server and logged back in -> effects were running like they should be, rebooted the pc, again effects working as they should be. This is a really wierd bug. 

But thats how I got it fixed.

---

### Post by DWally on 2010-05-04
I had lots of problems on my Acer Aspire (GeForce 9400M) resetting to no visual effects on reboot. Very annoying! Finally figured it out. Go to System-> Preferences -> Startup Applications, click on Add button, and add "compiz" under command line and hit save. Back out, reboot and check. Once I did this, my machine boots up with visual effects enabled, no problems from then on. Hope this helps.....

---

### Post by amendt on 2010-05-04
Thanks Dwally, that worked! I couldn't find startup applications in my remix desktop so I went to Accessories > Terminal and typed in **gnome-session-properties** then followed your instructions.  Amazing.

---

### Post by mustard greens on 2010-05-17
I hate to say it but re-enabling bluetooth on start up worked for me.  any ideas why?

---

### Post by mustard greens on 2010-05-17
the bluetooth workaround was doing the trick, but then someone recommended a remove then reinstall of compiz which seems to have also dome the trick.  no more need to have bluetooth eneabled as a start up app.  visual effects are sticking.

---

### Post by Didymus7777 on 2010-05-18
You are the bomb, I just upgraded to the Lucid Lynx and was having this issue.  I can not thank you enough for taking the time to post this.

---

### Post by maiaymistru on 2010-05-31
Yes thanks for the thread. High effects worked as a charm for the last couple of weeks, and then all of a sudden it was reset to none after each boot. I updated video drivers et al, nothing seemed to make any difference.

But when I set compiz to autostart, as mentioned above, that worked for me.

---

### Post by fresta on 2010-08-20
For me clicking "Remember Currently Running Applications" in System:Preferences:Startup applications solved the issue.

---

### Post by rchiossi on 2011-01-25
> **DWally said:**
> I had lots of problems on my Acer Aspire (GeForce 9400M) resetting to no visual effects on reboot. Very annoying! Finally figured it out. Go to System-> Preferences -> Startup Applications, click on Add button, and add "compiz" under command line and hit save. Back out, reboot and check. Once I did this, my machine boots up with visual effects enabled, no problems from then on. Hope this helps.....

Wow man, thanks! This did the trick for me! =)

---

