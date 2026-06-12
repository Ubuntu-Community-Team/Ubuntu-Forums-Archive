---
title: "vanishing text"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by vividia on 2009-01-28
Since switching to intrepid, I've noticed that occasionally text disappears.  Its only in certain programs like Amarok and K3B.  Sometimes text shows up but for nano seconds.  I notice that these are K proggies.  Is there a compatibility issue?  I have Nvidia card.  Does that make a difference?  I'd really like to use Amarok again without using K.

---

### Post by egalvan on 2009-01-28
> **vividia said:**
> Since switching to intrepid, I've noticed that occasionally text disappears.  Its only in certain programs like Amarok and K3B.  Sometimes text shows up but for nano seconds.  I notice that these are K proggies.  Is there a compatibility issue?  I have Nvidia card.  Does that make a difference?  I'd really like to use Amarok again without using K.

From where does the text disappear? 

Amarok & k3b are both media players... do you lose text from ID tags?
Headings?

And it's refreshing to find someone with a bigger music collection than mine...

So how does Amarok handle the load?

Yup, I'm really a boy and I use Linux.

ErnestG

---

### Post by vividia on 2009-01-28
> **egalvan said:**
> From where does the text disappear? 

Amarok & k3b are both media players... do you lose text from ID tags?
Headings?

The only place text is stable is in the title bar.  It seems unstable in the file directory, on buttons, menus, everywhere but the title bar which is not actually part of the program but Gnome.


> And it's refreshing to find someone with a bigger music collection than mine...

So how does Amarok handle the load?

Call me paranoid but where did that information come from?  How much does it say I have?  It's probably outdated.  I just checked the music folder and I am currently sitting on 639 GB.

It handles it quite well.  When I was still using Windows I used a program called Media Monkey that had a few features I miss.  But Amarok was a better program overall.  And I'd like to be able to use it.

> Yup, I'm really a boy and I use Linux.

ErnestG

Well, thats not really surprising.  My signature was actually a reply to a classmate last semester when I was using my laptop to present a project to the class.  When i had finished the presentation, the very first question asked was if the OS I was using was Linux and if I trully was a girl.  That was how I replied. :D

---

### Post by niteshifter on 2009-01-28
Hi,

639GB!!! That is impressive. Here I thought my 220GB had me running with the big dogs.

Anyways, K apps use the Qt toolkit for the interface, "pure" GNOME apps use GTk. I'm not a KDE / Qt expert (I'm a GNOME guy) at all but qt3-qtconfig / qt4-qtconfig (depending on which Qt version you have, available in the repos) can be useful in fixing problems like this.

---

### Post by vividia on 2009-01-28
> **niteshifter said:**
> Hi,

639GB!!! That is impressive. Here I thought my 220GB had me running with the big dogs.

Anyways, K apps use the Qt toolkit for the interface, "pure" GNOME apps use GTk. I'm not a KDE / Qt expert (I'm a GNOME guy) at all but qt3-qtconfig / qt4-qtconfig (depending on which Qt version you have, available in the repos) can be useful in fixing problems like this.

Yeah... its a lot.  I have it on a 1TB drive and I'm afraid I'm going to need a bigger one.  And its not flacs as some people would say.  They're mostly mp3s and oggs.  Slowly becoming more oggs. ;)

I have intrepid and I'm not sure if which version I have nor where to look to find out.  

Can I fix this in terminal?

---

### Post by vividia on 2009-01-28
I did try to install qt4-config using just sudo apt-get install and it said that what I had was the newest so that was a dead end.

I did take some screenshots because I don't think I adequately explained.

[http://www.box.net/shared/gjb0rkqnmq](http://www.box.net/shared/gjb0rkqnmq)
[http://www.box.net/shared/5111qvbltx](http://www.box.net/shared/5111qvbltx)
[http://www.box.net/shared/ct5ul6c2mc](http://www.box.net/shared/ct5ul6c2mc)

---

### Post by niteshifter on 2009-01-28
Hi,

As you said - and we see from the screenshots - that fonts / text are missing, it's a fonts problem I think. Have you tried via qt4-qtconfig changing fonts / font sizing?

The configuration tool is invoked via terminal:
```
qtconfig-qt4
```

And as I wrote earlier I'm no KDE/Qt expert, my solution for the few KDE apps I use is to run KDE virtual :) However, back in my days of using Edgy I had a problem similar to yours. Not missing text, just rendered badly. Playing with fonts in qtconfig got me past it.

---

### Post by vividia on 2009-01-29
Ok.  I have to apologize.  I really do not know what I'm doing at this point.  I can get qtconfig going but now I don't know what I should fix.

---

### Post by niteshifter on 2009-01-29
Hi,

Step 0 - Invoke qtconfig via terminal:
```
qtconfig-qt4
```

Step 1 - Click the Fonts tab (see attachment Step-1-Qt Configuration.png)

Step 2 (see attachment Step-2-Qt Configuration.png) First, write down what is showing for Family, Style and Size (should you need to restore them), then experiment: selecting a different "Family" (font name) / Style / Size. Change one at time, save and exit qtconfig, and try your troublesome app(s).

---

### Post by egalvan on 2009-01-29
> **vividia said:**
> Since switching to intrepid, I've noticed that occasionally text disappears. 

Before you "switched to Intrepid", what were you running?

Did you have any text problems then?

What was the compelling reason to switch to Intrepid?

Have you installed the kde-core?

I have Gnome and KDE installed on all my Linux machiens, and a few also have XFCE.

I normally run Gnome, but like to play with KDE.

Oh, that's KDE 3.x.x, not 4.x.x.

Only my play machine has anything higher than 8.04.x

---

### Post by spegru on 2009-01-29
I also had this problem (disappearing text in menus etc) in Intrepid and with a nVidia graphics card - 
It seems to be caused by a bug in the nVidia driver.
It works fine with the opensource one although you cannot do compiz with that

I suggest you try disabling the proprietary nVidia driver via: system>administration>hardware drivers

spegru

---

### Post by vividia on 2009-01-30
> **egalvan said:**
> Before you "switched to Intrepid", what were you running?

I wiped out Hardy and installed Intrepid.  That would be the definition of switching rather than upgrading.  Upgrading is more hassle than its worth.

> Did you have any text problems then?

No.  I had no text problems then.  Hence I said "since switching to Intrepid".  Since is the operative word here.

> What was the compelling reason to switch to Intrepid?

Have you installed the kde-core?

First, I wanted to try it out.  I can always go back to Hardy if I want to or try out Elive Gem.  Second, I had Gnome and KDE last time and it actually caused more problems than I knew how to solve like sound, keyboard... I was starting to go through what felt like a total system failure but in slow motion with Compiz Fusion effects.  Like being in a car crash.  Not watching it.  In it.

> I have Gnome and KDE installed on all my Linux machiens, and a few also have XFCE.

I normally run Gnome, but like to play with KDE.

Oh, that's KDE 3.x.x, not 4.x.x.

Only my play machine has anything higher than 8.04.x

Should I be happy for you and all your "machiens"? ;)

---

### Post by vividia on 2009-01-30
> **spegru said:**
> I also had this problem (disappearing text in menus etc) in Intrepid and with a nVidia graphics card - 
It seems to be caused by a bug in the nVidia driver.
It works fine with the opensource one although you cannot do compiz with that

I suggest you try disabling the proprietary nVidia driver via: system>administration>hardware drivers

spegru

Thanks for the tip!  I followed your advice and went to the hardware drivers and found out that it was only using the 96 driver and not the recommended 177.  Not sure how that happened.  I took 96 off, installed 177, rebooted and everything was pristine!

Thank You Again!!!

---

