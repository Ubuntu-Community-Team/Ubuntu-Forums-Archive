---
title: "Tips on getting organized before I go much further?"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by smcrossman on 2011-05-31
Okay...in the last 2 (or is it 3?) weeks I've upgraded to Natty on my old beyond hope PC, installed Natty dual boot on my current PC, and installed Natty on my netbook.  I've done away with MS Outlook...now using Google Calendar to sync up between evolution & iPhone. I've dealt with NVidia issues, and am slowly learning my way around Unity. Still working out the kinks in a lot of areas, but I'm realizing that I had better get organized or I won't remember what changes i've made on which computer or where to find files, etc.

Any suggestions on organizing files? Everything from themes, icons, pictures, contacts, calendar, recipes, medical information/records, major financial documentation, to standard emails, faxes, documents and various grabs off the inter net.  I am also in the process of trying to become fairly paperless.  Bill statements will be scanned for record-keeping and all the financial tracking will be spreadsheeted (I have a ton of medical stuff so this is the only way I've found to accommodate all the needs.  I'd like to be able to access most any record/document at any of my 3 computers, and if possibly while on the go.

Pictures and music will have to be addressed but those can wait for a bit. Most of what I found on searching dealt with music.  I figure if I have my base file system lined out and in operation then the music/photos will be easier.

Finding desktops, backgrounds, icons, etc that I've installed and then being able to use them is already a problem.  I'm having permission issues or location issues, then issues with permission to move them. 

I won't even mention (ha, ha) about the rather large file of "sound effects" I've kept of mostly *.wav files with a few others thrown in that I like to use for my alarms and event sounds. That is just a big file of sounds in alpha order...with no rhyme or reason.  Some are worth keeping others are just standard dings, and beeps. 

Anyway....as is obvious I will be making a lot of changes, installs, uninstalls, tweaks, etc over a LONG period of time.  How do I best set myself up so I'm not going crazy with what went where or was this done or not?  

Oh, I suppose a good first step would be actually learning about Samba...is there a good resource just for that? So maybe I can develop consistency across my little network!

Thanks for any leads, tips, etc.  If I need to split this up somehow and place it in different locations let me know!

---

### Post by P=NP on 2011-05-31
Everything should be kept in your /home folder. If you back this folder up all your settings and documents will be easy to recover if you bork something.

As far as tweaks go, start an empty file and keep all your commands in there. That way if you need to reinstall you could just run them all consecutively without forgetting anything.

I would suggest staying away from Samba and learning about SSH and SSHFS.

---

### Post by smcrossman on 2011-05-31
Thanks for the recommendations.  I have started copying information (from forums, blogs, documentations) I've needed & used on any one of the PCs into tomboy in a separate notebook. They sync up in U1 and I can refer back to them so much quicker.  I hadn't thought about keeping a command log...That wouldn't be much different, but more condensed and if I do a separate one for each machine I can then figure out what has been done where (hopefully!

Samba came up automatically when I started trying to network locally. What exactly are SSH and SSHFS?  How's that for a newbie question?  I'm just starting to try to figure out whether when looking at software packages I need Deb, KDE, GNU, etc.....if it seems like something I can use and it installs I check it out, but that is surely going to lead to problems!  LIttle (basically no) programming background other than dabbling and all I know is that the languages I was exposed to didn't play so well together most of the time.  Here in Ubuntu land it all seems kind of mish-mashed.

Everything in the home directory. I can create directories, folders files....all in whatever filing system seems to work for me....hmmmm.....I guess I better find out about naming requirements/limitations....?  This could be fun!

---

### Post by Carcharoth on 2011-05-31
> **smcrossman said:**
> This could be fun!

no,this will be fun. I started years ago, and never completely committed until a few weeks ago. I have a mission critical application, Autocad, and I had been told that it would run under Wine, but that the setup was nearly impossible.

it's not impossible. autocad actually runs a tad quicker in Meerkat, in my opinion, for the work I do.

Samba was kind of the same. I had been told it would work, but not specifically how one set it up. I forget where I was poking around, but the first time I found it in my set up, everything installed more or less automatically.

Ubuntu works better on my windows network than windows works on my windows network. if there are any drawbacks to Samba, I have not found them. ( but I keep an open mind )

best wishes.

---

