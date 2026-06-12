---
title: "back-up"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by amalnath on 2010-10-04
how to backup my system for future possible restorations??

---

### Post by SaintDanBert on 2010-10-04
Fetch **luckyBackup** from the repositories.  You can learn more about it at [ http://luckybackup.sourceforge.net/ ]( http://luckybackup.sourceforge.net/ ).

The workhorse at the guts is command-line **rsync**. LuckyBackup is a graphical front end -- a wrapper.  You dance with the GUI. It will make appropriate rsync commands as "jobs". You run the jobs to save or restore files.

LuckyBackup will place two entries into your Applications menu (Gnome). One entry is for your "root user" and the other entry is for
"plain users". I save my developer stuff as an end-user.  I use the "root user" for system-wide recovery work.

Rsync is able to take steps such that a tree of folders at one place on your workstation gets created as a duplicate in another place -- including over the network.  If you make changes at the sources, rsync will cause synchronization so that both the source and destination trees remain identical.

Given inexpensive external and network drives, I find the combination of luckyBackup and rsync quite effective and easy to use.

There are quite a few backup-recovery tools in the linux world. Each one tries to offer better features. Quite a few features involve the scheduler, manipulating the details of the backup and recovery jobs, and with finding files that you have saved in the past.

Bonne chance,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-10-04
I feel that I must say a few words about what we call "backup."
I prefer the term "failsafe copy". Its purpose is to protect data files from catastrophic deletion -- either because of hardware or software error or end-user error. You can go through the motions, but if you are not certain that you have copies that are readable, then you are wasting time.  This means that you must discover some process that works for you so that you make failsafe copies and then verify the copies are actually available.

Since you are trying to protect against catastrophe, it is not enough to have those copies stored in the same room with your computers. If you store them in the same building, you are a little better off. The preferred approach takes a copy to some other place. Consider taking one of your failsafe drives and store it in your space at work. Another option involves a friend -- you store his drive, he stores your drive.  If you make a full copy once each day, pick one day each week and move that copy to your alternate site. [highlight]Make a process that works for you.[/highlight] Otherwise, you will not use it reliably.

Bonne chance,
~~~ 0;-Dan

---

### Post by HermanAB on 2010-10-04
Howdy,

Just backup your data files.  There is not much point in backing up the whole system, since Ubuntu is very easy to install and one day when a disk drive fails, you would want the latest version of Ubuntu, not a five year old prehistoric version...

---

### Post by SaintDanBert on 2010-10-04
I agree with **HermanAB** about "backup your data files", but ...
I recently paid about $80 USD each for 500 Gbyte drives. With one in my laptop and one external, I can rsync a wholesale copy of the files with little trouble. Granted, that is exactly one copy not the two or three deep copies that many recommend. My time is worth something.

Let's think about what it means to "... backup your data files ..."
We know that everything in your $HOME folder ( [ /home/username ]( /home/username ) ) you want to keep. If you have files elsewhere on your disk, like [ /usr/local/* ]( /usr/local/* ) or similar, you want to keep those. You also want to keep everything in your system configuration [ /etc/* ]( /etc/* ). Everything thing else on your drive was put their by your distro installer or distro updates. Other things are they because you fetched and downloaded applications and utilities. 
[list]
[*]you can spin your distro media to get all of that back
[*]you can re-run updates to recover those
[*]you can re-fetch applications and utilities (grin) assuming that you remember what and where they came from
[/list]

If you omit the above frome your rsync copy, that same 500 Gbyte drive will hold multiple copies instead of just the one. (I might use three external drives. I write one on even dates and one on odd dates. If a drive fails, only one day's details are at risk. I'd use the 3rd drive for a wholesale copy in addition to the day's work copies.)

~~~ 0;-Dan

---

### Post by amalnath on 2010-10-05
thanks SaintDanBert and HermanAB for your valuable suggestions.. :smile::smile:

---

### Post by beta.tester on 2010-10-05
[B]Hi

I know this is marked as solved, but may I point you in the direction of the excellent backup tool in Linux mint? I use both distros and have found a way to get the tool working successfully in Ubuntu (Meerkat 64 bit flavour here at present and 32 bit not so long ago :)


I too use both Linux Mint Isadora (64 bit flavour) and Ubuntu (Meerkat RC at present again 64 bit flavour :) Mint I use on my laptop and Ubuntu on my other machine. As an ex systems engineer I am almost fanatical about backing up and the backup tool in Mint, for me, is the best I have seen. Yes there is a way to do this in Ubuntu I have found.

Go to the Repositories [http://packages.linuxmint.com/list.php?release=Isadora](http://packages.linuxmint.com/list.php?release=Isadora)

Download: mint-translations (2010.09.01 mint-common 1.0.5 mintbackup 2.0.6) When you have downloaded them install them in this order:

1) mint-translations
2) mint-common
3) mintbackup

You do this by highlighting the file and "use Ubuntu software centre" to install with.

When you have done this look in System => admin => and there is your backup tool :) for ease of use perhaps right click and add to launcher :)

Enjoy these great distros, I try to help with both flavours as and when I can.

I trust this helps you and kind regards


[/B]

---

### Post by amalnath on 2010-10-09
Hi,
 Kudos to you beta.tester, certainly your post helped me..
 Followed your post and got my backup tool..:lolflag:
 thanks a lot..

---

