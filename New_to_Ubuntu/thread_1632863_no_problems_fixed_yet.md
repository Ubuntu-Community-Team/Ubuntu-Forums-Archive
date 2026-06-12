---
title: "no problems fixed yet"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by ByteOneZero on 2010-11-28
i have several issues to address,but i will begin with just one.nothing i try to accomplish in this os ever works the first time.this even applies to posted instructions followed to the letter.i am attempting to transfer the total contents of my internal hd to an external hd.i have tried booting from a live cd and following a set of terminal commands.(sudo /bin/bash)   then: mkdir /media/disk then: mount etc. as is noted by the how to geek website.my terminal just sits there idle waiting on more info.is there anyone out there able to help me dump my internal drive to my new external? i am not very pc literate and even less ubuntu literate.thanks in advance for any advice.

---

### Post by Daveth on 2010-11-28
to what purpose? To back-up, or create a separate home directory, or...?

---

### Post by ByteOneZero on 2010-11-28
t y i want my whole ubuntu set up on an external so i can put win 7 on my internal drive.my internal has been compromised into 2 sections due to a virus.im using the good half but i only want the internal for windows 7 now.

---

### Post by anewguy on 2010-11-28
It won't be quite as simple as just copying your hard disk.  Grub has to be updated in order to boot, I suspect your fstab will need to be changed, etc..

Why not just install to the USB drive, then just copy your data over to it?  Watch where grub goes.

It may also be necessary to restore the mbr on your internal hard disk before you can install Windows 7 since it currently is set for grub.

Dave

---

### Post by zipteye on 2010-11-28
> **anewguy said:**
> It won't be quite as simple as just copying your hard disk. Grub has to be updated in order to boot, I suspect your fstab will need to be changed, etc..
 
Why not just install to the USB drive, then just copy your data over to it? Watch where grub goes.
 
It may also be necessary to restore the mbr on your internal hard disk before you can install Windows 7 since it currently is set for grub.
 
Dave
 
Yeah, if you have Windows 7, you need to do Recovery console and type /Fixmbr,
or windows wont boot.
 
I'm just going out on a limb here , but... install Ubuntu to your external drive.
Then mount your external drive throught the ubuntu that you have on your internal drive.
Then cp the files and or directories you want to the external drive.
Then update-grub
 
**Caution** 
 I may be totally off the mark and you should probably wait till someone here either confirms or denies this approach.
**

---

### Post by ByteOneZero on 2010-11-28
well thanks dave for the response.unfortunately all youve said is complete greek to me.in windows you just back everything up at control panel.i am soooo frustrated at linux's operation.almost 2 months of trying and i'm still befuddled at the terminology being used.i am not computer literate ,just stubborn.

---

### Post by ByteOneZero on 2010-11-28
win 7 is not installed yet.my only os now is lucid.i don't understand cp or any of those terms sorry.if that means i cant do this then ill just pay someone i guess

---

### Post by anewguy on 2010-11-28
> **ByteOneZero said:**
> well thanks dave for the response.unfortunately all youve said is complete greek to me.in windows you just back everything up at control panel.i am soooo frustrated at linux's operation.almost 2 months of trying and i'm still befuddled at the terminology being used.i am not computer literate ,just stubborn.

I don't think we're going to be able to explain things in quite that simple of terms when some of what is involved is technical to some degree.  I think we would probably spend a lot of unneeded time walking you through each step.

So, what I would suggest, is that you find a friend, a co-worker, whatever, that is more knowledgable in computers and ask them to help you.  Depending on where you live, there may be a group of students at a local high school or university that are familiar with Linux and Windows and would be willing to help you - just call either and ask if there is someone in the computer technical support you can talk to - they'll be happy to give you a contact amongst the students.  When someone local is helping you and they might have a question, please feel free to post back here for more help.

This may seem like a strange suggestion to some on the forum, but with a novice user like this without any of the "simple" technical knowledge (like what the mbr is, how to copy files, how to be sure grub is installed correctly, etc.), I think they would be better off trying to find 1-on-1 local support, a physical body that can help them.  

ByteOneZero, check local schools and local computer clubs - you will most likely find someone willing to help for either very little or no cost at all - the ubuntu community is pretty good at free support.  I'm sorry if what I suggested originally confused you - that wasn't my intention.  And don't worry about knowing what all that means - let someone else help you, you may find a computer buddy or club that interests you and might help you learn to whatever level you desire.  If you don't have a desire for any deeper knowledge that's fine, too!

Please let us know if there is anything we can do to try to help you find some local support.

Dave ;)

---

### Post by zipteye on 2010-11-28
Ok, well as one beginner to another...
Go ahead and install the Windows 7 on your internal.
Once it is all done installing and you set up your account (or accounts), 
go download the newest Ubuntu to your Desktop, then burn it to a DVD. 
It should be a .iso image.
 
Here's one option:
With windows 7,
Go to disk management, or type Disk Management in the search box.
Once you are at Disk Management, if you have a big Hard Drive, click on the C: drive and choose 'Shrink' from the actions. 
Then you will have to type in how much space you want to shrink it by. (In megabytes)
So if you want 5 Gigs of free space, that would be 5000.
 
Put your Ubuntu Disk in the CD/DVD Rom tray and reboot winfdows.
It should load the Live Disk for Ubuntu.
Choose the Install option.
Choose the free space option.
Follow the propmts to install Ubuntu.
 
You do'nt need internal and external drives this way.
 
If you mean you want to retrieve all of you old windows files from your corrupted internal... then I'm not sure how to do that. But you can see and access windows files fro the Ubuntu Live disk.

---

### Post by ByteOneZero on 2010-11-28
i already have a live disc for ubuntu.is that sufficient?otherwise i think ill give it a shot if i can figure out that GRUB reference in the earlier response. thanks,Tony

---

### Post by zipteye on 2010-11-28
Yes, that should be sufficient.
Once Ubuntu is installed, it will give you a prompt to restart the computer.
Take the live disc out first then click on the restart button.
 
Now, when I had to re install, I clicked that and it hung on me when it went to restart.
Dont panic.
Just hold down the power button on the computer till it shuts down.
Wait about 20 seconds the power it back up.
When it boots back up it will list several options to boot from. 
Use the arrow keys on your keyboard to go up and down the list.
If you want ubuntu pick the first ubuntu in the list.
If you want Windows 7, pick the first Windows in the list.
 
 
We can deal with trimming down the options later.

---

### Post by anewguy on 2010-11-28
I would suggest that if you want everything back on the internal drive, and ubuntu is already installed to the internal drive, including the files, programs, etc., you mentioned wanting to save in your first post, that the "easiest" way to accomplish this might be to leave your ubuntu where it is, leaving grub as it is.  Although we normally advocate installing Windows first and Linux second, this may be one case where to accomplish what you want may be easier just by re-installing Windows.  After doing so, you initially won't be able to boot ubuntu but fear not - it's a simple matter to straighten that out.

However, if you have nothing in your current ubuntu installation that you need to save, that will help make things a little easier.

I'm still concerned, however, about you tackling all of this if your skill set in regards to the mbr, Windows and Ubuntu, and how it all fits together, is limited.

It's up to you, but seriously look into local help.  If you can't find that, then post back and I'll try to come up with some simple step-by-step to get you where you want to go.

unfortunately, the good-intentioned instructions provided so far won't get you there.

Dave ;)

EDIT:  You also mentioned in your PM about this being a some what older computer.  Be sure it will actually run Windows 7, that Windows 7 drivers are available, etc., before you try to install it on that computer.

---

### Post by ByteOneZero on 2010-11-30
well thanks to the caring "geeks" here. i am 50% along.my whole rig is on my big external drive.now i am not totally sure about wiping my internal drive but i'll try and search how.i have booted from new set up to make sure i didnt lose my stuff.so my only trepidation is why can i only see half of my internal drive contents?one partition is invisible.i would love to erase the whole thing since im sure i cant recover the corrputed half (Without paying big bucks to the pros).i understand in windows you generally can only save data and not apps or programs from these typical recovery setups anyhow. thanks again,Tony

---

