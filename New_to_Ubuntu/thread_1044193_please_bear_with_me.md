---
title: "please bear with me"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Touch0Gray on 2009-01-19
I apologize, I assume this has been covered dozens, if not hundreds of times before. I tried to search and really did not come up with a satisfactory answer to the specific situation/question.

I am new to linux but have managed to keep it running for several weeks now without bailing. I have an older athlon 1.4 with 512 ram a Nvidia video cards (agp) and an OLD Creative Banshee 16 mB pci in the box. I would LOVE to be able to run dual monitors as I do in windows (extend desktop to monitor) My mag lcd only has the standard monitor cable, no S vid, if it did I could run 2 from the first card I assume.

I am running 8.04 with all the updates it feeds me every day or so.

Is there a way?

I am trying to wean myself from windows before I need to buy a new computer if you catch my drift. I am having a good bit of success running my old win applications via Wine (business app's)

Thanks for the help

Gray

---

### Post by mikewhatever on 2009-01-19
I must confess I don't quite understand the problem. What kind of connections do you have for the two monitors? You obviously must have them connected somehow, if they were to work under XP. In other words, what is the problem?

---

### Post by emarkd on 2009-01-19
i don't really understand either, but if you have two video outputs with two monitors connected, you may be able to use the widget at system>preferences>screen resolution to detect and turn on both screens.

---

### Post by hyper_ch on 2009-01-19
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by redseventyseven on 2009-01-19
...so let me see if I've got this straight - you have two video cards (one NVidia and one Creative Banshee) with a monitor plugged into each?

The NVidia card should be fine, but I'm not sure about the Creative Banshee card. Have you managed to get the Banshee card to work on its own?

---

### Post by txcrackers on 2009-01-19
You'd probably be better off with a different *primary* video card that has two connections (workable ones are available for under $30).

---

### Post by Touch0Gray on 2009-01-20
> **mikewhatever said:**
> I must confess I don't quite understand the problem. What kind of connections do you have for the two monitors? You obviously must have them connected somehow, if they were to work under XP. In other words, what is the problem?

The problem is, they both work under windows, but only the primary (nvidia, agp) is recognized under Ubuntu

As i stated if my monitors had an s-video in I could use my n-vidia for both, but that is not the case. 

I believe the cables are called VGA

This is an old machine and I do NOT intend to put any money into it.

---

### Post by blackened on 2009-01-20
As emarkd said, if the other video card was recognized, then you should be able to enable it through the Screen Resolution program at System -> Preferences -> Screen Resolution.

The dialog should show a picture of two monitors, click on each in turn and in the Resolution drop-down box one should be marked as "Off". Adjust the drop-down to your preferred resolution and set the refresh rate in the drop-down just below that, then hit apply.

---

### Post by Touch0Gray on 2009-01-21
I am sorry if I wasn't clear as to my question. There is no indication in the Screen resolution of a second monitor or display. I went into my bios and switched my primary display to PCI rather than AGP and Ubuntu would not display on the associated monitor. SO....apparently this card is not supported and all of the research I have found supports that supposition. Thanks for your time.

---

### Post by overdrank on 2009-01-21
> **Touch0Gray said:**
> I am sorry if I wasn't clear as to my question. There is no indication in the Screen resolution of a second monitor or display. I went into my bios and switched my primary display to PCI rather than AGP and Ubuntu would not display on the associated monitor. SO....apparently this card is not supported and all of the research I have found supports that supposition. Thanks for your time.

So you are trying to use two graphics cards. Have you tried the command ```
gksu displayconfig-gtk
```

---

### Post by Touch0Gray on 2009-01-21
> **overdrank said:**
> So you are trying to use two graphics cards. Have you tried the command ```
gksu displayconfig-gtk
```

Thanks I will try that, I stand to lose nothing.

My next post will have a more descriptive title, I understand now.

---

### Post by Touch0Gray on 2009-01-21
I tried the [gksu displayconfig-gtk]and it gave me the configuration window which actually does list the banshee, pci card, but the options for enabling it are not available as a secondary monitor. It will allow me to make it my primary monitor,and my other(now default) but I am rather nervous about doing that because it it doesn't work, then wouldn't I have NO working display at all? In which case how would I fix it?. Could that be done thru the recovery console (command line)?

My other option here is to see if I can find an adapter that will allow me to go from my Nvidia card (which has a VGA and s-video out and supports dual monitors) to the vga input on my secondary monitor and just pull the pci card out of the box entirely.

Before I even consider switching my office to Ubuntu permanently I need the ability to run dual monitors and a scanner (which is an ongoing project at which I am failing miserably. Stay tuned for a thread titled Visioneer 8600 HELP!!!!!!)

---

### Post by Touch0Gray on 2009-01-22
ARGGGGGGGGGHHHHHHHHHHHH......
a friend gave me a different video card because there didn't seem to be ANY way the Creative was going to work. I put in an ATI Rage 6 pci and now I can use one monitor or the other, but not both. I have had this so screwed up 4 or 5 times that the recovery mode was my only salvation

I have been using the  [ gksu displayconfig-gtk ] to make my changes. 

From where I sit now, I am using the nvidia agp (in to a Samsung synchmaster 931BF) and the AT pci card is in to a Mag LT4664s and it is getting a signal and I can read the card bios information at the top of the screen.

Still, the display config panel will not allow me to make the pci card and Mag a secondary display and if i do it the other way (with the Mag as default) it works BUT the Samsung on the nvidia doesn't.](*,)](*,)

I feel like an idiot, this shouldn't be this hard should it?????

---

### Post by overdrank on 2009-01-22
> **Touch0Gray said:**
> ARGGGGGGGGGHHHHHHHHHHHH......

I feel like an idiot, this shouldn't be this hard should it?????
I wish I could be of more help, I have limited experience and I was using a integrated graphics along with the nvidia. As for two separate cards I can not help. :(
Have you tried to manually edit your xorg? Does is show both graphics cards after using xfix to correct your issues.

---

### Post by Touch0Gray on 2009-01-22
> **overdrank said:**
> I wish I could be of more help, I have limited experience and I was using a integrated graphics along with the nvidia. As for two separate cards I can not help. :(
Have you tried to manually edit your xorg? Does is show both graphics cards after using xfix to correct your issues.

I can say for sure that I haven't tried to edit my xorg (because I don't know what it is or where, or what to edit it to) And, I don't know what xfix is either....I am in so far over my head here.

When I go to the terminal, and [gksu displayconfig-gtk ] is see both displays listed and I can use one or the other, just not both.  

Ok so I do know that in windows, if you don't have the right drivers, you cannot run dual monitors, can I assume this is a driver issue??????

Not that that will get me any closer to a resolution to the problem

---

