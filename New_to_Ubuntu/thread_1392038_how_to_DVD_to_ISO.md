---
title: "how to DVD to ISO"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by kowalsky on 2010-01-27
hi all,
I'm interested in the best software for ubuntu 9.10 that can burn a ISO image of a DVD,
thanks,
kowalsky

---

### Post by cotcot on 2010-01-27
Your question is confusing. In the title you ask the opposite of what you ask in the text. 

You can make a DVD compatible structure from nearly any video using Devede (devede is in the repositories). With Devede you can make an iso and burn it to a DVD with whatever burning app (Brasero, K3B, ...). Devede has a buring option as well.

---

### Post by J V on 2010-01-27
I'm pretty sure you can do it with dd...

something like this? (dont try it until someone confirms it works)
```
sudo dd if=/mnt/cdrom of=~/cd.iso
```

---

### Post by Devi1903 on 2010-01-27
Simplistic way? Right click on dvd mounted on desktop and click copy disc

---

### Post by J V on 2010-01-27
d'oh xD

Does this create an image or only copy the files?

---

### Post by oldos2er on 2010-01-27
It creates an *.iso image, which you can then burn.

---

### Post by J V on 2010-01-27
awesome, should have known ubuntu would have something to do that built in... as always :P

---

### Post by warfacegod on 2010-01-27
> **Devi1903 said:**
> Simplistic way? Right click on dvd mounted on desktop and click copy disc

Brasero now puts them in .toc format not .iso, unfortunately.

---

### Post by J V on 2010-01-27
iat ftw :P

Can't you tell brasero to save as iso? I mean cmon, its gotta have that somewhere... why is brasero going the way of magiciso anyway? stupid one-program-only images xD

---

### Post by Devi1903 on 2010-01-27
Puts in .toc for audio CDs, the rest usually .iso

---

### Post by Devi1903 on 2010-01-27
but anyone who wants to add in the option for doing .iso for audio cd would be great.

---

### Post by warfacegod on 2010-01-27
> **J V said:**
> iat ftw :P

Can't you tell brasero to save as iso? I mean cmon, its gotta have that somewhere... why is brasero going the way of magiciso anyway? stupid one-program-only images xD

I tried to help someone the other day with getting Brasero to do .iso, no dice. Mine won't do it either. Not that I care if mine works.

---

### Post by chrisinspace on 2010-01-27
> **cotcot said:**
> Your question is confusing. In the title you ask the opposite of what you ask in the text. 

Like cotcot, I'm confused.  Do you want to take a physical DVD and create an .iso image or start with an .iso file and burn it to a DVD?

For ripping DVD to .iso, I like k9copy.  It's a KDE application, but it works fine in Gnome.

---

### Post by llawwehttam on 2010-01-27
Try gnomebaker. Its in the repos and I've found it much nicer and cleaner to use than brasero. Creates iso's too under the 'tools' menu.

```
sudo apt-get install gnomebaker
```

It refers to 'burning' as 'baking' so don't be confused.

---

### Post by warfacegod on 2010-01-27
> **Devi1903 said:**
> but anyone who wants to add in the option for doing .iso for audio cd would be great.

Try acetoneiso.

---

### Post by oldos2er on 2010-01-27
> **warfacegod said:**
> Brasero now puts them in .toc format not .iso, unfortunately.

Brasero creates *iso files for me, from the right-click 'Copy disc' function.

Edit: And if you open the full program, choose 'Disc copy'.

---

### Post by Devi1903 on 2010-01-27
yer basero needs some work done on it

---

### Post by warfacegod on 2010-01-27
> **Devi1903 said:**
> yer basero needs some work done on it

I have virtually every multimedia whatnot and thingamabob, restricted or otherwise that could possibly be needed to do an .iso rip. I just put an Ubuntu install disc in my wife's computer and hers refuses to rip as .iso as well. Apparently, it's a 9.10 thing because this was never a problem, for me, in 9.04 and back. Again though, I don't care. I don't use it and I just haven't bothered to remove it yet.

---

### Post by llawwehttam on 2010-01-27
Just remembered I did a blog on gnomebaker recently.
[http://llawwehttam.blogspot.com/2010/01/best-cddvd-writer-for-linux.html](http://llawwehttam.blogspot.com/2010/01/best-cddvd-writer-for-linux.html)

---

### Post by oldos2er on 2010-01-27
> **warfacegod said:**
> I have virtually every multimedia whatnot and thingamabob, restricted or otherwise that could possibly be needed to do an .iso rip. I just put an Ubuntu install disc in my wife's computer and hers refuses to rip as .iso as well. Apparently, it's a 9.10 thing 

Again, this works fine for me in 9.10. After you right-click and choose 'Copy disc', click the drop down menu under 'Select a disc to write to' and click 'Image File'.

---

### Post by Devi1903 on 2010-01-27
yer fine for me too. If the easiest way to do it and works fine. No reason to use other programs really.

---

### Post by halitech on 2010-01-27
If you have a dvd that is over 4.4gig, K9copy will shrink it down to fit on a normal dvd or allow you to rip it in avi format.

---

### Post by kowalsky on 2010-01-27
thanks to all,
I will re-read all answers; still if it was not clear:

I have a dvd, I want to get an iso file, the image of that dvd. Usually I need to rip it first, however, I do not want to encode it, I just want to pass the one folder with the VOB files and whatnot to some app that puts together one big *.iso file.

thanks,
kowalsky

---

### Post by halitech on 2010-01-27
k9copy

---

### Post by running_rabbit07 on 2010-01-27
I haven't seen the Copy selection in the menu since moving up from Jaunty. When I put a DVD in, it is not listed. Is there anything special to install to get that option?

Edit: also when I go to Brasero and try to copy to file it won't allow me to do anything.
> **warfacegod said:**
> I have virtually every multimedia whatnot and thingamabob, restricted or otherwise that could possibly be needed to do an .iso rip. I just put an Ubuntu install disc in my wife's computer and hers refuses to rip as .iso as well. Apparently, it's a 9.10 thing because this was never a problem, for me, in 9.04 and back. Again though, I don't care. I don't use it and I just haven't bothered to remove it yet. Same here.

---

### Post by warfacegod on 2010-01-27
> **oldos2er said:**
> Again, this works fine for me in 9.10. After you right-click and choose 'Copy disc', click the drop down menu under 'Select a disc to write to' and click 'Image File'.

Yup, been there, done that, it makes a .toc

---

### Post by kowalsky on 2010-01-27
Ok,
many thanks to everybody.
I've put the dvd in the dvd unit, some manager showed up, selected Brasero and then I just had to select *.iso and type the name of the iso file (at the end of some path).

I suppose, for any other dvd I should do the rip, and then select that folder where the ripped version goes and then turn it into iso file.


Everything works just fine,
Thanks again,
kowalsky

---

### Post by airtonix on 2010-01-27
> **warfacegod said:**
> Brasero now puts them in .toc format not .iso, unfortunately.

[IMG]http://www.ubuntu-pics.de/bild/40070/screenshot_002_iSNae2.png[/IMG]

change the filetype in the properties file chooser dialog window.

---

### Post by warfacegod on 2010-01-27
> **airtonix said:**
> [IMG]http://www.ubuntu-pics.de/bild/40070/screenshot_002_iSNae2.png[/IMG]

change the filetype in the properties file chooser dialog window.

See post #26.

---

### Post by ThePinkWitch on 2010-01-27
> **halitech said:**
> If you have a dvd that is over 4.4gig, K9copy will shrink it down to fit on a normal dvd or allow you to rip it in avi format.

oh cool..I've been using DVD Shrink thru WINE. it works well but good to know a linux program that does it. Thanks for the info :)

---

