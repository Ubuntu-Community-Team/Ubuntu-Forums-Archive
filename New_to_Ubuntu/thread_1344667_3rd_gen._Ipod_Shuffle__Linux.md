---
title: "3rd gen. Ipod Shuffle / Linux"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by cjnkns on 2009-12-03
I was hoping someone here could help me out getting my ipod shuffle to work on Ubuntu.

When I plug it in the light just blinks and the device does not appear in Rythmbox or Banshee. I have an ipod classic that works fine but I just can't get the shuffle to work.


Any help is appreciated! 

Thanks.

---

### Post by yeats on 2009-12-03
Have you seen this?:

[http://www.ipodlinux.org/wiki/Generations](http://www.ipodlinux.org/wiki/Generations)

---

### Post by ukripper on 2009-12-03
you can try gtkpod - [http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/)

---

### Post by speedwell68 on 2009-12-03
I have 2nd generation Shuffle and I use it in conjunction with Songbird with it's iPod support plugin.  It works very well.  You can get the latest DEB for Songbird here...

[http://www.getdeb.net/updates/?q=songbird](http://www.getdeb.net/updates/?q=songbird)

---

### Post by cjnkns on 2009-12-03
Thanks I'll try working through your suggestions! Thank you for the help.

---

### Post by cjnkns on 2009-12-05
> Have you seen this?:

[http://www.ipodlinux.org/wiki/Generations](http://www.ipodlinux.org/wiki/Generations)

It states that the 3rd generation will not be supported!? Why in the world would it not be?

If linux expects its user base to grow not supporting an ipod is really not an option... imho

---

### Post by ukripper on 2009-12-05
> **cjnkns said:**
> It states that the 3rd generation will not be supported!? Why in the world would it not be?

If linux expects its user base to grow not supporting an ipod is really not an option... imho

ipod is not and will not be stopping linux to grow. Apple is stopping themselves to grow within linux community, it is their choice.

Not everyone is fond of ipod in here anyway.

---

### Post by Norm24 on 2009-12-05
> **ukripper said:**
> ipod is not and will not be stopping linux to grow. Apple is stopping themselves to grow within linux community, it is their choice.

Not everyone is fond of ipod in here anyway.

Agreed.

I'll stick with my Sandisk Fuze.

---

### Post by cjnkns on 2009-12-05
> ipod is not and will not be stopping linux to grow. Apple is stopping themselves to grow within linux community, it is their choice.

Not everyone is fond of ipod in here anyway.

I understand your point. But apple ipod like it or not is by far the most popular mp3 devices. You would think that with the majority of people using them - there would be more of an effort to support them on linux.

---

### Post by meganox on 2009-12-27
You seem to be missing the point, Apple are making it incredibly difficult if not impossible for Linux to run on the iPod.  When Linux users are faced with a hardware vendor as hostile to the principles of openness that allow open source software to exist as Apple is, they are not going to waste their time trying to support those products, they will simply go elsewhere.

The upshot is, if you think the iPod is such a great product, you should buy a Mac or PC to use with it; if you think Linux is a great product, you should steer clear of vendors like Apple.

It's not Linux's fault.

[http://en.wikipedia.org/wiki/Vendor_lock_in#Apple_Inc](http://en.wikipedia.org/wiki/Vendor_lock_in#Apple_Inc).

I should also point out that iPodLinux is a Linux distribution that runs on the iPod, it has nothing to do with being able to manage tracks on your iPod on a Linux based system.

---

### Post by Felix-the-Cat on 2010-02-06
I recently plugged in my new Ipod shuffle expecting it to run easily by copy pasting files simply using Rhythm box. How naive I was. After trying Rhythmbox and GTKpod with my 3gen shuffle and having no success I tried gnupod-tools from the repos (I'm running Karmic btw). I then realized that gnupod-tools 0.99.7 is broken and thus you need to get gnupod-tools 0.99.8 and have fun with make, which I did. Buuuut the 3gen shuffle database format has apparently changed and therefore even gnupod-tools 0.99.8 doesn't work as neither does anything else on Linux for the shuffle...yet. There are active efforts to reverse engineer the database. Discussion and development can be found here:

[http://www.mail-archive.com/bug-gnupod@gnu.org/msg00013.html]("http://www.mail-archive.com/bug-gnupod@gnu.org/msg00013.html")
[http://shuffle3db.wikispaces.com/iTunesSD3gen]("http://shuffle3db.wikispaces.com/iTunesSD3gen")

Hope this helps.
A lot of people aren't willing to go the extra mile to get something to work which is one thing holding Linux back, the most computer savvy people don't hold the biggest chunk of the consumer market so as long as we can contribute to such efforts above to make things work out of the box Liunx will only become better and better.

Now...until gnupod-tools or something supports the 3gen shuffle I'll spend my time trying to get Itunes working on wine or my Virtual Machines. Fun times. :)

---

### Post by Floola on 2010-03-14
Floola 5.5 now supports shuffle3G.

Visit [http://www.floola.com](http://www.floola.com)

---

### Post by ohmybuntu on 2010-05-09
yoopieh, thanks to you, floola and this thread, my shuffle 3G finally works under linux! I really appreciate your help.

---

### Post by GSF1200S on 2010-05-09
> **ohmybuntu said:**
> yoopieh, thanks to you, floola and this thread, my shuffle 3G finally works under linux! I really appreciate your help.

How? I have a 2GB ipod shuffle hooked up that I bought today and for the life of me I cant get it to work. I have tried gtkpod, rhythmbox, and floola 5.7, and nothing. It pops up in rhythmbox, and Xubuntu mounts it just fine, but everytime I try to use any of the programs to put music on the ipod, it just says "Please use itunes to sync music to this ipod."

I swear, I really hate Apple- they could make it easy to work with other programs. The only reason I bought it is because my mom wanted one and its mothers day.

---

### Post by ukripper on 2010-05-10
> **GSF1200S said:**
> 
I swear, I really hate Apple- they could make it easy to work with other programs. The only reason I bought it is because my mom wanted one and its mothers day.

Now that is sweet. Hope it works out for you.

---

### Post by velmont on 2010-10-23
This is just so stupid. I told my girlfriend 20 times she shouldn't buy anything from apple, but, well, she had that coupon which got her a shuffle 3g for free. However, now we've big problems activating it.

Nothing in Linux can activate the stupid machine.

So I need to find someone to do it for us. Anyway, once activated, I think it'll work in Rhythmbox. Just so incredible frustrating that you need to abide by Apple's North Korean regime in order to make it  work first.

Boycott Apple! :mad:

(this post: [http://ubuntuforums.org/showpost.php?p=9706489&postcount=6](http://ubuntuforums.org/showpost.php?p=9706489&postcount=6) says it'll work after activating in iTunes)

---

### Post by Felix-the-Cat on 2010-10-23
I have found the easiest way to use Apple products or Windows products when I absolutely HAVE to is to use a virtual machine and then pass through the host devices I need. When the crapware that is Apple messes up, I can just reset the machine easily to a snapshot taken before I installed the mess on that guest.

---

### Post by daveoily on 2011-05-31
> **velmont said:**
> 

(this post: [http://ubuntuforums.org/showpost.php?p=9706489&postcount=6](http://ubuntuforums.org/showpost.php?p=9706489&postcount=6) says it'll work after activating in iTunes)

Dead simple, totally worked for me, cheers!:D

---

