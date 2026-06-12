---
title: "Using Ubuntu to recover data after Windows Crash"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by CherokeePlaza on 2011-02-15
**[SIZE=3][COLOR=darkred]HELP me, PLEASE![/COLOR][/SIZE]** I currently have a _Dell Latitude D610_, _running Windows XP Professional_ and yesterday after a restart my computer failed to start Windows. I had a crash several years ago and my brother used a version of Ubuntu that enabled me to go in and recover my important data and files before we reformatted the hard drive. It's been so long I can't remember what version he used, or if it even matters. 
 
I just _spent hours downloading the **Ubuntu Studio 10**_ (started with one of the Desktop versions, but after more than 4 hours of trying to download the approximately 600 mb. file, I had only managed to get 136 mb. and it said there was more than 8 and a half hours left - download speed was 'frozen' at 18.3%). I stopped that download, went back to the Studio download and downloaded the 1.68 gig file in just a few more hours.
 
**_Obviously, I have NO experience with Ubuntu_**, so please **[SIZE=2]forgive me if I sound like a complete idiot.[/SIZE]** _Is this the correct version I need in order to access my Dell data? If not, what do I really need? If I can use Studio for this purpose, can I just use my Daemon Tools Pro to burn the ISO image to a DVD and use that DVD to boot up my Dell - by changing my boot order to boot from the DVD/CD rom?_ [-o<[-o<
 
Thanks for any and all comments and suggestions, and **_again, I apologize if I sound like a complete idiot -- it's just that I am an idiot when it comes to using anything but Windows stuff...I've been brainwashed, I admit it!_** ](*,)
 
Cherokee

---

### Post by sikander3786 on 2011-02-15
Welcome to the forums :-)

The version you probably should use is desktop 32-bit Ubuntu 10.04. Download it here.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Then burn a [Live USB]("http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html") or a [CD]("https://help.ubuntu.com/community/BurningIsoHowto").

Boot from the USB or CD and if the files are still there on the partition, just mount your partition from under Places menu at the top panel and copy/paste your data over to a safe location.

If the partition table is damaged or the files were deleted, you can try using photorec. It recovers files but changes filenames, filenames will not be recovered.

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

And during the process if you fall in Love with Ubuntu, don't hesitate to install it :lolflag:

Good Luck!

---

### Post by kn0w-b1nary on 2011-02-15
i've never used studio, but here is what you can do.

1. Burn .iso to DVD. (I can't recommend a good burner for Windows)
2. Select Try Ubuntu without installing.
3. Plug in a USB drive.
4. In Ubuntu, open the windows drive in nautilus and copy important data to USB.

Hope this helps!

---

### Post by shunan on 2011-02-15
If the windows partition is undamaged you can easy copy and backup. You can find a nice work-through with images here

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

If your partition is damage you can still try and recover it using ubuntu and some forensic tools, for more check this site

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

and good luck

---

### Post by CherokeePlaza on 2011-02-15
> **sikander3786 said:**
> Welcome to the forums :-)
 
The version you probably should use is desktop 32-bit Ubuntu 10.04. Download it here.
 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
Then burn a [Live USB]("http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html") or a [CD]("https://help.ubuntu.com/community/BurningIsoHowto").
 
Boot from the USB or CD and if the files are still there on the partition, just mount your partition from under Places menu at the top panel and copy/paste your data over to a safe location.
 
If the partition table is damaged or the files were deleted, you can try using photorec. It recovers files but changes filenames, filenames will not be recovered.
 
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)
 
And during the process if you fall in Love with Ubuntu, don't hesitate to install it :lolflag:
 
Good Luck!
 
 
 
Thanks so much for your help. Tried to use the initial option for the desktop version, changing to the 10.04 LTS, but again download speeds sucked and was going to take me more than 7 hours to download the 600+ mb file, with speeds maxed at 23.8 kb/s! Decided to use the BitTorrent option under alternative downloads, chose the same version and speeds are much, much better.
 
_Can I still use the same process you provided to make my boot cd?_ If no, please let me know and I'll just have to suffer through the hours and hours to download the right version. 
 
Thanks again for your help! **BTW, if I wasn't dependent on my Windows-dependent programs, mainly Adobe Creative Suite 3 and my animation/graphic design programs, I would switch to Ubuntu in a skinny second. ):P**
 
 
Also, **_thanks to everyone that has offered me suggestions and guidance_**. It means a lot to have such great people willing to help this dork. I'm going to try everything until something works for me. I'm desperate at this point and, just like a typical girl, I've wasted an entire box of Puffs boo hooing over my plight! **I'm switching to alcohol if nothing else works....[-o<[-o<**

---

### Post by Hedgehog1 on 2011-02-15
> **CherokeePlaza said:**
> I'm desperate at this point and, just like a typical girl, I've wasted an entire box of Puffs boo hooing over my plight! **I'm switching to alcohol if nothing else works....[-o<[-o<**

We guys also cry over lost data (and the first scratch on a new car!), so don't sweat it too much.  Who wants to look all red-eyed and puffy anyway?  Backups help keep your tears to a minimum, but it usually takes an event like this to start doing backups...  That reminds me, I am a little overdue to backup one of my drives myself...

Whatever means you use to get an .iso downloaded of Ubuntu (I prefer Bit Torrents as well), the process of burning a boot CD and doing the 'Try Ubuntu' option is the same.

Once you get the GUI running, the 'places' menu will let you select your Windows drive (we all hope).  Your USB drive can also be selected there if it didn't show up on its own.

Then just copy your files from the Windows drive to the USB drive.
  
:KS

p.s. use a slower burn speed on the CD to get a real solid burn

---

### Post by sikander3786 on 2011-02-16
> **CherokeePlaza said:**
> _Can I still use the same process you provided to make my boot cd?_ If no, please let me know and I'll just have to suffer through the hours and hours to download the right version. 
 


If I understood you correctly, yes the process of burning an Ubuntu CD/USB is the same for all the releases. You can burn it to disc using any of your favorite disc burning apps or you can use UNetbootin to create a Live USB.

Hope you'll be able to recover your data successfully :-)

---

### Post by CherokeePlaza on 2011-02-16
> **Hedgehog1 said:**
> We guys also cry over lost data (and the first scratch on a new car!), so don't sweat it too much. 
 
Boy, do I remember the first scratch on my new car!  It was my first new car and I went out and bought it two days after throwing my now-EX husband out on his butt.  I loved that car so much more because I'd gotten it all by myself - with no help from him or anyone else.  I got the better end of that deal, anyway!:lolflag:
 
Thanks so much for being so kind and for helping me.  You made me feel much better.
 
Take care.

---

### Post by CherokeePlaza on 2011-02-16
> **shunan said:**
> If the windows partition is undamaged you can easy copy and backup. You can find a nice work-through with images here
 
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)
 
If your partition is damage you can still try and recover it using ubuntu and some forensic tools, for more check this site
 
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
 
and good luck
 
 
Finally, I managed to download the correct version of Ubuntu and have burned the image to CD.  HOWEVER, **_when I boot from the CD, I get the exact screen provided in the first link you indicated EXCEPT I DO NOT have the 'Try Ubuntu without making any changes to your computer' option_**.  Everything else is exactly the same.  That option isn't there at all - it's not even there but grayed out.
 
What could be the cause and remedy of this problem?  I swear the more I try, the more petrified I'm getting that I'm going to lose everything on my hard drive - about 130 gigs of programs, music, data and work files.  Man, first thing I'm doing when and if I get this fixed, is to buy a backup hard drive.  This is just too nerve wrecking.
 
Thanks again to everyone for your great help and advice.  I couldn't have gotten this far along without your amazing guidance.  If I could, I'd buy you all a drink...or 4.  =D>

---

### Post by CherokeePlaza on 2011-02-16
> **sikander3786 said:**
>  
Boot from the USB or CD and if the files are still there on the partition, just mount your partition from under Places menu at the top panel and copy/paste your data over to a safe location.
 
If the partition table is damaged or the files were deleted, you can try using photorec. It recovers files but changes filenames, filenames will not be recovered.
 
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)
 
And during the process if you fall in Love with Ubuntu, don't hesitate to install it :lolflag:
 
Good Luck!
 
 
 
When I boot from the CD, I get the exact screen as in the link provided by shunan EXCEPT **[SIZE=2][COLOR=red]I DO NOT have the 'Try Ubuntu without making any changes to your computer' option.[/COLOR][/SIZE]** Everything else is exactly the same. That option isn't there at all - **it's not even there but grayed out. 8-[**
 
BTW, is it possible to use Adobe or any of the typical windows apps with ubuntu? I don't think so, but thought I'd ask, just in case. Thanks, again, for your great help. ):P

---

### Post by kn0w-b1nary on 2011-02-16
> **CherokeePlaza said:**
> 
BTW, is it possible to use Adobe or any of the typical windows apps with ubuntu? I don't think so, but thought I'd ask, just in case. Thanks, again, for your great help. ):P

Adobe flash works natively, and Photoshop can be installed using a program called WINE.

---

### Post by CherokeePlaza on 2011-02-16
> **sikander3786 said:**
>  
If the partition table is damaged or the files were deleted, you can try using photorec. It recovers files but changes filenames, filenames will not be recovered.
 
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)
 
 
 
This looks interesting, but **_without having the 'Try Ubuntu' option, is it even possible to go into the Ubuntu's universe repositories to download and install the testdisk & photorec indicated in the blogspot guide_** -  "[I]You need to install the parent package i.e, testdisk for using photorec. It is in the universe repositories. Make sure universe repositories are enabled by going to Software Center > Edit > Software Sources."  

[/I]If so, where do I find the command line?  Wait...if I'm not able to boot up, my wireless connection won't work and I won't be able to download anything.  Do I need to download/install the testdisk and photorec onto the same disk I installed unbuntu on?  Since using a CD as opposed to a DVD, there will only be limited space available to add any additional programs to the live cd.  
 
I first thought that my issue of not having the 'Try Ubuntu' option might be a result of my using a DVD instead of a CD, so **I went back and burned the image to a CD and tried it.  It didn't make any difference, as I'm not still getting the option to try Ubuntu without making changes to your computer'.**  I should have known that it wouldn't be so simple as having used the wrong type of disk...that would be too easy.:cry:

---

### Post by CherokeePlaza on 2011-02-16
> **kn0w-b1nary said:**
> Adobe flash works natively, and Photoshop can be installed using a program called WINE.
 
That's promising, but what about other Adobe programs like those on the Creative Suite 3 Master Collection (Illustrator and those like it)?  ;)

---

### Post by hansolo4949 on 2011-02-16
Which  version of Ubuntu are you trying to use? I believe studio probably does not have a livecd option, so you need to use the desktop version. Also, you most likely can recover your lost data via Ubuntu, if we can just get livecd up and running, so your data is close at hand!

---

### Post by sikander3786 on 2011-02-16
It doesn't matter if you are seeing a Try Ubuntu option or not if you are able to successfully get to the desktop. Can you see the desktop? Or is it the command line that you are booting to? You mentioned it in a previous post but wasn't much clear to me.

Secondly, when you install programs in a Live CD/DVD or USB environment, they don't get burnt to the disk. Instead they are installed to RAM so when you end your session, you get rid of those programs as well and when again boot from the same CD/DVD and want to use the same program you used before, you need to install it once again.

Universe repositories are enabled by default. I mentioned enabling Universe on my blog page just because I thought if some one is trying from inside her Ubuntu install, she might have disabled the Universe repositories accidentally or willingly and might need to re-enable. Otherwise, they are enabled on the Live CD/DVD.

So, go to Applications > Accessories > Terminal and

```
sudo apt-get update && sudo apt-get install testdisk
```

It should install photorec and you can follow the blog post then.

I hope you will get your hands back on your data soon :-)

---

### Post by kn0w-b1nary on 2011-02-16
> **CherokeePlaza said:**
> That's promising, but what about other Adobe programs like those on the Creative Suite 3 Master Collection (Illustrator and those like it)?  ;)

it's being worked on... [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584&iTestingId=57771](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584&iTestingId=57771)

---

### Post by hansolo4949 on 2011-02-16
> **sikander3786 said:**
> It doesn't matter if you are seeing a Try Ubuntu option or not if you are able to successfully get to the desktop. Can you see the desktop? Or is it the command line that you are booting to? You mentioned it in a previous post but wasn't much clear to me.

Secondly, when you install programs in a Live CD/DVD or USB environment, they don't get burnt to the disk. Instead they are installed to RAM so when you end your session, you get rid of those programs as well and when again boot from the same CD/DVD and want to use the same program you used before, you need to install it once again.

Universe repositories are enabled by default. I mentioned enabling Universe on my blog page just because I thought if some one is trying from inside her Ubuntu install, she might have disabled the Universe repositories accidentally or willingly and might need to re-enable. Otherwise, they are enabled on the Live CD/DVD.

So, go to Applications > Accessories > Terminal and

```
sudo apt-get update && sudo apt-get install testdisk
```

It should install photorec and you can follow the blog post then.

I hope you will get your hands back on your data soon :-)

I do not believe you can get into the livecd without clicking on the button.....unless you can close the install or try window, because if you can, then you are golden, since closing the window will initiate the livecd.

---

