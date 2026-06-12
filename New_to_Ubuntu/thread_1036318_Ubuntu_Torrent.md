---
title: "Ubuntu Torrent?"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Twilfong on 2009-01-10
I just downloaded the Ubuntu torrent, and was checking the hash to make sure it was fine, and noticed that there are hashes listed for Kubuntu and Xubuntu, and I wanted to use one of those versions, as Ubuntu (for me) doesn't seem to display screen resolution properly. Where do I find those torrents?

---

### Post by taurus on 2009-01-10
[http://www.kubuntu.org/getkubuntu/download](http://www.kubuntu.org/getkubuntu/download)

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by avtolle on 2009-01-10
You do realize that the major difference between Ubuntu, Kubuntu and Xubuntu is the desktop environment and the applications under each, while the basic system is the same for all. So, why do you think you will have better luck with the resolution issue under one of the named derivatives than with Ubuntu? Not trying to be condescending, but is there a thread somewhere that gives you hope?

---

### Post by HunterThomson on 2009-01-10
I am a paranoid Linux user. I would never download my OS from a torrent. Directly download it form Kubuntu.org or Xubuntu.org. From a source you trust.

---

### Post by Twilfong on 2009-01-10
Which is better? I like the feel of Kubuntu, but I think I was having similar problems with screen resolution.

Alternatively, can I just install Ubuntu and change to K or X if necessary? Or is it something I would have to basically start all over for?

---

### Post by HunterThomson on 2009-01-10
What video card do you have???

---

### Post by taurus on 2009-01-10
For Kubuntu,

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

For Xubuntu,

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

### Post by Twilfong on 2009-01-10
> **avtolle said:**
> You do realize that the major difference between Ubuntu, Kubuntu and Xubuntu is the desktop environment and the applications under each, while the basic system is the same for all. So, why do you think you will have better luck with the resolution issue under one of the named derivatives than with Ubuntu? Not trying to be condescending, but is there a thread somewhere that gives you hope?

I am aware of that, but I read it on some thread, and I was using the wubi installer to test it out before scrapping windows, and it recommended trying a different desktop environment, and it worked. I don't know enough about programming to say why, but it did...

---

### Post by avtolle on 2009-01-10
OK, fair enough. BTW, if you install the Kubuntu desktop and Xubuntu desktop packages, you will be able to choose at log in which one you want to use for that session, and you may elect to choose one as default, while having access to the others. Good luck with the video problem.

---

### Post by Twilfong on 2009-01-10
> **avtolle said:**
> OK, fair enough. BTW, if you install the Kubuntu desktop and Xubuntu desktop packages, you will be able to choose at log in which one you want to use for that session, and you may elect to choose one as default, while having access to the others. Good luck with the video problem.

Terrific! Thank you!

---

### Post by -kg- on 2009-01-10
> **HunterThomson said:**
> I am a paranoid Linux user. I would never download my OS from a torrent. Directly download it form Kubuntu.org or Xubuntu.org. From a source you trust.

I understand your concerns, but I've always heard it's better to download an .iso via a torrent.  This is due to the checksums being done automatically during a torrent download.

Not to worry, though.  Would you trust a torrent download if it was linked to from the Ubuntu website?

[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

Part way down the page is a list of torrent sites that you can download the various distros of Ubuntu via Bittorrent.  A little farther down is a list of mirror sites from which you can download the distros via http or ftp.

These mirrors are really necessary considering the number of downloads that Ubuntu gets.  If the only available site to download from was Canonical or the Ubuntu website, they would be hard pressed for enough bandwidth.  Let alone the fact that international downloads could, and at times would be very slow due to paths and nodes being down.

I'd say that if the site is linked to by the Ubuntu website, they will likely be a safe place to download from, whether through http/ftp or bittorent.

Of course, *any* site can be hacked (maybe not easily, but...), even the official Ubuntu site.

---

