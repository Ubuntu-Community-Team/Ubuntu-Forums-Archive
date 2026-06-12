---
title: "Facebook"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by tomxyz on 2009-02-14
Hello all,

I recently created an account on facebook. For some strange reason I don't see who is online (bottom right corner)
This is on my dapper drake installation using firefox. I updated firefox but the problem remained.
On my other more recent laptop I'm using kubuntu 8.10 with konquerer, there it just works fine. So I decided to install konquerer on my dapper system to see if that would do the trick. 
So with konquerer on dapper, when opening facebook I can't type, my keyboard doesn't work.I can't even login to see if it works.

Somebody with similar experience?

---

### Post by Paqman on 2009-02-14
Dapper is really, really old. Do you even get updates any more? If not your should seriously consider upgrading to 8.04 in order to keep receiving security updates.

You problem is probably due to the very old packages (for Flash?) that you'll have in Dapper. That's why it works on the newer system and not the old one. Try enabling the Backports repo if you haven't already. To enable Backports go to System > Admin > Software sources, check the Backports box and let it reload. Update Manager should pop up in the corner soon after.

---

### Post by Temposs on 2009-02-14
Dapper is old, but it is perfectly well supported until June of this year. No reason to upgrade until then, unless you're too unsatisfied with its performance.

Facebook does not use Flash except for ads, basically, so flash won't be your problem.

I really am not sure what the issue is here, though, as I don't use Dapper and I have never experienced that issue with facebook. It is likely an issue with how Firefox is handling the javascript.

So you installed Firefox 3.0.6 on Dapper and it still does the same thing?

---

### Post by ozbolt on 2009-02-14
You should really get in Hardy. Becouse you will be able to use Drapper till June, but what after that? Why ot updating now when you have problems?

---

### Post by HavocXphere on 2009-02-14
Try clearing the FF cache. Fixed some weird FF issues recently like that.

Afaik the chat thing also has to be specifically enabled. Maybe some cookie on your PC has the chat disabled.

Dunno...kind guessing here.

---

### Post by Carl H on 2009-02-14
I think what you're referring to are icons in the status bar at the bottom of the Firefox window?

You might have inadvertantly removed the status bar. Try View, Status Bar in Firefox. (Sorry, I'm guessing at the FF menu, cos I'm at work using IE).

---

### Post by tomxyz on 2009-02-14
thanks for all info,

Yes maybe I will have to update to a more recent version. But for this old laptop my dapper installation is perfect, everything works fine, now just because my wife want's to talk to her friends on facebook I'm facing a new challenge. The things you do for love ...:)

I have no experience with upgrading a whole system, can I do it from within adept? Or do I download a new iso file and let it run?

any input would be much appreciated ! grtz Tom

---

### Post by earthpigg on 2009-02-14
the latest version of pidgin, from getdeb.org, has facebook chat support ;)

---

### Post by Paqman on 2009-02-14
I believe Facebook's chat implementation is just a version of Meebo, so you might have better luck using that.

---

### Post by Temposs on 2009-02-14
If you plan to upgrade through adept, you will have to upgrade at least 3 times to get to the next supported version(7.10). That's because you can only upgrade to the next version when you do an upgrade.

I'd recommend to back up all the personal data onto an external storage unit and install whichever version you'd like(8.04 or 8.10, probably) by downloading the LiveCD iso and installing over the current install.

If you want to mess around with firefox a bit more on 6.06, try renaming the .firefox directory(Ctrl-H in nautilus to see hidden files) in the home directory(/home/youruserid) to .firefox2, and then restart firefox. It will automatically create a new .firefox directory when you restart, and you can see if that helps facebook.

You could also try manually installing Firefox 3.0.6, and see if that helps.

---

### Post by Paqman on 2009-02-14
> **Temposs said:**
> If you plan to upgrade through adept, you will have to upgrade at least 3 times to get to the next supported version(7.10). That's because you can only upgrade to the next version when you do an upgrade.


For normal releases you're right, but he's on an LTS release, and you can upgrade straight from one LTS to the next. So he could jump straight from 6.06 to 8.04 in one upgrade.

---

### Post by tomxyz on 2009-02-14
You are right Paqman, 

I or better Ubuntu developers just upgraded my system from 6.06 to 8.04 with just one click ! How awesome is that, with windows I would still be popping in cd's to install all correct drivers.

So my facebook problem is solved, my wife is happy, what else could a man want ? :guitar:

---

