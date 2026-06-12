---
title: "gvfs/fuse reset for Ubuntu 16.04"
date: 2017-07-16
forum: Networking &amp; Wireless
---

### Post by ComputingFroggy on 2017-07-16
I have been running *Xubuntu* 16.04 on my 2 main machines quite happily for a while.

For a few weeks back, I have been having some troubles when connecting to remote servers (FTP, SFTP, SMB) from the file explorer (*Thunar*) :

[LIST]
[*]    the connection takes a long time: a few minutes instead of a couple of seconds (looks like there some time out problems)
[*]    the password is always asked (even if I have registered).
[/LIST]

I've tried using *PCManFM* instead of *Thunar*, but the same problem persists.

I can not tell what triggered that, but there's definitely something altering the connection. It worked fine on both machines. Then, a few weeks back I had theses symptoms on one machine, but the other was fine. And since last week-end, I have the same troubles on my second machine.

From what I remember, I installed *Zoiper* and *Tryton* (using the Debian apt) on the second machine: it might be one of this two generating the problem ... but removing them did not solve it.

I've tried removing the two files in* .local/share/keyrings/ (login.keyring, user.keystore),* but that did not change a thing.

I've uninstalled gvfs

```
$ sudo apt purge gvfs

```
and resinstalled it

```
$ sudo apt install gvfs brasero gvfs-backends gvfs-fuse

```
without any success.

I've tried to remove libfuse2 package and I got an error message (in French sorry):

```
$ sudo apt remove  libfuse2
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.
L'information suivante devrait vous aider à résoudre la situation : 

Les paquets suivants contiennent des dépendances non satisfaites :
 grub-common : Dépend: libfuse2 (>= 2.8.4-1.4) mais ne sera pas installé
               Recommande: os-prober (>= 1.33) mais ne sera pas installé
E: Erreur, pkgProblem::Resolve a généré des ruptures, ce qui a pu être causé par les paquets devant être gardés en l'état.

```

The only solution I can think of, is to re-install the system from scratch ... but I am not really keen on this: this is not *Windows* after all.

Any help would be appreciated, thanks.

---

