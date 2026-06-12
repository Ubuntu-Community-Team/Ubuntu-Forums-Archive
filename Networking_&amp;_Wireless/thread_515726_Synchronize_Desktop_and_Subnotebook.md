---
title: "Synchronize Desktop and Subnotebook"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by atomic_turtle on 2007-08-02
Hello,

I've got a Desktop PC currently running Kubuntu Edgy and a Subnotebook running Xubuntu Feisty. Does anybody know of any possibilities to synchronize different machines? There's a component "Synchronize" in Kontact which I could install on my Xubuntu machine - I haven't yet found any proper documentation or Howto regarding this (kitchensync), but there must be other possibilities, too. After all, Ubuntu was created as a networked system, no?
Thanks for any tips!
Best regards,

atomic_turtle

---

### Post by networkr on 2007-08-02
If you're talking about just document synchronization, I'd recommend 'rsync' combined with 'cron' or other scheduling program to keep all your files in sync with one another.  Keep in mind, rsync only works in one direction, so if you edit on both platforms and want the latest at all times on either machine, you'll have to issue two rsync commands, one northbound (e.g.  laptop---> desktop) and one southbound (e.g.  desktop---> laptop).  The link below has a nifty gui if you want to just do it manually.

    [http://packages.ubuntu.com/edgy/x11/grsync](http://packages.ubuntu.com/edgy/x11/grsync)

Unison is also an option, which does both directions, but does not enjoy the ubiquitous community support of rsync.

There's another neat sounding program for syncing other information in Mepis, another fork of Unbuntu which also might suit your needs at the following link:

     [http://www.mepis.org/node/10751](http://www.mepis.org/node/10751)

Best of luck,

networkr

---

### Post by atomic_turtle on 2007-08-03
Hi networkr,

thanks, I'll try that.
No, I'm not talking about document synchronisation, I want to synchronise my emails, contacts, calendar and notes (well, those are all documents of some sort...)
I find it a little amazing how in forums for a system that was actually written to be used as a networked system nearly no one seems to have ever tried to sync different computers... or is it just so easy that no one bothers to grapple with such a trivial question? How about syncing a Desktop with a Smartphone? I'm considering buying one and then I'd like to sync all three - Desktop, Notebook and Mobile.
Well, I'll be sure to try out your tip! Thanks!
Any other tips would really be appreciated as I'm a bit lost.
Regards,

atomic_turtle

---

### Post by kevdog on 2007-08-04
Not exactly sure the point of your post.  All the things you want to sync are files kept in directories, so you can mirror and synch these directories/files.

I use unison -- its easy to set up -- and its based on the rsync algorithm. It does enjoy good support with a yahoo list --- and it does have a gtk gui.   Im not sure if it would work from a phone -- possibly I dont know much about it.

---

### Post by atomic_turtle on 2007-08-07
Hi,

I was actually just thinking of that myself. Probably all the files containing my emails, contacts, calendar entries and notes (all in Kontact) are stored somewhere in my home directory, probably all in .Kontact or so?
It should be easy to set up a synchronization mechanism using rsync or unison on those directories. Would the respective applications then automatically draw on the always updated files? That would be all I need, actually.
I just bought the Linux magazine 08/2007 in search of a solution to this. It didn't contain what I wanted, but there is a lot of stuff about synchronizing Handys and PDAs, so I'll keep that.
Thanks a lot!
Regards,

atomic_turtle.

---

### Post by kevdog on 2007-08-07
With both unison and rsync you specify a pair of root directories (one on the server, and the other on the client).

In interactive mode with unison, when it detects a difference in the two replicas (for example an update copy of one file compared to the old version on the other machine) if will ask you which replica you want to transfer.

To automate the process, you can give the program preset algorithms to specify for example replica #1 always takes precedence over replica #2 (or vice versa), or the file with the newer file creation time (inode number) always takes precedence over a file created previously.  

Running unison in interactive mode a few times, allows you to "test" your automation parameters, and actually look at what the program is going to change before doing so.  If you dont like it, you can kill the program and then use a different algorithm -- in this case nothing was created or destroyed.

I believe Unison runs rsync down below, however has just added another top layer onto the program to add various features, a gui, etc.

Its actually very easy to use, although it does take some time to read through the documentation.  Again if using a windows machine as one of the replicas, I believe you need to install cygwin first, to use either rsync or unison (I think, unless you just want to install putty which acts as to make the ssh connection, and then run the unison binary ontop of putty -- I know this can be done since I at one time used putty/unison to synch my USB stick from a remote location several times a day.)

---

### Post by atomic_turtle on 2007-08-07
Windows? Brrrhahua! Nooo! I count myself lucky to have gotten rid of the stuff.
Okay, maybe it would be nice if I could synchronize with my work PC - but that is running Lotus Notes, not the usual Outlook. First I will try to get my own Desktop and my own Notebook synchronized, then I'll add my own cellphone to the pair and when that works, I might think of syncing my office machine.
Thanks a lot!
Regards,

atomic_turtle

---

### Post by kevdog on 2007-08-07
Let me know how the cellphone goes -- because I bet that is going to be a no go.  Both rsync/unison work over a ssh connection.  Id be surprised if your cell phone has installed by default a ssh client.  The only way I could think this would be possible is if you had some wired connection to one of the computers and the computer detected this phone as another hard drive (local hard drive) or something similar.

---

### Post by atomic_turtle on 2007-08-08
Hi kevdog,

I'm not thinking of syncing my cellphone using rsync or unison. I don't have a very sophisticated phone, so the chances of doing that are near zippo. I read in another post that my model (Sony-Ericcson K700i) can be synced by bluetooth. I'll try that, but I guess I'll have to buy a bluetooth dongle for my Desktop has no interface for that and my notebook neither.
Let's see. First things first, so I'll start out by trying to sync my Desktop and subnotebook.
Regards,

atomic_turtle

---

### Post by atomic_turtle on 2007-08-12
Hi kevdog,

in the meantime I've come across an alternative that I might try: OpenSync. It's a tool specifically for the purpose of syncing several machines and even cellphones. At the moment, there's only a plugin for Motorola listed in the UU Wiki and I have a Sony-Ericcson, but it might be worth a shot and if it's good, my next phone will be a Motorola.
rsync has the undeniable advantage of also working between Linux and Windows machines, so in principle I could sync my home and work PCs or for example share my calendar with someone using Windows. Well, I'll try it and see.
Regards,

atomic_turtle

---

### Post by atomic_turtle on 2007-08-17
Hi,

I haven't yet had the time to actually try it, but I've read something about Unison - seems to be pretty easy for syncing files and directories. 
Has anybody actually tried syncing several machines and could tell me if/ why either Unison or OpenSync would be better suited for the purpose?
Thanks a lot!
Regards,

atomic_turtle.

---

### Post by kevdog on 2007-08-17
Never heard of opensync until you mentioned it, then I went through their pdf presentation.  Seems like a new technology atttempting to sync smaller devices -- has to do intermediate data conversion into xml.  Seems quite new.

What do you want to do?  Unison/Rsync can synchronize large files -- no intermediate xml translation -- although really only works well in client server relationship -- or spoke/wheel pattern.  Opensync looks better for syncing info between unlike smaller devices via an xml intermediate that can do the translation into the appropriate format.

You could try both, and report back.

---

### Post by atomic_turtle on 2007-08-28
Hi kevdog,

sorry, I didn't have an opportunity to look in here for a while.
Well, what I'd like to do is sync unlike devices - Desktop, Notebook and mobile - so Opensync seems worth a shot. But for now, those plans are on ice. I'm waiting for the enduser version of the OpenMoko OpenSource-mobile to come out in October. As that will run Linux, syncing should be quite easy. So, all that remains for now is my Backup-routine. I still haven't finished that, I kind of let it rest near-finished. I often do that, which is actually stupid because it then takes much longer to get into the stuff again and finish it. Once that's done, I can look at syncing my Desktop and Subnotebook again. 
Regards,

atomic_turtle.

---

