---
title: "Firefox Hanging"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by rlogan on 2009-04-27
Hi all

Just having a problem with Firefox hanging on one website only, well one that I can tell at this point. The website is [www.nrl.com](www.nrl.com) it does use flash and java from what I can tell.

What happens is the screen goes grey when this site is just about loaded, memory use is nothing abnormal. After sitting on the website for 5-10 seconds memory use goes through the roof. Basically Firefox will consume whatever ram is left, in my case 1.7Gb which causes the machine to stop responding.

This only became an issue from when the Firefox upgrade to 3.0.8, when the update to 3.0.9 came through I was hoping for a resolution but no joy !

I have removed flash-plugin-nonfree then cleared cache and reinstalled the same but no joy. I am considering removing Firefox and reinstalling but will leave to last resort.

Is anyone else having the same problem and if so could you please give some tips.

Many thanks in advance

Cheers

Richard

---

### Post by L'PIKL on 2009-04-27
Loaded the site no problems. And no hog on RAM usage or CPU. When I was on 8.10 I would have these issues all the time. hated to use FF, but since i upgraded to 9.04 and FF 3.0.9 its smoother now.

do you get the same errors with other browsers? might want to try the Opera 10 beta. to compare

Goodluck!

---

### Post by rlogan on 2009-04-27
Its really strange this one cos the site comes up just fine on the 3 other machines here on Jaunty. Its just my machine, which is a right pain !!!

It works on Opera 9.64 just fine, but its rendering of pages is rather painful by comparison to FF.

Just tried complete removal of FF and then reinstalled but no joy.

Considering putting in FF 3.5 and see how it goes, will mull that over a little before i do it though !!

Thanks for your reply

Cheers

Richard

---

### Post by Jakey_TheSnake on 2009-04-27
Try uninstalling and deleting your ~/.mozilla folder. 

I.e. /home/username/.mozilla (ctrl + H to view hidden folders).

Then reinstalling.

---

### Post by rlogan on 2009-04-27
Hey Jakey_The Snake

Your suggestion worked perfectly.

Will have to import my old bookmarks back in, but well worth the 5 mins work to do that.

Thanks heaps, you solved a really silly but very annoying issue for me.

Cheers

Richard

---

