---
title: "Wubi Sucks, Iso burning sucks, cant install!"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by josh0261 on 2009-07-31
Every time I try to burn an .iso of Ubuntu or Kubuntu, it turns out to have an error and the insallation fails. I've tried burning at a slower speed, downloading iso files from different mirrors, using a different burning application.. installing on different machines.. everything basically.
So I resort to downloading Wubi. I actually wanted KDE, but I get an error with that. So gnome it is. Then I realise my system has been identified as 64 bit.. which is certainly is not!!
Any one else had similar problems, or suggestions? =(
Thanks

---

### Post by lisati on 2009-07-31
Frustrating, isn't it?

Do you remember what the error message said?

For many years I thought my desktop was 32-bit but I recently discovered it was 64-bit.

---

### Post by josh0261 on 2009-07-31
Not specifically, just the usual 'try burning the iso at a slower speed, faulty hard disk..' kinda thing.
I have burned several different images at the slowest speed, and tried to install on 3 different machines.

---

### Post by snek on 2009-07-31
Have you tried replacing your burner or reading drive?
I recently discovered that one of my pc's would not install XP but would install Vista & Ubuntu & Server 2008 because the dvd-rom drive was broken! I have no idea why the other 3 OS's installed just fine and why XP gave errors. However, after replacing the drive everything installed just fine and MUCH faster than before as well.

Considering the drives only cost about 15-20 euro's these days it shouldn't be too much of problem for you to replace it I guess? ;)

Or you can always swap them from another machine..

New drives also support more dvd/cd types.. I've had problems with this in the past where one drive would burn a cd just fine, but my other drive had problems reading it eventhough the drive that burnt it had no problems reading it.

---

### Post by Bigtime_Scrub on 2009-07-31
I got tired of making CD/DVD coasters with Linux and since I hop around a lot I needed another solution. I got myself a decent sized USB stick and I use UNetBootin now. It is supported in both Linux and Windows. What it basically does is make a bootable USB drive and all you need to do is drag and drop the .iso you want to use. I have found UNetBootin to be far more reliable then burners.

---

### Post by automaton26 on 2009-07-31
Always use **md5sum** to check that the downloaded .iso file is exactly the same, *before* attempting to burn it to a disk. That will remove one possible cause of errors.

Also, most burning software has an option somewhere to *verify* the data after it's been written to disk.

You can only be reasonably sure the disk is correct if you do **both** of these.

---

