---
title: "startup programs list"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by nicnok on 2011-01-26
This is closely related to 1514711, but far more basic.
I am trying to slim down to optimise running speed. 
I want to start by trimming out all heavy use software that boots on startup. I have made a start by disabling "Bluetooth Manager" for example [don't have one] through System>Preferences > Startup Applications. System>Preferences > Startup Applications lists [presumably] all of them [23 in my case] but doesn't give me sufficient information in plain English to decide what they do [ie can I do without them] or the memory cost they incur. Has anyone made such a list?

I realise the list of potential programs is vast so what I probably need is a list of 'vitals'. I can see it must include stuff to get GNOME running for example. Perhaps another approach would be to list all the heavy memory users and decide it they're worth the cost. For example, I don't know what "Policykit Authentication Agent" or "Remote Desktop" do, how important they are or if they use memory once loaded.

OK, I could have spent this time googling the 23 applications, but would I have got beyond 1 or 2? or understood the articles at my state of knowledge?

---

### Post by gordintoronto on 2011-01-26
The only people who need remote desktop are people who know what it is -- but that's not a good general rule.

It would help if you said what version you are running.

You could turn off Update Notifier if you use Synaptic to check for updates fairly frequently, like maybe once a week.

You might not have iBus on your system. If you are unilingual, you could turn it off. My list has 27 entries, with 13 enabled. I don't have one called Policykit. Do you log onto a Windows domain?

---

### Post by nicnok on 2011-01-27
Thanks for responding, I'm on 9.10 [sorry, new to these forums, thought the version showed up on the side screen].
I find Update notifier useful, so for me that stays, but the other part of my Q kicks in - if having it running uses lots of memory it is something I could close off.
Sorry, I miscounted: I have 22 of 24 applications enabled. [seemed a lot, hence the Q!]

Now for the depth-of-ignorance bit:
How would I find out whether I had iBus on the system? [I occasionally work in Greek script.]
I log on to our ISP - but lots of websites I visit are likely to be running Windows?? [have I misunderstood?]
At the heart of this Q is memory useage - ie if its tiny it might as well stay.

---

### Post by nicnok on 2011-01-27
Oops - found [in Ubuntu Software Centre] that I have "iBus Preferences" installed & it is "used by 2 pieces of installed software", so removing it = bad idea? BUT there is no program with iBus in the title on the list in Startup Preferences.
I presume that means it boots on demand on this pc. >> If that boots on demand won't many of the others  listed in Startup Preferences do the same? >> so why have them booting at startup?

---

### Post by JKyleOKC on 2011-01-27
If you post a screenshot of your startup applications list that will help us make suggestions.

The "PolicyKit" item is one you need to keep if you ever want to make changes to your system files. It's what gives you the popup message that asks for your password, and if you disable it from the startup, the "unlock" button on many configuration programs will simply quit working! I just went that route last week and it was extremely puzzling for quite a while...

---

### Post by nicnok on 2011-01-27
Just spent 20 mins trying to find out how to take a screenshot of Startup Applications Preferences, but can't find it in Help, neither will it copy so I can't paste into this reply - Help please! [am I looking in the right help I wonder?]

---

### Post by JKyleOKC on 2011-01-27
Look at [http://ubuntuforums.org/showthread.php?p=8920811&highlight=screenshot#post8920811](http://ubuntuforums.org/showthread.php?p=8920811&highlight=screenshot#post8920811) and item 7 of the list tells how. I use Xubuntu rather than Ubuntu (same basic system but different window manager) so had to do some looking myself to find the instructions for you...

---

### Post by col48 on 2011-01-27
'Print Screen' records the whole screen
Alt+'Print Screen' records the current window (I guess the one where the cursor is]

Print Screen is typically the button to the right of F12

---

### Post by nicnok on 2011-01-27
[IMG]http://ubuntuforums.org/home/nicnoks/Screenshot-Startup%20Applications%20Preferences1.png[/IMG][IMG]http://ubuntuforums.org/home/nicnoks/Screenshot-Startup%20Applications%20Preferences2.png[/IMG]

Thanks for the screenshot advice. Here [I hope] they are [too big for one]. I've attached them through "advanced> Insert Image". [copy & paste didn't work]

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by JKyleOKC on 2011-01-27
Interesting...

I get Email notifications of new messages in threads to which I'm subscribed, including this one (subscription is automatic for all participants in the thread, and optional for lurkers). In the notification of the previous message, both images were listed but when I attempted to click on the addresses shown, to view them without actually coming into the forum to do so, all I got was the forum entry page!

So I came into the forum, and now the message shows only one address -- and it's a "file:///" address instead of "http://" which means that it's for a file local to my system, which of course doesn't exist.

I've not tried to attach files, myself, so can't be a lot of help getting it to post so everyone can view the images. I'll attach my own such screen shot to see if it goes through okay, and if it does I can then give you step-by-step instructions on getting yours into the thread.

EDIT: Okay, it went through. Note that your list will look different because I have a different window manager than you, but here's what I did:

1. Capture the image with alt-PrntScrn key and save it as "screenshot.png" in my home directory.

2. Return to this message reply screen, scroll down the page to "Manage attachments" button, and click it.

3. On the resulting window, click the topmost "Browse" button and locate the image file in my home directory, then click the "Open" button and then "Upload."

I suspect that this is also what you did, and have no idea why it didn't work!

---

### Post by nicnok on 2011-01-28
Ahha... Well, I replied using 'Quick Reply'. I could find no 'attach' option so tried to attach by using "Insert Image" in the menu bar. - obviously the wrong option.
This is sent using the grey 'Reply' button [bottom left] and as you say an option to 'manage attachments' is available way down under 'Additional Options' Here goes:... simple, hope it works!

---

### Post by JKyleOKC on 2011-01-28
It did!

The "Check for new hardware drivers" can be unchecked, as can the "Remote Desktop Server" if you do not need to access the machine from another system. The various power management entries should be left alone on a laptop, but can be unchecked on a desktop system if you don't care about the screensaver working. Check for updates could be unchecked without harm to the system but I prefer to leave it checked so that I get immediate notification of security updates.

Those items with "GNOME" in their name aren't familiar to me since my window manager (XFCE) doesn't automatically load them; someone else will have to offer advice about those.

Hope this helps!

---

### Post by nicnok on 2011-01-29
Thanks, that's useful.

---

