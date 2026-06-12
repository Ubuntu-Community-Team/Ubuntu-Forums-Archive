---
title: "Problem With Synaptic Package Manager and System Update"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by iliagontarev on 2011-03-12
Hello

There is an issue a cannot solve as i can't fix synpatic

it started with and update that cannot be completed:
[COLOR="Red"]"error ... one package broken use "broken" filter to locate it"[/COLOR]

so i open up the synaptic and it fails to work

[COLOR="Red"]E: Malformed 1st word in the Status line
E: Error occurred while processing libatasmartT (UsePackage1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/COLOR]

I scanned the web for some answers and it turns out im helpless i tried to reinstall synaptic but i think i might have done a bigger mess typing a code sudo apt-get -f install and something else trying reinstall synaptic.
:confused:

Please Help!



EDIT: New Issue

Opening Update Manager:

[COLOR="Red"]An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed 1st word in the Status line, E:Error occurred while processing libatasmartT (UsePackage1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'[/COLOR]

---

### Post by runeh76 on 2011-03-12
Hi

Terminal:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by iliagontarev on 2011-03-12
> **runeh76 said:**
> Hi

Terminal:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

Hey! - didn't work - same code


Fetched 5,703B in 1s (4,355B/s)
Reading package lists... Error!
E: Malformed 1st word in the Status line
E: Error occurred while processing libatasmartT (UsePackage1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by drazoro on 2011-03-12
Hello run the following command in the terminal : sudo aptitude update

---

### Post by zipperback on 2011-03-12
Open a terminal window. (Applications -> Accessories -> Terminal)

Now enter the following.

```
sudo apt-get install synaptic --reinstall
```

That should reinstall synaptic for you.

If it still gives you a problem, let me know and I'll walk you through tracking down the problem.

- zipperback
:popcorn:

---

### Post by runeh76 on 2011-03-12
Try this:

```
cd /var/lib/dpkg
mv status status-bad
cp status-old status

sudo apt-get update
```

---

### Post by iliagontarev on 2011-03-13
> **zipperback said:**
> Open a terminal window. (Applications -> Accessories -> Terminal)

Now enter the following.

```
sudo apt-get install synaptic --reinstall
```

That should reinstall synaptic for you.

If it still gives you a problem, let me know and I'll walk you through tracking down the problem.

- zipperback
:popcorn:

Hey! Got the same here:


Reading package lists... Error!
W: Encountered status field in a non-version description
E: Malformed 1st word in the Status line
E: Error occurred while processing doc-base (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
i@i-laptop:~$

---

### Post by iliagontarev on 2011-03-13
Hey Runey Got the same error

Wow now this is getting real strange i can't deal with that problem...
the fact is that notification icon (white brick in red square) is active and and the problem originally derived from system update.

---

### Post by runeh76 on 2011-03-13
Check Synaptic Package Manager. At left there is reading **"Other Filters"** or something like that, click it and u find [B]Fix broken packages.
[/B]. See what packages there is and post them here.

Also post sources.list

```
gksu gedit /etc/apt/sources.list
```

---

