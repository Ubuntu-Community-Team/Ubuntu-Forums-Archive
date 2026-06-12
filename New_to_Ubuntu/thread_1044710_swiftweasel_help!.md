---
title: "swiftweasel help!"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by LeadHop on 2009-01-19
Firefox has been quite troublesome lately so i re-installed swiftweasel.  problem is, I forgot how to set it into my profile!

what i mean is that i don't remember how to set it so that the icon shows up under applications > internet > swiftweasel. 

I've all the files in a folder on my desktop.  what directory do i have to move it to so that i can use it like firefox?  Also, is there anyway i can move firefox's settings over to swiftweasel?  TIA!

---

### Post by LeadHop on 2009-01-19
to clarify: I want to have swiftweasel under applications > internet like firefox.  I'd also want to have it in the laucher with the swiftweasel logo. I had this with gutsy, but it seems more difficult with ibex.  thanks again!

---

### Post by oldos2er on 2009-01-19
You can create a launcher via the menus System, Preferences, Main menu, New Item. Or right-click on your desktop and choose Create Launcher.

---

### Post by LeadHop on 2009-01-20
ah, just like linux to have a simple answer.  

I have a question though - will doing this allow for swiftweasel to receive updates like firefox?  I just don't know if i installed it properly since I can't find a swiftweasel svg to set as the icon though it did it by itself the last time i installed in gutsy.

---

### Post by Yellow Pasque on 2009-01-20
> will doing this allow for swiftweasel to receive updates like firefox?
If you add the swiftweasel repository to your sources, you'll get updates for it along your other Ubuntu updates.

You probably downloaded the source (.tar.gz) when you want a .deb package. Currently, the latest .deb is Swiftweasel 3.03 for Hardy. I'm waiting for 3.05 Intrepid .debs too :\
As I wrote in another thread:
> stickk (the maintainer) had been battling health problems for the last few months (pancreatitis, gall bladder surgery). He also had trouble getting the mozilla suite to build on Intrepid for a bit. IIRC, he also lost the .deb scripts he was using to build. Note that the 3.05 tarball has been on the sourceforge download site for a bit now, so it'll probably be very soon when 3.05 .deb's appear.

---

### Post by LeadHop on 2009-01-20
> **Temüjin said:**
> If you add the swiftweasel repository to your sources, you'll get updates for it along your other Ubuntu updates.

You probably downloaded the source (.tar.gz) when you want a .deb package. Currently, the latest .deb is Swiftweasel 3.03 for Hardy. I'm waiting for 3.05 Intrepid .debs too :\
As I wrote in another thread:

oy... so we're gonna have to wait it out then?  any idea if i can reinstall the new .deb when it comes out and keep all my previous settings?

---

### Post by zika on 2009-01-20
3.0.5 is available already [http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=650372](http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=650372) ... 30-dec-2008.

---

### Post by Yellow Pasque on 2009-01-20
> **zika said:**
> 3.0.5 is available already [http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=650372](http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=650372) ... 30-dec-2008.
Those are source tarballs. Most users probably don't want to build Mozilla from source.

---

### Post by zika on 2009-01-20
> **Temüjin said:**
> Those are source tarballs. Most users probably don't want to build Mozilla from source.
as far as my memory serves me, and it rarely fails due to good error correction provided by DNA, I've just unpacked these executables at the beginning of this year in already prepared directory and I have been using SwiftWeasel(as a backup to Minefield nightly trunks)from there merrily ... ;) 
the whole point of SwiftWeasel is that it is compiled optimized for a particular platform. so it's not source for sure ... ;)

---

### Post by LeadHop on 2009-01-20
that's not a .deb file though...

---

### Post by egalvan on 2009-01-20
> **zika said:**
> as far as my memory serves me, and it rarely fails due to good error correction provided by DNA, I've just unpacked these executables at the beginning of this year in already prepared directory and I have been using SwiftWeasel(as a backup to Minefield nightly trunks)from there merrily ... ;) 
the whole point of SwiftWeasel is that it is **compiled optimized for a particular platform. so it's not source for sure **... ;)

I have no experience in this, but can't the sources include the compile-time optimizations? Or any other info needed for optimizations?

---

### Post by zika on 2009-01-20
> **egalvan said:**
> I have no experience in this, but can't the sources include the compile-time optimizations? Or any other info needed for optimizations?
they might but I do not think in this case. author talks about compiling ... it worked for me ... ;)

---

