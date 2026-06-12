---
title: "Kdenlive wont reinstall-I broke it!"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by MisFitt on 2010-04-14
I watched a video on You Tube about upgrading Kdenlive and foolishly messed with something that wasn't broken,now it is and I can't reinstall from software sources or add/remove,HELP!
I've included this screenshot to show the error I get when trying to "Get Software",
Thanks in advance:oops:

---

### Post by t0p on 2010-04-14
When you were trying to upgrade kdenlive, did you add a new repository to your list of software sources?  If so, remove it.

Next, make sure all traces of kdenlive are removed from your system, with the command

```
sudo apt-get remove --purge kdenlive
```

or

```
sudo apt-get purge kdenlive
```

Next, update your package list with command

```
sudo apt-get update
```

Now, reinstall with command

```
sudo apt-get install kdenlive
```

---

### Post by MisFitt on 2010-04-14
OK,I put in all of it in scroll order
I thought I'd removed the software link but obviously not-or have I?
THANKS HEAPS btw
It's asking me also if I'm the root-which I need help with

---

### Post by nitstorm on 2010-04-14
enter sudo before ur command and then u'll be prompted for the password , so put it in and hit enter and should work like a charm wenever the system asks u for root permissions.

---

### Post by MisFitt on 2010-04-14
I did that and it's installed,I see it in the software list but it wont open,nothing,hmm
and I also reinstalled it in synaptic
rebooted,reinstalled,rebooted into "repair broken packages",reinstalled....zip,wont open

---

### Post by sandyd on 2010-04-14
you either need to use ppa-purge or to force the version of kdenlive because its having a version mismatch atm.

---

### Post by MisFitt on 2010-04-14
> **carlee said:**
> you either need to use ppa-purge or to force the version of kdenlive because its having a version mismatch atm.
Thankyou.
Not sure if I've done it correctly but ppa purge is saying that ppa isn't there.
I did (attempt to)delete it out software sources yesterday
Removed kden,rebooted,reinstalled still nothing so I would same I'm in the same situation alas.
Oh dear this is way beyond me

moi@moi-desktop:~$ sudo apt-get autoremove kdenlive
[sudo] password for moi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kdenlive kdenlive-data swh-plugins
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 15.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 156563 files and directories currently installed.)
Removing kdenlive ...
Removing kdenlive-data ...
Removing swh-plugins ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

all the "Unknown media type in type" I don't understand what they mean or do
also,just a thought,is it possible I've deleted anything I shouldn't have from Software Sources by mistake?

---

### Post by MisFitt on 2010-04-15
I'm still terribly stuck and have been reading/looking.
Is it software sources(ppa),synaptic or is it likely to have been a terminal command that was wrong?

  .Am I facing the potential of having to reinstall the entire system to get it back because I haven't a clue?
Kino opens,kdenlive and openshot don't.

---

### Post by MisFitt on 2010-04-16
this message popped up when trying to update:
There was an error message which I could not catch to duplicate alas

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_non-free_binary-amd64_Packages).
This has occurred because I have messed up the ppa I'm assuming.
The thing's still a mess,nothing video working

---

