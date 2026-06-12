---
title: "trying to setup a TOGGLE between English and Korean"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by phubert28 on 2010-05-20
I've recently installed 64 bit 10.4 following my WinXP SP3 TANKING.

**I am TRYING to study Korean and later Japanese and need to TOGGLE between those languages and English for text input.**

KNOWING the difference, I nevertheless managed to set my SYSTEM menus to Korean ... quite unintentionally.

Banging around blindly I followed one Google search match on my problem to a suggestion that I UNINSTALL Korean, et al, language support and would then DEFAULT to English.

NOW, however, under **Installed Languages**, the first part of the list (Asturian Berber, Bokmal, Chattisgarhi, Chinese, Occitan, Pedi, Shuswap, Sichuan) is in English. The remainder of the list of languages is apparently in a combination of Japanese and Korean. And under **Language & Text**, I have a long list of English variants (I ONLY need United States), along with Chinese (Singapore), and what appear to be two choices for Korean (in Korean (Hangul and Hanji) and one choice for Japanese in Japanese.

Seems I've royally messed this up...
[B]
#1 is there any way back without completely reinstalling Ubuntu?[/B]
#2 IS there any way to TOGGLE between input languages for TEXT input in ANY program? (already posted this elsewhere, tho I may not have stated it well!!)

Any ideas????

---

### Post by BandD on 2010-05-20
Ok, when you go to System --> Administration --> Language Support are "English (United States)" and "English" in bold?  With a longer list of English variants in gray?  If so, that's exactly how it's supposed to be.

There is no need to unistall Korean at this point (unless you already have).  Try logging out.  Once you get to the log-in screen there should be an option at the bottom task bar to select the session language.  You should be able to select English.

The good news is there is a very easy way to enable the "language toggle" you're looking for.  I'll explain after we get English set as the default again.

---

### Post by phubert28 on 2010-05-20
I had already followed instructions arrived at via a Google search suggesting uninstalling the offending languages and did so and rebooted.

Yes, English (United States) and English are bolded now.

I have SCIM set as the input method.

However, I have a number of icons I've added to the launch bar and, among those, when I MOUSEOVER Firefox, Thunderbird and OO Write I see either English and Korean or ALL Korean still.

That isn't causing any problems, but it IS _strange_.

**

After another reboot, and another look, this is what characters I see displayed with mouseover on the following icons on the launch bar:

Firefox: English and Korean
Thunderbird: English and Japanese
OO Write: Korean only

I am reporting this ONLY as a symptom (of what, I don't know).

The list raised by Install/Remove languages is still a mess with a mix of English, Japanese and Korean describing the entries. Many entries are described only in what appears to be a Japanese-Korean mix.

---

### Post by phubert28 on 2010-05-21
As to setting English as the default, let me provide some more examples.

First, all PRIMARY selections in menus are now English.

However, under System > Preferences,

Anthy is in English and Japanese
SCIM is English and Korean

Under Applications,

The first entry (whatever it is) under Graphics is Korean only
The first entry under Internet is also entirely in Korean, though mouseover pops up in English "Download and share files over BitTorrent"
The first four entries under Office are entirely in Korean
And the last entry, glabels, has "glabels' in English but the moseover and suffix in the menu in Korean.

Have any idea how I can get out of this mess???

---

### Post by BandD on 2010-05-21
This is really strange.  

Let me make sure I understand what you have already done.  When you go to System --> Administration --> Language Support, then click on "Install/Remove Languages" is there a check mark/gray box next to "English" only?  Or are there check marks/gray boxes next to "English" "Korean" and "Japanese" at this point?  If "Korean" and "Japanese" do have check marks/gray boxes next to them, click on each one and at the bottom of the window try unchecking the "translations" box (if it's checked).  I think you want to have only the "Input Methods" and "Extra Fonts" boxes checked for both Korean and Japanese.

Also you can delete SCIM.  It's outdated and not supported anymore.  I'll explain the replacement once we can figure out how to get the language stuff all worked out.

---

### Post by phubert28 on 2010-05-21
Under Installed Languages, there is a box checked next to the top entry, BUT the first 30 or so entries are displayed in Korean.

No other boxes in the list are checked.

The only entries in the list DISPLAYED in English are

Asturian\;Bable; Leonese; Asturleonese
Berber languages
Bokmal, Norwegian; Norwegian Bokmal
Chhattisgarhi
Chinese, Min Nan
Chinese (simplified)
Chinese (traditional)
Occitan (post 1500)
Pedi; Sepedi; Northern Sotho
Shuswap
Sichuan Yi; Nuosu

The remainder of the list is displayed in what appears to be Kanji with the same Korean suffix on every line.

:)

---

### Post by phubert28 on 2010-05-21
I'm afraid I've Googled for answers/directions and one set I ran into instructed me to install SCIM for the language support I was looking for.  So, I UNINSTALL SCIM, then?

I see ONE of the menu items that was messed-up was anthy and that is in Synaptic as scim-anthy - I'm marking ALL that for complete removal now.

---

### Post by phubert28 on 2010-05-21
Removing SCIM & scim-anthy, and rebooting, however, did not help the menu situation.

Everything I described below remains as I described it.

**

ooops. One MORE item "scim-bridge"!!

Will address that now.

mmmm.... now I'm puzzled.

Under System ?> Administration > Language support > Language & Text

in the box for "Keyboard input method system"

#1 no default is set
#2 the list CONTAINS scim-bridge

However, under Synaptic, I see no remaining scim modules installed...

---

### Post by BandD on 2010-05-21
Have you tried logging out.  Then once you click on your user name at the log in screen, there is an option at the bottom of the screen to select the system language.  Can you set that to English and log in? Does that help?

Do you remember what guide you used that caused everything to go haywire?  If so, can you post the link here?

---

### Post by phubert28 on 2010-05-21
Yes, I kept forgetting that.
However, when I just TRIED it, the language LIST was in Korean.
I picked whatever was at the top and still everything is unchanged.
Reinstall Ubuntu, perhaps???

**

I AM wondering why those specific things (the Thunderbird, Firefox and OO Write icons, and the Applications and System menu entries specified as well as the Installed Languages LIST, but for the noted exceptions) are affected.

**

Turns out I may have made things a little worse.

NOW, under "Places" five folders the mouseover identifies as beginning with /home/Paul are in Korean... and are displayed in Korean in the File Browser as well...

But, on login, since the LIST I was choosing from was in Korean, I really don't have any idea WHAT I was choosing... I ASSUMED English would be at the top!

And, in the dialogue about changing labels that followed, I told it to go ahead ... bad idea, I guess.

---

### Post by BandD on 2010-05-21
How many choices do you have in the log in list?  Maybe try them all just to see...

---

### Post by BandD on 2010-05-21
When you go to Language Spport under the Language tab in the "Language for Menus and Windows" section is "English (United States)" listed first?  If not,then drag it to the top of the list and then press the "Apply System Wide" button.  You may have to log out and back in to see if it affeccted anything...

---

### Post by BandD on 2010-05-21
you could also try this out [https://help.ubuntu.com/community/LocaleConf]("https://help.ubuntu.com/community/LocaleConf")  

It might give us some info.  Can you post the results of ```
locale
``` run in a terminal?

---

### Post by phubert28 on 2010-05-21
Yes, English (United States) and English are the first two and the only ones not grayed-out.

This has been true for several reboots.

Earlier, trying to GET Korean and Japanese support, I dragged THEM BETWEEN English US and English... they do not appear there now, but I suppose that could have been ONE of the steps that got me into the trouble I'm in.

---

### Post by phubert28 on 2010-05-21
Interesting

paul@Aragorn:~$ locale
LANG=en_GB.utf8
LANGUAGE=en_US:ko:ko_KR:ja:en
LC_CTYPE="en_GB.utf8"
LC_NUMERIC="en_GB.utf8"
LC_TIME="en_GB.utf8"
LC_COLLATE="en_GB.utf8"
LC_MONETARY="en_GB.utf8"
LC_MESSAGES="en_GB.utf8"
LC_PAPER="en_GB.utf8"
LC_NAME="en_GB.utf8"
LC_ADDRESS="en_GB.utf8"
LC_TELEPHONE="en_GB.utf8"
LC_MEASUREMENT="en_GB.utf8"
LC_IDENTIFICATION="en_GB.utf8"
LC_ALL=
paul@Aragorn:~$

**

I've been wondering if there might be terminal command that could get me out of this!

---

### Post by phubert28 on 2010-05-21
the only problem with localepurge is that I couldn't see how to SELECT entries in the interface... it didn't support mouse clicks - I saw en-US and en-US-utf8 (or somesuch) and assumed en-US would be adequate, but wasn't able to put a check in the box!

**

O.K. THIS time logging-in, I specified "unspecified ANSI" for the language and at least my Places labels are now back to English... tho everything else discussed remains as it was.

TYPE under the File browser list is in Korean... but it may have been that way since I got into this... hadn't looked there.

Folder names are back to English tho..

**

However, AFTER logging-out and logging-in again, when I try to run localpurge:

sudo apt-get install localepurge

I now get:

paul@Aragorn:~$ sudo apt-get install localepurge
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
paul@Aragorn:~$

**

Have to do some real world errands & appointments - is there such a thing as a non-destructive Ubuntu reinstall???

---

### Post by BandD on 2010-05-21
use the space key to select the locales (languages) you want to keep.  So select "en" and "en_US" and "en_US.utf8" and no others.

---

### Post by phubert28 on 2010-05-21
Thanks for that, but now locales won't run, as you see from my other response... locked resources - AFTER a logout - another reboot needed, perhaps? (will do that now (glad Ubuntu is so much faster than WIN!!!))

**

O.K. apparently my abrupt termination of LOCALES caused the lock... didn't see it under processes or I would have killed it...

**

The next step was sudo apt-get autoremove 

THAT is taking time.

---

### Post by BandD on 2010-05-21
I had the same problem becuase I forced the terminal to close while localepurge was still running.  A reboot seemed to fix it.  So reboot then run ```
sudo apt-get install localepurge
``` again and select the "en" and "en_US.utf8" locales using then spacebar and then hit enter.  Reboot and see if everything is fixed.

Then maybe we can work on getting Korean and Japanese installed the RIGHT way! :)

---

### Post by phubert28 on 2010-05-21
#1 - THANK YOU for all the help
#2 - I really DO need to get to other things or my wife will not be happy!
#3 - did as you suggested, but problem remains
#4 - probably will reinstall Ubuntu if it won't blast the apps I've installed & configured

---

### Post by BandD on 2010-05-21
I totally understand.  When  you get a second can you post the output of "locale" run  in a teminal again?  Just out of curiosity...

---

### Post by phubert28 on 2010-05-21
paul@Aragorn:~$ locale
LANG=C
LANGUAGE=en_US:ko:ko_KR:ja:en
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=
paul@Aragorn:~$

But, any tips/comments/info on the reinstall fallback????

This is only my 2nd install of ANY Ubuntu and only my first serious attempt to USE it.

And, unfortunately, I didn't specify 'custom' for partitioning or I'd have made better use of my 2 hard drives, I suspect (MOST oddly, Dell wouldn't PERMIT me to order a 2nd 320GB drive with the Optiplex 360 ... my only option was a 160 ... weird...)

I could use Partition Magic BEFORE I reinstall... LOOKS like I ended up with a huge "lost & found" ?????

---

### Post by sgosnell on 2010-05-21
Just to be didactic, Hangul, the Korean language, does not use kanji, it's a separate alphabet.  Korean uses an alphabet, although it doesn't use Roman letters.

You can't run two instances of apt at the same time.  Synaptic, aptitude, apt-get, update manager, and dpkg are all different versions of this, and you can only run one at a time, to prevent getting wild confusion by installing things over the top of other things.  Each program writes a lock file, and it's possible to have the lock remain in place if you kill the program without warning.  

As to your language problem, I have never seen that, and I really don't know where to start.  Good luck with it, and please post the solution here when you find one, so others can benefit.

---

### Post by phubert28 on 2010-05-21
O.K. I looked for "yeomeo" (can't type the Korean) and found no match - the ONLY language that supposedly was installed.

Since I found no match, I uninstalled it. THAT fixed my "Installed languages" list display - only it left me with ONLY Chinese TO select.

So, I went to languages and chose English and began THAT install as apparently I had UNINSTALLED English!

I might be on my way to fixing everything!!! (tho not on my way (yet) to installing Korean and Japanese and setting up the toggle solution you said you knew of)

---

### Post by phubert28 on 2010-05-21
Yes, I know Korean doesn't use Kanji - there IS Sino-Korean, however.

Still, what I saw looked like Kanji - hence Japanese.

---

### Post by phubert28 on 2010-05-21
O.K. NOW the Installed Languages LIST is fixed, as are the login choices (sort-of)

However, the MENU issues for Applications > 

Graphics
Internet
Office

And the icons for Tbird, FF, and OO Write

remain unchanged.

Latest locale is as follows"

paul@Aragorn:~$ locale
LANG=en_US.utf8
LANGUAGE=en_US:ko:ko_KR:ja:en
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=
paul@Aragorn:~$

the LANGUAGE=, of course, is the most interesting.

---

### Post by BandD on 2010-05-21
One last try.  

Enter this in a terminal and past the output here: ```
gedit /etc/default/locale
```

as well as this: ```
gedit /var/lib/locales/supported.d
```

The re-install method will wipe everything.  I've read about ways to make backups of the programs you have installed, but I don't recall where or how.  If it comes to that it would probably be worth starting a new thread and ask how you go about doing that.

---

### Post by phubert28 on 2010-05-21
/etc/default/locale is:

LANG="en_US.utf8"
LANGUAGE="en_US:ko:ko_KR:ja:en"


What we might have expected, I think... but of course I didn't know about this file.

Question is: how do I modify it without screwing it up??? :)

***

But, supported.d is a directory!

The dir contains:

en
local

local is:
en_US.UTF-8 UTF-8

en is:

paul@Aragorn:/var/lib/locales/supported.d$ cat en
en_HK.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_IN UTF-8
en_ZW.UTF-8 UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_NG UTF-8
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_SG.UTF-8 UTF-8
en_BW.UTF-8 UTF-8
en_AG UTF-8
en_ZA.UTF-8 UTF-8
en_CA.UTF-8 UTF-8
en_IE.UTF-8 UTF-8
paul@Aragorn:/var/lib/locales/supported.d$ 


(golly, coulda been using cat rather than gedit!)

---

### Post by BandD on 2010-05-21
Ok is that /etc/default/locale?  

We'll back it up first ```
sudo cp /etc/default/locale /etc/defualt/locale.backup
```

Then we'll edit the file to (hopefully) fix all this nonsense. ```
sudo gedit /etc/default/locale
```

When the text editor opens erase everything and replace it with ```
LANG="en_US.UTF-8"
``` and click save.

Log out and log back in.  If that doesn't work, restart.  I'll keep my fingers crossed...


*Sorry about the cat thing.  I feel like a dope now.  I always forget about it for some dumb reason!

---

### Post by phubert28 on 2010-05-21
Well, I had already made the following change and rebooted:

paul@Aragorn:~$ cd /etc/default
paul@Aragorn:/etc/default$ cat locale
LANG="en_US.utf8"
LANGUAGE="en_US"
paul@Aragorn:/etc/default$ 

Looked like the language SELECTION on login was now correct, but the menus persist... dunno how Korean and Japanese got stuck in Applications! ...AND in the File System "Type" field!

As you can tell, I'm not big on backups :(

Tho apparently it did no HARM.

**

I thought install  didn't disturb the user's stuff (/home mount point)

---

### Post by sgosnell on 2010-05-21
Yes, I was thinking that cat would be quicker and easier than gedit, because you have to use sudo in order to modify the files.

Try this, from the man page for update-locale:
```
 sudo update-locale LANG=en_US.UTF-8 LANGUAGE 
```
That should set LANG to en_CA.UTF-8 and remove definitions for LANGUAGE.

From [Ubuntu man pages](http://manpages.ubuntu.com/manpages/hardy/man8/update-locale.8.html).

---

### Post by BandD on 2010-05-21
If you go into synaptic and type in "language-pack-ko" or "language-pack-ja" is anything installed?

---

### Post by phubert28 on 2010-05-21
Well, I see a problem.

I ran the command, but this is the result:

paul@Aragorn:~$ cd /etc/default
paul@Aragorn:/etc/default$ cat locale
LANG="en_US.utf8"
LANGUAGE="en_US"
paul@Aragorn:/etc/default$ sudo update-locale LANG=en_US.UTF-8 LANGUAGE
[sudo] password for paul: 
paul@Aragorn:/etc/default$ locale
LANG=en_US.utf8
LANGUAGE=en_US:ko:ko_KR:ja:en
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=
paul@Aragorn:/etc/default$ 


I wonder if I need to enter the en_US WHERE ko:ko_KR:ja: are now seen 

thus:

LANGUAGE="en_US:en"

You may not have caught it, but earlier I mentioned that I DRAGGED the two Korean entries in the Installed Languages List, along with Japanese, BETWEEN English US and English on the list... THAT is what we seem to be seeing in the LOCALES output.

---

### Post by BandD on 2010-05-21
That's a really good idea, give it a go.  But is seems really strange to me that running the update-locale command reverted back to the ko and ja settings...

---

### Post by phubert28 on 2010-05-21
nope - apparently nothing but English - dunno where it's getting its FONTS from :?

---

### Post by sgosnell on 2010-05-21
Strange.  That should have cleared the LANGUAGE variable.  Try ```
sudo  update-locale --reset LANG=en_US.UTF-8 LANGUAGE 
``` That is supposed to clear out all variables not set on the command line.

---

### Post by phubert28 on 2010-05-21
Yes the MYSTERY is just WHERE it's getting this setting.

Simply DRAGGING those languages between English US and English in the Language for menus and windows list appears to have caused all the problem... but the list NOW doesn't SHOW that.

---

### Post by BandD on 2010-05-21
how about searching for "hangul"

---

### Post by phubert28 on 2010-05-21
Nice try (at least copy & paste is cool)

Trying the edit I suggested to locale

---

### Post by phubert28 on 2010-05-21
searching? how, where?

But I'm going to reboot first after that edit to locale...

---

### Post by BandD on 2010-05-21
searching synapic

---

### Post by phubert28 on 2010-05-21
Well, my suggestion to about the edit to locale worked!

NOW can we talk about getting Korean and Japanese back and how to TOGGLE?

:GRIN:

gotta go again, tho: appointment!!!!!

THANKS AGAIN, tho!!!!

Glad a reinstall wasn't needed!

---

### Post by sgosnell on 2010-05-21
Reinstalls are seldom necessary.

---

### Post by phubert28 on 2010-05-21
I know - gotta get that Windows infection out of my head!

This one was interesting, though!

---

### Post by BandD on 2010-05-21
AWESOME!  It was kinda fun trying to track this down.  I'm glad it worked out!  Here's how to enable Korean and Japanese the RIGHT way! :)

Go to System --> Administration --> Language Support.  Click on Install/Remove Languages.  Select Japanese (in the bottom check only "input methods" and "extra fonts") and Korean (again in the bottom check only "input methods" and "extra fonts").  Click Apply changes.

After the packages install, in the Language Support window under "Keyboard input mehtod system" drop down menu select "ibus".  Close the Language Support window.

Then go to System --> Preferences --> ibus preferences. Select the "input method" tab.  Click on the "Select an input method" drop down menu and select Korean (I don't really know much about Korean, but I'm guessing you'll want the han2 one). Then click "add".  If, after English, you'll use Korean the most use the up button to move it up to the top of the list.  Then click the "Select an input method" drop down again and select Japanese (I prefer the anthy one, the 1st option).  Click add and move it up to the 2nd posistion (if you'll use Japanese less than Korean, otherwise put it at the top of the list).

Click back to the "General" tab and note the "Keyboard Shortcuts" and see if they suit your needs.  Note that you can only activate ibus when a text field is active.  So use gedit or openoffice or firefox or some such to test.  If ibus is disabled English will be the default.  The default key binding to enable is ctrl+space this will bring up the language first on the "input method" tab list.  To get to the next language on the list the defualt is (I think) alt+Left Shift.  This will be your TOGGLE.

Let me know how it goes!

---

### Post by phubert28 on 2010-05-21
So, you're saying DON'T select Translations?????

Under Installed Languages (TO install) I now ONLY see JUST "Korean" and "Japanese" as choices for those languages.

---

### Post by BandD on 2010-05-21
If you just want to be able to type in Korean and Japanese and you don't want to have your desktop (menus etc.) in Japanese or Korean at any time.  Then DON'T install translations.

If you do input methods and extra fonts you will be able to type in both languages.

---

### Post by phubert28 on 2010-05-21
Under IBus Preferences, General tab,

Enable or disable shows Control + space; Zenkak

Have any idea what that "Zenkak" is???
Something to be ignored, perhaps??

Finished your list, tho, BandD, and it looks GREAT.

Now the only question is how to set the FONT for Korean (and Japanese) along with Font SIZE...

Tried changing the default (Sans) font size and that didn't appear to make a difference in the Korean... just changing font size in OO Write works fine, tho... so I guess no problem!

Again, thanks much!!!!

So, how does this thread get set to "Solved"??

---

### Post by BandD on 2010-05-21
To mark it as solved go to the top ot the thread and click on "Thread Tools" and you should see it. 

As for changing the defualt system font for Korean (or Japanese) I'm not really sure.  In oo.org you should be able to scroll through the fonts and find some that are Korean and some that are Japanese.  I can't remember the Japanese ones off the top of my head and I'm not on my home computer...

---

### Post by phubert28 on 2010-05-21
I don't have a problem with the font - only the size - and solved that - though not for gedit - not that this is a problem.

It's getting easier and easier to like Ubuntu :-D

---

### Post by sgosnell on 2010-05-21
In gedit, open Edit/Preferences, and on the Fonts & Colors tab, uncheck the box to use system fonts and put in whatever you like.  You can also change the default font size globally from the desktop view, by right-clicking and selecting Change Desktop Background, then selecting the Fonts tab, and setting whatever font sizes you want.

---

### Post by phubert28 on 2010-05-21
More good stuff for the newbie - thanks!

Just received my Ubuntu Pocket Guide and Reference, too!

When on mainframes in the early 70's, I DID _read_ the manuals, assiduously! Time to start doing it again, I expect.

For now, at least, I'm putting all my 'how-tos' in Tomboy notes...

---

### Post by sgosnell on 2010-05-22
Back then, you had to read the manuals, there was no other way.  No internet, no nothing.  I remember that my university had a computer.  One.  It had its own building, and when the West Texas wind got up, programs could get scattered as the punch cards blew across the campus.  You only let that happen once.

---

### Post by phubert28 on 2010-05-22
So much for that "pocket guide" ... seems I'm not THAT much of a newbie! :D

True about then vs. now... all in all, I liked then better ... but I had full access to a room full of mainframes! Techie/programmer (Assembly language only)

The bad part, tho, was that there was little means available to SHARE code you'd developed... a great pity. So much more could have been accomplished.

---

### Post by sgosnell on 2010-05-22
Looking back, the good old days weren't all that good.  I'll take now.

---

### Post by phubert28 on 2010-05-22
A portion of mine were VERY good - absolute freedom, developed what *I* wanted, had lines of people asking for MY help (and I provided it) - I was jazzed. But platforms went obsolete and work environment soured as management pursued 'upward mobility' by lowering standards - BAD move.

Naturally, they failed to realize that they could have real upward mobility AND high standards... if they were willing to let the right people do the work of implementing it.

---

### Post by a-guy-in-japan on 2010-05-23
To BandD: 
You have my sincere gratitude for providing those excellent instructions! I'm a new Ubuntu user and was worried the process would be much harder.

I will be happy to pass the info along to anyone it can helpO:)

&#12393;&#12358;&#12418;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#65281;&#12288;(Thank you VERY much!) :P

---

### Post by BandD on 2010-05-23
&#12393;&#12356;&#12383;&#12375;&#12414;&#12375;&#12390;&#65281;&#12288;&#12288;Ubuntu&#12288;&#12408;&#12288;&#12424;&#12358;&#12371;&#12381;&#65281;

---

