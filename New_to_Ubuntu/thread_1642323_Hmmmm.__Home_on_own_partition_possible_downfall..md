---
title: "Hmmmm.  Home on own partition possible downfall."
date: 2010-12-10
forum: New to Ubuntu
---

### Post by Kellemora on 2010-12-10
Hi Gang

All of my computers, except my main computer, were set-up out of the box, which places /home on the OS partition.  So, on a dual or triple boot computer, each OS has it's OWN /home within it's own partition.

When I set up this, my main computer, I made /home it's OWN partition, because it was highly recommended to do it this way, and of course I backup /home elsewhere on-site and also off-site.

This computer is Triple Boot and has had a few OS's installed on it.

Initially, I installed
Partition 1, /dev/sda1 ntfs Windows XP-Pro.
Partition 2. /dev/sda2 ext 3 / Ubuntu 8.04
Partition 3. /dev/sda3 ext 3 /home
Partition 4. /dev/sda4 Extended
     Partition 5. /dev/sda5 linux-swap
     Partition 6. /dev/sda6 ext 3  CentOS

Later Partition 6. Was Cleared, Reformatted and Debian 5 Installed.
Later Partition 6. Cleared again and an attempt at installing 10.04.
Later Partition 6. Cleared again and 10.04.1 installed, failed.

These installed OS's did NOT install a /home directory, probably because of the fact I had /home as it's own partition.

What kind of barrel of WORMS have I created?

AND Should I go back to keeping /home within the OS's own partition?

I have not had any problems, but I'm afraid moving /home from a 64 bit 8.04 over to a 32 bit 10.04.1 might cause problems.

FWIW:  I have NO personal datafiles in /home, other than browser bookmarks that I can't seem to find.  I keep ALL personal datafiles on an external hard drive, connected to yet another computer, that I jokingly call my file server and that drive is backed up both on-site and off-site.
Someday I might learn how to set up a real file server.
But right now I just want to get my new computer set up with the following.
P1 Windows XP-Pro (just in case, I rarely use the doze at all anymore)
P2 Ubuntu 10.04.1
P5 Ubuntu's latest releases.

So, my closing question would be.  Should /home be it's own partition or should I let /home install in the partition it's related OS resides in?

Just thought of one more question.  Should Windows be stuck in a VirtualBox instead of requiring a boot-up to get to it?  Or am I better off, since I use it so rarely now, keep it on it's own partition?

Thanks Guys n Dolls

TTUL
Gary

---

### Post by amjjawad on 2010-12-10
> **Kellemora said:**
> So, my closing question would be.  Should /home be it's own partition or should I let /home install in the partition it's related OS resides in?

I have 9 Operating Systems installed on PC1 (I have two), 8 are Linux and the 9th is XP which is on another HDD.
Only one OS (Ubuntu 10.04) has /home while others don't have /home.
As you may know, it's recommended to have /home partition (a separate partition) but if you're backing up your important data into an external HDD and you don't have problem to install instead of upgrading, then it's not necessary to have separate /home partition.

That's my humble opinion :)

---

### Post by oldfred on 2010-12-10
I agree with amjjawad.

Most of the time I recommend a separate /home as having separate /data partitions is more advanced. Separate /home becomes one step up from the default / & swap configuration and keeps system from data.

When I first upgraded to Karmic I followed my own advice and created a /home but immediately decided to convert to /data. Then I found /home was only 1GB and realized that is easy to backup and not much reason to have it separate. I now install the new version of Ubuntu into a new / and only copy over some settings from /home as I find I need/miss them.

If you are using firefox the bookmarks & other settings are in a hidden folder - ~/.mozilla/firefox. I actually only have profile.ini in that folder and have the profile itself in my shared NTFS partition from when I dual booted a lot. I now use XP only an hour or two a week. 

I have kept dual booting XP, just because I did not want to reinstall or totally reconfigure to work in VirtualBox as it is not worth the effort and I keep hoping I can totally convert to Ubuntu.

---

### Post by cariboo on 2010-12-10
There could be problems with sharing /home with different distos, as all the configuration files may not be in the same place.

I personally setup a separate /home partition for every distro installed. I do share 1 swap partition amongst  all the installed distros.

---

### Post by Verbeck on 2010-12-10
you could use different usernames or path to the user's home for each distro so the config files do not conflict

---

### Post by amjjawad on 2010-12-10
> **cariboo907 said:**
> There could be problems with sharing /home with different distos, as all the configuration files may not be in the same place.

I personally setup a separate /home partition for every distro installed. I do share 1 swap partition amongst  all the installed distros.

I share only **swap** and I don't need to create /home for other distributions as I don't use them much, I keep them for learning/experiment purposes.
Only my main OS (Ubuntu) has /home on its own partition.

Yes, sharing /home might cause problems.

---

### Post by Kellemora on 2010-12-10
Thanks all for your splendid responses and insight!

I had set aside like over 250 gigs for /home on it's own partition and I think the highest it's ever been was 7 gigs.

After a couple of installs, and usages of other distro's, my /home folder started growing again.

I prefer to load clean, avoids conflicts that way.

I've been manually keeping a second copy of my major bookmarks in both an .odt file and also as an .html file, since I bounce around to so many different computers during the day.

Even learned a few tricks in doing so that helps clean up bad links, and then finds duplicates if they exist.
Can also sort them by what purpose those links serve also much easier.

You know I've held off on installing 10.04.1 for a long time, because I could not get it to work on most of my older computers.  Finally got it up and running on one older one, but it required a lot of changes to files before it would quit crashing.  But now it has been humming along quite well.  

I still didn't want to trust putting it on my main computer, so I used the backup MoBo and CPU off the shelf and bought a new case for it.
That way I don't have to worry about messing anything up.
Besides, the way technology moves forward so fast.  The backup Mobo sitting on the shelf will be obsolete in another year anyhow.

Again, thanks for all your help guys.
Think I will just let /home reside WITH the OS instead of on a separate partition, since I keep all Data OUT of the computers themselves.

The one and only thing I seriously use Windows for is my Accounting program.  And occasionally, if I want to automate a game I'm playing.  There are tons of FREE programmable autoclickers for Windows, but nothing better than that lousy Kautoclick for Linux that I've found so far.  Although it does work slightly better on 10.04.1 than it does on 8.04 even though its the same program.  At least the keyboard alternates work on 10.04.1 as do a few other things on on-line games.

TTUL
Gary

---

