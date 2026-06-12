---
title: "Problem installing libxine1-ffmpeg"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Farmer of Bricks on 2009-02-01
I need libxine1-ffmpeg to play mp3's in Amarok.

This is what happens:
```
user@computer:~$ sudo apt-get install libxine1-ffmpeg
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxine1-ffmpeg: Depends: libxine1-bin (= 1.1.11.1-1ubuntu3.1) but 1.1.11.1-1ubuntu3.2 is to be installed
E: Broken packages
user@computer:~$

```

Please help!

---

### Post by Daveth on 2009-02-01
have you not loaded all your codecs from the medibuntu repository?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Farmer of Bricks on 2009-02-01
> **Daveth said:**
> have you not loaded all your codecs from the medibuntu repository?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I enabled the Medibuntu repos, but it still won't install.

What does this mean?
```

The following packages have unmet dependencies:
  libxine1-ffmpeg: Depends: libxine1-bin (= 1.1.11.1-1ubuntu3.1) but
 1.1.11.1-1ubuntu3.2 is to be installed

```

I think it means that the libxine1-bin that I have is the wrong version, but I may be wrong. 

Thank you for your help.

---

### Post by Farmer of Bricks on 2009-02-01
Strange, just ran Adept Updater, and it upgraded amarok-xine, and a bunch of other stuff, but I still get the error in the previous post

---

### Post by Daveth on 2009-02-02
yes, it does look like dependency version drift between what you have and what it needs. I'm not at all sure about adding that other library- I suppose you can always uninstall it if things go bad.

---

### Post by GnuSense on 2009-02-02
I'm getting the same problem on Hardy.

It appears I didn't have the "universe" option enabled in my SECURITY repository in my sources.list.  

 Look over [this]("https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/256404/comments/2") post. 

[https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/256404](https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/256404)

---

### Post by GnuSense on 2009-02-03
Those who are still getting this problem can try this:

> sudo echo "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe" >> /etc/apt/sources.list

Obviously if you are using intrepid, substitute that for hardy above.

> 
sudo apt-get update

> sudo apt-get upgrade

Restart Amarok.  Probably flying monkeys will not be emitted from your USB ports.

---

### Post by Farmer of Bricks on 2009-02-04
It didn't work. 
Blender upgraded, but no libxine1-ffmpeg, and Amarok is now having trouble playing certain .ogg files, which may be a problem from K3B, but probably isn't. 

Any other suggestions, besides doing a clean install of Intrepid?

---

### Post by mc4man on 2009-02-04
If you have in software sources -> updates -> "Important security updates" - (hardy-security) enabled then you should be able to install libxine1-ffmpeg ( 1.1.11.1-1ubuntu3.2

If still a no go, then just go and download and install directly from here

[http://packages.ubuntu.com/hardy/libxine1-ffmpeg](http://packages.ubuntu.com/hardy/libxine1-ffmpeg)


Edit : also make sure in "Ubuntu Software" that 'universe' is enabled in addition to hardy-security

---

### Post by stovicek on 2009-02-04
> **Farmer of Bricks said:**
> It didn't work. 
Any other suggestions, besides doing a clean install of Intrepid?

Is this an Intrepid or Hardy install? The reason I ask is that the versions of the packages shown in your error are ones found in Hardy repos and not Intrepid repos. Are you sure the repos in your sources.list are all set for the correct release?

---

### Post by Farmer of Bricks on 2009-02-06
I am definitely using Hardy. I don't have KDE 4.2, for one, or Amarok 2, and I want them both, but don't have the time to do a full clean install, nor the desire to do a borktastic internet upgrade to Intrepid (I currently use KDE4.1 in my day-to-day, and have stopped using KDE3.5 entirely. i just use its apps.)

---

### Post by Farmer of Bricks on 2009-02-06
> **mc4man said:**
> ... download and install directly from here

[http://packages.ubuntu.com/hardy/libxine1-ffmpeg](http://packages.ubuntu.com/hardy/libxine1-ffmpeg)


Third try, after some updates today, this worked. Still want KDE 4.2.

---

