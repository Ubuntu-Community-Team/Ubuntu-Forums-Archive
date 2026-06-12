---
title: "Cannot drag &amp; drop. Permission issue????"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by suomalainen on 2010-03-13
Ubunteros,

As you can see from the attached pic. I was trying to drag and drop a file (in order to copy it to another location) and I received the error message that I don't have permission to handle it.

Can someone tell me what I must do????

As a side note. MY Ubuntu 8.04LTS will not boot up, so I'm using a LIVE CD to look at my  Ubuntu drive and find the files I need to copy prior to re-installing ubuntu.

Anyway, I appreciate your help in telling me what I need to do to copy these files.

Thanks!!!

---

### Post by XubuRoxMySox on 2010-03-13
I'm using a different file manager, but I think you can change the "permissions" on any folder by opening it as root.

Try right-clicking on the folder you want access too and select "properties" and "permissions." To edit the permissions you'll be asked for the root password.

I like PCManFM for my file manager because it has a cool option where you click **Tools > Open Current Folder as Root**, enter your password and poof! Superuser mode.

-Robin

---

### Post by coffeecat on 2010-03-13
> **suomalainen said:**
> a LIVE CD

That's your problem. The files/folders you are trying to copy from your unbootable Ubuntu are owned by you, but only when you are booted into your hard drive installation and working in your account. The permission is determined by the UID (user identity number) which will probably be 1000. When in the live session you are user "ubuntu" with a different UID. So you need to invoke a root nautilus from the terminal with: 

```
gksudo nautilus
```But I see a **BIG** potential problem with your screenshot. It looks as though you are trying to drag and drop into ubuntu's home. This only exists in RAM. It will be lost when you power down. Use 'gksudo nautilus' to get to your HD home folder and then plug a USB drive in and drag and drop into that.

---

### Post by suomalainen on 2010-03-13
coffeecat,

Actually, not see in the pic I posted is another hard drive I was dropping into. Regardless, I used gksudo nautilus and navigated to the HDD where my files were and then tried to copy them into the other HDD and same error message popped up.

Am I doing something wrong???

Thanks for your support!

---

### Post by coffeecat on 2010-03-13
What is the "other HD" formatted to? If it's ext3/4 you are running into permissions problems again and will need to open another root nautilus to drop into. The trouble with this is that all the folders and files will end up being owned by root, and you'll have to chown them back when you restore after you reinstall.

If you are only copying personal data, videos, music, that sort of thing, it will be much easier to use a FAT32 or NTFS-formatted external drive. No permissions problems there. But I see you have unhidden the hidden files in your home folder which looks as though you are trying to copy all your settings. You are going to encounter problems whatever you do. Some of those hidden files have special permissions and these will be lost using root powers and drag and drop and/or FAT32/NTFS hard drive.

If you are trying to copy all your hidden folders/files, there is one way round that with "sudo cp -a" from the terminal. The a option preserves permissions and does a recursive copy. I can give you more details if you give more details.

What are you trying to copy?

What is the filesystem you are copying to?

---

### Post by suomalainen on 2010-03-13
coffeecat,

My version of Ubuntu 8.04 LTS 64 bit will not boot anymore. However, using live CD I can see the drive where my Ubuntu 8.04 files are. I can also see another HDD that I use solely for dumping data onto.

What I want to do is copy all the hidden files and folders like ".evolution" so that when I reinstall my 8.04 my email will be preserved and I will not have lost my emails.

As you can see in the attached pic, I'm doing just that using the gksudo nautilus command you taught to me but it is taking over 22 hours to copy. Is this normal??

I believe all drives are formatted to NTFS.

Do this info help?

---

### Post by coffeecat on 2010-03-13
OK that's clearer. By copying to NTFS, you'll be able to keep your personal data fine, but I don't understand why it's copying so slowly that it will take 22 hours to copy 1.6GB. 1.6GB should take only a couple of minutes.

Are you using the 8.04 live CD? NTFS support is OK in 8.04 but I can't remember how good it was. It's such a long time since I've used 8.04 that I can't remember if file transfers and writes to NTFS were slower than in later version of Ubuntu. Did you do copies to NTFS from the hard disc 8.04? Was it slow then because, no, that's not normal for what I get in 9.10.

If I think of anything I'll post back. Perhaps someone else might have something to offer.

---

### Post by suomalainen on 2010-03-13
coffeecat,

How about the  "sudo cp -a" command you were going to teach me????

Right now I using the gksudo nautilus command to copy hidden files like .evolution from the Ubuntu HDD to the "data dump" HDD I have.

But now I'm unsure if this is correct based on the sudo cp -a command you were mentioning.

What to do?

Thankis

---

### Post by coffeecat on 2010-03-13
> **suomalainen said:**
> How about the  "sudo cp -a" command you were going to teach me????

Right now I using the gksudo nautilus command to copy hidden files like .evolution from the Ubuntu HDD to the "data dump" HDD I have.

But now I'm unsure if this is correct based on the sudo cp -a command you were mentioning.

Using a drag and drop to copy to a NTFS drive/partition is perfectly OK. The only problem is the low speed you're getting which, at the moment, I can't explain. The only things that won't get copied properly are a couple of hidden configuration files which have special permissions. This is because NTFS doesn't support Unix/Linux permissions.

The 'sudo cp -a' was if you were going to copy to a Linux filesystem such as ext3. At the time I posted that suggestion you hadn't revealed what the filesystem was that you were copying to, if you remember, and a copy from and to a Linux filesystem using two instances of root nautilus would have resulted in all your files being owned by root. Not a disaster, but an inconvenience to chown them back to your ownership.

For what it's worth the command would be:

```
sudo cp -av /media/mountpointA/home/yourusername /media/mountpointB/
```
Where mountpointA is the folder that the live CD has mounted your Ubuntu installation to and mountpointB is the folder where the external drive is mounted. You'll have to look in /media of the live filesystem to see what they are called. About the options: The main advantage of -a is that it preserves permissions, but only when copying to a Linux filesystem. But it also does a recursive copy so the command above will copy everything in your home folder. The -v option = verbose. That is, you get feedback in the terminal to get some idea of how quickly it's going.

It will certainly be quicker than a drag and drop, but whether you want to abort the nautilus copy and try that is up to you.

I don't have a Hardy live CD any more otherwise I was going to see how quickly it would copy to NTFS here. But I do have a (neglected) hard disc install on one partition of one of my machines. I'll boot that up soon and see what a NTFS write is like with that and post back.

---

### Post by coffeecat on 2010-03-13
Well, that didn't take long.

I booted into 8.04, attached an external USB NTFS drive and dragged and dropped a folder containing about 1500 files, total 1.2GB. It copied at 16MB/sec (over 1000 times faster than your copy) and took a minute or so.

So I open a root nautilus with 'gksudo nautilus' and did the same and it copied at 18MB/sec - even faster.

So there's nothing wrong with NTFS write in 8.04. I can't explain that slow copy except....

How much RAM have you? The live CD uses much more RAM than a hard disc installation, and if you have less than 512MB you may be short on memory and that could possibly explain a slow copy.

---

### Post by suomalainen on 2010-03-13
CoffeeCat,

Thanks for your continued support thus far!!!! I got 8 GB of RAM....

Now I noticed an error in my reporting to You. My data dump drive is indeed NTFS. But my Ubuntu is installed on a  ext3 file system. Does this now cause any problems. I apologige for the incorrect information I reported.

Thank you.

P.S. Once the .evolution folder has been copied over from the ext3 filesystem to the NTFS file system and once I have re-installed Ubuntu 8.04 , will I be able to simply copy back over the file .evolution to my home folder and everything will resume as usually? Or do I need to configure Evolution first?

Thanks!

---

### Post by suomalainen on 2010-03-13
In addition to above I also have this question:

As mentioned earlier I have a secondary "Dump drive" where all my data goes. I have changed the pictues of the folders within this drive from Folders to various jpeg and gif images I have. Thus, when this drive is open I can see pictures representing folders instead of a boring looking folder by itself.

With Live CD open, when I go to this drive, just like when I had Ubuntu installed, I only see the plain folders and not the pictures? Why is this?

Also, how can I save the nvidia display settings for my dual displays?

Thanks again.

---

### Post by coffeecat on 2010-03-13
> **suomalainen said:**
> I got 8 GB of RAM....

That's - um - plenty! :)

> **suomalainen said:**
> Now I noticed an error in my reporting to You. My data dump drive is indeed NTFS. But my Ubuntu is installed on a  ext3 file system. Does this now cause any problems. I apologige for the incorrect information I reported.

Don't apologise. I'd assumed your Ubuntu was on an ext3 filesystem. That was the default for 8.04. So you're doing the right thing: using a root nautilus to read the ext3 partition to get over permissions issues and using an ordinary nautilus to write into a NTFS partition.

> **suomalainen said:**
> P.S. Once the .evolution folder has been copied over from the ext3 filesystem to the NTFS file system and once I have re-installed Ubuntu 8.04 , will I be able to simply copy back over the file .evolution to my home folder and everything will resume as usually? Or do I need to configure Evolution first?

You might want to post a separate support question for that, but certainly all your mail, your address book and other stuff are in there, so if you copy .evolution into your new home folder, it should work. If there is a skeleton .evolution folder there in a fresh install it will just get overwritten by your one. Keep a backup though and backup the .evolution folder that comes with a default install - just in case!

> **suomalainen said:**
> As mentioned earlier I have a secondary "Dump drive" where all my data goes. I have changed the pictues of the folders within this drive from Folders to various jpeg and gif images I have. Thus, when this drive is open I can see pictures representing folders instead of a boring looking folder by itself.

With Live CD open, when I go to this drive, just like when I had Ubuntu installed, I only see the plain folders and not the pictures? Why is this?

I'm not sure how you did this. Perhaps the images and settings are in hidden files in your home folder, not in the actual folders that appear as images. I've only ever personalised folders with the inbuilt 'emblems' under properties so I can't really answer this. 

> **suomalainen said:**
>  Also, how can I save the nvidia display settings for my dual displays?

I should imagine these are in /etc/X11/xorg.conf. While you have a root nautilus open, copy this file over to your backup disc - you need a root nautilus because this is a system file owned by root. Once you have reinstalled, you must reinstall the proprietary nvidia driver before you edit your new /etc/X11/xorg.conf. Then you can edit the new xorg.conf with the settings you have in the old. Or possibly overwrite the new xorg.conf with your backed-up copy - but keep a copy of the fresh xorg.conf first just in case.

You might want to start a support thread before you commit yourself. Install the nvidia driver and start a thread explaining what you want and post the contents of the two xorg.conf files. That way, if there is something I haven't anticipated, this will (hopefully) be picked up.

---

