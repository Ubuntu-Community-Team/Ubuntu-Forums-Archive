---
title: "Nervous with second thoughts... few questions"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Proto_Blaze on 2010-07-25
I am a windows 7 user. when i get my new rig built i was considering using ubuntu for the main, and windows as a secondary for gaming.

I have seen some comments on hardware issues (that cause overheating) like fans not working and stuff like that. i have mostly seen those about laptops running ubuntu though. does it plague laptops more than desktops? i dont want my new $1500 custom built to get fried.

Next, why do you use ubuntu? why do you prefer it over windows and possibly mac?

would i be screwed if i dont know any code and i install something?

what are a few things you can do in ubuntu that you cant do in windows? (besides customizing)

---

### Post by iponeverything on 2010-07-25
There is no rush to jump in and install. 

Get your new machine, run 10.04 from a usb drive for while - monitor temps check for general compatibility issues. Google around looking for issues with your hardware and Linux.. 

After you get enough information - make an informed choice.

---

### Post by lisati on 2010-07-25
> **Proto_Blaze said:**
> I am a windows 7 user. when i get my new rig built i was considering using ubuntu for the main, and windows as a secondary for gaming.

I have seen some comments on hardware issues (that cause overheating) like fans not working and stuff like that. i have mostly seen those about laptops running ubuntu though. does it plague laptops more than desktops? i dont want my new $1500 custom built to get fried.

Next, why do you use ubuntu? why do you prefer it over windows and possibly mac?

would i be screwed if i dont know any code and i install something?

what are a few things you can do in ubuntu that you cant do in windows? (besides customizing)
I can understand your apprehension. I was nervous and excited prior to installing Ubuntu for the first time.

It sounds like you want to use a [dual boot]("https://help.ubuntu.com/community/WindowsDualBoot") - the link will hopefully help you with your planning.

Don't worry too much about knowing any "code" (i.e. programming): you might need a few commands at the terminal instead, but someone here will be able to guide you if needed.

---

### Post by collinp on 2010-07-25
To address your questions in order of post:


[LIST]
[*]I haven't heard anything about fans not working in desktop setups. If anything, they'll just run wide-open all the time.
[*]I prefer Ubuntu because it's free as in cost and free as in the ability to edit and redistribute it at your will, and always will be. It also responds faster than Windows in most cases, and tends to use far less resources.
[*]You don't need to know any form of "code" to use Ubuntu. Unless you're a power user, everything can be managed through the GUI.
[*]To answer that question, it really depends upon what you're wanting to do. Almost every, if not every, common task that most Windows users do can be done on Ubuntu.
[/LIST]

---

### Post by Proto_Blaze on 2010-07-25
the way i want to dual boot is to have 7 just for gaming, and pretty much everything else on the os is uninstalled... also is it possible to go to windows and install the game on the ubuntu section? and play it from windows? also you said the monitor displays temperature.. is it in Fahrenheit? and how do i get it to display?

---

### Post by nick_goodfate on 2010-07-25
> **Proto_Blaze said:**
> Next, why do you use ubuntu? why do you prefer it over windows and possibly mac?

[LIST]
[*]much faster
[*]this forum
[*]FREE OS and Apps
[/LIST]

---

### Post by iponeverything on 2010-07-25
> **Proto_Blaze said:**
> the way i want to dual boot is to have 7 just for gaming, and pretty much everything else on the os is uninstalled... also is it possible to go to windows and install the game on the ubuntu section? and play it from windows? also you said the monitor displays temperature.. is it in Fahrenheit? and how do i get it to display?

from the package manager install lm-senors and and the senors applet.

The add the applet to tool bar. Right click on the applet to change the preferences about what would like displayed. The applet shows in Celsius, Fahrenheit or Kalvin. You can also monitor fan speed.

---

### Post by Proto_Blaze on 2010-07-25
> **iponeverything said:**
> from the package manager install lm-senors and and the senors applet.

The add the applet to tool bar. Right click on the applet to change the preferences about what would like displayed. The applet shows in Celsius, Fahrenheit or Kalvin. You can also monitor fan speed.

package manager? i have yet to see ubuntu

---

### Post by collinp on 2010-07-25
> **Proto_Blaze said:**
> also is it possible to go to windows and install the game on the ubuntu section? and play it from windows?

From my knowledge, such a setup isn't possible. You have to install Ubuntu programs while booted into Ubuntu, and Windows programs while booted into Windows.

For reference, if you're still having second thoughts about Ubuntu, you can test-drive it under Windows 7 using the Wubi utility. Wubi allows you to install Ubuntu under Windows without going full on and installing it to the hard disk in a standard install. If you decide that you're not happy with it and want to remove Ubuntu, you just uninstall it like any other Windows program. [http://wubi-installer.org/](http://wubi-installer.org/)

Also, when you boot the Ubuntu CD, a standard CD should give you the option to boot into a LiveCD version of Ubuntu. LiveCD means that it acts like a normal installation of Ubuntu, but it's not actually installed on the hard drive - it's running completely in RAM. Once you reboot or shut down your computer, any changes made to the LiveCD are lost as the RAM is wiped. Along with Wubi, it's a good way to get a "feel" for Ubuntu and see if you like it or not.

---

### Post by mbsullivan on 2010-07-25
> also is it possible to go to windows and install the game on the ubuntu section?

Yes, but only if you bastardize what you might refer to as the "Ubuntu section" (in terms of file systems). In short, things get complicated and messy, and I don't see why you'd want to.

Mike

PS: Upon further research (I don't use Windows), it looks like it MAY be possible to mount an ext3/ext4 partition under Windows fairly reliably now using [ext2fsd]("http://www.ext2fsd.com/") (see howto [here]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/") and elsewhere by Googling it). This would let you "peek" into something which you placed into Ubuntu's partitions while still leaving the partitions/file systems fairly untouched.

That being said, I still don't see why you'd want to do it this way.

PPS: > package manager? i have yet to see ubuntu

Put the games under Windows. I just decided for you. :)

---

### Post by Proto_Blaze on 2010-07-25
i dont need wubi, i have the installer on a flash drive set up, but my parents are strict with the current laptop (family laptop... i have to maintain it because they go into sites with viruses) so im waiting to get my new rig before playing with it... also is it better to just have 2 hard drives with an os on each? or dual boot 1 hard drive?

---

### Post by collinp on 2010-07-25
> **Proto_Blaze said:**
> also is it better to just have 2 hard drives with an os on each? or dual boot 1 hard drive?

If you're worried about space issues, two hard drives could be advantageous. However, if space isn't an issue, then it comes down to mostly personal preference. If one hard drive fails, the other will still keep going, etc.

---

### Post by Proto_Blaze on 2010-07-25
> **collinp said:**
> If you're worried about space issues, two hard drives could be advantageous. However, if space isn't an issue, then it comes down to mostly personal preference. If one hard drive fails, the other will still keep going, etc.

its more like

1 500gb hdd with ubuntu and 7
2 250gb hdd, one with ubuntu, and the other with 7

which would be better?

---

### Post by collinp on 2010-07-25
> **Proto_Blaze said:**
> its more like

1 500gb hdd with ubuntu and 7
2 250gb hdd, one with ubuntu, and the other with 7

which would be better?

I would probably pick the second setup with two hard drives, due to my point in my previous post: "If one hard drive fails, the other will still keep going, etc."

---

### Post by mbsullivan on 2010-07-25
> 

1 500gb hdd with ubuntu and 7
2 250gb hdd, one with ubuntu, and the other with 7



I guess that depends on how much DATA you're planning on having, and how much GAME STUFF you're planning on having.

Hard drives have a fairly limited lifespan (1-5 years, probably 3 average if you use it everyday), so it'd be better to have 2 if you think that you'll have:

[INDENT]1. less than 250GB of stuff on your desktop (everyday) system
2. less than 250GB of games[/INDENT]

However, it really doesn't matter THAT much. If there're any other things you're worried about, go with the 500GB drive.

Mike

---

### Post by Proto_Blaze on 2010-07-25
> **mbsullivan said:**
> I guess that depends on how much DATA you're planning on having, and how much GAME STUFF you're planning on having.

Hard drives have a fairly limited lifespan (1-5 years, probably 3 average if you use it everyday), so it'd be better to have 2 if you think that you'll have:
[INDENT]1. less than 250GB of stuff on your desktop (everyday) system
2. less than 250GB of games[/INDENT]However, it really doesn't matter THAT much. If there're any other things you're worried about, go with the 500GB drive.

Mike

the life span is really that short?

---

### Post by collinp on 2010-07-25
> **Proto_Blaze said:**
> the life span is really that short?

I think that was an understatement (this computer's hard drives are all over 7 years old and running fine).

---

### Post by cj.surrusco on 2010-07-25
> **Proto_Blaze said:**
> its more like

1 500gb hdd with ubuntu and 7
2 250gb hdd, one with ubuntu, and the other with 7

which would be better?

I would probably go with the one hard drive for both. That way, you can resize the partitions if you feel that you need more space in either of the operating systems. Then again, if you have 2 disks, you could add a partition for Ubuntu on the Windows drive, or vice versa. It doesn't really make a difference either way. 

> **collinp said:**
> I would probably pick the second setup with two hard drives, due to my point in my previous post: "If one hard drive fails, the other will still keep going, etc."

Well wouldn't you have the same risk either way? If you add another disk, wouldn't you double your chances of having a failure of losing half of your data? ;)

---

### Post by Proto_Blaze on 2010-07-25
ok, theres other question... but i cant remember them at this moment... thanx for everything

---

### Post by cj.surrusco on 2010-07-25
> **collinp said:**
> I think that was an understatement (this computer's hard drives are all over 7 years old and running fine).

I agree. I have used 6 different hard drives (each of them for more than 3 years) and have never experienced a fail. Also, I have hard drives in right now that are 5 years old and still fine.

---

### Post by Proto_Blaze on 2010-07-25
i remember what i want to ask!!! if i have the same program installed in both os's could i pull up files from each other?

---

### Post by slooksterpsv on 2010-07-25
> **Proto_Blaze said:**
> i remember what i want to ask!!! if i have the same program installed in both os's could i pull up files from each other?

Like a document, sure, if you have a DOCX file you read on windows, you can open it up on Linux no problem.

Same with other programs that are compatible, openoffice, pdfs, etc.

---

### Post by Goolie on 2010-07-25
If you're spending all that moneys on HDD get a SSD =P

But, as you use Ubuntu more and more you'll find you'll use Windows less and less.

A little adaptation.  And I agree with some of the above posts to get it booted from a USB / CD and test it out in that manner.  Best way to see how everything running before you really drop a whole new OS in there. 

Good luck, and cheers!

---

### Post by Linux&amp;Gsus on 2010-07-25
In regards to hard drives I would use 2. However, you'll need to know how big you need them.

Just for the theoretical exercise...
You said that you would use Win7 pretty much only for games, everything else on Linux. If 250GB is enough, then you'll get one of those for your everyday Linux and put that in as 2nd HDD (You'll need to install Windows first, on the 1st HDD to make Windows happy (that is still the case right, Windows needs to install on the 1st HDD?)).
So, for your 1st HDD you could make a partition for Win7 and your games, e.g. 70GB, plus another 250GB partition. This extra 250GB partition is for your backup of you files from Linux.

That would make it then:
HHD 1: Win7 + Backup = 320GB
HDD 2: Linux = 250GB

But as I said, you need to do the math yourself according to your needs of HDD space.

Also, you need to be aware of the limitations of this backup! You still have your data if you Linux drives goes south. If the other one dies it will take your saved games with it, if you haven't backed them up somehow, but you still have the original files.
That is a heck lot better then no backup but, of course, it is not a protection against everything.

Cheers,
L&G

---

### Post by mbsullivan on 2010-07-25
> 
Originally Posted by Proto_Blaze View Post
the life span is really that short?
I think that was an understatement (this computer's hard drives are all over 7 years old and running fine).

Well, it's hard to get an answer that will apply uniformly to EVERYBODY, but I've found that heavily accessed disks start failing at 1-3 years. 

For normal usage, I'd say probably 5-?, but it's telling that manufacturer's warranties used to extend for 3 years, and now often only extend for 1.

I've had almost all of my drives die on me eventually, at least the ones which were big enough just not to chuck after a while. However, some have lasted 6-7 years of abuse.

The point is: harddrives die... For normal use, hopefully it'll last long enough that you're ready to get a better/bigger/fancier one anyway. But it's also worth keeping in the back of your mind.

Mike

PS: I've never had a drive die in warranty, only just out... So they know what they're doing. :(

---

