---
title: "Evolution Calendar alarms not working - anyone help?"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by Noo 2 Ubuntoo on 2010-06-13
Hi,
   Since upgrading from Karmic to Lucid a week ago my Evolution calendar alarms/reminders stopped working. I've tried running them the default way (Preferences/calendarsandtasks/alarms with "Display alarms in notification area only" checked) and with (gconf-editor/apps/evolution/calendar/notify/notify_with_tray) to no avail.

I usually run them with the "notification area" and "notify with tray" switched off as I like them to appear in the middle of my screen but neither is working. The appointments/alarms appear in my calendar but the alarms just don't seem to be working. I use one calendar only if that's any help.

Has anyone else had a similar experience? Does anyone know what's happened/have the solution? 

Thanks

---

### Post by Noo 2 Ubuntoo on 2010-06-14
So, in the absence of any reply and in looking further into this I have found that if I:

1.  go to System-Preferences-Startup applications and uncheck Evolution alarm notifier.

2. do a restart 

3.recheck Evolution alarm notifier

4. do another restart

5. set an alarm

6. turn off the computer and turn it on after the time for the newly set alarm has passed (i.e. the alarm has expired) the "old" alarm/reminder displays correctly.

The next time I turn the computer off and on Evolution reverts to it's behaviour of incorrectly not displaying past alarms/reminders that have not been viewed.

Can anyone advise what is causing this behaviour and the fix please? I shouldn't have to be resetting the alarm notifier and restarting the computer every time I switch off.

Thanks

---

### Post by Noo 2 Ubuntoo on 2010-06-18
Bump - anyone?

---

### Post by dasbrow on 2010-07-07
Funny, once Ubuntu was rough but reliable and there was help out there somewhere.  Now it's unreliable and there is no help.  Along with, apparently, everyone else, I'm about to abandon Linux and return to the onerous, but functional, Windows.  Ahh, but it's been a grand two or three years!!

---

### Post by Noo 2 Ubuntoo on 2010-07-07
> **dasbrow said:**
> Funny, once Ubuntu was rough but reliable and there was help out there somewhere.  Now it's unreliable and there is no help.  Along with, apparently, everyone else, I'm about to abandon Linux and return to the onerous, but functional, Windows.  Ahh, but it's been a grand two or three years!!

Yes, I agree. I found a bug relating to this on Launchpad here: [[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/147163]](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/147163]) which is now **3 YEARS OLD!!** and maturing nicely. Even then it was already known about by the developers!!! What business in it's right mind would buy this OS when it's PIM is critically flawed? If Canonical think they are going to break into the mainstream any time soon without winning over businesses they are living in cloud cuckoo land.

Un/Fortunately for Ubuntu I have the option of dual booting into my Windows partition. Guess what? I've already started doing just that! And telling MS friends about my "experiences" with Linux.

Gnome project have still got a lot of work to do with evolution if they want it taken seriously.    

Still, maybe they're happy with a 1.25% share of the market. ;)

---

### Post by philinux on 2010-07-07
Just checked on this. I get emails from mt google calender and the notification pop is working. 
This a clean instal lucid.

---

### Post by dre12b on 2010-07-19
I'm experiencing the same problem - no local alarms for google calendar events even though the calendar is synced through evolution.  Serious problem.  Would love to find a solution.

This is on what was originally a clean install of lucid, not an upgrade (but I've modified the install in many ways since).

---

### Post by Noo 2 Ubuntoo on 2010-07-20
dre12b. Your problem is different from mine. I am not using Google calendar for anything. Philinux may have misled you as s/he started talking about Google calendar, but this is not the problem. I am only using the Evolution local calendar. It sounds like yours may be a syncing problem between Google calendar and Evolution.

Oddly, my Lucid upgrade is sitting on an ext 3 file extension. I thought that Lucid was supposed to be on ext 4? That may be the problem for both of us, if yours is on ext 3 too. My next step is a manual fresh install (when I get round to it) and I'll post the results back here.

---

### Post by dre12b on 2010-07-20
I just checked and I'm not getting alarms for my personal calendar either (and my GCal syncs successfully with Evolution).

Strangely enough I have Lucid installed on a second laptop - used the same install disk on both machines - and alarms ARE working on that computer.  Both installs are on ext4 partitions, so I don't think thats the problem.

---

### Post by dre12b on 2010-07-20
After seeing [this post]("http://ubuntuforums.org/showpost.php?p=4275931&postcount=3") on an older thread, I disabled alarms for both my Personal (local only) and Gcal (Gcal synced w/ local copy) under Preferences>Alarms> then closed down and restarted evolution.  Then I enabled the alarms again for both calendars.  Now alarms notifications are appearing normally for both calendars.  I also tested having the computer totally shut off for a scheduled an alarm and then restarting.  The notification appeared after login, as it should.  

I'll keep the thread updated on whether the "fix" holds.  Noo 2 Ubuntoo, does this work for you?

If anybody can point me to the proper thread/location I'll post or add to a bug report for evolution.

---

### Post by dre12b on 2010-07-20
Just missed an alarm.  Unpredictable failure - the best kind!  So enable and then disable the alarm feature for each calendar you use after each login.  Isn't that a charm?

---

### Post by lidex on 2010-07-21
In 'System>Preferences>Startup Applications' do you have 'Evolution Alarm Notifier' checked/enabled?

---

### Post by dre12b on 2010-07-21
yes.

---

### Post by Noo 2 Ubuntoo on 2010-07-21
> **dre12b said:**
> After seeing [this post]("http://ubuntuforums.org/showpost.php?p=4275931&postcount=3") on an older thread, I disabled alarms for both my Personal (local only) and Gcal (Gcal synced w/ local copy) under Preferences>Alarms> then closed down and restarted evolution.  Then I enabled the alarms again for both calendars.  Now alarms notifications are appearing normally for both calendars.  I also tested having the computer totally shut off for a scheduled an alarm and then restarting.  The notification appeared after login, as it should.  

I'll keep the thread updated on whether the "fix" holds.  Noo 2 Ubuntoo, does this work for you?

If anybody can point me to the proper thread/location I'll post or add to a bug report for evolution.

Nope it didn't work. In fact even my old workaround mentioned atthe beginning of this thread is no longer working (although I don't think I tried it a second time).

For clarification, I have always been getting alarms that go off whilst the computer is switched on. It is only alarms that go off when the computer is off that are being missed. Occasionally an alarm that went off when the computer was off does appear. So, as you say in a later post it's unpredictable. Personally I think it's one of 2 things:

1. Evolution "alarm notify" daemon is failing to connect properly with Gnome session management in respect of alarms that went off whilst the computer was switched off - more of a session management problem really. OR:

2. At start up of the computer, Evolution is failing to run a daemon to do a backwards search for any alarms that went off (whilst the computer was off) that have not been already been notified. It's like a process is failing to run.

The cause for this may be a hardware problem or just a slightly faulty install. I have  a friend whose alarms work fine just like on your second laptop. 

The possible cause mentioned at #1 was originally put forward by Francesco Locunto in the launchpad bug report here : [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/147163](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/147163)

**2.5 years ago!**  It seems this is known about upstream but it's not considered important! You may want to add your comments/findings. I'll try a fresh install this weekend in the hope it's a slightly bad install and post the result back here.

---

### Post by Noo 2 Ubuntoo on 2010-09-26
Well, for anyone interested, I finally got around to doing a fresh install - 2 in fact. First one I restored my old evolution data & settings without thinking and found the problem persisted.

So I tried another "Fresh install", this time without any restore of evolution data/settings and.... the problem persists. 

I noticed the alarm displayed in the middle of the screen (when the computer is switched on and the alarm initiates), but the default setting is for the alarm to appear in the top panel, although it is my personal setting to have the alarm display in the middle of the screen. This was just a standard install though and I had **definitely not** reset the alarm notify position after the 2nd Fresh install. This tells me the "Fresh Install" was not as "Fresh" as it should have been.

I can't imagine where the system picked up that old setting from as I formatted the Ubuntu partition of the hard drive before re installing.

One thing, a friend has a 64 bit installation and his alarms display correctly, whereas mine is 32 bit. Maybe that has something to do with it, but I'm fresh (excuse the pun) out of ideas now as to what could be causing the problem.  :confused:

---

### Post by dre12b on 2010-11-16
Well, a fresh x86 Maverick install seems to have cured the problem I cited: unpredictable failure of evolution alarm notifications.  I'm pretty sure I restored my home folder rather than using the evolution wizard.  I'm unsure whether this was a bug fix or simply that the 

As has been noted above, this does not address the original bug described here regarding notification failures on start-up for alarms that occurred when the computer was shutdown.

---

### Post by Noo 2 Ubuntoo on 2010-11-16
there has been a development which I wasn't going to post but as dre12b has reposted here goes:

About 2 weeks ago every second Evolution alarm (which had become due and expired whilst the computer was switched off) started displaying on computer start up.
    
I have done nothing more to the computer since my last post and am still on Lucid:confused:

The problem seems to have half resolved itself, but I saw no updates relating to Gnome daemons, desktop or Evolution (I think the problem rests in one of these areas) whilst updating Lucid. If it eventually displays all expired alarms I will post back.

I still think it's a sporadic bug which has somehow partially repaired itself.

---

### Post by onaridge on 2010-11-16
I don't get any new email notifications since I installed Evolution about a month ago. Anybody got any ideas? Yes I have checked the appropriate boxes etc. I have asked this question before but I don't think too many people use Evolution and I am beginning to understand why :-)

---

### Post by jtarin on 2010-11-17
The one's not recieving notifications or alarms.....are you setup as POP or IMAP?

---

### Post by Noo 2 Ubuntoo on 2010-11-17
> **onaridge said:**
> I don't get any new email notifications since I installed Evolution about a month ago. Anybody got any ideas? Yes I have checked the appropriate boxes etc. I have asked this question before but I don't think too many people use Evolution and I am beginning to understand why :-)

This is really off topic and belongs in another "email notifications not working" type thread like this one[http://ubuntuforums.org/showthread.php?t=1311909]("http://ubuntuforums.org/showthread.php?t=1311909")but:

The final answer to this is to install the excellent Jean-Yves Lefort mail notification,located in Ubuntu Software centre or Synaptic, whichever is your preference. They've sorted it out now so you don't have to mess about at the command line creating new file references and linking them like I had to. 

So all you do is install the above Mail notification, link it to your mail account and it "just works".

---

### Post by dre12b on 2010-12-02
Since my last post I have confirmed that I am NOT receiving alarm notifications for Evolution calendar items that occur while the machine is shutdown.

Does the workaround mentioned above work for calendar notifications or only email?  New messages are indicated in the "message" panel applet for me, but no notifications.  Not a problem for me, my only concern is the unreliable notification behavior for calendar alarms that organize my work day (and life)!

---

### Post by Noo 2 Ubuntoo on 2010-12-02
> **dre12b said:**
> Since my last post I have confirmed that I am NOT receiving alarm notifications for Evolution calendar items that occur while the machine is shutdown.

Does the workaround mentioned above work for calendar notifications or only email?  New messages are indicated in the "message" panel applet for me, but no notifications.  Not a problem for me, my only concern is the unreliable notification behavior for calendar alarms that organize my work day (and life)!

If you are asking about my post re Jean-Yves Lefort's mail notification then no, it does not work for calendar alarms, only e mail. 

By the way, about every 2nd or 3rd calendar alarm that became due whilst the computer was off is now being notified to me when I next switch the computer on. I have done absolutely nothing more to fix the problem, it's like the system has a mind of it's own. 

If you are using this at work I would recommend the "MS Outlook" calendar (which I found completely reliable when I used it at work) or Mozilla Sunbird (calendar only) or Lightning (Thunderbird with Sunbird integrated) as long as you don't set recurring reminders - Lightning/Sunbird has a bug relating to those kinds of reminders.

The drawback (for me) to both the Microsoft & Mozilla solutions is that they do not integrate to the desktop (Windows in MS's case) requiring you to keep them running all the time to receive your calendar alarm notifications.

---

### Post by dre12b on 2010-12-02
Thanks for the info - too bad Yves Lefort's program doesn't provide calendar notifications.  I previously used Outlook on Windows and Thunderbird on Windows then Ubuntu.  I was drawn to Evolution's elegant desktop integration, but the lack of alarm notification is a serious concern for my workflow.

---

### Post by Noo 2 Ubuntoo on 2011-01-24
OK, so for anyone interested I have developed a workaround this problem. It seems that if I record at least 2 alarms on any given day (they can be at the same time, next to each other or separated by any time period within the day) Evolution will display at least one of them.

If there are more than 2 alarms on a particular day Evolution **usually** displays all of them. I use the appearance of an alarm as a prompt to check the drop down calendar in the panel at the top of the desktop  for any other alarms that should have gone off.

Remember, this is for alarms that became due whilst the computer was turned off, **not** alarms becoming due whilst the computer is on - this alarm function works fine.

I am not marking this thread solved as a workaround is not a solution. I live in hope that someone in the know looks at this thread one day and posts the solution.

---

### Post by dre12b on 2011-01-24
Thanks for this Noo 2 Ubuntoo.  The other day I received a notification for a missed appointment when I turned the computer on - I'm pretty sure it occurred when I had multiple missed appointments.  So makes sense.  I'm mystified that this hasn't been fixed.  

We should all comment on the old bug you turned up to see if we can get some attention for it: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/147163](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/147163)

---

### Post by Noo 2 Ubuntoo on 2011-01-24
> **dre12b said:**
> Thanks for this Noo 2 Ubuntoo.  The other day I received a notification for a missed appointment when I turned the computer on - I'm pretty sure it occurred when I had multiple missed appointments.  So makes sense.  I'm mystified that this hasn't been fixed.  

We should all comment on the old bug you turned up to see if we can get some attention for it: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/147163](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/147163)

Hi Dre12b, I see what you mean but (there's always a but with me) I now  believe this is some kind of hardware problem that affects very few people who have a certain bit of hardware or combination of hardware that the Alarm system just doesn't like, unless you give it a kick up the 
a_ _  e  by inserting more than 1 alarm reminder within a 24 hour period. 

That would explain why so few people have commented on this and the fact that a friend has no problems with reminders on his machine. I can't/won't do an analysis of all the hardware in my computer, trying to cross reference similar hardware with other users experiencing the same problem, especially when my theory could be wrong anyway.

 Besides, my PC was cobbled together from 3 old machines by a couple of friends who build their own computers from scratch. I am neither a builder nor a programmer so I'll stick where I am. 

Sorry if this reply disappoints but I have to be realistic about my capabilities and the interest of the developers in this problem if this affects  a minority of users, as it seems to.

---

### Post by dre12b on 2011-01-24
That would make sense.  I've also been puzzled at the small number of people commenting here.  Though I'm using a Thinkpad T60 laptop, so far from an obscure build.

No expectations that you would cross-reference parts with software.  I wonder if there is another configuration option in Evolution that triggers the issue.

---

### Post by Noo 2 Ubuntoo on 2011-01-25
Dunno, I've looked at the settings under G-conf editor/apps/evolution in the past, but I don't understand what I'm looking at. For now my workaround works OK (for me with my software/Hardware configuration))

---

### Post by anrom on 2011-04-10
I just did a network upgrade to Lucid 10.04. I'm having the same problem of Evolution 2.30.3 not showing calendar alarm notifications, when it was fine before in Hardy.  

I tried the fix in this thread [http://ubuntuforums.org/showthread.php?t=874333&highlight=evolution+2.30.3+alarm]("http://ubuntuforums.org/showthread.php?t=874333&highlight=evolution+2.30.3+alarm"), where I de-selected the 'notify_with_tray' entry in gconf-editor. Though several people said it worked for them, it didn't for me.

Has anyone come up with any other solutions?

---

### Post by Noo 2 Ubuntoo on 2011-04-11
> **anrom said:**
> I just did a network upgrade to Lucid 10.04. I'm having the same problem of Evolution 2.30.3 not showing calendar alarm notifications, when it was fine before in Hardy.  

I tried the fix in this thread [http://ubuntuforums.org/showthread.php?t=874333&highlight=evolution+2.30.3+alarm]("http://ubuntuforums.org/showthread.php?t=874333&highlight=evolution+2.30.3+alarm"), where I de-selected the 'notify_with_tray' entry in gconf-editor. Though several people said it worked for them, it didn't for me.

Has anyone come up with any other solutions?

Open Evolution and try: Edit/Preferences/Calendar and Tasks.
Under "General" tab ensure "Alerts" are set to display a notification before every appointment (advance notice period of alarm to be set by you).

Under "Alarms" tab ensure "display alarms in notification area only" box is deselected (this should be unchecked anyway if you deselected the "notify with tray" in gconf-editor, but you never know). Select all calendars appearing under "select the calendars for alarm notification".

---

### Post by anrom on 2011-04-11
Thanks, Noo 2 Ubuntoo. I have been getting popup alerts since a reboot, but still no sound alarm. I applied your fix and performance is still the same - popup, but no sound.  Slightly different issue than what this thread is for, so I'll keep searching for an answer.

Edited to add: Came across a mention of KAlarm somewhere and installed it. it does everything Evolution's alarms do and it works for me in Ubuntu 10.04, FF 3.6.16. It's got a small pop-up text and sound alarm built in. I don't use Evolution for email, so I've gone with KAlarm.

---

### Post by Noo 2 Ubuntoo on 2011-04-13
anrom, if you're still subscribing to this thread which desktop are you using, Gnome, KDE or some other? 

 Reason I ask is I really want an alarm system that works without me having to record every alarm twice (the workaround I use) before the alarm will display (in situations where the PC was switched off when the alarm became due). I thought Kalarm required a KDE environment but I use Gnome.

(edit - off thread but if you wanted a sound or music to play, I believe  that can be done in Gconf -editor apps/evolution/calendar/notify. Double click "programs" then click "add" in the edit key box that displays and enter the file path to the program you want to run. As I understand it this should "just work" but I've never tried it and wouldn't be able to offer any further help if you tried it and it went wrong.)

---

### Post by anrom on 2011-04-17
Noo 2 Ubuntoo,

I'm using Gnome. KAlarm is a KDE application but also runs on Gnome & other desktops. I found it easy to dl [http://www.astrojar.org.uk/kalarm/]("http://www.astrojar.org.uk/kalarm/") and add to my panel with a right-click from Applications/Accesories, which is where it ended up after download. 

I like the small popup text alert with the default beep sound, which is loud enough for me. I think I'd get annoyed at music playing for all the alarms I set. Good luck.

---

### Post by 1longtime on 2011-05-12
> **Noo 2 Ubuntoo said:**
> Open Evolution and try: Edit/Preferences/Calendar and Tasks.
Under "General" tab ensure "Alerts" are set to display a notification before every appointment (advance notice period of alarm to be set by you).

Under "Alarms" tab ensure "display alarms in notification area only" box is deselected (this should be unchecked anyway if you deselected the "notify with tray" in gconf-editor, but you never know). Select all calendars appearing under "select the calendars for alarm notification".

I followed this setup months ago, and I'm seeing/hearing no alarm at all.  I've NEVER seen/heard an Evolution alarm.  This occurs even when I'm logged into the machine working and Evolution is open.  I'm forced to check my calendar obsessively to stay on top of my daily events.  Once again: I have never seen a single alarm from Evolution ever.

I have a vanilla Evolution install.  I see an Evolution notification app in the Startup menu.  I see evolution-indicator as an installed package (a Gnome panel indicator applet) which was installed by default.  I've never tweaked Evolution in any way on this machine.  I'm using a Dell E6510 running 64bit Ubuntu.  This was a problem with 10.04, 10.10, and now 11.04 (I log in with "Ubuntu Classic" with 11.04 because I didn't care for the new Unity desktop... I think that means I'm still a Gnome user).

My de facto alarm: coworkers walk by and ask "aren't you going to the meeting?"

---

### Post by Noo 2 Ubuntoo on 2011-06-07
> **1longtime said:**
> I followed this setup months ago, and I'm seeing/hearing no alarm at all.  I've NEVER seen/heard an Evolution alarm.  This occurs even when I'm logged into the machine working and Evolution is open.  I'm forced to check my calendar obsessively to stay on top of my daily events.  Once again: I have never seen a single alarm from Evolution ever.

I have a vanilla Evolution install.  I see an Evolution notification app in the Startup menu.  I see evolution-indicator as an installed package (a Gnome panel indicator applet) which was installed by default.  I've never tweaked Evolution in any way on this machine.  I'm using a Dell E6510 running 64bit Ubuntu.  This was a problem with 10.04, 10.10, and now 11.04 (I log in with "Ubuntu Classic" with 11.04 because I didn't care for the new Unity desktop... I think that means I'm still a Gnome user).

My de facto alarm: coworkers walk by and ask "aren't you going to the meeting?"

I don't know what your level of knowledge is so apologies if this seems patronising: 

After doing the settings in "Edit/Preferences" when you set an appointment you need to set the alarm for that specific appointment by clicking the alarm icon (usually a clockface with yellow ring around it). The alarm dialogue box will appear, if you have never done this before it's probably pre set to "none". If so click the drop down menu and choose the advance warning time period you want. You can customise to any time you want. When you're finished, click "close" which will return you to the appointment box and click the "save" icon in the top left corner of the appointment box. 

Assuming you have done nothing in gconf-editor, the alarm should appear in the top panel as a little yellow clock. The other thing is, I still have to record every single reminder twice  to make it work - have you been doing that?

I don't envy you using this reminder system at work, must be very embarrassing for you. Mozilla Sunbird/Lightning will work on Ubuntu (except it doesn't like recurring appointments and you have to keep it running in the background all the time).

P.S. the other thing I forgot to say is, although you see "Evolution alarm notifier" in the startup applications Preferences" make sure it is definitely checked/ticked so that the startup apps daemon knows to initiate the alarm notifier each time you switch on your machine.

---

### Post by Gordon D on 2011-08-03
I am experiencing the same problems. Ubuntu 11.04 - Unity. Have used Google Calendar for years. Was using Thunderbird and Lightning and all reminders and alarms worked fine.

Migrated to Evolution and now I only seem to get alarms on a random basis and the Snooze function doesn't seem to work either. Perhaps I need to delete and re-enter all my recurring events, but I don't relish this, especially given that newly added events don't seem to work correctly either.

The notification envelope doesn't turn blue either when I get new mail, although I am not sure if it is related.

Frustrating that this doesn't work out the box as it should be core. Have tried a few of the suggestions in these threads, but no luck.

Will be moving back to Thunderbird at the earliest opportunity.

---

### Post by Noo 2 Ubuntoo on 2011-08-04
> **Gordon D said:**
> I am experiencing the same problems. Ubuntu 11.04 - Unity. Have used Google Calendar for years. Was using Thunderbird and Lightning and all reminders and alarms worked fine.

Migrated to Evolution and now I only seem to get alarms on a random basis and the Snooze function doesn't seem to work either. Perhaps I need to delete and re-enter all my recurring events, but I don't relish this, especially given that newly added events don't seem to work correctly either.

The notification envelope doesn't turn blue either when I get new mail, although I am not sure if it is related.

Frustrating that this doesn't work out the box as it should be core. Have tried a few of the suggestions in these threads, but no luck.

Will be moving back to Thunderbird at the earliest opportunity.

I think your problem is slightly different - possible synchronisation problems between Google calendar and Evolution calendar. My problem is with the local calendar and remains to this day, I just keep double entering every appointment to make them work. My notification envelope in the panel does turn green? (maybe they changed the colour for Unity - I'm still on Lucid) when I get new mail but only whilst I have Evolution switched on and logged into my e - mail accounts. The envelope won't change colour if mail arrived whilst Evolution was off/not logged into accounts. This is why I use the excellent Jean-Yves Lefort mail notification.

You may get the answer if you look for Evolution/Google calendar synchronisation problems or start your own thread on the issue.

---

