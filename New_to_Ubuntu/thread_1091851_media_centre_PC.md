---
title: "media centre PC"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-03-09
I am currently dual-booting Windows XP and Ubuntu 8.10. Both take a while to start up, and often all I want to do is play my music. Is there any way to add another partition and boot into an OS that just plays music, and that's it.

I'm assuming that this is what a "Media Centre PC" does. The only one I know of is Windows Media Centre, but I don't have it, and I don't want to spend money on it. Also knowing windows I'd imagine it would be bloated and slow!!

Any thoughts?

---

### Post by borneux on 2009-03-09
you could try mythbuntu

---

### Post by cmay on 2009-03-09
i have a pc i only use for "media-center"
i have installed crunch-bang linux on a pc with a tv card isntalled. the tvtuner card with remote i have not configured right yet as i am currently just using acidrip to rip all my 300 dvd and it takes time.

i use xine for movies and rythmbox for music. then i also use elisa that is a really good media center and before i made this setup i had configured the remote to work and had made elisa start up by it self and i also made the pc autologin. i removed all other programs than these programs that i used but i resintalled ubuntu for some reason ( i was bored i guess) and now i gone back to using crunch bang. 

you can very easy use elisa as a media center on your ordinary pc as long as the restricted drivers are enabled. 

my personal opnion on this is that it does not need to be so complicated and fancy as such. if i want a remote control and want a pc  to be a media center that only does this then it is  just to buy a good tuner card wiht remote and do a custom ubuntu install maybe using the netbook launher as gui and then use elisa as the only program the user can see. or as i ended up wiht using crunch-bang and a simple openbox meny with 3 menu items. xine rytmbox and elisa. 
then for admin jobs i use a sudo enabled account that can use all program on the system. 
i have been very happy wiht using crunc bang linux this way and i could have done it just as easy with ubuntu if i wanted to.

---

### Post by Afkpuz on 2009-03-09
Ubuntu+mythtv makes for a nice media center.  You can even set it to start on log in, so it feels like a real media center.  Also, check out elisa media center and linuxMCE.

---

### Post by dfreer on 2009-03-09
> **abhiroopb said:**
> I am currently dual-booting Windows XP and Ubuntu 8.10. Both take a while to start up, and often all I want to do is play my music. Is there any way to add another partition and boot into an OS that just plays music, and that's it.

I'm assuming that this is what a "Media Centre PC" does. The only one I know of is Windows Media Centre, but I don't have it, and I don't want to spend money on it. Also knowing windows I'd imagine it would be bloated and slow!!

Any thoughts?

The difference between a Windows Media Center and what you are describing, is that you have to boot the normal windows OS (XP or Vista), and then launch Media Center. So you aren't really gaining any sort of speed increase, boot the OS and then launch VLC/iTunes/Amarok whatever would probably be just as quick.

A Media Center PC is often the same thing, only it automatically launches Media Center after it loads the OS and you generally never fall back to the desktop.

However, on some laptops by major manufactures, they sometimes include a mini-os just for playing Music/DVDs/etc on a separate partition. HP's is called "Quickplay" and it's the one I'm most familiar with, it involves a slimmed down install of XP, that is hibernated every time it is shutoff, so that boot times are rather quick. It then loads it's Quickplay application which just lets you do the basics, you can't do anything else like surf the web/play games.

What you might want to look into is GeeXboX, used it several years ago as a replacement for HP's Quickplay and I remember it working pretty well (not quite as fast, but that might have changed since): 
[http://geexbox.org/en/index.html](http://geexbox.org/en/index.html)

EDIT: Most people seem to be recommending full blown media center applications, which is fine. I would recommend Elisa or MythTV myself if that was what you are looking for. However, by default those are the same as Windows Media Center in that they are applications that are loaded AFTER the OS has already booted, which won't give you that speed boost you are looking for.

---

### Post by chrisod on 2009-03-09
You could put Puppy Linux on a partition or even on a thunbdrive and use it as your music OS. It would be way speedier than booting a full operating system.

---

### Post by skroops on 2009-03-09
> **abhiroopb said:**
> 
I'm assuming that this is what a "Media Centre PC" does. 

No that's not right, a Media Center PC is just a PC dedicated to showing DVDs, TV, Music etc.  It still has a full operating system.

What you want is something similar to Dell MediaDirect, and similar partititions that Laptop (and some desktop) manufacturers put on their PCs to enable quick booting for DVD watching and music listening.  Those partitions do infact run lightweight Linux OSes.  Unfortunately those are normally installed by the manufacturer and you will have to look for a similar free option.

I can't help you with that but you may want to consider restating your question without the above assumption as it seems to be getting you confused answers.

---

### Post by cmay on 2009-03-09
i got this linux media center package and i installed them all just to see what i liked best.
://www.linuxpusher.com/index.php?cPath=106_108&osCsid=b8dd79f673ef1d5d28ed7ca6ca1b4f35

i decided i wanted to use crunch bang with a minimal setup of programs instead. reason was that on crunch bang i could use openbox to configure a menu so i had only the music and video programs showing and it took very little time to set up. no SQLserves or anything. then also the crunch.bang just works the best on this pc with the hardware for some reason. so i ended up using that. i liked earOS very much until i started to configure it and intstalling and removing programs. i ended up tearing hair out of my head and i was kicking and screaming and yelling a lot. so i installed crunch bang and called it a day.

---

### Post by lovinglinux on 2009-03-09
I guess what you want is a lightweight OS with media capabilities. Anyways, you might want to try my media center extension for Firefox - [FoxMediaCenter]("http://fmc.isgreat.org/").

It is primarily developed for TV and video, but can also be used to play and manage music lists. I also have plans to port it to Songbird in the near future.

I wrote this extension because I wanted a simple TV recorder and programming guide. MythTV is great, but it has too many features for me.

Download, screen shots, user guide and support at [http://fmc.isgreat.org](http://fmc.isgreat.org)

Please read the "Important Notes" and "Requirements" sections of the web site before installing it.

---

### Post by abhiroopb on 2009-03-10
Thanks everyone for the advice.

Yes I think what I am looking for is something lightweight that starts up quickly. I had the HP Quickplay (as my laptop is a HP) but since I changed the HD the quickplay has been deleted. Something liket that quickplay would be ideal I think. 

Puppy Linux seems to be a good alternative, however, is there anything (perhaps like Mythbuntu) that is known for this sort of thing?

GeeXBox looks like the closest to what I am looking for, any comments on this distro?

---

### Post by dfreer on 2009-03-10
BTW, if you still have an HP laptop and windows installed, you should be able to restore your original QuickPlay partition. Takes a bit of setup but should work I've done it before.

---

### Post by cmay on 2009-03-10
the package i linked to i got has geexbox in it. i think its cool and when it works its great. but its still too unstable. i would not invite people over for watching a movie to impress them with the stability of linux to put it this way. it has crashed on me more than once when in the middle of a good movie.

 but its amazing that you can just pop in a cd and boot into a live media center and when done eject the cd and your pc is back to normal. 
if it becomes a bit more stable i am sure lots of people want to have this in their pocket for lunch breaks at the office :)

---

### Post by abhiroopb on 2009-03-10
That is exactly what I was thinking about....but if I can get quickplay to work...that may be quite useful as well!!

---

### Post by LowSky on 2009-03-10
instant on Linux... like the HP thing

[http://www.prestomypc.com/](http://www.prestomypc.com/)

unfortunatley the beta wont be availible until 3/16/09

---

### Post by abhiroopb on 2009-03-11
Presto seems a bit scammy to me, may be worth it though.

Tried GeeXboX and to be honest it doesn't work for me right now, I need something a little more "user-friendly", and geeXboX is too much of a headache.

I guess I'll just have to settle for booting up Ubuntu :(

---

### Post by dfreer on 2009-03-13
Getting the HP Quickplay back on your PC involves resizing the partitions (may not be needed) so there is a blank (no partition) approx. 1 GB chunk at the end of your hard drive. Some online have said it only needs ~250 MB's, but I seem to remember 1 GB myself.

Then, you download the Quickplay Installer from HP's site, I think this is the installer I used: [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-46803-1&lc=en&dlc=en&cc=us&os=228&product=1842155](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-46803-1&lc=en&dlc=en&cc=us&os=228&product=1842155). I would check to see if there is a newer one/one specific for your PC (should be found in the Driver's for your model).

If all goes well it should install. As for booting to it... it may wipe out your MBR, which means you would be unable to boot Ubuntu but Windows/Quickplay should boot just fine. **IF** it doesn't wipe your MBR, than you will likely not be able to boot to it unless you modify your GRUB to boot it. 

I know that when I Triple booted Windows/Quickplay/Ubuntu, I installed windows first, created the partitions for Linux but didn't install it, installed quickplay, then installed Ubuntu. And the Ubuntu GRUB installer was able to pick up on all 3 and I could boot to whichever one I wanted. Good luck!

---

### Post by abhiroopb on 2009-03-15
A couple of questions:
1. How does quicplay browse your music? Mine is saved in my ext3 linux partition.
2. The link you gave me seems to be an "installer", its only 300kb, it doesn't seem like it is the actual program...any thoughts on that?

Thanks a lot, we seem to be getting there :)

---

### Post by abhiroopb on 2009-03-15
A slightly different take on this idea:

would it be possible to take a distro like gentoo or arch, and JUST install a media player (e.g. rhythmbox) and the requisite sound drivers, and leave it at that? That way it wouldn't waste time loading unneccesary componenets.

---

### Post by dfreer on 2009-03-15
> **abhiroopb said:**
> A couple of questions:
1. How does quicplay browse your music? Mine is saved in my ext3 linux partition.
2. The link you gave me seems to be an "installer", its only 300kb, it doesn't seem like it is the actual program...any thoughts on that?

Thanks a lot, we seem to be getting there :)

Quickplay *I think* can access the windows Hard drive for music. Most certainly it can't access an ext3 partition.

As for using a linux distro with just a media player, I think that would be a great solution. The idea behind QuickPlay is that it is a slimmed down Windows OS, that Hibernates everytime it shutsdown so that it boots back up quickly. 

If you were to try to do a linux version, I would install a Debian base system, install x + media player of your choice (Elisa Media Center perhaps?) + sound, then do the following:
(1). Enable Automatic Login
(2). Login script to startx and launch Elisa Media Center
(3). Mount Music/Video Folders so Elisa can Find them.
(4). When Elisa Media Center closes, hibernate the system.
(5). Modify GRUB so you can tri boot windows/Ubuntu/your slim debian.

Just some rough ideas. Further speed increases by recompiling the kernel but IDK.

---

### Post by abhiroopb on 2009-03-16
Then Quick Play would seem to be useless for my purposes (as all my music is in the ext3 partition).

Would Debian be the best choice? Wouldn't something lighter and more customisable like gentoo be more appropriate? Gentoo can be built from the ground up so could jst install the very BASIC programs/processes required. In addition I only need a musi player (e.g. Songbird), and not a full blown media centre.

Unfortunately I don't think I'm qualified to be doing this. Are there any guides available for this sort of thing?

---

### Post by abhiroopb on 2009-03-19
I recently saw this: [http://en.wikipedia.org/wiki/Splashtop](http://en.wikipedia.org/wiki/Splashtop), which apparently is installed on the motherboard of a PC and boots in under 5s, now obviously I can't achieve that with my current laptop, but is there something similar?

All I want is to be able to boot as QUICK as possible and play music.

---

### Post by abhiroopb on 2009-03-20
bump!

---

