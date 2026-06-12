---
title: "beginner in encryption"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-23
id like to encrypt my file system and generally my os.
not having a lot of experience  i cant do/say much about it.

so what steps should i follow? 

i dont mind reinstalling in order to make some non-default option available and the procedure more simple

---

### Post by jerome1232 on 2009-07-23
Use the alternate install cd it can setup encrypted lvm for you.

---

### Post by unutbu on 2009-07-23
Here is a nice guide for setting up a LUKS-encrypted installation:
[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

---

### Post by Locke_99GS on 2009-07-23
dm-crypt, TrueCrypt, Loop-AES are capable of excrypting a file system at the block level.

ecryptfs can stack on top of most filesystems, but can't excrypt entire volumes.

---

### Post by heyyy on 2009-07-23
will this make my system slower?
also any guides without having to reinstall?

---

### Post by heyyy on 2009-07-23
also will this affect upgrades?

---

### Post by heyyy on 2009-07-23
> **jerome1232 said:**
> Use the alternate install cd it can setup encrypted lvm for you.

from where can i get this cd?

---

### Post by unutbu on 2009-07-23
You can download the Alternate CD iso from here:
[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)
> 
Will this make my system slower?
I suppose if one were to try to benchmark it, there would be some delay, 
but in everyday usage I do not find it noticable. 
> 
any guides without having to reinstall?
No, you must reinstall.
> 
also will this affect upgrades?
I have read that there is no problem doing upgrades (of the distribution), 
but since upgrades do not always go through perfectly, I'd recommend having backups of your data before attempting this.

---

### Post by heyyy on 2009-07-23
also will i have all the options and apps already installed with the alternative cd?

---

### Post by unutbu on 2009-07-23
When you boot the Alternate CD, you will be greeted by text-based installer.
(See the pictures in [http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)).

Once the Alternate installer is finished, you should be able to boot Ubuntu as usual -- except that you will be asked to type in a password early on in the boot process.

Once you do that the boot proceeds and you should get to the usual GDM login window.
At this point, you should find all the standard apps, just like a regular Ubuntu install.

---

### Post by heyyy on 2009-07-23
thanks
will the suspend-hybernation functions have any problem?

---

### Post by heyyy on 2009-07-23
would it be nice the developers to add this feature to the main cd asking if we want encryption?

---

### Post by unutbu on 2009-07-23
> will the suspend-hybernation functions have any problem?

Good question. I haven't been able to get suspend/hibernation to work while using LUKS.
I think you lose these features when you use LUKS.
Or maybe there is a way, but I don't know how to do it.

---

### Post by heyyy on 2009-07-23
> **unutbu said:**
> Good question. I haven't been able to get suspend/hibernation to work while using LUKS.
I think you lose these features when you use LUKS.
Or maybe there is a way, but I don't know how to do it.

what is LUKS?

---

### Post by unutbu on 2009-07-23
[http://en.wikipedia.org/wiki/Linux_Unified_Key_Setup](http://en.wikipedia.org/wiki/Linux_Unified_Key_Setup)
This is one way to do whole-disk encryption. LUKS as implemented by the Alternate installer uses dm-crypt. I think Locke_99GS mentioned a few other ways. [http://ubuntuforums.org/showpost.php?p=7666238&postcount=4](http://ubuntuforums.org/showpost.php?p=7666238&postcount=4)

---

### Post by heyyy on 2009-07-23
i suppose with the alternative cd im covered,right?
i also suppose i could follow the steps on the cd with no problem... i mean i dont need to have really big technical knowledge in order to set it up?

---

### Post by unutbu on 2009-07-23
I recommend reading this guide ([http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)) from beginning to end before you actually install.

If you have any questions, you can post them here.

---

### Post by heyyy on 2009-07-23
since i only have a laptop and only one drive wouldnt be simplier to choose 
"Guided - use entire disk and encrypted LVM"  ...?

---

### Post by jerome1232 on 2009-07-23
That's what I would do, However if you are going to use encryption and lvm, I would make it a priority to learn how to mount these types of partitions from an Ubuntu live cd.

Just because it sucks to begin learning about lvm and encryption when your computer is having other problems and you can't even figure out how to get at your files.

---

### Post by heyyy on 2009-07-23
any site that describes all the steps in the "automated" steps?

---

