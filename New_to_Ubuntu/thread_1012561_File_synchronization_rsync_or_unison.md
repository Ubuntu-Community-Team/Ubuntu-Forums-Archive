---
title: "File synchronization: rsync or unison?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by BlakeM on 2008-12-15
**What I would like to do:**

I intend to use an eee pc at uni to take electronic notes, send emails, record lectures, etc., on the move. Because the eee pc doesn't look very comfortable to use and has very little storage, I would like to use a desktop computer at home. I would like to have the files synchronised automatically between the two computers whenever a change is made.

Given the small storage available on the eee pc, which in your opinion is a better option:

[LIST=1]
[*]Have multiple folders set up to use remote, two-way sync using rsync/unison; or
[*]Have all files stored on the desktop and temporarily copy files to the eee pc when I need to edit them. After editing, have changes synced back to the desktop and file removed locally? (Not sure if this is possible?)
[*]Any other method?
[*]Is what I want even possible?
[/LIST]

I'm aware of dropbox and similar services but I am concerned with privacy issues and the limited storage allowance. I'm also not interested in web interfaces. This is something I'd enjoy if I could set it up myself.

Also, I'm reading about them both now, but what's the difference between unison and rsync? rsync sounds like it can already do what unison can?

---

### Post by jbrown96 on 2008-12-16
I use rsync on a single machine to do backups. I find that it doesn't work nearly as well as I imagined. It doesn't seem to know which files are already present and copies them each time. It doesn't have multiple copies of each file; it just overwrites them for some reason. I'm not sure how much data you are talking about, but when I'm syncing 500-700GB it really adds up.

I'm not sure whether you will have internet access in class and how reliable it is, but sshfs might be something to look into. It's very easy to setup a server (just need a ssh server -- sudo apt-get install openssh-server) and connecting on a client is also very easy. In places, you can "connect to a server" and have it remember all your settings and create an icon on the desktop. This way you will never need to use any storage on the eEe, unless the network is available. 
Obviously, this depends on an internet connection that is 1) always available, 2) very reliable, and 3) has a port that you can use for ssh. At my school, we have two wireless networks; one is secured and all the ports are open (ssh isn't a problem), but the unsecured network is worthless except for browsing. 

I think you might be surprised how little storage space "notes" and "lecture recordings" take, especially if you do nightly transfers. 

I don't know much about unison (I took a short look at the website), but it doesn't seem to offer anything that rsync doesn't, except a Windows client. I would go with rsync; it's been tested for many years and is widely used on production systems.

---

### Post by Zack McCool on 2008-12-16
> **jbrown96 said:**
> I use rsync on a single machine to do backups. I find that it doesn't work nearly as well as I imagined. It doesn't seem to know which files are already present and copies them each time. It doesn't have multiple copies of each file; it just overwrites them for some reason. I'm not sure how much data you are talking about, but when I'm syncing 500-700GB it really adds up.

That's not how rsync [should] works...   rsync should (and does here) check for updated files, and only replace those with a newer date on the source.  If there are any changes to a file, it will be updated or replaced.

> 
I don't know much about unison (I took a short look at the website), but it doesn't seem to offer anything that rsync doesn't, except a Windows client. I would go with rsync; it's been tested for many years and is widely used on production systems.

I am unfamiliar with Unison as well.  Personally, I'd stick with rsync as it is tried and true, and if you do need to do updates remotely, it is designed to work well over SSH.  Set up the rsync daemon on the server, with SSH as the transport, and you get excellent speed with maximum security...

---

### Post by scorp123 on 2008-12-16
> **Zack McCool said:**
>  I am unfamiliar with Unison as well.  You should give it a try then. It has a nice GUI front-end too that will inform you of file conflicts if it detects any.

> **Zack McCool said:**
>  Personally, I'd stick with rsync as it is tried and true Same can be said about Unison. Besides: Unison works tip top across operating systems as it exists for Linux, Windows and Mac.

---

### Post by Paqman on 2008-12-16
> **BlakeM said:**
> 
[*]Any other method?


Save your documents to an SD card on the eeePC. Get a card reader for your desktop (they're ridiculously cheap, and plug straight into a USB header). Just yank the SD out of the eeePC and stick it into the desktop. Job done.

---

### Post by Zack McCool on 2008-12-16
> **scorp123 said:**
> You should give it a try then. It has a nice GUI front-end too that will inform you of file conflicts if it detects any.

I don't generally want a gui for this type of operation.  I prefer a shell script, and a crontab entry.  Is unison scriptable, or is it exclusively gui?

> 
 Same can be said about Unison. Besides: Unison works tip top across operating systems as it exists for Linux, Windows and Mac.

rsync works just fine on all 3 as well...   Again, it's just not a gui, which is probably why I like it so much...   I use rsync under cygwin to keep my Windows servers backed up, and it works a champ...   ;)

---

### Post by Zack McCool on 2008-12-16
OK, for grins, just installed unison, and testing it now.

First thing: Unison works both ways.  It compares both filesystems and tries to synchronize them with the newest files to both, and asks when there are conflicts.

Next: Unison is incredibly slow the first time it is run, while checking differences between 2 roots.  I'll have to see how it runs thereafter, but considering what I need it for, this is probably an unnecessary delay.

Last: Unison does seem to have a terminal-only mode, and I haven't looked at it yet to see how it works.  

So, if you want a GUI, or need the ability to synchronize 2 filesystems moving the updated files both ways, Unison will do that.  If you are looking to just make backups from an active source to a backup location, it seems that rsync is better...

---

### Post by BlakeM on 2008-12-16
Wow...thanks for the quick replies. Really appreciate your time and effort.

I should mention that I'm very new to Ubuntu (almost a month now). Before I switched to Ubuntu I was using XP and the only thing I used CLI for was "ipconfig", lol. I'm at that stage where I'm still experimenting with CLI. I'm not afraid to learn more about it, but I must admit that it is time consuming.

>  I'm not sure whether you will have internet access in class and how reliable it is, but sshfs might be something to look into. 

From what a friend tells me, wireless covers almost the entire campus. Speeds shouldn't be an issue. SSH sounds promising. I did read about it before posting this thread but I found it pretty confusing. I'll read more tonight. From what I've gathered so far SSH is kind of like CLI access to a remote computer? Does it make temp copies of files locally and then remove them after editing? Or do I have this totally wrong...

> In places, you can "connect to a server" and have it remember all your settings and create an icon on the desktop. This way you will never need to use any storage on the eEe, unless the network is available. 

Do you mean: Wherever I am able to connect to a server I can have an icon on my desktop that points to a folder on the server? If so, are there any issues with latency? What happens when a connection drops mid-session?

> I don't generally want a gui for this type of operation. I prefer a shell script, and a crontab entry. Is unison scriptable, or is it exclusively gui?

From what I've read it does both? Might be wrong though.

I've thought of something else as well...If I choose not to have files stored locally on the eee pc then I risk not having access to my files if there's no internet connection. Maybe I could use a "dropbox" type folder for current work and archive older work on the desktop. I suppose I could still access these archived files using FTP and copy them locally if I needed to.

That SD card idea sounds very promising as far as simplicity is concerned. Being able to access older files on a server might come in handy though.

In the next couple of days I'll try setting up a remote connection between a laptop and a desktop and see how I go transferring files.

Thanks again for your time! :D

---

### Post by scorp123 on 2008-12-16
> **Zack McCool said:**
> I don't generally want a gui for this type of operation.  Understandable, especially if you want things to happen automatically via scripts.

> **Zack McCool said:**
>  Is unison scriptable  Of course! :)

> **Zack McCool said:**
>  rsync works just fine on all 3 as well...  Cygwin can be a pita. Unison's windows GUI port solely depends on GTK+ which is easily installed, and the command line version is a stand-alone *.exe with no other dependencies whatsoever. So you can use it to automate things on Windows too (e.g. via the "Task Scheduler").

So as soon as Windows is involved I tend to prefer unison. On Linux and Solaris I use "rsync" a lot too.

---

### Post by scorp123 on 2008-12-16
> **Zack McCool said:**
>  Next: Unison is incredibly slow the first time it is run, while checking differences between 2 roots.  It does some hashing, checksumming, and so on the first time it has to compare directories. But after that it's pretty neat and fast.

And yes, the advantage is that it can compare stuff both ways. That's a nice feature as soon as more than two machines need to sync!

> **Zack McCool said:**
> Last: Unison does seem to have a terminal-only mode, and I haven't looked at it yet to see how it works.  Please take a look here if you want to read more:

[http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html](http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html)

Syncing between Windows and Linux:
[http://hamed.dk/home/45-unison](http://hamed.dk/home/45-unison)
[http://blog.kowalczyk.info/articles/usingUnison.html](http://blog.kowalczyk.info/articles/usingUnison.html)

What I do:

I use SSHFS for Windows:  [http://dokan-dev.net/en/](http://dokan-dev.net/en/)
This allows me to access remote Unix or Linux SSH servers by mounting the remote folder via SSH (yes, just as you would do in Gnome!).

From Unison's point of view both the local folder and the remote SSH location are local subdirectories, so I don't have to worry about SSH tunnelling via putty, cygwin tools, or something like that.

It works pretty nice so far.

Linux-to-Linux syncing is even easier, just use "rsync" or "unison" on both ends, have both use "scp", and voila, done. :D

---

### Post by Kellemora on 2008-12-16
Hi Blake

One thing to watch closely for is that you DO NOT have the DELETE On Receiver button checked when using Rsync for both directions, or for one direction for that matter if you only have SOME of your files on the portable.  Delete REMOVES any files NOT in the Source Folder when you run it.

In other words, if you download a document to edit, then go to write it back using Rsync and that's the ONLY document you downloaded to work on.  Delete will ERASE all the other documents in that folder, since they are NOT on the Source.

Just a heads up is all!

TTUL
Gary

---

### Post by BlakeM on 2008-12-18
> **Kellemora said:**
> Delete will ERASE all the other documents in that folder, since they are NOT on the Source.

Just a heads up is all!

TTUL
Gary

Hey Gary,

Thanks a lot for the heads up :|. Probably saved me at least an hour of my life ;-).

Blake

---

