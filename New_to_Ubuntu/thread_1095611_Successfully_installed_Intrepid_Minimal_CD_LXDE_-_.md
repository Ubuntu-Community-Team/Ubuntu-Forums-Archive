---
title: "Successfully installed Intrepid Minimal CD LXDE - can it be upgraded?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by manilaph on 2009-03-13
On my first attempt, I was able to successfully install the Intrepid 8.10 Minimal CD which took more than an hour to complete.

I started with sudo aptitude install **xorg** **gdm** **lxde** **menu** **synaptic** **firefox**

then added **openoffice**, **deluge**

then realized there was no sound and did some searching in these forums and found-out that i needed to install **alsa** and **pulseaudio**

i was then using firefox to surf and it detected the needed **flashplayer** and i also needed to install the  **java jre** stuff.

anyway, everything is now working super-fast and clean.

my question is... when the next version of Ubuntu 9.04 comes out, can I just upgrade this set-up or will I have to do it all over again with the 9.04 minimal cd.

will **sudo aptitude safe-upgrade** work if i use the 9.04 repositories when it is out?

or should i do a **sudo aptitude dist upgrade**?

by the way, this set-up was installed in a P4 1gig Ram machine with wired-connection.

i can also install this on a laptop but will have to add:

sudo aptitude install **iwlwifi** (stuff) and **wicd**.

cheers!

---

### Post by theozzlives on 2009-03-13
The way it's looking right now, the alternate CD will launch a dialog that gives you the option to upgrade.

---

### Post by manilaph on 2009-03-13
Thank you.

Does that mean I have to download the cd again?

I am just worried that it might add stuff that i may not need. I enjoy my current set-up with LXDE... fast and light.

Will changing all the repositories to the Jaunty 9.04 then do an upgrade command do the trick?

---

### Post by mpsii on 2009-03-13
I know you are going for lean and mean, and whatnot, but I have found upgrading to be TONS easier with update-manager.

But... yes... just like any other Debian-based distro, you change the sources.list file to point from intrepid to jaunty. Issue the apt-get update and apt-get dist-upgrade commands... voila! (or aptitude, which bleh, I have never liked)

---

### Post by manilaph on 2009-03-13
ok thank you. will wait for the next release. can't wait!

---

### Post by mkvnmtr on 2009-03-13
When I do a minimal install I like to install the update manager and of course synaptic.

---

### Post by manilaph on 2009-03-14
> **mkvnmtr said:**
> When I do a minimal install I like to install the update manager and of course synaptic.

is the update manager the same as doing

[I]sudo aptitude update
sudo aptitude upgrade[/I]

i noticed that there is no automatic update notifier not like with the Ubuntu LiveCD version.

i am using LXDE by the way.

is there a way to get automatic notifications regarding available updates?

---

### Post by mpsii on 2009-03-14
> **manilaph said:**
> is the update manager the same as doing

[I]sudo aptitude update
sudo aptitude upgrade[/I]

i noticed that there is no automatic update notifier not like with the Ubuntu LiveCD version.

i am using LXDE by the way.

is there a way to get automatic notifications regarding available updates?

update-manager is an actual utility

```
 $ sudo apt-get install update-manager
```

To use it, run:

```
 $ sudo update-manager 
```

This will also notify you of any released distributions, telling you that Intrepid 8.10 is available right now (if you run it on Hardy or Gutsy).

To upgrade to the next available distribution, even unreleased (like Jaunty):
```
 $ sudo update-manager -d
```

---

### Post by luc0zade on 2009-04-04
There is also a fix for other question asked - is there a way to get automatic notifications regarding available updates?

This might be due to a bug, see [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/300463]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/300463") for more info.

Running LXDE with Hardy, I had to apply the fix described on the page liked above - which was simply to change the line

OnlyShowIn=GNOME;XFCE;

in /etc/xdg/autostart/update-notifier.desktop to

NotShowIn=KDE;

---

### Post by mfrazzz on 2009-04-11
> **luc0zade said:**
> 
Running LXDE with Hardy, I had to apply the fix described on the page liked above - which was simply to change the line

OnlyShowIn=GNOME;XFCE;

in /etc/xdg/autostart/update-notifier.desktop to

NotShowIn=KDE;

Actually, just add LXDE to the list instead:

OnlyShowIn=GNOME;XFCE;LXDE;

I did that on my Xubuntu 8.10 install that is now running LXDE.  I have a VM that was installed with minimal CD and LXDE and did the same and it works there too.  Love the minimal install method.  About to try it on an old laptop to see how it does with this.

---

### Post by JoshuaRL on 2009-04-11
If you install Update Manager, it should show you when there are updates with that fix.

But if it doesn't you can always run it with:
```
sudo update-manager -d
```
That will check if there is a distro update available.

---

### Post by mfrazzz on 2009-04-23
FWIW: I just took my minimal CD LXDE install up to Jaunty with Update-Manager.  Just ran update-manager and it showed Jaunty was available.  Told it to upgrade, and after answering a number of questions through the process and a few hours (this is a Pentium II laptop so only 128MB of memory and slow) I now have a minimal Jaunty LXDE laptop now :D

So in answer to the original question, Yes you can :D

---

