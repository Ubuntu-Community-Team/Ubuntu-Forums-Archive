---
title: "duplicate sources error (medibuntu)"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by al.adab on 2009-11-26
I keep getting the following error upon *sudo apt-get update*

[I]W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems[/I]

running apt-get update seems to correct it (the message no longer appears) but it doesn't. It appears again if I re-boot the machine and run the command above. 

Any idea?

---

### Post by coffeecat on 2009-11-26
Post the contents of your /etc/apt/sources.list file. Also, see if you have a /etc/apt/sources.list.d/medibuntu.list file. Post the contents of that as well if you have.

---

### Post by slakkie on 2009-11-26
Could you run the following:

```

# Let's find which repo's are duplicate:
sort /etc/apt/sources.list /etc/apt/sources.list.d/*.list | uniq -d

```

That will probably return some repository, let's say:
```

deb http://packages.medibuntu.org/ jaunty free
deb http://packages.medibuntu.org/ jaunty non-free

```

Then look in which files it is present:
```

grep "deb http://packages.medibuntu.org/ jaunty free" /etc/apt/sources.list /etc/apt/sources.list.d/*.list

```
That will output the files which contain this entry. Remove one of the entries (the entry, NOT the file!). Repeat where needed.

---

### Post by al.adab on 2009-11-26
OK, here's the content of my */etc/apt/sources.list*: 

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

---

### Post by al.adab on 2009-11-26
also found a */etc/apt/sources.list.d/medibuntu.list* : 

## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu - Ubuntu 9.10 "karmic koala"
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu (source) - Ubuntu 9.10 "karmic koala"

I'll now also try slakkie's solution...

---

### Post by al.adab on 2009-11-26
sorry slakkie can you please clarify the code you gave? Nothing much comes out of it :)

---

### Post by SaintDanBert on 2009-11-26
> **slakkie said:**
> Could you run the following:

```

# Let's find which repo's are duplicate:
sort /etc/apt/sources.list /etc/apt/sources.list.d/*.list | uniq -d

```

That will probably return some repository, let's say:
```

deb http://packages.medibuntu.org/ jaunty free
deb http://packages.medibuntu.org/ jaunty non-free

```

Then look in which files it is present:
```

grep "deb http://packages.medibuntu.org/ jaunty free" /etc/apt/sources.list /etc/apt/sources.list.d/*.list

```
That will output the files which contain this entry. Remove one of the entries (the entry, NOT the file!). Repeat where needed.


Could we possibly be more arcanely geek-ish?!?!?!

Why is this situation an ERROR and not a WARNING?  If I put the same folder onto my $PATH, the shell does not complain. What is the operational difference? 
[indent]Either apt or synaptic is looking for files. Here is a list of folders to search. OH! You want to waste some time searching twice? Okay, I'll let you know but keep looking.[/indent]

It is easiest to maintain line oriented text files if the record order does not matter. If duplicates are an issue:
[list]
[*] why can't apt or synaptic report the sources in some sorted order so that duplicates are easier to find?
[*] Why can't apt or synaptic report duplicates with some sort of text file "line number"?
[*] When you add repositories using the GUI, why doesn't it complain about duplicates?
[/list]

I remember when compiler error messages were "Syntax error. Halting." It is sad that we still have software with similar complaints. It is sadder still that the complaint likely exists for no real good reason.

Sigh,
~~~ 0;-Dan

---

### Post by al.adab on 2009-11-26
not sure I gotcha :) but then I'm neither a native-English speaker nor a geek, so you will forgive my doubts. 

I checked Software Sources, and unchecked the second line from the bottom. No error now, but have I done the right thing (in simple language, please)?

Thanks :)

---

### Post by slakkie on 2009-11-26
```

sort /etc/apt/sources.list /etc/apt/sources.list.d/*.list | uniq -d

```

Here you sort all the entries you have in your sources.list and other sources.list files (which are kept in the directory /etc/sources.list.d/). It will only print out duplicate records.

Just like in the example below:

```

deb http://packages.medibuntu.org/ jaunty free
deb http://packages.medibuntu.org/ jaunty non-free

```

These entries have more then 1 entry defined in your sources.list files.

Then you search in the files which files have that specific entry:

```

grep "deb http://packages.medibuntu.org/ jaunty free" /etc/apt/sources.list /etc/apt/sources.list.d/*.list

```

If it finds the line in a file it will output something like this:
```

/etc/apt/sources.list:deb http://packages.medibuntu.org/ jaunty free

```

It will probably find 1/2 files and you need to remove the medibuntu entries.

If it can't find anything, please do the following:

```

grep medibuntu /etc/apt/sources.list /etc/apt/sources.list.d/*.list

```

And report back :)

---

### Post by slakkie on 2009-11-26
> **al.adab said:**
> not sure I gotcha :) but then I'm neither a native-English speaker nor a geek, so you will forgive my doubts. 

I checked Software Sources, and unchecked the second line from the bottom. No error now, but have I done the right thing (in simple language, please)?

Thanks :)

Seems like you fixed it :)

---

### Post by ranch hand on 2009-12-19
I am finding this to be a problem for me in Jaunty.  I do not have medibuntu in my sources list at all and it is only in the Sources.d file once.
> 
## Medibuntu - Ubuntu 9.04 "jaunty jackalope"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

That is from the /etc/apt/sources.list.d/medibuntu.list.

There is a medibuntu.list.save but I assume that is not a file that is read by apt.

Looking in my other 9.04 install there is nothing in the sources.list.d at all.  I am thinking that I need to empty mine and update apt and then put it in my sources.list and update again.

This has not bothered me, been going on forever until I read this thread.  Now it is getting on my thungus.

---

### Post by coffeecat on 2009-12-19
> **ranch hand said:**
> Now it is getting on my thungus.

Can you provide a translation for this ignorant Limey? :p

That's a curious one - the Medibuntu issue that is. If I was in your position I'd be tempted to simply clear out /etc/apt/sources.list.d/ so that I wasn't bothered with the error. Since I only use Medibuntu for libdvdcss2 and w62codecs, and since they never get updated, so long as they're already installed it wouldn't bother me.

---

