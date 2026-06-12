---
title: "eeeXubuntu repos and upgrading"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by exzachtly on 2009-04-26
A former Mac fanatic here with my first post, so before anything else, I gotta say, I'm shaking with happy to have discovered Linux! Ask my poor wife who has to hear me tell the same tale over and over about how the peoples can be freed from poorly "supported" OS's that try to sell you things from within the key functions of the system (sick), lol

Upgrading eeeXubuntu:
So my understanding is that what I've loaded here is Xubuntu but with package choices that are best for this particular machine... So if I were to load a mountable USB with Jaunty, would I be able to choose to upgrade, and if so, would that alter the special EEE-friendly portions?

Repos:
Okay, I think some repo locations might have been moved for the version it's based on (Gutsy), because when I try to refresh or add packages in Synaptic, I get a long message telling me all these locations that it can't reach... Is there a way to figure out what they should be set to, and change them?
--
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.45 80]
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.45 80]
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
--

Thanks much!!

---

### Post by ikisham on 2009-04-26
I think Gutsy's support ended this month. So you should upgrade or maybe install a fresh copy of Jaunty or any other 'eee' system you may want.

---

### Post by exzachtly on 2009-04-26
Aha!  Thank you sir, that solves one mystery! So as to the upgrading, should I trust that the packages specific to EEE would remain unchanged if I let a ISO image do an automated upgrade, or should I perhaps contact the person who compiled this distro to see about reinstalling the EEE specific tweaks?

---

### Post by snowpine on 2009-04-26
I would recommend a backup of all personal files, followed by a fresh install of Xubuntu 9.04. eeeXubuntu was one of the very first eee-specific distros, at a time when "mainstream" Xubuntu did not run well on the eee. Asus eee pc's are well supported by the current version (Jaunty Jackolope), so the "tweaks" are no longer necessary.

Understand that even if you get the upgrade manager working, you'd have to upgrade sequentially 7.10->8.04->8.10->9.04. Therefore I suggest it's less hassle to back everything up and start fresh. 

By all means, test Xubuntu 9.04 first (as a live CD or USB) before making any final decisions. Good luck!

---

### Post by exzachtly on 2009-04-26
Thanks for the clarification!

I'll try a fresh load of Jaunty-ness and report back here for anyone else having a similar question.

---

