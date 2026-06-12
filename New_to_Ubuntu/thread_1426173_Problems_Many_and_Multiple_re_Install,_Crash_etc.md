---
title: "Problems Many and Multiple re: Install, Crash etc"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by NewBee2113 on 2010-03-09
I will try and be both brief and thorough.  I am a total Linux Newbie, and have only used Windows.  I have no programming or cmd type experience and have once or twice screwed up System 32 files.

I switched to Linux as I had a laptop with Vista that was just incredibly slow.  Thought Linux would help and also want to learn about it for many reasons (including hating Windows monopoly and viruses.)

Here are my computers specs as best I can ascertain:  
-I have a Gateway W340 laptop
-Intel Celeron 512 RAM
-60 GB hard drive
-ATI Radeon Graphics card


I tried installing: Ubuntu 9.10 from image files "burned" to disc
I think it is kernel: 2.6.31.14 generic
GNU Grub 1.97 ~beta 4

I completely removed Vista on install.  Initial problem on install was mouse did not work but figured out the apic=off under the F6 options.

Once I did this I managed to install and seemed to work.  However, system froze several times and I had to "power off" and restart.  

*First Question:  is there a way to restart besides power button?

Then on restarts various different things:  either I would just get blank screen with blinking underscore in upper left corner. (power off).  I would get the Ubuntu log and nothing else (power off),  Then sometimes on 3rd or 4th try it would work.

* 2nd question  at blinking underscore is there anything i should do?

Work for a bit then 2 more problems:  mouse would stop working after about anywhere from 10 minutes to 60 minutes.  Touchpad and keyboard ok.  kept using and used Ubuntu to install updates it said i needed.  Then lost WiFi kept disconnecting even though modem right next to me.

Did a complete reinstall.  Same problems!  I want to get into Linux but this is making it hard to love.  Also the forum bug fixes and stuff are way above my "pay grade" computer literacy wise.

3rd Question:  Should I try to install an earlier version of UBuntu?

sorry this was not so brief, but I have spent the better part of 3 days trying to fix this

---

### Post by Temposs on 2010-03-10
1) When the system freezes, usually the only way to restart is with the power button.

2) The blinking underscore just means the system is waiting for something to happen. If your system has crashed, then maybe nothing will happen.

3) You can try an earlier version if you'd like. Sometimes it will make a difference. The currently supported versions are 8.04, 8.10, 9.04, and 9.10. You might want to try Ubuntu 9.04 if you want to try a different version. Also, keep in mind that Ubuntu 10.04 will be released at the end of April, which isn't too far away.

Ubuntu does its best to do well on every computer, but you have to keep in mind that your computer is designed for Windows, and this means that the Ubuntu folks cannot predict the weird combinations of parts in your machine all the time. (Note: my machine described in my signature is designed specifically for Ubuntu, and works perfectly)

---

### Post by NewBee2113 on 2010-03-10
Temposs:

Thanks for the support.  I am trying to be patient and figure this out.  This is sort of a play around computer just for my Linux experiment. (so far I have "blown up the lab", so to speak).

I have it working again, after multiple power button restarts ("hard starts" is that correct?)

Question #1:  How can I call up my systems specs? And put them in the signature like yours.  It may help me get specific help.

Also, the problem I have was mouse then keyboard keeps freezing.  I read somewhere that I had to alter my settings at install, (apic or aspic=off...in the F6 options).  I read i was told to make those changes permanent but not sure if that is correct and if so, how to do it.

Is it correct?  if so how?

Question 3:  Also, update manager says i have like 244 updates to update.  I tried once and had wireless problems so I did fresh install.  And have not updated, but having crashing and freezing and failure to launch issues described above.

Suggestion?  Update all, some, none?

thanks

---

### Post by Temposs on 2010-03-10
1) You can find some of your system specs at least if you go to System->Admin->System Monitor, and then click the System tab.

2) I'm not sure about this currently.

3) You should definitely run all of the updates! It might solve your problems if you're able to get them installed. Also it will make your system overall more stable. Are you able to plug-in an ethernet cable so you can have a wired internet connection, instead of using your wireless? At least until you're able to get your issues resolved, it might be a good idea to use your wired connection.

---

### Post by NewBee2113 on 2010-03-10
OK, thanks:

my system is a Gateway laptop
Memory: 432.8 MiB
Intel Celeron 520@1.60Ghz

available disk space:  66.1 GiB

Ubuntu 9.10 (karmic)
2.6.31-14
GNOME 2.28.1

I tried once in main screen doing a restart.  failed.  Hard start and it worked (no blank screen with cursor, no restart in safe mode..right to desktop).

Mouse did not freeze or keyboard yet.  Going to download 235 updates then restart and see how it goes.  (I have it directly connected not wireless)

Going to bed and will check on this tomorrow and update.  I really want Ubuntu to work.  The brief things I have seen I like a lot.

Thanks for your help and sorry I am so cluelessly newb!

---

### Post by Temposs on 2010-03-10
Let me know how it works out after installing the updates.

Also, what do you think about upgrading your RAM? It would give your system a nice speed boost.

---

### Post by NewBee2113 on 2010-03-10
So far its ok.  I tried massive downloads and it weirdly froze...whenever i moved mouse it started going again, so perhaps it was related to some screensaver/hibernate thing.  So I decided to download a few at a time (of all 244 updates).

It worked ok.  Periodically, I tried restarting and had mixed success.  Sometimes wouldget to main screen and freeze.  Sometimes the blank screen cursor, sometimes i would do the "safe mode" restart which never seems to finish.  Just seems  

It seems ok, but far from stable.  Going to keep trying rest of downloads.

Will update periodically.  

Did not consider upgrade as its a laptop (can you upgrade Ram on a laptop), and it is sort of my "play computer" just for my Linux experimenting.

---

### Post by Temposs on 2010-03-10
You can definitely upgrade RAM on a laptop. It's the best way to extend the performance lifetime of your laptop. You should definitely upgrade if you're able. According to what I've seen your laptop can hold up to 4gb of RAM.

---

### Post by Temposs on 2010-03-10
Oh, and also, did you enable any hardware drivers listed in System->Admin->Hardware Drivers? If there are any listed there, you might try enabling them. Or if they are enabled, then you might try disabling them. You definitely should not be getting this kind of freezing behavior.

---

### Post by NewBee2113 on 2010-03-10
No proprietary drivers show up in that driver list.  SO i guess that's good.  I have seen a bunch of things related to the ATI video cards...should i be looking at that.

I think I have ATI radeon only because a sticker on my laptop says ATI radeon.  Is there a way besides the one you showed me to get a full breakdown of all my computers components.  (how  windows you can go into control panel and see everything (modem etc..)

Computer seems to be ok right now.but it is not smooth.  Mouse/keyboard freezing randomly, sometimesater 2 minutes, sometimes as now works smoothly.  Although I still fear attempting to shut down and restart.

Gonna just keep using it a bit tonight and explore some more tomorrow.  

Thank you for your patience.  I really want to learn about Linux and command lines and all that stuff, but a lot of the advice on the board seems a bit advanced.

---

### Post by Temposs on 2010-03-10
So, there are some ways to find out more info about your system. The System->Admin->Disk Utility and System->Admin->Network Tools will tell lots of info about their respective topics. To get a complete list of hardware, there are two commands you can do in the terminal:

```
lspci
```

and

```
lsusb
```

The first shows stuff that's more or less connected directly on the motherboard. The second shows devices that are connected more or less by USB connection. You should be able to find what all or most of your hardware is by looking through these lists :-)

---

### Post by NewBee2113 on 2010-03-12
I will check those out, but things seem to have gone from bad to worse.  I cannot get ubuntu to load.  I get to various different points:  1. is I power off and then i get the blank screen with the "_" in the corner and cannot type or CTL +ALT or anything., 2. i get to the screen that asks for generic startup or recovery mode (2 versions  .20 and .14) + memory test.  I have been trying to get .20 (as this was the updates that I downloaded 2 days ago).

When I do recovery mode the stuff races by but then hangs on a line that says as follows:

[2.090869] [Firmware Bug]: ACPI: ACPI brightness control misses_BQC function.

I have seen this a few times although the 2.090869 is not always the number ..Sometimes in the 1.7 range or not...(i think this might be seconds?)

Hitting spacebar gets me some extra lines but then stays frozen at which point i have to power off.  I then try to go to generic mode start and sometimes it works.

Finally, as of late when i get to the start desktop page my mouse/keyboard have been frozen and system cannot even do CTL+ALT+DEL.

My thoughts are: reinstall, but i have done that twice.  or complete burn a new ISO image disk and reinstall.

If so, do you have a link to a stable ISO image that is up to date or most recent?

I am not worried as nothing is on the computer.  My office just got new computers so I am going to take an old desktop to play around with Linux too.  So I don't care, other than time, about the reinstall.

Also I reinstall should I partition?  I have been replacing with linux completely so I did not partition the drives.

---oh and sorry so wordy---just want to be thorough

---

### Post by NewBee2113 on 2010-03-12
Could I really be a complete nerd!!!?  and I mean that in the totally best way.  I think I have inadvertently stumbled upon a solution.

So I remembered reading in a forum:  I was having problems on install with my mouse and keyboard and read to try the install options (F6) one of which is acpi=off.  I did this and it worked so i could use my mouse/KeyBord.  But i also remembered reading that you had to make this a permanent change (not sure how)

So, next time after multiple hard (re)starts i decided why not hit 'c' for command.  I get some sort of GRUB code.  I see the line that says "quiet splash"  did some more online searching of message boards and GRUB stuff and decided to add at the end of the quiet splash  acpi=off.  Then I rebooted and here I am...it worked.

The tests will be if I can log off, restart computer etc.  I will keep you posted.

If not, is there a way to make the acpi=off change permanent (I just typed it in and rebooted)  did not hit save or enter or anything else.

Thanks.  I am so excited...but trying to stay calm..but I totally want to learn this stuff

---

### Post by albert s on 2010-03-12
I think it is somewhere in the BIOS

---

### Post by NewBee2113 on 2010-03-12
Spoke too soon.  Computer froze on the main screen.  Just did a hard reboot and got a screen i have never seen before:

the ubuntu logo came up (in white black background)

And then in very small fine print :

filesystem checks are in progress:
/(/dev/disk/by-uuid/1e774815-c708-4074-8ce0-cfc012c23b44)   4%
ESC to cancel checks

but then it froze here?  Gonna let it sit for a while then i guess hard reboot?

---

### Post by Temposs on 2010-03-12
I wonder if your hard disk is dying...that can cause the kind of random freezing you're describing. It seems like it's freezing all over the place, and not consistently with one kind of action, except maybe accessing stuff on the hard drive. I think if you load up a LiveCD(or USB) and then in the terminal type this command:

```
fdisk -l
```

That should list all your hard drives. Find the id for your main hard(the partition with the most space) drive and do this command:

```
fsck /dev/sda1
```

But sda1 could be replaced with the appropriate id that you identified with the fdisk command. If when you run fsck you find that there are errors found on your disk, then you know why there's a lot of freezing.

---

### Post by NewBee2113 on 2010-03-15
Sorry for the delay got tied up:

ok, so i tried running first command and got the following:
percival@percival-laptop:~$ fdisk -l
percival@percival-laptop:~$ fdisk -l

My computer is named "percival" when it first asked for a name and it is only partition.

So I then decided to do the fsck command for the following:

fsck percival@percival-laptop.  and got the following:

percival@percival-laptop:~$ fsck /dev/percival
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: No such file or directory while trying to open /dev/percival

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

percival@percival-laptop:~$ fdisk -l
percival@percival-laptop:~$ fsck percival@percival-laptop
fsck from util-linux-ng 2.16
Usage: fsck.ext4 [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
        [-I inode_buffer_blocks] [-P process_inode_size]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
percival@percival-laptop:~$ 

Not sure what this all means or if i even did the fsck correct.  please advise.  Thanks so much.

Also, after seemingly having major failures, i decided to go in when it ask for recovery mode or hit 'c' for command.  I hit the 'c' and took out the "quiet splash" and added acpi=off and it loaded up.  Previously when i tried loading in "recovery mode" the code seems to hang on the ACPI [firmware bug] i mentioned above.  just a note and not sure if this is all related.

As I have mentioned.  I have managed to get on this computer and have it work, but then mouse will freeze and keyboard and then getting it to work again is a chore and a half with no rhyme or reason.

---

### Post by NewBee2113 on 2010-03-15
OK, so my previous post was slightly incorrect.  As I mentioned, when I got to the GRUB screen that asks for regular mode or recovery mode or you can hit 'c' for command or 'e' for Edit.....I did 'e' and in the code that appears i took out the "quiet splash" and replaced with acpi=off.

Computer worked great for hours, and got to briefly tour Ununtu.  I decided to test it out with a restart.  Computer came back to the desktop (good), but froze soon after entering keyring (not good).  At hard restart i was at GRUB screen and did my trick again....and *BAM* it worked and I am online.  (Also in the restart i noticed the code at the very last line that said "fsck clear"  which is good.

So my question is:  how do I incorporate my change (Quiet splash removed and replaced with acpi=off)  as I think this might be what has been my dilemna.

(I am having other minor problems, but I will check forum or post again  (having a wireless connect issue, but I have seen this in the forum)(also need to figure out how to set up my online email with evolution)

Thanks for any help, I am excited.

---

