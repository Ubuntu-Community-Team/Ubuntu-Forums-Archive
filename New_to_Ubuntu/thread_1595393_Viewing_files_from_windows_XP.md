---
title: "Viewing files from windows XP?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by AxisGundam on 2010-10-13
Hi , guys. I've had a problem with my windows XP yesterday(something to do with 'mup.sys')and it refused to boot up which is why I decided to switch over to Ubuntu.I have considered using Ubuntu for quite sometime now but , I wish to keep the anime and music I have spent so many time downloading.

Would the Ubuntu 10.10 installation overwrite my existing OS and all the files I have?
I am currently on a live USB setup on a Acer Aspire One netbook and can't seem to find my files on windows xp. 
Would I be able to view files(.mkv/.mp3/.flac) I've had on my previous OS installation after I've installed Ubuntu 10.10?
If so , how? 
I tried mounting on this live setup and it failed , is this an issue with live setups or will I be unable to view my files? :(

---

### Post by kaldor on 2010-10-13
**Yes**, it will overwrite XP and all your files if you are not careful.

Take a look at this:

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)



Bit outdated, but should still apply fine.

Edit (Forgot the rest of your posts :) ):

Ubuntu can play .mp3 and .flac just fine. You'll need to install a package once Ubuntu is installed which will let you use Flashplayer, media codecs, java, and the like.

I've never used .mkv before, but upon a Google search it seems there shouldn't ba a problem.


The Aspire One netbook has a decent Linux track record.

Take a look at this:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Good luck :)

---

### Post by AxisGundam on 2010-10-13
> **kaldor said:**
> **Yes**, it will overwrite XP and all your files if you are not careful.

Take a look at this:

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)



Bit outdated, but should still apply fine.

Edit (Forgot the rest of your posts :) ):

Ubuntu can play .mp3 and .flac just fine. You'll need to install a package once Ubuntu is installed which will let you use Flashplayer, media codecs, java, and the like.

I've never used .mkv before, but upon a Google search it seems there shouldn't ba a problem.


The Aspire One netbook has a decent Linux track record.

Take a look at this:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Good luck :)
Thing is , my netbook does not have a cd drive. And I do not see the application / places / system menu on my live usb setup.

---

### Post by AxisGundam on 2010-10-13
IS there any way I can create a partition and install ubuntu 10.10 along side my existing OS(I assume this would allow me to view my files in Ubuntu) using the live usb setup?
I am not able to boot into windows xp.

---

### Post by TNT1 on 2010-10-13
> **AxisGundam said:**
> IS there any way I can create a partition and install ubuntu 10.10 along side my existing OS(I assume this would allow me to view my files in Ubuntu) using the live usb setup?
I am not able to boot into windows xp.

During the install process, Ubuntu will identify the windows OS and present you with the option to install side by side and choose between the OS's at startup.

But you should still be able to see your windows files from the live usb.

---

### Post by AxisGundam on 2010-10-13
> **TNT1 said:**
> During the install process, Ubuntu will identify the windows OS and present you with the option to install side by side and choose between the OS's at startup.

But you should still be able to see your windows files from the live usb.
When does this happen?
I definitely do not want to lose my files if the installation fails to detect it...
Are there any screenshots/videos showing the installation sequence of Ubuntu 10.10?

Edit: I am unable to view the files , how do I go about showing them?
Mounting has failed.

---

### Post by TNT1 on 2010-10-13
> **AxisGundam said:**
> When does this happen?
I definitely do not want to lose my files if the installation fails to detect it...
Are there any screenshots/videos showing the installation sequence of Ubuntu 10.10?

Edit: I am unable to view the files , how do I go about showing them?
Mounting has failed.

Running in live USB, you should see the windows files, and you can back them up from there. go to main menu, and look in places/computer you should see the windows file system listed.

---

### Post by AxisGundam on 2010-10-13
Main menu?
Where is that?

---

### Post by mastablasta on 2010-10-13
places - on the upper bar.

---

### Post by TNT1 on 2010-10-13
> **AxisGundam said:**
> Main menu?
Where is that?

Top right of your screen... the little ubuntu logo? you should also have a "places" button as well...

Have a look here:
[http://www.liberiangeek.net/2010/09/perfect-desktop-ubuntu-10-10-maverick-meerkat-installation-screenshot/](http://www.liberiangeek.net/2010/09/perfect-desktop-ubuntu-10-10-maverick-meerkat-installation-screenshot/)

---

### Post by kaldor on 2010-10-13
Ahh, I was assuming you were using the Desktop edition. I assume you're using the netbook edition (Aspire One :) )?

If so, I'd probably just recommend you get the Desktop edition. But, in the meantime...


Yes, you can partition the hard drive and install both OSes side by side. BUT, since you have no backups, I tried to avoid that step; it's likely to go fine, but when important data is involved it's best to leave it alone.

For the install sequence, it's verrry straightforward. The install errors are more likely to be technical than related to a mistake on your end (from my experience).

But I don't know why you couldn't view files... just bring up the file browser (not sure where that is on the new netbook UI) and browse to the locations shown in my original link.

---

### Post by AxisGundam on 2010-10-13
> **TNT1 said:**
> Top right of your screen... the little ubuntu logo? you should also have a "places" button as well...

Have a look here:
[http://www.liberiangeek.net/2010/09/perfect-desktop-ubuntu-10-10-maverick-meerkat-installation-screenshot/](http://www.liberiangeek.net/2010/09/perfect-desktop-ubuntu-10-10-maverick-meerkat-installation-screenshot/)
I did not see them just now , I will attttttempt to rerun the usb live setup.

---

### Post by petronell on 2010-10-13
I ditched Windows about three years ago now. Ubuntu will do everything you want, I now don't even use Wine for my needs.

For your mkv files they will play using vlc.

---

### Post by petronell on 2010-10-13
And the places menu is on the top left of the screen. Can you confirm which flavour you are using?

If you have the netbook edition, can you confirm whether it is 10.04 or 10.10 as their interfaces are different.

---

### Post by AxisGundam on 2010-10-13
> **kaldor said:**
> Ahh, I was assuming you were using the Desktop edition. I assume you're using the netbook edition (Aspire One :) )?

If so, I'd probably just recommend you get the Desktop edition. But, in the meantime...


Yes, you can partition the hard drive and install both OSes side by side. BUT, since you have no backups, I tried to avoid that step; it's likely to go fine, but when important data is involved it's best to leave it alone.

For the install sequence, it's verrry straightforward. The install errors are more likely to be technical than related to a mistake on your end (from my experience).

But I don't know why you couldn't view files... just bring up the file browser (not sure where that is on the new netbook UI) and browse to the locations shown in my original link.
Is there any reason you are recommending that?
I am led to believe the netbook version is optimised for smaller displays and has drivers for most of the netbooks.

@petronell I am running Ubuntu 10.10,

---

### Post by TNT1 on 2010-10-13
> **AxisGundam said:**
> Is there any reason you are recommending that?
I am led to believe the netbook version is optimised for smaller displays and has drivers for most of the netbooks.

@petronell I am running Ubuntu 10.10,

The general consensus is that desktop edition is better for for the aspire one.

---

### Post by petronell on 2010-10-13
OK, I have a 10.10 netbook beside me.

Boot up using your live CD and choose try ubuntu. Once you come up to the home screen you should see a number of icons down the left hand side of the screen. Click on the third from bottom which looks like a grey folder.

You should see your windows xp partition in there.

I suggest backing up to usb disk before doing anything else.

---

### Post by petronell on 2010-10-13
I agree the desktop edition will make it easier to rescue your files, once we have done that, then you can choose if you would rather use the netbook remix.

---

### Post by AxisGundam on 2010-10-13
> **petronell said:**
> OK, I have a 10.10 netbook beside me.

Boot up using your live CD and choose try ubuntu. Once you come up to the home screen you should see a number of icons down the left hand side of the screen. Click on the third from bottom which looks like a grey folder.

You should see your windows xp partition in there.

I suggest backing up to usb disk before doing anything else.
That would be 'Files and Folders' , yes?
The only things I see are items in the 'Favourite folders' which would be documents , music , pictures , videos and downloads.
And none of these folders contains items from my xp partion.


Btw , my live usb setup takes a long time to boot , is this normal? ( 20minutes - 1 hr)

---

### Post by petronell on 2010-10-13
Seems quite a long time to me, right click on one of the favourite folders, doesn't matter which. It will then open it and say nothing in the folder.

In the top right of the window is a small grey folder icon, click on that and you are into a more normal window manager type application.

Then on the left hand side you should see your xp partition in the top half of the folders?

---

### Post by AxisGundam on 2010-10-13
> **petronell said:**
> Seems quite a long time to me, right click on one of the favourite folders, doesn't matter which. It will then open it and say nothing in the folder.

In the top right of the window is a small grey folder icon, click on that and you are into a more normal window manager type application.

Then on the left hand side you should see your xp partition in the top half of the folders?
Well , I see 'Acer' which may either be the recovery partition or my xp partion.
There is nothing in it. ( Perhaps that's because it's not mounted?)
I have tried to mount that and got this error message

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by petronell on 2010-10-13
OK you have issues on the hard disk, chkdsk /f will fix those issues. 

Have you got your windows xp cd there?

Can you boot it up using that and then when you are in the blue dos part of setup choose the recover/fix option. NOT THE RE-INSTALL.

That should get you to a dos prompt where by you can execute the chkdsk command.

May be worth considering purchasing a new HDD as well - how old is it?

---

### Post by AxisGundam on 2010-10-13
> **petronell said:**
> OK you have issues on the hard disk, chkdsk /f will fix those issues. 

Have you got your windows xp cd there?

Can you boot it up using that and then when you are in the blue dos part of setup choose the recover/fix option. NOT THE RE-INSTALL.

That should get you to a dos prompt where by you can execute the chkdsk command.

May be worth considering purchasing a new HDD as well - how old is it?

I would say about 6 months old , it shouldn't have such a short lifespan.
The Aspire One does not come with a windows xp cd / recovery cd.
And it does not have a cd drive.
The only way I can recovery my OS is via a recovery program , which of course is impossible since I am able to boot in my xp.

---

### Post by mikechant on 2010-10-13
The problem is probably that your windows partitions were not unmounted cleanly when you had your XP problem. Ubuntu won't mount them in this case.
The normal recommendation is to boot into windows, let it do a chkdsk (probably automatic on startup) and shut down cleanly.

But this doesn't sound like an option in your case, and I guess you don't have an external cd/dvd drive to run a windows recovery disc from?
(EDIT: Extra posts added while I was typing, I see you definitely don't have a recovery cd)

However, it appears that if you have another PC available you can make an equivalent of the windows recovery disc on a USB stick:
[http://blog.emptycrate.com/node/386](http://blog.emptycrate.com/node/386)
As you don't have a recovery disc it looks like you need to do this on another PC running XP, then you can get the necessary files to make the USB image from the hard drive.

If you can get this work you can run the windows recovery console on the netbook and do a chkdsk from there. Once you've done that, 'live' ubuntu should be able to see/mount/access the windows partitions.

There is an 'ntfsfix' utility for ubuntu but although it fixes some ntfs errors, it still needs a windows chkdsk afterwards.

---

### Post by AxisGundam on 2010-10-13
> **mikechant said:**
> The problem is probably that your windows partitions were not unmounted cleanly when you had your XP problem. Ubuntu won't mount them in this case.
The normal recommendation is to boot into windows, let it do a chkdsk (probably automatic on startup) and shut down cleanly.

But this doesn't sound like an option in your case, and I guess you don't have an external cd/dvd drive to run a windows recovery disc from?

However, it appears that if you have another PC available you can make an equivalent of the windows recovery disc on a USB stick:
[http://blog.emptycrate.com/node/386](http://blog.emptycrate.com/node/386)
As you don't have a recovery disc it looks like you need to do this on another PC running XP, then you can get the necessary files to make the USB image from the hard drive.

If you can get this work you can run the windows recovery console on the netbook and do a chkdsk from there. Once you've done that, 'live' ubuntu should be able to see/mount/access the windows partitions.

There is an 'ntfsfix' utility for ubuntu but although it fixes some ntfs errors, it still needs a windows chkdsk afterwards.
Yes , I do have another PC.
I will try this tomorrow.
Thanks everyone for your swift replies ^_^

---

