---
title: "Font &amp; ATI drivers install..."
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Himself2007 on 2009-11-03
Hello

I have an ATI Radeon Atlantis 9000 Pro (RV250) card and has the problem of black screen.
This has been solved correctly and I can use the Normal visual effects in Appearance preferences now.
But I have a font diplay problem in my desktop and applications.
So as I read previously my solution is in installing ATI required drivers.
About this post from one of the guys shown in the next screen capture image:

[[IMG]http://img230.imageshack.us/img230/3674/clipboard1yx.jpg[/IMG]](http://img230.imageshack.us/i/clipboard1yx.jpg/)

I downloaded the ATI drivers and they are situated in my "downloads" folder, ready to be installed!
But the problem is that I don't find the way to "navigate to my download spot" in the terminal! 
How can I point to this ATI upgrade file FROM the terminal?
Don't laugh!!! I'm a newbie to Ubuntu!
For the rest...I don't see any way I can't understand...for now.
Thanks

Luc

---

### Post by waspbr on 2009-11-03
As far as I know, the default download spot is your desktop. 

so what you have to do is go to a terminal window and type

```
cd ~/Desktop
```

note that the ~ actually represents your home folder (/home/yourUserName/)

once you do that just run the command.

cd actually stands for change directory 

cd .. goes to the preceding directory 

dir gives you a list of files and folder inside the directory

pressing tab autocompletes the name of the file you are trying to type

here is a little something about the commands 
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")


gl

---

### Post by Himself2007 on 2009-11-03
waspbr

Good!
Thanks very much for the cue and the document.
Very useful.

Luc

---

### Post by Himself2007 on 2009-11-03
[B][I][COLOR="DarkGreen"]Still need help!

My ATI driver is on the desktop.

I just entered this in the terminal:

sudo sh ./desktop/ati-driver-installer-9-10-x86.x86_64.run

...and I have this reply from it:

"Can't open ./desktop/ati-driver-installer-9-10-x86.x86_64.run"

Help!

Luc[/COLOR][/I][/B]

---

### Post by waspbr on 2009-11-04
Normally it is easier just navigate to the place you have to do things, in your case the Desktop with:

```
cd ~/Desktop
```

Though from the line you wrote I can see where things have gone wrong, you wrote "desktop"  instead of Desktop. Linux is case sensitive. 


Anyway just try 

```
cd ~/Desktop

sudo sh ./ati-driver-installer-9-10-x86.x86_64.run

```


gl

---

### Post by Himself2007 on 2009-11-04
Hello waspbr

I did a little try..but no success!
What did I do wrong here?

[[IMG]http://img101.imageshack.us/img101/4649/screenshot1a.jpg[/IMG]](http://img101.imageshack.us/i/screenshot1a.jpg/)


Luc

---

### Post by mcduck on 2009-11-04
The solution would be running "chmod +x ati-driver-installer-9-10-x86.x86_64.run" to set the execute permission for the file.

But it won't do you any good since your graphics card isn't supported by new versions of Ati's proprietary graphics driver. Ati/AMD dropped support for all older graphics cards in their drivers (and older driver versions don't work with new Linux kernels and X versions) so using the open source driver is your only option..

---

### Post by anewguy on 2009-11-04
I suspect all you need to do is place a forward slash ("/") after the "." before the file name, as in:

cd ~/Desktop

sudo sh ./ati-driver-installer-9-10-x86.x86_64.run

BUT....I could be wrong.  So, if that doesn't work, please do the following and post the output back here:

cd ~/Desktop

ls -al


Dave :)

---

### Post by Himself2007 on 2009-11-04
Anewguy

Thanks for the advices.):P
And it worked as the install process happened.
And this was the real syntax:

[[IMG]http://img503.imageshack.us/img503/5076/rightsyntax.jpg[/IMG]](http://img503.imageshack.us/i/rightsyntax.jpg/)

Now, going over McDuck's advices as I am new to Ubuntu and like to try and learn from my own errors...
Thanks also McDuck but I can try things as I did a backup just before going this update process.
And everybody knows how weird a video update can be on a computer!
I'm "insured"!
I would also like to thank all others who tried to help me despite my unsuccesses!;)

Luc

---

### Post by Himself2007 on 2009-11-04
> **mcduck said:**
> The solution would be running "chmod +x ati-driver-installer-9-10-x86.x86_64.run" to set the execute permission for the file.

But it won't do you any good since your graphics card isn't supported by new versions of Ati's proprietary graphics driver. Ati/AMD dropped support for all older graphics cards in their drivers (and older driver versions don't work with new Linux kernels and X versions) so using the open source driver is your only option..

mcduck

You were right about this!
A complete mess...hard to describe in fact!:lolflag:
But I applied my previous backup and everything is fine now.
Let's see it in a positive way!
At least I learned two new things here!;)

Luc

---

