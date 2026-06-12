---
title: "firefox and thunderbird installation problem"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by aloprot on 2010-07-17
Hi ubuntu forum members, I have a problem regarding Firefox and thunderbird installation. I want to use the latest version of both firefox and thunderbird, not the one in the repositories. I have downloaded both from the official website, extracted them but when double clicking to execute them, they do nothing. I've been on google but didn't find a guide to install them properly. I found something which has to do with adding a ppa mozila-daily I think it was called. My knowledge in security is more than low. Is this safe? Also I want them to update themselfs...to the latest versions in the future.
If you can, please provide me with a guide. Thanks so much!

---

### Post by the.phantom on 2010-07-17
for me this is the best/easiest way to do it

[http://ubuntuforums.org/showthread.php?t=421370](http://ubuntuforums.org/showthread.php?t=421370)

on the main page/3rd party projects
he has mkade it easy now with his repositories ! and after updated it will auto update usually a day after release of firefox or thunderbird.

---

### Post by oldsoundguy on 2010-07-17
Been using this for several years.  It allows updates when they are no longer being put in the repositories for your particular build.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by Norm24 on 2010-07-17
Thunderbird 3.1 may not work with Ubuntu.I had several issues regarding Tbird.It simply would not launch even though it was installed.Don't know if that bug has been addressed yet.

Look here:
[http://ubuntuforums.org/showthread.php?t=1517315](http://ubuntuforums.org/showthread.php?t=1517315)

---

### Post by aloprot on 2010-07-17
At the end I convinced myself to use ubuntuzilla. I followed the guide but it does not work. I don't know, the download location could be changed? Could an administrator change my post location to ubuntuzilla or can someone can tell me what's wrong?
I followed this guide: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

---

### Post by nightshade209 on 2010-07-17
With regard to the ones you have downloaded from the Mozilla website, I assume you got them in the .tar.bz2 format? After you have extracted it, open the folder, right-click on the file named "firefox" (or "thunderbird", whichever it is), select Properties. Then go to the Permissions tab, and tick the box next to "Allow executing file as program". Now try launching it. Also, you will need to exit any other firefox (or thunderbird) windows that are open before you launch the new instances.

---

### Post by techunit on 2010-07-17
I have done it using Ubuntu Tweak to manage my PPAs... I works great and It gives you tons of options to boot...

---

### Post by lovinglinux on 2010-07-17
See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) tutorial.

---

### Post by aloprot on 2010-07-18
Lovinglinux, I have tried your #2 option but I have troubles with ubuntuzilla. I did this steps:
Edited my etc/apt/sources.list adding this line deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

Then I did sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29

But while running this command, sudo apt-get update I get this error: W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


I tried to ignore it and do sudo apt-get install firefox-mozilla-build as it says there on the ubuntuzilla page but I get Building dependency tree       
Reading state information... Done
E: Couldn't find package firefox-mozilla-build

What did I do wrong?

---

### Post by crichard on 2010-07-18
> **aloprot said:**
> Hi ubuntu forum members, I have a problem regarding Firefox and thunderbird installation. I want to use the latest version of both firefox and thunderbird, not the one in the repositories. I have downloaded both from the official website, extracted them but when double clicking to execute them, they do nothing.  Also I want them to update themselfs...to the latest versions in the future.
If you can, please provide me with a guide. Thanks so much!


Try this post [http://surferzworld.com/2010/01/installing-firefox-thunderbird-ubuntu/](http://surferzworld.com/2010/01/installing-firefox-thunderbird-ubuntu/)

You can update to newer version easily, because Check for updates is enabled in this method.

---

### Post by aloprot on 2010-07-18
I will try and install them again, old fashion way from the mozilla website but will the update automatically or do I need to download them again and again?

---

### Post by oldsoundguy on 2010-07-18
Linux is not Windows.  NO updates are automatic.  You will, however get a notification that an update is available in some programs (I get them in Firefox and in Thunderbird).  But you have to GO GET THE UPDATE yourself.
Just another layer of protection.

---

### Post by lovinglinux on 2010-07-18
> **aloprot said:**
> Lovinglinux, I have tried your #2 option but I have troubles with ubuntuzilla. I did this steps:
Edited my etc/apt/sources.list adding this line deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

Then I did sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29

But while running this command, sudo apt-get update I get this error: W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


I tried to ignore it and do sudo apt-get install firefox-mozilla-build as it says there on the ubuntuzilla page but I get Building dependency tree       
Reading state information... Done
E: Couldn't find package firefox-mozilla-build

What did I do wrong?

Ubuntuzilla is for 32bit only. Your options are basically to download from Mozilla and install manually (Method #1) or use a PPA (Method #3).

> **aloprot said:**
> I will try and install them again, old fashion way from the mozilla website but will the update automatically or do I need to download them again and again?

When you download and install manually, you need to download again when a new version come out. That's the price of being ahead of the repositories. There is a way to keep it updated, but I don't recommend.

If you are more concerned about convenience, then use one of the ubuntu-mozilla ppa repositories.

---

### Post by aloprot on 2010-07-19
I have fixed it now, it seems that I was running amd64 version instead of 32 bit version. Now I am on 32 bit and everything works fine. Thanks for all your replies.

---

### Post by jimbo2907 on 2010-08-26
Hi Folks....thank you for taking the time and trouble to help us noobs.

I installed Ubuntu 5 days ago....looked great....seemed to offer everything I want.

Then I clicked on the firefox icon and it brought up Google ...Great!....Then I said ..this is easy..I'll have a look at my share-trading dynamic platform.  Searched for Commsec and click 'launch Webiress'...and then it hiccupped!

I got a message saying I needed Java  "Now downloading".....Okay I've had this happen in windows...no problemo..   Then I tried to follow the instructions contained on the download page from Java....thats what started my five days (30 hours now and counting) of misery.:(

Finally on one of the hundreds of Ubuntu pages I've read I found that there is a bug in java....that prevents it from working with the Firefox that Ubuntu provides.

So I cleverly removed firefox ....and went to Mozilla and downloaded a new version 3.6 of Firefox.....followed the instructions at Sourceforge.net (and other places I can't remember).   Now I have Firefox in a folder in 'Documents' with libjavaplugin_oji.so linked to ///java/jre.6.0_21/plugin/i386/ns7...

BUT  I don't have Firefox in Applications/Internet!    How on earth do I fire the thing up please?     (31hours and counting ....*hysterical laughter*)

---

### Post by jimbo2907 on 2010-08-27
Okay I found that by Cd ///firefox and  typing './firefox' it will startup the "A Web Browser" (which I had previously got working to allow me to browse the web).   But when I try to fire up Webiress I still get the messsage "Java not installed ...now downloading". 

Help please?

---

