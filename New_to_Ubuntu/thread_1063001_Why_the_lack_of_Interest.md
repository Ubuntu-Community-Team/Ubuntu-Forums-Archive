---
title: "Why the lack of Interest"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by garwal on 2009-02-07
[B]Just a quick Bio first. I am a 60 year old PhD in Computer Science Retired and I have always used some flavour of Linux. No expert but have done my share of research.Now my question, If you read you will find one of the first things a windows convert is asking for is a voice chat program like Yahoo. You then see many giving advice to use the dozen or so apps that will do text chat, ie"pidgin,QuteCom,Gizmo, and all the rest. Not one of these have I had luck getting to work with voice. Yes I know Skype works great but few use this application. So I wonder why the lack- luster effort being put in to development of something that will work. I love my linux and will not switch but if anyone knows of a way to have voice on one of the dozen chat applications I would be glad to write a step by step of how to set it up and make it clear for everyone. Lets see if we can come together and solve this problem. 
Thanks
Gary;)[/B]

---

### Post by igknighted on 2009-02-07
The app you seek is Empathy.  All the other choices out there were a mess (Pidgin especially... messy code and a mess of a development team), so there is a new framework being built (telepathy/tapioca) that is being leveraged by the forthcoming gnome-default chat program (Empathy) that is working on solving this issue.

In the end, I think the true number of people who use voice/video chat are rather low.  It's just that the feature isn't available, so you hear from those people.

---

### Post by garwal on 2009-02-07
> **igknighted said:**
> The app you seek is Empathy.  All the other choices out there were a mess (Pidgin especially... messy code and a mess of a development team), so there is a new framework being built (telepathy/tapioca) that is being leveraged by the forthcoming gnome-default chat program (Empathy) that is working on solving this issue.

In the end, I think the true number of people who use voice/video chat are rather low.  It's just that the feature isn't available, so you hear from those people.

Thanks for the quick reply. I played with Empathy last night for some time and could not get audio to work. Now that I have some time to play I would like to pay forward all the time many gave me through the years. If you could point me in the proper direction I would love to help further the development of this new chat program. Again thanks for your time , your a true linux man:p
Best Wishes
Gary

---

### Post by igknighted on 2009-02-07
> **garwal said:**
> Thanks for the quick reply. I played with Empathy last night for some time and could not get audio to work. Now that I have some time to play I would like to pay forward all the time many gave me through the years. If you could point me in the proper direction I would love to help further the development of this new chat program. Again thanks for your time , your a true linux man:p
Best Wishes
Gary

I don't think it will work now, it is a very young app.  Try the very latest from Jaunty, you might have better luck.  But this is where most development in this field is at the moment, so check back often.

EDIT: The telepathy framework is the core of the project, see their page here: [http://telepathy.freedesktop.org/wiki/](http://telepathy.freedesktop.org/wiki/)

---

### Post by diablo75 on 2009-02-07
If I were having problems with recording audio, here's what I'd do.  (This is assuming your source of audio is from a standard microphone, and not through a mic that is built into a webcam... separate steps needed for that...).

Anyway, if you have a regular mic, do the following:

Double-click on the sound level icon in the right part of the upper panel (looks like a little speaker).  A volume control panel will appear.  Click on the Preferences button.  In here you will find several unchecked potential audio inputs and outputs.  To make matters simple, just check them all off and click OK.

This will expand your audio panel and probably add a few tabs, hopefully producing one that is called "Capture".  I can't get much more specific than this, but what you are looking for are recording levels that need to be turned up and enabled.  It might take a little trial and error.

---

### Post by MikeTheC on 2009-02-07
All I have to offer is my opinion.

My guess is that most people out there who do online chatting aren't, for whatever reason, pushing to have voice chat. I just don't think it's that much of a "killer app". Sure, you see it used heavily in MMORPGs, but outside of that? Well...

Now I know *this* isn't going to make you particularly happy (in the sense of being satisfied), but if you really want to see what group of users out there is the one most "into" (relatively speaking, at least) non-text chat, it's Mac users using iChat. It appeals to that group, at least in part because Apple has presented it well.

In contrast, a platform "of and by" its users (i.e. Linux) by definition is the best possible (if not perfect) representation of the will of the user community, so if non-text chat is not particularly developed or used in Linux, it's probably a fair assessment that most Linux users have no need of nor desire for it.

I hope Empathy, or somesuch other application as recommended by igknighted or someone else fits the bill for you. I know exactly what it's like to have an itch you can't scratch.

---

### Post by HermanAB on 2009-02-07
Skype pretty much has the voice market cornered and it works pretty damn good and is cross platform.  With 8 to 12 million users online at any one time, it is also immensely popular.

Cheers,

Herman

---

### Post by Ripose on 2009-02-07
You could always try WINE along with the Windows version of a voice app.

---

### Post by garwal on 2009-02-07
Thanks for all the help. I got a smile or two. Been using Skype for years and yes it does well but not all want to use it. A cross platform program is long over due. And I hope it will be addressed soon. It just be me looking to make my disto perfect for me:p that itch you can not scratch as you put it.Oh well one thing I found is that usual bunch of Linux Heads willing to offer help. I thank each of you and this is just one reason I have always used Linux.
Gary

---

### Post by leonardo_neo on 2009-02-07
> **garwal said:**
> [B]Just a quick Bio first. I am a 60 year old PhD in Computer Science Retired and I have always used some flavour of Linux. No expert but have done my share of research.Now my question, If you read you will find one of the first things a windows convert is asking for is a voice chat program like Yahoo. You then see many giving advice to use the dozen or so apps that will do text chat, ie"pidgin,QuteCom,Gizmo, and all the rest. Not one of these have I had luck getting to work with voice. Yes I know Skype works great but few use this application. So I wonder why the lack- luster effort being put in to development of something that will work. I love my linux and will not switch but if anyone knows of a way to have voice on one of the dozen chat applications I would be glad to write a step by step of how to set it up and make it clear for everyone. Lets see if we can come together and solve this problem. 
Thanks
Gary;)[/B]

I agree with you. I feel to say that most people don't 'want' voice chat, that is why it is not yet developed in Linux platform, is a false belief.

Why wouldn't someone want to have voice chat along with text chat?? Why wouldn't someone want to have video conferencing features?

Well, I believe most of the Linux users like me want to have these features, but they don't know how to do this, as they are not developers.

---

### Post by HermanAB on 2009-02-07
By the way, since you are a Comp Sci and possibly retired, why don't you write a voice chat program?  Seriously - please write one!

Cheers,

Herman

---

### Post by Kellemora on 2009-02-07
HI Gary

Gary here too!

FWIW:  I've only been using Ubuntu now since late August 2008 and have been looking for a simple text only program similar to RealPopUp on the Doze......

Over 20 different programs have been suggested, but not a single one did what I wanted.  Unless I established a full blown server to handle it.  Way overkill for the simplicity I was looking for!

As GREAT as Ubuntu is, it is very lacking in most common usage items.  Like the ability to make the center mouse button do a BACK when in a browser.  No support for 120 key keyboards!

I know most hardware devices are supported by 3rd party vendors, and done so without any help from the manufacturers themselves.
But it's really surprising to find some of the top selling devices have no drivers at all.

I think it's GREAT that some guru's spend the time to develop drivers and the like, and some of those drivers work better and have more features than the OEM drivers for the DOZE, but in almost all cases, some MOST IMPORTANT functionality was overlooked.

I'm 61 years old and am seriously trying to learn enough about things so that maybe I could even do simple scripting.  But programming, although I did well in BASIC back in the early 1980's.  Technology passed me by like a speeding locomotive!

I do feel that UBUNTU IS the Shot in the Arm that Linux needed to make manufacturers sit up and take note.  Gates disaster, the ultimate spyware OS named Vista was another shot in the arm for folks to look to LINUX!

But, unfortunately, at the present time, in order to use Ubuntu successfully, one NEEDS a Windows box to handle it's shortfalls.
Like something as simple as changing the toner cartridge in a laser printer.  That feature was omitted from the excellent otherwise printer driver.  And the new 64 bit version of Ubuntu REQUIRES the 32 bit version to see files IT cannot see!  Crazy!

But, Ubuntu is growing FAST and most of the things we need are either in the works are already out here in beta form to try!
So it's just a matter of hoping Ubuntu perks up before Windows7 recaptures the poor blokes who tried Vista and got burned bad enough to look to Linux for something WORTHY to put into their computers.

TTUL
Gary

---

### Post by majoorpa on 2009-03-26
I have to quite disagree with some of the opinions aired. There are several people who would like to have voice chat. The significance of hearing the voice of your loved ones is important to several people. May be the majority of linux users would like text clients ( ?similar to scripting ). However there a large chunk of people who prefers voice chat.

I feel that is the only area which linux needs to conquer. As a desktop it is very mature and can be used by masses. It is the only reason why I have to return to other OS very frequently. The current software most talked about is skype and empathy. Skype is fine but is not universal as it is blocked by several ISPs. Empathy could have filled that gap if it was more stable and functions for a newbie like me.

I appreciate the efforts of Gary to fill that gap and thanking him for the same.

---

### Post by markbuntu on 2009-03-26
People complain about free beer too.

---

### Post by sidewinder12s on 2009-03-26
Yes, It would be great if we could get a Program like Pidgin that would cover AIM, Messenger, Skype, and the sort for Voice/Video chat. Im An exchange student in Argentina right now that just installed Ubuntu on my Laptop because i like tinkering with the settings and OP and Windows was Boring me. And I have also Hosted many Students in the US from Abroad, And talking with them in Voice chat is great and its also great for talking with my family. Its just good to see the ones your talking to, and i hope they get something done with this, along with a lot of the shortcomings that Ubuntu has that force one to Keep Windows on there system for. For one i cant get my Wireless to work, and i dont know if its the Drivers or the Networking Software that comes with Ubuntu. But i still need to try whatever it is everyone talks about in the Wireless Forum. I really like this OP and i hope it picks up more Support

Geoff

---

### Post by Son of William on 2009-03-26
> **MikeTheC said:**
> 
. . .

In contrast, a platform "of and by" its users (i.e. Linux) by definition is the best possible (if not perfect) representation of the will of the user community, so if non-text chat is not particularly developed or used in Linux, it's probably a fair assessment that most Linux users have no need of nor desire for it.



I don't think that is a fair statement.  If an app is not available it is not because most Linux users have no need of nor desire for it - it is because those willing and able to write the app have not yet done so (and may never do it).

For example, I would love it if the latest computer games would run under Linux but my need or desire is immaterial - I don't write the games and I lack the technical skill to make them run under Linux.

I am not complaining - beggars can't be choosers as they say.  But don't discount Garwal's concerns and desires.

---

### Post by misswham on 2009-03-26
well i have yahoo and i have yahoo voice in and voice out.  I have a phone number that will call land lines and cells.  I pay for this service and never get to use it since i have switched to linux because it only works with yahoo.  the same with webcams also.  So i do think that there are a lot of people who are interested in this feature or these features, they just arent available because anyone who uses yahoo inst messenger misses it totally because i do.  when i need to make a call from there i have to log off of here and log onto windows. If i had that feature and my blackberry synced with ubuntu outlook, i would ditch windows all together,

---

### Post by lykwydchykyn on 2009-03-27
Please keep in mind, many of these protocols are proprietary.  If you want to use yahoo instant messanger with voice, instead of questioning why pidgin/empathy/et al haven't implemented it, ask why Yahoo hasn't bothered releasing a full-featured version of their chat client for Linux, or why they haven't released protocol information to these devs.  

Kopete apparently has "experimental support" of Jabber/Google talk voice chat.  Maybe that's worth a look.  Ubuntu users have a nasty habit of forgetting about KDE applications. ;-)

---

### Post by egalvan on 2009-03-27
> **Son of William said:**
> I don't think that is a fair statement.
  If an app is not available it is not because most Linux users have no need of nor desire for it - it is because those **willing and able **to write the app have not yet done so (and may never do it).

For example, I would love it if the latest computer games would run under Linux but my need or desire is immaterial -
 I don't write the games and I lack the technical skill to make them run under Linux.

I am not complaining - beggars can't be choosers as they say.
  But don't discount Garwal's concerns and desires.

Folks who are "willling and able" are usuyally driven by some NEED..
if no-one needs the app, why write it?

OSS/FOSS is "scratch an itch"...

As for games, it also brings in a matter of resources...
Simpler games, such as the original Doom, can be written by one person, or a very small team... ( as indeed Doom was )
but such games are no longer the type to be asked for by the game-playing masses..

everyone wants the latest-and-greatest in graphics and sound,
and such games take far more man-power to create, write and debug...
Such teams nowadays number in the 50-100 range.
While it IS possible to get that many OSS/FOSS writers interested in a game project, the odds are low.
This would more than likely have to be a $$-based venture...
And too many games houses don't see a sufficient return-on-investment in the Linux market.
And don't forget, that sometimes access to some hardware/software information needed to properly code such software is at times limited with NDA's (Non-Disclosure Agreements... anathema to most OSS/FOSS authors)

Yes, I purchased the Linux versions of Quake...
and I liked how they ran faster and more stabler than the MS-Windows versions.

And I think most folks are actually thinking "phone app" when thinking of "voice chat".
Realistically, how many simultaneous participants are possible when talking and listening?
Three? Four? Maybe Five?

Whereas while typing and reading, twenty is not an unusually high number.

---

### Post by 3rdalbum on 2009-03-27
> **Kellemora said:**
> And the new 64 bit version of Ubuntu REQUIRES the 32 bit version to see files IT cannot see!  Crazy!

It would be crazy, except that I don't know what you mean and I suspect you might be misunderstanding some other sort of problem.

Acer did actually write a Vv-capable instant messenging client for its Aspire One. Unfortunately for various reasons I haven't managed to extract it from Linpus Lite and run it on my desktop:

1. It's been built not to work on 64-bit, and that's what I use
2. The version on the Aspire One Restore CD doesn't work, and I don't still run Linpus Lite so I can't get an updated version.
3. It requires strange versions of libraries that I'd have to copy across too.

Acer has kept it proprietary too, despite using libpurple. If only they'd open-sourced it, then we'd have a Vv messenger.

If you have a compatible webcam you could try Meebo.com. But in my experience, Vv over IM networks has been merely a gimmick that few people use more than once or twice. The people who are serious about videoconferencing are on Skype, which is an excellent program for Windows, Mac and Linux as well as embedded platforms.

---

