---
title: "Songbird installation issues"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by bungz on 2009-12-19
Hi 

I'm trying to install songbird from [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

However, when in choose install, it does download the packages, but later shows the attached error message. 

Would appreciate any help. 

Thanks.

p.s. - I got a similar message when i tried installing gPodder as well.

---

### Post by Extract_Here on 2009-12-19
goto [www.songbird.com](www.songbird.com) and download strait off of their do you know how to install a tar.gz file.

---

### Post by Extract_Here on 2009-12-19
sorry i meant get [www.get](www.get)**songbird**.com there

---

### Post by bungz on 2009-12-19
[quote=do you know how to install a tar.gz file.[/quote]

Nope. Don't know how to go about that. :confused:

However, downloading now. Will try and get back.

---

### Post by Extract_Here on 2009-12-19
the download is in tar.gz ill tell you how when you reply back

---

### Post by 3rdalbum on 2009-12-19
That is nothing to worry about. You haven't added the GPG key for that repository, so it can't authenticate the packages from that repo.

You can still install software from it no problems.

Might be a good idea to find and add the GPG key anyway so you know the packages have not been tampered with in transit.

EDIT: The Medibuntu GPG key is in the 'medibuntu-keyring' package. After installing it, update your package list.

---

### Post by bungz on 2009-12-19
> **3rdalbum said:**
> That is nothing to worry about. You haven't added the GPG key for that repository, so it can't authenticate the packages from that repo.

You can still install software from it no problems.

Might be a good idea to find and add the GPG key anyway so you know the packages have not been tampered with in transit.

EDIT: The Medibuntu GPG key is in the 'medibuntu-keyring' package. After installing it, update your package list.

Ummm... Where can i find the 'medibuntu-keyring' package?

---

### Post by 3rdalbum on 2009-12-19
> **bungz said:**
> Ummm... Where can i find the 'medibuntu-keyring' package?

System > Administration > Synaptic Package Manager.

After installing, hit the Reload button.

---

### Post by bungz on 2009-12-19
> **Extract_Here said:**
> the download is in tar.gz ill tell you how when you reply back

Done downloading. What do i do next?

---

### Post by marshmallow1304 on 2009-12-19
You don't need to mess with the .tar.gz.  And Songbird is not in Medibuntu, so adding the Medibuntu keyring will not help (but, as I am now aware, it helped with the other packages).

From [this page]("http://www.getdeb.net/updates/Ubuntu/all#how_to_install"):
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```

---

### Post by bungz on 2009-12-19
Still says "could not find songbird package"

---

### Post by bungz on 2009-12-19
I think it is sorted. Thanks, folks.

---

### Post by slughappy1 on 2009-12-19
From your picture it looks like you are missing a key. Why not try ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783 && sudo apt-get update
``` After that go to their website and click the install button they have next to Songbird. That's how I installed it. 

Hope that helps.

---

### Post by bungz on 2009-12-20
3rdalbum's suggestion on fixing the medibuntu-keyring package helped in finding other programs (like gpodder) that i was having issues with. 

Marshmallow1304 suggested link gave me the instruction on what i need to do to manually configure repository. That fixed it. 

Thanks, all.

---

