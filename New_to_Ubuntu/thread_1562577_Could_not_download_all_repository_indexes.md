---
title: "Could not download all repository indexes"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by WeedaWolf on 2010-08-27
Hello

I have looked many places for this, and many solutions are provided. I think I have tried them all. Some advise going into a list called "etc/apt/list" or something like that. I thought I did that one right, but I'm not sure.

This is the message:

Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Could you help me on that? I may need step by step instructions.
I know how to use the lists and do stuff in the terminal, but...still a beginner.
Haven't been able to recheck for updates for over 100 days. :(

First person with right answer gets :popcorn: :D

---

### Post by skatinjj on 2010-08-27
> **WeedaWolf said:**
> Hello

I have looked many places for this, and many solutions are provided. I think I have tried them all. Some advise going into a list called "etc/apt/list" or something like that. I thought I did that one right, but I'm not sure.

This is the message:

Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Could you help me on that? I may need step by step instructions.
I know how to use the lists and do stuff in the terminal, but...still a beginner.
Haven't been able to recheck for updates for over 100 days. :(

First person with right answer gets :popcorn: :D

You can look [here]("https://answers.launchpad.net/ubuntu/+question/109200")

---

### Post by WeedaWolf on 2010-08-27
but where is ~bin? all my options to save it are the typical, namely Files, Documents, Pictures, etc. Is it a certain one of these? I'm not sure I can save it anywhere else. Maybe I need to move it?
Thanks

---

### Post by lhb1142 on 2010-08-27
> **WeedaWolf said:**
> Hello

I have looked many places for this, and many solutions are provided. I think I have tried them all. Some advise going into a list called "etc/apt/list" or something like that. I thought I did that one right, but I'm not sure.

This is the message:

Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Could you help me on that? I may need step by step instructions.
I know how to use the lists and do stuff in the terminal, but...still a beginner.
Haven't been able to recheck for updates for over 100 days. :(

First person with right answer gets :popcorn: :D

Dear Sir/Madam:

This has happened to me on a number of occasions. I recommend that you first effect a restart on your computer and try again.

If that does not work, wait an hour or so (or even a day), restart your computer and retry.

If that doesn't work either, I recommend that you download and install the Bleachbit applications - you download only one but there are actually two (Bleachbit is available in the Synaptic Package Manager).

Once they are installed, run them both. Then restart your computer and try again.

Waiting some time (they're probably updating the repository) and clearing the computer with the two Bleachbits has always worked for me.

Tip: you must set up both Bleachbits before you run them the first time; the setup, though it takes some time, is straightforward. Note that if an option you select gives a warning (it's slow or it will remove your bookmarks, whatever), HEED that warning and make sure that that particular option is NOT checked.

Another tip: when running Bleachbit (as root) you must, of course, enter your computer password. You need not enter the password when you run the plain Bleachbit - but, when you do so, you will see a couple of "errors." The way to eliminate these errors (which are really not important) is to run the plain Bleachbit from the terminal. You merely enter 'sudo Bleachbit' (without the quotes), enter your computer password, and the plain Bleachbit will open. When you run it that way, there will be no "errors."

It is important to always run both Bleachbits.

I find, in addition to solving the particular problem you are having (and I have had), running the Bleachbits at the end of every session ensures a 'clean' computer the next time you use it.

I hope this helps you solve your problem.

Lawrence H. Bulk

---

### Post by ankspo71 on 2010-08-27
Hi,
I checked out the repository you posted, and it appears that the repository is down for Lucid as seen here: [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/) (or they never had a repository for your version of Ubuntu.) Maybe they are updating the repository too.

Sometimes it is possible to use Karmic's PPA repositories even when you use Lucid because they might share the same files. To do this you can go to your Software Sources application, and change the repository so that it uses the Karmic repos instead:

System > Administration > Software Sources > Third Party Software > then change the one with the repository in question from Lucid to Karmic.

Be aware though, that if they never had a Lucid repository for that PPA, then they might have had a reason to not include it because of some  incompatibilities or something.

---

### Post by jtarin on 2010-08-27
When you have this problem check the address in your browser and see if it coincides with the measage.
The address you gave in your first post does return a 404. Go here and see why there is a 404.There is no Lucid directory.  [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/)

> #gnome-do
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
# deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) lucid main # **_disabled on upgrade to lucid_**

---

### Post by WeedaWolf on 2010-08-27
by the way, sorry, I forgot to tell, I have 10.04 lucid

---

### Post by jtarin on 2010-08-27
> **WeedaWolf said:**
> by the way, sorry, I forgot to tell, I have 10.04 lucid30 lashes across the naked eyeball with a wet noodle.:p

---

### Post by WeedaWolf on 2010-08-27
ankspo71: I believe you get the :popcorn:
I tried your method, and I have another problem.



Yay! Only this time it was a problem that I've had before I got the updating problem! Google keeps giving me its beta of Chrome to install. Even if I try to install it, it stays there, lol.

Ah...hopefully this doesn't come up again. 
Although, you are sure that changing it to "Karmic" means that it still gets ALL updates? Cuz I changed something before, and it worked, but my brother told me that I had taken out the thing that gives me the updates ;) lol.
So, you are totally sure that I'll get all updates? :D

---

### Post by ankspo71 on 2010-08-27
Hi,
For now you will be getting the updates that they provide for Karmic. I don't see why you wouldn't automatically be notified of any updates in this case, but you can always run the updater manually too. When they have a repository for Lucid up and running, I recommended that you switch to it just in case there are future differences in the packages or updates though. I'm glad the repository change helped because sometimes it does, and sometimes it doesn't.

---

### Post by WeedaWolf on 2010-08-27
K, thanks! Now I can get back to my computer after 100 days, :lolflag:lol. I'll be sure to change back, if it comes. Thanks :D :popcorn: :KS

):P

---

### Post by WeedaWolf on 2010-08-27
oh..how do i switch this to [SOLVED]?

---

### Post by ankspo71 on 2010-08-27
> **WeedaWolf said:**
> oh..how do i switch this to [SOLVED]?

You can click on "thread tools" near the top of this topic to mark it as solved.;)

---

