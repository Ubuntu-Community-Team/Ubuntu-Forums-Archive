---
title: "Installing a wireless adapter"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by phillip_peters52 on 2008-03-15
I am trying to configure a Netgear WG111T adapter so i can connect to the internet on my home PC without having to reinstall ubuntu as I am a universit student I am normally hard wired in, but I have come home and now require to access via wireless. My system currently duel boots with both windows vista and ubuntu 7.1.

Can any one please advise me on how i can install this device without internet access.

Thanks

---

### Post by pytheas22 on 2008-03-15
It looks after some quick googling that you will need ndiswrapper to get that card to work.  There is an outline here [http://ubuntuforums.org/showthread.php?t=51993](http://ubuntuforums.org/showthread.php?t=51993) of what to do.  It doesn't cover installing ndiswrapper, but that can be done easily via synaptic.  Try following that thread and post the results.

That thread also only covers getting connected to a WEP network, which might as well be unencrypted these days, but try at least getting that far as a start; WPA can be set up later.

---

### Post by phillip_peters52 on 2008-03-15
Ok well I have tried to install ndiswrapper and it does not seem to register that the package is installed. Could this be due to not having any internet access while in ubuntu?

If so is there another way around this?

---

### Post by pytheas22 on 2008-03-15
If there's a way for you to get an Internet connection to your computer, it would make things much simpler.  But if you can't, you could still install ndiswrapper by doing this:

1. make sure your Gutsy CD is in your drive, and type in a terminal
```

sudo apt-get install build-essential
```

2. download the ndiswrapper source from [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.52.tar.gz?modtime=1201988892&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.52.tar.gz?modtime=1201988892&big_mirror=0) and save it on a USB stick or whatever.

3. transfer the ndiswrapper tarball to your home directory on your Ubuntu machine, and right click on the icon to extract it (select "Extract Here").

4. compile and install ndiswrapper:
```

cd ~ndisw*
make
sudo make install
```

Now ndiswrapper should be installed, and you just need to grab the Windows drivers for it and install them, as outlined in that thread I posted above.  Try this and let us know how it goes.

---

### Post by phillip_peters52 on 2008-03-20
I do not currently have the disc i installed ubuntu from with me as it is at uni, i have tried to  download and burn the same version to cd to install the software but it does not accept the cd as a valid file source and asks for the version that was created when i was at uni. Is there a way around this?

---

### Post by dstew on 2008-03-20
You can install packages off line by using the [nonetdebs]("http://nonetdebs.homeip.net/") service. If you just want one package, you can go to the [Ubuntu packages page]("http://packages.ubuntu.com/"), search for it and download it. Then, install it with ```
dpkg -i *filename.deb*
```

---

### Post by pytheas22 on 2008-03-20
Yes, you can use nonetdebs to figure out all the packages you'll need for build-essential and dependencies, or at a minimum, make sure you install the gcc compiler and the kernel headers, which I think is all you need to build ndiswrapper (but I could be wrong).

---

