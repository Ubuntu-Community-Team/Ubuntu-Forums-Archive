---
title: "Upgrades not recognized"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by bonsaitree on 2009-05-06
My update manager isn't recognizing the 9.04 upgrade and I can't figure out why.  I've tried forcing it to search for upgrades and updates in terminal.  I've poured through the forums trying to find someone with a similar issue to no avail.  I would just dl it and upgrade and be done, but my burner hasn't been working right for a while and so I don't want to mess with trying to burn and iso.  

Distribution is 8.04.2 "hardy"
Hardware shouldn't be the issue as it all exceeds requirements.
Update manager did recently update or upgrade a couple packages (I can't remember which) but it also said that not all were available or something so I did a "partial install".

Any help would be appreciated.  Thanks :D

---

### Post by mprince on 2009-05-06
Under Administration> Software sources> Updates tab 
make sure you select 'Normal Releases' where it says Show new distribution releases.

---

### Post by Didius Falco on 2009-05-06
> **bonsaitree said:**
> My update manager isn't recognizing the 9.04 upgrade and I can't figure out why.  I've tried forcing it to search for upgrades and updates in terminal.  I've poured through the forums trying to find someone with a similar issue to no avail.  I would just dl it and upgrade and be done, but my burner hasn't been working right for a while and so I don't want to mess with trying to burn and iso.  

Distribution is 8.04.2 "hardy"
Hardware shouldn't be the issue as it all exceeds requirements.
Update manager did recently update or upgrade a couple packages (I can't remember which) but it also said that not all were available or something so I did a "partial install".

Any help would be appreciated.  Thanks :D

You can't skip a release by upgrade, other than for the Long Term Support Releases. 9.04 isn't an LTS release.

What you'll have to do is upgrade to 8.10, make sure you have all the updates and then upgrade from there to 9.04.

It'd probably be easier, and certainly a lot less downloading and time-consuming to just back up your data and do a fresh install. A lot of people (and I'm one of them) prefer a fresh install because there is less chance of problems.

You could get RemasterSys and back up your whole install to a bootable CD or DVD and just boot with that and copy your data back to your install after it was set up.

Here is a link to the RemasterSys web site, where you can get the repository information to add to your sources list.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

On Edit: You could use Unetbootin to burn the 9.04 iso to a bootable USB stick, if you have one of those, and if you have a second USB stick, or room on your hard driveto make a partition just big enough to hold your data, you could do the whole thing without any cds.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I hope this helps... If you still prefer to do it the Upgrade/Update/Upgrade way, let us know.

---

