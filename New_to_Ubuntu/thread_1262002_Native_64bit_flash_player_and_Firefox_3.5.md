---
title: "Native 64bit flash player and Firefox 3.5"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Dave W. on 2009-09-09
Hello all,

Sorry about reposting this.  I think it got lost in the sauce.

I have used Ubuntuzilla for FF 3.5. No problem there.

I would like to try this for Flash player:

[http://www.myscienceisbetter.info/in...-on-linux.html](http://www.myscienceisbetter.info/in...-on-linux.html)

But I don't know where to begin.

Do I just grab the Ubuntu script on the bottom of the page, and paste it in the terminal?

I have also tried this video, but it didn't work for me.

[http://www.5min.com/Video/How-to-Ins...lpha-159203519](http://www.5min.com/Video/How-to-Ins...lpha-159203519)

I am using firefox 3.0.13 for now. I'm wondering if I should just wait for Ubuntu 9.10? Any thoughts or suggestions are appreciated.

Thanks,
Dave

---

### Post by Perfect Storm on 2009-09-09
Well, have you tried this; [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by Dave W. on 2009-09-09
Yes, I have, but I will re-read it and try again.

Thanks,
Dave

---

### Post by Perfect Storm on 2009-09-09
Please post if any error output shows up while running the script.

---

### Post by atomizer on 2009-09-09
I would wait, since it is an Alpha release. (have to admit I use 32-bit linux now just for having a stable flash)

The first link doesn't work any more. Looked at the video in the second link, an saw that that IS the regular way to install flash by hand. ( done it enough before). Maybe 3.5 uses another folder, I don't know. Browse your hidden folders and look for folders that look like .mozilla or .firefox or whatever. It doesn't hurt to create a plugins folder in either one of those folders, and copy libflashplayer.so in there.(it isn't neat, I know)

---

### Post by NoaHall on 2009-09-09
Despite being alpha, it is incredibly stable, and gets much more performance than the 32 bit version running natively on 32 bit.

Just copy it into /usr/share/mozilla/plugins (i think)

---

### Post by Dave W. on 2009-09-09
Well, I've tried all ways again and I must be doing something wrong.
I haven't tried manually installing into 3.0.  I may try that.

I have not seen any error when running the script.  In the mean time I think I will use Ubuntuzilla and go back.  

Thanks all for your suggestions.  I will try again later.

-Dave

---

### Post by Excedio on 2009-09-09
This thread worked beautifully for me.
 
[http://ubuntuforums.org/showthread.php?t=1235196&highlight=firefox](http://ubuntuforums.org/showthread.php?t=1235196&highlight=firefox)

---

### Post by Perfect Storm on 2009-09-09
Have you thought of trying Opera while waiting?

---

### Post by Dave W. on 2009-09-09
No I haven't.  Can I get it from the repository?  Will I also have to "configure" flash?

Dave

---

### Post by Dave W. on 2009-09-09
Excedio,

Will that script also configure native 64bit flash.  I have no problem updating firefox 3.5.  It is flash that is my problem.

Dave

---

### Post by Perfect Storm on 2009-09-09
If flash is installed, it should pick it up automatically.

You can download Opera here; [http://www.opera.com/](http://www.opera.com/)

---

### Post by Dave W. on 2009-09-09
A.I.,

Would I be able to remove it if it doesn't suit my needs through ADD/Remove?

Thanks,
Dave

---

### Post by Perfect Storm on 2009-09-09
> **Dave W. said:**
> A.I.,

Would I be able to remove it if it doesn't suit my needs through ADD/Remove?

Thanks,
Dave

Yes, it comes in a .deb file. If it doesn't show up there. You can use Synaptic Package Manager and search for Opera and remove it.

---

### Post by Excedio on 2009-09-09
> **Dave W. said:**
> Excedio,
 
Will that script also configure native 64bit flash. I have no problem updating firefox 3.5. It is flash that is my problem.
 
Dave
 
Actually no. But this will get it going again.
 
[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)
 
It's as simple as downloading the flash from [here]("http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml") and droping it into your .mozilla/plugins folder

---

### Post by Dave W. on 2009-09-09
Thanks A.I.,  I'll give it a try.  If I want to get the 64 bit alpha flash player, how do I do that in Opera?  I'm not quite clear on that.

-Dave

---

### Post by Perfect Storm on 2009-09-09
> **Dave W. said:**
> Thanks A.I.,  I'll give it a try.  If I want to get the 64 bit alpha flash player, how do I do that in Opera?  I'm not quite clear on that.

-Dave

I used the script I link posted earlier.

---

### Post by Dave W. on 2009-09-09
Thanks, A.I. and Excedio!!  

I have enough to keep me busy for a while.

I'll post back when I get all this sorted out.

Dave

---

### Post by Excedio on 2009-09-09
Anytime :-)

---

### Post by nanotube on 2009-09-09
if you're using ubuntuzilla, read this section of the faq:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BThunderbird.2C_Firefox.5D_For_64-bit_Ubuntu_users](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BThunderbird.2C_Firefox.5D_For_64-bit_Ubuntu_users)

in brief: use 32bit flash with 32bit official mozilla build.

---

### Post by Dave W. on 2009-09-09
Very interesting Nanotube.  This could be my problem.  Right now I am using firefox 3.0.13 and flash player version 10.0.21.1.   I don't know if this flash player is an old native 64 bit version or not.  All I know is that it is working well.  Do you know anything about this flash version?

Thanks neighbor,

Dave

---

### Post by nanotube on 2009-09-09
i don't think it's possible to tell from the version whether it is 64 or 32bit. but if it doesn't work when you run the official mozilla build, maybe it's 64bit... 

if you want to use the mozilla build of 3.5.2, try manually installing the flash plugin into your profile directory, as per the instructions on the ubuntuzilla faq.

---

### Post by Dave W. on 2009-09-09
I'm kind of at a standstill right now.  Since everything is more or less working well,  I think that I should leave things as they are.  

     I did install Opera and I will play with that for awhile.

Thanks for your help.

Dave

---

### Post by nanotube on 2009-09-09
if it does what you want, indeed, no need to mess with it. :) 

if everyone took this approach, there would be a lot fewer posts on these forums :)

---

