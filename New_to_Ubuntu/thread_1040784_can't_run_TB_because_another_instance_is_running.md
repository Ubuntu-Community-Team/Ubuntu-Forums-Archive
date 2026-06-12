---
title: "can't run TB because another instance is running"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-01-15
Thank for any help.
TB is refusing to run because it says that another instance of TB is running. Could this have something to do with ".parentlock" or "lock"
files? If so where are they and can I delete them?
Or is something else causing the problem? 
I had the TB screen on for a few minutes then I got this problem.
I checked the "profiles.ini" and it appears to be ok.

1% Ubuntu workin on 2% Ubuntu

---

### Post by blueridgedog on 2009-01-16
Can you tell me what TB is?  You can check and see if it is running by using a terminal and typing:

```
ps ax | grep TB
```

Note that the name and capitalization have to be exact.

If it is running and you want to stop it, take not of its process id and then type:

```
sudo kill XXXXXX
```

Where xxxxx is the process ID you observed.

---

### Post by stevoo on 2009-01-16
TB -> The PirateBay grrrrr


but what blueridgedog dog said .. 

youll need to kill it before starting another one.

If you find it and doesnt die.
```

Use sudo kill -9 XXXXX
```

---

### Post by Jack Shankle on 2009-01-16
Thank you for replying.
Here is what I got as you directed. 

jack@mysolemate:~$ ps ax | grep TB
 6251 pts/0    R+     0:00 grep TB
jack@mysolemate:~$ sudo kill 6251
kill: No such process
jack@mysolemate:~$

---

### Post by blueridgedog on 2009-01-16
Your PS only found your search for TB, so eitehr it is not running or it is named something different.  You can issue a:

```
ps ax
```

to see the entire list, perhaps you will reconise it.

---

### Post by Jack Shankle on 2009-01-16
Thanks for replying.
Here is what I did. Had trouble entering the PW

jack@mysolemate:~$ ps ax | grep TB
 7142 pts/1    S+     0:00 grep TB
jack@mysolemate:~$ sudo kill -9 7142
[sudo] password for jack: 
kill: No such process
jack@mysolemate:~$

---

### Post by Jack Shankle on 2009-01-16
Thanks for any help.
Maybe the trouble I am having is caused by my floundering around with
TB in the beginning and maybe I have duplicates of everything and don't
know it. When I look I have scads of items under mozilla-thunderbird
and Thunderbird. If this is the case I have no idea how or what to
uninstall/remove/delete/????

1% Ubuntu working on 2% Ubuntu

---

### Post by lswb on 2009-01-16
As blueridgedog said, your search indicates the TB process is not running. A better command for searching for a running process is pgrep. It will not report itself in its results. Use the -fl option to search and return the commplete command line for a process, i.e. "pgrep -fl TB" in this case.

lock files are generally kept in /var/run (or a subdirectory of var/run) using a name format of
"processname.pid" and with the process id as the contents. Sometimes these are not erased when a program exits because of a crash or other error. See if you have a file named "TB.pd" in /var/run and if so "sudo rm /var/run/TB.pid"

---

### Post by blueridgedog on 2009-01-16
Good catch on the temp file...that could be it.

---

### Post by Tibuda on 2009-01-16
What the hell is TB? I guess it is Thunderbird, if so try```
killall thunderbird
```

---

### Post by hotstovejer on 2009-01-16
How are you "running" The Pirate Bay? It's a website. How did you install TB? Is it running thru Firefox?

I'm confused...

Jeremy

---

### Post by Jack Shankle on 2009-01-16
Thanks for any help.

killall thunderbird didn't do anything.
TB is Thunderbird.

I have no idea how to find /var/run.
I've searched on "processname.pid. found nothing.
I've searched on "TB.pid. found nothing.

The instructions are beyond my abilities.
I'm am absolute novice with Ubuntu.
Sorry to take up your valuable time everyone.

1% Ubuntu working on 2% Ubintu

---

### Post by Jack Shankle on 2009-01-16
I have NO idea why "Pirate Bay" is running. I am not aware of it.
I first downloaded TB from [www.mozilla.com](www.mozilla.com). I was later told this
was totally wrong. So I tried to delete everything I could find and
got TB from Ubuntu. Then it started to work and then the process is
running message.....

1% Ubuntu working on 2% Ubuntu

---

### Post by hotstovejer on 2009-01-16
I see. You downloaded the tar.gz, and didn't install ti via add/remove programs. You tried installing it that way, and now there is more than one instance running. Correct?

You can go to System --> Administration --> System Monitor and under the Processes tab, kill everything you see for Thunderbird. Then try restarting it.

Jeremy

---

### Post by LowSky on 2009-01-16
> **hotstovejer said:**
> 
You can go to System --> Administration --> System Monitor and under the Processes tab, kill everything you see for Thunderbird. Then try restarting it.



+1 thats the easiest way to do it from Gnome

---

### Post by Jack Shankle on 2009-01-16
Thanks guys for replying.
Yes, I did it the wrong way and tried to delete my mistakes
and installed it thru Ubuntu. 
I tried what you suggested Hotstovjer and there was not a single
item there for Thunderbird. Only one for Firefox.

I am about to dive off the deep end and take Ubuntu back off the Puter
and reinstall it and go through the whole process again. It will
be a hassle as I am Dual Booting with 2 Vistas on one drive and Ubuntu
on another. If I can remember all that I did.
Will wait till I hear from you again before doing it.

1% Ubuntu working on 2% Ubuntu

---

### Post by kellemes on 2009-01-16
All you need to know is here..
[http://kb.mozillazine.org/Profile_in_use]("http://kb.mozillazine.org/Profile_in_use")

This can happen when your tb-versions on your os's aren't the same, and some plugins can be at fault too.

---

### Post by Jack Shankle on 2009-01-16
Thanks again for replying.

I have probably fouled up Ubuntu with my mistakes installing Thunderbird
the wrong way that the ONLY solution is to start over. I don't see any other path available and I am taking up to much of every bodies time.

1% Ubuntu working on 2% Ubuntu

---

### Post by albinootje on 2009-01-16
> **danielrmt said:**
> What the hell is TB? I guess it is Thunderbird, if so try```
killall thunderbird
```

Try :
```

ps auxw|grep thunder

```

Just like Firefox, with Thunderbird it's not just the thunderbird binary you have to deal with (There's also /bin/sh and thunderbird-bin involved).

Opening the System Monitor and shutting down all thunderbird processes is easier for a Linux beginner imho.

The "killall -9" in a terminal is for later ;-)

It is also possible that there's a stale lock file in your Thunderbird profile directory.
Please report back when this didn't solve your problem.

---

### Post by Jack Shankle on 2009-01-16
Thanks for replying.
The code ps auxw | grep thunderbird didn't work for me. 

I guess you all know that I imported my email etc. from the Vista HD 1
and imported it into TB on Ubuntu HD 2.

1% Ubuntu working on 2% Ubuntu

---

### Post by albinootje on 2009-01-16
> **Jack Shankle said:**
>  The code ps auxw | grep thunderbird didn't work for me. 


That's only meant for you to see whether there is anything thunderbird related still running.
If ps auxw|grep thunderbird didn't show anything, then thunderbird is not running.
Try :
```

find .mozilla-thunderbird/|grep lock

```
to find the possibly stale lock file(s).

---

### Post by Jack Shankle on 2009-01-16
Hi Albinootje,
Below is the response from the command you give me.

jack@mysolemate:~$ find .mozilla-thunderbird/ | grep lock
.mozilla-thunderbird/gkfx983t.default/blocklist.xml
jack@mysolemate:~$ 

The "gkfx98e3t.default" is the email etc. I copied to a CD from the Vista HD 1 and I imported it into TB on Ubuntu. HD 2.
I had no control over what it copied.

1% Ubuntu working on 2% Ubuntu

---

### Post by albinootje on 2009-01-16
> **Jack Shankle said:**
> 
Below is the response from the command you give me.

Thanks.
> 
jack@mysolemate:~$ find .mozilla-thunderbird/ | grep lock
.mozilla-thunderbird/gkfx983t.default/blocklist.xml


Good.. no lock files.
And "ps auxw|grep thunderbird" didn't show you anything running ?
Can you starting thunderbird again to check ?

---

### Post by Jack Shankle on 2009-01-16
Here what your command showed:

jack@mysolemate:~$ ps auxw | grep thunderbird
jack      6222  0.0  0.0    304    68 pts/0    R+   17:36   0:00 grep thunderbird
jack@mysolemate:~$ 

Thanks for all your help.

1% Ubuntu working on 2% Ubuntu

---

### Post by albinootje on 2009-01-16
> **Jack Shankle said:**
>  jack@mysolemate:~$ ps auxw | grep thunderbird
jack      6222  0.0  0.0    304    68 pts/0    R+   17:36   0:00 grep thunderbird


Good. Please type the following in a terminal :
```

thunderbird

```
and post the output in case it still doesn't want to start.

---

### Post by Jack Shankle on 2009-01-16
Here is the response:

jack@mysolemate:~$ thunderbird

After this it posted the Message Box stating that there was another instance
of TB running

1% Ubuntu working on 2% Ubuntu

---

### Post by albinootje on 2009-01-16
> **Jack Shankle said:**
> Here is the response:

jack@mysolemate:~$ thunderbird

After this it posted the Message Box stating that there was another instance
of TB running 

That's very strange :(

Can you cancel that (thunderbird from the terminal), and post the output of :
```

ps auxw|grep -i thunderbird
find .thunderbird/|grep lock
find .mozilla-thunderbird/|grep lock
dpkg -l|grep -i thunderbird

```
Thanks.

---

### Post by Jack Shankle on 2009-01-16
Hope I did this right:
Don't know what you mean bt cancelling thunderbird from the terminal.
So I didn't do that.


jack@mysolemate:~$ ps auxw | grep -1 thunderbird
jack      6537  0.0  0.0   2744  1016 pts/0    R+   18:05   0:00 ps auxw
jack      6538  0.0  0.0   3236   804 pts/0    R+   18:05   0:00 grep -1 thunderbird
jack@mysolemate:~$ find .thunderbird/ | grep lock
find: `.thunderbird/': No such file or directory
jack@mysolemate:~$ find .mozilla-thunderbird/ | grep lock
.mozilla-thunderbird/gkfx983t.default/blocklist.xml
jack@mysolemate:~$ dpkg -l | grep -i thunderbird
ii  thunderbird                               2.0.0.19+nobinonly-0ubuntu0.8.10.1      mail/news client with RSS and integrated spa
ii  thunderbird-gnome-support                 2.0.0.19+nobinonly-0ubuntu0.8.10.1      Support for Gnome in Mozilla Thunderbird
ii  thunderbird-locale-en-gb                  1:2.0.0.14+1-0ubuntu2                   Thunderbird English language/region package
jack@mysolemate:~$ 

1% Ubuntu working on 2% Ubuntu

---

### Post by albinootje on 2009-01-16
> **Jack Shankle said:**
> 
jack@mysolemate:~$ ps auxw | grep -1 thunderbird
jack      6537  0.0  0.0   2744  1016 pts/0    R+   18:05   0:00 ps auxw
jack      6538  0.0  0.0   3236   804 pts/0    R+   18:05   0:00 grep -1 thunderbird

Yes, correct, thanks for the output.
It's a mystery to me why thunderbird complains about another thunderbird still running :(

Can you post a screenshot of the error ?

---

### Post by Jack Shankle on 2009-01-16
Tried to upload a screen shot but no luck sorry.
Here is the exact message:

Thunderbird is already running, but is not responding. To open new
window, you must first close the existing Thunderbird process or
restart your system.


                                          OK button at lower right

---

### Post by egalvan on 2009-01-16
OK guys, maybe we are chasing the wrong rabbit...

I have my FireFox profiles on an external drive, and have the profiles.ini point to that external drive.

If I start FF and tell it to use my external profile, and that drive is not available (not connected, not mounted, etc),

 then FF does NOT complain that the profile is un-avaialable, but that ...

"The profile is in use"

I put up a screen shot to show the exact "error" message.

When I first started trying to use my profiles in this manner, that mis-guided error message caused me much grief, trying to find the "running instance of FireFox", which of course did not exist.

Maybe the OP has a similar problem? Thunderbird just can't find his profile, but the "error" message is sending us after the wrong rabbit?

I suggest he try launching the profile manager for TB, and create a new profile with default options, and see if this runs.

"wascully wabbit"  :)


EDIT... OK, the "attach files" option is not working at this moment..

so the exact error message is as follows...

> Profile in Use

Firefox cannot use the profile "124fff" because it is in use right now.

To continue, close the running instance of Firefox or choose another profile.



further edit... seems some more options are not running well at this moment, I cannot choose any codes or formatting.


Just finished accepting up-dates...

---

### Post by albinootje on 2009-01-16
> **egalvan said:**
>  When I first started trying to use my profiles in this manner, that mis-guided error message caused me much grief, trying to find the "running instance of FireFox", which of course did not exist.
--- cut ---
I suggest he try launching the profile manager for TB, and create a new profile with default options, and see if this runs.


Very interesting, thanks for sharing.

To the OP, please try this in a terminal :
```

thunderbird -P

```

---

### Post by Jack Shankle on 2009-01-16
Hi,
I think we are getting somewhere.
Notice I ran the command with a small "p"
Got very different results with a capital "P"
Can't figure out how to send it to you.
It produces a window called: Thunderbird User profile button
You need to see it so I will keep tinkering till I figure it out.
This one is the small "p"

jack@mysolemate:~$ thunderbird -p

run-mozilla.sh: Cannot execute /usr/lib/thunderbird/thunderbird-bin.pure.

---

### Post by egalvan on 2009-01-16
> **Jack Shankle said:**
> Hi,
I think we are getting somewhere.
Notice I ran the command with a small "p"
Got very different results with a capital "P"


WARNING...
WARNING...

some folks may view my comments as mocking or insulting the OP,
but they are not.
They are poking jibes at Bill Gates.
All others should view them as gentle reminders that at times things are different because they ARE different...no matter what Microsoft says... :)

WARNING...
WARNING...

What a concept... "p" is not the same as "P".

Yes, one of the difficulties (and strengths) of *.nix is that uppercase and lowercase are different.


"difficult" for beginners, and those coming from Microsoft.
but a "strength" for old-time *nix users, and those willing to learn a new (or different) way of doing things.

:)


And to the OP, congratulations, you have taken the first step in a long journey to a larger world!

ErnestG

---

### Post by Jack Shankle on 2009-01-16
Can't get the stupid thing to attach to the message so i'll describe it 
as best I can. This is by using the capital "-P"

--------------------------------------------------------------
  thunderbird - choose user profile
---------------------------------------
thunderbird stores information about your settings, preferences and other
user items in your user profile
--------------------------------------------------
                                            
----------------                |  DEFAULT (HIGHLIGHTED)
create profile                                                                                                                                                                                                                                       
---------------

---------------
rename profile
---------------

---------------
delete profile
----------------

                               | |  work offline
                               |x|  don't ask at startup 


             |exit|                |x  start Thunderbird|

Best I can do but you get the idea.
Just out of curiosity what is an OP?

---

### Post by albinootje on 2009-01-17
> **Jack Shankle said:**
> Can't get the stupid thing to attach to the message so i'll describe it 
as best I can. This is by using the capital "-P"
-- cut --
Just out of curiosity what is an OP?

Good. Create a new profile, and see whether Thunderbird still complains.
And "OP" is "Original Poster", the person who started a the thread.

---

### Post by Jack Shankle on 2009-01-17
Hi Albinootje,
Thank you and others for all your help and patience.

Creating a new profile did the trick. I think it's now working.
At least the TB screen came up. I'll play with it some more to
check it out thoroughly.
Sure saved me a lot of headaches by having to reinstall Ubuntu.

Not sure if this promotes me to 2% Ubuntu or I am still at 1% LOL.
Am much relieved and thanks again everyone.

---

### Post by albinootje on 2009-01-17
> **Jack Shankle said:**
> 
Creating a new profile did the trick.

Great you have it working, and most thanks should go to egalvan.

---

### Post by egalvan on 2009-01-17
> **Jack Shankle said:**
> Hi Albinootje,
Thank you and others for all your help and patience.

Creating a new profile did the trick. I think it's now working.
At least the TB screen came up. I'll play with it some more to
check it out thoroughly.
Sure saved me a lot of headaches by having to reinstall Ubuntu.

Not sure if this promotes me to 2% Ubuntu or I am still at 1% LOL.
Am much relieved and thanks again everyone.

A good first step.

Does TB start directly, or does it go to a "profile chooser" window first?

If it starts directly, then your original "profile.ini" file is not where TB wants it.

I know, kinda confusin'


TB and FF expect to find the file "profile.ini" in a specific location.

The "profile.ini" file has information on the name and location of your profile folder. Also some other minor info...

ErnestG

---

### Post by Jack Shankle on 2009-01-17
Thanks all  - sorry to take your time.
The screen came on as stated before but that's all it did. No addresses
or email. I wouldn't be surprised at all if my profile was in the wrong place.
I'm going to try one more thing before I give up on Ubuntu.
A complete start over of Ubuntu.
I looked at the "add/remove" and I didn't see the main TB package
there. Others recommended that I use the "add/remove" to install TB.
So I am a little confused.

---

### Post by albinootje on 2009-01-17
> **Jack Shankle said:**
> Thanks all  - sorry to take your time.
The screen came on as stated before but that's all it did. No addresses
or email. I wouldn't be surprised at all if my profile was in the wrong place.
I'm going to try one more thing before I give up on Ubuntu.
A complete start over of Ubuntu.
I looked at the "add/remove" and I didn't see the main TB package
there. Others recommended that I use the "add/remove" to install TB.
So I am a little confused.

You have used Mozilla Thunderbird on MS-Windows before right ? So you know how to configure your email settings for Thunderbird, right ?
Please do the following :
1) open a terminal
2) type in (copy&paste) :
```

mv ~/.mozilla-thunderbird ~/.mozilla-thunderbird-old
mv ~/.thunderbird ~/.thunderbird-old

```

Then start Thunderbird again.

---

### Post by FutureWaves on 2010-01-31
This thread (and a few others) helped a lot in making Thunderbird run again after backup so I thought I would contribute with a fairly simple solution:
Two files (profile.ini and .parentlock) can actually lock down Thunderbird and state that "It's already running" upon trying to start it. You will NOT find any running processes though as the error message is misleading.
(And for the newbies: Remember to activate "Show hidden files" in order to find the hereafter mentioned directories ;o)

When you copy-paste your previous account to the freshly installed version you will most likely also copy "/home/(user)/.mozilla-thunderbird/(8-characters).default/.parentlock". Delete this file and Thunderbird will replace it with a working one.

The other file is "/home/ulrika/.mozilla-thunderbird/profiles.ini" - This can also prevent Thunbderbird from starting. Delete this too. BUT: Now all your previously mail will have vanished from Thunderbird. This is caused by Thunderbirds "new" profile which has also made a new version of the directory  "/home/(user)/.mozilla-thunderbird/(8-characters).default" which of course is empty.
Solution: Go to  "/home/(user)/.mozilla-thunderbird" where you will see 2 (or more!) directories "(8-characters).default" (Thunderbird randomly names these directories upon creation). Now copy the directory "/home/(user)/.mozilla-thunderbird/(8-characters).default/Mail" and all contents into the new "(8-characters).default" (which does not have the "mail" directory so you cannot mistake it - And when you are up and running you can delete the old directory).

(My 'old' "(8-characters).default" directory with all content was named "mqypzg3g.default" and the 'new' "4zr5h4cq.default" just for clarification.)

---

