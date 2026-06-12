---
title: "Updating/Software Sources issues"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-12-05
ok alot of my software sources say they're from hardy heron release but that doesn't make sense to me... i was trying to install EL and using the guide i should be able to put Intrepid instead of hardy as the release but when i do i get an error close to this one ```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.
``` that's what i get when i try to update my desktop or even try to search for updates. I'm runing Ubuntu 8.10 Intrepid. but it's still saying that i'm having older repositories. Is there anyway to update these?

---

### Post by yellowaeroplane on 2008-12-05
not sure if this is exactly what you're looking for, but check out the "software sources" feature.

It's under System>>Administration>>Software Sources

You can check and un-check which repositories you're fetching from.


or... if you're comfortable editing text files, type this in a terminal:

```
sudo gedit /etc/apt/sources.list
```

then comment out the ones you don't need with "#"



These methods are both two different ways to do pretty much the same thing. Hope this helps a little at least!

---

### Post by 133794m3r on 2008-12-05
i was using the Software Sources Feature. that's why i said I tried to update it to intrepid it wouldn't update.

---

### Post by yellowaeroplane on 2008-12-05
Your system should still update, all it's saying is that it couldn't fetch from that particular repository.

I was getting the exact same error message when I updated and all I did was go into the "sources.list" file with gedit and commented (#) out the lines from Hardy.

---

### Post by yellowaeroplane on 2008-12-05
By the way, I just looked at the error message you got... and that repository is not even from Hardy, it's from Edgy... so just comment that bad boy out

---

### Post by 133794m3r on 2008-12-05
well yeah i know.. i tried doing teh Intrepid version of it b/c teh guide said it could run it w/ intrepid but it told me no and didn't work.. :/
ok here's the exact error i get when i run update manager or it runs on it's own ```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Michael.Godawski on 2008-12-05
Can you please post your whole sources.list

```
cat /etc/apt/sources.list
```

---

