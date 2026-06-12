---
title: "Please Help"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by PleaseHelp2 on 2009-01-02
I have searched and gotten most of the info that I require but am still having problems.  

Brief story to hopefully keep the "don't be lazy, learn how to use it" posts out, I was given a new Dell computer for Christmas which had ubuntu installed on it.  I have never used Lynux anything in my life and I am a hardworking single father of two who only has very basic computer knowledge... I don't have the time or energy to learn about using Lynux.  Dell has a 21 day system exchange but by the time I opened the box on Christmas it was already past the 21 days after purchase.

I am trying to install Windows Vista simply because I know how to use Windows.  Through searching I have determined that I have to seperate and format a portion of my hard drive in order to be able to install and use Windows, which is fine...  I can handle that.  My problem is that I can't get to the partition editor.

When I boot off of my Live disk, I click on the first option (use ubuntu without changing anything), it looks like it starts to load then goes to a black screen and shows:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

(initramfs)

then after a few seconds it comes up

Revalidation failed (errno=-5)

If anyone can help I would be most appriciative... if any of your suggestions involve "download this ad do this that and the other", please keep in mind that I don't know how to use Lynux at all :(  

Thanks in advance!

---

### Post by lykwydchykyn on 2009-01-02
- Just for the record, it's "Linux", with an "i".  Written by a guy named Linus, hence the name.

 - Are you wanting to end up with a situation where you dual boot between Ubuntu and Vista, or are you intending to trash Ubuntu entirely and only use Vista?  If your intention is the latter, you shouldn't have to repartition anything, I'm sure Vista's installer would be happy to wipe out anything that might be on the disk at this point.

 - Is this an actual desktop computer or some kind of netbook (a.k.a. sub-notebook, mini-9/12 etc).  Are you sure it has the specs to run Vista?

 - Are you using the live CD that came with your system, or did you download one from the internet?  Because it sounds like your CD is either defective, or not liking your system.

---

### Post by PleaseHelp2 on 2009-01-02
Sorry for the spelling error.

The computer is a desktop...  a Dell Inspiron 530.  Vista Basic (which is what I am trying to install) normally comes standard on the computer I recieved so I'm sure it has the specs for it.

I would like to end up with Vista only but not really sure how to accomplish that.  Just installing Vista on what I currently have would be fine if it is easier.

I'm using the disk that came with the computer.

Hope this helps

---

### Post by adult swim on 2009-01-02
you should be able to put the vista cd in the computer and restart it.  when the bios comes up, it should say something like dell, hit the f12 key to bring up the boot menu.  when that pops up, select cd/dvd and then hit enter.  that should get you to where you install vista

---

### Post by PleaseHelp2 on 2009-01-02
I have already booted from the Vista DVD.  When trying to install it says:

Windows cannot be installed to this hard disk space.  Windows must be installed to a partition formatted as NTFS.

It says this about every shown partition which is why I was trying to get to the partition editor.

---

### Post by hyper_ch on 2009-01-02
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by adult swim on 2009-01-02
do you have an ubuntu live cd?

---

### Post by PleaseHelp2 on 2009-01-02
Ubuntu 8.04 LTS DVD, came with the system.

It is when I use this DVD that I click on the first option (use ubuntu without changing anything), it looks like it starts to load then goes to a black screen and shows:
```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

(initramfs)

Revalidation failed (errno=-5)
```

---

### Post by logos34 on 2009-01-02
> **PleaseHelp2 said:**
> I have already booted from the Vista DVD.  When trying to install it says:

Windows cannot be installed to this hard disk space.  Windows must be installed to a partition formatted as NTFS.

It says this about every shown partition which is why I was trying to get to the partition editor.

never actually tried to install vista, but if it's anything like XP it should list the partitions on the hard disk, which you can highlight and delete.  Then select the resulting empty space and tell it to install/format.  Can you do that?

---

### Post by newbee70 on 2009-01-02
> **PleaseHelp2 said:**
> I have searched and gotten most of the info that I require but am still having problems.  

Brief story to hopefully keep the "don't be lazy, learn how to use it" posts out, I was given a new Dell computer for Christmas which had ubuntu installed on it.  I have never used Lynux anything in my life and I am a hardworking single father of two who only has very basic computer knowledge... I don't have the time or energy to learn about using Lynux.  Dell has a 21 day system exchange but by the time I opened the box on Christmas it was already past the 21 days after purchase.



Thanks in advance!



Sounds like you need to give Dell support a call.

---

### Post by Michael.Godawski on 2009-01-02
If there is no data on the machine, you can try to download the Gparted Live CD and either make sure the drives are really mark as free space, or you can try to create a ntfs partition for Vista.


[LIST]
[*][http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[*][http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
[/LIST]

---

### Post by PleaseHelp2 on 2009-01-02
> **logos34 said:**
> never actually tried to install vista, but if it's anything like XP it should list the partitions on the hard disk, which you can highlight and delete.  Then select the resulting empty space and tell it to install/format.  Can you do that?

This got it, thank you so much :)

---

### Post by nothingspecial on 2009-01-02
Just for the record, I started out in exactly the same boat as you.
Me, the wife and the kids all use Ubuntu fine now.
Before you leave is there anything in particular you were having a problem with.
Remember what ever goes wrong in the future, if you have ubuntu the chances are you can get it fixed here for free.
Otherwise good luck.

---

### Post by logos34 on 2009-01-02
> **PleaseHelp2 said:**
> This got it, thank you so much :)

ok.

Don't forget about linux--Dell wouldn't put it on their desktops if they didn't think the average user could handle it.  Be surprised how easy it is to learn.  If you can't run the live cd to test it out, you could safely install it inside windows using Wubi.  I encourage you give it a chance.  Like nothingspecial says, unlike with MS you'll get plenty of free and prompt technical assistance in the ubuntu forums.

---

