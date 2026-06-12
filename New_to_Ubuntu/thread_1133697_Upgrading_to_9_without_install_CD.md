---
title: "Upgrading to 9 without install CD"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Roadbloc on 2009-04-23
I may be asking a really dumb question here, but is it possible to upgrade from 8.04 to 9 through the update manager? If not, is there a way i can upgrade using the install disk and not have to reinstall???

---

### Post by Menschenfresser on 2009-04-23
Sure! The update manager will notice there is a new distribution available and will offer you a new button to do it (you can also force this to update to e.g. a beta). However expirience tells (me) that is is wise to wait a couple of days, since the servers will be pretty hammered down and you will wait ages till you download everything :)

---

### Post by tom56 on 2009-04-23
The answer is in the release notes! :)

[http://www.ubuntu.com/getubuntu/releasenotes/904overview#Upgrading%20from%20Ubuntu%208.10](http://www.ubuntu.com/getubuntu/releasenotes/904overview#Upgrading%20from%20Ubuntu%208.10)
> 
To upgrade from Ubuntu 8.10 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.04' is available. Click Upgrade and follow the on-screen instructions.
In your case, you'll need to do this twice. Once to go from 8.04 to 8.10, then once more to go from 8.10 to 9.04. If I were you I'd make sure to restart inbetween the two, and remember to install any updates before you hit upgrade.

EDIT: I agree with the guy above though, leave it a couple of days. The servers will be under a lot of stress right now so it will take forever if you do it today.

---

### Post by Roadbloc on 2009-04-23
is it also possible to upgrade with the cd rather than a fresh install???

---

### Post by Linux_Kid66 on 2009-04-23
Sure! The update manager will notice there is a new distribution available and will offer you a new button to do it (you can also force this to update to e.g. a beta). However expirience tells (me) that is is wise to wait a couple of days, since the servers will be pretty hammered down and you will wait ages till you download everything, it's easy!

---

### Post by mikewhatever on 2009-04-23
> **Roadbloc said:**
> I may be asking a really dumb question here, but is it possible to upgrade from 8.04 to 9 through the update manager? If not, is there a way i can upgrade using the install disk and not have to reinstall???

I think the previous posters overlooked the fact that you were asking about upgrading from 8.04 to 9.04 directly. The answer to that is no. If you want to upgrade, you'd have to go 8.04->8.10->9.04. Furthermore, since 8.04 is an LST release, the update manager may not notify you of any newer non-LST releases, unless configured to do so. By default, the update manager in 8.04 is configured to notify of newer releases only when the next LST release is out.

---

### Post by j7%&lt;RmUg on 2009-04-23
> **mikewhatever said:**
> I think the previous posters overlooked the fact that you were asking about upgrading from 8.04 to 9.04 directly. The answer to that is no. If you want to upgrade, you'd have to go 8.04->8.10->9.04. Furthermore, since 8.04 is an LST release, the update manager may not notify you of any newer non-LST releases, unless configured to do so. By default, the update manager in 8.04 is configured to notify of newer releases only when the next LST release is out.

First the above poster is right about both of those things and second that is exactly why i didnt get the LTS (Long Term Support) version. Im going to wait till the afternoon of the 24th to download 9.04 since that is when the US is quiet so the servers will be less of a pain.

---

### Post by dawynn on 2009-04-23
If you're on 8.04 you are well advised to travel up the channel -- 8.10 first, then 9.04.  Make sure your system is running well with Intrepid (and no Hardy) before moving to Jaunty.

However, the advice about waiting a week or so is also very good.  Expect the repositories to be very busy for the next several days as many people are eagerly waiting to move to Jaunty.

---

### Post by Roadbloc on 2009-04-23
What exactly is the difference between an LTS and any other releases and does it effect the performance and stuff???

---

### Post by mikewhatever on 2009-04-24
> **Roadbloc said:**
> What exactly is the difference between an LTS and any other releases and does it effect the performance and stuff???

LST releases are supported for tree years on desktops, as opposed to 18 months for regular releases. Other then that, there is no difference.

---

### Post by dawynn on 2009-04-24
Generally, during development, an LTS angles more toward stability, and away from new technology.  Other releases try to add more and better features.  But the purpose of an LTS is "Long Term Stability" -- so they tend to shy away from adding more features in favor of creating a solid release.

Then again, on the anecdotal side, there's usually a few things I need to tweak to get my system working after every release, LTS or not.  So, each new release usually starts out a bit rocky for me (although Jaunty has been really smooth -- a lot better than the 8.10 nVidia debaucle).

---

