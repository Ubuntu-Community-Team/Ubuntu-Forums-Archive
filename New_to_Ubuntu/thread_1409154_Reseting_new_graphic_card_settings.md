---
title: "Reseting new graphic card settings"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by Earl-Grey on 2010-02-17
Please could somebody tell me if there is an easy way to get my graphics card settings back to how it was on a fresh Ubuntu installation, without deleting everything and re-installing Ubuntu?

I have a simple ATi Xpress 200m graphics card and it was working fine with the original Ubuntu 9.10 install. I could run all the compiz effects on maxim  (although I prefer to keep it simple) and wasn't having any trouble with my graphics until I tried to play Urban Terror the FPS game.

The screen size was wrong and I thought it was because I didn't have the correct drivers. So I followed this guide > [URL="http://sidrit.wordpress.com/2008/08/10/enabling-desktop-effects-for-ati-radeon-xpress-200m-on-ubuntu-hardy-heron/"]here
[/URL] 
Rebooted and now I can't use any of the compiz effects at tall.

Basically, is there an easy was to delete the stupid thing I did and get back to the original settings?

---

### Post by mikewhatever on 2010-02-17
I'd say not having Compiz is a worthy trade off for having the correct screen resolution, but it's up to you.

remove the installed driver with:

sudo apt-get purge xorg-driver-fglrx

By the way, here is the correct link:

[http://sidrit.wordpress.com/2008/08/10/enabling-desktop-effects-for-ati-radeon-xpress-200m-on-ubuntu-hardy-heron/](http://sidrit.wordpress.com/2008/08/10/enabling-desktop-effects-for-ati-radeon-xpress-200m-on-ubuntu-hardy-heron/)

---

### Post by Earl-Grey on 2010-02-17
> **mikewhatever said:**
> I'd say not having Compiz is a worthy trade off for having the correct screen resolution, but it's up to you.

remove the installed driver with:

sudo apt-get purge xorg-driver-fglrx

By the way, here is the correct link:

[http://sidrit.wordpress.com/2008/08/10/enabling-desktop-effects-for-ati-radeon-xpress-200m-on-ubuntu-hardy-heron/](http://sidrit.wordpress.com/2008/08/10/enabling-desktop-effects-for-ati-radeon-xpress-200m-on-ubuntu-hardy-heron/)

Thank you very much for the help.

I did have the correct screen resolution, but for some reason when I played that game only half of the screen would show. I think it could have been because I am using two monitors.

I will see if I can get it back to how it was.

Thank you again.

---

### Post by halitech on 2010-02-17
the link you pointed to was for Hardy (8.04) when there was a proprietary driver you could use for your card. Now, the only driver you can use is the opensource driver which may not work as well with 3d games.

---

### Post by Earl-Grey on 2010-02-17
> **halitech said:**
> the link you pointed to was for Hardy (8.04) when there was a proprietary driver you could use for your card. Now, the only driver you can use is the opensource driver which may not work as well with 3d games.

Are you saying that the only driver I can use is the opensource one or is there a 9.10 ATi version ?

---

### Post by halitech on 2010-02-17
that is correct. ATI dropped support for your card back about the same time 9.04 came out but it only works in 8.04 and 8.10 so unless you want to revert to 8.04 then you only have the open source driver to use.

---

### Post by Earl-Grey on 2010-02-17
> **halitech said:**
> that is correct. ATI dropped support for your card back about the same time 9.04 came out but it only works in 8.04 and 8.10 so unless you want to revert to 8.04 then you only have the open source driver to use.

I didn't know that. It's a shame that they dropped supporting my card.

Thanks :popcorn:

---

### Post by halitech on 2010-02-17
you aren't alone, they dropped support for everything below the HD2400 series which really upset a lot of people. Combine that with Xorg making changes to the way xorg works and you have alot of really upset people, me included with an X12500

---

