---
title: "External Hard drive. And Desktop/Folders not working."
date: 2009-02-18
forum: New to Ubuntu
---

### Post by Magical Mike on 2009-02-18
Hey 
Firstly. When I open places>Home Folder.
It opens fine, but when I click on documents (Or any other folder)
It acts like its loading.
But then it just freezes.
And were ever I move the window. It hides the icons. And then I have to force quit the file browser. And the icons on my desktop are not there.
And I cant even highlight stuff on my desktop.
What can I do to fix this?

---------

I have a maxtor one touch 4.
Is there a way I can take it apart. And make it my permanant hard drive?
If not, can I put ubuntu on it, so when I plug it in to othe computer, and boot it, it will boot the hard drive, and use ubuntu?

--------
Can I get jaunty Jackalope yet?

---

### Post by insineratehymn on 2009-02-18
1) Sounds like metacity is bad. Try reinstalling that or something, never seen that issue.

2) Maybe. Depends on your motherboard more than anything. If you can boot from USB I would give it a shot. As far as taking it apart... Sure, go ahead. Take it apart. Don't get mad if it stops working forever though, regardless of what a tutorial tells you.

3) [Yes.]("http://perldoc.perl.org/perlretut.html")

---

### Post by Magical Mike on 2009-02-18
What is metacity? I have never heard of it.
Is it the program that alows you to browse files or something?
How would I reinstall this?
Its not in my add or remove programs.
I am thinking I should just do this
[http://malocite.wordpress.com/2008/07/13/reinstall-ubuntu-but-keep-your-home-folder/](http://malocite.wordpress.com/2008/07/13/reinstall-ubuntu-but-keep-your-home-folder/)

-edit.
I am new to linux..
So I am not sure how to get jaunty jackalope...
Is there a CD for it out yet?
Or is there a CD out for the Intrepid Ibex? 
If not, were could I download it?
(Sorry for all these questions..)

---

### Post by insineratehymn on 2009-02-19
[Metacity]("http://en.wikipedia.org/wiki/Metacity") is the window manager for Ubuntu, like explorer is the window manager for Windows.
If you want to reinstall, [heres]("http://ubuntuforums.org/showthread.php?t=679965") a little link that even earned a "sweet, i love you man".

Or if you wanna mount your home and format, that will work fine too (maybe the best option if you think there are other culprits).

Sorry I gave you the wrong link! Didn't notice it until this morning!
[Try this one.]("http://linux.softpedia.com/progDownload/Ubuntu-Jaunty-Jackalope-Download-43130.html")

Make sure you know what you're getting into with Alpha software, though. It is exaclty what it states it is... alpha. As in pre-beta. As in pre-pre-release. Don't be shocked if it a) doesn't work well b) works awesome c) doesn't work at all.

=)


Yeah, if you don't

---

### Post by Magical Mike on 2009-02-19
> **insineratehymn said:**
> [Metacity]("http://en.wikipedia.org/wiki/Metacity") is the window manager for Ubuntu, like explorer is the window manager for Windows.
If you want to reinstall, [heres]("http://ubuntuforums.org/showthread.php?t=679965") a little link that even earned a "sweet, i love you man".

Or if you wanna mount your home and format, that will work fine too (maybe the best option if you think there are other culprits).

Sorry I gave you the wrong link! Didn't notice it until this morning!
[Try this one.]("http://linux.softpedia.com/progDownload/Ubuntu-Jaunty-Jackalope-Download-43130.html")

Make sure you know what you're getting into with Alpha software, though. It is exactly what it states it is... alpha. As in pre-beta. As in pre-pre-release. Don't be shocked if it a) doesn't work well b) works awesome c) doesn't work at all.

=)


Yeah, if you don't

Ok well heres the delio!
I upgraded from ubuntu 8.04 to ubuntu 8.10!
Using some command I found.
And I let it do its thing over night, and it works now!
---
But I have some more questions!
I have one of those danged ATI cards. (Last time I installed the driver for it, so i could have the sweet awsome effects). I had to reinstall ubuntu because it would not log in.. It would say screen out of range ect. I even tried editing the refresh rates. that did not work (I am about to instal them agian on this version of ubuntu and see if it works.
It says it will work. 

see heres a picture
[http://i43.tinypic.com/2ah5ljb.png](http://i43.tinypic.com/2ah5ljb.png)
sooo should I do it?
And I just tried to open the documents again. And it gose to grey.
(At least I dont have to reboot all the time...) 
I am not going to upgrade to alpha, jaunty yet. I will wait till it can be picked up on the update :D

---

### Post by insineratehymn on 2009-02-19
Good to hear its working now! ATI... oh god. You could sit on this forum all day and read ati/nvidia woes. I dunno what to tell you about that restricted driver. It will either work wonderfully and your computer will be screaming and playing WoW in wine and dancing across your desk... or you could be like me. And sit there for 4 hours editing your xorg.conf file and messing with drivers in the console until your eyes bleed. I dunno. Buyer beware on that one, bub. But at least search your card first and see how it goes. Oh, and have a second computer with internet and the forums page open before you start. ;)

---

### Post by Magical Mike on 2009-02-19
> **insineratehymn said:**
> Good to hear its working now! ATI... oh god. You could sit on this forum all day and read ati/nvidia woes. I dunno what to tell you about that restricted driver. It will either work wonderfully and your computer will be screaming and playing WoW in wine and dancing across your desk... or you could be like me. And sit there for 4 hours editing your xorg.conf file and messing with drivers in the console until your eyes bleed. I dunno. Buyer beware on that one, bub. But at least search your card first and see how it goes. Oh, and have a second computer with internet and the forums page open before you start. ;)


aha yeah lol.
Oh uh, I noticed with the new update I did, everything is lagging (I hate to complain about a lagg) But its like any program I open has a lagg.
I checked my partion and I have a swap, so thats not the problem.I mean, I dont have any programs up. And it says 77% of memory is in use by programs

See (Bottom right)
[http://i43.tinypic.com/2m30bjd.png](http://i43.tinypic.com/2m30bjd.png)

I have like around 700 MB of ram or a little more.. This computer came with 256 MB of ram...
(I am about to build one of those bare bones computer.) But until then, I need this one to work..

-edit
you have an ATI card? And Interpered Ibex?
Well did the driver work for you on your ibex?
If not, then there is a chance it could work for me?

---

### Post by insineratehymn on 2009-02-19
Don't have any programs working? I see Mozilla, that little task manager thing, your weather bug, that search engine, and you probably got compiz and all that! Wanna see whats running and maybe slowing you down in a cool, low power method? Open a console, maximize the screen and run the top program. It'll show you whats going on and you can sort it by user or anything. Take a screenshot of that and put er up.

Edit:

Yeah, I got an ATI, but not on my 8.10 box. I got that on 8.04 and I never got the drivers to work. On 8.10 its some cruddy onboard Intel.

---

### Post by Magical Mike on 2009-02-19
> Open a console, maximize the screen and run the top program.
I am not sure what you mean by that.
:( 
And documents do not work now :( I thought they did because everything was loading fine..
I think I will do a reinstall on my computer agian :(

---

### Post by insineratehymn on 2009-02-20
Hmm... before you install all that other stuff, do a fresh wipe/install. Then try some of the things you do on a daily basis. Alot of problems can be created if you start with the necessities and work your way up to aesthetic options. If the first thing you do is install Mac4Linux, compiz, vizual task managers, Wine/Cedega, etc... and then you discover that your computer doesn't run right you are kind of up the creek without a paddle. Start fresh; check openoffice, gimp, etc... Learn the terminal! If it looks boring at first thats fine, you already know how to make it look good!

BTW, open a console, click the "maximize" button, and type: ```
top
```
This will show you what is eating your processor/memory.

There is a prettier option. htop, but it has to be installed from the repos.

---

### Post by Magical Mike on 2009-02-20
Ugh, Problems are still here..
I still cant get to my documents :(
How can I transfer my /Home Directory to a external hard drive? So i can reinstall ubuntu agian.
I tried this

[http://malocite.wordpress.com/2008/07/13/reinstall-ubuntu-but-keep-your-home-folder/](http://malocite.wordpress.com/2008/07/13/reinstall-ubuntu-but-keep-your-home-folder/)

But I think I cant do that because I am not sure how to mount my external hard drive.
I mean its already mounted. But I dont know what he means when he says this.

> First mount the drive (I’ll skip all those steps and assume you already know how to do that.  If you don’t, try here or google it.

    sudo cp -r /home /mount/newdrive

[COLOR="Lime"]Next, go and check to make sure all your files and directories have copied to the new drive.[/COLOR] 
Looking at the green text.
Why would they have already copied if all you did was mount it with the above command?

---

### Post by Magical Mike on 2009-02-20
Ok, so I plugged in my external hard drive, thinking I can drag and drop my home folder into the drive. And let it save there, kinda liek a flash drive.
Then it would not let me.
So I opened the drive in a partion editor.
And I wiped the drive. And changed the filesystem, to EXT3
Then I try to grag and drop agian, and this is what I get
[IMG]http://i43.tinypic.com/f37510.png[/IMG]
Then, I think, maybe if I unmount it, then mount it agian, it will work.
So I do that. Then when I plug it in, I get this
[IMG]http://i40.tinypic.com/qrk86b.png[/IMG]

[IMG]http://i40.tinypic.com/2qrzmoh.png[/IMG]

Ubuntu dose not suport EXT3? Should I change it to FAT something?

---

### Post by Magical Mike on 2009-02-24
WOOOHOOO I figured all my shiz out!!!!!!!!!!!

Ok heres what I did..

-Upgraded to ubuntu 8.10
-My computer came with 256MB of ram.. A year ago my dad bought me 500MB of ram. Guess what..... for one whole year... My 500MB of RAM was not plugged in!!!!!!!!! LMFAO!! I plugged it in, and it is so fast! And I enlarged my Swap Portion by 1 gig..

-Updated, and reinstalled some stuff, and now my file browser works!
-Downloaded the restricted thrid party drivers from the add/remove thing, and my ATI card works good now!!!!!!!!! I can finally get the wavy windows!!! WOOHHOOOO!!!

---

