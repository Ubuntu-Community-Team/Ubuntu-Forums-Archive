---
title: "Standard Partitioning Plan for All My Ubuntu Installs"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by brucewagner on 2010-04-25
I'm installing Ubuntu on hundreds of machines -- all different hardware -- and want to standardize things in an intelligent way. 

The "remnants" left behind in the /home partition after a fresh install (when /home is a separate partition) , I don't like. 

On the other hand, I want to be able to easily reinstall the Ubuntu OS and all apps 1-4 times every six months.  That's 2-8 times per year!

It makes no sense to me to backup, and then restore, up to 500-600GB of user data EVERY TIME -- not to mention that it's taking a huge risk of losing that data... each time. 

Like you should be, I'm concerned about making my / partition ( which includes /home ) too small.  I'm also concerned about making my swap partition too small (for example, in the case of a tower with 8GB or more of RAM, and I want it to be capable of using the Hibernate function).

That's why the "standard" configuration I am proposing is:

Three partitions on every machine:

50GB for /
      ( where the /home is in this partition too )
10GB for swap
All Remaining Space for /data

On a re-install, the / is formatted (including the /home) , but the /data is not touched. 

This way, Ubuntu, Gnome, and all software, finds the / and /home in the same partition, and cleanly freshly installed -- as any normal install would be. 

Yet, the users data ( on /data which could be 600GB ) never needs moved because it is never touched. 

Of course, I still advise users to backup their data before re-installing the OS,  but at least they don't need to restore from backup.  And even if they don't backup, their data shouldn't be touched anyway.

Giving the / partition 50GB should easily provide enough space for Ubuntu and all the dozens of apps I install ( grand totalling 9.4GB ), plus another 40.6GB which the user can use for any combination of:  additional apps, possible virtual machines, temporary workspace,  and/or temporary download space. 

Make sense?

---

### Post by Sef on 2010-04-25
> That's why the "standard" configuration I am proposing is:  three  partitions on every machine:

50GB for /
      ( the /home is in this partition too)
10GB for swap
All Remaining Space for /dataFor root (/), 10 gb is big enough.  If you want to make it 15 gb, you could too.

For swap, it should equal your ram.   This is so hibernation will work. 

For home, the rest of the hard drive.

This way you can reinstall and not worry about the data on home.  When you reinstall with a home partition, you only format the root and the swap partitions.  Of course, always back up your data before reinstalling.

---

### Post by QIII on 2010-04-25
There is no "Standard"

Are you expecting multiple users per machine?

Create separate /home partitions.   Don't leave them under /.

For instance, create 3 partitions: /, /home, /swap. (If you want to make one for /data you can, but you could also just use /home).

When you reinstall, manually  create partitions and do not recreate or format the /home partition but leave it  there.

Make your / partition somewhere between 10 and 30GB.  30GB is really  probably way too big, unless you anticipate installing a lot of  applications.  (By default, your virtual drives for your VMs should be created in /home.)

Make your /swap partition about 1.25x the size of your RAM.

Use whatever is left for /home.  As I said, when you re-install, do not re-create or re-format /home.

Edit:  Sorry, Sef.  I must have been typing when you were.  I'm balancing a foster kid on my knee while he watches a movie on one screen and trying to type around him!

---

### Post by brucewagner on 2010-04-25
Thanks but did you guys read my post?

I have a need to create one standard for the hundreds of machines I am installing Ubuntu on. 

Did you read my comments on the negative effects of "remnants" left behind in the /home directory, on a reinstall...?

And the occasional problems that can occur when an app expects the /home to be on the / partition...?

Also, the part about:  If you want a machine to be able to Hibernate, the swap partition needs to be LARGER than the amount of RAM you have...?

And the part about allowing lots of extra space in / to allow for the installation of virtual machines,  lots of temporary download space, and all the additional apps anyone could want or need. 

This is why I chose to, on reinstall, to format / and swap but NOT to format /data

It seems to me that...   The idea of a separate partition for /home is bad for two reasons.   The remnants of the previous version of the OS remain in /home if it's not formatted.  And, some software seems to have issues when /home is NOT on the same partition as / ( as reported by a few users ).

---

### Post by mike555 on 2010-04-25
your ideas are good , just be sure to backup users data ...I use a auto backup program to backup my /home (on the / partition) to my /Data partition each day ....

---

### Post by k3lt01 on 2010-04-25
> **brucewagner said:**
> 
50GB for /       ( where the /home is in this partition too )
10GB for swap
All Remaining Space for /data

On a re-install, the / is formatted (including the /home) , but the /data is not touched. 
The only thing you are not considering here is user settings are contained in /home. If you do a clean install and reformat /home you will lose your user settings.

My advice would be that you modify your plan ever so slightly to give /home a separate partition. That way you don't lose user settings but you can still keep /data separate.

---

### Post by brucewagner on 2010-04-25
> **mike555 said:**
> your ideas are good , just be sure to backup users data ...I use a auto backup program to backup my /home (on the / partition) to my /Data partition each day ....

Oh.... That's a very good idea too.  Then users don't necessarily need to be trained to save everything to /data

What backup program do you configure to do this backup of /home to /data daily...?

Another Note:  I require all users to use a DropBox folder (within their /data folder) for ALL "irreplaceable data" (user created data like documents, personal photos, etc.).  This way, all critical data is also backed up to "the cloud" and the user's other computers, if any.

---

### Post by k3lt01 on 2010-04-25
> **brucewagner said:**
> Did you read my comments on the negative effects of "remnants" left behind in the /home directory, on a reinstall...?These are very easily dealt with if you create a new user profile (e.g. testuser) and copy the relevant parts over to the normal users /home/[normaluser]/ (over-writing what is already there) that way you still keep user settings but don't have unwanted remnant material from previous installs.

---

### Post by brucewagner on 2010-04-25
> **k3lt01 said:**
> The only thing you are not considering here is user settings are contained in /home. If you do a clean install and reformat /home you will lose your user settings.

My advice would be that you modify your plan ever so slightly to give /home a separate partition. That way you don't lose user settings but you can still keep /data separate.

The thing is....   I think I want to lose those settings.  I think it's better to start out with a fresh clean install... when installing a new version of Ubuntu.  No?

What specific settings are you referring to?

Why would you want to keep them?

Isn't it better to start with a clean install -- to avoid any possible conflicts....?

---

### Post by k3lt01 on 2010-04-25
> **brucewagner said:**
> The thing is....   I think I want to lose those settings.  I think it's better to start out with a fresh clean install... when installing a new version of Ubuntu.  No? um no with regards to settings. As for / itself then yes. but I keep /home separate for that reason.

> **brucewagner said:**
> What specific settings are you referring to?Firefox, about 500 or so bookmarks and associated things like passwords etc.

> **brucewagner said:**
> Why would you want to keep them?Cause I don't want to have to type everything back in. It will take more time to put all my user settings back manually than it would by keeping a small /home and having it all there. 

> **brucewagner said:**
> Isn't it better to start with a clean install -- to avoid any possible conflicts....?Read my last post about how to handle possible conflicts. Time is money, I wouldn't dare charge a customer or waste a friends time if I knew I could take less time and still come out on top.

---

### Post by brucewagner on 2010-04-25
> **k3lt01 said:**
> Firefox, about 500 or so bookmarks and associated things like passwords etc.

For that, I think the superior method is to simply use [http://xmarks.com](http://xmarks.com) 

It backs up all of those things automatically, and even synchs with all my computers, if I want it to.

---

### Post by k3lt01 on 2010-04-25
> **brucewagner said:**
> For that, I think the superior method is to simply use [http://xmarks.com](http://xmarks.com) 

It backs up all of those things automatically, and even synchs with all my computers, if I want it to.
Does it also do Pidgin (.purple)?
How about .skype?
.songbird?
.moovida?
.gtkpod?
.gpsdrive?
.gconf?
.dosbox?
.dosemu?
.evolution?
.bibledit?
.adobe?

How about Fieldworks? Does it back that up and transfer it across to?
And Adapt It?

Firefox was 1 example, there are many more, the above is just a selection of what I use. Others will use more, or less, should we all just reformat our / (containing /home) and lose that info and then put it back manually? [I don't think so Tim]("http://en.wikipedia.org/wiki/Home_Improvement_%28TV_series%29")!

Btw not everyone trusts clouds to keep their info on. I certainly don't think it is a more viable alternative especially when you can keep it all on a ext hdd using zsync or something to keep everything safe.

---

### Post by QIII on 2010-04-25
I've been using Linux since shortly after Linus introduced it to the  world.  I used Unix extensively before that.  I still use OpenSolaris.  I've been doing this computer gig since the 70's, so you may take my advice for what you will.  But my advice is what it is.  I didn't compel you to consider it.

> **brucewagner said:**
> Thanks but did you guys read my post?
Did you read my comments on the negative effects of "remnants" left behind in the /home directory, on a reinstall...?

Yes.  I read it.  Consider what "remnants" are left there.  Some of those "remnants", like user preferences, are relatively important.  What other remnants, specifically, are problematic?  The OS itself is installed in /, not /home.

> And the occasional problems that can occur when an app expects the /home to be on the / partition...?When does this occur?  What specific applications should I add to my list of things to be careful about?  I have used a separate /home partition for years and have never encountered that.  If you use apt to install, virtually everything will be installed in /.  If you install something manually, you can exercise some control over where things are installed.

> Also, the part about:  If you want a machine to be able to Hibernate, the swap partition needs to be LARGER than the amount of RAM you have...?In reality, the RAM state is no larger than the RAM it is contained in.  Theoretically, then, you need only the exact amount of swap as you have RAM.  However, the physical characteristics of disk technology make that virtually impossible to accomplish.  So you go a little larger.  Is not 1.25 x RAM larger than RAM?  You will often hear 2x.  That is likely a waste.  An exact match could be a close shave.  1.25x should give you what you need.

> And the part about allowing lots of extra space in / to allow for the installation of virtual machines,  lots of temporary download space, and all the additional apps anyone could want or need.Most vm software, by default, creates the virtual disks in /home.  You can choose to do it elsewhere, of course, but I would suggest some other location than /.  Perhaps yet another partition like /vms.  You probably do not want / to house temporary files.  / is generally where your system files live.  Temporary files and user-specific data is what your /home or /data or other partitions should be used for.  My opinion is that it is unwise to use / for temporary files.  It would be much like using the system directory in Windows.  And I did say 10 - 30, but 30 is probably a bit to big.  (But I must correct my units.  That should be GB.)

> This is why I chose to, on reinstall, to format / and swap but NOT to format /dataYou can do precisely that for /home.  If you want a /data partition (which I did not rule out, if you will reread my response) you can also do that.

> It seems to me that...   The idea of a separate partition for /home is bad for two reasons.   The remnants of the previous version of the OS remain in /home if it's not formatted.  And, some software seems to have issues when /home is NOT on the same partition as / ( as reported by a few users ).Again, what "remnants"?  Some "remnants" you may want to keep are user preferences, Email profiles and Firefox profiles.  And again, which applications?  Which few users?  Again, the OS lives in /, not /home.  The use of a separate /home partition is highly recommended virtually universally across the Linux community.

Not trying to be smart.   And I did say you could use a /data partition if you chose to do so.  But I am saying I have been doing this for more than 35 years.  Take that for what it is worth.

---

