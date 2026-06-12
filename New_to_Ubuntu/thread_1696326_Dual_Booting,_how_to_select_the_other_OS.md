---
title: "Dual Booting, how to select the other OS"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by Churchwarden on 2011-02-27
When I installed Ubuntu this morning I chose to install it alongside W vista HP.  Starting up the computer always takes it into Ubuntu, without giving me the option of selecting windows.

What have I done which I ought not to have done or not done that which I ought?

Nick

---

### Post by hansolo4949 on 2011-02-27
first of all, there is a good chance nothing bad has happened, so don't panic. Second, open up a terminal and type ```
sudo update-grub2
```

Then reboot. If you do not get a selection screen, reboot and press shift while you are booting up, that will force a grub screen to pop up. If windows is not on there, then immedately go into your windows partition, and get all of the data you need out of there, because any further fixes will get hairy.

---

### Post by col48 on 2011-02-27
Churchwarden
You _probably_ only hit the boot-it bit of the Windows partition from my reading elsewhere.  Hansolo's suggestion checks this.

All your Windows data will still be there.  I'm sure Hansolo will guide you home.  And welcome to Ubuntu.


You presumably have Lucid (10.04) or Maverick (10.10).

---

### Post by Churchwarden on 2011-02-27
> **hansolo4949 said:**
> first of all, there is a good chance nothing bad has happened, so don't panic. Second, open up a terminal and type ```
sudo update-grub2
```Then reboot. If you do not get a selection screen, reboot and press shift while you are booting up, that will force a grub screen to pop up. If windows is not on there, then immedately go into your windows partition, and get all of the data you need out of there, because any further fixes will get hairy.

Thanks, Hansolo4949 but how do I "open up a terminal"?

I really am *very* new to this!

N

---

### Post by Quackers on 2011-02-27
If you are still having problems please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Quackers on 2011-02-27
> **Churchwarden said:**
> Thanks, Hansolo4949 but how do I "open up a terminal"?

I really am *very* new to this!

N

Applications menu > Accessories > Terminal

---

### Post by col48 on 2011-02-27
To Open up a terminal it will be something like

Applications>Accessories>Terminal

(only something like because the path may have changed since v8.04)

NB prefixing a command with sudo is the standard way of running it as the administrator.

---

### Post by Churchwarden on 2011-02-27
> **Quackers said:**
> Applications menu > Accessories > Terminal

Oh no!

Thank goodness I have this old desktop working.  I can't even log into my laptop now.  the Ubuntu log in screen is not accepting the password that I have used at least 5 times!

I will go and have a look at those other links that we given to me a bit ago.

I fear that my brain is beginning to hurt!

Nick

---

### Post by Quackers on 2011-02-27
Check that your shift lock or num lock is not selected on your keyboard.
My brain hurts all the time. Isn't that normal?

---

### Post by Churchwarden on 2011-02-27
> **hansolo4949 said:**
> first of all, there is a good chance nothing bad has happened, so don't panic. Second, open up a terminal and type ```
sudo update-grub2
```Then reboot. If you do not get a selection screen, reboot and press shift while you are booting up, that will force a grub screen to pop up. If windows is not on there, then immedately go into your windows partition, and get all of the data you need out of there, because any further fixes will get hairy.


Managed to log in eventually. 

Right:  Having got into the Terminal and entered the code, I still boot up with no option to choose Windows.   I have tried holding down the shift key while booting up and it goes straight through to the desktop.

What's next?

Nick

---

### Post by hansolo4949 on 2011-02-27
the next step us to get your data off your hard drive, if you have any sensitive data in windows, since a reinstall seems to be in your future:(. Go to places, and select the hard drive that does not have "file system" for its name. Then, go to users, select the file that has your windows account name in it, and you should have my documents, the desktop, and all the other folders you may have your stuff in. now, just copy that to an external storage device, or copy it onto the Ubuntu desktop.

---

### Post by hansolo4949 on 2011-02-27
Another opion, if you just want to get everything back to pre-Ubuntu state, is to do this.


If you have a windows recovery cd, put it in and boot from it, like you did with the Ubuntu cd. Open ip a command prompt (cmd) and type: bootrec /fixmbr (note the spaces!) and bootrec /fixboot. Then reboot your computer. You should go right into windows without any problems. Now, all you have to do is get rid of the Ubuntu partitions, but that's another tutorial:)

---

### Post by Churchwarden on 2011-02-27
> **hansolo4949 said:**
> first of all, there is a good chance nothing bad has happened, so don't panic. Second, open up a terminal and type ```
sudo update-grub2
```Then reboot. If you do not get a selection screen, reboot and press shift while you are booting up, that will force a grub screen to pop up. If windows is not on there, then immedately go into your windows partition, and get all of the data you need out of there, because any further fixes will get hairy.

At the moment I can't use that computer.  I would guess that Ubuntu has overwritten the windows partition.  I guess this because Ubuntu has access to an alarmingly large part of the HD even though I believe that I asked it to install alongside Windows.

I took an image of the C drive on to an external HD and I have all my windows documents and photos backed up on to an external HD and this desktop so I need not, I believe, panic.

I now need to find out how to copy back the image on to the C drive, becasue ATM I am completely stuck as I can't get into grub to using the shift key as Hansolo4949 told me.  I wonder why my laptop does not respond in the way it should... 

Any other ideas.  Ubuntu seemed so quick and straightforward.

Nick

---

### Post by Churchwarden on 2011-02-27
> **Churchwarden said:**
> At the moment I can't use that computer.  I would guess that Ubuntu has overwritten the windows partition.  I guess this because Ubuntu has access to an alarmingly large part of the HD even though I believe that I asked it to install alongside Windows.

I took an image of the C drive on to an external HD and I have all my windows documents and photos backed up on to an external HD and this desktop so I need not, I believe, panic.

I now need to find out how to copy back the image on to the C drive, becasue ATM I am completely stuck as I can't get into grub to using the shift key as Hansolo4949 told me.  I wonder why my laptop does not respond in the way it should... 

Any other ideas.  Ubuntu seemed so quick and straightforward.

Nick

Isn't it odd how you type a questions go back to what you were asking about and immendiately answer your own question?  I got into the grub screen by, instead of holding the shkist key down, pressing it repeatedly and alternating between one shift key and the other.

Right: now to post what Hansolo4949 was asking for...

:)

---

### Post by Churchwarden on 2011-02-27
> **hansolo4949 said:**
> Another opion, if you just want to get everything back to pre-Ubuntu state, is to do this.


If you have a windows recovery cd, put it in and boot from it, like you did with the Ubuntu cd. Open ip a command prompt (cmd) and type: bootrec /fixmbr (note the spaces!) and bootrec /fixboot. Then reboot your computer. You should go right into windows without any problems. Now, all you have to do is get rid of the Ubuntu partitions, but that's another tutorial:)

Tried to do that but it stopped after a while with a big red screen with an all encompassing ERROR sign and note to say that it couldn't allocate temporary storage or something like that.

BTW What it says on the grub screen is

Ubuntu with Linux 2.6.35-22-generic
Ubuntu with Linux 2.6.35-22-generic (Recovery mode)
Memory test

Hoping and praying:???:

Nick

---

### Post by Churchwarden on 2011-02-27
> **hansolo4949 said:**
> Another opion, if you just want to get everything back to pre-Ubuntu state, is to do this.


If you have a windows recovery cd, put it in and boot from it, like you did with the Ubuntu cd. Open ip a command prompt (cmd) and type: bootrec /fixmbr (note the spaces!) and bootrec /fixboot. Then reboot your computer. You should go right into windows without any problems. Now, all you have to do is get rid of the Ubuntu partitions, but that's another tutorial:)

The recovery disc has been inserted and has run for a bit.  I am now on a screen which says Asus Preload and gives me a set of options:

1. Recover Windows to first partition only
2. Recover Windows to Entire Hard drive
3. Recover windws to entire hard drive with two partitions.

I am choosing 1...

The Error Screen has appeared and the actual wording is: "cannot set temp path to work in" 

I will try option 3.

Here's hoping.  Back soon...

N

---

### Post by Churchwarden on 2011-02-27
> **Churchwarden said:**
> The recovery disc has been inserted and has run for a bit.  I am now on a screen which says Asus Preload and gives me a set of options:

1. Recover Windows to first partition only
2. Recover Windows to Entire Hard drive
3. Recover windws to entire hard drive with two partitions.

I am choosing 1...

The Error Screen has appeared and the actual wording is: "cannot set temp path to work in" 

I will try option 3.

Here's hoping.  Back soon...

N

Interesting that Windows has been resinstalling for ages now.  Ubuntu only took about 5 minutes. The error screen did not appear and windows in now installing no end of Preload patches :smile:

Yawn...

N

---

### Post by col48 on 2011-02-28
Comment on post #13 - visibility of files in another partition

If you have two OS installed in separate partitions (eg Ubuntu 10.10 alongside Windows XP, or Windows XP alongside Windows 7) I would expect each to be able to see all the files on the other partition subject only to ownership/permissions limitations and the compatability of the file systems.  So if you need administrator permission you would have to be an administrator, (in Ubuntu terms, the root user) for instance.  You would be very rash to write files into the [boot] partition of another OS - this includes altering existing files or moving them - unless you knew it was safe, just in case you upset something fundamental there; but you could copy (not move) files from there to the running OS's partition as safely as copying them within the running OS's partition would be.

Whether the file you look at is meaningful in the current context is another matter - software which understands it may not be installed there.

---

### Post by hansolo4949 on 2011-02-28
So you decided to reinstall windows? good. Now, if you still want to use ubuntu, let's reinstall it, and see if the problem happens again (since you now have no sensitive data to spend hours reloading on there), so we can tell if this is a problem with your system, or a one-time issue, and I think it's a one-time issue. Sorry I did not get back to you sooner, Ubuntu e-mail must be messing up, for I have gotten no notifications...

---

### Post by Churchwarden on 2011-03-01
> **hansolo4949 said:**
> So you decided to reinstall windows? good. Now, if you still want to use ubuntu, let's reinstall it, and see if the problem happens again (since you now have no sensitive data to spend hours reloading on there), so we can tell if this is a problem with your system, or a one-time issue, and I think it's a one-time issue. Sorry I did not get back to you sooner, Ubuntu e-mail must be messing up, for I have gotten no notifications...


Don't worry about not getting back sooner.  I have kept myself and the laptop busy installing Windows Vista HP.  (It has taken ages!)  This is a list of the what I have done with it so far:

1.  Install vista from the recovery disc using the two partition option.
2.  Allowed it to do all the updates that it wanted: SP1, SP2 and some other stuff.
3.  Installed Firefox and security: ZoneAlarm, AVG, SpywareBlaster and Spybot.

I feel that I am now ready to have another try with Ubuntu.  I can reset the boot options and boot it up with the pen drive.  This I have done before.  I can click on the Ubuntu desktop icon "Install Ubuntu" and things should proceed.

There are one or two issues that I need to have explained though, if you have time and energy.:

1.  In my Vista (and XP setup on this desktop) I have all my user files in a separate partition (and separate internal hard drive on the desktop).  I use OpenOffice in the Vista environment so there are lots of OO docs in the user partitions.  The questions are: a) will these partitions be visible from Ubuntu?  b) is it sensible to access them and work on them from Ubuntu or will I be storing up some sort of problem for myself?

2.  Can I set up extra partitions from Ubuntu with the equivalent of the partition managing software in Vista or Partition Magic in XP?

I look forward to the words of the people who know!  :)

All the best

Nick

---

### Post by hansolo4949 on 2011-03-01
The answer to both of your questions is yes. You can see all Windows partitions from Ubuntu, and read/write from them. You can also create partitions using a free partition manager called Gparted, which is available in the software center.

---

### Post by col48 on 2011-03-02
```
a) will these partitions be visible from Ubuntu?

```Yes, and if permissions stop you reading or writing them these can be adjusted from Ubuntu.

```
b) is it sensible to access them and work on them from Ubuntu or will I be storing up some sort of problem for myself?
```There is only a problem - and it's an inconvenience rather than a crisis - with working on documents cross-partition if you want to read them from both sides of the border and the software on one side can't cope - it's the same kind of issue as trying to read a document written by Word2007 when all you have is Word97. An experiment with a disposable document will not do any damage and may be reassuring.  Both with OpenOffice and Word or Excel you can 'Save As' in an older format which the other party can understand.

```
Can I set up extra partitions from Ubuntu with the equivalent of the partition managing software in Vista or Partition Magic in XP?

```As Hansolo has said, yes, using gparted.

---

### Post by Churchwarden on 2011-03-02
Thanks very much.  I am now happily using Ubuntu and I can get to windows when I really need to.

I would rather like to use Ubuntu with many of my windows files but leave them where they are.  At the moment I can't find a way to get Documents to point to a folder other than the one it defaults to.  In Vista you can do this.  Am I missing something?

Nick

---

### Post by col48 on 2011-03-03
This ventures in deeper than I would go, as I don't keep anything in Documents anyway.  But I do observe that some apparent folders are actually links to other folders, so it must be possible.  But I wonder if it would be stable given that it will be pointing to a different partition? But if it is always mounted in the same place (and if the Windows partition is always mounted when Ubuntu is running) it ought to be OK.

(Later):

The ln command (use it in Terminal) can set up a link (like a Windows shortcut).  Look it up with ln --help in Terminal.  You would need a symbolic link (a softlink as opposed to a hardlink) as it links to a different partition.  Bear in mind I have never used this myself.
Watch out - file permissions could trip you up.

Hope this helps.

---

