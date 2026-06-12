---
title: "Download debs for install offline?  Best place to get them?"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by dBuster on 2009-03-31
Not sure where to post this so I am giving it a shot in the beginner area and it can more than welcome be moved accordingly if needed.

I am going to be installing 8.10 on my sisters machine this weekend.  I just learned though that they have lost their internet connection temporarily due to the economic times.  I want to be able to bring with me a cd comprised of a variety of debs.  Mainly I am needing to include Scribus for sure but I am sure I would be looking for others as well. 

Any recommendation for the Scribus deb download?  

Any recommendations for other popular debs for me to take along?  They are not heavy users but are internet users.  I am looking for at least Gnome Do or AWN for sure.   

I believe that Open Office is standard install so I do not need to worry about that, if I am wrong correct me.  

I am sure that once they have their internet connection again I will be back out there to walk them through the updates.  Thanks in advance...

---

### Post by aeiah on 2009-03-31
whilst you can get debs from packages.ubuntu.com, getdeb.net and the software's own website, that isn't the hard part. if you arent careful you'll end up going round in circles because your package needs a dependency that you havent got.. and then your dependency will need a dependency, and and and it can be a nightmare :p

the best thing to do would be to create a virtual machine and install all the stuff you want and either use aptoncd to create an iso repository or copy the apt cache of all the downloaded .deb files it grabs and stores when you're installing stuff. you can then use all these files when you install the real ubuntu on your sisters pc.

the second best thing would be to grab the ubuntu dvd, as this has a lot more software on it and just install from there. for things like gnome-do that isnt in the repo, you'll need to manually download it from the site and make sure you have all of its dependency packages (if any)

be on guard for your sister's pc needing a graphics card driver. fingers crossed she's got onboard intel graphics.

---

### Post by hyper_ch on 2009-04-01
.deb from repos in your sources list are stored in /var/cache/apt/archives

So you can just install things from there again (for what's in the repos)

---

### Post by dBuster on 2009-04-01
> **aeiah said:**
> whilst you can get debs from packages.ubuntu.com, getdeb.net and the software's own website, that isn't the hard part. if you arent careful you'll end up going round in circles because your package needs a dependency that you havent got.. and then your dependency will need a dependency, and and and it can be a nightmare :p

the best thing to do would be to create a virtual machine and install all the stuff you want and either use aptoncd to create an iso repository or copy the apt cache of all the downloaded .deb files it grabs and stores when you're installing stuff. you can then use all these files when you install the real ubuntu on your sisters pc.

the second best thing would be to grab the ubuntu dvd, as this has a lot more software on it and just install from there. for things like gnome-do that isnt in the repo, you'll need to manually download it from the site and make sure you have all of its dependency packages (if any)

be on guard for your sister's pc needing a graphics card driver. fingers crossed she's got onboard intel graphics.

Gosh now I wish I could remember if she has a dvd drive on that pc...  hmmf memory is just not there for me now.  argh!  

So the DVD has more software?  From the website it looked and sounded like it was just language paks were the difference...

Any good links to assist me with doing the vm and setting up aptoncd...

Anyone have any ideas of any good apps to include on this cd???

---

### Post by dBuster on 2009-04-01
Any further ideas?

---

### Post by lkraemer on 2009-04-01
You might want to have a look at this:
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

It should make it easy.

lkraemer

---

### Post by egalvan on 2009-04-01
These are just a bit dated, and need a DVD, but it's very useful..

I have the repo's for 8.04 & 8.10...


[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=distrowatch](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=distrowatch)


and shipping is fairly quick, mine arrived in less than a week.

---

