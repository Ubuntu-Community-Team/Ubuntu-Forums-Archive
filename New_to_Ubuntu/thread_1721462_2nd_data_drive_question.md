---
title: "2nd data drive question"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by Woodogg18 on 2011-04-04
So this may be a dumb question but I'm extremely new to ubuntu, so bear with my ignorance. I will be getting a 2TB internal drive to act as a data drive to store all my music, videos, etc. I have my computer set up to dual boot vista and ubuntu. Now will I be able to access this drive from both OSs?  I assume I will as I access my externals from both, I'm just worried about having to configure a bunch of stuff to do it as I'm still learning Linux and how it works. Like I said, probably a dumb question with a simple answer, I just want to make sure I know what I have to do when I install it (if anything)

---

### Post by Enigmapond on 2011-04-04
Because you have a dual boot and want to share it between the 2 OS's. Then make sure it's formatted NTFS. Windows won't see it if it's ext3 or ext4.

---

### Post by Woodogg18 on 2011-04-04
I planned on NTFS. So I just plug it in (sata 3), format, and it should work just fine?

---

### Post by rosencrantz on 2011-04-04
It's quite easy - you should be able to set up your hard drive configuration before installing. Make sure you disable formatting if the drive is already NTFS and set any mountpoint like /media/data or /windows/...
If you didn't set it  during install, you can add a line to your /etc/fstab file - here's a quote from my automatic setup:
UUID=<my UUID> /windows/D  ntfs-3g defaults,locale=de_DE.UTF-8 0 0
Note that you need admin rights, so edit with sudo nano or sudo gedit.
Replace de_DE by en_US or whatever country/character set you work with. You can detect your drive's UUID with 
sudo blkid
If you haven't set a label, it's probably the UUID of the device /dev/sdb1 for a primary or /dev/sdb5 for an extended partition.

Cheers,
rosencrantz

---

### Post by wolfen69 on 2011-04-04
> **rosencrantz said:**
> It's quite easy - you should be able to set up your hard drive configuration before installing. Make sure you disable formatting if the drive is already NTFS and set any mountpoint like /media/data or /windows/...
If you didn't set it  during install, you can add a line to your /etc/fstab file - here's a quote from my automatic setup:
UUID=<my UUID> /windows/D  ntfs-3g defaults,locale=de_DE.UTF-8 0 0
Note that you need admin rights, so edit with sudo nano or sudo gedit.
Replace de_DE by en_US or whatever country/character set you work with. You can detect your drive's UUID with 
sudo blkid
If you haven't set a label, it's probably the UUID of the device /dev/sdb1 for a primary or /dev/sdb5 for an extended partition.

Cheers,
rosencrantz
No need for all of that, especially for a noob. Ubuntu will see the drive automatically. Just go to Places and you will see it.

---

### Post by rosencrantz on 2011-04-04
Yeah, right, that was where my inner SuSE user took over. Still, it's always good to know your /etc/fstab ;-)

---

### Post by Woodogg18 on 2011-04-04
> **rosencrantz said:**
> It's quite easy - you should be able to set up your hard drive configuration before installing. Make sure you disable formatting if the drive is already NTFS and set any mountpoint like /media/data or /windows/...
If you didn't set it  during install, you can add a line to your /etc/fstab file - here's a quote from my automatic setup:
UUID=<my UUID> /windows/D  ntfs-3g defaults,locale=de_DE.UTF-8 0 0
Note that you need admin rights, so edit with sudo nano or sudo gedit.
Replace de_DE by en_US or whatever country/character set you work with. You can detect your drive's UUID with 
sudo blkid
If you haven't set a label, it's probably the UUID of the device /dev/sdb1 for a primary or /dev/sdb5 for an extended partition.

Cheers,
rosencrantz

Yeah, you see, um , that might as well be Klingon your speaking there to me, I have no idea what all that was about. Lol. And I already installed and got everything going so a "plug and play" option was what I was hoping for. Thanks anyway though. And thanks to wolf.

---

### Post by Dutch70 on 2011-04-04
Not to worry Woodogg18, you will learn to speak Klingon, and you will start to look like this ... :idea: ...lol j/k

I agree with wolfen for now, but later, you will probably want to automount your ntfs disk. It's much, much easier than you might think.
When you get comfortable, you'll have this thread to come back to. 
So this link may come in handy...
[[COLOR="RoyalBlue"]HTG Explains: What is the Linux fstab and How Does It Work?[/COLOR]]("http://www.howtogeek.com/howto/38125/htg-explains-what-is-the-linux-fstab-and-how-does-it-work/")

For example, I just had to add the highlighted part of the pic, to get my ntfs partition to automount when I login.

---

