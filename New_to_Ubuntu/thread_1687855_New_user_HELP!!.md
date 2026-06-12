---
title: "New user HELP!!"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by steve Ambrose on 2011-02-14
Hi Everyone I am completely newbie and I have just installed version 10.10 I followed the prompts on the CD to install alongside windows (vista) . Ubuntu works fine and Im really impressed with the speed and looks.
However when I shutdown and reboot I cannot get back to windows I have pressed several F keys but the screen seems to lock and when I let go of the F key ubuntu boots. I am given no choice of OS.

Thanks Steve):P

---

### Post by Trooper_Max on 2011-02-14
Normally, you should not have to press any F keys while booting. Just wait and you should get a GRUB screen that displays your boot options from which you can use the arrow keys to select an option and enter to boot.

If for some reason you don't see what I'm talking about, go ahead and go into Ubuntu and open up a Terminal prompt from the application menu (think it's under accessories). Use the following command to update your grub menu:

**sudo update-grub**

This may take just a little while depending on your configuration, but as it is running, it should list the different operating systems it finds. Let us know what it lists.

~Troop

---

### Post by Iowan on 2011-02-14
There *should* be a moment when Grub displays options for loading. On my system, the arrow keys (DOWN in particular) lets me select a different boot option.

---

### Post by steve Ambrose on 2011-02-15
Hi Everyone I am completely newbie and I have just installed version  10.10 I followed the prompts on the CD to install alongside windows  (vista) . Ubuntu works fine and Im really impressed with the speed and  looks.
However when I shutdown and reboot I cannot get back to windows I have  pressed several F keys but the screen seems to lock and when I let go of  the F key ubuntu boots. I am given no choice of OS.

I have gone to the terminal and put sudo update-grub and this is what is listed. By the way I have a sony Vaio laptop

steve@steve-VGN-NS20J-S:~$ sudo update-grub
[sudo] password for steve: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
steve@steve-VGN-NS20J-S:~$ 


Thanks Steve):P

---

### Post by hansolo4949 on 2011-02-15
I'm sorry steve, but I think you're hosed. There is a glitch in the Ubuntu installation software that is very rare, but when it manifests itself, even if you choose to dual-boot, it will wipe out any other oses. Do you see any other hard drives when you go into the "places" menu? if you do, try and open the one that is not named file system (make sure you have no external drives attached for simplicity. If it opens, you can access the vista partition on your hdd, and get your info off of the drive, if you cannot open it, it will be a lot harder to recover your data, and if no others show up, vista is gone forever, and I hope you have a backup:(. Please tell us what happens, because we are all standing by waiting for people in distress to come calling;).

---

### Post by Guilden_NL on 2011-02-15
There are two possibilities, one good, one bad.

The bad one is that you somehow mistakenly partitioned your drive and formatted your entire drive, wiping out Windows.

More likely it is the good, I have had this happen twice with 10.10.  I had to correct the device mount for the Windows partition.

Rather than do it from memory and forget something, let me go find a post that has step by step instructions and post it back here.

In the meantime, go to System/Administration/Disk Utility then click on your drive, do you have a NTFS or FAT partition?

Also, do this in anticipation of needing more info to help you:
Use a LiveCD to boot the computer, choosing the option to try without any changes.

1. Download the boot info script from here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
2. Move the boot info script to the desktop.
3. Open a terminal and run the 
Code:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

Then post here, using the code command in the Advanced editor (hash or pound # button) or typing [CODE*] before the text and [/CODE*] after the text, leaving the asterisk out.

---

### Post by hansolo4949 on 2011-02-15
Thank you, Guilden_nl for giving out that info. I hate sounding all gloom and doom, but from experience on these forums, if you cannot fix the problem soon, and start mucking around with 500 different possible "fixes" the person normally ends up hosing their data or gets frustrated and reinstalls everything, so thank you for chiming in :)

---

### Post by steve Ambrose on 2011-02-15
Thanks Guys, there is no other drives in the places menu only filesystem in the my computer screen. I did a full windows backup on an external harddrive before I started. I did follow the install correctly , I wish now I partitioned manually but thought as a newbie it would be better for the install to do it for me.

I await your further instructions.
Steve

---

### Post by Guilden_NL on 2011-02-15
> **hansolo4949 said:**
> Thank you, Guilden_nl for giving out that info. I hate sounding all gloom and doom, but from experience on these forums, if you cannot fix the problem soon, and start mucking around with 500 different possible "fixes" the person normally ends up hosing their data or gets frustrated and reinstalls everything, so thank you for chiming in :)

Ain't that the truth!!!  I have a feeling it got the Windows partition wrong.  I've never had the problem before but on two, no three now that I think of it, 10.10 blew it.  It's a GRUB2 bug and I've reported it along with many others.  

I'd like a prompt that asks "If you know what you're doing, here's what I plan to write, if it is wrong, update it here before pressing "Commit": [COLOR="MediumTurquoise"]insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa
linux /boot/vmlinuz-2.6.35-25-generic root=UUID=1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa ro quiet splash
initrd /boot/initrd.img-2.6.35-25-generic[/COLOR]

---

### Post by Guilden_NL on 2011-02-15
> **steve Ambrose said:**
> Thanks Guys, there is no other drives in the places menu only filesystem in the my computer screen. I did a full windows backup on an external harddrive before I started. I did follow the install correctly , I wish now I partitioned manually but thought as a newbie it would be better for the install to do it for me.

I await your further instructions.
Steve

Steve, it won't see your Windows drive under Places because it is not properly mounted as a device.

Go to System/Administration/Disk Utility and tell us what that shows for Volumes.

---

### Post by robro on 2011-02-15
> **steve Ambrose said:**
> Thanks Guys, there is no other drives in the places menu only filesystem in the my computer screen. I did a full windows backup on an external harddrive before I started. I did follow the install correctly , I wish now I partitioned manually but thought as a newbie it would be better for the install to do it for me.

I await your further instructions.
Steve

I might could help,
if you did a full backup than you should be able to restore windows.
I havent been through this before but if you have a windows installer cd around you should be able to install it back and restore the backup from there although like i said i have never been thru this before but i have heard that thats on way to do it.

---

### Post by hansolo4949 on 2011-02-15
> **Guilden_NL said:**
> Ain't that the truth!!!  I have a feeling it got the Windows partition wrong.  I've never had the problem before but on two, no three now that I think of it, 10.10 blew it.  It's a GRUB2 bug and I've reported it along with many others.  

I'd like a prompt that asks "If you know what you're doing, here's what I plan to write, if it is wrong, update it here before pressing "Commit": [COLOR=MediumTurquoise]insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa
linux /boot/vmlinuz-2.6.35-25-generic root=UUID=1ed7dfa6-12cf-4d01-bc43-4961c3abf5fa ro quiet splash
initrd /boot/initrd.img-2.6.35-25-generic[/COLOR]


Yes, I completely agree. Or perhaps there should be a "beginners Ubuntu" that takes all the "tech" out of it, sort of like OS-X. It could be a simple, extensively debugged (probably older) version of Ubuntu, that has a minimal chance of mucking up. That way, both parts of the community is satisfied! Maybe I (or someone) should send a message to the ubuntu team about that.....

---

### Post by hansolo4949 on 2011-02-15
Sorry Steve, but Vista is hosed, and you seem to be the unfortunate victim of the installer bug. Now, if there was something you are desperate to get back, that you did not back up, there ARE free file-recovery programs out there....


Update: sorry, I didn't see your post, Guilden. Yes, you should go there and tell us if there are any NTFS or FAT partitions.

---

### Post by steve Ambrose on 2011-02-15
In disk utility it shows my hard druve make and my cddrive. the hard drive shows a total of 250gb with 9.4gb extended and 9.4gb swap there is an option to edit partion. it also shows linux ox83 device /dev/sda1

hope that helps ,

---

### Post by hansolo4949 on 2011-02-15
Looks like Vista is NOT there, unless the Vista partition is named very strangely. Back when you were able to use vista, do you remember what your "hard drive" in my computer said it was called? If you can remember, and it does not match any of the names you saw in the volume, then it's time to whip out the ol' vista install cd and backup.

---

### Post by steve Ambrose on 2011-02-15
will this boot scipt download work?
please let me know before I waste more time....maybe this will encourage me to push on and set up ubuntu to the full

---

### Post by hansolo4949 on 2011-02-15
Boot script download? I think I know what you are talking about but, but Vista is gone, there is almost no chance of getting it back:(. On another note, unless you have some windows programs you need to desperately use, then Ubuntu is a great alternative to Windows.

---

### Post by steve Ambrose on 2011-02-15
Ok guys vista is gone long live ubuntu!! The only real program is I have a sony ebook reader can i use this with ubuntu and if so what do I need to download and install the ebooks. Also I have a sony walkman will this be recognised by ubuntu

thanks steve

---

### Post by hansolo4949 on 2011-02-15
I do not know about either of those working, although they probably will. For the program, just install the default ebook program under a windows emulation program called Wine.

Edit: I found this thread that may be useful to you:[http://ubuntuforums.org/showthread.php?t=181263](http://ubuntuforums.org/showthread.php?t=181263)

---

### Post by Guilden_NL on 2011-02-15
Yes the bootloader script will tell me what your GRUB2 is trying to load for Windows (if anything).

I am booting up a dual boot system to capture a screen print or two for you.

What is the total size of your HD? 250Gb?

Looks like Vista is still on there.

Give me a few to get over to that system.  I currently am replying on my personal laptop which only has Ubuntu on it.  I have one system with Windows on it just for these reasons.

And yes, you can use your Sony reader with Ubuntu, no restrictions at all.

---

### Post by steve Ambrose on 2011-02-15
thanks mate do you have a link from where I can download wine, will that play windows games as well. I love my football manager

---

### Post by hansolo4949 on 2011-02-15
? okay, now i'm confused. The volume manager is not even seeing the vista partition, which means there is a 99% chance Vista is nuked. Did I miss something? I think I missed a couple of your posts, so I will go back and look.....

---

### Post by steve Ambrose on 2011-02-15
thank you so much, my total drive space shows 250gb , 9.4gb swap and 9.4gb ext what ever that means?

---

### Post by hansolo4949 on 2011-02-15
> **steve Ambrose said:**
> thank you so much, my total drive space shows 250gb , 9.4gb swap and 9.4gb ext what ever that means?


I believe that Ext means it is an extended partition. Okay, is there several partitions under the extended partition? there should be one that says extended partition. To the left/right of that one, is there another, indipendent partition?

---

### Post by steve Ambrose on 2011-02-15
it just says 241gb ext4 and then to the left it says 9.4gb swap and 9.4gb ext
there only seems to be this one

---

### Post by hansolo4949 on 2011-02-15
Then, Vista truly IS gone. Sorry for all the confusion. Guilden, he will not be able to find anything in the boot script, since Vista is completely gone. Anyway, you should be good to go, and good luc with Ubuntu! If you consider this thread "solved" please mark the prefix as so. Thank you :)

---

### Post by steve Ambrose on 2011-02-15
Thanks at least now I can stop trying.

---

### Post by hansolo4949 on 2011-02-15
yes, finally:D Have fun!

---

### Post by Guilden_NL on 2011-02-15
Here are two shots of the drives on my dual boot system.
The shot of Ubuntu only is a single drive with the Ubuntu system and apps on it.

The shot of Dual Drive has all of my Data on it as an NTFS partition and then you can see the XP system portion in the extended partition.

If you have one drive, your Ubuntu will be where my Data is as EXT3 or EXT4 (you noted which earlier, I forget), and Vista could be under one of the extensions, but it would have to say NTFS.

Looks like you may have partitioned over the Vista, but really can't say without knowing if you only have one physical hard drive and without the boot script.

---

### Post by Guilden_NL on 2011-02-15
> **steve Ambrose said:**
> it just says 241gb ext4 and then to the left it says 9.4gb swap and 9.4gb ext
there only seems to be this one

To confirm, you do not have a second hard drive?

If so, then Vista has been overwritten. If you have a second hard drive, then the bootloader script posted here is the answer to fixing the device identification issue with GRUB2.

If it has been overwritten and you still want to do a dual boot, you can reload Vista and still have Ubuntu.  You mentioned games; as much as I love Linux, Wine sucks for Windows based games.

BCD is a straightforward tool to accomplish this.  Here's a quick read of how to add Vista after Ubuntu, or reload Vista then add Ubuntu afterward.
[http://neosmart.net/wiki/display/EBCD/Linux]("http://neosmart.net/wiki/display/EBCD/Linux")

Here is where you download BCD: [http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

Good luck!

---

### Post by lisati on 2011-02-19
Threads merged.

Please do not start multiple threads for the same question.

---

### Post by yeats on 2011-02-19
> **hansolo4949 said:**
> I'm sorry steve, but I think you're hosed. There is a glitch in the Ubuntu installation software that is very rare, but when it manifests itself, even if you choose to dual-boot, it will wipe out any other oses.

I'm not sure we have enough information to say that steve Ambrose's Vista installation was wiped out by "a glitch in the Ubuntu installation software"...  He's clearly new to Linux/Ubuntu and it's just as (if not more) likely that he misunderstood what was happening in the partitioning setup of the installer.

I'm only pointing this out because the OP posted another thread saying that "install bug wiped out my vista", which may not be the case.

---

### Post by asmoore82 on 2011-02-19
> **steve Ambrose said:**
> Well I give up with this distro.. 
Some people come in with bizarre preconceived notions and hence bizarre expectations.
> **steve Ambrose said:**
> nothing works ,
I have quite a bit of evidence to the contrary
> **steve Ambrose said:**
> calibre wont install properly,
```
sudo apt-get install calibre
```
> **steve Ambrose said:**
> no help to load drivers for FTDSi , cant find my com ports , games wont find my drive under wine,
Linux &#8800; Windows : [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
> **steve Ambrose said:**
> Its faster than windows but &#8230;
Indeed. Faster, Freer, Stronger.
Perhaps you are too impatient, or perhaps
you are too *locked-in* at this time.

---

### Post by RedRat on 2011-02-19
I would like to suggest to all Newbies to try and download the LTS versions of Ubuntu as a starting point. Sometimes the intermediate releases are really beta issues of Ubuntu and may have problems that long standing users here find trivial to solve, but to a Newbie may be shocking and cause consternation. As you can see from this thread of some 4 pages, there is plenty of help but for a true newbie, it may well be disconcerting, 

I remember when I first started out with Linux and later with Ubuntu this forum was pretty thin. The various stable long term releases of Ubuntu, the LTS identifier, should be your starting point and then as you learn more about the system, try the upgrades. Just a suggestion from a onetime newbie.

---

### Post by steve Ambrose on 2011-02-19
Hi I just tried the sudo install command for callibre and got this failed message

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python-django/python-django_1.2.3-1ubuntu0.2.10.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python-django/python-django_1.2.3-1ubuntu0.2.10.10.1_all.deb)  404  Not Found [IP: 91.189.92.167 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
steve@steve-VGN-NS20J-S:~$ 

What should I do now, sorry for being a pain , I am over my tantrum now , im am just sooo tired
steve

---

### Post by steve Ambrose on 2011-02-19
Linux is not windows link, that was a great article and has made things clear to me. I will learn how to drive this thing...LOL

---

### Post by yeats on 2011-02-19
> **steve Ambrose said:**
> Hi I just tried the sudo install command for callibre and got this failed message

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python-django/python-django_1.2.3-1ubuntu0.2.10.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python-django/python-django_1.2.3-1ubuntu0.2.10.10.1_all.deb)  404  Not Found [IP: 91.189.92.167 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
steve@steve-VGN-NS20J-S:~$

try doing ```
sudo apt-get update
```
which will refresh your package lists, then do
```
sudo apt-get install calibre
```

> What should I do now, sorry for being a pain , I am over my tantrum now , im am just sooo tired
steve

It can be a big learning curve, but hang in there and ask for help where you need it!

---

### Post by Old_Grey_Wolf on 2011-02-19
> **steve Ambrose said:**
> Hi I just tried the sudo install command for callibre and got this failed message

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python-django/python-django_1.2.3-1ubuntu0.2.10.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python-django/python-django_1.2.3-1ubuntu0.2.10.10.1_all.deb)  404  Not Found [IP: 91.189.92.167 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
steve@steve-VGN-NS20J-S:~$ 

What should I do now, sorry for being a pain , I am over my tantrum now , im am just sooo tired
steve

It looks like the server you are using is not responding; therefore, the 404 error.

Get into Synaptic Package Manager and go to the menu "Settings > Repositories"; then, select "Other..." from the "Download from:" menu. Then click on the "Select Best Server" button. It will take some time for Synaptic to test the servers and give you a suggested server. When it does, click the "Choose Server button". Then follow the instructions to Reload.

Then try updating again.

Many times the problem will resolve itself after a few hours or days when the server has been updated or the network/server problem resolved.

---

### Post by steve Ambrose on 2011-02-19
> **yeats said:**
> try doing ```
sudo apt-get update
```which will refresh your package lists, then do
```
sudo apt-get install calibre
```

It can be a big learning curve, but hang in there and ask for help where you need it!


Thanks so much , it worked , dont know why but I will learn and find out. Tomorrow I shall buy a book about the command line. All I need to know now is how to install FTDSI drivers so I can run a serial to usb converter:D

---

### Post by Dutch70 on 2011-02-19
> **steve Ambrose said:**
> Thanks so much , it worked , dont know why but I will learn and find out. Tomorrow I shall buy a book about the command line. All I need to know now is how to install FTDSI drivers so I can run a serial to usb converter:D

Very helpful site with the command line...
[[COLOR="Red"]http://www.linuxcommand.org/index.php[/COLOR]]("http://www.linuxcommand.org/index.php") Also look under "tips, news & rants" (no pun intended steve) :D They have books & more helpful links.

Remember, you only have to do this once. After that...

you'll do it by choice. :popcorn:

---

### Post by hansolo4949 on 2011-02-20
> **yeats said:**
> I'm not sure we have enough information to say that steve Ambrose's Vista installation was wiped out by "a glitch in the Ubuntu installation software"...  He's clearly new to Linux/Ubuntu and it's just as (if not more) likely that he misunderstood what was happening in the partitioning setup of the installer.

I'm only pointing this out because the OP posted another thread saying that "install bug wiped out my vista", which may not be the case.



If that was the case, you would probably be right. But, we have had him look, and he even posted a screenshot of the partitions in his HDD, and there are No ntfs partitions, and none that even sound like they may have been from his previous system.

---

### Post by yeats on 2011-02-20
> **hansolo4949 said:**
> If that was the case, you would probably be right. But, we have had him look, and he even posted a screenshot of the partitions in his HDD, and there are No ntfs partitions, and none that even sound like they may have been from his previous system.

Correct - just as they would look if he had selected to install Ubuntu as the only OS.  My point is that I don't see any evidence in the thread that the absence of Vista was caused by a "glitch" in the installer.

With that, I'll leave it alone ;-).

---

### Post by hansolo4949 on 2011-02-21
> **yeats said:**
> Correct - just as they would look if he had selected to install Ubuntu as the only OS.  My point is that I don't see any evidence in the thread that the absence of Vista was caused by a "glitch" in the installer.

With that, I'll leave it alone ;-).



Okay, now I see what you mean. I thought you meant that the data was still on the HDD, sorry.  Best of luck with Ubuntu, Steve!

---

### Post by hansolo4949 on 2011-02-21
Double post, sorry.

---

