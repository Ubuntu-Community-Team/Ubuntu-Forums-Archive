---
title: "Need help with Lightscribe"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by UglyShirts on 2008-12-28
I have a headache, so I'll make this as brief as possible.  

Just installed an LG GH20 DVD Burner in a Dell OptiPlex GX620 running Hardy 8.04.  Burning works fine, but LightScribe functions do not.  Neither Simple Labeler nor LaCie image burners work.  In the LaCie image burner, I can open the app fine from a command line in Terminal, but when I go to print the disk, I get a greyed-out drop-down saying "No drives have been detected."  

This has been making me insane for the better part of the evening.  I've been Googling / poking through these forums looking for a solution for several hours, and have seen solutions ranging from altering my jumper configuration to "you're screwed in all kernels after Edgy."  Please, won't someone end my pain?  I just want to burn pretty pictures on my expensive LightScribe DVD's.

---

### Post by hyper_ch on 2008-12-28
what's lightscribe function?

---

### Post by UglyShirts on 2008-12-28
> **hyper_ch said:**
> what's lightscribe function?

Neither of the apps I installed to label the non-data side of the Lightscribe media seem to be working, because the drive isn't apparently recognized by the OS when being asked to perform that function.  The data burns perfectly, but the labeling will not function, and I'm hoping someone has it figured out.

---

### Post by theozzlives on 2008-12-28
You'd be surprized how well a Sharpie works, but seriously, I have LightScribe on one of my writers. It didn't come with any dosks to try it out so I buy cheap disks.

---

### Post by onezeno on 2008-12-28
Have you checked [here]("https://help.ubuntu.com/community/LightScribe")?  Are you on a 64-bit machine?  

@hyper_ch:  Lightscribe requires both a special burner and disks, and will allow you to flip over the disk and burn a black/white image (actual image, not ISO) as a CD label.  

I have a Lightscribe burner but I've never bothered to use it.  I'll post again if I get it working.

---

### Post by hyper_ch on 2008-12-28
interesting.. now I know what it is. Thx :) but can't help with the issue you have.

---

### Post by UglyShirts on 2008-12-28
> **onezeno said:**
> Have you checked [here]("https://help.ubuntu.com/community/LightScribe")?

Actually, that's where I started.  I installed my packages from the links on that page.

> Are you on a 64-bit machine?

That's a good question.  I have no idea, nor any idea of how to find out.

---

### Post by hyper_ch on 2008-12-28
run
```

uname -a

```

This returns for me:
```

Linux xubi 2.6.27-11-generic #1 SMP Fri Dec 19 16:29:35 UTC 2008 x86_64 GNU/Linux

```
and the **x86_64** says I'm using 64bit.

---

### Post by UglyShirts on 2008-12-28
Here goes nothin':

```

Linux 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

```

I don't know if that helps.

---

### Post by hyper_ch on 2008-12-28
it's 32bit (i686)

---

### Post by UglyShirts on 2008-12-28
Update:  

Double-check reveals that Simple Labeler apparently DOES recognize the drive.  LaCie 4L still does not.  And that's the one I'd like to use.  

Found some additional info here, but an attempt to follow the steps results in an authentication failure on step 2:

[http://fedorasolved.org/multimedia-solutions/lightscribe-for-linux](http://fedorasolved.org/multimedia-solutions/lightscribe-for-linux)

Step three there looks like it might address if not outright resolve the issue, but an attempt to run that command also produces authentication failure.  

There's also some information here indicating to me that I may not have installed the program properly or be "running it as root," but a lot of it is beyond my skill level:

[http://ubuntuforums.org/archive/index.php/t-540063.html](http://ubuntuforums.org/archive/index.php/t-540063.html)

I'm sure I'm doing something wrong, here.

---

### Post by UglyShirts on 2008-12-28
More info:

I just noticed when I try to click the "print" button in LaCie 4L, I get errors in the terminal window:

```
4L-cli: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

Hopefully that will help someone help ME figure out what the hell I'm doing wrong.

---

### Post by onezeno on 2008-12-28
Try this:

sudo apt-get install libstdc++6

---

### Post by UglyShirts on 2008-12-28
> **onezeno said:**
> Try this:

sudo apt-get install libstdc++6

Tried that.  It seemed to install something, but it didn't fix the problem.  :(

---

### Post by anewguy on 2008-12-28
I'm going out on a limb here, so I'm going to leave it to someone else for the exact syntax, but that error could indicate on the outside (not knowing the product or haved used it) that a dependency is missing.  There is a way at the command line to get those, something along the way of:

sudo apt-get build-dep <what ever your package name is for the LaCie software product>

It's also possible that some sort of link is needed - perhaps to point something to the Ubuntu path versus a more general "Linux" path.

This is assuming the product is Linux based.  If it's a Windows product running in Wine then I don't know that answer.

Dave :)

---

### Post by anewguy on 2008-12-28
Just found this link as well, if you haven't seen it:

[http://onlyubuntu.blogspot.com/2008/05/howto-install-lightscribe-in-ubuntu.html]("http://onlyubuntu.blogspot.com/2008/05/howto-install-lightscribe-in-ubuntu.html")


One of the follow-ons on the post says you also need to install libstdc++5, so try this:

sudo apt-get install libstdc++5

and see if that helps any.

Dave:)

---

### Post by halw on 2008-12-28
> **anewguy said:**
> Just found this link as well, if you haven't seen it:

[http://onlyubuntu.blogspot.com/2008/05/howto-install-lightscribe-in-ubuntu.html]("http://onlyubuntu.blogspot.com/2008/05/howto-install-lightscribe-in-ubuntu.html")


One of the follow-ons on the post says you also need to install libstdc++5, so try this:

sudo apt-get install libstdc++5

and see if that helps any.

Dave:)

Nice work Dave. I just got a ligtscribe burner, not yet installed, and have been looking for a, more or less, definitive set of instructions on installing the Lacie software. Your link seems to be what I'm looking for.

Hal

---

### Post by 2hot6ft2 on 2008-12-28
In the LaCie 4L program where it "would" show the drive there is a little circular arrow similar to a reload arrow (just to the left) (it goes in kind of a semi circle).
Did you click on that? You have to each time for it to load the drives info. I'm not on the laptop right now or I would take a screenshot.

---

### Post by 2hot6ft2 on 2008-12-28
The lightscribe software is ok I suppose if you want text going around the disc. Personally I don't care for turning the disc to read it and I usually have more to put on it than will fit and still have a large enough font to read easily.

The LaCie 4L software is great for putting pictures on the disc and sizing them to fit unlike the lightscribe software.

Just so you know what each one can and cant do.

---

### Post by rhonaldmoses on 2008-12-30
Check this page entirely dedicated for using LightScribe in Ubuntu [also 64 bit ubuntu].

[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

---

### Post by Aussieartist on 2008-12-30
Thanks for this thread... I'm trying to get the files:
[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)
but I get this:

/tmp/lightscribe-1.14.32.1-linux-2.6-intel-2.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

Am I missing something stupid? (Wouldn't be the first time. :))
Thanks
Aussie

---

### Post by Aussieartist on 2008-12-30
Doh! Ignore last post... The answer jumped up and bit me on the bum!
A

---

