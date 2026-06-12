---
title: "Question on saving Thunderbird and re-installing my OS"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by listerdl on 2009-11-11
Hi, I have a few issues with my ubuntu intrepid in that the sounds simply doesnt want to work and flash just doesnt play. I have tried a million different things but it seems that it might just be easier to re-install which I would happily do - but - my Thunderbird is on this laptop which is my lifeline....

I am thinking to save the Thunderbird, (TB) on a portable flash drive? Or on a partition in ubuntu? and then re-install the OS followed by re-installing TB.

Apparently this can be done by simply copying your "~/.thunderbird" folder - this includes both your profile seetings and your mail folders.

Does that sound right to you? THANKS

---

### Post by jotto! on 2009-11-11
I use Tb on my windows box..Im new to Ubuntu.
Whenever I want to reformat my XP box, I simply copy across the profile folder to a USB stick or 2nd HDD and then when reinstalled, simply copy it back. All mail and folders back where they should be.

---

### Post by alphaniner on 2009-11-11
Yeah, you've got the right idea.

Better yet, though, you could store your profile permanently on a thumb drive, so you could access it regardless of what OS you are running at the time.  I highly recommend it!

---

### Post by listerdl on 2009-11-11
Thanks so just to confirm that I am doing the right thing - (and dont worry I wont blame you if anything goes wrong!! ;) )

I need to copy this folder: .mozilla-thunderbird to a thumbdrive. Reinstall ubuntu, same version, then install Thunderbird - locate the same folder and overwrite that with the old current version? Thanks!!

---

### Post by oldfred on 2009-11-11
If you want to save your bookmarks and settings you can do the same with firefox. 
Start tbird once to create a default profile & just replace that with your archived profile and directories. The profile file has the location of the files.

---

### Post by listerdl on 2009-11-12
> **oldfred said:**
> If you want to save your bookmarks and settings you can do the same with firefox. 
Start tbird once to create a default profile & just replace that with your archived profile and directories. The profile file has the location of the files.

So are my TB folders and emails not stored on my local machine? Does the profile simply act as a Unique Indicator?

---

### Post by mkvnmtr on 2009-11-12
All of your Thunderbird settings and mail are stored in your home in the .Mozila-thunderbird file. This is the one you need to save. Then on your new installation look for that file in your home.mRemove it to the trash and replace it with the one you saved. You can do the same thing with the .mozilla file to save your Firefox and other Mozilla browser settings and bookmarks. When you open your home click on the show hidden files  and you will see the files.

---

### Post by mister_p_1998 on 2009-11-12
OK no problem, I did this recently,
drag the contents of .mozilla-thunderbird to your new home dir.
you'll see theres a file called profiles.ini

Contents below:

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=lr010s8b.default

Where it says Path= you have to make sure either the folder name is called the same as the one in profiles.ini (in the above case lrr010s8b.default) ,
or rename the entry in the profiles.ini to match the name of the folder in yours: XXXXXXX.default.

the way I did it was install a virgin copy of thunderbird onto the new install, delete the XXXX.default & profiles.ini and copy my originals into its place.

Worked a treat!

Steve

---

### Post by ukripper on 2009-11-12
> **listerdl said:**
> 

Apparently this can be done by simply copying your "~/.thunderbird" folder - this includes both your profile seetings and your mail folders.

Does that sound right to you? THANKS

Yes but it is ~/.mozilla-thunderbird, that is what i do everytime for my users if they don't have separate home partition already.

---

### Post by waspbr on 2009-11-12
If you are going to do a new install then you might consider making a /home partition, during the installation just allocate space for a root partition (/) [normally minimum of 5-10GB] and and the remainder of the space you use for a /home (and a swap of course). 

The benefits of having a home partition is that you can simply install a new version of ubuntu on the root  partition and you personal settings and accounts will remain the same. 

Personally I often reserve space for 2 root partitions, I use one for a stable release and a second one for a testing one.

All the benefits of a fresh install and I get to keep my account intact.

---

### Post by gdonwallace on 2009-11-12
You have it right.  Copy the .mozilla-thunderbird directory.  That will get all your settings and your emails.

As for firefox there is a much easier way.  Download the xmarks plugin for firefox.  The plugin will save your bookmarks and passwords to an online folder.  When you re-install firefox after the reinstall of the OS; just install firefox with the xmarks plugin.  It will prompt for a login and then download your bookmarks and passwords to your new firefox install.  Also, when ever you add a new password or bookmark, xmarks will prompt to re-sync with their server and keep everything up to date.  Xmarks is a real life saver for me.

---

### Post by listerdl on 2009-11-12
> **mister_p_1998 said:**
> OK no problem, I did this recently,
drag the contents of .mozilla-thunderbird to your new home dir.
you'll see theres a file called profiles.ini

Contents below:

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=lr010s8b.default

Where it says Path= you have to make sure either the folder name is called the same as the one in profiles.ini (in the above case lrr010s8b.default) ,
or rename the entry in the profiles.ini to match the name of the folder in yours: XXXXXXX.default.

the way I did it was install a virgin copy of thunderbird onto the new install, delete the XXXX.default & profiles.ini and copy my originals into its place.

Worked a treat!

Steve

So simply you drag over the entire folder called: .mozilla-thunderbird to a thumbdrive. Then re-install the machine. Then re-install a fresh copy of thunderbird. Then overwrite the .mozilla-thunderbird with the saved version and rename the profiles.ini?

Sorry to be so precise its just that I am fearful to lose like three years of emails here....thanks

---

### Post by mister_p_1998 on 2009-11-16
you can just replace the thunderbird folder  & ini with your old one..
Steve

---

