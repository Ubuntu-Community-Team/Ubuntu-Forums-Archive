---
title: "Run M$ Outlook in Linux?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Captain Legless on 2009-02-06
Is it possible to run Micro$oft, (spit), Outlook in Linux, maybe through WINE?

As good as 'Evolution' maybe, it seems to be a bit basic and missing many features found in Outlook. There may be add-ons or plug-ins available for Evolution that I'm not aware of, if that is the case, where are they?

---

### Post by Thingymebob on 2009-02-06
What exactly are you missing from outlook? You're correct there are plugins for evolution a good place to start is [http://projects.gnome.org/evolution/eplugins.shtml]("http://projects.gnome.org/evolution/eplugins.shtml"). Another alternative is thunderbird + lightning which I find to be far superior to outlook, although doesn't integrate with Ubuntu desktop as well as Evolution.

These plugins are included in your Ubuntu installation 
 - calendar-file, - calendar-http, - calendar-weather, - itip-formatter, - plugin-manager, - python, - default-source, - addressbook-file, - startup-wizard, - mark-all-read, - groupwise-features, - groupwise-account-setup, - webdav-account-setup, - mail-account-disable, - publish-calendar, - caldav, - imap-features, - google-account-setup, - sa-junk-plugin, - bogo-junk-plugin, - exchange-operations, - mono,

```
sudo apt-get install evolution-plugins
```
will give you
- bbdb, - subject-thread, - save-calendar, - select-one-source, - templates, - copy-tool, - mail-to-task, - mark-calendar-offline, - audio-inline, - mailing-list-actions, - default-mailer, - email-custom-header, - import-ics-attachments, - prefer-plain, - mail-notification, - attachment-reminder, - face, - backup-restore

```
sudo apt-get install evolution-plugins-experimental
```
will give you
- folder-unsubscribe, - mail-to-meeting, - save-attachments, - external-editor, - ipod-sync, - tnef-attachments

---

### Post by dro0g on 2009-02-06
> **Captain Legless said:**
> Is it possible to run Micro$oft, (spit), Outlook in Linux, maybe through WINE?

As good as 'Evolution' maybe, it seems to be a bit basic and missing many features found in Outlook. There may be add-ons or plug-ins available for Evolution that I'm not aware of, if that is the case, where are they?

I use Outlook 2003 via Codeweaver's Crossover (commercial version of wine) but I believe it works fine in wine as well. It's a little bit flakier than under Windows, but by and large it works great. I periodically try Evolution but I've always found it to be unusable. OWA with Exchange 2007 works OK as well.

You have to do some tweaking to get Outlook set as the default mail client for mailto: and such. Here's my entry under Preferred Applications in the System -> Preferences menu.

```
/opt/cxoffice/bin/wine "/home/user/.cxoffice/win2000/drive_c/Program Files/Microsoft Office/OFFICE11/OUTLOOK.EXE" -c IPM.Note /m %s
```

---

### Post by y@w on 2009-02-06
I tried using Outlook using CrossOver on OS X and I couldn't get SSL to work. It turns out they don't have the SSL API's yet.. You can work around it by establishing an SSL connection using stunnel. Otherwise, works great for me on OS X and I imagine it's the same in Linux..

---

### Post by Captain Legless on 2009-02-07
> **Thingymebob said:**
> What exactly are you missing from outlook? You're correct there are plugins for evolution a good place to start is [http://projects.gnome.org/evolution/eplugins.shtml]("http://projects.gnome.org/evolution/eplugins.shtml")..................

Thanks as usual guys. I'll check some of this stuff out in due course.

There are just 'silly' bits and pieces that I miss from Outlook - such as the ability to assign different colours in the calender, ability to drag and drop appointments...etc
Automatically assign colours to incoming mail meeting various criteria, being able to forward and reply to emails without having the blue line preceding original text.......others that I can't remember off the top of my head.

I don't doubt that it's a very good email client, it does look a lot like Eudora.

If I were to run Outlook through WINE, I assume I would have to reinstall a new setup. Would I then me able to import mail, contacts and calender details from the instance installed on my XP partition?

---

### Post by Captain Legless on 2009-02-07
I had a look at the "manual" and tried the following:-
[U]
**[COLOR="Blue"] How do I change the color of my calendars and tasks?[/COLOR]**[/U]

[COLOR="Blue"]In the Calendar component, right click on the calendar in the top-left tree and click on Properties. Select a suitable color in the properties window. Similarly, change the color of the task from the "Tasks" component.[/COLOR]

NOTHING!!:(

---

### Post by Eisenwinter on 2009-02-07
You call them "Micro$oft", yet you prefer to use their software over open source alternatives.

---

### Post by Captain Legless on 2009-02-07
> **Eisenwinter said:**
> You call them "Micro$oft", yet you prefer to use their software over open source alternatives.

I don't PREFER to, if that was the case I obviously wouldn't be posting questions here..........would I? :roll:

---

### Post by Sidewinder1 on 2009-02-07
You may wish to try Thunderbird as stated above; with all of the add-ons and extensions you should be able to do 99.9% if not all...

---

### Post by empty_spaces on 2009-02-07
+1 for Thunderbird.

Currently, I'm managing 3 email accounts in it - work email(POP), Gmail(IMAP), and Hotmail(Webmail Extension)
I use the Lightning extension to display calendars/appointments in Thunderbird, and the Provider for Google extension to manage my Google calendar from within Thunderbird.

---

### Post by Declanthedork on 2009-02-07
Before you use [They who must not be named], try Mozilla Thunderbird. It's a fairly unheard of program.

---

### Post by Captain Legless on 2009-02-07
OK - thanks guys.
I've had a look at Thunderbird some time back, infact I used Thunderbird to import my emails from Outlook to Evolution, I wasn't aware there are more odds and sods that can be added to it.

---

### Post by abn91c on 2009-02-07
hav a look at kmail, it has all the outlook features by default

---

### Post by Captain Legless on 2009-02-07
OK, I'll take a look. I didn't think Kmail was so comprehensive.

---

### Post by misswham on 2009-07-30
The only reason I log into windows xp is because I need to sync my blackberry with my ms outlook.  I have read all of these answers and havent found an answer yet.

can this be done?

---

### Post by kansasnoob on 2009-07-30
I really don't have an answer but, quite honestly, using Outlook Express in Linux seems to make as much sense as buying a new Lexus and tossing in an old Ford engine!

---

### Post by presence1960 on 2009-07-30
> **kansasnoob said:**
> I really don't have an answer but, quite honestly, using Outlook Express in Linux seems to make as much sense as buying a new Lexus and tossing in an old Ford engine!

:lol: lmao

---

### Post by egalvan on 2009-07-30
> **kansasnoob said:**
> using Outlook Express in Linux seems to make as much sense as buying a new Lexus and** tossing in an old Ford engine!**

Well, I love Japanese auto technology, but I can think of a couple of "old Ford engines" I would love to have...

Ford Shelby Cobra V8, circa '69... massive power, and dependable.

Ford 300CI, (inline six), massive torque, absolutly bullet-proof.

:D

Sorry, I couldn't resist!

---

### Post by misswham on 2009-07-30
I assumed I explained why I needed outlook to sync with my contact and calender with my blackberry.  I just wanted to know.  I am sorry if I offended someone because I asked.  I have a legitimate reason why I need outlook.  I said I use linux for 99% of my computer needs and I dont see why someone would get offended because i asked about 1 app in windows that I have to use that linux can't accommodate.  Wine is in Synpatic and I assumed that it was intended to be used with some windows apps.

---

### Post by aesis05401 on 2009-07-30
> **misswham said:**
> I assumed I explained why I needed outlook to sync with my contact and calender with my blackberry.  I just wanted to know.  I am sorry if I offended someone because I asked.  I have a legitimate reason why I need outlook.  I said I use linux for 99% of my computer needs and I dont see why someone would get offended because i asked about 1 app in windows that I have to use that linux can't accommodate.  Wine is in Synpatic and I assumed that it was intended to be used with some windows apps.

Hello, 

I think whenever anyone uses the '$' in MS there may be some replies that are not as friendly.  Best of luck with whatever solution works for you.

---

### Post by bodhi.zazen on 2009-07-31
> **misswham said:**
> The only reason I log into windows xp is because I need to sync my blackberry with my ms outlook.  I have read all of these answers and havent found an answer yet.

can this be done?

[http://ubuntuforums.org/showthread.php?t=190938](http://ubuntuforums.org/showthread.php?t=190938)

[http://www.linux.com/news/embedded-mobile/mids/8210-syncing-your-blackberry-on-linux](http://www.linux.com/news/embedded-mobile/mids/8210-syncing-your-blackberry-on-linux)

---

### Post by presence1960 on 2009-07-31
> **misswham said:**
> I assumed I explained why I needed outlook to sync with my contact and calender with my blackberry.  I just wanted to know.  I am sorry if I offended someone because I asked.  I have a legitimate reason why I need outlook.  I said I use linux for 99% of my computer needs and I dont see why someone would get offended because i asked about 1 app in windows that I have to use that linux can't accommodate.  Wine is in Synpatic and I assumed that it was intended to be used with some windows apps.

I don't think you offended anyone. kansasnoob took the opportunity to poke some fun at the use of OS's and apps, not at anyone personally. While I thought his comment funny, I apologize if you were offended.

---

### Post by ukripper on 2009-07-31
Go thunderbird as others suggested! Supports multi platform and plenty of addons:D

---

### Post by Stevie78 on 2009-07-31
Theres simply no need for Outlook as there is Thunderbird.

---

### Post by y@w on 2009-07-31
If you're using Outlook to sync with your Blackberry to manage contacts and calendars, I'd highly recommend you check out Gmail's Blackberry app. It lets you sync both over the air without having to plug in a cable all the time.

---

### Post by mikechant on 2009-07-31
kansasnoob said:
> I really don't have an answer but, quite honestly, using Outlook Express in Linux seems to make as much sense as buying a new Lexus and tossing in an old Ford engine!

The original poster was talking about **Outlook** not **Outlook Express**

They are completely different programs. Outlook express is an very basic, insecure, ancient and now unsupported mail client for home use. Outlook is a very comprehensive heavy-weight business oriented mail client, task manager, meeting planner calender etc. and is 100% compatable with and highly integrated with the MS Exchange server, which is heavily used by businesses. Despite being written by MS, the outlook/exchange combination is comprehensive, polished, well regarded and is often a big obstacle to Linux migration in the business world.

Stevie78 said:
> Theres simply no need for Outlook as there is Thunderbird.

See my comments above. Thunderbird is an excellent mail client which I use myself at home, and it is far superior to Outlook Express. But it is not a substitute for Outlook if you are using an Exchange server. And even if you are not using an Exchange server, Outlook has a lot of good little features and is very hard to match.

I feel it's necessary to state that my experience comes from using Outlook for about 10 years at work, where Windows is the standard environment. At home I exclusively use Ubuntu and Thunderbird and they do everything I need.
Outlook is the only MS applications that I have never had cause to mutter "****ing piece of useless MS cr*p" at.

---

### Post by egalvan on 2009-07-31
> **presence1960 said:**
> I don't think you offended anyone. **kansasnoob took the opportunity to poke some fun at the use of OS's and apps**, not at anyone personally. While I thought his comment funny, I apologize if you were offended.

And i took the opportunity to poke some fun at kansasnoob! :P

Ford Shelby 427!

:KS

ErnestG
Countdown: two to go!

---

### Post by jacklinux on 2009-07-31
i try'd to run outlook on ubuntu and it failed. Even WINE held no anwsers. i guess'd it was like the WLM installer.

---

