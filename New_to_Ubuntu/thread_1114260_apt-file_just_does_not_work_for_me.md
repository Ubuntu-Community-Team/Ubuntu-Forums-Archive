---
title: "apt-file just does not work for me"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by ranch hand on 2009-04-02
I would be thrilled if someone would be so kind and condisending, stupe so low and be so bending (as my dad used to say) as to tell me how to run this.

I ran;
```

sudo apt-file update

```
and then;
```

apt-file list mypackage

```
The first (update) took several minutes on DSL but just said that it couldn't get the repos.  So I;
```

sudo apt-file purge

```
and got;
> 
W: Can't remove /var/cache/apt/apt-file/us.archive.ubuntu.com_ubuntu_dists_intrepid_Contents-i386.gz: No such file or directory
W: Can't remove /var/cache/apt/apt-file/us.archive.ubuntu.com_ubuntu_dists_intrepid_Contents-i386.gz: No such file or directory
W: Can't remove /var/cache/apt/apt-file/us.archive.ubuntu.com_ubuntu_dists_intrepid_Contents-i386.gz: No such file or directory
W: Can't remove /var/cache/apt/apt-file/archive.canonical.com_ubuntu_dists_intrepid_Contents-i386.gz: No such file or directory
W: Can't remove /var/cache/apt/apt-file/security.ubuntu.com_ubuntu_dists_intrepid-security_Contents-i386.gz: No such file or directory
W: Can't remove /var/cache/apt/apt-file/security.ubuntu.com_ubuntu_dists_intrepid-security_Contents-i386.gz: No such file or directory
W: Can't remove /var/cache/apt/apt-file/security.ubuntu.com_ubuntu_dists_intrepid-security_Contents-i386.gz: No such file or directory
W: Can't remove /var/cache/apt/apt-file/packages.medibuntu.org_dists_intrepid_Contents-i386.gz: No such file or directory
W: Can't remove /var/cache/apt/apt-file/ppa.launchpad.net_teamgnunet_ubuntu_dists_intrepid_Contents-i386.gz: No such file or directory

I looked at the referenced file and it had nothing in it (what a surprise) but the list is for more than the 2 repos that were listed in the failure to get message.

SO, just what have I failed to do?  AND, just how simple do you have to be to have this problem?

---

### Post by wolfen69 on 2009-04-02
i think what you are trying to do can be achieved by:
```
sudo apt-get clean && sudo apt-get autoremove
```

---

### Post by mister_pink on 2009-04-02
I don't think that helps!

I've used apt-file and never had any trouble. Normal useage shouldn't require sudo, but you're right about using it to update its database. 

Try updating the database again and seeing if there's any contents to the files then.

Oddly I just tried to update my database and was unable to download the file. Maybe a problem or change in the repos.

Edit, I tell a lie, was only some 3rd party repos that couldn't download. The rest worked. Doesn't help your problem much though.

---

### Post by ranch hand on 2009-04-02
HMMM, I thought that I was going to get a list of possible uninstalled packages.

That is why getting nothing was not a surprise as this is a new installation and I have been carefull about what I load as it is only a 10Gb drive so I don't have a lot of stuff on it but I do want it solid so I thought I would check.

From what I read here;
<http://www.debuntu.org/how-to-find-missing-packages-with-apt-file>
gave methe idea that this may be a handy tool.  Does not seem to work for me.

I was not sure of the age of that info so I checked synaptic and the packagewas there so I apt-get installed it.  I usually use apt-get as I trust it more and like the info on other packages (recomended and suggested) that you get along with the things you may have left on that should be removed.

Also, I you are on dialup, loosing your connection is less of a dissaster in apt-get.

---

### Post by mister_pink on 2009-04-02
apt-file just allows you to look into files that are included in a package, ie that will get installed when you use apt-get to install it. It also lets you search within all available packages for a certain file.

---

### Post by ranch hand on 2009-04-02
Well. I tried it again.

I first ran apt-get update.

Then apt-file update.  There are now 3 .gz files in /var/cache/apt/apt-file.  They are;
> 
packages.medibuntu.org_dists_intrepid_Contents-i386.gz

security.ubuntu.com_ubuntu_dists_intrepid-security_Contents-i386.gz

us.archive.ubuntu.com_ubuntu_dists_intrepid_Contents-i386.gz

So that looks good but without the 3rd party repos.

I guess it does work, may have had some problem with adress' that apt-get update fixed.

Looking at the man page for apt-file and concidering that I have a 10Gb HDD on this box (an old HP pavilion xt993)--is this apt of any real use?

I just down loaded the bugger because it sounded neat on the website I mentioned before and I really do like to play with my system now that I have one that you can play with.  I don't think I will learn much about it if I don't play with it.

This apt, right now, to me, seems a little silly.

---

### Post by unutbu on 2009-04-02
I have apt-file installed and find it useful, but rather infrequently. On a system where hard drive space is tight, I think it would be a prime candidate for removal.

Note that the info you could find through apt-file can alse be found by going to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Near the middle there is a "Search the contents of packages" searcher.

---

### Post by ranch hand on 2009-04-02
Well I'll be giggered, so there is.

I think I will remove the bugger.  I may put it on my big box when I get it here and play with it on one of my "play" installations and see what damage I can do, I mean see what it can do.

---

