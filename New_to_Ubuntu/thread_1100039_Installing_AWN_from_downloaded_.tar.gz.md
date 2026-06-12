---
title: "Installing AWN from downloaded .tar.gz"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by cfree220 on 2009-03-18
Hi, I currently have AWN 0.2.6 installed on 8.10 (it's the latest version in the repositories). I'd like to upgrade to 0.3.2.1; I've downloaded the .tar.gz file from the project page, and was wondering how to go about installing it. I do want to upgrade... so I'm hoping that I will be able to maintain current settings, launchers, etc...

---

### Post by issih on 2009-03-18
If I was you, I'd opt to add this ppa instead:

[https://launchpad.net/~awn-core/+archive/ppa](https://launchpad.net/~awn-core/+archive/ppa)

That should be less messy than compiling from source.

This should explain adding ppa's if you are not au fait.

[https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html)

you will also need to grab the gpg key as that is now required:

[http://www.youtube.com/watch?v=UUZOQsNo_ws](http://www.youtube.com/watch?v=UUZOQsNo_ws)

Hope that helps.

N.B. if you do want to install from source you need to extract the tarball then read the readme file for directions on what to do, most source packages work the same way, but it is not set in stone, and you should always read the readme, thats what it is for :)

---

### Post by cfree220 on 2009-03-18
hmmm.... So would I need to download each of the package files individually and install them? Instead of downloading one that contains them all? Is there a certain order I should do that in?

---

### Post by snova on 2009-03-18
> **cfree220 said:**
> hmmm.... So would I need to download each of the package files individually and install them? Instead of downloading one that contains them all? Is there a certain order I should do that in?

No, you add that repository to your sources list and then your system will automatically update from it.

[Instructions]("https://help.launchpad.net/Packaging/PPA#Installing software from a PPA")

---

### Post by cfree220 on 2009-03-18
errr.... I guess this is why I'm on these forums and not general help XD

How do I add that as a software source?

---

### Post by phantom3113 on 2009-03-18
to add software sources, go to system>>administration>>software sources, and select the third party tab. select add, and put this in: deb [http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu](http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu) intrepid main. Next, go to: [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCA244889B2802451](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCA244889B2802451) and copy/paste the nonbold text into a new text file. Save it as AWN PPA or whatever sounds good to you. To add this, go to the same place as before, only this time select the "authentication" tab. select "import key file" and selec the file you just created. That should be everything you need to do to put AWN into the repositories.

---

### Post by snova on 2009-03-18
> **cfree220 said:**
> errr.... I guess this is why I'm on these forums and not general help XD

How do I add that as a software source?

There's a link in that link, it points to [here]("https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html").

This would be the APT line you use:

```
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu intrepid main
```

And remember to add the archive key following these instructions:

[Adding the keys using Gnome]("https://help.launchpad.net/Packaging/PPA#Adding the keys using Gnome")

The key you need can be found here:

[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

### Post by cfree220 on 2009-03-19
Thanks for the help. Unfortunately, the page with the archive key is currently unavailable. so I'll have to wait to add that... :(

---

### Post by snova on 2009-03-19
> **cfree220 said:**
> Thanks for the help. Unfortunately, the page with the archive key is currently unavailable. so I'll have to wait to add that... :(

It will work without the key, but it would have complained about package authentication.

At any rate, it seems to be up now...

[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x7D2C7A23BF810CD5](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x7D2C7A23BF810CD5)

---

### Post by cfree220 on 2009-03-19
I have the key, but it still isn't working. Here's what I've done so far:

Added: deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) intrepid main
To: /etc/apt/sources.list

And added the key using the software sources interface.

I then ran
```
sudo apt-get update
and
sudo apt-get upgrade
```

But it did not retrieve any packages....

---

### Post by Paqman on 2009-03-19
Open up Synaptic and have a look to see what AWN packages you've got available.

---

### Post by cfree220 on 2009-03-19
They are the packages for 0.2.6

---

### Post by cfree220 on 2009-03-19
Hmmm... I was just looking at the launchpad page. It seems that 0.3.2 is for Jaunty... can I install this on Intrepid anyways, or will I have to wait for 9.04?

---

### Post by Paqman on 2009-03-19
> **cfree220 said:**
> Hmmm... I was just looking at the launchpad page. It seems that 0.3.2 is for Jaunty... can I install this on Intrepid anyways, or will I have to wait for 9.04?

If you use the PPA, you'll get 0.3.2 no matter what version of Ubuntu you've got.

Double-check your entry for the PPA. Either go to "Software Sources" or check /etc/apt/sources.list.

---

### Post by cfree220 on 2009-03-19
hmmm got it working, but it seems to be missing some of the extra applets, such as a pandora radio player...

---

### Post by cfree220 on 2009-03-19
And now I've got those working too.

I love Ubuntu. I thought the Vista GUI was nice...

---

### Post by Paqman on 2009-03-19
Indeed. With AWN, a nice Emerald theme and Compiz Fusion effects, an Ubuntu desktop can be a thing of beauty!

---

### Post by cfree220 on 2009-03-19
It's too bad that Ubuntu doesn't ship with better themes... I'm actually really surprised that there's no gloss, transparency, or slick icons. I know that having fully customized (read: gone WAY overboard) my GUI, it's a lot easier to quickly navigate various programs and features. I think that an improved default theme would definitely be a step towards making Linux more attractive to people considering transitioning.

---

