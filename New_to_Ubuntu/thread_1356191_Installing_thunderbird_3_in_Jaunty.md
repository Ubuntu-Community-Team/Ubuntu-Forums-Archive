---
title: "Installing thunderbird 3 in Jaunty"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by scotcella on 2009-12-15
Hi all,

I am in need of a little help to clear up my confusion..  I am trying to install thunderbird3 in Jaunty.

I have read a number of posts but have a little set back, either I'm a bit blonde or just not "getting it".

Anyway one of the links I read up had very clear instructions...


> Part I: install process

The install process is very simple:

   1. Download the file
   2. Extract the archive
   3. Move the thunderbird folder to /opt
   4. Create a link to run it easily


1. Download the file

You can download the most recent public release from Thunderbird's website:
[http://www.mozillamessaging.com/en-U...arly_releases/](http://www.mozillamessaging.com/en-U...arly_releases/)

2. Extract the archive

Go to the folder where you downloaded the file (should be a .tar.bz2) and extract it (right click -> extract here). Alternatively, you can also use the tar command.

3. Move the thunderbird folder to /opt

You will need sudo rights to move the file to /opt. You can either start Nautilus in root mode and move the folder graphically or use this command, assuming you are working in the folder where you extracted the archive.

```
sudo mv thunderbird /opt
```

4. Create a link to run it easily

You will create a link to the executable and put it in /usr/bin, this way you simply have to use this link to run the testing version, for example using the "run application" dialog (Alt+F2). I called it "thunderbird3" to make it clear.

```
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird3
```


Now I have downloaded and extracted it onto my desktop but when I try to move the thunderbird folder to /opt, the terminal output is:
> 
mv: cannot stat `thunderbird': No such file or directory

Any help is appreciated, thanks in advance!

---

### Post by s3MA00RRNY on 2009-12-15
Add this through Adminstration > Software Repositories > Third Party.

deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main 

**Then just upgrade your packages through Update Manager.**

---

### Post by scotcella on 2009-12-15
Thanks..

I got an error, it says..

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6

---

### Post by tqprvn on 2009-12-16
me too :(

---

### Post by tom.swartz07 on 2009-12-16
> **tqprvn said:**
> me too :(

if youre using karmic, try this

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa

and then install thunderbird.

it will keep you updated with firefox too.

---

### Post by tqprvn on 2009-12-16
wont work with Jaunty? Im still on 9.04

---

### Post by scotcella on 2009-12-16
No tom.. not using Karmic, as I said on my title, I am using Jaunty.

---

### Post by Merk42 on 2009-12-16
For Jaunty copy the text [here](http://ppa.launchpad.net/fta/ppa/ubuntu/dists/jaunty/Release.gpg), save as a text file and then go to Import Key File in the updates tab of Software Sources to import it

There's a command line way to do it, but I don't know it off hand.

---

### Post by scotcella on 2009-12-17
Thanks...

---

### Post by tom.swartz07 on 2009-12-17
> **scotcella said:**
> No tom.. not using Karmic, as I said on my title, I am using Jaunty.

oops, my bad. sorry.
either way, you just had to add the mozilla daily builds and update.
glad you got it though.

---

### Post by scotcella on 2009-12-17
Actually none of the things are working.. i'm stil trying to figure a way around it..  never mind but i'll get there eventually

---

