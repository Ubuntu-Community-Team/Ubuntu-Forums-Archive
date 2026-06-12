---
title: "Copying files from crashed windows with ubuntu"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by auggie_doggie on 2011-04-03
Hi Guys,
 
i'm a newbie and have a question. i have recently downloaded the recent version of ubuntu(10.10 desktop) and i need some help. i have booted ubuntu from the cd and i can see my crashed hardrive(win 7 64 bit).when i try to copy it to my external hardrive i get an message saying you do not have permission to write to this file. 
 
can someone please please explain to me in layman terms,step by step how to copy the files please. i have looked in this forum with help and the only thing i found was sudo nostrilus but i don't understand how to use it. also some forum said to download slax as slax could fix this problem by just dragging. unfortunately slax does not recognize my external drive.
 
your help in this matter is greatly appreciated.
 
regards

---

### Post by coffeecat on 2011-04-03
The problem would seem to be with the external hard drive. What filesystem is it formatted with? What is the exact error message?

Running 'gksudo nautilus' - not 'sudo nostrilus' - will give you a file browser with full root powers. This is sometimes helpful but it would be wise to find out what your particular problem is before running something with privileges you may not need.

You say you can see your crashed Win7. Do you mean that you can see the Win7 partition in the Places menu and that when you click on it, a file browser (Nautilus) window opens and you can see all the folders and files in your C: partition?

---

### Post by hakermania on 2011-04-03
You don't have the permission to do that, I'll try to help you:
1) From the places menu select the Windows partition so as to ensure it is mounted.
2) Open Applications->Accessories->Terminal
3) type in ```
sudo su
``` You'll become root immediately.
4) type in ```
cd /media/
```
5) type in ```
ls
``` You'll probably see something strange, like a hash, e.g. 6aaf11e4ccce63ab355372e5f3b10bfd
6) Type in the first letter/number of the hash it showed you after the word 'cd', e.g.```
cd 6
``` Then, press [TAB], the whole word will be automatically shown. Press enter
7) Now, type in ```
chown -R $USERNAME:$USERNAME *
``` Wait for this to finish and then try again to copy any file from the windows partition

---

### Post by auggie_doggie on 2011-04-03
@coffeecat:- i will give you a quick rundown,
 
in ubuntu->places->computer> i see cd-rw->39.2 mb volume->expansion drive(external usb NTFS)->OS(crashed windows 7 drive internal,NTFS)->recovery->filesystem
 
when i open OS drive->users->auggie doggie->videos
 
i want to copy the videos folder to my expansion drive(NTFS)
 
when i copy and go to the expansion drive(NTFS) i am unable to paste as the paste option is disabled from the context menu but i am able to place it to the dektop.
 
if i drag the video folder and drop it to the expansion drive, i get this error:
 
Error while copying to "/media/Expansion drive" you do not have permissions to write to this folder.
 
i was a after a step by step instruction  on how to copy the video folder to the expansion drive.

---

### Post by auggie_doggie on 2011-04-03
@ hackermania:- i will try your method and let you know how it went!!
 
really appreciate the quick responses!! :)

---

### Post by hakermania on 2011-04-03
Hmm, after seeing the exact error the drive in which you're trying to write may has the permissions problem!?

---

### Post by auggie_doggie on 2011-04-03
@ hackermania:- i tried your method and when i typed ls i did not get a hex addr but instead got: 
 
Expansion Drive OS in blue color. 
 
i then used cd E tab and got this:
 
cd Expansion(back slash-button does nt work on laptop) Drive/
 
chown -R $USERNAME:$USERNAME *
 
it was doing something in the background with some files and then came back to the promt.
 
i tried to copy and drag from the os drive to the expansion drive, i got the same error as before "that i did not have permission..."
 
also if ubuntu changed the file permissions, does that mean those permissions are permanent even when i connect to windows?

---

### Post by auggie_doggie on 2011-04-03
are there any live linux os that can actually use copy paste or drag and drop folder embedded into it?

---

### Post by coffeecat on 2011-04-03
> **auggie_doggie said:**
> are there any live linux os that can actually use copy paste or drag and drop folder embedded into it?

Yes, Ubuntu. But I can't follow what you are doing, and what do you mean by folder embedded within it? I suspect though that the NTFS filesystem on your USB drive might be inconsistent, caused by an unclean unmount last time you used it. Did you unmount it properly when you last used it? If the filesystem is unclean then it will be mounted read-only in Ubuntu in order to protect it from further damage. In which case you need to mount it in a Windows system and unmount it properly. Or possibly even run a chkdsk in Windows.

You are trying to copy to a NTFS-formatted external drive. If the filesystem is clean, it will be  automounted by Ubuntu read-write. You do not have to chown it - in fact you can't because NTFS does not support Linux permissions.

Let's be clear about what you are doing. Go to your Places menu and click on the entry which corresponds to your Win7 C: partition. A Nautilus window will open in the root of the Windows filesystem showing you folders such as Boot, Program Files, Windows and so on. Double-click on the Users folder to open it, and then navigate to the folder and files you want to copy. Push that windows to the left of the desktop.

Now plug in your USB NTFS drive, switch it on and let it automount. A new Nautilus window will open; push that to the right. Now simply drag and drop whatever you want from the left window to the right. If you still get an error message, then there is something wrong with the external drive. See above.

---

### Post by auggie_doggie on 2011-04-04
@ coffeecat:- i tried the instructions you gave me but it still comes up with the same error as before about permissions. i can see my external drive mounted but will just not copy the folder. i have tried a brand new usb flash drive(FAT 32) and it still does not copy and comes with the same permission error as before.

the embedded thingy i mentioned before was:

i meant isn't there a ubuntu that comes with drag n drop or copy paste feature already built into the os rather than invoking Nautilu.

---

### Post by Learning Linux 2011 on 2011-04-04
" in ubuntu->places->computer> i see cd-rw->39.2 mb volume->expansion drive(external usb NTFS)"

That is a little confusing.  Is 39.2 mb a typo?  Did you mean 39.2 GB?

Also, are you sure you aren't trying to copy to the CD-RW?

---

### Post by Learning Linux 2011 on 2011-04-04
Also (someone else may need to verify this), but I'm not sure if Linux will allow you to access 64-bit NTFS systems.

---

### Post by Learning Linux 2011 on 2011-04-04
Also, are you sure the drive itself isn't physically defective, i.e. with bad sectors, doesn't spin up properly, won't read/write, etc.

If you aren't sure, maybe you should download some disc utilities from the manufacturer.

---

### Post by auggie_doggie on 2011-04-04
ok guys i found something interesting. i tried to copy a file to my usb fat 32 and it worked with the copy paste but it did not work with my expansion drive which is in ntfs. so does that mean if i can get an external hardrive formatted in fat 32 it will copy? i will try this out shortly and keep you posted guys.

thanks

---

### Post by auggie_doggie on 2011-04-04
> **Learning Linux 2011 said:**
> " in ubuntu->places->computer> i see cd-rw->39.2 mb volume->expansion drive(external usb NTFS)"

That is a little confusing.  Is 39.2 mb a typo?  Did you mean 39.2 GB?

Also, are you sure you aren't trying to copy to the CD-RW?


what i meant was those were all the drives that i can see.cd-rw,39.2 mb volume,expansion drive

---

### Post by Learning Linux 2011 on 2011-04-04
Does your system have the NTFS utilities installed?  Go to you Ubuntu Software Center under your Application menu and search for 'ntfs'

You have to have NTFS support installed to write to NTFS.

Go to System -> Administration  and look for NTFS Configuration Tool



And yes, you could more than likely copy anything to any drive formatted with FAT32.  FAT32 isn't as picky as NTFS.

---

### Post by auggie_doggie on 2011-04-04
i could not find the ntfs configuration tool. how do i install itif i'm booting from cd?

thanks

---

### Post by Learning Linux 2011 on 2011-04-04
> **auggie_doggie said:**
> i could not find the ntfs configuration tool. how do i install itif i'm booting from cd?

thanks


You can either go to a Terminal (command line) and type:

```
sudo apt-get install ntfs-config
```Or use your Ubuntu Software Center and search for NTFS Configuration Tool and install it.

You can install it even if you are using the CD, just bear in mind that since you cannot permanently write anything to CD, it will be deleted when you shut down.  But then you can just re-download it if you need it again.


Then go to System -> Administration -> NTFS Configuration Tool to activate it. 
(You will be prompted for your user password).

---

### Post by auggie_doggie on 2011-04-04
@ learning linux 2011- i am not able to connect to the wireless network in ubuntu. so i searched online and found ntfs-config_1.0.1-1_all.deb

however when i install it i get an error message please see the screenshot. what am i doing wrong?

[IMG]http://i760.photobucket.com/albums/xx242/lord_kaiser83/Screenshot.png[/IMG]


thanks

---

### Post by coffeecat on 2011-04-04
@auggie_doggie, you said in your first post that you were using Ubuntu 10.10, but those screenshots are from an obsolete version of Ubuntu. Which version is it? NTFS support was not good prior to about 8.04. You need to run the 10.10 live CD. Then you will not need to install any NTFS packages and will probably have no problems.

And what is this "expansion drive" that you have mentioned repeatedly? How does it appear in Places? Is it "POCKET"?

[quote="Learning Linux 2011"]Also (someone else may need to verify this), but I'm not sure if Linux will allow you to access 64-bit NTFS systems.     [/quote]

No, that's OK. I've installed 64-bit Windows 7 to my main system and Ubuntu can read files in its partition just fine. I've not tried writing to the partition because that's a bad idea.

---

### Post by Learning Linux 2011 on 2011-04-04
Yeah, unfortunately there are some problems with wireless in Linux because the manufacturers won't cooperate with the developers of Linux.

Can you plug your computer into the internet somehow? A "wired" connection should work.

The NTFS utilities are actually several files that work together, which is what those "dependencies" are referring to.

You really need to use one of the methods I mentioned for this.  If you can somehow figure out a way to plug your laptop directly into the Internet, it should work.

Also, like the previous person said, I'm not sure if you are using an older version of Ubuntu, but you need to use a more recent version for this, like 10.04 or 10.10.

---

