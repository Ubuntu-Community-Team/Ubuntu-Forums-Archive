---
title: "thunderbird 3.0"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by DarinB on 2010-02-04
stupid thunderbird keeps on crashing. 
a big problem when i write an important biz email that disappears. 
Any body know what is up with this new release. 
2.0 was a steady as a rock. 
this one is pure crap???

---

### Post by Tholley on 2010-02-04
I haven't updated to 3.0 yet... maybe I'll wait awhile... ;)
 
sorry... wish I could tell ya something....

---

### Post by porchrat on 2010-02-04
Must admit I don't enjoy 3.0.

That autodetect thing with the incoming and outgoing servers drives me nuts.

---

### Post by kellemes on 2010-02-04
Never had problems with TB3, currently using TB(3.0.2pre) without issues.

---

### Post by coolbrook on 2010-02-04
Have you tried running it from terminal?  Perhaps that will shed some light on the problem at the point of impact.

---

### Post by Silvertones on 2010-02-04
I've been using 3.0 since it was a beta release. In windows that is. Never an issue. I've been using it in Ubuntu for a few days with no issue but here's what I did.
1. Install from Ubuntuzilla--don't run it yet
2.```
 thunderbird -ProfileManager
``` 
   Create a profile or however many you need. They will be in .thunderbird as opposed to .mozilla-thunderbird
3. Copy and paste the files that are inside the profile at .mozilla-thunderbird into the profile foler inside .thunderbird
4. open TB and you'll never know it was changed except it looks different.

---

### Post by DarinB on 2010-02-04
thats what i did, it worked great for about a month or two now i am getting slammed. must be one of the updates to some lib. who know now it works like crap

---

### Post by DarinB on 2010-02-04
would love to fix it or go back to 2.0 that thing was solid as a rock!

---

### Post by kellemes on 2010-02-04
As already said..
You can run it from terminal and watch the output.
Possible your profile is broken and you can try working from a fresh one as explained by *Silvertones*.

TB2 is in the standard repositories of Karmic and Jaunty (your profile says you're on Jaunty).
```
sudo apt-get install thunderbird
```
should do it I guess.

---

### Post by DarinB on 2010-02-04
yes it is a great idea, i have to remember to always start it from terminal so when it does crash i can get info. thanks.

---

### Post by Silvertones on 2010-02-04
As I mentioned, your profile from version 2.0 is still intact because version 3.0 doesn't migrate the old profile from version 2.0.Instead of starting fresh copy and paste from .mozilla-thunderbird to .thunderbird. It'll be the same as reverting to v2.0. You'll loose your month or two of emails and contacts. Make a copy of the profile in .thunderbird though in case that's not it.

---

### Post by DarinB on 2010-02-04
I am ready to do the .mozilla switch as above. i did copy and paste the .thunderbird 3.0 to my desktop to save it. but i have some really important emails in there any way to save them somewhere and then load them back.

---

### Post by DarinB on 2010-02-04
i opened thunderbird and firefox with terminal and why would firefox or thunderbird not crash at all for hours of trying to get it to crash.
i didn't pay attention closed firefox re-opened it with the icon from the panel and it crashed in a about a minute. ???? is some one punking me???

---

### Post by DarinB on 2010-02-04
i got something on firefox crash at least
rin@darin-desktop:~$ firefox

(firefox:25755): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/darin/.recently-used.xbel', but the parser failed: Error reading file '/home/darin/.recently-used.xbel': Is a directory.
Segmentation fault
darin@darin-desktop:~$ 

no idea what this means 
still no crash on thunderbird

---

### Post by nanotube on 2010-02-04
> **DarinB said:**
> i got something on firefox crash at least
rin@darin-desktop:~$ firefox

(firefox:25755): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/darin/.recently-used.xbel', but the parser failed: Error reading file '/home/darin/.recently-used.xbel': Is a directory.
Segmentation fault
darin@darin-desktop:~$ 

no idea what this means 
still no crash on thunderbird

well, try deleting ~/.recently-used.xbel , which apparently is a directory...

---

### Post by DarinB on 2010-02-04
where is it in my home folder? 
i also got this in my thunderbird terminal but it did not crash yet
darin@darin-desktop:~$ thunderbird

(thunderbird-bin:29686): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/darin/.recently-used.xbel', but the parser failed: Error reading file '/home/darin/.recently-used.xbel': Is a directory.
deliver mode: 0
deliver mode: 0

i guess it is the same thing.

---

### Post by DarinB on 2010-02-04
well i removed that directory or what ever it was as stated above....and i got immediate crash of thunderbird. it happens when i cut copy from a web page on the internet and paste it onto an email reply...or if i cut or copy and paste a link  that is when it crashes with one of those crash report send outs. here is a read out that i have. it went on about 20 more times but i only included two. any ideas on this one???

darin@darin-desktop:~$ thunderbird

(thunderbird-bin:31314): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(thunderbird-bin:31314): Gtk-CRITICAL **: gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed

---

### Post by DarinB on 2010-02-05
another read out...but no crash.

darin@darin-desktop:~$ thunderbird

** (soffice:12046): WARNING **: unable to get gail version number
error - missing word count in dictionary file
Hash Manager Error : 4
deliver mode: 0
deliver mode: 0
deliver mode: 0

** (soffice:13794): WARNING **: unable to get gail version number

** (soffice:13826): WARNING **: unable to get gail version number
darin@darin-desktop:~$

---

### Post by kellemes on 2010-02-05
Don't get it..
soffice? This is an errormessage from OpenOffice.

---

### Post by DarinB on 2010-02-05
I am sure those emails had attachments. It seems i also get problems with attachments. since i have been running from terminal no crashes or shut downs on either firefox or thunderbird. 
that sucks who wants an os that you have to go to terminal to open apps??????

---

### Post by DarinB on 2010-02-06
> I am ready to do the .mozilla switch as above. i did copy and paste the .thunderbird 3.0 to my desktop to save it. but i have some really important emails in there any way to save them somewhere and then load them back.

regarding this method of reverting back to 2.0 as mentioned above???

---

### Post by DarinB on 2010-02-07
another error
darin@darin-desktop:~$ firefox
Segmentation fault

no idea what to do. 
my thunderbird crashed but i didn't run it in terminal...i can't reproduce the crash in terminal. three days now. 
but if i open it not in terminal it crashes asap!!!!!
when i copy paste a link from firefox on to it using my mouse. 
i saw a post about jedit but i have no idea what that is????
HELP ready to quit ubuntu??? piece of crap!!!! 
BUT I GOT NOTHING TO GO TO THAT IS BETTER. 
I NEED TO BE ABLE TO GET OUT EMAILS FOR BUSINESS PURPOSES I CAN'T BE F*ING AROUND!!!!!!!

---

### Post by nanotube on 2010-02-07
> **DarinB said:**
> another error
darin@darin-desktop:~$ firefox
Segmentation fault

no idea what to do. 
my thunderbird crashed but i didn't run it in terminal...i can't reproduce the crash in terminal. three days now. 
but if i open it not in terminal it crashes asap!!!!!
when i copy paste a link from firefox on to it using my mouse. 
i saw a post about jedit but i have no idea what that is????
HELP ready to quit ubuntu??? piece of crap!!!! 
BUT I GOT NOTHING TO GO TO THAT IS BETTER. 
I NEED TO BE ABLE TO GET OUT EMAILS FOR BUSINESS PURPOSES I CAN'T BE F*ING AROUND!!!!!!!

well, it seems like something may be borked up with your profile... have you installed a bunch of weird addons? does the stuff still crash if you start with a fresh profile (command "firefox -P" or "thunderbird -P" to start the profile manager, and create a fresh new profile)

---

### Post by DarinB on 2010-02-07
will i lose my emails?
and is the exact code 
firefox -P 
or 
sudo firefox -P
sudo thunderbird -P

---

### Post by nanotube on 2010-02-07
> **DarinB said:**
> will i lose my emails?

no, your emails will remain in your old profile, and you can copy them over later.

> 
and is the exact code 
firefox -P 
or 
sudo firefox -P
sudo thunderbird -P

no sudo - just plain 'firefox -P' or 'thunderbird -P'. 

as a general rule - never run a gui application with sudo, it can mess up the ownership of your user files. if you need to run a gui app as root, use 'gksudo' instead. (in this case, you don't need any sudo at all.)

---

### Post by DarinB on 2010-02-07
i did the one for firefox but a gui did not open to create a new profile for thunderbird it did, therefore i have to recreate all the accounts i have about 5 email accounts and  8 inbox folders with filters. its is a bit of a job to recreate everything...how do i copy over the emails???

---

### Post by nanotube on 2010-02-07
> **DarinB said:**
> i did the one for firefox but a gui did not open

are you sure you didn't have firefox already opened somewhere before you did that?

>  to create a new profile for thunderbird it did, therefore i have to recreate all the accounts i have about 5 email accounts and  8 inbox folders with filters. its is a bit of a job to recreate everything...how do i copy over the emails???

all the mail is stored in the "Mail" subdirectory of your thunderbird profile, and if you have any imap accounts, that's in "ImapMail". your user account setups are in prefs.js.

for more detailed writeup about migrating a profile, see here:
[http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location#Create_a_new_profile_and_migrate_your_old_data](http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location#Create_a_new_profile_and_migrate_your_old_data)

---

### Post by DarinB on 2010-02-08
> As I mentioned, your profile from version 2.0 is still intact because version 3.0 doesn't migrate the old profile from version 2.0.Instead of starting fresh copy and paste from .mozilla-thunderbird to .thunderbird. It'll be the same as reverting to v2.0. You'll loose your month or two of emails and contacts. Make a copy of the profile in .thunderbird though in case that's not it.


what parts of the profile are the emails, the accounts so i can be sure to keep those when i do this downgrade????

i am thinking of setting up a new profile and downgrading that one. to see if everything works. Is this possible???

---

### Post by SecretCode on 2010-02-09
> **DarinB said:**
> what parts of the profile are the emails, the accounts so i can be sure to keep those when i do this downgrade????

By default they will be in a folder like
/home/username/.mozilla-thunderbird/8randomchrs.default/Mail/

With separate subfolders for each mail account, and a number of files within each folder - back up all of them.

---

### Post by DarinB on 2010-02-09
i made a new profile as suggested, i copied over the mail folder cache, abook.mab, blacklist.xml, prefs.js i had to re-enter the passwords and save them i have about 8 sub inbox folders and mail filters how do i get those. in. i am not sure if there is an easier way maybe just copy over the entire .mozilla folder and add the mail but i wont have the current sub folder emails.?????

---

### Post by DarinB on 2010-02-09
i have discovered something interesting....according to the resposes above the .mozilla-thunderbird is the 2.0 profiles and the .thunderbird is the 3.0 profiles...when i created a new profile in thunderbird 3.0 it appeared in both .mozilla-thunderbird and in .thunderbird therefore copying over the .mozilla-thunderbird into the .thunderbird lead to no change at all....all the new addons are there as well as everything else...it also still crashes. 
how can i downgrade to 2.0 and not lose my emails and accounts and sub folders and email in them???????

---

### Post by DarinB on 2010-02-10
i am really stuck with this thing profile change has not worked i removed the custom button 0.6.0.8 add ons maybe i have to log out and log back in???



Add-ons: {58D4392A-842E-11DE-B51A-C7B855D89593}:1.1.5,es-AR@dictionaries.addons.mozilla.org:1.1.1,fr@dictionaries.addons.mozilla.org:2.1,lookout@aron.rubin:1.2.10,{2ab1b709-ba03-4361-abf9-c50b964ff75d}:1.6.5,{972ce4c6-7e08-4474-a285-3208198ce6fd}:3.0
BuildID: 20091204170421
CrashTime: 1265816800
Email: [email]darinb6@optonline.net[/email]
InstallTime: 1261611646
ProductName: Thunderbird
SecondsSinceLastCrash: 622
StartupTime: 1265816617
Theme: classic/1.0
Throttleable: 1
Vendor: 
Version: 3.0

This report also contains technical information about the state of the application when it crashed.

---

### Post by DarinB on 2010-02-10
happened again no idea what to do?
Add-ons: {58D4392A-842E-11DE-B51A-C7B855D89593}:1.1.5,es-AR@dictionaries.addons.mozilla.org:1.1.1,fr@dictionaries.addons.mozilla.org:2.1,lookout@aron.rubin:1.2.10,{2ab1b709-ba03-4361-abf9-c50b964ff75d}:1.6.5,{972ce4c6-7e08-4474-a285-3208198ce6fd}:3.0
BuildID: 20091204170421
CrashTime: 1265822134
Email: [email]darinb6@optonline.net[/email]
InstallTime: 1261611646
ProductName: Thunderbird
SecondsSinceLastCrash: 5334
StartupTime: 1265822129
Theme: classic/1.0
Throttleable: 1
Vendor: 
Version: 3.0

This report also contains technical information about the state of the application when it crashed.

---

### Post by DarinB on 2010-02-11
I am eliminating each add on one by one if i get a crash i remove the next one and see if it stops. 
i am wondering there has to be a way to save the mail folder the pref.js the abook.mab the blacklist.xml delete all of thunderbirds in synaptic  then go to my home folder and delete all the .mozilla-thunderbird and .thunderbird isn't there a purge command in terminal i can use for thunderbird then reinstall thunderbird 2.0 ?
any thoughts anybody?

---

### Post by DarinB on 2010-02-11
ok i finally got a real message on the thunderbird crashes 
here it is 
darin@darin-desktop:~$ mozilla-thunderbird
darin@darin-desktop:~$ 
(crashreporter:4724): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(crashreporter:4724): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(crashreporter:4724): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

---

### Post by DarinB on 2010-02-12
I finally gave up my system was so frakked. eventually the Grub died. 
I ended up trying karmic OMG what a pain. after an all nighter i ended up with either no printer with cups and everything installed but no printer recognition OR no Internet even with everything present in the config files. and the usb ls. 
I ended up trying linux mint on a lark around 10 this morning. And considering many podcasts rave about it...it works really well. BTW Thunderbird 2.000023 works great
thank you  for all your hard work trying to help me with this pain. I learned a great lesson don't upgrade anything if what i have works. And Tbid 3.0, 3.1 etc are all not ready for prime time.

---

