---
title: "yes, yet another beginner / yahoo chat"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by stvrich on 2009-10-23
Hello,
:)

I DO intend to BE a "permanent" member here/now.
trying to CRAM all the Linux my tiny brain can take.
(I'm an "ex" win I.T. guy from long ago)  I'm not THAT old, just haven't been in the "industry" lately.

I ---KNOW--- the experienced techs here have seen what I'm about to say 4.5 billion times... but I must put it this way.  I AM completely new to U8.1  what I NEED to do right away is just...

---------------please-

I just WANNA get yahoo CHAT running immediately (for security reasons)
I'm pretty sure my xp is in fact being monitored ... long story, it's a "friendly" competition.

I simply wanna be on Linux -- right ---now, while leaving my chat up and running.

I've tried using pidgeon.  NG  :( just seems to "hang" never connecting.
I've tried installing wine,  then yahoo chat...:(:( phooey
THEN it said I needed flash for firefox (the browser I'm using):(:(:( 
Tried to insall the win xp  version of adobe,  wine did not seem to "kick in"  gving an error:confused:

uhm
a couple hours have gone by, of ME trying to read self help files... and etc.
please....

I am "assuming" this is simple (to someone who KNOWS)  can ...SomeBody
just spell it out for me?

I JUST wanna get yahoo CHAT running.  immediately.  And shutdown XP

'splain me,
step by step, I can follow directions.  The ones on the WEB ... are USELESS aparently, 
yes, I am fluent in English!  It just doesn't seem to be OBVIOUS to me what I am missing.

my ubuntu is relatively still new and fresh, straight from the cd... I have done little or nothing to modify a THING.  It DOES have a wireless (and active) inet connection.

sorry for the lameness....
I'm just in a rush to get chat up
and shut down xp.

any rapid response is MUCH appreciated.

Steve

---

### Post by stvrich on 2009-10-23
The Error I get is

An error ocurred while loading the archive

And the command line said:
[/home/steve/Desktop/install_flash_player.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/steve/Desktop/install_flash_player.exe or
          /home/steve/Desktop/install_flash_player.exe.zip, and cannot find /home/steve/Desktop/install_flash_player.exe.ZIP, period.

---

### Post by Mariane on 2009-10-23
A rather general response. 

In Ubuntu, when you don't know what exactly is the chat program you want you can do:

```

sudo apt-cache search chat

```

This gives you a list. Pick a likely name and scroogle it up to see if it would do what you want. Don't pick anything called lib-something as these won't do anything on their own. 

Once you have chosen, let us say a chat program called XYZchat, type

```

sudo apt-get install XYZchat

```

and then

```

XYZchat

```

Mariane

---

### Post by oldsoundguy on 2009-10-23
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

.exe files will not install on any form of Linux outside of installing in VM or Wine.

---

### Post by masque7 on 2009-10-23
> **stvrich said:**
> .exe.
Flash + .exe? I don't understand. Looks like you were trying to install the Windows version of Flash or something?

Please be more clear in what your problems are. As far as Yahoo chat goes, yes, Pidgin is a multi-protocol IM client that supports Yahoo chat. Please give the specific problems/errors and refrain from smiley abuse (if possible!) :)

---

### Post by Penguin Guy on 2009-10-23
[[SIZE="3"]Click here to get flash working.[/SIZE]]("apt:flashplugin-nonfree")
Or run this in the terminal: [COLOR="Green"]sudo apt-get install flashplugin-nonfree[/COLOR]

---

### Post by Paqman on 2009-10-23
The new default chat client in Ubuntu is going to be Empathy. I believe you can get Yahoo chat working if you install empathy and telepathy-haze.

---

### Post by stvrich on 2009-10-23
Thanx penguin guy... I'll give yours a try.
I'm obviously TRYING to use WINE preccisely to get a windows program going.   uhm... the yahoo chat and adobe WOULD be the *.exe files referred to.  

I read about WINE and the stuff that I was pointed to told me that once I had installed WINE, it would automatically be used to run the *.exe files.  except... there is "something" stopping it.

I haven't a clue (yet)

wasn't going to say anything till they realized that I'm just totally ignorant of the Linux stuff.  ie WINE 
and any file system issues.

except for the fact I'd use WINE, with an *.exe file.  obviously.  (if not, please do enlighten me)  I'm TRYING.

I feel so DARN clumsy, but, I'm excited to just keep trying.  I've ordered some good course materials (ubunto server 9)  but working with an ubuntu manual right now.  ibex

and stuck on basics, cramming.

---

### Post by stvrich on 2009-10-23
I did mention I installed WINE, right.  At least I think, I did.


WINE is used for *.exe files ... right?

---

### Post by pricetech on 2009-10-23
Check out this page:

[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

I had a similar problem with Pidgin and Yahoo and this solved it for me.

NOTE:  There are 2 distinct commands listed.  Copy and paste them one at a time.

Good Luck and let us know if that fixes it for you.

---

### Post by Paqman on 2009-10-23
> **stvrich said:**
> 
WINE is used for *.exe files ... right?

Yes, but it's a bit of a fudge, only a tiny minority of Windows apps will run well through it. Using a Linux app will always be quicker and easier than trying to shoehorn a Windows app into your system with Wine.

---

### Post by pricetech on 2009-10-23
Flash:
If you're using the 64 bit version of Ubuntu, follow these steps to make flash work.  If you're using the 32 bit version it's actually easier.

Download the 64 bit Flash Player from Adobe Labs
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Unzip it and copy it to the following locations:
/usr/lib/mozilla/plugins
/usr/lib/opera/plugins
/home/username/.mozilla/plugins

NOTES:
You won't have an opera folder if you don't have Opera installed.
The word "username" refers to your username.
The .mozilla folder is hidden so you'll need to view hidden files to see it.

After that it should work.

If you're using 32 bit just install the flash plugin via Synaptic.  Just search for "flash" and install the "flashplugin-nonfree" to make flash work in Firefox.

IMPORTANT !!!!!
The steps for 32 bit will NOT work on 64 bit and vice versa.

Again, keep us posted how it goes.

---

### Post by stvrich on 2009-10-23
Okay,  now the flash plugin is working.

do you recommend any particular chat client?
(and, I am assuming, as most windows people do.. .that if I am told a certain program... it WILL install...)

remember, my relative viginity here...LoL
I'm TRYING to "do the right things".

---

### Post by stvrich on 2009-10-23
the link worked without a single hiccup.  by the way, I did nothing but click on it.

---

### Post by stvrich on 2009-10-23
RE:  Wine,  Ohhhh I didn't know that, I've READ about WINE so many times I thought it was a "sure thing"

thanx paqman

---

### Post by stvrich on 2009-10-23
trying your suggestions now Price tech.... brb

---

### Post by stvrich on 2009-10-23
price tech... I just read your quote... (LMAO)

where did THAT quote come from???  chest/hat/fire???  LOL

---

### Post by stvrich on 2009-10-23
okay, THAT (the update manager "update") seems to be working, it's downloading a LOT,
it'll be a while ... I'll repart back asap

---

### Post by stvrich on 2009-10-23
All my stuff is 32 bit.  ubuntu 8.1

---

### Post by stvrich on 2009-10-23
god, it IS going to be a while... it's saying an hour and 20min

whew

---

### Post by pricetech on 2009-10-23
> **stvrich said:**
> price tech... I just read your quote... (LMAO)

where did THAT quote come from???  chest/hat/fire???  LOL

From a British Science Fiction series called Doctor Who.  The doctor said it, but the context is way too involved to explain.

---

### Post by stvrich on 2009-10-23
I guess I'm being dumb.... I guess I should go in and UNCLICK SOME of it...

and just accept the pidgeon?

---

### Post by stvrich on 2009-10-23
it's okay I "get it" as soon as you mention Dr. Who...
cool

---

### Post by pricetech on 2009-10-23
> **stvrich said:**
> god, it IS going to be a while... it's saying an hour and 20min

whew

Obviously you did not update after you installed.  Lots of stuff to update the first time.  Routine updates will take a fraction of the time.

---

### Post by stvrich on 2009-10-23
okay... I just kinda figured that out on my own.... I DID stop it and what I saw in progress looked fundamentally VERY important.... ignorant as I am..

so I restarted the whole thing again.

thanx guys.... this is marvelous.

I knew it had to be "basic" stuff I was just unaware of....

as soon as it's done updating... I'll be back with report

---

### Post by stvrich on 2009-10-23
at least, I'm hoping this allows me to just install/run   'chat'  .... LoL

it will be SO much better when I understand things.
looking forward to it.

---

### Post by tacantara on 2009-10-23
stvrich:  If you still have problems trying to get Yahoo IM up and running via Pidgin, you might try using the chat feature in Yahoo Mail.  I set up Pidgin to manage my Yahoo IM, but I find it more convenient most times to just open a tab on my Firefox browser and keep it for checking my Yahoo mail and chat.

I haven't tested the web browser chat feature with any of the other Linux-friendly browsers, so I can't comment on if it'll run in Chrome, et.al.

---

### Post by stvrich on 2009-10-23
no, I did NOT update after installing... you ARE correct.

it SHOULD be logically evident to do... and I did not think it at all.
thank You

---

### Post by stvrich on 2009-10-23
tacantara... yes, that was what I was HOPING for, at a minimum... the yahoo mail version

---

### Post by ikisham on 2009-10-23
People, this guy is using Intrepid (ubuntu8.10). It has the old yahoo protocol (or something like that) in Pidgin so it won't work, of course. Anyone out there that uses Pidgin and yahoo just tell him the settings he must change in Pidgin to reenable the yahoo chat. It looks that simple and he may chat from the live-cd, no updates needed.

---

### Post by stvrich on 2009-10-23
Hmmmm  I'm "listening"

---

### Post by pricetech on 2009-10-23
> **ikisham said:**
> People, this guy is using Intrepid (ubuntu8.10). It has the old yahoo protocol (or something like that) in Pidgin so it won't work, of course. Anyone out there that uses Pidgin and yahoo just tell him the settings he must change in Pidgin to reenable the yahoo chat. It looks that simple and he may chat from the live-cd, no updates needed.

The update is what I had to do to make Pidgin work with Yahoo.  Just passing along what worked for me.

If you have a quicker fix, I'd like to make a note of it.

---

### Post by stvrich on 2009-10-23
ikisham, I THINK there was supposed to be some "new" version of pigeon they pointed me at... but I (of course) would not know (for sure) if THAT version has the required update.  I am asuuming it will, tho.  I'll give it a try and see.  Other than that... I'm still all ears.

---

### Post by stvrich on 2009-10-23
I will note it also, of course....

---

### Post by stvrich on 2009-10-23
1 hour 8 min to go... it's a bit quicker than it's estimating

---

### Post by pricetech on 2009-10-23
> **tacantara said:**
> 
I haven't tested the web browser chat feature with any of the other Linux-friendly browsers, so I can't comment on if it'll run in Chrome, et.al.

Just now tested it in Seamonkey, Opera, Galeon, and it works in all 3.  I'm assuming it has already been tested in Firefox and I did not try it in Epiphany.

---

### Post by pricetech on 2009-10-23
> **stvrich said:**
> ikisham, I THINK there was supposed to be some "new" version of pigeon they pointed me at... but I (of course) would not know (for sure) if THAT version has the required update.  I am asuuming it will, tho.  I'll give it a try and see.  Other than that... I'm still all ears.

The two commands you copied and pasted from the Pidgin website would add them to your list of software to update and the update is what made it work for me.

Incidentally, I am running 8.04 now but that same method worked in 9.04 so I see no reason for it not to work in 8.10

---

### Post by stvrich on 2009-10-23
Roger, loud and clear.

30 min to go

---

### Post by stvrich on 2009-10-23
almost there, says 20 min.

---

### Post by stvrich on 2009-10-23
Yes, I am noting ALL of this as simply fundamental "to do" stuff after a new install.  I went to "spidertools" website, where I bought my Linux training,  to run some linux tutorials, and of course without flash they wouldn't run either... so...

ALL this is VERY fundamental to the most basic desktop.

I truly appreciate the help.

---

### Post by stvrich on 2009-10-23
done downloading, now applying alllll that new stuff

---

### Post by stvrich on 2009-10-23
okay, ready to reboot.  

As a side note, THIS installation of Ubuntu (for some reason) was giving me strange file system errors upon reboots (lately) after rebooting 2 or 3 times it would start.  I do NOT know what that was about.  Nor am I too terribly worried about it (yes, I KNOW "it is not right") It SHOULD come back up no problem -  I believe, and for all I know, the updates may have "fixed" it.  We'll see.

I went back into update manager, and I see it is now offering me the Ubuntu 9.04

SHOULD I just go ahead and update it... while I am at it?

I'll do the reboot, and assuming it "works" I will check pidgeon, and see if there's a new version of pidgeon to apply and test it.

I should be back in a few min.

---

### Post by Paqman on 2009-10-23
> **stvrich said:**
> 
I went back into update manager, and I see it is now offering me the Ubuntu 9.04

SHOULD I just go ahead and update it... while I am at it?


Up to you. It may take a long time, depending on your internet speed.

However, 9.10 is out in a week, so you'd still be behind the play, and would have to run *another* upgrade to get to the latest system. It might just be easier to skip 9.04 and do a fresh install of 9.10 in a weeks time.

Or you could just stay on 8.10, which will be supported until April.

---

### Post by stvrich on 2009-10-23
I am pleased to report.

Pidgeon ABSOLUTELY works... !
I am suitably THRILLED.

And my eyes are (just a little bit more) open.  As I said, this "update" is fundamental.  And was missing.

After reboot.
I applied the NEW version of Pidgeon.  
Then THAT, once installed notified me there was yet ANOTHER 2 or 3 updates for THAT version of Pidgeon.
After applied,
it appears fine.

Also,
With the flash plugin, The Yahoo mail/chat DOES indeed work also.
So do my tutorials in the spidertools website.

THANK YOU for helping me.

I definitely had the feeling I had like (at least) 6 pairs of eyes on me as I did this.
I appreciate it folks.
I'll MOST LIKELY be back...

probably soon.
I will be TRYING to "break" things... you know how it goes.
Studying like crazy.  

Thank you.  :P

if you've any final comments, I'll check back in the near future/ all this evening.  :)

(no I won't bother with updating the system.. .QUITE happy it's working now... just wanna get ON with learning more command line, scripting... already been doing some python.... etc....

I just MUST get "moving" on this.  I'll get the 9.04 in the mail on cd in about a week)

---

### Post by stvrich on 2009-10-23
Yes, SpaceMan Spiff is my icon.  from Calvin and hobbes.  I've made an ENTIRE series of avatars/icons in both gif and jpeg if anybody wants a copy of it.  Calvin has LIMITLESS facial expressions so you can switch the icon to suit the moment/your mood.

---

### Post by stvrich on 2009-10-23
and ... yes, XP went  "OFF"  immediately following
there should have been NO interruption of my "chat client" being online in the slightest,

except a little flicker.

but now.....
I'm sure, no access.

;->

---

### Post by stvrich on 2009-10-23
if I take this ONE step further in security, is there some way to encript this data stream to/from this machine... encrypting just the chat?

or is that too much to ask now?  Too far beyond me?
I know it's balatantly obvious I've barely learned to SPELL Linux...
if you've anything to remark on I will do what I can to implement security/my own monitoring.

I realize that if someone is monitoring... say, the OTHER end of this chat, or ANY communications from THIS (new ubuntu setup) and they even use screen scraping... on the XP or vista side of things, (if THAT is what's on the other side)  I'm sure even encrypting this stream is relatively useless or defeated.  

With thanx
Steve

---

### Post by Randy Myers on 2009-10-28
I copied and pasted and put the deb--etc in repository; however, the certification key never appeared on desktop to get the ball rolling. I un-installed gaim and pidgin. Tried to re-install but I told that it will not be installed. I want to 100% be free of windows. Any help would be apprecaited.

---

### Post by pricetech on 2009-10-29
When you copy and paste the lines posted on the Pidgin site, there are two distinct command lines there.  Copy and paste each one separately.

I say that because I made the same mistake initially.

(duh)

---

