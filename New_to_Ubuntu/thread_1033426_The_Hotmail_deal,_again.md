---
title: "The Hotmail deal, again"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Circuit Rider on 2009-01-07
I know the Hotmail deal has been discussed previously and marked [SOLVED] but in my case it remains unsolved, and I need to add Facebook to the issue list.

Hotmail does not work when you approach it with a fully updated Ubuntu machine. It is established that MS changed Hotmail recently and sniffers are unfriendly to Ubuntu. All previously suggested fixes involving useragent adjustments, etc., have not worked. Hotmail won't download to Email apps. Can't get it to work. Facebook is the same way. 

I am trying to change from Windows XP to Ubuntu, but members of my household addicted to their Hotmail and Facebook are growing more restless and impatient by the day.

Here's what I have noticed that has not been addressed: I downloaded Intrepid in October when it was released and installed it on a machine I built at Christmas. When it was first installed these websites WORKED. When the system downloaded updates in Ubuntu and Firefox they no longer worked.

As a test I booted the computer with the CD (sans updates), and  Hotmail and Facebook WORKED. Boot again from the installed, updated program and they don't work. 

Same is true on my laptop. When I installed Hardy last fall everything worked perfectly. After it picked up updates they didn't.

I know MS is partly to blame, but I have the feeling something has changed with updates in Ubuntu. But being a newbie I have no way of knowing what or how to remove the offending file.

I have seen no discussion on this and would covet comment from experienced folks. I really don't want to return to Windows but may be forced to just to keep peace. HELP!

---

### Post by Raynman37 on 2009-01-07
You say you've been having problems with Facebook too?  It sounds like we are pretty much in the same place as far as the OS goes (8.10) and I have not noticed any problems with Facebook (I check a few times a day).

If you have a lot of bookmarks, I would back your bookmarks up somewhere safe and reinstall Firefox.  It seems like it may just be something happend in the install of the updates that did this, seeing as this sounds like a pretty isolated incident.  Did you do anything else besides update in the time between it working and not working?

EDIT: I'll look at hotmail tonight.  I'm on my Windoze work pc.

EDIT 2: Can you post a link to the previous hotmail thread so I don't tell you to do things you already did? Thanks!

---

### Post by gettinoriginal on 2009-01-07
you will have to edit this for your browser, but it worked for me:  :P
[http://wvarner.blogspot.com/2008/11/windows-live-mail-hotmail-stopped.html](http://wvarner.blogspot.com/2008/11/windows-live-mail-hotmail-stopped.html)

---

### Post by Raynman37 on 2009-01-07
Yeah, I just found something similar:

> 
 Tetsuo__Shima wrote on 2008-11-17: (permalink)

Hello!

I had this problem with hotmail and after searching some forums I was able to fix it.
+++++ Hotmail recognizes Firefox now. +++++++

You have to do the following in Firefox.

In the adress bar type: About:config

Accept the terms.

Then search for: USERAGENT
In the list that appears search for:

general.useragent.vendor predetermined Chain Ubuntu

Change the word: Ubuntu for: Firefox
It should read:

general.useragent.vendor predetermined Chain Firefox

and to save you close the tab then in file you select QUIT
This way the change is saved in Firefox 3.0.3

And works well under Ubuntu Intrepid 8.10

To verify that the change worked I rebooted the computer several times and no problem what so ever, hopefully it will work for anyone with this little problem.

In any case thank you for your time!!
Hope that you have a great weekend!!!

Tetsuo


---

### Post by Circuit Rider on 2009-01-07
I've done the useragent routine. No luck. In fact, when I boot from the CD and check useragent it discloses Ubuntu and 8.10 and it works fine. This is not the useragent causing this. It is something else.

This is happening on two machines, one with Intrepid and one with Hardy.

Funny thing, I am now on my machine at the office with an old HD plugged in (experiment) with Intrepid, not fully updated. Hotmail and Facebook working fine. Useragent reports Ubuntu.

---

### Post by Raynman37 on 2009-01-07
Did you try both my and Gettinoriginal's useragent fixes, because they are similar but different.  Gettinoriginal's may be a little more targeted for the Hotmail fix, so you may have some luck with it.

---

### Post by Circuit Rider on 2009-01-07
Thanks. I'll give it a whirl.

The deal is that useragent is identical in the unupdated CD and the updated installed program, except that there is an added "Firefox.extra" line that I cannot remove. Ubuntu shows up in both, and one works. That's why I don't really think it is a useragent issue. I think it is an update issue. I just don't know how to find and fix it.

---

### Post by Captain_tux on 2009-01-07
> **Circuit Rider said:**
> 
Hotmail does not work when you approach it with a fully updated Ubuntu machine. 



I have fully updated 8.04 machine at home and used it late last night to access both Hotmail and Facebook without any problems at all. While problems did exist for a while with Hotmail (it's owned by the kids in Redmond), I've never had a problem using Facebook. I'm guessing the problem is more with your browser than anything else.

I'd back up my bookmarks and uninstall/reinstall Firefox (if that's what you're using)... and if it isn't what you're using, you should be ;)

---

### Post by stoogiebuncho on 2009-01-07
Don't know if you've already tried this or not, but this is what fixed it for me.  It's a user-agent fix that doesn't require any editing of about:config

Install user-agent switcher and create a new entry.  Fill it out thusly:

> Description: Firefox 3.x (WinXP)
User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
App name: Mozilla Firefox
App Version: 5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
Platform: Win32
Vendor: Firefox
Vendor Sub: {leave blank}

It fixes hotmail.  I haven't had any problems with facebook yet and I can't help you there.

---

### Post by Circuit Rider on 2009-01-07
Thank you all for trying to help. I have tried ALL the useragent fixes and NONE work. I have not uninstalled and reinstalled Firefox, which I will try tonight before putting XP back on.

The problem: 
[LIST]
Boot computer from installed, updated Ubuntu: Hotmail does not work.
Boot computer from unupdated CD: Hotmail works
[/LIST]

On BOTH the useragent info is the SAME. It cannot be a useragent issue. It has to be an issue with an Ubuntu update or a Firefox update.

I have also tried Opera and all the other browsers I can download. None of them work with Hotmail, either, leading me to believe there is an Ubuntu issue. I don't know how to run that down.

Facebook is a pain anyway you go because it is so SLOW, but the girls like it.

Thanks again. We'll keep plugging.

---

### Post by LowSky on 2009-01-07
Dude I hav eno idea what you did but it sound like you messed up your firefox on both of your machines. As I'm being nice and checking all three (yes 3!) that have ubutnu. My destop (8.10) is fine, my laptop (8.04.1) fine, my older laptop (8.04 Xubuntu) Just Fine....So this issue has to be on your end not Ubuntu's!!!

I have no issue using Facebook, even the messager works perfectly from within the browser. Im using a completly up-to-date version of 8.10 

As for Hotmal - I don't use it. I use the supplied account from my ISP (Optimum Online) and a yahoo account as a back up, both work from their websites and Thunderbird(Optonline), so I can't complain. Heck fo some poop and giggle I just tried my AIM mail account and that works too... 

My suggestion is you use a more user friendly email client. Oh and reinstall Firefox!

---

### Post by Raynman37 on 2009-01-07
Are you able to have your Hotmail sent to an external email client like Thunderbird or similar?  If you do it that way, you wouldn't even have to use a browser to get to your email.

EDIT: Oh yeah, I hate new Facebook too.

---

### Post by gettinoriginal on 2009-01-07
I have Firefox 3.05 as my browser, below is a pic of my settings in "about:config" and I can recieve, write, attach, and send emails without difficulty. :P

[ATTACH]99085[/ATTACH]

---

### Post by Captain_tux on 2009-01-07
> **Captain_tux said:**
> I have fully updated 8.04 machine at home and used it late last night to access both Hotmail and Facebook without any problems at all. While problems did exist for a while with Hotmail (it's owned by the kids in Redmond), I've never had a problem using Facebook. I'm guessing the problem is more with your browser than anything else.

I'd back up my bookmarks and uninstall/reinstall Firefox (if that's what you're using)... and if it isn't what you're using, you should be ;)

Just used Hotmail & Facebook again... not a problem.

---

### Post by Circuit Rider on 2009-01-07
> **LowSky said:**
> Dude I hav eno idea what you did but it sound like you messed up your firefox on both of your machines. As I'm being nice and checking all three (yes 3!) that have ubutnu. My destop (8.10) is fine, my laptop (8.04.1) fine, my older laptop (8.04 Xubuntu) Just Fine....So this issue has to be on your end not Ubuntu's!!! ***
My suggestion is you use a more user friendly email client. Oh and reinstall Firefox!

Will uninstall and reinstall Firefox on both tonight. 

But, I have also tried Opera and all the other browsers I can download. None of them work with Hotmail, either, leading me to believe there is an Ubuntu issue. I don't know how to run that down.

Thanks a bunch.

---

### Post by Raynman37 on 2009-01-07
Instead of using Firefox/Opera/whatever to open your hotmail, just find the pop and smtp server url's and setup Thunderbird to import your hotmail.

Here are some instructions:

> Read your Hotmail with Thunderbird:
--------------------------------------
>>> In order for your Thunderbird to be able to read your Hotmail (and some other popular web-based email providers like Yahoo, Gmail, etc.) you simply need to download and install an 'extension' called 'WebMail'. It can be found at Thundebird-creator's webpage:

[http://webmail.mozdev.org/installation.h](http://webmail.mozdev.org/installation.h)...

Installation-instructions can be found at the bottom of the page mentioned above. Further settings for your accounts (like Account Setup, Server Settings, etc.) can be found at the menu on the left.

More instructions:

[http://www.ubuntu-unleashed.com/2008/01/howto-access-web-based-email-through.html](http://www.ubuntu-unleashed.com/2008/01/howto-access-web-based-email-through.html)

EDIT: This may work too:

[http://www.scribd.com/doc/128984/howtothunderbirdhotmail-v2](http://www.scribd.com/doc/128984/howtothunderbirdhotmail-v2)


What I've been reading though is not very comforting.  It seems that some people are able to get away with using the pop3 service from hotmail because they've had their accounts for a long time, but the newer ones, you have to pay for.  Not being a hotmail user (you should really switch to gmail, it's fantastic) though, I'm not sure.  EDIT: This seems to be because of this new "Live" thing that they have.

I would still try to reinstall Firefox or make the switch do a different email provider(ps- you can still use windows live messenger with a gmail account...I do!).  Other than that, it may not even be a problem on the Ubuntu side of things, but a problem on the Hotmail side.

---

### Post by Kosimo on 2009-01-07
I don't know what happens to you guys but I can easily access my "old" hotmail inbox without any isse, and also using facebook almost every day.

---

### Post by dccrens on 2009-01-07
I have had my hotmail account forever and have never been able to get "web browsers" to pop the mail reliably. I have been using "freepops" with kontact/kmail and it works great. Freepops also has an updater so when MS changes hotmail they update freepops to work.

---

### Post by Circuit Rider on 2009-01-07
Well I am working from the machine in question. I uninstalled and then reinstalled Firefox and that did not solve the problem. I then wiped the disk and totally reinstalled the system.

Of course the useragent reports Ubuntu 8.10 and it works like a charm.

I can get into both Hotmail and Facebook. Now the system wants to download 210 updates, among them a couple of Firefox updates. I am afraid to install them because I don't want the problem again.

Anyway, we can work with it for now.

Thanks for all comments.

---

### Post by Raynman37 on 2009-01-07
Well I would at least install the non-Firefox updates at this point.  Don't want to leave your system vulerable and un-updated.

I am going to say, I think it's a problem with your install/system in particular and not with Ubuntu as a whole or with the Hotmail site, seeing as I just logged in and navigated the whole Windows Live area with no problem.

Sorry we couldn't figure out why it's doing this to you!

---

### Post by Circuit Rider on 2009-01-14
Interesting thing happened. The laptop, which was unable to access Hotmail, can now go there after downloading updates yesterday. Apparently there was a fix of some kind.

I am still afraid to update the home computer for fear of screwing something up.

Anyway, thought it was interesting to note.

---

