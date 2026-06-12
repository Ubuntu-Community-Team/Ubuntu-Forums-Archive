---
title: "Just installed, need to burn a DVD but never used this OS"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by TheLegendOfTheCrappyCompu on 2011-06-28
The title pretty much says it all
I don't have a clue on how to use this OS and it appears to have some pretty obvious bugs. However, I have to use this OS to burn a file right now, yet I can't figure out how and I think I may have damaged a DVD in the process.
So can you tell me step by step what would you do to burn a bootable DVD, if you had just installed?

---

### Post by dFlyer on 2011-06-28
Which Desktop environment did you install, each has it's own cd/dvd burner. I'm using Unity and my burner is Brasero it located in the MultiMedia folder. Just start the program and follow the prompts for file burning if that is what you want to do.

---

### Post by TheLegendOfTheCrappyCompu on 2011-06-28
> **dFlyer said:**
> Which Desktop environment did you install, each has it's own cd/dvd burner. I'm using Unity and my burner is Brasero it located in the MultiMedia folder. Just start the program and follow the prompts for file burning if that is what you want to do.
I'm using Unity too, I think. The interface is bugged, it doesn't work properly nor does the screen resize properly.
Brasero doesn't work here, it doesn't see the DVDs as readable... I downloaded K3B and it got stuck on 0%, plus it made a noise I never heard, it looked like it was breaking so I cancelled it

---

### Post by dFlyer on 2011-06-28
> **TheLegendOfTheCrappyCompu said:**
> I'm using Unity too, I think. The interface is bugged, it doesn't work properly nor does the screen resize properly.
Brasero doesn't work here, it doesn't see the DVDs as readable... I downloaded K3B and it got stuck on 0%, plus it made a noise I never heard, it looked like it was breaking so I cancelled it

Strange, I have no problem with unity, I've been using it since beta1 and I find it very stable for a young desktop environment. When you installed 11.04 did you check the md5sum of your download? Brasero work for me without a problem. Screens resize without a problem here also. What type of error messages are you receiving?

---

### Post by dFlyer on 2011-06-28
If you need to burn a bootable dvd, you need to have an image file iso and select Burn Image. This will bring up a screen that allows you to select the image iso you wish to burn and will also require you to put a dvd in the drive. I would suggest that you check the md5sum of the image you wish to burn before you do to make sure your download was good. I beleive the kde cd/dvd burner you downloaded does about the same thing. I haven't used kde or its cd/dvd burner in a very long time so not sure how that works.

---

### Post by TheLegendOfTheCrappyCompu on 2011-06-28
> **dFlyer said:**
> Strange, I have no problem with unity, I've been using it since beta1 and I find it very stable for a young desktop environment. When you installed 11.04 did you check the md5sum of your download? Brasero work for me without a problem. Screens resize without a problem here also. What type of error messages are you receiving?
I don't know what a md5sum is, but I'm guessing I can't check it now anymore.

Everytime I selected one of the options to burn the file on Brasero it just changed the blank DVD total size and gave a error message "Media Closed or Unreadable" or something like that. 

And when I tried K3B it just stayed at 0% and my ODD started making some very unsafe sounding noises, as if it was going to break, so I cancelled it and took the DVD. Although the ODD had been unused until recently, so I can't know if it is normal.

About Unity, it just ignores my commands, while the computer doesn't let me change the screen size or resolution properly, it always ends up on some sort of tiny cell phone resolution with the screen partially blank, so I need to "refresh" things to see anything again

---

### Post by dFlyer on 2011-06-28
The md5sum file is provided by the web site you downloaded your file from. Look for a file called MD5SUM and click it open. It will list an alpha/numeral checksum. If your in ubuntu you need to enter the following command in the directory your file was saved to:

md5sum "NameOfFile.iso" with out the quotes.

If your using windows you will have to search the web and download md5sum.exe and enter the following command in the directory you downloaded your iso file to:

md5sum.exe "NameOfFile.iso" with out the quotes.

In either case the file must match the alpha/numeral order as provide by the md5sum file on the web site you downloaded from. 99% of the problems new users have is with a bad download or burn, usually as a result of windows. 

Since your running unity have you enter the below at a terminal to make sure your computer can run the software:

/usr/lib/nux/unity_support_test -p

All the responses have to be yes for unity to run correctly. If you have a some no's my suggestion is to log out of unity and log into classic gnome and burn your dvd there. Once your done come back and we can work out your problem with unity, which usually is a video issue.

---

### Post by Jagoly on 2011-06-28
Try logging in with ubuntu classic.

To do this,

log out
click on your user
without typing your password, choose ubuntu classic as the desktop environment on the bar at the bottom.

EDIT: ^ beat me

as for the DVD issue, what exactly are you burning? another ubuntu live CD? That is important.

---

### Post by TheLegendOfTheCrappyCompu on 2011-06-28
I'm on Classic, finally found the terminal. The support test results were all "Yes", it means Unity should work normally right?

I'm going to try to burn again right now.

edit: forgot to say, brasero and other programs seem to freeze or crash sometimes, also on brasero the total DVD size is reduced every time I select a .iso file, I'm using the "burn image" option

---

### Post by andrew.46 on 2011-06-28
If the gui burners are giving you trouble try something like the following:

```
growisofs -dvd-compat -Z /dev/dvd=**[COLOR="Red"]my_filename.iso[/COLOR]**
```

Of course you need to put the correct path and filename of *your* iso file in there...

---

### Post by alphacrucis2 on 2011-06-28
My personal favourite burning program is k3b. Can be installed from the repos. As it is a kde app the downside on the initial install is that it will pull in quite a few kde libs that it needs to run.

Whoops I see you tried k3b already. If you are having trouble with all the burner sw including the previously mentioned command line then I would suggest getting rid of the debian cdrkit burning stuff and replace it with cdrtools which you can install from this ppa:

[https://launchpad.net/~brandonsnider/+archive/cdrtools]("https://launchpad.net/~brandonsnider/+archive/cdrtools")

After installing this you just use brasero or k3b etc as normal

---

### Post by Swagman on 2011-06-28
Something I've noted whilst reading this.

People have been very helpful telling you how to do/try stuff but when it came to using the terminal no help was given in **HOW/where** is the terminal !!

I see you managed to find it but in future.... just press this combination

CTRL + ALT + T

---

