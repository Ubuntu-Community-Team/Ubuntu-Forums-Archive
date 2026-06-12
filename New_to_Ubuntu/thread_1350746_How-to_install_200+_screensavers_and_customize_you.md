---
title: "How-to install 200+ screensavers and customize your desktop looks!"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Ghost|BTFH on 2009-12-09
This tutorial is for users of Ubuntu and will not work the same in Kubuntu or Xubuntu.  Please make sure you're following along in Ubuntu. :)

Everyone likes variety.  More choices (when it comes to eye candy) equals more fun.  More chances for you to find that look that just says, "it's me."  That's what this tutorial is about - making Ubuntu a little bit more...you.

First of all let me start off with this warning that you should always follow: any command that says "sudo" at the beginning of it is giving an Administrator level command.  You are, for that command, acting as ROOT.  

This means if you do not trust the source of the information, don't do it.

Also, if you come across a web site that has files available for downloading and one of them happens to be a .deb package - this should be a warning to you.  A .deb package is a Debian package designed to make installation much easier than building the program from source (if you're a newbie, trust me, that can be daunting).  All of our download-able programs from the repositories are .deb packages.  

Our repositories are trusted sources, so those files are just fine, generally speaking - however, if the file you're looking for is not in our repositories, that means it's not been accepted into our lists for either legal reasons, security reasons, time issues (such as the program was offered up a little too late in the build) or because nobody's suggested it.  It might be fine, but then again, it might not be.

So, in a way, accepting and installing a .deb package from outside the safe zone of the repositories, can be a lot like taking an aspirin from a stranger - it might not be aspirin after all.

That being said, a lot of times people will say "Oh, you can trust xyz website, I download stuff from them all the time." which might mean the stuff on that site is safe, or that the person telling you this is really lucky.  To be on the safe side, stick with the repositories...

But, what about all the really cool things on websites, like...nifty screensavers and cool themes for your computer?

I'm glad you asked.

Let's take a look in **System -> Preferences -> Screensaver**.  Hmmm...not very many screensavers, are there?  There's a few cool ones, but nothing that really says, "you" right?  Go ahead and close that for now and let's get you a ton of screensavers!

Now the first part is very easy, just follow these steps:

1) Go to **System -> Administration -> Synaptic Package Manager**

2) Once the Package Manager is open, click **Search**

3) In the box that pops up, type in:

*xscreensaver*

4) From the list that shows up, scroll down and select the following to install:

[U]xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra[/U]

5) Click **Apply**

6) Close the program when it's finished.

The next part is a little scary, so I'll give you a full description of what we're doing.

First, we're going to open a terminal.  You can get one by clicking **Applications -> Accessories -> Terminal**

At the *:~$* prompt, I want you to type in:

*cd /usr/lib/xscreensaver*

and hit enter.

Now what this does is, it tells the computer that you want to c(hange)d(irectory) to **/usr/lib/xscreensaver**. In fact, your prompt should now show you this:

*:/usr/lib/xscreensaver$*

Now if you'd like to see what's in here, just type

*ls*

and hit enter.  This asks for a l(i)s(t) of the contents of the directory.

You should see a HUGE list of words.  That list is actually a huge pile of screensavers.  Now, we would like them to be inside our directory called */usr/share/applications/screensavers* because that is where all of our nice gnome screensavers (Like the ones you saw when you opened **Screensaver**) like to hang out.

Because the directories are restricted to Administrator or Root level, we have to give it a Root command to copy them.  Root commands are done by giving the command sudo before the command we want the computer to do.  The command for copy is cp and to copy everything inside a directory, you would use the wildcard *  After the wildcard, we would want to tell it where to put the file copies, which is the */usr/share/applications/screensavers* area.  So the whole command would look like this:

*sudo cp * /usr/share/applications/screensavers*

If we type that into the terminal it will ask us for root's password.  After it's been entered, all the screensavers from */usr/lib/xscreensaver* will be copied into */usr/share/applications/screensavers*.

Okay, so what?  How's that going to help?  Well, remember when we first opened **System -> Preferences -> Screensaver** and we found like, 20 screensavers tops?  Go open it again and check it out.

You should now see somewhere in the neighborhood of over 200 screensavers, ready and waiting for you to enjoy.  Pretty cool, huh?

We're not done yet, let's have a little more fun!

Go to **System -> Preferences -> Appearance** and you will see about half a dozen themes in there that you can change your computer's look with.  More is better though, right?  More choices, more options, more fun!

So let's add some!

Go ahead and close **Appearance** for now and let's go back into **System -> Administrator** and open up the **Synaptic Package Manager** again.  This time in the Search box, we're going to type in 

*gnome themes*

After it's done searching, if you scroll down a little ways, you'll find several very nice themes you can add to your collection.  Specifically, let's add the following:

[U]gnome-themes
gnome-themes-extras
gnome-themes-more
gtk-smooth-themes
gtk2-engines-sapwood
gtk2-engines-smooth
metacity-themes
murrine-themes
[/U]
And then click **Apply**.

Now if we close **Synaptic Package Manager** and go to **System -> Preferences -> Appearance**, we'll now see quite a few new themes to choose from!

While you're checking things out, you can also click on the Customize button and change things like:

_Control_ (This is the internals of windows, sliders, check boxes, buttons, etc.)
_Window Borders_ (This is where you change the actual window borders and the minimize, maximize and close buttons for your windows)
_Icons_ (These are the actual icons displayed for common programs in gnome)

And while you're in there, you can even change your _mouse pointer_ as well.  _Colors_ can be changed, but only in certain themes - other themes have fixed color schemes.

Well, that's all there is to it, hopefully this has been a quick and easy customization of gnome in Ubuntu that makes you feel just a little bit more at home in your own computer.

Have fun and don't take any strange aspirins. ;)

Cheers,
Ghost

---

### Post by duncan503 on 2009-12-10
Thank you: works pretty good, specially the screen savers love it :P

---

### Post by OldGoat58 on 2009-12-10
Ghost,

Dude, or Dudette, as the case may be!  You just totally rocked my world.  The screensaver "StonerView" is just what I need for those cold lonely nights when it's just me and my Makers Mark bourbon.  The themes, just too cool.

I'm slowly but surely picking up on bits and pieces to make my computing experience more enjoyable.  If you have a good line on reputable repositories and a good source for terminal commands I'd appreciate the help!

Thanks!
Mike
Loving Ubuntu in Fairless Hills, PA

---

### Post by ssulaco on 2009-12-10
> **Ghost|BTFH said:**
>   
Our repositories are trusted sources, so those files are just fine, generally speaking - however, if the file you're looking for is not in our repositories, that means it's not been accepted into our lists for either legal reasons, security reasons, time issues (such as the program was offered up a little too late in the build) or because nobody's suggested it.  It might be fine, but then again, it might not be.

So, in a way, accepting and installing a .deb package from outside the safe zone of the repositories, can be a lot like taking an aspirin from a stranger - it might not be aspirin after all.

Thanks Ghost for the tutorial,Yes stick with the repos.

---

### Post by ssulaco on 2009-12-10
> **OldGoat58 said:**
>  If you have a good line on reputable repositories and a good source for terminal commands I'd appreciate the help!

Oldgoat,look here
[http://ss64.com/bash/](http://ss64.com/bash/)

---

### Post by LuisGMarine on 2009-12-10
someone should make a bash script to download and install all these .....

---

### Post by tommynz1975 on 2009-12-11
Great turtorilal, thank you.

One question.  why copy? ok it mayn't take up much space to have a second set of files, but I would hope ubuntu had an alias feature to link-point

 */usr/share/applications/screensavers*.
to the directory
/usr/lib/xscreensaver

Sadly I am not retaining knowledge like I used to, so feel like I am loosing my mind.
Thank goodness for forums.

If you or anyone else has or wants to make a how-to on downloading **Every Game** from the repo's.  for those who just for the sake of doing it want all games. please post the how-to.

---

### Post by Ghost|BTFH on 2009-12-11
Duncan - Very welcome!!! :D

> **OldGoat58]If you have a good line on reputable repositories and a good source for terminal commands I'd appreciate the help![/QUOTE]

Actually, I just use:

[I][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) (For wine, obviously)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)[/I]

And those do me just fine.  I know there's more, but I've had no real need for anything beyond those vast resources.

Oh, and it's Dude, and you're welcome for having your world rocked. :)

[QUOTE="ssulaco"]Thanks Ghost for the tutorial,Yes stick with the repos.[/QUOTE]

VERY welcome!  I'm glad to give back to the community, even if it's just a tiny bit like this.

[QUOTE=LuisGMarine]someone should make a bash script to download and install all these .....[/QUOTE]

The only issue with that is the fact it requires sudo.  I tend to shy away from making scripts for newbies that require that command, as unless you're code savvy, it's not always easy to know what the script is supposed to do before you run it.

[QUOTE=tommynz1975 said:**
> One question.  why copy?

Hey Tommy, the copying was done just because it was a process that newbies can be comfortable doing - most people learn *cp* early on, so performing *sudo cp* is not as scary as say doing an *ln* or *mv*.  A more confident user would know and be comfortable using *mv* instead of *cp*, or using *rm* on the old directory afterward if they wanted to keep their software footprint small.  I would presume a more confident user would read through the instructions, understand exactly what was going on, and make their own decision as to how they wanted it moved.

That was a really good question, I appreciate it. :)

I'm really glad everyone's enjoyed the tutorial and the huge collection of fun stuff that's hidden inside our own humble repositories.

Cheers,
Ghost

---

### Post by cartisdm on 2009-12-11
> **Ghost|BTFH said:**
> Have fun and don't take any strange aspirins. ;)

Cheers,
Ghost

He told me it was candy!!! Haha, but thanks for the How-To Ghost

---

### Post by tbullock17 on 2009-12-13
Ghost,

Adding my thanks to the several above.  I  will use these screensavers and see how they compare to what I am used to.

I am moving to ubuntu from Windows-XP.  In XP I have a program that displays hundreds of pictures that act as my screen saver.  I would like to still use those if I can.  Someone suggested installing wine and then using the windows program there.  Would that work to act as a screensaver for ubuntu?  I am using Karmic Koala as you are.  

If this  question should really be in a different thread, can you tell me a better place to transfer it?

Thanks.

Tom

---

### Post by Ghost|BTFH on 2009-12-13
> **tbullock17 said:**
> In XP I have a program that displays hundreds of pictures that act as my screen saver.  I would like to still use those if I can.

Welcome to Ubuntu!

It sounds like the first step is for you to be introduced to my leetle friend F-Spot Photo Manager.

Open it up, import the folder you're referring to that has your photos in it, select all the photos when that's done and mark them all as FAVORITES.

Then, in your screensaver preferences, go to F-Spot photos.

ALL photos tagged as Favorite are used in a wonderful slide show thanks to F-Spot.

If you need a more detailed step-by-step guide, please let me know and I'll be happy to post one.

Cheers,
Ghost

---

### Post by tbullock17 on 2009-12-13
Ghost,

Thanks for your quick reply.  I apologize that I seem to have misled you by not including enough information.  The XP program is Webshots (an older version that runs in XP, but not in Vista).  That program has its own format.  The pictures work well within it, but they are not jpegs or bmps. That is why I mentioned wine, tho I have no experience with that program yet.

Do you think that FSpot Photo Manager would work with those?  I suppose If I could extract them into  jpegs then I could use FSpot PM as you suggest.  Or am I making an incorrect inference that F Spot PM uses jpeg format?

Your suggestions appreciated!

Tom

---

### Post by Ghost|BTFH on 2009-12-13
Oh my...no, Linux is not like Windows.  We don't just use jpeg and bmp formats. :)

With Ubuntu installed, you have the ability to edit and work with pretty much any web capable image file you can imagine:

jpeg, png, tiff, bmp, gif, etc...as well as pix, fli, cel, ico, tga and many more using Gimp.

Through Gimp, you could convert virtually ANY image file into a jpeg, png, or whatever else you might imagine that you would like to use F-Spot with.

I think you will be quite thrilled over the image creation and manipulation software that is available right at your fingertips in this OS.

And if you have more questions on it, ASK AWAY! :)

Cheers,
Ghost

---

### Post by tbullock17 on 2009-12-13
> **Ghost|BTFH said:**
> Oh my...no, Linux is not like Windows.  We don't just use jpeg and bmp formats. :)

With Ubuntu installed, you have the ability to edit and work with pretty much any web capable image file you can imagine:

jpeg, png, tiff, bmp, gif, etc...as well as pix, fli, cel, ico, tga and many more using Gimp.

Through Gimp, you could convert virtually ANY image file into a jpeg, png, or whatever else you might imagine that you would like to use F-Spot with.

I think you will be quite thrilled over the image creation and manipulation software that is available right at your fingertips in this OS.

And if you have more questions on it, ASK AWAY! :)

Cheers,
Ghost
Through Gimp, you could convert virtually ANY image file into a jpeg, png, or whatever else you might imagine that you would like to use F-Spot with.

Now that is interesting!  If I google GIMP will I find some instructions how to use it?  or do those come with installation? Searching with synaptic package manager I find it right away and many other modules with gimp in the name.  Can you tell which of these I need and which to ignore?

Tom

---

### Post by tbullock17 on 2009-12-13
> **tbullock17 said:**
> Through Gimp, you could convert virtually ANY image file into a jpeg, png, or whatever else you might imagine that you would like to use F-Spot with.

Now that is interesting!  If I google GIMP will I find some instructions how to use it?  or do those come with installation? Searching with synaptic package manager I find it right away and many other modules with gimp in the name.  Can you tell which of these I need and which to ignore?

Tom
I forgot: in previous post it was just before going Christmas shopping.  Will catch you when I get back.  thanks much for your  interest and willingness to help newbies!!

Tom

---

### Post by lemmy999 on 2009-12-13
If you have a vanilla Ubuntu install then you will already have GIMP installed. Go to Applications>Graphics>GIMP Image editor and bang!!!! you're good to go!

AFAIR all you need to do in GIMP is import your image and then do a "save as" Pick whichever format you want!

---

### Post by tbullock17 on 2009-12-13
Thanks, Lemmy999,

Great tips!  I appreciate your quick reply.  Now have to capture my webshot images on disk and bring to Karmic to import.  Likely will be tomorrow or Tuesday.

Tom

---

### Post by Ghost|BTFH on 2009-12-13
> **tbullock17 said:**
> Thanks, Lemmy999,

Great tips!  I appreciate your quick reply.  Now have to capture my webshot images on disk and bring to Karmic to import.  Likely will be tomorrow or Tuesday.

Tom

If you run into any snags, please feel free to ask.  There are many great tutorials on Gimp, if you like video tutorials, check out [Gimp Video Tutorials]("http://sixrevisions.com/graphics-design/gimp_video_tutorials/") and if you prefer reading tutorials, you can check out [Gimp.org]("http://www.gimp.org/tutorials/") which has quite a lot it can show you as well.

I've done a fair bit with Gimp and photo manipulation, but I consider myself to still be a student of it's more advanced features.

Cheers,
Ghost

---

### Post by wordmaster on 2009-12-13
Hi Ghost,

Thank you very much for all the screensavers. There are a lot of very cool fractals and such there, but where can I get seasonal screensavers. Something along the lines of the Christmas screensavers I used to get for windoze? Surely there are some of those available for ubuntu, aren't there?

By the way the Webshots photos are encrypted or something. I have tried all kinds of ways in windoze to change them to regular pics and have never had any success. Also, although you can run the webshots stuff free on windoze with some really fantastic pics, they do not have it for linux. Hadn't thought about wine, but would such a program running under wine actually kick in and act as a linux screensaver?

---

### Post by Ghost|BTFH on 2009-12-13
Okay, I am offering this information with the caveat that these programs were not written by me, they have not been added into the repositories for whatever reasons, and I have not personally tested them - ergo, I do not KNOW they are safe, however I will presume they are, due to the time they have been around.

[Webshots file convertion for KDE (Would work inside gnome as well with some dependencies added)]("http://www.kde-apps.org/content/show.php/Ultimate+WebShots+Converter+for+KDE?content=43440")

[Webilder, which works similar to Webshots]("http://www.webilder.org/")

As for Holiday Screen Savers...

There's Fuzzy Flakes, in the long list of screen savers listed, which is a cute winter saver.

You could also just take a bunch of lovely Holiday scene pictures, slap them into F-Spot and tag them as favorites.  Instant Holiday slide-show screen saver.

As for the goofy screen savers that show random animations of Santa flying around, reindeer farting or other such non-sense, to my knowledge there are no such things for Linux.  Of course, we also don't have the spyware/malware that would be generally added with such things when they're installed.

Cheers,
Ghost

---

### Post by wordmaster on 2009-12-13
Dang! I wanted the one with the reindeer farting! LOL

Seriously, some of those with good 3D type pictures of snow falling, covering stuff up, Christmas light scenes, etc. were pretty, and yes, lots of them were eat up with spyware, adware, etc. but a few weren't. Too bad someone has not done some of those for linux. Oh well, maybe next year....

---

### Post by Ghost|BTFH on 2009-12-13
Oh, you want SNOW?  Well, why didn't you say so?

*sudo apt-get install xsnow*

ALT+F2

Type in xsnow for the command and hit enter.

Make sure you don't have your windows maximized - works even better with a pretty winter scene for your desktop wallpaper.

You get snow that accumulates on your window tops, bottom of your desktop, and even get Santa to do a fly-by from time to time.

;)

No farting reindeer though.

Cheers,
Ghost

---

### Post by Volcom350Z on 2009-12-13
Thanks for this thread Ghost

---

### Post by chillyomi on 2009-12-13
Great tut man the screensavers and the themes are all aweome now the hard part is deciding which one to use:o

---

### Post by Ghost|BTFH on 2009-12-13
> **chillyomi said:**
> Great tut man the screensavers and the themes are all aweome now the hard part is deciding which one to use:o

That's always my toughest decision, although on screensavers, I just plug it in as Random and let it do its thing.

For the themes, I always find one that I like the basic color scheme and then customize everything else to how I like it. My very favorite is the Alloy Window Border, in case you were wondering...something about a Nuclear Fallout symbol for the Close button just does it for me. :)

Cheers,
Ghost

---

### Post by Danno2468 on 2010-01-18
Wow this is an awesome how too! I am not a beginner by no means, but this would have been useful a few years ago.  It is hard to get any kinda practice on terminal, aside from when something isn't working right or is broken which is frustrating to fix.  I like to see code laid out and explained what it's doing.  Good stuff Man:D

---

### Post by Easy Limits on 2010-01-18
Cool!  Thanks.  I don't know what I would do without the bouncing cow.:D

---

### Post by blumagic on 2010-03-25
I am a windows user and a big webshots fan. When I switched over to Ubuntu,I found a great application called bgchanger. It is no longer being supported and I am now using webilder. So far, so good, it is a nice program and good for changing your desktop.

blu.....

---

