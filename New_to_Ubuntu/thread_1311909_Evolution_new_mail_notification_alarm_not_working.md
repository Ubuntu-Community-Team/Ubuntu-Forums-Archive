---
title: "Evolution new mail notification alarm not working"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Noo 2 Ubuntoo on 2009-11-02
Hi, just installed Karmic a couple of days ago and noticed the new mail notification alarm in the panel isn't working. I checked the plugin manager GUI and mail notification is checked. When I click on the little envelope (seems to be a manager for empathy, evolution and pidgin) in the panel it shows evolution but lists mail as 0 when I have unopened mails. Anyone know why Evolution isn't talking to this little envelope and not displaying new mail notifications?

I did disable the alarm notification for calendar events appearing in the panel a while ago so they appear in the middle of my screen.

Thanks in advance

---

### Post by Noo 2 Ubuntoo on 2009-11-03
Bump any one?

---

### Post by Dedi Landsman on 2009-11-03
Hi, i had a somewhat similar problem, but rather with the sound alert for new mail in Evolution [the icons for new mail works fine]. i got around this by installing a plug-in [general to ubuntu, not specifically an Evolution plugin] called Mail Notification [http://www.nongnu.org/mailnotify ]("http://www.nongnu.org/mailnotify")
It is excellent, there are many others, but this one seems to be the best as it fits well with Gnome, it should be in Synaptic

---

### Post by Noo 2 Ubuntoo on 2009-11-03
> **Dedi Landsman said:**
> Hi, i had a somewhat similar problem, but rather with the sound alert for new mail in Evolution [the icons for new mail works fine]. i got around this by installing a plug-in [general to ubuntu, not specifically an Evolution plugin] called Mail Notification [http://www.nongnu.org/mailnotify ]("http://www.nongnu.org/mailnotify")
It is excellent, there are many others, but this one seems to be the best as it fits well with Gnome, it should be in Synaptic

Thanks for the advice  found it in synaptic and been reading up on it.It looks like you need to load in another program and be careful about where you place it in the file system before this can talk to evolution. As a noobie this is complicated for me ( I'm sscared of the terminal and command line) but something else is happening now - I'm getting new mail notifications appearing and then they disappear after a few seconds. It used to be (intrepid 8.10 - I went straight thru to Karmic)  that an envelope with a yellow star appeared in the notification area of the panel when I got a new mail and it stayed there until I opened the mail. Does anyone know if the  behaviour has been purposely changed so that the new mail notification only displays for a few seconds now? Just trying to establish if this is a feature or if somethings wrong.

---

### Post by Dedi Landsman on 2009-11-03
> It looks like you need to load in another program and be careful about where you place it in the file system before this can talk to evolution.as far as i remember it does not  have anything to do with Evolution, it communicates directly to your mail server such as Google. Synaptic is gonna take care were to put the new stuff.
 >  I'm scared of the terminal and command lineyou don't have to mess with that either, just download with Synaptic, and configure some details in this new one, in Applications>Internet>Mail notification.
you wont have to bother any more about the notifications with Evolution.

---

### Post by Noo 2 Ubuntoo on 2009-11-03
Ok tried that - found 2 in synaptic - first one called "evolution -mail- notification" which wasn't installed, Second one "mail notification" which was installed. I didn't install the first one and went to applications - internet where I found mail notification. Tried to configure but then it wanted a password for a keyring (presumably because it wants to save my e mail password to the keyring in Ubuntu but I dont know the password and I've never used the keyring? Anyone tell me what to do next?

---

### Post by Dedi Landsman on 2009-11-04
Hi, the version of  "mail notification" that i installed is: **5.4.dfsg.1-1 Ubuntu** my Ubuntu is J.J. 9.04
 in the configuration of my "mail notification"  there is nothing about Keyring. 
 maybe "mail-notification-evolution" would do better  for you? [it is not installed on my machine].

---

### Post by frogotronic on 2009-11-04
mail notification also does not work on my Karmic install (fresh)

----------------------------------

EDIT:  Here's the solution: [https://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/355209](https://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/355209)

---

### Post by philinux on 2009-11-04
Clean install Karmic

It's working here, but I didn't get any sound notification.

I disabled the mail notify plugin and in prefs unticked play a sound. There is a notify tick box there too. Bit overkill.

Made a script to play a sound and then a filter to activate it as a workaround. This has been bugged.

---

### Post by Noo 2 Ubuntoo on 2009-11-04
Multiple thanks to Dedi Landsman and cement_head. For any other Ubuntu noobs like me here's the full story to get notification of new e mails on **evolution 2.28** working properly:

1. Open Synaptic package manager (in administrator mode) ensuring you have **BOTH ** these packages  installed (my upgrade only came with one of them installed)

(a) mail-notification-evolution                                            5.4.dfsg.1-1ubuntu:5.4.dfsg.1-1ubuntu:evolution support  for mail notification

(b) mail-notification 5.4.dfsg.1-1ubuntu:5.4.dfsg.1-1ubuntu: mail notification in system tray

2. Open evolution going to Edit - plugins and check the box for "mail notification" and  "Jean-Yves Lefort's Mail Notification"

3. Go to Applications - Internet - Mail Notification and click "Mail Notification" which should appear as an icon in notification area in the panel at the top of your screen.

4. Right click the "Mail Notification" icon in the top panel, then click "properties" and add your evolution mailbox from the drop down menu that appears and your finished **UNLESS **

5. you get a message that mail notification cannot contact evolution in which case open a terminal (in administrator mode) typing the following:

sudo ln -s /usr/lib/evolution/2.24/plugins/org-jylefort-mail-notification.eplug /usr/lib/evolution/2.28/plugins/
sudo ln -s /usr/lib/evolution/2.24/plugins/liborg-jylefort-mail-notification.so /usr/lib/evolution/2.28/plugins/  

Press enter and exit terminal. I did a restart to make sure it updated and then repeat steps 1 - 4 to be sure of everything.

**Step 5  only applies to evolution 2.28 which ships with Karmic Koala ** as can be seen through the references to "2.28" in the terminal command at step 5 above. It should also work with evolution version 2.26 in Jaunty Jackalope by changing the "2.28" to "2.26". Thanks again to  cement_head and Dedi Landsman I couldn't have worked this out without your help.

---

### Post by trytenn on 2009-11-26
Hi!
This is maybe a stupid question but why would I want the notification applet to look in evolution for new mails? The applet blinks error when i turn off evolution. Do you always have evolution running? My little netbook is to slow for that. Ore can the applet check for new mails in accounts that is registered  in evolution without starting evolution? I know I can configure it to check for example gmail. I just wonder what the notification-evolution-applet thing is good for. 

No 2 Ubuntu: Your "how to" was great! Thanx!

ps. Maybe you have a evolution-daemon running in the background? If so, how do you do that? 

ps2. They should have put this indicator as default instead of the other one that don't work with evolution. It doesn't look good to new users when the preconfigured applications don't work.

---

### Post by trypanon on 2009-11-26
> **noo 2 ubuntoo said:**
> hi, just installed karmic a couple of days ago and noticed the new mail notification alarm in the panel isn't working. I checked the plugin manager gui and mail notification is checked. When i click on the little envelope (seems to be a manager for empathy, evolution and pidgin) in the panel it shows evolution but lists mail as 0 when i have unopened mails. Anyone know why evolution isn't talking to this little envelope and not displaying new mail notifications?

I did disable the alarm notification for calendar events appearing in the panel a while ago so they appear in the middle of my screen.

Thanks in advance
***
has it (notification) ever worked on any system??? I gave up with this after 2 minutes of worthless struggling - the loss of notificator's will to work won, & i went to have some nicotine :)

---

### Post by Noo 2 Ubuntoo on 2009-11-26
> **trytenn said:**
> Hi!
This is maybe a stupid question but why would I want the notification applet to look in evolution for new mails? The applet blinks error when i turn off evolution. Do you always have evolution running? My little netbook is to slow for that. Ore can the applet check for new mails in accounts that is registered  in evolution without starting evolution? I know I can configure it to check for example gmail. I just wonder what the notification-evolution-applet thing is good for. 

No 2 Ubuntu: Your "how to" was great! Thanx!

ps. Maybe you have a evolution-daemon running in the background? If so, how do you do that? 

ps2. They should have put this indicator as default instead of the other one that don't work with evolution. It doesn't look good to new users when the preconfigured applications don't work.

Firstly,as my user name suggests I am new to all things linux  so my answer may be stupid:  

I have 2 mail accounts registered in evolution. One is a POP account and the other is Gmail (as in using IMAP for receiving options). The POP account won't work unless I open evo (which can be done via the mail notification). The Gmail (IMAP) account will link to the Gmail server via the mail notification icon (just double click & a GUI appears asking for password to connect to mail server). I think this confirms your own experience. 

I use the POP account for low priority stuff, so no matter if I dont access it for a couple of days. The Gmail (IMAP) account is for high priority & I open it via mail notification every time I go on the internet. The use to me is that I do research on the net & often have multiple apps running simultaneously, which gets confusing. I don't want to run evo (yet another app on my overcrowded panel) unless I have to, so the mail notification is a nice gizmo for me.  

When researching I don't have the inclination to look at incoming mails and forget to check when I finish a session. The mail notification reminds me how many unopened mails I have (I always disable networking via the network manager applet in the panel which sits next to the mail notification applet).

I guess the above confirms I don't have evo running in the background although I suppose there may be a way to do that (which I don't know). 

I agree your PS2 - the indicator applet is a waste of space to me - mine can recognise how many accounts I have in evo but always lists my in boxes as empty and I don't use empathy or Pidgin - there may be problems with those apps too.

Maybe no one else has a use for mail notification (most people don't seem to like evo) but it can be invaluable for some,depending on their circumstances and how they use their computer. I hear great things about Thunderbird, but I make extensive use of evo's calendar and I hear Lightning is quite buggy.

---

### Post by trytenn on 2009-11-26
Okej. I don't used to use mail clients. But now I have to many mail accounts so one client for them all make things easier. But evolution have made me disappointed. Mostly the indicator problem, but now it works and I don't want to tweak thins again.
I installed the netbook-remix and the shipped music player Exaile also have many buggs. It feels like the 9.10 release was a beta release. But still, ubuntu is great and I'm now 100% bill gates free.

---

### Post by ccoupe on 2009-12-03
Many thanks!  I had to use the ln -s commands in step 5. One has to quit and restart Evolution after the terminal commands before it finds the new soft links. A system restart or logout is not required.

---

### Post by Noo 2 Ubuntoo on 2009-12-03
> **ccoupe said:**
> Many thanks!  I had to use the ln -s commands in step 5. One has to quit and restart Evolution after the terminal commands before it finds the new soft links. A system restart or logout is not required.

Happy to be of help. I didn't know you only have to quit and restart evolution, thanks for the tip.

---

### Post by rbaleksandar on 2010-05-05
Old thread but still up to date at least for me. :D
The linking command (ln -s /usr/......) returns that the file exists. 

  I'll give an example to make it clear what I do and what the Notifiere/Evolution does:

- Mail Notifier is running. Evolution is NOT running. I set it to check directly the Gmail account I have and not via any other application (Evolution in our case).
- A new mail arrives.
- Mail Notifier pops up a message telling me this.
- But when I try to open the message by clicking on the Mail Notifier, it opens Opera (my default browser) and not Evolution.

  So far I'm not able to find a way to change this. I want the Mail Notifier to check my inbox not with Evolution but by directly connecting to Gmail. And when it finds out that a new message(s) has arrived, I'll be able to check it out by using Evolution (that is - Evolution starts automatically in this case) and not by opening my web browser and visiting [www.gmail.com](www.gmail.com).


Cheers,
rba

---

### Post by Noo 2 Ubuntoo on 2010-05-07
> **rbaleksandar said:**
> Old thread but still up to date at least for me. :D
The linking command (ln -s /usr/......) returns that the file exists. 

  I'll give an example to make it clear what I do and what the Notifiere/Evolution does:

- Mail Notifier is running. Evolution is NOT running. I set it to check directly the Gmail account I have and not via any other application (Evolution in our case).
- A new mail arrives.
- Mail Notifier pops up a message telling me this.
- But when I try to open the message by clicking on the Mail Notifier, it opens Opera (my default browser) and not Evolution.

  So far I'm not able to find a way to change this. I want the Mail Notifier to check my inbox not with Evolution but by directly connecting to Gmail. And when it finds out that a new message(s) has arrived, I'll be able to check it out by using Evolution (that is - Evolution starts automatically in this case) and not by opening my web browser and visiting [www.gmail.com](www.gmail.com).


Cheers,
rba

Happy the thread still helps others. The mail notifier is working for you the same as for me.

 As far as I know the Mail Notifier runs by establishing it's own connection with your mail account via a web interface (not an e - mail client like evolution, thunderbird etc). If it detects unopened mail it tries to provide access via the e mail client you have registered with it. If the e mail client is not running it defaults to opening the mail via a web browser. At least that's how it works for me using Googlemail in IMAP mode. Maybe using Gmail in POP mode would allow the notifier to open evolution automatically? 

Sorry this doesn't help but I don't have the expertise to know how to change it's behaviour. This may not be the notifier for you as there may be other mail notifiers that will automatically open evolution for you.

---

### Post by rbaleksandar on 2010-05-07
Hi. :)

  Thanks for the reply. Do you know any mail notifiers that will do what I described in my previous post?

---

### Post by frogotronic on 2010-05-08
> **rbaleksandar said:**
> Old thread but still up to date at least for me. :D
The linking command (ln -s /usr/......) returns that the file exists. 

  I'll give an example to make it clear what I do and what the Notifiere/Evolution does:

- Mail Notifier is running. Evolution is NOT running. I set it to check directly the Gmail account I have and not via any other application (Evolution in our case).
- A new mail arrives.
- Mail Notifier pops up a message telling me this.
- But when I try to open the message by clicking on the Mail Notifier, it opens Opera (my default browser) and not Evolution.

  So far I'm not able to find a way to change this. I want the Mail Notifier to check my inbox not with Evolution but by directly connecting to Gmail. And when it finds out that a new message(s) has arrived, I'll be able to check it out by using Evolution (that is - Evolution starts automatically in this case) and not by opening my web browser and visiting [www.gmail.com](www.gmail.com).


Cheers,
rba

Are you sure that you have the evolution mial notification plugin removed?

---

### Post by rbaleksandar on 2010-05-08
Hi.

  Well, no. It's not removed. I thought both mail-notification and mail-notification-evolution should be installed. At least that's what I understand from reading the packages' description:

```

**mail-notification**
mail-notification works with system trays implementing the
freedesktop.org System Tray Specification, such as the GNOME Panel
Notification Area, the xfce4 Notification Area and the KDE System Tray.
** Note: Evolution support is available with mail-notification-evolution.**

```

```

**mail-notification-evolution**
 This package provides Evolution support for Mail Notification.

```

  So in order to make the mail-notification do what I described in a previous post, I have to remove the mail-notification-evolution? Will give it a try. :)

There is simply no option in the settings-menu of the notification-applet that gives me the opportunity to choose Evolution for opening messages and the notification-applet to check my inbox via direct connection to Gmail. :(

---

### Post by frogotronic on 2010-05-08
Ok, so there's two issues (one is the mail-notify setup, one is the notifications popups)

1) If you don't want to be checking evolution mailboxes, then you don't need to have that plugin installed, or at least setup up to check evolution

2) Launch MAIL NOTIFICATION and choose ADD under the General Tab (see screenshot 1)

3) Enter your Gmail account information, close dialogue

4) Switch to the Status Icon tab, and choose the "launch e-mail reader" (screenshot #2)

5) Make sure your DEFAULT **Mail Reader** is selected as evolution...

   *SYSTEM>PREFERENCES>PREFERRED APPLICATIONS*

6) You'll have to set up your Gmail account in Evolution via the Add Accounts, etc.  (I'll assume you know how to do this, if not try --> [here]("http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/")).

7)  Now, to get the notifications to work - not so easy in Jaunty and Karmic (or at least not that intuitive).  Open up Configuration Editor (if its not under your Applications>System Tools>Configuration Editor) you can make it appear by editing your menus via the Main Menu application (System>Preferences) or simply type

```
gconf-editor
```

in a terminal.

In gconf-editor, go to apps->mail-notification->popups and
  (a) erase everything in actions.
  (b) uncheck "blink on errors" (under apps->mail-notification)

8) close up gconf-editor, terminal, evolution.

9) Make sure Mail Notifications (see screenshot) is set to run at startup, see screenshot 3

10) Make sure your libnotify is installed

```
sudo apt-get install libnotify1 libgtt2-notify-perl python-notify evolution-indicator libnotify-bin
```

11) Reboot


______________________________________________


Post back if this doesn't work

- CH

---

### Post by rbaleksandar on 2010-05-08
Thanks for the detailed info. :)

  I had almost everything except the gconfig-part. Now when it prompts me for a new mail and I click open it still opens Opera. But if I click on the tray icon, it opens Evolution. Huh...

---

### Post by frogotronic on 2010-05-08
> **rbaleksandar said:**
> Thanks for the detailed info. :)

  I had almost everything except the gconfig-part. Now when it prompts me for a new mail and I click open it still opens Opera. But if I click on the tray icon, it opens Evolution. Huh...

So do you get a gtk popup, or a notify-osd popup (see attachment for notify osd)?

---------------------------------------

Edit:  The problem could be the GMAIL settings - do you remember answering a prompt (from Opera) that asked you whether or not you wanted to use Gmail as the default mail client the first time you logged into Gmail?  If so, you need to find that option, either in Opera Settings or Gmail Settings and uncheck it.

---

### Post by Noo 2 Ubuntoo on 2010-05-08
> **rbaleksandar said:**
> Thanks for the detailed info. :)

  I had almost everything except the gconfig-part. Now when it prompts me for a new mail and I click open it still opens Opera. But if I click on the tray icon, it opens Evolution. Huh...

I'm following this with interest so:

1.Is the notification a popup that disappears after a few seconds or does it stay in your tray until you open the mail?

2. Does the tray icon open Evolution fully connected or do you still have to input passwords to make the final connection to your mail account?

---

### Post by rbaleksandar on 2010-05-08
1)The notification is in form of a standart dialog window. See [here]("http://ubuntuforums.org/showthread.php?p=8780523") (1st post describes what happens). It's weird because when I test the notification with "Display test messages" I get a normal **osd popup** like the one in cement_head's last post (see the thumbnail). I think this started happening after I removed the settings from the **gconfig**.

2)Here's a description what does what:

- clicking on the tray icon -> opens inbox with Evolution (that's how it's supposed to work and I'm happy about it :))
- clicking on a popup (before)/dialog window (now) -> opens inbox with Opera (not how it's supposed to work) that is - it opens mail.google.com.


  cement_head, I haven't seen such prompt in Opera. Besides I haven't created a mail account in Opera (using the integrated mail client there) AND in the preferences in PROGRAMS I've chosen Evolution for the **mailto protocol**.

---

### Post by frogotronic on 2010-05-08
> **rbaleksandar said:**
> 1)The notification is in form of a standart dialog window. See [here]("http://ubuntuforums.org/showthread.php?p=8780523") (1st post describes what happens). It's weird because when I test the notification with "Display test messages" I get a normal **osd popup** like the one in cement_head's last post (see the thumbnail). I think this started happening after I removed the settings from the **gconfig**.

2)Here's a description what does what:

- clicking on the tray icon -> opens inbox with Evolution (that's how it's supposed to work and I'm happy about it :))
- clicking on a popup/dialog window -> opens inbox with Opera (not how it's supposed to work).


  cement_head, I haven't seen such prompt in Opera. Besides I haven't created a mail account in Opera (using the integrated mail client there) AND in the preferences in PROGRAMS I've chosen Evolution for the **mailto protocol**.

okay, so all you have to do is remove the popup 

Goto Evolution>Prefences and uncheck the "display a notification" (see screenshot).

You've got some program that's generating a gtk popup - find that and shut it off and everything should work as you want.

- CH

---

### Post by rbaleksandar on 2010-05-08
The only program that I know it's generating popups right now is Rythmbox. But even after turning it off, the notification is still in form of a dialog window. Can you tell me how to see which application is generating popups? Besides I find it dull if I have to turn off all applications that have no problems displaying popups just to get a popup-notification from MN. :( When I run Empathy, Rythmbox etc. etc. at the same time, I don't have such problems although all these applications generate popups.

---

### Post by Noo 2 Ubuntoo on 2010-05-08
> **rbaleksandar said:**
> The only program that I know it's generating popups right now is Rythmbox. But even after turning it off, the notification is still in form of a dialog window. Can you tell me how to see which application is generating popups? Besides I find it dull if I have to turn off all applications that have no problems displaying popups just to get a popup-notification from MN. :( When I run Empathy, Rythmbox etc. etc. at the same time, I don't have such problems although all these applications generate popups.

Would this be something to do with gconfig-editor and then apps/evolution/eplugin/evolution-indicator and then uncheck the "show bubble2 function?

I mean "show_bubble" function.

And of course I meant "gconf-editor"......doh!!

---

### Post by frogotronic on 2010-05-08
> **rbaleksandar said:**
> The only program that I know it's generating popups right now is Rythmbox. But even after turning it off, the notification is still in form of a dialog window. Can you tell me how to see which application is generating popups? Besides I find it dull if I have to turn off all applications that have no problems displaying popups just to get a popup-notification from MN. :( When I run Empathy, Rythmbox etc. etc. at the same time, I don't have such problems although all these applications generate popups.

Try linking the popup with sound and when the sounds plays its "that" popup - just a process of elimination

You are using the Jean Yves notification and not the other?

---

### Post by rbaleksandar on 2010-05-10
Yep, I'm using the Jean's plug-in. Will have to test these things. Because right now if I check my mail and I have 10 unread messages, 10 dialog windows pop up on the screen. Very annoying indeed. :D

---

### Post by frogotronic on 2010-05-10
> **rbaleksandar said:**
> Yep, I'm using the Jean's plug-in. Will have to test these things. Because right now if I check my mail and I have 10 unread messages, 10 dialog windows pop up on the screen. Very annoying indeed. :D

Hi,

Make sure all the actions are deleted, like this -> attached

---

### Post by rbaleksandar on 2010-05-10
Yes, I deleted them the first time you told me. :) Only ** [ ] ** was left in this column (like in your screenshot).

---

### Post by ArielEnter on 2010-05-12
I like what [rbaleksandar]("http://ubuntuforums.org/member.php?u=345172") did:

> - Mail Notifier is running. Evolution is NOT running. I set Mail Notifier to check directly the Gmail accountI told Mail Notifier to Consider new mail as read in the click action.

So basically my routine every time I receive a message is the following:

1.- The notification message show up and I select OK.
2.- I click on Mail Notifier so that all new mails are consider as read and their notification don't show up again.
3.- and then at last I open evolution to see the new emails.

Quite long I guess.

The other approach for those of you that don't mind to have evolution running all the time but don't want to see it on screen all the time, is to use an application call alltray that will minimize evolution to the notification area and not to the windows list panel. See the following post: [http://ubuntuforums.org/showthread.php?t=433661](http://ubuntuforums.org/showthread.php?t=433661)

In my computer, the indicator-aplet envelop did look different when ever I received a new mail, and also a message bubble showed up as long as evolution was running. But it didn't worked for me because I wanted a notification that stayed on screen until I closed up, and the bubble messages only staid 10 sec. If any body knows how to have only evolution's bubble notifications stay until I close them up it will be very appreciated if I could hear it.

---

