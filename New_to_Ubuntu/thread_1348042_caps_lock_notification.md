---
title: "caps lock notification"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by aylamarguerida on 2009-12-06
Just installed Ubuntu for the first time and I am trying to restore functionality that Windows had.  Previous computers (including this one with Windows) have notified me when I press the caps lock.  Some have a pleasant ding sound when it is pressed.  Others have had a transparent box pop up that that displays Caps Lock: On or Caps Lock: Off for a couple seconds.

I have done many searches and I can't seem to figure this one out.  I have seen an applet mentioned.  However, I think it puts an icon in the system tray.  But this is not what I want.  This would be present all the time, and the notification would not be obvious enough when it actually happens.  I just want the notification to be real time, and I want nothing the rest of the time.  I don't like clutter.

I did find a place under assistive technologies, keyboard accessibility, and then audio feedback.  I do have "beep when toggle key is pressed".  I assumed this selection would make my computer beep when I hit the caps lock key.  It doesn't.  As far as I can tell, this didn't change a thing.  My sound otherwise works.

I did have a most unusual occurrence though.  One day as I was using my computer, the functionality I wanted showed up.  As far as I know I didn't do anything (although I have been trying to get everything else optimized and configured...).  I just noticed that all of a sudden, when I activated caps lock, a ripple effect went through my title bar from left to right.  When I pressed caps lock again to deactivate it, the same ripple effect went in reverse from right to left.  This really impressed me.  I really liked it while it lasted.  But then the next day it was gone.  Again, I don't know of anything I did that could have affected this.

Lastly, another alternative that I would like is if the notifier could just pop up and tell me caps lock is on or off when I press it.  (I am referring to the little box that pops up when a network is connected for instance... it disappears on its own).  Is this possible?

Summary:
I would prefer to have either the ripple effect in my title bar or the notifier to tell me about caps lock.

If not this, I would like an audio notification.

I prefer no icon in my system tray.

I know this is possible because I actually saw the ripple!

Thanks for any help

Note: I am using Karmic and I do have compiz as well.  For a while I thought the ripple could be related to compiz but I couldn't find it anywhere.

---

### Post by bradleypariah on 2009-12-06
I don't have this *completely* figured out yet, but check this out:

In your Compiz Configuration Settings Manager, click on the "**Commands**" icon.
Choose the "**Key Bindings**" tab.  For "*Run Command 0*", click the "**Disabled**" box.
Choose "**Enabled**".  Press the "**Grab Key Combination**" button and press your [SIZE=1]CAPS LOCK[/SIZE] key.
Compiz won't view [SIZE=1]CAPS LOCK[/SIZE]  as a key combination, so just X out of the box and [SIZE=1]CAPS LOCK[/SIZE] should now be the key combination.

Click on the "**Commands**" tab.
Now, I know this command is useless to you for your intended purpose, but just bear with me for a minute.
For "*Command line 0*", enter
```
gksudo nautilus
```All this command does is open a root file browser window.  Just close it!  LOL
Or just hit cancel.  The nautilus window isn't the point here.  
My point is, if you hit the [SIZE=1]CAPS LOCK[/SIZE] key now, the computer asks for your password to begin root nautilus.  See where I'm going?

So now, if we can just get one of our Linux veterans on here to divulge a simple Linux command to play a "ding!" or ripple your panel, we're done!  :-D

Can somebody interject here please?

---

### Post by tars_ac on 2009-12-07
I've  written a small script to do this, but I couldn't find a way to trigger it.  You've given me the answer!

This isn't the most elegant way to do this, but it works.  In Compiz, set the script to "caps" and put both of these files in the $HOME/bin.  (Make sure $HOME/bin is on the $PATH first).  Run "chmod 775 ~/bin/caps" and "chmod 775 ~/bin/caps-notify.py" to make them executable, and it should work.

Note:  I used 0x1 as my caps lock LED.  This varies based on your hardware.  If you have a different one, you can find out by running "xset q" and looking at the LED mask.  If the number that changes isn't the last one, you'll need to change caps to look at a different digit (not too hard, just add as many extra digits "[0-9a-zA-Z]" to the end of the sed statement as you need, after the parentheses.  If it's not a 1, you'll need to change caps-notify.py.  Look for & 0x1 and change it to whatever works for you.

(Note: rename caps.txt to caps.  The forum wouldn't let me upload without the extension)

---

### Post by aylamarguerida on 2009-12-07
Thanks!  This works great!

---

### Post by bradleypariah on 2009-12-08
Sweet!  :-D


That was some friggin' teamwork!  

:lolflag:

---

### Post by bradleypariah on 2009-12-08
Oh!  P.S. - [aylamarguerida]("http://ubuntuforums.org/member.php?u=972604"), if you're happy with the result, you should edit your first post and rename this thread **"[SOLVED]** - [B]caps lock notification"

:-D
[/B]

---

### Post by aylamarguerida on 2009-12-08
I was going to hold off on marking the thread "solved".  Here was my reasoning:

While my need is resolved, and this is perfect for me, there are some other things I mentioned in the post that are not resolved.  These don't need to be resolved from my point of view, but I wouldn't necessarily consider this thread to be completely done.  

I don't want to encourage people to quit reading it.  I replied to the thread to indicate that my issue was solved, so nobody wastes time trying to help me with a problem I no longer have.  It is more of a documentation issue (for searches) at this point.

It would be great if somebody replied here to explain any of the other issues so that other people could benefit from my problem.

---

### Post by bradleypariah on 2009-12-09
I read through your post again... and I didn't read any other issues?

What are you referring to?  Are you still holding out for somebody to make a process that would do the ripple effect instead?

Also, marking this forum [SOLVED] definitely is not a deterrent for other people to read this thread.  I personally choose the [SOLVED] threads first when I'm searching for answers.  :-)

Cheers!

---

### Post by aylamarguerida on 2009-12-09
I guess it is just a mystery.  I am not holding out for anything else.

I just was curious what the ripple was.  It clearly exists, and I thought it might be related to compiz, but it doesn't seem to be.

Also, I was curious why the keyboard setting didn't work as an accessibility option.  Nothing seems to change when I check/uncheck that box.

So I guess if you think I should, I will mark solved since my problem is definitely solved.

---

### Post by red_five on 2010-04-07
I realize this is solved, but I have a shorter method that is all bash. I used the xset | grep | sed pipeline from tars_ac's script, then added logic to handle num lock as well. You can probably add an additional case for scroll lock, too, if you want; the mask would probably be 4 for most systems. Oh, and this probably goes without saying, but make this executable.

[SIZE="3"]lock_keys[/SIZE]
```

#!/bin/bash
icon="/usr/share/icons/gnome/scalable/devices/keyboard.svg"
case $1 in
  'num')
    mask=2
    key="Num"
    ;;
  'caps')
    mask=1
    key="Caps"
    ;;
esac
value=$(xset q | grep "LED mask" | sed -r "s/.*LED mask:\s+[0-9a-fA-F]+([0-9a-fA-F]).*/\1/")
if [ $(( 0x$value & 0x$mask )) == $mask ]
then
  output="$key Lock is on"
else
  output="$key Lock is off"
fi
notify-send -i $icon "$output"

```

In CompizConfig Settings Manager, set up the commands thusly:
[LIST=1]
[*]Command line X: lock_keys caps
[*]Command line X+1: lock_keys num
[*]Add 3rd command if desired for scroll lock
[/LIST]
Then set the key bindings as specified earlier.

---

### Post by rhydian on 2010-05-12
Thanks everyone for this; this is actually really useful for me as my physical Caps Lock LED has stopped working!

red_five, when I tried implementing your solution, terminal gives me:

/bin/lock_keys: line 20: notify-send: command not found

and nothing happens that I can see.

Do you know what I'm doing wrong here?  I'm still a complete novice with linux so no doubt I've missed something obvious.

Also, tars_ac: your solution works great for me (thank you!), with one minor query/comment/suggestion.  The notification appears and lingers for quite some time with me, so that if I just want to check the status of my Caps Lock I'm still left with the notification hovering for a good few seconds.  Moreover, while that "Caps Lock is on" notification is visible, pressing the Caps Lock button a second time - to take Caps Lock off again - doesn't get a notification until the first one has faded out some time later.  Is there some setting or parameter somewhere I can adjust so that these messages appears more "momentarily"?  Ideally it would be the display time for just these Caps Lock notifications I would like to adjust, not the global setting - I don't know if that's possible!?

Thanks again everyone, it's great to be part of this community!

---

### Post by TechnoMonkey76 on 2010-05-16
To use red_five's method, all you have to do is install the "libnotify-bin" package via apt-get (w/o quotes of course).  I figured this out by "trying" to run notify-send and seeing what package it told me to install to be able to run the command.  After it is installed, the notifications will show.  I do not know how to get the message delay set though, although I would enjoy being able to as well.  I personally own an Inspiron 1545, and although I don't need the Num lock feature because I don't have such a key, the Caps Lock issue has been bugging me for a LONG time!  I thank all of the people who have helped me resolve this issue!  :)

NOTE: The Dell Inspiron 1545 does NOT have any lock key lights.

---

### Post by Excedio on 2010-05-16
I feel silly for asking, but can someone please give me a step-by-step on how to do this using red_five's bash code?

I'm just not sure where to place the files and how to get them to work. Every time I think I have it right, nothing happens.

Also, here is what I get in my "xset q"

```

  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off

```

---

### Post by Excedio on 2010-05-16
> **TechnoMonkey76 said:**
> To use red_five's method, all you have to do is install the "libnotify-bin" package via apt-get (w/o quotes of course). I figured this out by "trying" to run notify-send and seeing what package it told me to install to be able to run the command. After it is installed, the notifications will show.** I do not know how to get the message delay set though, although I would enjoy being able to as well.** I personally own an Inspiron 1545, and although I don't need the Num lock feature because I don't have such a key, the Caps Lock issue has been bugging me for a LONG time! I thank all of the people who have helped me resolve this issue! :)
 
NOTE: The Dell Inspiron 1545 does NOT have any lock key lights.
 
Been researching this exact thing. Apparently using the tag -t *should* set a time out to a specified number of milleseconds. However, notify-osd is apparently ignoring this now. It's apparently been set to a standard 5 seconds.
 
[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508)

---

### Post by rhydian on 2010-05-17
TechnoMonkey76 - thanks! That's got it working for me!

Excedio - your xset q looks exactly the same as mine.  Here's what I did (in my very clumsy and non-expert way) to get the notifications working (hope this isn't too basic!):

1. Download the caps.txt file that tars_ac uploaded to this thread.

2. Rename this file "lock_keys" - without the quotes - and drop the .txt extension so it is recognised in File Properties as a shell script.  There obviously is a way to create a new shell script from scratch but I don't know how to do that yet!

3. Open the file in gedit, select all and delete.  Copy and paste red_five's bash code into this file, save and close.

4. Now you need to move this file into /bin.  I had to do this using the terminal with sudo privelages.  So for example if the file's on the desktop to start with:
```
sudo mv Desktop/lock_keys /bin
```

5. Make the file executable:
```
chmod 775 /bin/lock_keys
```

6. Now you'll need the libnotify-bin package TechnoMonkey76 mentioned - if you haven't got it already.  I got this from the Ubuntu Software Centre.

7. Finally set up your commands and bindings as red_five explains in CompizConfig Settings Manager.  For me X=0

Command line 0: lock_keys caps
Command line 1: lock_keys num

Bindings would be Caps Lock for "Run Command 0" and Num Lock for "Run Command 1"

8. That's it - you should be all good to go.

Let me know if that works!

---

### Post by Excedio on 2010-05-17
> **rhydian said:**
> TechnoMonkey76 - thanks! That's got it working for me!

Excedio - your xset q looks exactly the same as mine.  Here's what I did (in my very clumsy and non-expert way) to get the notifications working (hope this isn't too basic!):

1. Download the caps.txt file that tars_ac uploaded to this thread.

2. Rename this file "lock_keys" - without the quotes - and drop the .txt extension so it is recognised in File Properties as a shell script.  There obviously is a way to create a new shell script from scratch but I don't know how to do that yet!

3. Open the file in gedit, select all and delete.  Copy and paste red_five's bash code into this file, save and close.

4. Now you need to move this file into /bin.  I had to do this using the terminal with sudo privelages.  So for example if the file's on the desktop to start with:
```
sudo mv Desktop/lock_keys /bin
```5. Make the file executable:
```
chmod 775 /bin/lock_keys
```6. Now you'll need the libnotify-bin package TechnoMonkey76 mentioned - if you haven't got it already.  I got this from the Ubuntu Software Centre.

7. Finally set up your commands and bindings as red_five explains in CompizConfig Settings Manager.  For me X=0

Command line 0: lock_keys caps
Command line 1: lock_keys num

Bindings would be Caps Lock for "Run Command 0" and Num Lock for "Run Command 1"

8. That's it - you should be all good to go.

Let me know if that works!

Awesome! This worked for me. I've also added in a Scroll Lock command and added a second output (screenshot). Also, regarding the Timeout of the bubble, I may have the fix for it soon! :-)

I will post back here when It's working.

---

### Post by btechcs on 2010-05-20
The notification does not fade soon enough. There has to be some way to invoke this notification similar to volume notification, where key-press is updated into the notification (volume up and down is realtime).

Any ideas how volume notifications are done in ubuntu?

---

### Post by Excedio on 2010-05-20
> **btechcs said:**
> The notification does not fade soon enough. There has to be some way to invoke this notification similar to volume notification, where key-press is updated into the notification (volume up and down is realtime).

Any ideas how volume notifications are done in ubuntu?

To quote myself...

> Been researching this exact thing. Apparently using the tag -t *should*  set a time out to a specified number of milleseconds. However,  notify-osd is apparently ignoring this now. It's apparently been set to a  standard 5 seconds.
 
[https://bugs.launchpad.net/ubuntu/+s...sd/+bug/390508]("https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508")

---

### Post by sgosnell on 2010-05-20
If you can live without audio, and just an icon in the panel, the easiest way to do all this is ```
sudo apt-get install lock-keys-applet
```then add it to your panel.

---

### Post by btechcs on 2010-05-22
I too use the lock applet, its not as good looking as the notification (even with it's flaws). I guess the volume notification is called using dbus and not using notify-send utility. 

Any more ideas?

---

### Post by Aquatic Fist on 2010-05-22
This is what I do to get a sound every time I press caps lock:

1. Goto Preferences > CompizConfig Settings Manager > Commands.
2. Type "mplayer (location of audio file)" in command line 0.
3. Goto the Key Bindings tab and click "Disabled" after "Run command 0".
4. Grab key combination > press caps lock > close windows

Now it should work.

For me it looks like this:

[IMG]http://img710.imageshack.us/img710/4128/capslockaudio.png[/IMG]

---

### Post by btechcs on 2010-05-24
Finally the notification is real time. I used the update method call from notify-osd using python. I needed a service to run in the background, which can independently create and modify notifications, and two trigger scripts to call the service by dbus.

The dbus service, and two calling scripts were called by python. I used the same xset code in the first reply to get the status of locks. 

The archive contains the following files:

1. lock_keys - Service python script, must be running for real-time notification toggle. This require caps shell script for usage.

2. lockNum - trigger python script, used as keyboard binding for num lock.

3. lockCap - trigger python script, used as keyboard binding for caps lock.

4. caps - shell script to identify the status of locks. 
       USAGE:
          $> caps caps
          $> caps num

The way to install this is to navigate to download directory and run the following commands:
> 
$> tar -xvzf lock_Notify.tar.gz
$> cd lock_Notify/
$> chmod a+x *
$> sudo mv * /bin
[sudo] password for user: 

Now open System -> Preferences -> Startup Applications
  Add /bin/lock_keys to startup.

Open System -> Preferences -> CCSM,
  Add command 1 = lockNum
  Add command 2 = lockCap
  And add num lock and caps lock shortcuts to these commands from CCSM.

---

### Post by Excedio on 2010-07-19
Finally got it perfect. :-D

[http://opensourceexcedio.wordpress.com/2010/07/19/capsnumscroll-lock-notifications/](http://opensourceexcedio.wordpress.com/2010/07/19/capsnumscroll-lock-notifications/)

---

### Post by tars_ac on 2010-07-19
Excedio,

Is there any word on if the revised notify_osd is going to make it into the mainline?  I admit I haven't been following this thread closely once my original code worked for me, but it would sure be nice to have it disappear faster.  I don't like installing stuff from PPAs unless it's a critical bug, though, because in my experience it tends to make life difficult later on.

---

### Post by Excedio on 2010-07-19
I have not checked the bug report to see if anyone convinced a dev to implement a mainline fix. However, now is as good a time as any. :-)

EDIT: Checked through the bug report. It's not been implemented at_all.

---

### Post by stinkeye on 2010-07-20
Haven't read the whole thread, but have you seen this.
[**_[COLOR="DarkRed"]http://www.webupd8.org/2010/07/indicator-keylock-displays-keyboard.html[/COLOR]_**]("http://www.webupd8.org/2010/07/indicator-keylock-displays-keyboard.html")

---

### Post by Excedio on 2010-07-20
> **stinkeye said:**
> Haven't read the whole thread, but have you seen this.
[**_[COLOR=DarkRed]http://www.webupd8.org/2010/07/indicator-keylock-displays-keyboard.html[/COLOR]_**]("http://www.webupd8.org/2010/07/indicator-keylock-displays-keyboard.html")

I have. However, that's really ugly (IMO). The method that most of us used in this thread it much nicer looking and has finally been perfected using this: [http://www.webupd8.org/2010/07/patched-notifyosd-updates-option-to.html](http://www.webupd8.org/2010/07/patched-notifyosd-updates-option-to.html)

---

### Post by sgosnell on 2010-07-20
IMO, the way you're doing it is pretty ugly, and far more involved than necessary.  I'm not a big fan of the OSD, and I prefer having an indicator on the panel, so I can see it hours after I've toggled the NumLock or Caps Lock, and went away.  Beauty is in the eye of the beholder, and IMHO simpler is better, almost always.  But it's your computer, so do things the way you want.  So will I.

---

### Post by Excedio on 2010-07-21
> **sgosnell said:**
> IMO, the way you're doing it is pretty ugly, and far more involved than necessary.  I'm not a big fan of the OSD, and I prefer having an indicator on the panel, so I can see it hours after I've toggled the NumLock or Caps Lock, and went away.  Beauty is in the eye of the beholder, and IMHO simpler is better, almost always.  But it's your computer, so do things the way you want.  So will I.

To each his own. :-)

I guess they way I see it is..we are just doing it the way it should have already been done. :-)

---

### Post by btechcs on 2010-07-23
> **tars_ac said:**
> Excedio,

Is there any word on if the revised notify_osd is going to make it into the mainline?  I admit I haven't been following this thread closely once my original code worked for me, but it would sure be nice to have it disappear faster.  I don't like installing stuff from PPAs unless it's a critical bug, though, because in my experience it tends to make life difficult later on.

I did use python notify-osd calls for realtime notification of caps lock and num lock status. Its very simple, just create a daemon to listen to dbus calls for caps and num, then just bind the script to call the dbus function to caps and num lock. Final touch is to add the daemon to start-up.

The code is there in my last post. Its not very clean, but it works. Pretty efficient too.

Let me know if someone would need help in packaging the code.

---

### Post by rhydian on 2010-07-31
> **Excedio said:**
> Finally got it perfect. :-D

[http://opensourceexcedio.wordpress.com/2010/07/19/capsnumscroll-lock-notifications/](http://opensourceexcedio.wordpress.com/2010/07/19/capsnumscroll-lock-notifications/)

Hi Excedio,

Thanks so much for sharing this.  I think I've managed to successfully replace the notify-osd as you described.  However I think I've also spotted a typo in the bash script as it is currently presented - the line of code after the "esac" looks like it's been truncated prematurely, and comparing with red_five's original I think the full thing should be:

value=$(xset q | grep "LED mask" | sed -r "s/.*LED mask:\s+[0-9a-fA-F]+([0-9a-fA-F]).*/\1/")

Making this change got it working for me at least.

Also in your blog, where you talk about setting up the key bindings, you mention lock_keys caps twice -  I guess one of those should be lock_keys scroll?

Finally, do you know how the -t value works?  It seems that anything less than 1000 seems very fleeting, and moreover whether you set it to 950 or 200 it seems to be the same.  Is 1000 the lowest proper value you can set?

To go off on a bit of a tangent, what would be really great is if the caps lock off notification replaces the current caps lock on one (or vice versa) rather than queing up behind it and displaying when the first one is out the way.  This is what happens with the Microsoft keyboard driver in Windows at least anyhow, and "feels" very natural.  Though I get the impression from this article - [http://www.webupd8.org/2010/05/mark-shuttleworth-its-ok-to-customize.html](http://www.webupd8.org/2010/05/mark-shuttleworth-its-ok-to-customize.html) - that this may not be on the cards for Ubuntu any time soon!

Thanks again, we've come a long way on this one!

Rhydian

---

### Post by postino2 on 2010-08-05
If you desire an audio and/or visual notification every time either the CAPS LOCK or NUM LOCK is pressed,  try using the simple feature included with LUCID LYNX (ver 2010-04):

System/Preferences/Assistive Technologies/Keyboard Accessibility/Keyboard Preferences/Accessibility/Audio Feedback

Click on radio button that says:  Beep when Accessibility features are turned on or off

Click on radio button that says:  Beep when a toggle key is pressed

Click on radio button that says:  Flash Entire Screen

It's that simple !  (I chose the barking dog.)

---

### Post by Rebelli0us on 2010-08-26
> **postino2 said:**
> If you desire an audio and/or visual notification every time either the CAPS LOCK or NUM LOCK is pressed,  try using the simple feature included with LUCID LYNX (ver 2010-04):

System/Preferences/Assistive Technologies/Keyboard Accessibility/Keyboard Preferences/Accessibility/Audio Feedback

Click on radio button that says:  Beep when Accessibility features are turned on or off

Click on radio button that says:  Beep when a toggle key is pressed

Click on radio button that says:  Flash Entire Screen

It's that simple !  (I chose the barking dog.)

Thank you, "Flash Entire Screen" works OK but there's no sound when I press Caps Lock or Num Lock keys

---

### Post by Excedio on 2010-10-07
Wow, really delayed reply coming. :)

> **rhydian said:**
> Hi Excedio,

Thanks so much for sharing this.  I think I've managed to successfully replace the notify-osd as you described.  However I think I've also spotted a typo in the bash script as it is currently presented - the line of code after the "esac" looks like it's been truncated prematurely, and comparing with red_five's original I think the full thing should be:

value=$(xset q | grep "LED mask" | sed -r "s/.*LED mask:\s+[0-9a-fA-F]+([0-9a-fA-F]).*/\1/")

Making this change got it working for me at least.

I must have messed up the copy/paste here somehow. Good catch.

> Also in your blog, where you talk about setting up the key bindings, you mention lock_keys caps twice -  I guess one of those should be lock_keys scroll?Again, good catch. The middle (second one) should have been "lock_keys num"...which is what I have in my key binding.

> Finally, do you know how the -t value works?  It seems that anything less than 1000 seems very fleeting, and moreover whether you set it to 950 or 200 it seems to be the same.  Is 1000 the lowest proper value you can set?I believe that it work's in milliseconds, so setting it at 1000 = 1 second.

> To go off on a bit of a tangent, what would be really great is if the caps lock off notification replaces the current caps lock on one (or vice versa) rather than queing up behind it and displaying when the first one is out the way.  This is what happens with the Microsoft keyboard driver in Windows at least anyhow, and "feels" very natural.  Though I get the impression from this article - [http://www.webupd8.org/2010/05/mark-shuttleworth-its-ok-to-customize.html](http://www.webupd8.org/2010/05/mark-shuttleworth-its-ok-to-customize.html) - that this may not be on the cards for Ubuntu any time soon!

Thanks again, we've come a long way on this one!

RhydianThis does sound nice, wish I knew how. :|

---

### Post by nikkpap on 2010-11-03
Hello mates ....

I made it more simple i hope, for the average n00b like me. ;)
I used two scripts like the aboves ones and i made the command trick like with compiz commands. In the first command i put my "caps.sh" and in the second my "nums.sh" every thing is working in my lappie. Acer Aspire 6290G 
If you want to see what is your hex numbers, you just try my caps-num-hex-finder.sh

# the rest as above, you choose a folder, i use ~/bin
# copy them inside and make them executables with 

sudo cp *.sh ~/bin
sudo chmod +x *.sh

double clik and run or sh caps-num-hex-finder.sh
note down your hex numbers with the CAPS ON then do it again with the CAPS OFF note again then with the NUMS ON then with NUMS OFF and then with CAPS and NUMS ON 

In my case was :
 
CAPS ON = 1 
CAPS OFF = 0
NUMS ON = 2 
NUMS OFF = 0 
CAPS ON + NUMS ON = 3 

Then go in my scrips and make the appropriate changes, and viola.

..:: Greetings from Greece ::.. 

"nikkpap"  [email]nikkpap@gmail.com[/email]

P.S. << Thanks my good friend "wizel" for correcting me all the time in the algorithms hahaha ;) >>

---

### Post by migs73 on 2010-11-03
The OP specifically requested to have the ripple effect from the window title bar. I think I have solved this particular issue (excuse me if somebody else has posted this but I didn't see it).

Enable the assistive technolgies as described before 

System/Preferences/Assistive Technologies/Keyboard Accessibility/Keyboard Preferences/Accessibility/Audio Feedback

Click on radio button that says: Beep when Accessibility features are turned on or off

Click on radio button that says: Beep when a toggle key is pressed


Then go to Compiz manager > Effects > Water Effect and check the box to enable it.


That's it. No scripts required.Ripple from Window Title bar when Caps Lock Pressed.

:)

---

### Post by nikkpap on 2010-11-04
ubuntu is open source so its open mind one man ask for something we all show the point we all analyse the point so the point is fixed ... its in your opinion and style what to use.... i prefer the OSD notifications from notify command. if you like the sound use the systems option thats it... all do the same work ....

---

### Post by flongx on 2012-10-26
If like me you don't use compiz, here's a way to do this without it:

sudo aptitude install xbindkeys sox libnotify-bin

Put this into the file ~/.xbindkeysrc:

#CapslockNotification
"notify-send "`xset -q | grep -o "Caps Lock: *[^ ]*"`" && play /usr/share/sounds/freedesktop/stereo/bell.oga"
    m:0x2 + c:66
    Caps_Lock 

Then just add xbindkeys to the startup applications.

---

### Post by overdrank on 2012-10-26
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

