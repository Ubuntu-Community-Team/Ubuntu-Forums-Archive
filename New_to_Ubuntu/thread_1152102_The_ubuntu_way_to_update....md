---
title: "The ubuntu way to update..."
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Erom on 2009-05-07
So I noticed Open Office has a new version out today (3.1), and I notice that I've got 3.0 installed and the update manager doesn't detect any updates of the official package. This gives me an opportunity to get a sort of "ubuntu philosophy" question answered...

As far as I see it, I have two options:
1) Download the new open office from the OO website and install it (which I have *probably* been using ubuntu enough to do at this point)
2) Wait for the manager to auto-update me

What's the "right" way to update a program like this? Is there an "offical" ubuntu recommended way? Does most of the community do it that way or do a  lot of people do something else? If everyone usually waits for the official package, how long does this usually take (not impatient, just curious if this is a days/weeks/months thing or something that waited until the next version of ubuntu)?

---

### Post by kanikilu on 2009-05-07
Someone correct me if I'm wrong, but my understanding is that these kinds of programs won't be *officially* updated until the next release unless there are security updates.

For the impatient, there is a PPA for OOo that is more frequently updated:

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

---

### Post by Kareeser on 2009-05-07
Jaunty will stay with OpenOffice 3.0, unless it gets uploaded to the backports repository.

You can download the .deb file from OpenOffice.org, and install it that way. :)

Do you need directions for option #1?

Edit: kanikilu, curse you for typing faster :) Erom, kanikilu's option also works, but you'll have to add the PPA to your Software sources. Choose which one you'd like us to guide you towards.

---

### Post by bawilson2 on 2009-05-07
Installing from the website works but then you don't get any more updates.  Adding the PPA repositories or waiting for an official release would be better.

You can read about how to add the PPA repositories here:

[http://matt.bottrell.com.au/archives/350-OpenOffice-3.1-for-Ubuntu.html](http://matt.bottrell.com.au/archives/350-OpenOffice-3.1-for-Ubuntu.html)

---

### Post by Hospadar on 2009-05-07
Really whatever you want, generally releases go into the repos a little slower for two reasons:
1) package maintainers don't like to push out major versions except at major new ubuntu releases (i.e. 8.10-9.04), just to assure stability and so other packages can count on certain things being available
2) package maintainers may be slow/unpaid/busy

So if you want the latest, go ahead and grab it.  I would uninstall the ubuntu version first, and maybe check a site like getdeb to see if someone has built an ubuntu package (unless the original developer provides a .deb) because it will typically be a lot easier to install.

---

### Post by Niniel on 2009-05-07
What "everybody else" does is irrelevant. :)

I like to update only from the official repositories. Which can take a while, e.g. they only offered OO 2.x for 8.10 even though 3 was already out. Other updates, e.g. FF, usually just take a day or two.
The reason why I prefer to just install the official updates is a) I'm too lazy to install things any other way and b) this minimizes the chances of the update/s breaking something. I once installed a program from source that was, as I learned later, available from the repositories - so I installed the new version from there - and while everything worked fine, I had to delete both versions before I was able to upgrade to U9.04 because some libraries had some conflict or another.
That may not be the case with OO, but it could happen. I guess it all depends on how adventurous you are. If you just want things to work, I recommend to stick to the official updates.

---

### Post by mcduck on 2009-05-07
> **kanikilu said:**
> Someone correct me if I'm wrong, but my understanding is that these kinds of programs won't be *officially* updated until the next release unless there are security updates.

For the impatient, there is a PPA for OOo that is more frequently updated:

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

That is correct. The general rule in Ubuntu is that fter a version has been relesed all program versions are locked (as these are the versions that Ubuntu developers have tested together with everything else, and that they can guarantee to work without problems).

After release you only get updates for security reasons and to fix serious bugs, never just to add new features.

Enabling the backports repository will give you some extra updates, but not everything can be backported easily and safely so if you want to always have the latest versions of your programs you'll need to find some 3rd-party repository for that. Or to use some Linux distribution that has rolling releases..

So, the short answer is that OpenOffice is not going to be updated until next Ubuntu release. And the long answer is that if there's serious enough bugs it might get updated anyway, and perhaps it will be available in backports at some point. But most likely you'll just ned to find repository that provides latest OpenOffice packages for Ubuntu.

---

### Post by Erom on 2009-05-07
...

Whoa! I hadn't encountered the concept of a PPA yet. That's pretty awesome! I think I'll give a shot at figuring this stuff out myself, but thanks a ton for the offer of assistance. This ridiculously helpful forum is probably one of the best thing in ubuntu :)

Edit: too many exclamation points

---

### Post by donkyhotay on 2009-05-07
Linux is about choice, there is no 'right' way of doing things. Personally I wait for things to update automatically in the repos except for games. I like to play various FOSS games online some of which update often enough that they are obsolete in the repos compared to what others are running online (wesnoth being the biggest one). Because of this I download and install these games manually to guarantee my version is compatible with others for online play. Other games that don't update as often (such as bzflag and tremulous) I use the repos version since it generally remains compatible with online play. Non-games (such as open office) I never mess with as there I have never seen a reason to have the most bleeding edge version before it shows up in the repos.

---

### Post by Erom on 2009-05-07
Oh, I realise that having the "latest and greatest" version of something like OO is totally uncorrelated with actually getting work done unless there was some "killer app" feature I needed... I really only brought it up because it gave me an opportunity to ask the bigger picture question. Of course, now I'm probably going to have to install it just to try out a PPA, hah.

---

