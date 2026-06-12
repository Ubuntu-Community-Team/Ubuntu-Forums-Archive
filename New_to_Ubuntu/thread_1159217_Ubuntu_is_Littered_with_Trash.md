---
title: "Ubuntu is Littered with Trash"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by ashton88 on 2009-05-14
There is Trash in /home/everysingleuseronyourbox/.local/share/Trash, and random trash directorys popping up like .Trash-0 and .Trash-1000 nestled in subdirectories.  Not to mention Trash it /root/.local/share/Trash ... and who knows where else... apparently there use to be ~/.Trash.

As I understand it, when you empty your Trash you are only emptying one Trash.  But there is still all the junk you didn't know you threw in your neighbors backyard (and he isn't happy about it).

Ubuntu is TRASHY.  (Can the 'T' release be called Trashy Tattler?)

Can someone point me to a single-click, easy-to-use, waste-management program that will automatically pick up and clear out my trash once a week no matter where it is?  Every link I go to tells me to manually go find and delete stuff... manually?  what?  This is a computer you know... it should be able to pick up after it self...  Isn't Ubuntu potty trained?  Even the venerable Windows is potty trained (albeit he wears adult diapers).

As it stands the trash over here is piling up in so many places I don't even know where all to look for it anymore.  The smell is unbearable.

Won't someone think of the children!

Thanks!

---

### Post by LowSky on 2009-05-14
Different owner, different trash.
use the search funtion to find all folder with the word TRASH

note: linux is set up to be user specific, so stuff in you user trash file, will not be in someone elses trash file.

also if you like you Shift+Delete, that way the file becomes garbage and is gone rather than going to a trash folder

---

### Post by Locutus_of_Borg on 2009-05-14
every user should have their own trash, i suppose you could bypass this by linking all of their ~/.local/share/Trash directories to somewhere

i dont know why you are getting .Trash-0 folders, i dont have any

---

### Post by CatKiller on 2009-05-14
> **ashton88 said:**
> As I understand it, when you empty your Trash you are only emptying one Trash. 

No. When you empty the Wastebasket, you are emptying that user's Trash. From all that users' .Trash files on all volumes.

Why would you want a user to be able to empty another user's Trash?

---

### Post by t4ggs on 2009-05-14
ashton88, don't ever talk that way about Ubuntu again

---

### Post by sloggerkhan on 2009-05-14
The only place I notice 'extra' trashes is removable media.

---

### Post by Bios Element on 2009-05-14
Just wow...I mean really, Unless you are logging in as root and deleting files, You'll never actually use any other trash folder then your own. So how is this an issue again? And why does this warrant a baseless flaming?

---

### Post by cosine352 on 2009-05-14
I have to admit that I really enjoyed the presentation of the problem. 
I have noticed that some applications produce it's own trash. For example the encrypted "Private" directory has it's own trash (like in my box /home/user/Private/.Trash-1000). But that Trash is used only when I delet something from the directory "Private".

---

### Post by Tibuda on 2009-05-14
> **Bios Element said:**
> Just wow...I mean really, Unless you are logging in as root and deleting files, You'll never actually use any other trash folder then your own. So how is this an issue again? And why does this warrant a baseless flaming?

That's probably the bad practice of 'gksudo nautilus'.

---

### Post by Bios Element on 2009-05-14
> **danielrmt said:**
> That's probably the bad practice of 'gksudo nautilus'.

Shift + Delete. >.>

---

### Post by decoherence on 2009-05-14
Some of you people sound like Apple users! :P

Why does GNOME occasionally create these weird extra trashes? I'm sure there's a good reason. Does anybody know? Like, *actually* know? That'd be a useful reply.

---

### Post by drs305 on 2009-05-14
I admit there are a lot of places that Trash can accumulate, but you can't really blame Ubuntu. 

- Each user has his/her own trash. That is as it should be. When you do something with your trash, you should not be able to mess with someone else's trash.

- Root has it's own trash. That also should not be surprising.

- The .Trash-1000, etc trash files are Ubuntu's way of handling *non-linux* file systems such as NTFS. That is Ubuntu trying to *accomodate* another system's trash.

All that being said, if you have admin powers you can easily set up a cron or anacron job to delete all the trash on the computer. Although I wouldn't do it, you could have all the trash deleted at a specified time. You can find all the above-mentioned folders with:
```

sudo find / -type d -name "*Trash*"

```

---

### Post by ashton88 on 2009-05-14
> **Bios Element said:**
> Just wow...I mean really, Unless you are logging in as root and deleting files, You'll never actually use any other trash folder then your own. So how is this an issue again? And why does this warrant a baseless flaming?

Flaming?  Perhaps something is lost in translation.  There is no flaming intended or otherwise.  My thesis statement is this:

*Ubuntu is full of .Trash*

So what I am hearing is I need to write a script to find all instances of .Trash and delete them, probably based on age or size or some combination therein - bigger files getting deleted more quickly... and then run this in crontab.

This was the direction I started thinking down, until I remembered that there was a huge community out there and I thought - someone must have written a program for this already? No? A script?  With some of the scripts I've seen I'd be surprised if "Taking out the Trash" hasn't been done a million times before.  Can anyone point me to a resource?

Thanks.

---

### Post by Niniel on 2009-05-14
Sure.
It's called Google.

e.g. "ubuntu trash script": [http://ubuntuforums.org/showthread.php?t=319211](http://ubuntuforums.org/showthread.php?t=319211)

---

### Post by ashton88 on 2009-05-14
> **Niniel said:**
> Sure.
It's called Google.

e.g. "ubuntu trash script": [http://ubuntuforums.org/showthread.php?t=319211](http://ubuntuforums.org/showthread.php?t=319211)

Thanks Niniel, for your time efforts!

Oh wait.  That particular script that you have linked there only clears out the .Trash directory... it really doesn't do anything that I mentioned about multiple directories.  You know... the main point of this thread... and my original post.

To borrow from your original rhetoric, "It's called 'reading.'" ;)

---

### Post by Niniel on 2009-05-14
Ohmygod, I'm so sorry!
Well, now that you know about search engines, I'm sure you can find something better yourself.
Good luck!

---

### Post by ashton88 on 2009-05-14
> **Niniel said:**
> Ohmygod, I'm so sorry!
Well, now that you know about search engines, I'm sure you can find something better yourself.
Good luck!

I seem to be having as much luck as you obviously did when you went and tried again ;)  Anyways.. on to something constructive (because epeen fueled passive aggressive nerd-sults are so 2008, dontcha think?).

):P

And since there were others actually interested in this as well, I now return you to your regularly scheduled program...

I recieved the following through a private post:
> The code below can be amended by adding a pipe and the xargs argument and "rm -R".  Also need to add root privileges.



I can appreciate that people don't want to list potentially dangerous/harmful commands in publicly accessible forums.  

However, as I would need to post here for verification ... if there is someone out there that can whip this up quick and post it - if there is something wrong with it I'm sure that it will be pounced on like the girl at your LUG meeting.

I mean, all I did was ask a question and the frustrated nerd-ragers have come out to play - just imagine if someone actually posted a malicious script! <gasp>

So my new question is:

***"If you were MacGyver, and only had a pipe, xarg, rm -r, and the statement sudo find / -type d -name "*Trash*" -- how would you automatically remove all the trash from your computer on a schedule?"***

:popcorn:

---

### Post by freeman2000 on 2009-05-14
Download "bleachbit" from Synaptics.  It may not do all that you want, but it will clean out crap from about 30-50 packages/places on Ubuntu, including about 10 different places within System (trash, cache, temp files, recent docs, clipboard, etc).  It also cleans out your browsers' cache, history, etc. It's quite a useful little program.  Good luck.

---

### Post by ashton88 on 2009-05-15
> **freeman2000 said:**
> Download "bleachbit" from Synaptics.  It may not do all that you want, but it will clean out crap from about 30-50 packages/places on Ubuntu, including about 10 different places within System (trash, cache, temp files, recent docs, clipboard, etc).  It also cleans out your browsers' cache, history, etc. It's quite a useful little program.  Good luck.

Bleachbit is a very cool little program; thanks for pointing it out!

Although it clears a lot of odds and ends off your system, as you suggested, it doesn't get all the .Trash.  The only .Trash folder it clears is the one in the users own.  Which makes sense from a security stand point - it's a user level security package.

What would be exceptional is if there was something like this that ran from the root account with a mind towards the overall space and security of these types of files on a system.

That said, Bleachbit will be a mainstay on my system.  Thanks for taking the time for the response.

---

### Post by amac777 on 2009-05-15
> **ashton88 said:**
> So my new question is:
"If you were MacGyver, and only had a pipe, xarg, rm -r, and the statement sudo find / -type d -name "*Trash*" -- how would you automatically remove all the trash from your computer on a schedule?"

**Warning**: you need to be *very* careful. What you are asking for is not necessary what you want to do. More on that in a sec.

First, a direct answer to your question:

Create the file /etc/cron.daily/deletetrashfiles by typing:

```
sudo nano /etc/cron.daily/deletetrashfiles
```

having this content:

```
#!/bin/bash
find / -type d -name ".Trash*" -print0 | xargs -0 -I '{}' rm -r {}
```

Then make that script executable with this command:

```
sudo chmod u+x /etc/cron.daily/deletetrashfiles
```

That will make your computer recursively delete all files in all directories that have a directory name matching the .Trash* pattern. The computer will automatically do this once per day around 6:45am or a few minutes after you turn on your computer each day.

But, BEWARE: **all files in all directories that start with .Trash* will be deleted!!!!!!** This may not be what you really want because it is possible that there might be a directory that starts with ".Trash" that is not actually a trash-can. For example, on my computer I see an evolution directory starting with .Trash for my Gmail account. So that is not really a Ubuntu trash can.

If you want to see which directories will be wiped out on your system if you follow the above instructions, you can run this command (this will only list the directories and not delete anything):

```
sudo find / -type d -name ".Trash*"
```

Good luck.

---

### Post by ashton88 on 2009-05-27
Thanks amac777!  I really appreciate the simplicity of that compared to what I have been playing with - doing a find, loading the results into an array, and then removing based on that.

I hear you 100% on the warning.

1 extra failsafe:

How could you write a simple script to, instead of deleting the contents of .Trash*, delete the contents of all instances of .Trash*/files/* and .Trash*/info/* ?  This wouldn't be 100%, but it would certainly be much safer.

---

### Post by Paqman on 2009-05-27
Instead of writing scripts to remove the trash, why not just prevent it from building up in the first place? Change your habits: always use shift-del and you'll never have any trash to empty.

---

### Post by ashton88 on 2009-05-28
Ahh... good call.  Unfortunately this assumes it is just my trash, and that's not the case.

To that end my goal is to have the computer adjust to my users, not vice versa.

---

### Post by decoherence on 2009-05-28
> **drs305 said:**
> - The .Trash-1000, etc trash files are Ubuntu's way of handling *non-linux* file systems such as NTFS. That is Ubuntu trying to *accomodate* another system's trash.


Thanks! Didn't know that one! I guess this is handled by Nautilus? I wonder how hard it would be to get more descriptive names...

---

### Post by drs305 on 2009-05-28
> **decoherence said:**
> Thanks! Didn't know that one! I guess this is handled by Nautilus? I wonder how hard it would be to get more descriptive names...

Well, there is a *bit* of logic, in that the 1000 in .Trash-1000 is the trash of the user whose uid is 1000. So there could also be a .Trash-.1001, .Trash-1002, etc.  ;-)

---

### Post by Therion on 2009-05-28
The best solution I've found is to use **Quickstart**.  It's *House Cleaning* option does the job quickly and neatly.  

And it really DOES clean house!

[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

Be SURE you read the install information.

---

### Post by cariboo on 2009-05-28
Personally I enable the delete option in nautilus by going to Edit-->Preferences-->Behaviour and enbale Include a Delete command that bypasses Trash and then disabling Ask before emptying the trash or deleting files.

---

### Post by Paqman on 2009-05-28
> **ashton88 said:**
> Ahh... good call.  Unfortunately this assumes it is just my trash, and that's not the case.

To that end my goal is to have the computer adjust to my users, not vice versa.

Should you be deleting anybody's trash but your own though?

---

### Post by michy99 on 2009-05-28
> **Paqman said:**
> Instead of writing scripts to remove the trash, why not just prevent it from building up in the first place? Change your habits: always use shift-del and you'll never have any trash to empty.

This was my habit until a few days ago, when I realized a split second too late that I had just deleted a 4 GB truecrypt container. No way to recover that with photorec. After hours of research and modfying and recompiling ext3grep several times, I was able to recover it.

My new habit: delete to trash, then empty trash after making sure there is nothing important there.

Yes, I could have saved myself a lot of trouble with a backup.

---

