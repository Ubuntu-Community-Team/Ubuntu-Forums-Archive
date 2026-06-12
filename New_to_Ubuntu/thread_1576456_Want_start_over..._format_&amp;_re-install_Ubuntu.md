---
title: "Want start over... format &amp; re-install Ubuntu"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-09-17
Hello:

I would like to completely un-install Ubuntu, format my entire disk and then re-install Ubuntu.

How would I do this?

Thanks,

---

### Post by abs_kkk on 2010-09-17
[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)
and install normally

---

### Post by Elfy on 2010-09-17
Boot the livecd or whatever you are using.

When you reach the partition stage - pick use the whole disk - it will format and remove all that was there.

---

### Post by Paul820 on 2010-09-17
If you are only using ubuntu, just put your disc in the drive and away you go. **Back up** any data you want to keep. I would suggest using a seperate '/' and 'home' partition then if you want to reinstall again you don't need to touch your home directory, all your settings will still be there for your programs.

---

### Post by macem29 on 2010-09-17
run the install again, choose use entire disk, old OS will be gone regardless of what it is

edit: I see that I type too slow :)

and isn't it funny how our "windows training" leads us to the conclusion that it's best to just chuck it all

---

### Post by Robert.Thompson on 2010-09-17
Thanks people!!! :)

---

### Post by Robert.Thompson on 2010-09-17
> **Paul820 said:**
> If you are only using ubuntu, just put your disc in the drive and away you go. **Back up** any data you want to keep. I would suggest using a seperate '/' and 'home' partition then if you want to reinstall again you don't need to touch your home directory, all your settings will still be there for your programs.

Hi Paul:

I would really like to install the way you suggest but I am not sure how to setup partitions during setup. Right now it shows:
/dev/sda
  /dev/sda1   ext4    153502 MB
  /dev/sda5   swap      6537 MB

How do I create '/' (root?) and 'home' and what size?

Thanks,

---

### Post by Paul820 on 2010-09-17
When it comes to the selecting partitions selection there is an option to select that allows you to define the sizes of each partition seperately. I see you have 153Gb or around that of hard disc space.

So click on sda1 and choose how much space you want for '/', you don't need much for that, i usually allow it around 15-20Gb, even that may be too much but i don't want to run out of space. There is a button called 'add' that you click and some options come up where you can select ext3 or ext4 or some others, click ext4 and then there is another option further down where you can select / or home or whatever. It's not hard to find.

When you choose how much space you want to give to '/', don't forget 1000 is 1Gb, so if you want 15Gb or 20Gb, you would type 15000 or 20000.

Then you finish selecting it by clicking ok or whatever (can't remember the buttons) and linux will resize the partion with some unallocated space where you can do the same as above, or leave it all for /home. Your swap is already there so you don't need to do anything for that.

Here we go, i have found a website that will explain it a bit better than i did: [http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/]("http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/")
Another better one: [http://www.psychocats.net/ubuntu/installseparatehome]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by Robert.Thompson on 2010-09-17
> **Paul820 said:**
> When it comes to the selecting partitions selection there is an option to select that allows you to define the sizes of each partition seperately. I see you have 153Gb or around that of hard disc space.

So click on sda1 and choose how much space you want for '/', you don't need much for that, i usually allow it around 15-20Gb, even that may be too much but i don't want to run out of space. There is a button called 'add' that you click and some options come up where you can select ext3 or ext4 or some others, click ext4 and then there is another option further down where you can select / or home or whatever. It's not hard to find.

When you choose how much space you want to give to '/', don't forget 1000 is 1Gb, so if you want 15Gb or 20Gb, you would type 15000 or 20000.

Then you finish selecting it by clicking ok or whatever (can't remember the buttons) and linux will resize the partion with some unallocated space where you can do the same as above, or leave it all for /home. Your swap is already there so you don't need to do anything for that.

Here we go, i have found a website that will explain it a bit better than i did: [http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/]("http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/")
Another better one: [http://www.psychocats.net/ubuntu/installseparatehome]("http://www.psychocats.net/ubuntu/installseparatehome")

Thanks Paul.

One question - when a new relase comes out, how do I install it to preserve my data?

---

### Post by Paqman on 2010-09-17
> **Robert.Thompson said:**
> 
One question - when a new relase comes out, how do I install it to preserve my data?

You can upgrade from one version to the next without reinstalling.

Alternatively, if you have a separate /home partition you can do a reinstall, and just pick the appropriate partition as /home again, and tell the system not to reformat it. Everything in your /home partition will be preserved.

---

### Post by Paul820 on 2010-09-17
> Thanks Paul.

One question - when a new relase comes out, how do I install it to preserve my data?

No problem, it's a bit hard trying to explain it to someone who hasn't done it before that's why i went and found those links for you. It makes it a bit easier when there is something a bit more visual to explain the steps.

As Paqman said, when you reinstall just select the root partition and select to format it and select your home partition but don't format it. Ubuntu will not touch your home then. It sure does save a lot of headaches if Ubuntu does get damaged somehow and all your data is wiped out. ;)

---

### Post by Robert.Thompson on 2010-09-17
Thanks to all! :)

Ubuntu is now re-installed, updated and operating like a charm.

---

### Post by macem29 on 2010-09-17
this is a great example of how a tech forum should work, congrats on the system recovery

---

