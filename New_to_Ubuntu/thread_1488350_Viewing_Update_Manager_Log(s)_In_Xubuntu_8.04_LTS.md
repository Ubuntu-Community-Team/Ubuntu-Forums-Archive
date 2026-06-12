---
title: "Viewing Update Manager Log(s) In Xubuntu 8.04 LTS"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by _crash_ on 2010-05-20
I need to look at my Update Manager log.  I found a thread that shows how to do this in Ubuntu 9.04.  I am wondering if the same Bash commands will work in Xubuntu 8.04 LTS.

Also, I would like to know if there is more than one log for the Update Manager.  I would appreciate it if someone could set me straight on that issue as well.

In a [[COLOR="Red"]previous thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1004326"), a forum member asked how to view the Update Manager log.  In said thread a reply was made by ShirishAg75.  I was considering trying what was suggested by ShirishAg75:


> $ sudo cat /var/log/apt/term.log


But the above thread was posted in a Community Discussion dedicated to Jaunty Jackalope, (Ubuntu 9.04).  And as the title of this thread says, I am using Xubuntu 8.04 LTS.


Here are my questions:

1)
Is it safe to use the above code in Xubuntu 8.04 LTS?  

2)
If the answer to 1 is yes, are there any precautions I should take?  (So that I don't mess up my system?)  

3)
If the answer to 1 is no, what should I do to view my Update Manager log in Xubuntu 8.04 LTS?

4)
Is there more than one log for the Update Manager?


Thanks, 

crash

---

### Post by Ozymandias_117 on 2010-05-20
> Here are my questions:

1)
Is it safe to use the above code in Xubuntu 8.04 LTS?  

2)
If the answer to 1 is yes, are there any precautions I should take?  (So that I don't mess up my system?)  

3)
If the answer to 1 is no, what should I do to view my Update Manager log in Xubuntu 8.04 LTS?

4)
Is there more than one log for the Update Manager?

1. It can't hurt anything

2. Nope. If that IS the wrong spot you just won't get any output

3. N/A

4. Not that I'm aware of.


Edit: Just some more information for you. In that command, sudo means run as root. While this CAN damage your system if certain commands are run after it (like rm), as long as the command that is called after sudo isn't destructive, you don't need to worry. The second command called is cat all this means is display the contents of the file named afterwards on the screen. The /var/log/apt/term.log is simply the location of the log file. Since this file is in a protected directory, you have to start the command with sudo so the system knows you're authorized to see it. If you are ever in doubt of a command, you can always use ```
man *command_name*
``` which will tell you what the command does, as well as switches you can add to modify what it does.

One other side note, you may want to run the command as ```
sudo cat /var/log/apt/term.log | less
``` which means it will display the log file in a way that you can scroll up and down (the | is a pipe which means send the output of my previous command as the input of the next) and less just makes long text files easier to read.

---

### Post by _crash_ on 2010-05-20
Ozymandias_117, thanks for your help!

I guess you can tell that I am pretty much functionally illiterate when it comes to Bash!

Anyway, onward to reply...


> ...sudo means run as root.


Right.  I am aware that sudo means Super User Do, (or, if you want to believe [[COLOR="Red"]Wikipedia[/COLOR]]("http://en.wikipedia.org/wiki/Sudo"), "substitute user do".


> While this CAN damage your system if certain commands are run after it (like rm), as long as the command that is called after sudo isn't destructive, you don't need to worry.

Right.  I have read [[COLOR="Red"]ATTENTION ALL USERS: Malicious Commands[/COLOR]]("http://ubuntuforums.org/announcement.php?f=326"), although most of the stuff in that thread is WAY over my head.  But you read my mind.  You saw the fact that I was scared enough to want to make sure that I knew I was going to be doing the right thing.  And that shows a great deal of attentiveness, for which I am grateful!


> The second command called is cat all this means is display the contents of the file named afterwards on the screen.


Right.  I have read up on cat a little bit, and as I understand it, cat is used to concatenate one file to another, or in my case, the log file to the bash terminal, (the screen).


> Since this file is in a protected directory, you have to start the command with sudo so the system knows you're authorized to see it.


OK, that is good to know and new info for me.  I did not know that /var/log/apt/ was a protected directory.  Thanks!


> If you are ever in doubt of a command, you can always use:  man command_name, which will tell you what the command does, as well as switches you can add to modify what it does.


Well thanks for trying to help!  I am probably going to get flamed for this, but here I go regardless.  I hate man pages.  man pages are for people who actually know what they are doing in Bash.  Seeing as how I am a dope when it comes to Bash, they are pretty much useless to me.  Don't get me wrong, I can see a day when I will use them, and be grateful for them, I am sure.  But for newbies, they suck.  (My opinion, for what it is worth).

I have read docs from [[COLOR="Red"]The Linux Documentation Project[/COLOR]]("http://tldp.org/"), which have helped me some.  But the problem is, as soon as you want to move beyond the thumb sucker stage of noodling around in Bash, you right away get thrown into something that is like intermediate level quantum mechanics or some such stuff.  It can be frustrating.  

Then the other problem is the size and sophistication of Bash/Linux/Unix.  I mean, some of the PDFs on The Linux Documentation Project are in the hundreds of pages.  And I am struggling just to keep my head above water on a lot of this stuff.

I want to learn, but my main problems are lack of time, lack of time, and lack of time.  (Did I forget to mention that my general lack of time is a hindrance to learning Bash?  Oh, never mind).

The bottom line is Bash scripting is very powerful, but with that power comes complexity.  And like I said, I am struggling to keep my head above water, etc..

But anyway, enough of my belly aching and back to being on topic.


> One other side note, you may want to run the command as
Code:

sudo cat /var/log/apt/term.log | less

which means it will display the log file in a way that you can scroll up and down (the | is a pipe which means send the output of my previous command as the input of the next) and less just makes long text files easier to read.



Hey, that is pretty cool!  I am familiar with the pipe char, (option, whatever you want to call it).  But I did not know you could use it to re-direct the output of cat to less!  That is interesting!

Anyway, I am probably going to take a slightly different route in grabbing that Update Manager log file, which was given to me by PaulFr many, many, [[COLOR="Red"]moons ago[/COLOR]]("http://ubuntuforums.org/showthread.php?t=715522").  But I will keep your suggestion on hand Ozymandias_117, and when I get a chance I am going to mess around with it.

I need to peruse the entire Update Manager log for some error messages.  I am going to do this by hand, in a word processor.  I know I can use grep, but I am not sure what the string I am looking for was, so I want to do it by hand, etc..  Therefore, I want to save the Bash session as a log file.

I will post what I find in this thread!

Hey thanks for all your help Ozymandias_117!  You rock!



Gratefully,


crash

---

### Post by Ozymandias_117 on 2010-05-20
> **_crash_ said:**
> 
I need to peruse the entire Update Manager log for some error messages.  I am going to do this by hand, in a word processor.  I know I can use grep, but I am not sure what the string I am looking for was, so I want to do it by hand, etc..  Therefore, I want to save the Bash session as a log file.

Then another option is ```
sudo cat /var/log/apt/term.log > ~/Desktop/your_filename
``` Which will output the results into a file on your desktop called "your_filename"

Or you could always just copy the file to your desktop ```
sudo cp /var/log/apt/term.log ~/Desktop
```

---

### Post by _crash_ on 2010-05-21
Ozymandias_117!

Man, that is really awesome!  THANKS!

I have to do a couple of things, (busy week this week).  When I get back on my computer in a little while, I am going to try this one that you gave me:

> Then another option is
Code:

sudo cat /var/log/apt/term.log > ~/Desktop/your_filename

Which will output the results into a file on your desktop called "your_filename"



I don't mean to be weird Ozymandias, but it is like you are reading my mind and know exactly what I want to do!

THANKS again for your great help!

Be back soon.


Gratefully,

crash

---

### Post by _crash_ on 2010-05-21
A general apology...

I just want to say I am sorry for ranting earlier in this thread about Bash and stuff.  I was having a bad night the other night.  

If anybody was offended I wanted to say I am sorry!

I want to learn Bash, but lack of time has been a real devastating killer for me lately on a lot of different issues, not just computers, Linux, Bash, etc..

Anyway, again I to say I am sorry to everyone:

[LIST=1]
[*]For ranting
[*]For being off topic
[*]If I offended anybody
[/LIST]

Please accept my apologies...


crash

---

### Post by _crash_ on 2010-05-22
I did 3 attempts and they all failed.  It looks to me like there is some kind of problem with permissions.  (If I am wrong, please feel free to correct me).

I will show the Bash sessions for each of the 3 attempts.  For all Bash sessions and for all file contents, I have changed the actual names of my su account  and my CPU to the following:

suName

CPUName

I have not made any other modifications other than what was stated above.

For all 3 attempts, I was logged into my su account.

---

### Post by _crash_ on 2010-05-22
_Attempt 01:   FAIL_

I was logged into my su account.

For this attempt, I tried one of the suggestions that Ozymandias_117 gave me in his previous post in this thread, to use cat to view the contents of 

cat /var/log/apt/term.log

and redirect said viewing to a file on my Desktop.



_Commands Used:_
sudo cat /var/log/apt/term.log > ~/Desktop/your_filename


NOTE:
I did one slight modification to the above command.  I changed the name of the file created on my Desktop to be "UM_Log", (short for "User Manager Log").



_Bash Session:_
```
suName@CPUName:~$ sudo cat /var/log/apt/term.log > ~/Desktop/UM_Log
[sudo] password for suName: 
suName@CPUName:~$ sudo cat /var/log/apt/term.log > ~/Desktop/UM_Log
suName@CPUName:~$ 

```



_Results:_
The "UM_Log" file appeared on the Desktop.  But it was a zero byte file.  There was nothing inside the file.

---

### Post by _crash_ on 2010-05-22
_Attempt 02:   FAIL_

I was logged into my su account.

For this attempt, I was trying to do the following:

[LIST=1]

[*]Make Bash record my entire Bash session to a text file using the script command.


[*]Use cat to display the contents of following file:
/var/log/apt/term.log


[*]The contents of the above file would then be recorded in said text file.
[/LIST]



_Commands Used:_

script UM_Log.txt

sudo cat /var/log/apt/term.log



_Bash Session:_
```
suName@CPUName:~$ script UM_Log.txt
Script started, file is UM_Log.txt
suName@CPUName:~$ sudo cat /var/log/apt/term.log
[sudo] password for suName: 
suName@CPUName:~$ exit
exit
Script done, file is UM_Log.txt
suName@CPUName:~$
``` 



_Results:_
A log file of the above Bash session was created, the file size was 236 bytes.

Here is the contents of the above file:


Script started on Fri 21 May 2010 07:55:35 PM EDT
?]0;suName@CPUName: ~?su_Name@CPUName:~$ sudo cat /var/log/apt/term.log
[sudo] password for suName: 
?]0;suName@CPUName: ~?suName@CPUName:~$ exit
exit

Script done on Fri 21 May 2010 07:56:33 PM EDT

---

### Post by _crash_ on 2010-05-22
_Attempt 03:   FAIL_

I was logged into my su account.

For this attempt, I simply copied the file to the Desktop per Ozymandias_117 suggestion in a previous post in this thread.



_Command Used:_
sudo cp /var/log/apt/term.log ~/Desktop




_Bash Session:_
```
suName@CPUName:~$ 
suName@CPUName:~$ sudo cp /var/log/apt/term.log ~/Desktop
[sudo] password for suName: 
suName@CPUName:~$ 

```



_Results:_
A file named "term.log" was created on the Desktop of my su account.  But the file was a zero byte file.  I checked the Permissions of the above file in the GUI:

Owner:
root (root)

Access:
Read & Write

Group:
root

Access:
None

Others:
None



When I tried to open the above file, I got this error dialog:

"Failed to open file '/home/suName/Desktop/term.log': Permission denied."

Also, I can not delete the above file off of the Desktop of my su account.

---

### Post by _crash_ on 2010-05-22
If Ozymandias_117 or anybody else can tell me what is wrong, I would greatly appreciate your help!

Gratefully,

crash

---

### Post by _crash_ on 2010-05-22
I need to do some security updates as soon as I can, and also install some badly needed application software.  I realize it might take a little while for somebody to respond to this thread again.

So in the mean time, I was hoping maybe somebody could answer these questions for me:


[LIST=1]
[*]Is there a way to set the Update Manager Log so that it has unlimited recording?  In other words, to make it so that the Update Manager Log does not dump the old stuff it has recorded when I start doing new stuff?  


[*]If the answer to 1 is yes, can I safely do this from my su account?
[/LIST]

The reason why I want to look at the log in the first place is to ask some questions about error messages I got when doing updates a few weeks ago.  If I can do the above, I can get on with my security updates and install some much needed application software.  

Then when somebody finally is able to help me get a copy of the log going that I can look at, I can ask my questions about the error messages I got a few weeks ago.  Otherwise, I am afraid that the Update Manager error messages that I got a few weeks ago might be "pushed off the top" of the log and lost, and I will not be able to post questions about said error messages.

Thanks any who might help!!


crash

---

### Post by Ozymandias_117 on 2010-05-22
It almost sounds like your log file is empty... Post the results of ```
ls -l /var/log/apt/term.log
``` (Please note the l is a lower case L, not the numerical 1)

---

### Post by _crash_ on 2010-05-24
Thanks for sticking with me Ozymandias_117!

BRB with what you asked for.

---

### Post by _crash_ on 2010-05-24
Here you go.  Sorry for taking so long to reply.  I had a couple of unforeseen interruptions.

As in my previous posts, I changed the names of my su account and my CPU.  But everything else is exactly as it appeared in Bash.



```
suName@CPUName:~$ ls -l /var/log/apt/term.log
-rw------- 1 root root 0 2010-04-01 00:31 /var/log/apt/term.log
suName@CPUName:~$ 

```

---

### Post by Ozymandias_117 on 2010-05-24
Okay:

1. Your term.log file IS empty, not sure who or what or how or why.

2. Do you do your updates through the update-manager program, or through the terminal?

3. You could try looking at /var/log/apt/history.log - Maybe it can help (If it's not empty too, lol)

3.5. You can use ls -l for that one to see if it's empty. It will return something like this, the bold is the file size:```
-rw-r--r-- 1 root root  **77836** 2010-05-24 17:36 history.log
```

4. What do you need this for? I don't know, but I may be able to figure out something else if history.log is also empty


Edit: Looking back at your previous post... My term.log file has 1 months worth of updates (Starting from a fresh install) without deleting any yet. Not sure if it will start at some point or not... but it at least holds quite a bit.

---

### Post by Miljet on 2010-05-25
This is a moot point since your term.log file seems to be empty, but when you copied it to your ~/Desktop, it also copied the owner/permissions. The reason you could not access it is because the copy was owned by root.

The down and dirty way to view the new file is to use ```
 sudo cat whatever_filename 
```

Or the better solution is to change ownership of the file. ```
 sudo chown your_name:your_name whatever_filename 
```

---

### Post by _crash_ on 2010-05-25
Ozymandias_117, thanks again for helping!


> 1. Your term.log file IS empty, not sure who or what or how or why.


OK.  (Sigh).  Well, even though it is kind of bad news, at least you are helping me make progress on this.  And I am truly grateful to you for this!

But I think I just had a wack on the side of the head, (epiphany).  When you said "...not sure who or what or how or why."  It made me realize something.  See the quote/reply to your item 4 below.



> 2. Do you do your updates through the update-manager program, or through the terminal?

Update Manager.  I am kind of allergic to Bash at this time.  (As seen in my poor mouth pity party that I had for myself earlier in this thread).



> 3. You could try looking at /var/log/apt/history.log - Maybe it can help (If it's not empty too, lol)


LOL!  Man, you are funny!  OK, I will look at it per your instructions.



> 3.5. You can use ls -l for that one to see if it's empty. It will return something like this, the bold is the file size:
Code:

-rw-r--r-- 1 root root  77836 2010-05-24 17:36 history.log


OK, I will execute your code and post the results here.



> 4. What do you need this for? I don't know, but I may be able to figure out something else if history.log is also empty

BIG SIGH.

OK.  Now I realize I may have shot myself in the foot with my own stupidity on this one.

Remember when I [[COLOR="Red"]said this:[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9343628&postcount=12")
> "The reason why I want to look at the log in the first place is to ask some questions about error messages I got when doing updates a few weeks ago."


You saying what you said caused me to remember something.  I think that the updates that I did and the subsequent error messages came as a result of me running the Update Manager after the initial install of Xubuntu 8.04 LTS on this CPU.

Here is what I did:
[LIST=1]
[*]I installed Xubuntu 8.04 LTS on this CPU.


[*]I had some other stuff come up.  I let the CPU sit totally idle for several months.  (I have more than one computer, so this was not a big deal).


[*]One thing led to another and I finally got around to getting going on the Xubuntu 8.04 LTS box.


[*]On the above CPU, I did all of the security updates that had accumulated since the install of the OS all at once.  I did this over like a 1-2 day period.  There were something like 200+ updates.  Half of which were considered essential/critical/whatever you call it type of updates.
[/LIST]

During the above security updates, I selected the little drop down list carrot that is in the Update Manager window.  Said carrot allowed me to look at everything that was happening at the CLI in this little black box.  At one point, a bunch of error messages came up in said little black box.  And at several points during said security updates I was sitting there watching what was happening.  You know, so I could learn something.  Also, in case something bombed out.

Like I said earlier in this thread, I don't remember the exact error message.  But the messages in the CLI box said several times that it could not resolve critical files needed to update the Update Manager itself.  And it kept saying it was falling back to a previous version of the Update Manager and/or Update Manager packages or something.

The above error messages were the ones I was wanting to grab.  Then I was going to post same in a totally separate thread, and ask if this was a serious problem or not.  You know, "should I be concerned about this?" type of a thread.

OK, well I have yet to explain yet why I think I am stupid.  But I will now.  You guys correct me if I am wrong.  But it appears as if the Update Manager might purge its log file when the user does this "first time update after the OS is installed" Update Manager massive security update.

It was only when I started to read your most recent post Ozymandias_117, (Post  #16), that I realized that this may be the case!

I feel like such an idiot!



> Edit: Looking back at your previous post... My term.log file has 1 months worth of updates (Starting from a fresh install) without deleting any yet. Not sure if it will start at some point or not... but it at least holds quite a bit.

> "but it at least holds quite a bit"

I agree.  Your log file does hold quite a bit.

However...

Could it be that what I surmised above is true?  Because of the massive nature of doing 200+ updates all at once, either Update Manager or something else in the OS decided that nobody in their right mind would want to look at all that boring stuff, and purged the Update Manager log file?  (Again, like I said before, you guys can correct me if I am wrong on this).

Thanks again, Ozymandias_117!

---

### Post by _crash_ on 2010-05-25
Miljet, thanks for your suggestions!  I will try them ASAP.

Thanks,

crash

---

### Post by _crash_ on 2010-05-25
Getting slightly off topic for just one tiny post here...

Ozymandias_117,

I know that this may be the wrong place to tell you this, but I don't have any choice.

Thanks for accepting my request to be on my friend list.  I tried to PM you, but the system will not let me.  I can not PM anybody until I have like 75+ posts.  And I am nowhere near that number right now.  But when I meet the above requirement, I will PM you.  (I was just going to thank you again for helping me, and ask you if you would mind looking at a couple of new threads I have been working on, stuff like that).

Anyway, I just thought I should be polite and let you know what is going on.


crash

---

### Post by _crash_ on 2010-05-25
Ozymandias_117 and Miljet, I am going to have to pick up this thread a little later.  I am shot.

I am going to live up to my name and go crash.  See you guys in a few hours.

crash

---

### Post by Ozymandias_117 on 2010-05-25
What I'm wondering is, if in trying to update the update-manager, perhaps it overwrote those files with fresh ones. Like it was making all the files/folders necessary to run without looking to see if there was one already there.

See if this gives you any errors (In terminal):```
sudo aptitude update && sudo aptitude full-upgrade
```


Side note (Replying to Miljet's concern):

That was the benefit of using ```
sudo cat term.log > ~/Desktop/file
``` copying the file this way means you would have been the file owner instead of root.


and I feel like I'm forgetting to answer a question/concern... let me go re-read the last few... lol

edit: Oh yeah, was your history.log empty as well? Also, if you post the links to the other posts at the bottom of your next reply I can glance over them.

---

### Post by Miljet on 2010-05-25
> copying the file this way means you would have been the file owner instead of root.

Sorry, but that just ain't true. Anytime you use sudo with any command to create a file or directory, even in your home, it will belong to root. Try using sudo to create a temporary file in your ~/Desktop and look at the permissions.

---

### Post by Ozymandias_117 on 2010-05-25
```
user@user-desktop:~$ sudo cat /var/log/apt/term.log > ./Desktop/test
[sudo] password for user: 
user@user-desktop:~$ ls -l ./Desktop/test
-rw-r--r-- 1 user user 277488 2010-05-25 21:41 ./Desktop/test
user@user-desktop:~$
```

Exactly as it came out of my terminal.

Edit: The reason it works is the sudo is only for the "cat /var/log/apt/term.log". You are then sending the results to a new file called "./Desktop/test". You only have sudo privileges for the first half of the command (The part before the >). If you tried to put the output into a protected folder (eg anything other than ~) you would get an error saying you aren't root.

---

### Post by Miljet on 2010-05-25
Sorry, I stand corrected. I did the exact same thing last night on my install just to be sure and the file belonged to root. Just tried it again now and the file belonged to me. I don't know what I did differently last night.

---

### Post by _crash_ on 2010-05-27
Ozymandias_117 and Miljet:

Sorry for being gone so long!

I may not have much time right now to answer everything that you guys posted over the last couple of days.  I will reply to as much as I can now, and then maybe get completely caught up later today/tonight.

I will start with the most recent post that I did NOT reply to yet, post [[COLOR="Red"]#16[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9355447&postcount=16").

I want to thank you guys for sticking with me on this.  I really am learning a lot, (even though I don't understand everything that the 2 of you are saying in regards to the Bash code you have been posting).

Like I said I will start off in chronological order and work may way down until I have replied to everything you guys have said.  Be back in a little while.

While being off line over the past day or two, I had another wack on the side of the head.  I think my most recent wack is even better than the first wack I had while back on this thread.  More on that later.

Again, much gratitude from me to the both of you helping me with my problems.

---

### Post by _crash_ on 2010-06-01
Ozymandias_117 and Miljet, please accept my apologies for being so late in getting back to this thread.  I have been off line for several days due to unexpected junk that has been happening in my life.  Again, my sincere apologies!


Ozymandias_117, here is another reply to your post [[COLOR="Red"]#16[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9355447&postcount=16").  (I never got a chance to do what you asked me to on points 3 and 3.5 of said post until now).



> 3. You could try looking at /var/log/apt/history.log - Maybe it can help (If it's not empty too, lol)

3.5. You can use ls -l for that one to see if it's empty. It will return something like this, the bold is the file size:
Code:

-rw-r--r-- 1 root root  77836 2010-05-24 17:36 history.log




Per your instructions above, I logged into my su account and did the following in Bash:

ls -l /var/log/apt/history.log



_Bash Session:_
```
suName@CPUName:~$ ls -l /var/log/apt/history.log
ls: cannot access /var/log/apt/history.log: No such file or directory
suName@CPUName:~$ 
```



The above Bash session has given me an idea.  I am going to try to look at some other log files that should be common to most Linux distros.  I am going to The [[COLOR="Red"]Linux Documentation Project[/COLOR]]("http://tldp.org/") to find said log file names/locations now.  If I am successful in finding what I need, my next post(s) will show what results I am able to obtain.

---

### Post by Ozymandias_117 on 2010-06-01
Try the top half of #22

---

### Post by _crash_ on 2010-06-02
Ozymandias_117: Again, thanks again for being so diligent and sticking with me throughout this mess.



> Try the top half of #22 



I am going to talk to you about the above.  I will get to it.  But I want to try a couple of other things first.


Over the past few days, I have been doing research and typing up posts about this whole mess.  I am going to try to finally put some permanent nails in the coffin of this thread.  So bear with me please as I finish up what I am trying to do.

Today I have an appointment and several errands to run.  But I am hoping to be back on this thread later today.  (If it were not for the fact of my schedule today, I probably would have my posts done and on this thread in a couple more hours from now).

If I can not get said posts on this thread today, I should have them on this thread by Friday.

---

### Post by _crash_ on 2010-06-04
So far, here is what I have:

My User Manager Log is empty.  Refer to posts [[COLOR="Red"]#13,[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9344651&postcount=13") [[COLOR="Red"]#15,[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9353514&postcount=15") and [[COLOR="Red"]#16[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9355447&postcount=16").

My History Log does not exist.  Refer to post [[COLOR="Red"]#27[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9394132&postcount=27")



In this post, I am going to attempt to prove to myself a theory.  So please bear with me for a little while.  I am going to try to see if other commonly used Linux logs are present on my system.

Per one of my previous posts, ([[COLOR="Red"]#27[/COLOR]](http://ubuntuforums.org/showpost.php?p=9394132&postcount=27")), I went to the The [[COLOR="Red"]Linux Documentation Project[/COLOR]]("http://tldp.org/").  I did not find what I needed.  So I used Google.  I got a few good pages:



Ubuntu Documentation> Community Documentation> [[COLOR="Red"]LinuxLogFiles[/COLOR]]("https://help.ubuntu.com/community/LinuxLogFiles")

[[COLOR="Red"]Ghacks> Learning Linux: Log Files[/COLOR]]("http://www.ghacks.net/2009/02/16/learning-linux-log-files/")

[[COLOR="Red"]nixCraft> Linux log files location and how do I view logs files?[/COLOR]]("http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/")





Here is some of what I learned.  You guys can correct me if I am wrong on any of these points.


[LIST=1]
[*]A daemon is a program that runs in the background, generally without human intervention, performing some operation important to the proper running of your system.


[*]Most system logs are plain ASCII text files.  Most system logs are stored in the traditional system log subdirectory:     /var/log


[*]The system logging daemon is syslogd.


[*]The all-encompassing system log is syslog.
[/LIST]



What I wanted to try in this post is to see if other logs on my system are either missing or disabled.

Most of the below log file descriptions I obtained from the previously mentioned [[COLOR="Red"]Ubuntu Community Documentation page[/COLOR]]("https://help.ubuntu.com/community/LinuxLogFiles").  For the below descriptions, I am not using the quote tags because I have edited said descriptions for readability.



_**Log Files Of Interest To Investigate**_

**Authorization Log**
Tracks usage of authorization systems, the mechanisms for authorizing users which prompt for user passwords.
*Location:     /var/log/auth.log*


**Daemon Log**
Contains information about running system and application daemons.
*Location:     /var/log/daemon.log*


**Debug Log**
Provides detailed debug messages from the Ubuntu system and applications which log to syslogd at the DEBUG level.
*Location:     /var/log/debug*


**Kernel Log**
Provides a detailed log of messages from the Ubuntu Linux kernel.
*Location:     /var/log/kern.log*


**Messages Log**
Contains informational messages from applications and system facilities.  This log is useful for examining message output from applications, and system facilities which log to the syslog / sysklog daemon at the INFO level.
*Location:     /var/log/messages*


**System Log**
Typically contains the greatest deal of information by default about your Ubuntu system.  It may contain information other logs do not.  Consult the System Log when you can't locate the desired log information in another log. 
*Location:     /var/log/syslog*


**X11 Server Log**
The default X11 Windowing Server in use with Ubuntu is the Xorg X11 server, and assuming your computer has only one display defined, it stores log messages in the file /var/log/Xorg.0.log. This log is helpful for diagnosing issues with your X11 environment. 
*Location:     /var/log/Xorg.0.log*


**Boot Log**
Contains information about system boot up.
*Location:     /var/log/boot.log*




**_Investigating The Log Files Of Interest:  Code Used & Results Listed Overview_**

As Ozymandias_117 has taught me, I am going to use the list command to show a file properties summary of each of the above log files.  For example, to show a file properties summary of the Authorization Log, I am going to do the following:


```
ls -l /var/log/auth.log
```



For each of the following logs, I will list:

[LIST=1]
[*]The log name.

[*]The Bash string I used to display the log file properties.

[*]The Bash output for the above.
[/LIST]



**_Investigating The Log Files Of Interest:  Log File Properties Summary_**

**Authorization Log**
ls -l /var/log/auth.log
-rw-r----- 1 syslog adm 2300 2010-06-01 14:59 /var/log/auth.log


**Daemon Log**
ls -l /var/log/daemon.log
-rw-r----- 1 syslog adm 262 2010-06-01 15:00 /var/log/daemon.log


**Debug Log**
ls -l /var/log/debug
-rw-r----- 1 syslog adm 0 2010-06-01 09:20 /var/log/debug


**Kernel Log**
ls -l /var/log/kern.log
-rw-r----- 1 syslog adm 0 2010-06-01 09:20 /var/log/kern.log


**Messages Log**
ls -l /var/log/messages
-rw-r----- 1 syslog adm 749 2010-06-01 15:00 /var/log/messages


**System Log**
ls -l /var/log/syslog
-rw-r----- 1 syslog adm 1911 2010-06-01 15:00 /var/log/syslog


**X11 Server Log**
ls -l /var/log/Xorg.0.log
-rw-r--r-- 1 root root 43536 2010-06-01 15:00 /var/log/Xorg.0.log


**Boot Log**
ls -l /var/log/boot.log
ls: cannot access /var/log/boot.log: No such file or directory



For readability, I will state my conclusions/opinions about the above in my next posts.

---

### Post by _crash_ on 2010-06-04
At this time I would like to summarize what I found in my previous post.


_Log file exists where it should be, and has data in it:_
Authorization Log
Daemon Log, (not much data, only 262 bytes)
Messages Log, (not much data, only 749 bytes)
System Log
X11 Server Log



_Log file exists where it should be, but has NO data in it:_
Debug Log
Kernel Log



_Log file does NOT exist at all:_
Boot Log





**_Commentary_**

**Daemon Log & Messages Log**
To me, no big surprise in regards to the Daemon Log and Messages Log being small.  This CPU is a stock install of Xubuntu 8.04 LTS.  Since the OS install, I have only done two things:

[LIST=1]
[*]Security updates.


[*]I have created one normal user account for surfing and email.  With said account, I have created RTF docs, text docs and folders.  I have also downloaded a few HTML pages and PDFs.
[/LIST]


**Debug Log**
I guess there is no surprise in regards to the Debug Log.  I don't know how to do anything complex, so Xubuntu has not recorded any activity.


**Kernel Log**
In my opinion, I would think that there should be some data in this log.


**Boot Log**
I am surprised that this log does not exist on my CPU.



_**Wack On The Side Of The Head #2**_
On The [[COLOR="Red"]Linux Documentation Project[/COLOR]]("http://tldp.org/") I once read a doc on how to install Linux on a CPU with low RAM / low hard drive space.  (Sorry, I do not remember the name of said doc.  (I went looking for it while typing this post but could not find it).  I do remember however, that on said doc, a point was made to turn off all logging.  Said doc said that saves on hard drive space.

Earlier in this thread, I mentioned that I felt I had a second wack on the head, and I was going to share that later.  Here it is.  My wack on the head #2 was that I thought that all of the logs were turned off by default in Xubuntu 8.04 LTS, (similar to what was said in the previous paragraph).  Due to the above results, it looks like this might not be completely true in my case.  

Please tell me if I am wrong.  But is it possible that:


[LIST=1]
[*]The User Manger Log never existed on my CPU to begin with.


OR


[*]The User Manger Log was deleted when the super user first installs the OS and/or does the very first security updates(s).  I say this because the very first security update(s) are huge.
[/LIST]


There are some logs that appear to be missing on my Xubuntu box, and I would think that they should be there.  The History Log, Boot Log, and the User Manager Log are all missing.  That is VERY WEIRD.  Also, the Debug and Kernel logs have nothing in them as mentioned previously.  

So based on all of the above, it does seem to me that my theory may be partially correct.  It does seem as if some of the logs on my Xubuntu box have been trimmed down, eliminated, or never existed in the first place on my CPU.

So, am I correct on any of these points?

I was thinking about asking someone on the Xubuntu 8.04 LTS development team about what logs may have been trimmed down, eliminated, or do not exist at all on my CPU.  (Remember, everything on this box is a stock install of the OS, except for the previously mentioned user account, and some folders and docs I created on said user account).

Except for the problems with my logs, everything else on this CPU is still working fine.  Update Manager still works.  Everything appears to be working OK with no problems.  It would be nice sometime in the near future to get the Update Manager Log up and running again, but it is not super critical right now.  

At the beginning of this thread, I wanted to look at the Update Manager Log.  But Ozymandias_117, Miljet and I have put in a lot of time on this thread.  And I am beginning to give up on this issue and am wanting to move on to more productive things.

---

### Post by _crash_ on 2010-06-04
Ozymandias_117, in [[COLOR="Red"]Post #22[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9356838&postcount=22"), you said:


> What I'm wondering is, if in trying to update the update-manager, perhaps it overwrote those files with fresh ones. Like it was making all the files/folders necessary to run without looking to see if there was one already there.

See if this gives you any errors (In terminal):

```
sudo aptitude update && sudo aptitude full-upgrade
```





As I have said before, I appreciate all of the tremendous help you have been giving me on this thread!  But for the next few days, I do not want to do anything drastic to this box.  I do not want to do Post #22 at this time.  I say this because the code you gave me in Post #22 looks a little bit on the strong side.  Said code looks like it will rebuild the entire Update Manager app and / or its resource files.  Please feel free to correct me on this if I am wrong.

The problem that I am facing right now is that I need to download some critically important ISOs over the next week or so.  I need said ISOs to get some other stuff going on some of the other CPUs that I have.  Previously in this thread I said that I have other CPUs.  But the CPU that this thread is about, my Xubuntu 8.04 LTS box, has become very critical to me right now to get my other CPUs straightened out.  (To make a long story short, I need this box to download a bunch of ISOs to fix my other computers).  Then after I have all of that stuff done, I can try the code in Post #22.

---

### Post by _crash_ on 2010-06-04
I just found out something.  Now I am angry at myself for not having seen this stuff sooner.

I went to the [[COLOR="Red"]Xubuntu Help & Support page[/COLOR]]("http://xubuntu.org/help").  I went there to see if I could find an official Xubuntu manual.  There is no official Xubuntu manual.  But there is an official manual for [[COLOR="Red"]Ubuntu 8.04 LTS[/COLOR]]("https://help.ubuntu.com/8.04/index.html").

Anyway, while I was on the Xubuntu Help & Support page, I found the following:

The [[COLOR="Red"]Xubuntu-users mailing list[/COLOR]]("https://lists.ubuntu.com/mailman/listinfo/xubuntu-users").

The [[COLOR="Red"]Xubuntu tech support system[/COLOR]]("https://launchpad.net/distros/ubuntu/+tickets"), which is a part of Launchpad.

When I get my head above water on the other work I have to get done, I am going to investigate the above support channels.  Maybe I could do a post and ask exactly what logs are turned off / do not exist in Xubuntu 8.04 LTS.  I think I might try this before trying the [[COLOR="Red"]Post #22[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9356838&postcount=22") Bash code.

---

