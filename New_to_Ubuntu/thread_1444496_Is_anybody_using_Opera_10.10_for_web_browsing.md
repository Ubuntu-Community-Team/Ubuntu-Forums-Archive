---
title: "Is anybody using Opera 10.10 for web browsing?"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-04-01
Giving up on getting Firefox to view pages like Pogo since it won't get past the applet started phase and wondering if Opera will work. Is anybody using Opera and did it need any add-ons to work correctly? If so, is there and easy install method with easy to follow instructions? (I finally figured out where/what terminal is but still don't know what the instructions mean.)](*,)

---

### Post by Temposs on 2010-04-01
Just go here: [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

Click the big download button which should download a .deb file for you. You can just double click on it and it will open an easy installer. In Ubuntu, any file that ends in .deb is something that can be installed by double clicking on it.

---

### Post by flyfishingphil on 2010-04-01
Thanks. I had found and done that then, to add to my frustration, I found that the gaming sites I want to use don't "recognize" Opera and call for IE's or Firefox. Unfortunately the FF offered here isn't up to date enough to use and I can't figure out how to update it to the version that works. I also noticed that, when you check Pogo and what browsers it accepts, it lists Linux as one of the systems it doesn't recognize.

Guess I can call this one closed and see if I can figure out a way to get directions on how to upgrade the FF to one that works.

Thanks for the response.

---

### Post by Temposs on 2010-04-01
I dunno what problem you're having. I just ran a game on Pogo and it worked just fine with the standard version of Firefox on Ubuntu 9.10.

---

### Post by Scunnered on 2010-04-01
**flyfishingphil**

There used to be a facility within Opera that let you report it to other web sites as IE or FF.  This plays hell with Operas browser share stats but might solve your problem.

See if you can still kid on web pages and give this a try.  Might just work for you.

---

### Post by TeoBigusGeekus on 2010-04-01
> **Scunnered said:**
> **flyfishingphil**

There used to be a facility within Opera that let you report it to other web sites as IE or FF.  This plays hell with Operas browser share stats but might solve your problem.

See if you can still kid on web pages and give this a try.  Might just work for you.
Right click on webpage->Edit site preferences->Network tab->Identify as pull down menu.

---

### Post by Linuxforall on 2010-04-01
Try the latest beta 10.52 6230, its in deb and is among the quickest of browsers around.

[http://snapshot.opera.com/unix/snapshot-6302/](http://snapshot.opera.com/unix/snapshot-6302/)

---

### Post by flyfishingphil on 2010-04-01
Getting a little impatient I guess, after several days of trying to get 9.10 to where/what I want and running into walls, so uninstalled the Opera. Went to Ubuntuzilla and installed the latest version of Firefox, restarted, went to Pogo to test and got this message in the middle of the screen:

Pogo.com games use the Java plug-in. You either do not have Java installed or you have a version that is incompatible with our games. It does not cost you anything to install Java.

Any ideas on what needs to be done? (Also addressed this in another post regarding Java updates but haven't gotten an answer yet.)

More research trying to figure out if Ubuntu is workable. CHecked version of FF installed here is the info:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.2) Gecko/20100316 Firefox/3.6.2

---

### Post by jaycee23 on 2010-04-01
Hope this solves your prob fishing dude

For i386 (32 bit Ubuntu):
$ sudo update-alternatives --install  /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so  /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50

 For amd64 (64 bit Ubuntu):
$ sudo update-alternatives --install  /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so  /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so 50

Not my cleverness - behold the power of google

Had the same prob as you Phil - Firefox not looking in the right place for java !!!

---

### Post by flyfishingphil on 2010-04-01
> **jaycee23 said:**
> Hope this solves your prob fishing dude

For i386 (32 bit Ubuntu):
$ sudo update-alternatives --install  /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so  /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50

 For amd64 (64 bit Ubuntu):
$ sudo update-alternatives --install  /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so  /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so 50

Not my cleverness - behold the power of google

Had the same prob as you Phil - Firefox not looking in the right place for java !!!
Copied you sudo, went to terminal and pasted, enter, password, went nowhere. Is there something else I need to do?

---

### Post by jaycee23 on 2010-04-01
Had to try it twice

Now able to use pogo.com

---

### Post by flyfishingphil on 2010-04-01
> **jaycee23 said:**
> Had to try it twice

Now able to use pogo.com
Went back and entered it in terminal. Here's all I got:

flyfishingphil@flyfishingphil-laptop:~$ sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50
flyfishingphil@flyfishingphil-laptop:~$ 

Is ther something else I need to do? (Keep in mind you're dealing with a total noob and been trying for about 24 hours to get this operational. Know little about Linux.)

---

### Post by jaycee23 on 2010-04-01
pkill firefox

Restart it then try to use the java plugin on pogo

Sorry have to put my little one to bed now (aawwww) - but will try to help you later if you're still in trouble if I get back online

:P

---

### Post by flyfishingphil on 2010-04-01
Still no good. Giving up and trying Opera again. Maybe with the adjustments from above I can get it to work for me. If not I'll flip a coin and see if I give up Pogo or Ubuntu and go back to "Windough$"

Thanks for the assists.

Well, tried setting Opera to be seen as IE and found out that it's as IE6 and Pogo won't be accepting that much longer and requires going to IE7 or, preferably, 8. With that in mind changed it to Firefox and still can't get to the game playing part. Even tried going in thru Facebook but that didn't work either.

Opera seems to be a little on the slow side when browsing. Can't seem to update the Firefox to work right. May have to do a little more poking around and see what else I find in major problems with Koala. Fortunately I did a dual boot so I can still go to "Windough$" when I need to take care of my business side. Will let you know what comes up as I figure out more.

---

### Post by jaycee23 on 2010-04-01
Only other thought would be to roll back version of Firefox to standard in repos.

Do a complete removal via purge.

If keen to use Firefox 3.6 - I would upgrade via Ubuntu-tweak.

You should be able to get Java to work that way.

---

### Post by flyfishingphil on 2010-04-01
Started with the FF that was in 9.10. First time at Pogo it said needed newer version. Went to the site recommended and it has 6u19 there. Would like to install that to see what happens but can't get it done. Directions get a little confusing when you don't speak the "Ubuntu language". Little things like what do I assign as a "path" when trying to install JRE-6u19-linux-i586.bin.

---

### Post by jaycee23 on 2010-04-02
i am only using Java version 1.6.0_15 and it works fine on pogo

To check version

java -version

Is your medibuntu rep activated?

Try this webpage

[http://www.futuredesktop.org/](http://www.futuredesktop.org/)

Go from 7a and follow the instructions there!

BTW always use this page when I install a clean version of Ubuntu  - lots of helpful hints in getting your system set-up.

---

### Post by flyfishingphil on 2010-04-02
I went back in and "re-installed" the "Ubuntu restricted extras", restarted and checked and FF is working fine now. 

Next problem, Opera still not working right. Gave it 9 minutes on 1 Pogo game and it never came up. Went to remove Opera and can't find to remove it using Synaptic or digging around in Ubuntu Software Center. Any directions on how to find and remove Opera?

Never Mind! Went back to Synaptics and entered Opera in Quick Search, instead of full Search, and there it was. All gone now! Someday I may actually get the hang of Ubuntu.

---

### Post by jaycee23 on 2010-04-02
Last thought - install ubuntu-tweak

Very useful piece of software for all sorts of stuff including installing opera and other ppa type software

---

