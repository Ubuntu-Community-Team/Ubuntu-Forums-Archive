---
title: "After using ubuntuzilla - loads of firefox problems"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by anothernewuser on 2010-05-23
This is a direct copy from a thread I put into the "ubuntuzilla" section of these forums ... I imagine thats bad form but ... my situation gets odder by the minute and I just noticed posts there can go weeks without answers.  If it's bad form sorry.

I have a new install of 10.04 ... the packaged Mozilla Firefox was annoying me so I followed the instructions to cut and paste and get access to the ubuntuzilla repository and now I may be worse off than I was...

I can't install any addons ... If I open the Add-ons screen the "Find Updates" button is greyed out so I couldn't update them if I could install them ... which I can't because of download error 228.

Is it normal that the "Find Updates" button is greyed out ...???

How do I install things like Ad Block or NoScript?

Please ... I haven't dealt with this for years and I have not much idea what to do here.

Other odd behaviour ... I think I'm getting bad reults from websearches ... I can't even google "ubuntuzilla" successfully at the moment.

A google search for ubuntuzilla turns up:


Sorry, The requested page was not found.
Back to the Shop

At the moment ... a few minutes ago it gave me a normal google results page but linked to some Apache welcome page ... and also it has returned a Yahoo 403 error message ... and just now a 404 error .... thats a lot of work for one little google search.

Just cleared browser history and now I can actually google "ubuntuzilla" and find what i;m looking for ... does any of this make sense?

And ... when I tried to edit this post I have to Save Changes twice to actually save them ...


Firefox ended up being completely paralyzed ... unable to load pages at all ... I have removed the firefox I got through ubuntuzilla ... removed the packaged firefox ... moved my profile ... reinstalled the packaged firefox added adblock through it and will use this set up to try and figure out how to get a firefox I can install addons to.  I had to do something I couldnt load any pages.

I can't imagine it was meant to function this way.

After a brief period of relative normality ... google searches are curently returning Yahoo 403 codes ... oh no ... now they're working again ... this ain't normal....

Any ideas whats happening?

---

### Post by cariboo on 2010-05-24
Depending on what version of Firefox you are using, some of the addons may not be compatible.

I would suggest you create a new firefox profile to see if that clears up the problem, open a terminal and type:

```
firefox -Profilemanager
```

If this helps, you can just transfer your bookmarks from the old profile to the new one.

---

### Post by anothernewuser on 2010-05-24
Well thats just it ... its a clean install from last night .. I deliberately reformatted my partitions to get rid of everything ... all I did since install was... add medibuntu ... add ubuntuzilla ... thats it ... and i've had trouble since ...


Hmmm ... I spose playing with Profiles cant hurt ... I'll give it a go.


Thanks for the suggestion.

---

### Post by wojox on 2010-05-24
> Is it normal that the "Find Updates" button is greyed out ...???

How do I install things like Ad Block or NoScript?


That's normal to be grayed out.

To install add-ons go to [https://addons.mozilla.org/en-US/firefox/](https://addons.mozilla.org/en-US/firefox/)

---

### Post by lovinglinux on 2010-05-24
> **anothernewuser said:**
> I can't install any addons ... If I open the Add-ons screen the "Find Updates" button is greyed out so I couldn't update them if I could install them ... which I can't because of download error 228.

You are not the only one experiencing this problem and I bet it has nothing to do with Ubuntuzilla. The thing is that Mozilla Add-ons site is currently under the process of being migrated to a new codebase. Lots of changes are gradually appearing on the site, but it will take a couple of weeks before it is completely finished. Meanwhile, things might get a little bit buggy. Just be patient and try to update again later.

> **anothernewuser said:**
> Is it normal that the "Find Updates" button is greyed out ...???

Yes. Unlike in Windows, Firefox is supposed to be updated from the official Ubuntu repositories, so that option is greyed out in order to prevent Firefox from downloading updates on it's own.

> **anothernewuser said:**
> How do I install things like Ad Block or NoScript?

Go to Mozilla Add-on site [https://addons.mozilla.org/en-US/firefox/](https://addons.mozilla.org/en-US/firefox/)

> **anothernewuser said:**
> Other odd behaviour ... I think I'm getting bad reults from websearches ... I can't even google "ubuntuzilla" successfully at the moment.

I would start by disabling ipv6.

See the fifth item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

---

### Post by anothernewuser on 2010-05-24
Well it seems to be working as it should at the moment ...

Could disabling ipv6 have solved all this?  how odd

Anywho ... have installed the latest version of AdBlock and NoScript...


Searches seem to be working ... particularly google searches had been turning up odd results...

Here's what I think I did ...

I removed firefox's ... both of them ...


I downloaded/extracted the latest firefox to the home directory ...

Used these commands from your site:

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s $HOME/firefox/firefox /usr/bin/firefox 

Which if I understand tells the system to look for firefox in home (?)

Along the way somewhere I disabled ipv6 ...


Anywho its working ...

I may try to undo some of this to get back on a more common firefox setup but at the moment I think I will try to just not be angry with my system.

Thank y'all for your help.


This oddness had me weirded out ... hope its gone.

I might very well have two copies of firefox ... off to check that now ... 

Again .. thanks for the help.  If it ain't, fixed I'll be back.


And as an aside .. I never thought it was caused by Ubuntuzilla either that's one thing that had me wondering.

For now this seems .... [Solved]

---

