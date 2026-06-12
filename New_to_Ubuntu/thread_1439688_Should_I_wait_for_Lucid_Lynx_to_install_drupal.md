---
title: "Should I wait for Lucid Lynx to install drupal?"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by wilnd on 2010-03-26
[COLOR=black][FONT=Verdana]Hello,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have happily installed Karmic Koala and am in the process of installing Drupal on LAMP (I plan to use it as dev platform and have my working site on the web).[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have now read many interesting posts about the soon-coming Lucid Lynx and am very eager to use it.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]To complicate things a bit, the next version of Drupal (7) is also out very soon and promises to be very nice as well.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]My question is aimed at persons who have the experience with both Ubuntu and Drupal and is the following:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Is it easier to wait until Lucid is out and then restart all my installs, or is the upgrade from Karmic to Lucid going to be such a breeze that I can start using my current system (aka Karmic + Drupal 6.16), then update to Drupal 7 when it comes out? (note that I am a complete beginner with no idea whatsoever about what I'm doing, and please bear with me!)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thank you All for your kind help, recommendations and advice![/FONT][/COLOR]

---

### Post by Paqman on 2010-03-26
As long as you're using standard packages from the Ubuntu repos there's no reason to think the upgrade shouldn't go like clockwork.

Up to you though really. You could stay on Karmic for another year quite happily if that's what you want.

---

### Post by wilnd on 2010-03-26
> **Paqman said:**
> As long as you're using standard packages from the Ubuntu repos there's no reason to think the upgrade shouldn't go like clockwork.
 
Up to you though really. You could stay on Karmic for another year quite happily if that's what you want.
 
Thanks for replying!
 
I am quite lazy (shame on me) and also weary of upgrades (because I have never done such thing before), so I guess my question is also motivated by the thought that starting from the beginning with longer-lasting OS and apps, I might delay upgrades until I am more familiar with Ubuntu.
 
I definitely do not realize the magnitude of the changes made during an upgrade such as Karmic to Lucid.

---

### Post by debian_andy on 2010-03-26
Since you are, as you said it yourself "lazy", I think it's easier to update Ubuntu or Drupal when they come out. The only think you have to do is to CLICK with the mouse button! With a new install, you will need to burn a CD which takes of course more effort.

If you choose to do a new install of Ubuntu, create the /var on a separate partition. When you install your LAMP and Drupal and you have to do a new install or reinstall Ubuntu in the future, you don't have to install Drupal (database,...) again. Saves you time to be .... more lazy ;)

---

### Post by kwacka on 2010-03-26
I've updated on one box, but had problems (background only,no keyboard/mouse access, so couldn't even change to another desktop) so did full install of 10.04. Other boxes are staying with 9.04/9.10 until full release of 10.04 comes out.

Another 'lazy' tip - when you come to upgrade/install, firstly go to Synaptic package manager, click 'file' and 'save markings as'. Ensure you tick the the 'save all changes' box and name/save the file wherever you want, e.g. /media/usb/MARKINGS

When you have reinstalled, upgrade/update your repositories, then open synaptic again, click on 'read markings', open your saved file and then 'Apply'.

This will collect from the repositories all the applications you have installed since your initial installion.

As advised earlier life is easier if you have a separate /var partition, and a separate /home partition - just don't format them when you install 10.04.  ;)

---

### Post by bodhi.zazen on 2010-03-26
> **wilnd said:**
> [COLOR=black][FONT=Verdana]Hello,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have happily installed Karmic Koala and am in the process of installing Drupal on LAMP (I plan to use it as dev platform and have my working site on the web).[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have now read many interesting posts about the soon-coming Lucid Lynx and am very eager to use it.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]To complicate things a bit, the next version of Drupal (7) is also out very soon and promises to be very nice as well.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]My question is aimed at persons who have the experience with both Ubuntu and Drupal and is the following:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Is it easier to wait until Lucid is out and then restart all my installs, or is the upgrade from Karmic to Lucid going to be such a breeze that I can start using my current system (aka Karmic + Drupal 6.16), then update to Drupal 7 when it comes out? (note that I am a complete beginner with no idea whatsoever about what I'm doing, and please bear with me!)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thank you All for your kind help, recommendations and advice![/FONT][/COLOR]

> **wilnd said:**
> Thanks for replying!
 
I am quite lazy (shame on me) and also weary of upgrades (because I have never done such thing before), so I guess my question is also motivated by the thought that starting from the beginning with longer-lasting OS and apps, I might delay upgrades until I am more familiar with Ubuntu.
 
I definitely do not realize the magnitude of the changes made during an upgrade such as Karmic to Lucid.

Unless you wish to perform some type of testing, you should not update either Drupal or Ubuntu until they are released as stable versions.

Server side, IMO, you want the applications (Drupal) and services (Apache) to be as stable as possible, more so if your interest is in Web design. Although there is some overlap, debugging broken Upstart scripts on a broken server is probably not what your are wanting to do, and such is a very real possibility if you update to 10.04 (speaking from personal experience with broken boot scripts on a server during 9.10 development, right around the second beta release).

Same with Drupal, I doubt you are wanting to have to re-write Drupal php code or fix the mysql database that was corrupted ...

From your posts I would suggest you wait for stable releases.

---

### Post by wilnd on 2010-03-26
> **Paqman said:**
> As long as you're using standard packages from the Ubuntu repos there's no reason to think the upgrade shouldn't go like clockwork. 
 
Thank you Paqman. Yes, this is the case, I am too green to do anything out of the beaten path! :D
 
> **debian_andy said:**
>  
If you choose to do a new install of Ubuntu, create the /var on a separate partition. When you install your LAMP and Drupal and you have to do a new install or reinstall Ubuntu in the future, you don't have to install Drupal (database,...) again. Saves you time to be .... more lazy ;)
 
Thank you Debian_andy, I will definitely use this advice! :D
 
> **kwacka said:**
>  Another 'lazy' tip - when you come to upgrade/install, firstly go to Synaptic package manager, click 'file' and 'save markings as'. Ensure you tick the the 'save all changes' box and name/save the file wherever you want, e.g. /media/usb/MARKINGS
 
When you have reinstalled, upgrade/update your repositories, then open synaptic again, click on 'read markings', open your saved file and then 'Apply'.
 
This will collect from the repositories all the applications you have installed since your initial installion.
 
As advised earlier life is easier if you have a separate /var partition, and a separate /home partition - just don't format them when you install 10.04. ;)
 
Thank you Kwacka, this is also very very interesting, I would definitely not have thought of that by myself (and have not finished my learners' readings by far!)
 
> **bodhi.zazen said:**
> Unless you wish to perform some type of testing, you should not update either Drupal or Ubuntu until they are released as stable versions.
(...) 
From your posts I would suggest you wait for stable releases.
 
Thank you Bodhi.zazen. Yes, this is the reason I was asking if I should wait, and sorry about this, I did not use enough precision and say "wait until stable versions are out". I definitely will not try to rewrite Drupal code (I'm green there too). I have enough work already with its simple CSS and PHP customization (being lazy does not help!).
 
Thank you All for you insight, advice and help, it is much appreciated!!!

---

