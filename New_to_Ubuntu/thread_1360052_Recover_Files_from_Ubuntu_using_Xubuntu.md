---
title: "Recover Files from Ubuntu using Xubuntu"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by bgphelps on 2009-12-20
Hi folks,

I would like to know if there is any way I can recover my personal documents (specifically Documents and Pictures folders) from Ubuntu using a Live Xubuntu USB (9.10). I plan on installing Xubuntu but want to restore my files first. I am presently unable to boot Ubuntu because every time I load I receive the message 'Gave up waiting for the root device.' Since I was planning on switching to Xubuntu anyway it didn't seem worth it to trouble-shoot this issue if I can easily retrieve my documents through the Live USB

That's basically it, if there is more information that is needed let me know please, also, I am living/working in Peru and where I live there is no internet so please don't give up on me if I don't respond immediately. I should have internet tomorrow afternoon/evening (Dec 21) and after that on the 28th.

Much thanks!

Brian

---

### Post by Sef on 2009-12-20
Run Xubuntu as a Live CD.  If you go into your home folder (or where ever they are), you should be able to see them and copy them to a flash drive.

---

### Post by bgphelps on 2009-12-20
Thanks for the prompt reply.

I just made a Live CD and am running Xubuntu 9.10. The Home Folder but all the folders within it (Documents, Music, Pictures, Video) are empty. 

Possible reason: When first running the Live USB I clicked on the install button, thinking that I would just take the hit and lose those files. Then, when it reached the first installation screen, I decided I would at least give it a shot to save those files, since although they're not terribly important, I'd still like to have them. I hit escape, and instead of quitting the installation it just immediately opened up the Xubuntu desktop. I assumed it just switched to a Live USB 'try out Xubuntu without making changes' mode since all of this happpened in less than 30 seconds. Also, running my laptop without a Live CD or USB just runs it like before so I really don't think changes were made. However, maybe in that short time I managed to eliminate these files?

Also I'll have internet access all evening but tomorrow no.

Much thanks

Brian

---

### Post by laidback on 2009-12-20
Think you're in the wrong place. The Live CD has a load of directories within it which are probably the ones you are looking at. You need to navigate to the HDD that your original OS is on. Look for File System in the file browser window, then "home" then you should see your own name or the name you've given your own home directory on the original OS. Go into that and up will come all your directories and data.

---

### Post by bgphelps on 2009-12-20
> **laidback said:**
> Think you're in the wrong place. The Live CD has a load of directories within it which are probably the ones you are looking at. You need to navigate to the HDD that your original OS is on. Look for File System in the file browser window, then "home" then you should see your own name or the name you've given your own home directory on the original OS. Go into that and up will come all your directories and data.
Thanks laidback,

Starting in File System, there is only one Home folder to click on. I click on it and my old personal folder ('Brian') is no longer there. The only option is 'Ubuntu' and the folders there remain empty. I searched through the file system using the terms 'Brian' , 'Yo Yo Ma' , and 'Bon Iver' (some music I had in the folder). No files were found under any of these searches. I also opened up the CD directly and did not find my folders in there either. Is there another way to open these folders that I am missing?

Thanks!

Brian

---

### Post by audiomick on 2009-12-20
Hallo.
I've just booted mine up into the 9.10 live cd to have a look.
My home folder, which is a separate partition, turns up in "places" as "497GB Dateisystem" . Mine is in German, Dateisystem means File system. It is below the icon for "computer", along with all the other partitions on my 2 discs.

If I click on "computer", a file browser window open which they are all in.

---

### Post by bgphelps on 2009-12-20
> **audiomick said:**
> Hallo.
I've just booted mine up into the 9.10 live cd to have a look.
My home folder, which is a separate partition, turns up in "places" as "497GB Dateisystem" . Mine is in German, Dateisystem means File system. It is below the icon for "computer", along with all the other partitions on my 2 discs.

If I click on "computer", a file browser window open which they are all in.
My screenshot button doesn't seem to be working (let's just leave that one alone), so...

When I click on 'Places' I receive the following options.

'ubuntu'
'Trash'
'Desktop'
'File System'
'Xubuntu 9.10 i386'
'Search for Files'
'Recent Documents'

No other file systems appear except the one listed, and inside of that I have run the searches and cannot find my files : /

Right now, I'm downloading Ubuntu 9.10 to create a Live Disc, not sure if giving it a shot in Ubuntu as opposed to Xubuntu will make a difference but I can't see a reason not to try. 

Danke Sehr! I appreciate you taking the time to load that up and take a look!

Brian

---

### Post by audiomick on 2009-12-20
Ok. Good luck with it. I have to go to bed soon, but I will look back in tomorrow at some stage to see how you went.

---

### Post by laidback on 2009-12-21
This is a little odd as every Live CD I've tried has given me access to my HDD, I tried several Ubuntu ones since 6.06, Puppy Linux, DSL, etc. Anything that comes my way really.
From the list you give I'd go for File System.
Let us know how you get on with 9.10.

---

### Post by snowpine on 2009-12-21
You do not need to reinstall to switch from Ubuntu to Xubuntu. They are just different desktop environments (Gnome vs. Xfce), same core system.

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by audiomick on 2009-12-21
> **snowpine said:**
> You do not need to reinstall to switch from Ubuntu to Xubuntu. They are just different desktop environments (Gnome vs. Xfce), same core system.

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

This is true, but I think his system is broken. See post #3

@ laidback: in post #7, Brian indicates that he looked in "File Sytem" without success.

My next bet would be, from Brian's list, in "ubuntu" or in "Xubuntu 9.10 i386". Does anyone know for sure which is the live CD system for the Xubuntu Live CD he was trying with?

---

### Post by bgphelps on 2009-12-21
Hey friends,

So I am currently running on a Ubuntu 9.10 Live CD, I wanted to see if it would make any difference. Here, I did find my HD (40 GB Hard Disk: 4) by clicking on 'Computer' under places, I even found my folder 'Brian'. Yet, it was too good to be true. Within the folder there were only two sub-folders ('Desktop' and 'Examples') and neither had my files.

So, after playing around with foremost for a little bit, I've decided that I'm going to do a clean install of Xubuntu to see how I like it. Pretty much all of my files were backed up in my external anyway, so it's not much of a loss. And I feel like now, in normal circumstances, I theoretically know how to get my files back (or even someone else's files who is running Windows), so I'm better for the experience ;)

Thanks everyone for your help! This was my first time using the forums and I'm impressed by everyone's friendliness, helpfulness, and general good nature!

Best wishes,

Brian

---

### Post by audiomick on 2009-12-21
Have fun with Xubuntu then.

---

### Post by bgphelps on 2009-12-21
That sounds ominous but will do : )

---

### Post by bgphelps on 2009-12-21
One last question I suppose.

Is it proper forum etiquette to now mark this thread as solved, although we didn't technically reach the hoped for conclusion?

---

### Post by audiomick on 2009-12-21
Yes, do that please.

---

