---
title: "What happens to /home when you reinstall?"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by Daremo_06 on 2009-07-13
I ended up reinstalling 9.04 over the weekend.  I had previously saved my user home files to a separate drive.

Then I partitioned the drive from the single 80G drive I had been using to instead create an 8G root drive.  Turned the other 70G or so into /home.

When I then reinstalled 9.04.  I migrated my user files back into /home/username, but I am learning after the fact that it appears Evolution stores email data in ~$HOME/.evolution.  So if I did not backup or copy that folder myself before starting my installation... all of my email data is gone correct?

Also, there seems be very little evolution support here on site.  Searching on site brings up multiple posts asking questions about Evolution and many of them have only the poster either bumping or updating the thread on what else they have done.  Any reason why no one seems to know Evolution?  Is there a forum that they (Evolution developers/experts) normally post in elsewhere?

Also going back to the partioning.  What is the best way to configure my partitions to achive the following.

1.  Make it easy to completely re-install

2.  Make it easy to back up important files

3.  Help prevent dumb mistakes from taking out previously said important data (such as re-installing without saving/backing up everything)

Is the current ~root and ~home partitions enough, or should I create a third?

Thanks

---

### Post by philinux on 2009-07-13
Having /home on its own partition is what I do. It's easier to do this at the first install rather than afterwards.

I have three partitions.

/
/home
swap

Click the psychocats link below.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by twright on 2009-07-13
Hi,
whilst if you have not backed up the folder the data is probably gone there are ways that you might possible be able to recover it.

The first step is to stop using the computer on which the data was stored, every time you write to disk you are drastically reducing the chances that your data can be recovered.

The next step is to look at photorec, testdisk and other data recover tools; if any trace of your data remains they may be able to get it back:
[http://en.wikipedia.org/wiki/PhotoRec](http://en.wikipedia.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Good luck...

---

### Post by theozzlives on 2009-07-13
A /home partition should be in the default install. It's invaluable to keep your files and settings. Yeah your mail is pretty much gone.

People around here seem to like Thunderbird, I like Evolution, that's probably why people can't get much responce.

---

### Post by Daremo_06 on 2009-07-13
> **theozzlives said:**
> A /home partition should be in the default install. It's invaluable to keep your files and settings. Yeah your mail is pretty much gone.

People around here seem to like Thunderbird, I like Evolution, that's probably why people can't get much responce.

Yeah, I was fairly sure that I had nuked it.  I'm fairly annoyed about this too because I researched what to back-up before doing this.  All I saw was to back up your home/username folders and that was suppose to be all you needed.  Again the lack of complete information about something related LINUX strikes someone.  This is prevailent problem with LINUX and if we really want to see it grow to be popular with the general computing public, these types of things need to be prevented if possible.

About Evolution, if its not popular here, then WHY is it the default email client for the distros?  That seems a little silly to me.  Why would you have it in your distro if all your experts use something else?  That speaks to A) the application itself apparently has something about it that many high level users don't like and B) your high level experts/users wont have that much familiarity with the application and hence can't support it very well.

Thankfully I only just recently migrated over to Evolution, about 3-4 months ago and I still have my old outlook files, so I can get older emails back.  Its just the past few months.  

GRRRRR....All of this could have been prevented had someone said to copy BOTH your /home/username folders and ~/.evolution folders when backing up important things before re-installing distros.

---

### Post by twright on 2009-07-13
> **Daremo_06 said:**
> Yeah, I was fairly sure that I had nuked it.  I'm fairly annoyed about this too because I researched what to back-up before doing this.  All I saw was to back up your home/username folders and that was suppose to be all you needed.  Again the lack of complete information about something related LINUX strikes someone.  This is prevailent problem with LINUX and if we really want to see it grow to be popular with the general computing public, these types of things need to be prevented if possible.

About Evolution, if its not popular here, then WHY is it the default email client for the distros?  That seems a little silly to me.  Why would you have it in your distro if all your experts use something else?  That speaks to A) the application itself apparently has something about it that many high level users don't like and B) your high level experts/users wont have that much familiarity with the application and hence can't support it very well.

Thankfully I only just recently migrated over to Evolution, about 3-4 months ago and I still have my old outlook files, so I can get older emails back.  Its just the past few months.  

GRRRRR....All of this could have been prevented had someone said to copy BOTH your /home/username folders and ~/.evolution folders when backing up important things before re-installing distros.
Most people actually just use webmail or at least imap these days so they just nuke their configuration files every time they reinstall as to be left with a "fresh" install.

I do not think that more people use thunderbird than evolution, just that those which do are more vocal about it :-)

---

### Post by Cypher on 2009-07-13
When someone suggests that your should backup your /home/<username> directory before doing a re-install, they should also be telling you HOW to do the backup. If through a GUI, the tool should be smart enough to pick up any hidden files/folders. If through the standard "cp" command, then it's imperative to add the "-a" flag in addition to the "-r" flag. The first saying to copy All files including hidden ones and the second saying to copy all the folders recursively.

Second, just like the outlook PST file you've been saving, if you were to go re-install Linux, you should've gone into Evolution and have it export the emails to a file of your liking and taken steps to save it.

Every distrobution maintainer has to choose some set of tools that are easy for people to use out-of-the-box without requrining them to set anything up. In these cases, evolution fits the bill perfectly. There are other tools that are out there, but the need for them is instigated by people finding something lacking in Evolution and migrating. So Evolution, in itself, is a perfectly good email client for a majority of people who use it.

Some users prefer to use Thunderbird, perhaps because they may use it in Windows environment and are comfortable with the familiar surroundings.

None of this is a limitation of Linux per say, but is with the kwowledge you garner using it. Re-installation can, and usually is, a desctructive scheme. Before re-installing Windows you'd go out of your way to ensure that all of your important files are backed up. Just because you have a seperate /home partition and re-installing Linux is a cinch in most cases, doesn't mean that you shouldn't be careful and KNOW what you are doing before doing it.

I, for one, think very long and hard before creating my partition scheme. I've traditionally used minimally 5 partitions: /, /usr, /var, /home and SWAP. Of these partitions, the /usr and /home get a good amount of space since this is where all of my applications (/usr) and my documents (/home) go. The others are enough to do what they need, but I don't waste a ton of space on them...

Now, whenver I do a re-inatllation of the same Linux distro or any other, I always format /, /usr, /var and SWAP. But I leave /home intact and just re-mount it back in the new distribution. This way the files are intact and then I can go ahead and remove any unused stale files from the previous distributions at my own leisure.

This scheme has allowed me to play with various versions of Ubuntu, Fedora and finally LinuxMint now which is the distro I'm using. If a new distro strikes my fancy, it doesn't take me long to get the new one running while keeping all of my files still handy..

---

### Post by Daremo_06 on 2009-07-13
> **Cypher said:**
> Now, whenver I do a re-inatllation of the same Linux distro or any other, I always format /, /usr, /var and SWAP. But I leave /home intact and just re-mount it back in the new distribution. This way the files are intact and then I can go ahead and remove any unused stale files from the previous distributions at my own leisure.

So how do I keep the distro from installing defaults into /home and overwriting things like .evolution ect ect?  I don't recall seeing any options for this during the install, but I might not have noticed it...

Also, to take my current 2 partition config and model it after yours, I would have to re-install the distro right?  Or could I create the partions using G-parted off the install disk and then run some commands to re-associate things?

Also about my previously backing up /home/username, the point I was trying to make was that it would be nice to have *EVERYONE* just add in something like.. 

"when you make back-ups, make sure you include not only your /home/username folders, but also make sure other applications are not using ~/.<foldername> to store information (for example Evolution)"

Something like that would be a good practice, no?  

You are right about it being my fault in the end for not backing everything I needed up.  I wasn't intentionally trying to say its not my fault, its the people giving me the advice, and it appears now like thats how it might come across.

Thanks!

---

### Post by twright on 2009-07-13
> **Daremo_06 said:**
> So how do I keep the distro from installing defaults into /home and overwriting things like .evolution ect ect?  I don't recall seeing any options for this during the install, but I might not have noticed it...

Also, to take my current 2 partition config and model it after yours, I would have to re-install the distro right?  Or could I create the partions using G-parted off the install disk and then run some commands to re-associate things?

Also about my previously backing up /home/username, the point I was trying to make was that it would be nice to have *EVERYONE* just add in something like.. 

"when you make back-ups, make sure you include not only your /home/username folders, but also make sure other applications are not using ~/.<foldername> to store information (for example Evolution)"

Something like that would be a good practice, no?  

You are right about it being my fault in the end for not backing everything I needed up.  I wasn't intentionally trying to say its not my fault, its the people giving me the advice, and it appears now like thats how it might come across.

Thanks!
Ubuntu does not create anything in /home on installation except an empty home folder if it does not already exist. Any .folders are created on login/when the application which created them is launched unless they already exist.

---

### Post by Daremo_06 on 2009-07-13
> **twright said:**
> Ubuntu does not create anything in /home on installation except an empty home folder if it does not already exist. Any .folders are created on login/when the application which created them is launched unless they already exist.

Wait a minute! I wonder if my emails are still on the drive then...  

My original installation used the whole drive.  This weekend I partitioned the drive and here is exactly what I did.

1.  Ran g-parted to resize the current partition down from 77GB down to about 65GB, I did NOT format this partition.

2.  Created a new partion about 8g in size.  Named it Root and formatted it to ext3.

3.  Renamed the partition that I resized to Home.

4.  Re-installed the distro.

So if I understand you correctly, since I took my original entire partition and made it smaller and called it /home, it SHOULD still have ~/.evolution on it with all my email data correct?  If that is all correct, then I merely need to move that folder to the new ~/ and I should have my emails back, right?

Lastly, I just found this...[https://answers.launchpad.net/ubuntu/+source/evolution/+question/45271](https://answers.launchpad.net/ubuntu/+source/evolution/+question/45271).

---

### Post by DizzyEwok on 2009-07-13
Yep, all your email data should be there.

---

### Post by LewRockwell on 2009-07-13
> **Daremo_06 said:**
> I ended up reinstalling 9.04 over the weekend.  I had previously saved my user home files to a separate drive.

curious exactly how /home was "saved" as this might prove helpful to others on what to avoid

personally I use clonezilla to make a complete clone of each and every bit and byte

> **Daremo_06 said:**
> 
Then I partitioned the drive from the single 80G drive I had been using to instead create an 8G root drive.  Turned the other 70G or so into /home.

When I partition an 80GB I divide it up as follows:

One 15-20GB primary partition at the beginning of the drive(I always consider the first primary partition as "available" for windoze if a future customer desires it, in the meantime any *nix distro can play around there)

One primary swap partition, usually 1xMAXRAM(except in pre-loaded hard drives where I don't know what "maxram" is going to be...then the swap is automatically 4GB...personal preference of course)

One 10-15GB primary partition(usually used for "main" *nix distro)

And the rest is extended with whatever logical partitions are desired
(usually smaller partitions to "contain" various *nix distros or just data)

> **Daremo_06 said:**
> 
When I then reinstalled 9.04.  I migrated my user files back into /home/username, but I am learning after the fact that it appears Evolution stores email data in ~$HOME/.evolution.  So if I did not backup or copy that folder myself before starting my installation... all of my email data is gone correct?

I guess I've always operated under the assumption that /Home would contain everything inside of /Home(perhaps I'm mistaken)

> **Daremo_06 said:**
> 
Also, there seems be very little evolution support here on site.  Searching on site brings up multiple posts asking questions about Evolution and many of them have only the poster either bumping or updating the thread on what else they have done.  Any reason why no one seems to know Evolution?  Is there a forum that they (Evolution developers/experts) normally post in elsewhere?

Being a fan of Jimmie Vaughan, the "fabulous" Thunderbird is mandatory for me

> **Daremo_06 said:**
> 
Also going back to the partioning.  What is the best way to configure my partitions to achieve the following.

1.  Make it easy to completely re-install

I find smaller partitions preferrable
(how about those folks that have one OS and one partition on a TB drive...lol)

> **Daremo_06 said:**
> 
2.  Make it easy to back up important files

If you're constantly producing invaluable content and also can't afford the down-time of swapping to your most current clone, then you should be utilizing the proper raid array already

Otherwise, say you accumulate photos on your drive...you should be immediately be organizing them into folders and then those folders should be duplicated on flash media until such time as you decide to burn them to optical media(usually when you've accumulated enough to fill a CD or DVD)
(here again, if the photos are valuable you should be burning at least two copies of the archive)

> **Daremo_06 said:**
> 
3.  Help prevent dumb mistakes from taking out previously said important data (such as re-installing without saving/backing up everything)

see previous

> **Daremo_06 said:**
> 
Is the current ~root and ~home partitions enough, or should I create a third?

Here, personal preference wins hands-down

I personally use clones so that if my hard drive catches on fire, a clone can be slipped in asap

your mileage may vary...

.

---

### Post by Daremo_06 on 2009-07-13
Alright.. so I have been trying to find it, but i havent been able to.  Could I be looking in the wrong place or have the wrong permissions to look at it since what is now a /home partition USED to be a ~/?  

How would one search for a folder named .evolution?  I was using nautilus, am I better off dropping down into terminal and running command line search?  If so, how would i structure my command to find that folder no matter where it is or what its permissions are?

I am assuming I want to do the following

> find -name '.evolution'

That should find the folder if its anywhere on the drive correct?

Thanks!

---

### Post by Daremo_06 on 2009-07-13
> **LewRockwell said:**
> curious exactly how /home was "saved" as this might prove helpful to others on what to avoid

Wellll, I don't think I did it by the correct method :D.  I ran > gksu nautilus and then copied the /home/username folders of each account and put a copy of them on a 500g storage drive.

---

### Post by Cypher on 2009-07-13
> **Daremo_06 said:**
> Alright.. so I have been trying to find it, but i havent been able to.  Could I be looking in the wrong place or have the wrong permissions to look at it since what is now a /home partition USED to be a ~/?  

How would one search for a folder named .evolution?  I was using nautilus, am I better off dropping down into terminal and running command line search?  If so, how would i structure my command to find that folder no matter where it is or what its permissions are?

I am assuming I want to do the following



That should find the folder if its anywhere on the drive correct?

Thanks!

In the terminal, try
```

cd
ls -a

```
This will send you to your home folder (just incase you aren't there already) and show you all files and folders hidden or not. You can then scroll the window to see everything that's available to you.

Now as far the /home folder from your previous question, the installation doesn't do anything apart from creating the /home folder and populating it with some skeleton files. Since during the installation I just ask it to mount the existing partition, it checks and finds the skeleton files it would've created anyway and lets my modified versions be.

Now once I'm booted up, if I open up Evolution, it's going to see the .evolution folder from the previous Distro and either upgrade the configuration or not and start showing me my info. So, in essence, nothing changes if I use the same version of Evolution.

---

### Post by oldos2er on 2009-07-13
Evolution home page is here: [http://projects.gnome.org/evolution/](http://projects.gnome.org/evolution/)

---

### Post by Daremo_06 on 2009-07-13
Alright, I figured it out.

What ended up happening is I created a new /home partition that then had the original /home information inside it.  So once I navigated to ~/home/home/rob/.evolution I was able to find my mail.  I moved the folder into the correct .evolution folder and poof email restored.

I am having a few problems though and I imagine its due to some configurations and settings/file paths being screwed up now.

In the debug logs under help I am getting the current 4 errors

- Error while Storing Folder 'Inbox/Facebook'

- Could not create lock file for /home/rob/.evolution/mail/local/Inbox.sbd/Facebook: Permission denied

- Error while Fetching Mail.

- Could not create lock file for /home/rob/.evolution/mail/local/Inbox.sbd/Facebook: Permission denied

I tried moving the original .gconf evolution files, but that did not correct the error messages.

Suggestions?

---

### Post by LewRockwell on 2009-07-13
this might help or at least be food for thought:

[http://ubuntuforums.org/showthread.php?t=106191&highlight=%22Error+storing+folder+INBOX%22](http://ubuntuforums.org/showthread.php?t=106191&highlight=%22Error+storing+folder+INBOX%22)

.

---

### Post by Daremo_06 on 2009-07-14
Fixed my Evolution errors.

It was simply a matter of permissions

sudo chown -R USER:GROUP /home/USER/.evolution

---

