---
title: "uninstal ubuntu"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by jimbo160 on 2010-01-02
I have a dual boot set up with windows xp, and ubuntu, and i want to uninstal ubuntu. can i simpley uninstal? I see other groups about changing things in mbr. is it possible to restore my windows to an earlier date. i could use instal disc, but there are 8 of them to reinstal my windows. i am just looking for a simple way to do this. can you make a suggestion?

---

### Post by jimbo160 on 2010-01-02
done some more reading, and am sorry for what seems to be a double post. just thought a simple restore would do the job. i feel i should have left well enough alone and not even bothered with ubuntu.

---

### Post by raymondh on 2010-01-02
No worries about the double post ... it happens.

Ok, 2 questions ...

1.  Your ubuntu install, is it in its' own partition or, did you install it thru wubi?
2.  Which version windows are you running?

If installed in its' own partition and you are using Vista, and you don't want to use those 'recovery disks' (8 of them, huh) ...

1.  [Download and burn this to a CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").  We need to fix the MBR first and get you booting into windows automatically upon start-up (which is what you want, right? ).  Here is the procedure.

> Boot into the CD I asked you to burn

When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the following (pressing ENTER after each command):


bootrec.exe /fixboot

bootrec.exe /fixmbr

Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

Now, re-boot your computer and in Vista, access the disk management utility.  From there, click to highlight the Ubuntu partitions and delete.  You may have the following (delete in order)

Root - which will be in ext format
SWAP
A EXTENDED partition that housed both root and SWAP.

Once clean of Ubuntu, go ahead and enlarge your Vista partition.  You might as well defrag.  When done, reboot and let windows run its' checkdsk function.

If you have a wubi install, you can remove ubuntu from the add/remove function of windows.  You will also have to edit the boot.ini file in windows.  Depending on your version of windows, 

[Here's the link]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")

If you have XP and Ubuntu is in it's own partition, we need a XP install disc.

Regards,

Raymond

---

### Post by jimbo160 on 2010-01-03
well, i am useing windows xp, on my computer. I did not use wubi. I downloaded ubuntu, iso burn to disc, when i was in windows i put my disc in, and followed the instructions. it was very simple, and best i can tell the program is in "c", in a folder of its on. there are 2 colders in "c", that are those that i am not able to open. they are those that when i click, it ask, "open with".  i am not very up on these computer things.

---

### Post by J V on 2010-01-03
Which tells us you probably *did* use wubi and you are in the absolute beginners forum for a good reason :)

What are these 2 folders called?

---

### Post by CharlesA on 2010-01-03
If you've got an XP disc handy, you can just boot into the recovery console and run the two commands above.

EDIT: Looks like you use Wubi.

---

### Post by dmaxel on 2010-01-03
If you say that Ubuntu is installed in your "C:" drive, then you have indeed installed Ubuntu using the Wubi installer. This makes uninstalling Ubuntu a bit easier. Just uninstall Ubuntu via Add/Remove Programs, and make necessary changes to boot.ini if they aren't automatically done for you (not 100% sure on that last one, best to double check).

EDIT: Got beat....twice! Hahaha

---

### Post by 3rdalbum on 2010-01-03
> **dmaxel said:**
> Just uninstall Ubuntu via Add/Remove Programs, and make necessary changes to boot.ini

The "changes to boot.ini" are not that important - they just stop the Ubuntu option from appearing at startup. Removing Ubuntu via Add/Remove Programs is what actually removes Ubuntu.

---

### Post by jimbo160 on 2010-01-03
ok, maybe i do have wubi, for on my C: drive, there are 2 of these folder that i cannot open. the folder description underneath the icon, "wubildr, file, 194KB. the other description, "wubildr, MBR file, 8KB. there is another folder that i can open, with description under icon, "ubuntu". withen that folder are 5 links, (folders), being, discs, install, winboot, ubuntu, and uninstal wubi. does this tell you anything toward me uninstalling ubuntu?

---

### Post by candtalan on 2010-01-03
> Just uninstall Ubuntu via Add/Remove Programs

This is the way to uninstall an ubuntu install when it has been installed within windows. You simply uninstall it like you would do for any Windows program, from Windows.

hth

---

### Post by jimbo160 on 2010-01-03
I shall try that, and hopefully it all works, for i want to use ubuntu on my other computer, and free this one up for my grandkids. thanks for the help,      Jimmy

---

### Post by candtalan on 2010-01-03
I find that Ubuntu is IDEAL for grandkids, mine was just over two years old when using it initially......

No viruses, very stable, free, runs well on old machines, lots and lots of games etc

---

### Post by jimbo160 on 2010-01-03
I see you like the ubuntu for the games. would you be able to tell me some of the games your grandkids play? I have a boy and girl, twins, that love to play with there pa paw's computer. they just turned 5. thanks ,    Jimmy

---

### Post by candtalan on 2010-01-03
Using Synaptic Package Manager:

gnome-games-data (for more than a dozen games as default install ubuntu I believe)

And in the repositories, including universe and multiverse:

gcompris
tuxmath
tuxtype
childsplay
circuslinux
PlanetPenguin Racer, or ppracer (for faster pc)
SuperTux (faster pc)
SuperTuxKart (faster pc)
TuxPuck

There are probably more, just examine the Games filters in Synaptic Package Manager

---

### Post by jimbo160 on 2010-01-04
thanks for the info. i may leave it there for a spell to see about the games. what version of ubuntu do you have? i have an upgrade disc, i got from ubuntu, that i planned on upgradeing to, but, i see so many negative comments about the upgrade, that i do not know yet. for instance, i see a lot about a lose of audio, and cannot reverse it. do you have any comments about this? i personaly find myself very dumb with useing ubuntu, as compared to windows. if you have any advice, or help you might share with me. thanks for your replies,           Jimmy

---

### Post by candtalan on 2010-01-04
My daily machine runs 8.04.3 and I also use this for some sound audio things. Occasionally the audio does not start properly, so on that occasion I just reboot, it usually starts ok, there are more elegant ways of dealing with that I believe. Sound in 8.04 can be a problem (pulseaudio). I also run 8.10 (sound is better), and 9.04 (sound ok) and also 9.10, a few people have had video probs in some machines with 9.10.

If you have something that works, with codecs etc then there is no reason to version upgrade if you are still getting security updates (18 months unless LTS, then 3 years)

If you are curious, then use an old or spare machine (enough RAM) for later version installs.

Good news is that Ubuntu is quick and easy to install - a clean install - anyway.

Version upgrades sometimes have problems although I keep my normal installations to basic things, so version upgrades are - so far - all good. I would always check out first though with a Live CD to check graphics and sound.

I recall that Windows took me a year or so to learn, and text books were useless, and stuff changed every version. 

Ubuntu - took a bit of time to unlearn the Windows things (!) but even ancient textbooks on Unix are still useful, and Ubuntu has no motivation to make life difficult every different version - unlike Windows which needs you to BUY a new version  - for their business model. Anyway the effort is well worth it, to get away from the secret Windows underlay which knows more about you than you do.

Enjoy!

---

### Post by jimbo160 on 2010-01-04
sounds good. I may continue to keep my computer as a dual boot with windows xp/ubuntu. I will give myself a little more time to learn about it. thanks.
       Another question i might share with you. I have a real old computer, that is running windows 98 se. The thing just does not function well for me, and i really don't want to junk it, nor spend any money on it. Can you tell me is there a way to instal ubuntu on that one, and it consume all the working drives, or update them to work in ubuntu? I am haveing problems with my modem not being recognised, getting on line, and updateing is not there. maybe if i do away with windows, and do a full install on that computer with ubuntu, the problems i have with windows would not be there. If there is anything you know about this, let me know.

---

### Post by candtalan on 2010-01-05
> **jimbo160 said:**
> I have a real old computer, that is running windows 98 se. The thing just does not function well for me, and i really don't want to junk it, nor spend any money on it. Can you tell me is there a way to instal ubuntu on that one, and it consume all the working drives, or update them to work in ubuntu?

RAM memory is far more important than CPU speed. One PC I got recently, originated with Windows 98 SE, it has a PIII 650MHz, 20GB HD but, importantly I filled it with RAM, it has 500MB RAM now, although when I literally rescued it from the journey to the scrap yard it only had 128MB. I installed Ubuntu 9.10, using the 9.10 Alternate CD, into 128MB ram and it was working but rather slow. With 500MB ram it is ok to use, I have been recording broadcast radio streams with it. It would run faster with xubuntu but I want ubuntu, and it is ok. Firefox takes 17 seconds to start up for the first time.

If I had not spent 10 uk pounds (15 US dollars?) to get the ram I would have used Puppy Linux, it would go like the wind in 128MB. But it is not like a standard mainstream GNU/Linux, like Ubuntu.

> 
 I am haveing problems with my modem not being recognised, getting on line, and updateing is not there. maybe if i do away with windows, and do a full install on that computer with ubuntu, the problems i have with windows would not be there. If there is anything you know about this, let me know.

If you are using a dial up modem then expect to need special actions. Linux will work with full modems, however unless your modem is a serial connected external modem you might find it will not be possible without a lot of work, or even impossible. In a similar situation a while ago I simply purchased an external serial connected modem. 

Perhaps you mean a dsl modem though? If so, then a network card is very low cost and ethernet from a router offers much better security than a modem by itself.

hth

---

### Post by Methuselah on 2010-01-05
Take a look at this too:
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by jimbo160 on 2010-01-05
Thanks for all the info.

---

