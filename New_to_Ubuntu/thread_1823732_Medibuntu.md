---
title: "Medibuntu?"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by xflbret on 2011-08-12
Hello all,

I while back I gave Ubuntu a chance, but had to abandon it because the drivers for my onboard video chip sucked. I have decided to give it another chance. The driver issue seems to be worked out, and I REALLY REALLY REALLY like the Gnome 3 interface. So, I can see myself sticking with this for a while.

The last time I gave Ubuntu a chance I had found a post on these forums where I could copy a huge amount of text to paste in the terminal, and it would install pretty much everything that Ubuntu should include but doesn't. But, for the life of me, and I have been drilling on and off for two days now, I can not find that post again.

I would much prefer this particular post because I love being able to copy and paste once or twice rather than several individual times.

Can someone help me find the post? Thanks.

---

### Post by Perfect Storm on 2011-08-12
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
sudo sed -i "/^# deb .*partner/ s/^# //" /etc/apt/sources.list && sudo apt-get update
sudo apt-get install ubuntu-restricted-extras non-free-codecs libdvdcss2 sun-java6-bin sun-java6-fonts sun-java6-plugin
```

Line 1 - adds medibuntu
Line 2 - adds medibuntu software to Ubuntu Software Center (so it appears)
Line 3 - enables Partner repositories
Line 4 - install codecs, Java etc.

---

### Post by xflbret on 2011-08-12
I appreciate the response, but the one I was looking for had several more lines. It included google earth, the M$ fonts, and a lot more...I know I'm not crazy. It's here somewhere...or at least it used to be.

---

### Post by jmszr on 2011-08-12
xflbret,

Here is the Ubuntu Community Documentation for Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .

Also, here is the Comprehensive Multimedia & Video Howto: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) .

Hope one or the other is what you're looking for.

Edit: MS fonts are included in the "ubuntu-restricted-extras" package.

I'm not sure if Google Earth is still included in the Medibuntu package; if not, you can get it through here: [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth) .

---

### Post by Frogs Hair on 2011-08-12
Google Earth was included in earlier versions of Medibuntu repository and the version offered was outdated   . I have the repository installed per the instructions at the link , which are similar to those already posted.

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui)

---

### Post by wojox on 2011-08-12
This installs the repo and keyring:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

```

Then install non-free codecs:

```
sudo apt-get install non-free-codecs
```

More cool stuff:

```
sudo apt-get install libdvdcss2 gxine libxine1-ffmpeg vlc mplayer mencoder
```

Currently Google Earth 6.0 in unstable. Look for 5.X. It's not held in Medibuntu anymore. :P

---

### Post by Perfect Storm on 2011-08-13
> **xflbret said:**
> I appreciate the response, but the one I was looking for had several more lines. It included google earth, the M$ fonts, and a lot more...I know I'm not crazy. It's here somewhere...or at least it used to be.

It is meta-packages which makes it easier to grab many packages at once.

---

### Post by beew on 2011-08-13
> **wojox said:**
> Currently Google Earth 6.0 in unstable. Look for 5.X. It's not held in Medibuntu anymore. :P
What do you mean? it is very stable on all my Ubuntu boxes. Don't need medibuntu for GE anymore, just install the package lsb-core from Synaptic and then install the .deb from
[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

---

### Post by wojox on 2011-08-13
> **beew said:**
> What do you mean? it is very stable on all my Ubuntu boxes. Don't need medibuntu for GE anymore, just install the package lsb-core from Synaptic and then install the .deb from
[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

True. I was going to go that route but thought it may be a little confusing. :P

---

### Post by garvinrick4 on 2011-08-13
> I appreciate the response, but the one I was looking for had several  more lines. It included google earth, the M$ fonts, and a lot more...I  know I'm not crazy. It's here somewhere...or at least it used to be.The code artificial intelligence gave you will include Microsoft fonts, gstreamer's you will need, well most everything except google earth. You can make a string of code as long
as you want add whatever you like.
Below is your ppa's if desired. 
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)
Below google earth and some copy and paste for stable version instructions included:
[http://www.ubuntuupdates.org/ppa/google_earth](http://www.ubuntuupdates.org/ppa/google_earth)

---

