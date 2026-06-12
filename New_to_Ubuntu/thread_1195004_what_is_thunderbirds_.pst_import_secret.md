---
title: "what is thunderbirds .pst import secret???"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by stinger30au on 2009-06-23
Can someone please explain that it is possible for thunderbird to be installed to a pc running xp and it can retireve email from outlook expess and yet evolution can not read pst files?


if you have xp running and install thunderbird it can read all the email from outlook express and import it without outlook express running.

magic aint it.

i have been hunting thru these archives and this challenge has been around for over 4 years now

correct me if im worng but thunder bird is open source is it not?
and isnt evolution open source as well???

so cant we pinch the bits of magic out of thunderbird that can read the pst files and shove the the magic in to evolution so it can do the same as well???

if thunderbird can do it in windows, then they surely know the secret to it, so what is it and why is it so difficult after 4 years to not have a solution to this for everyone to share and use?

please enlighten me with tons of wisdom and knowledge

---

### Post by stinger30au on 2009-06-23
just found this too

[http://freshmeat.net/projects/pstimportplugin/?branch_id=72191&release_id=265973](http://freshmeat.net/projects/pstimportplugin/?branch_id=72191&release_id=265973)

thunderbird pst import plugin

---

### Post by wizard10000 on 2009-06-23
> **stinger30au said:**
> Can someone please explain that it is possible for thunderbird to be installed to a pc running xp and it can retireve email from outlook expess and yet evolution can not read pst files?


if you have xp running and install thunderbird it can read all the email from outlook express and import it without outlook express running.

magic aint it.

i have been hunting thru these archives and this challenge has been around for over 4 years now

correct me if im worng but thunder bird is open source is it not?
and isnt evolution open source as well???

so cant we pinch the bits of magic out of thunderbird that can read the pst files and shove the the magic in to evolution so it can do the same as well???

if thunderbird can do it in windows, then they surely know the secret to it, so what is it and why is it so difficult after 4 years to not have a solution to this for everyone to share and use?

please enlighten me with tons of wisdom and knowledge

Outlook Express doesn't use .pst files but I get the general idea  ;-)

If you don't want to go through Thunderbird to get your mail into Evolution maybe Outport is what you need - but I don't think this will work with OL2007 data files.  Should work with OL2000/2003, though.

[http://outport.sourceforge.net/](http://outport.sourceforge.net/)

---

### Post by jimv on 2009-06-23
Install the Lightning calendar/task plugin for Thunderbird and forget about Evolution.  You'll be happier.

Plus you can install the Google Calendar Provider plugin for Thunderbird which will allow you to sync with Google Calender.

---

### Post by stinger30au on 2009-06-23
> **jimv said:**
> Install the Lightning calendar/task plugin for Thunderbird and forget about Evolution.  You'll be happier.

Plus you can install the Google Calendar Provider plugin for Thunderbird which will allow you to sync with Google Calender.

no i wont be happier im sorry.

i have been the route of thunderbird, infact i bashed my head against a brick wall with it for over a year.

the best thing i ever did was ditch it and move all my emails etc to evolution

---

### Post by stinger30au on 2009-06-23
> **wizard10000 said:**
> Outlook Express doesn't use .pst files but I get the general idea  ;-)

If you don't want to go through Thunderbird to get your mail into Evolution maybe Outport is what you need - but I don't think this will work with OL2007 data files.  Should work with OL2000/2003, though.

[http://outport.sourceforge.net/](http://outport.sourceforge.net/)


the clinets im converting use outlook express

outport will not do outlook express

here is a thread from 4 years ago with the same question and still no decent answers 4 years later

[http://ubuntuforums.org/showthread.php?t=78159&highlight=import+outlook+express+evolution](http://ubuntuforums.org/showthread.php?t=78159&highlight=import+outlook+express+evolution)

---

### Post by michaelzap on 2009-06-23
> **stinger30au said:**
> Can someone please explain that it is possible for thunderbird to be installed to a pc running xp and it can retireve email from outlook expess and yet evolution can not read pst files?

if you have xp running and install thunderbird it can read all the email from outlook express and import it without outlook express running.

I think that you answered your own question right there. PST files can only be read on Windows systems with Outlook installed (or Outlook Express for its files). So if Evolution were installed on Windows it probably could read these files. The problem is that PSTs are a proprietary format with lots of restrictions.

---

### Post by stinger30au on 2009-06-23
> **michaelzap said:**
> I think that you answered your own question right there. PST files can only be read on Windows systems with Outlook installed (or Outlook Express for its files). So if Evolution were installed on Windows it probably could read these files. The problem is that PSTs are a proprietary format with lots of restrictions.

ah ha!

well that really sucks

im amazed after 4 years that no one has reverse engineered their protocols and made an importer for the data yet

---

### Post by michaelzap on 2009-06-23
> **stinger30au said:**
> ah ha!

well that really sucks

im amazed after 4 years that no one has reverse engineered their protocols and made an importer for the data yet

I think that there are other tools that can do what Thunderbird does. See this page for some examples:
[http://www.slipstick.com/addins/housekeeping.asp](http://www.slipstick.com/addins/housekeeping.asp)

But really, once you get your email out of Outlook (whatever way works), why would you ever need to do it again?

I originally exported all of my Outlook email to Thunderbird and then just moved those files to Linux. But nowadays I use IMAP anyway, so I uploaded all that downloaded email via IMAP. Now I can get to any of it using any program I choose.

You might consider doing that instead of messing with local files.

---

### Post by questioning on 2009-06-23
> **michaelzap said:**
>  PST files can only be read on Windows systems with Outlook installed (or Outlook Express for its files). 



You can copy the pst files from windows to your ubuntu file system. you dont need windows or running outlook express to have working pst files. still evolution is unable to import.

---

### Post by stinger30au on 2009-06-23
HOLD THE BUS!!!!

i have just found that kmail

[http://kontact.kde.org/kmail/](http://kontact.kde.org/kmail/)

can & *DOES* have an import of outlook express version 4/5/6 .dbx

if you install it 

sudo apt-get install kmail

and open it and hit file, import theres the outlook express import tool

cool. 
no need for windows to be running by the looks of it
i must test this later today

---

### Post by stinger30au on 2009-06-23
> **michaelzap said:**
> 
But really, once you get your email out of Outlook (whatever way works), why would you ever need to do it again?.


when your busy converting clients to ubuntu regularly, you want to make the operation as easy and smooth and fast as possible

---

### Post by stinger30au on 2009-06-23
i just tested kmail, it can import direct from .dbx files *WITHOUT* windows running and it does import all attachments as well


*YIPPIE*

---

### Post by jimv on 2009-06-23
> **stinger30au said:**
> no i wont be happier im sorry.

i have been the route of thunderbird, infact i bashed my head against a brick wall with it for over a year.

the best thing i ever did was ditch it and move all my emails etc to evolution

I can't imagine what it is that you could be trying to do that would cause you so much frustration.

---

### Post by HermanAB on 2009-06-23
The very best way to handle Email is with a decent IMAP mail server, for example Citadel, which has a BerkeleyDB backend.  

Run Outlook, create a new account to hook with IMAP to Citadel, then click-drag-drop all your email from the old local account to the new IMAP account.

Problem solved.

From now on, you can access your email with any mail client or web browser from anywhere  in the world.

---

### Post by stinger30au on 2009-06-23
> **HermanAB said:**
> The very best way to handle Email is with a decent IMAP mail server, for example Citadel, which has a BerkeleyDB backend.  

Run Outlook, create a new account to hook with IMAP to Citadel, then click-drag-drop all your email from the old local account to the new IMAP account.

Problem solved.

From now on, you can access your email with any mail client or web browser from anywhere  in the world.

does this work with outlook express at all as a number of my clients are using this and im doing my best to get them away from it

---

### Post by stinger30au on 2009-06-23
another handy utility to convert .dbx files

[http://freenet-homepage.de/ukrebs/english/dbxconv.html](http://freenet-homepage.de/ukrebs/english/dbxconv.html)

i must test it and see if it also does attachments too

---

### Post by stinger30au on 2009-06-23
i just tested dbxconv

it does convert the email attachments as well

yippie


so you can backup the emails to a directory using fabs autobackup and convert from there 

[http://www.fpnet.fr/autobackup/download.php?lang=en](http://www.fpnet.fr/autobackup/download.php?lang=en)

---

### Post by stinger30au on 2009-06-23
convert outlook express .wab to idif format use his

[http://www.worldstart.com/tips/tips.php/1949](http://www.worldstart.com/tips/tips.php/1949)

dawn address book converter


yippe!!

no need to install thunderbird to windows xp and stuff round

backup all the data to hdd first via fabs autoback and convert from there

now if evolution could just look at the .dbx files and .wab file we would be cooking with gas

im glad to see it can be done with out thunderbird

after 4 years there should be an alternative and i have found one

the thunderbird route would probably save a bit of stuffin round, but, for me its nice to see an alternative, the easiest solution to all of this would be a direct import from evolution itself though

---

