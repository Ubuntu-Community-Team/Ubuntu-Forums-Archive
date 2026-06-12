---
title: "help with cd rom drive"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by jrotten10 on 2009-12-29
HEY;
Quick question....seems that my Movie PLayer has up and quit on me, wont play dvd when inserted.....any suggestions??

Also since this a noob site...what does it mean to mount or unmount a drive??

---

### Post by jrotten10 on 2009-12-29
Hey

Don't mean to waste anyones time here, but it seems that my cd rom is not connected with my media player(movie player) hopw can i fix??  have already checked to ensure my prefs all ok and movie player is the selected program....am having trouble getting around to try and fix this.....should i uninstall, or maybe you know of a better program......the problem seems to have started when i tried to rip a dvd...Thanks

JR

---

### Post by Buuntu on 2009-12-30
Install VLC, it's great for any kind of video.  To install it all you have to do is type this into a terminal (Applications > Accessories > Terminal):
```
sudo apt-get install vlc
```

Mounting is what needs to be done to make things accessible to your filesystem.  For example, when you insert a CD Ubuntu will automatically mount it to /media/cdrom to make it accessible to you.  When you unmount it is no longer accessible in your filesystem, and therefore have no way of accessing other than remounting it (it will still be there as a device file in /dev/, just not in a way that you can read or write to it).  For a more thorough explanation you can read here: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by dineshs on 2009-12-30
I am not an expert,But I think SMplayer can help

---

### Post by 3rdalbum on 2009-12-30
> **jrotten10 said:**
> HEY;
Quick question....seems that my Movie PLayer has up and quit on me, wont play dvd when inserted.....any suggestions??

I echo the suggestion to use VLC for all DVDs.

But you should know that many commercial DVDs are encrypted as a form of copy prevention. The encryption is very weak but it's still illegal in America to write software to decrypt DVDs - unless you have bought a license from the proper company. As Ubuntu is free, obviously there's no included license.

If you are running 32-bit Ubuntu, you can buy PowerDVD from the Ubuntu store ([http://shop.ubuntu.com](http://shop.ubuntu.com)) which is perfectly legal. If you're using 64-bit or you don't want to buy this software, you can enable the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org)) and install the "libdvdcss2" package. This adds probably-not-legal-in-the-US DVD decryption support to Ubuntu so you can play your encrypted discs.

---

### Post by jrotten10 on 2010-01-04
[B]Hey there;
it says there is help for all here, even noobs, I asked five days ago why my cd rom won't read my dvds anymore, I had tried to copy a dvd and now every time I put a movie in Movie Player says it can't read...pls help me fix this

thanks

just trying to learn karmic

jr
[/B]

---

### Post by cariboo on 2010-01-04
Please don't create multiple threads on the same subject. I have merged your three threads.

You need to do some basic trouble shooting, before we can help with your problem. Open an Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n10
```

just after you have inserted a cd in the drive. Paste the output in your next post.

---

