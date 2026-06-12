---
title: "Need Adobe Acrobat PDF viewer"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by PDA1 on 2009-11-25
Can anyone tell me where to get and HOW to install Adobe Acrobat so I can view PDF files?

I've downloaded the Acrobat so many times for linux and the darn thing won't run.

It seems I have to install countless other packages and I'm SICK OF IT.

I assume Adobe is the standard....unless someone has a better idea of what to use.

---

### Post by Mr. Devil on 2009-11-25
Enable partner repositories and Aptitude will pick it up.

---

### Post by staf0048 on 2009-11-25
I'm pretty sure Ubuntu comes with a PDF viewer as standard.  Is there a reason why you need Acrobat specifically?

---

### Post by PDA1 on 2009-11-25
> **Mr. Devil said:**
> Enable partner repositories and Aptitude will pick it up.


How do I do that?

---

### Post by PDA1 on 2009-11-25
> **staf0048 said:**
> I'm pretty sure Ubuntu comes with a PDF viewer as standard.  Is there a reason why you need Acrobat specifically?

For whatever reason a PDF file a friend sent can't be read on my machine.  I can read other PDF files on this machine (Ubuntu) but not the one in question.  No it's not a corrupted files as I can read it on Windows OS.

---

### Post by 73ckn797 on 2009-11-25
Go to System/Administration/Software Sources and tick the restricted and multiverse sources. You will need to reload. Then go to System/Administration/Synaptic Package Manager and you should find it listed as acrobat.

---

### Post by Cheesemill on 2009-11-25
System > Administration > Software Sources > Other Software

Check the line that ends in partner

You can then use Software Centre or:
```
sudo apt-get install acroread
```

---

### Post by kansasnoob on 2009-11-25
> **Cheesemill said:**
> System > Administration > Software Sources > Other Software

Check the line that ends in partner

You can then use Software Centre or:
```
sudo apt-get install acroread
```

+1!

Although I prefer Evince which should be installed by default. Maybe a right click and choose to open with .................. evince?

---

### Post by PDA1 on 2009-11-25
Here's what happened-

earl@earl-laptop:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package acroread


What do I do?

---

### Post by tacantara on 2009-11-25
> **73ckn797 said:**
> Go to System/Administration/Software Sources and tick the restricted and multiverse sources. You will need to reload. Then go to System/Administration/Synaptic Package Manager and you should find it listed as acrobat.

Did you check the restricted & multiverse sources box in Software Sources, then reload, as mentioned in the quoted passage above?  I had to to that in order to download Acrobat Reader.  It worked fine for me when I executed it in that order.

---

### Post by PDA1 on 2009-11-25
Yes, I did.  What does "reload" mean?

---

### Post by PDA1 on 2009-11-25
I think "reload" applies to Synaptic Package Manager.

Regardless, when I search for the word ADOBE in Synaptic the word doesn't appear.

A bunch of other viewers for looking at PDF files show up but I specifically want Acrobat.

---

### Post by tacantara on 2009-11-25
Reloading Synaptic is essentially refreshing the package information.  To manually refresh Synaptic, just click on the Reload icon in the top left corner of the icon bar at the top of the GUI.  If I remember correctly though, Synaptic will automatically reload after you are done checking the box to enable restricted and 3rd Party titles.  Just in case, though, be prepared to manually refresh.

---

### Post by PDA1 on 2009-11-25
'still can't find the word Acrobat or Adobe when I search synaptic.

However, it DOES say I have installed some sort of Ubuntu PDF viewer.

---

### Post by tacantara on 2009-11-25
There is a PDF viewer that comes as a default program with every Ubuntu distro.  Try searching for _***acroread***_ and tell me what you find.

---

### Post by PDA1 on 2009-11-25
Found nothing called ACROREAD in Synaptic.

---

### Post by tacantara on 2009-11-25
I assume you've gone to System > Administration > Software Sources and checked the boxes on the Ubuntu Software Tab labeled Proprietary drivers for devices (restricted) and Software Restricted by Copyright or Legal Issues (multiverse).  If you haven't, then check those boxes and close the Software Sources box, then manually reload Synaptic.

If you have checked those boxes, try closing Synaptic and reopening it, or close Synaptic and run the terminal command to install acroread:

```
sudo apt-get install acroread
```

---

### Post by PDA1 on 2009-11-25
Solved!

Here's where I found out what to do.

[http://ubuntuforums.org/showthread.php?t=1110044](http://ubuntuforums.org/showthread.php?t=1110044)


Thanks for your help, and especially all of your patience

---

### Post by NJ0E on 2009-11-25
Another way to get it is to install Open Office.  It has a native .pdf reader in the Word Processor application.

---

### Post by PDA1 on 2009-11-25
Tried that already.

It doesn't work.

For whatever reason Writer can't open a PDF file.  

As I said earlier, I got Acrobat and I can read PDF's perfectly.

Thank you

---

### Post by 73ckn797 on 2009-11-25
Go to "Thread Tools" at the top of the page when viewing this thread and mark it as "Solved". This could be a help to others searching the forums.

---

