---
title: "Deleting files"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by InsaniaEx on 2010-06-03
Wanted to get Visual Boy Advance, so I download tar files for it, but was completely unsure how that worked,

I then found it was on Add/Remove programmes, so go to install, but am told it conflicts with installed programmes. So I delete (with the delete button) the archive the download came in, and that which was extracted. Still can't install. Did I delete incorrectly?

---

### Post by bodhi.zazen on 2010-06-03
hard to say.

close Synaptic

Open a terminal and run

```
sudo apt-get install foo
```

Where "foo" is the name of the package you are wanting to install.

---

### Post by BoneKracker on 2010-06-03
probably ran an 'install.sh' or the like, then deleted the distribution files before running the corresponding 'uninstall.sh'

if he did actually run an installer, he might have to download the package again from wherever he/she got it, and see if it contains an uninstaller

---

### Post by InsaniaEx on 2010-06-03
its VBA Express, how would I write that, it doesn't seem to work what ever way I do.

---

### Post by bodhi.zazen on 2010-06-03
Try :

```
sudo apt-get install vbaexpress
```

---

### Post by InsaniaEx on 2010-06-03
[FONT=monospace]That came back with:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vbaexpress: Depends: visualboyadvance but it is not installable
E: Broken packages

[/FONT]

---

### Post by oldos2er on 2010-06-03
Check Software Sources to make sure you have the universe repository enabled.

---

### Post by InsaniaEx on 2010-06-03
How do I go about doing that?

---

### Post by bodhi.zazen on 2010-06-04
> **InsaniaEx said:**
> How do I go about doing that?

See [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu)

You may need to simply update:

```
sudo apt-get update
sudo apt-get install vbaexpress
```

---

