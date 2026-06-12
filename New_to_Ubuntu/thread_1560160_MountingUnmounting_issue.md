---
title: "Mounting/Unmounting issue"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by BobJam on 2010-08-24
I want to move a folder from my /dev/sda6 to my dev/sda1.  My dev/sda/6 is the partition where /home/<my user name> is mounted.  (And no, this folder is not part of /home/<my user name> . . . I'm calling it "used to be <my user name>" so it's a separate folder in /home and the path is /home/used to be <my user name>.  It's my old home folder from a previous version [don't ask . . . long story]).

The reason I want to do this is because my sda6 partition only has 14GB left, while sda1 has 74GB free space.  And as I download more apps and make settings for them, my /dev/sda6 partition nears completely full.  I'm starting to get nervous.  More than 50% of it is taken up by "used to be <my user name>"

Here's my gparted screenshot:

[IMG]http://i38.tinypic.com/20zqvlc.jpg[/IMG]

I would assume this involves some unmounting and mounting, but I don't know the specific commands or how to do it, or even if it can be done (I assume so though).

My understanding is that folders cannot be unmounted unless you are outside the system.  So would I need to do this with a System Rescue CD or a LiveCD?

As I'm sure you can see, I'm totally ignorant about this mounting and unmounting stuff.

I also have an unallocated partiton of 71GB, so would it be easier to put it there?

I really need step-by-step instructions on how to do this.

(BTW, from time-to-time I grab a file from /home/used to be <my user name> and put it into /home/<my user name>, so whatever the solution I need access to this folder.  I assume that would be the mounting part.  But first I'm guessing I need to unmount the thing.)

P.S.  In the alternative, I guess I could shrink my sda1 and enlarge my sda6 instead of doing all this mounting and unmounting stuff.  Indeed, my sda1 is wayyyy too big for just the little I have in /.

---

### Post by Silent Warrior on 2010-08-24
I agree with your PS, I was just going to suggest something to that effect. How's it going?

---

### Post by BobJam on 2010-08-24
The drawback to the partition resizing solution is that there is the risk of corrupting the data, though that risk is low and that's probably the way I'll go . . . especially since I've done that before and pretty much know what I'm doing, whereas I'm totally ignorant when it comes to mounting and unmounting and have never done that before (except on installation).

Nevertheless, I'd still like to know how something like what I describe in my OP would be done with the mounting method . . . even though I'll likely not use it.  Am sure that sooner or later I'll have to struggle with this mounting stuff, so better to get my arms around it when it's not an "emergency".

(BTW, I did one time grapple with the mounting stuff [here]("http://ubuntuforums.org/showthread.php?t=1498957") and I failed miserably until user wierdtalk kindly walked me through it.)

---

### Post by BobJam on 2010-08-25
Success . . . just did a resize of the partitions (using GParted on SRCD) and it went fine.  Now I have plenty of room in my sda6 . . . and sda1 is shrunk down to more realistic space for /.

But I'd still like to know what the mount/unmount method would be for this, so I'm not going to mark this solved just yet.

---

### Post by QLee on 2010-08-25
[QUOTE=BobJam]
But I'd still like to know what the mount/unmount method would be for this, so I'm not going to mark this solved just yet.[/QUOTE]

There is no "mount/unmount method" you would move (command, mv) the folder in the mounted filesystem. ...or copy it to the place you want it then delete the old one.

---

### Post by BobJam on 2010-08-25
@ QLee,

Wait a minute . . . wait a minute.

You mean simply using the mv command would take it out of sda6 and place it in sda1?

I'll just use <example> for the folder.  So the path would be /home/<example>.

Now I don't want to move or copy it to another folder, I just want it mounted on sda1.

So, what would the actual command line, using mv, be?

---

### Post by QLee on 2010-08-25
[QUOTE=BobJam]...
Now I don't want to move or copy it to another folder, I just want it mounted on sda1.
[/QUOTE]
  
Well, you started this thread with[QUOTE=BobJam] I want to move a folder from my /dev/sda6 to my dev/sda1.[/Quote]

Maybe you don't understand mounting, in which case reviewing this might help.
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by BobJam on 2010-08-25
@ QLee,

OK . . . sorry, clearly I don't have the lingo down.

So let's leave the word "move" out of it.

What I would like to see the commands/steps for is what I said in post #6:  I want the folder "detatched" from sda6 and "attached" to sda1.

I take it from your post #7 that I could indeed do what I want via the mount commands.

Thanks for your patience.

(BTW, I'm reading through the Ubuntu Community link you gave me on mounting . . . but if I could see the steps and commands to do this specific task, it might help me understand.)

---

### Post by formaldehyde_spoon on 2010-08-25
> **BobJam said:**
> @ QLee,

OK . . . sorry, clearly I don't have the lingo down.

So let's leave the word "move" out of it.

What I would like to see the commands/steps for is what I said in post #6:  I want the folder "detatched" from sda6 and "attached" to sda1.

I take it from your post #7 that I could indeed do what I want via the mount commands.

Thanks for your patience.

(BTW, I'm reading through the Ubuntu Community link you gave me on mounting . . . but if I could see the steps and commands to do this specific task, it might help me understand.)

Like QLee said, the easiest way would have been to copy and paste it from /home/XXX to /XXX.  This would have solved your problem.

You can't do it with moun/unmount.  You don't mount folders to partitions, you mount partitions to folders, and sda1 is already mounted at /, you can't also mount it somewhere else.  You could split sda1 into two partitions and keep the lefthand one mounted at /, and then mount the new empty one at /home/XXX.

Read this thread for some hopefully helpful info: [http://ubuntuforums.org/showthread.php?t=1506071](http://ubuntuforums.org/showthread.php?t=1506071)

---

### Post by BobJam on 2010-08-26
@ formaldehyde_spoon,

Thanks.  Am trying, and have been for quite a while, to get my arms around this concept.  I wonder if most noobs have trouble with this, or if I'm just particularly dense.

Am reading through the link you kindly provided, and also re-reading the Ubuntu Community article.  One of these days I hope to have the revelation and the "Aha" moment.

But for now I've solved the problem by resizing partitions.  So, I'll study up some, hope I "get it, and mark this as solved.

Thanks again to you and  QLee.

---

### Post by BobJam on 2010-08-26
@ formaldehyde_spoon,

Your post #20 in that thread link you gave me has a kewl drawing that seems to get me closer to getting my arms around all this stuff.  Still reading, but wanted to mention that you have my compliments for the effort I see so far in that thread.

Am getting closer . . .

---

### Post by BobJam on 2010-08-26
@ QLee,

From post #30 in that thread formaldehyde_spoon linked to:[INDENT]"[COLOR=Blue]*And of course we all know that with computer hardware and software, asking the proper question using the proper terminology is all-important to getting a usable answer.*[/COLOR]"
[/INDENT]This pretty much says why my OP was phrased misleadingly.

---

### Post by QLee on 2010-08-26
I don't know if this will help in your quest or not, but I do understand how mounting can be confusing. I think of it this way, each "mount" can be a discrete partition (volume) but, when mounted, becomes just part of the one big filesystem. So, if I take a file (or folder) which resides on the filesystem in a portion of the tree which is at a location in the filesystem where sda6 is mounted and move it to a location where sda1 is mounted then the file (or folder) is now on sda1. The partition sda6 now has free space equal to the file (or folder) size and sda1 now has that much less free space. But, the "filesystem" still takes the same amount of space in total. This would have accomplished what you originally proposed, and given you free space on sda6, equal to the size of the folder you mentioned.

Upon reflection, it appears your confusion stemmed from the fact that the folder you wanted to move was in ~home and you've probably read descriptions of "moving /home", which can be difficult for the inexperienced.

Actually, the way you enlarged the partition was probably the best solution to the original problem. Good choice.

---

### Post by BobJam on 2010-08-26
@ QLee.

Just curious then.  If I tried to move /home/xxx to / now, sda1 having been shrunk and now not having enough space to accommodate it, if I tried a copy and paste of /home/xxx to /, would I now get a "not enough space" type refusal?

Am tempted to try that, but prudence says I'd better wait for your answer.

(And BTW, when I say "/home/xxx", I'm talking about that "used to be <username>" directory, not "/home/<username>" . . . just using formaldehyde_spoon's shorthand).

---

### Post by BobJam on 2010-08-26
> **formaldehyde_spoon said:**
> You don't mount folders to partitions, you mount partitions to folders

@ formaldehyde_spoon,

I think this is helping.  Have to read that simple line over a few times, but I think maybe that's the key to getting my arms around this whole thing.

Wait a minute . . . wait a minute.

How does that jive with what QLee (and you) said about just copying and pasting my /home/xxx directory to / ?  Isn't that like trying to mount a folder to a partition?  Geeezzz, for a minute there I thought maybe I had it.

Hmmm . . . have to re-read some more.

---

### Post by QLee on 2010-08-26
[QUOTE=BobJam]
How does that jive with what QLee (and you) said about just copying and pasting my /home/xxx directory to / ?  Isn't that like trying to mount a folder to a partition?  Geeezzz, for a minute there I thought maybe I had it.[/QUOTE]

Trying to play us off against each other, eh? :-)

If you moved /home/xxx/ to /, you would then have /xxx/, not /home/xxx/. The /home folder would not move just because you moved one of it's sub-folders.

---

### Post by BobJam on 2010-08-26
> **QLee said:**
> Trying to play us off against each other, eh? :-)Not really.  If you'll notice, I said that you **BOTH** said this.

Or are you talking about the possibility that you'll each give opposing answers?  In that case, it will be interesting to see formaldehyde_spoon's answer.

Of course, with your emoticon, I take it this wasn't really a serious question.

> **QLee said:**
>  If you moved /home/xxx/ to /, you would then have /xxx/, not /home/xxx/. The /home folder would not move just because you moved one of it's sub-folders.

Yes, but now I don't think sda1 would have enough room on it for the xxx directory and it's subfolders and files.

Not sure I'm getting this though.  Again, an actual series of steps and commands might make it clear to me.  (With the caveat of course of "Don't try this at home.  Stunt was performed by a professional" . . . and of course I'm just an amateur.)

---

### Post by formaldehyde_spoon on 2010-08-27
> **QLee said:**
> Trying to play us off against each other, eh? :-)
...

:D 
> **BobJam said:**
> @ formaldehyde_spoon,

I think this is helping.  Have to read that simple line over a few times, but I think maybe that's the key to getting my arms around this whole thing.

Wait a minute . . . wait a minute.

How does that jive with what QLee (and you) said about just copying and pasting my /home/xxx directory to / ?  Isn't that like trying to mount a folder to a partition?  Geeezzz, for a minute there I thought maybe I had it.

Hmmm . . . have to re-read some more.

There is no mounting happening when you copy and paste some files. 
I completely agree with QLee: what you did was the best solution (it just wasn't the easiest). 
> **BobJam said:**
> Not really.  If you'll notice, I said that you **BOTH** said this.

Or are you talking about the possibility that you'll each give opposing answers?  In that case, it will be interesting to see formaldehyde_spoon's answer.

Of course, with your emoticon, I take it this wasn't really a serious question.

Yes, but now I don't think sda1 would have enough room on it for the xxx directory and it's subfolders and files.

Not sure I'm getting this though.  Again, an actual series of steps and commands might make it clear to me.  (With the caveat of course of &quot;Don't try this at home.  Stunt was performed by a professional&quot; . . . and of course I'm just an amateur.)

Partitions contain certain files/folders, and will ALWAYS contain those ones, unless you delete them, or create more (eg. move/copy+paste something from another partition).

Say you have three partitions: 

P1 has these files(by files I also mean folders):   usr, tmp, sbin, home, dev, mount, etc   -- and so on.  All the directories you see in / on your own computer
Note, for the sake of this example that mount and home are completely empty. 
P2 has: bobjam, usedToBeBobjam 
P3 has your movie collection: starwars.divx, watchmen.divx, madmax.divx 

You must have a partition mounted at /, and obviously P1 is intended to be mounted there, and is the only one that will work there (the others don't have the necessary system files), so lets's assume P1 is mounted at / 

You could (if it were possible to run Linux without any user data) now go to /home, and see that it is empty.
This is because at some stage (probably during install) you told Ubuntu that you wanted /home on a separate partition to /. 

You need mount a partition with valid user data to /home, and the only valid candidate here is P2. After it is mounted, if you go to /home you'll find that it isn't empty, it contains bobjam and usedToBeBobjam.  So /home/bobjam now exists, and holds all the account data Ubuntu needs to log you in.
Note that the contents of P1 and P2 have not changed. They still contain the same files as above. 

You want to access your movies in Ubuntu, so you need to mount P3 somewhere.  Convention says you should mount it in /mount or /media, but you can mount it anywhere you like. 
If you mount it in /mount, you will now have /mount/starwars.divx, and the others.  Valid, but a little strange to put files directly in /mount.
It would be better to create a folder in /mount called movies.

Before we do that, remember that the file system is an upside-down tree, with / at the top (the root).  The rule is: *everything* is on the / partition (P1) *unless* it's on a 'lower' partition, then *everything* in that subtree is on that new partition, *unless* they are on another even lower partition, and so on...

So **after** mounting P3 at /mount, if we created the folder /mount/movies it would be on P3 (because P3 is mounted to /mount).  Your divx files won't be inside /movies, they'll be next to it. So /mount/movies will exist (empty) and /mount/starwars.divx will exist...
What you want to do is create /mount/movies **before** you mount P3, so that it exists on P1, not P3, then mount P3 to /mount/movies, instead of the previous choice of mounting P3 to /mount.
Now your movies are in /mount/movies: /mount/movies/starwars.divx exists, for example.

The movies are still on P3 (remember everything is on / [P1] *unless* they're on a lower partition).  The movie files *are* on a lower partition: P3 at /mount/movies 

You could instead mount P3 to /home/bobjam/movies (*after* you create this movies folder here), and have /home/bobjam/movies/starwars.divx
Then everything in / would be on P1, except anything inside /home, because everything in /home is on P2, except everything that is in /home/bobjam/movies, because everything in /home/bobjam/movies is on P3...

Note all files/folders are still on the same partitions they were at the top.  The only difference to the contents of the partitions is that P1 has the empty(when the computer is off) folder mount/movies and P2 has the empty(when the computer is off) folder bobjam/movies 

Assuming P1 at /, P2 at /home and P3 at /home/bobjam/movies, if you move /home/bobjam/movies/starwars.divx to /home/bobjam/starwars.divx then you have deleted the file from P3 and moved it to P2.  If you now decided you want to mount P3 at /mount/movies instead, starwars.divx will still be on P2 at /home/bobjam/starwar.divx.  If you then move /home/bobjam/starwar.divx to /tmp/starwars.divx it will be deleted from P2, and moved to P1.

.....that is way too much text to be a clear explanation, but I guess it would be silly not to post it, so...

---

### Post by QLee on 2010-08-27
[QUOTE=BobJam]...
Of course, with your emoticon, I take it this wasn't really a serious question.[/quote]

That's why I used it. As usual when I divert from being serious and try to make a joke, it falls flat.

[QUOTE=BobJam]Yes, but now I don't think sda1 would have enough room on it for the xxx directory and it's subfolders and files.[/quote]

The key to your statement is the word, "now". You've already made the choice to expand the partition where /home resides. As I stated previously, I think it was the correct solution.

[QUOTE=BobJam]Not sure I'm getting this though.  Again, an actual series of steps and commands might make it clear to me.  (With the caveat of course of "Don't try this at home.  Stunt was performed by a professional" . . . and of course I'm just an amateur.)[/QUOTE]

But Bob, the original conditions under which you asked about "moving" that directory don't exist any longer, there is no longer any need to move it to create unused space on sda6 and, in fact, you state now there isn't room for the /xxx/ folder on sda1 so it would be pointless to try it.

As well as the community documentation, there are also the man pages. For example, if for some reason you wanted to research what the mv command does, you could open a terminal and enter, man mv, that would open the manual page for the mv (move) command.

Different people learn with various different methods and at differing rates, if you keep at this the "aha" moment will come and then it will start to make sense.

---

### Post by BobJam on 2010-08-28
@ formaldehyde_spoon,

> **formaldehyde_spoon said:**
> :D .....that is way too much text to be a clear explanation, but I guess it would be silly not to post it, so...

Well . . . yes, it is a lot of text, BUT if I relate it to some of your drawings in that other thread, I think maybe it will become clear.  I think if I read over it a few times, this one may finally put me over the top.

You certainly have this stuff down.  Assuming it didn't all come to you in a vision, am curious . . . how long did it take for you to achieve the mastery on this topic that you obviously have?

(And lest you think you're being left out, QLee, you also have mastered this topic well.  Someday, I hope to climb the mountain that you guys have conquered.)

In any case, THANKS for all the effort here, formaldehyde_spoon.

---

### Post by BobJam on 2010-08-28
@ QLee,

> **QLee said:**
> As usual when I divert from being serious and try to make a joke, it falls flat.No, I got it . . . is just that I'm cranky and humorless most of the time.  Definitely a character flaw (and my inability to grasp this concept isn't helping either).   People who have no sense of humor generally have no sense at all.  Thanks for reminding me that I need to stop and laugh now and then.

So, it was not that you "fell flat" in the attempt . . . it was my sour puss.

> **QLee said:**
> The key to your statement is the word, "now".So I take it you agree that it wouldn't work **NOW**?

> **QLee said:**
> Different people learn with various different methods and at differing rates, if you keep at this the "aha" moment will come and then it will start to make sense.Yes, you can be assured I will "keep at it".  This is one of those challenges that will stay active 'till I beat it.

Curious . . . if you can remember, was there any one thing that put you over the top on this concept, or was it just that all the accumulated sources finally came together at once?

Also curious, do you think this particular topic is one that most noobs have trouble with?

---

