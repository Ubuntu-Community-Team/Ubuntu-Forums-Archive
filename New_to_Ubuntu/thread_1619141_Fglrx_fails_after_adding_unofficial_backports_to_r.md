---
title: "Fglrx fails after adding unofficial backports to repositories"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by cheph on 2010-11-11
Hello all,

So I added the the unofficial backports to my repositories that were recommended on this howto page under unofficial backports [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) specifically i added:
```

ppa:falk-t-j/lucid
ppa:abogani/ppa

```and did what this page [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) told me to do under adding repository, I went to the terminal and pasted this:

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

```and

```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```I did all this just because I wanted jack2 installed (and that just because i wanted another program, mididings, to work). anyways that worked and jack2 was running fine but when I started the computer this morning i got this Ubuntu is in low graphics mode error message on startup. I reconfigured the graphics and restarted with the fglrx driver deactivated, when i try to reinstall the driver i get the following error:

```

E: fglrx: subprocess installed post-installation script returned error exit status 10

```Anyways best case scenario I would like to keep jack2 and get my accelerated graphics back. What I think happened is either that the new repository upgraded my fglrx driver to an unstable version that wont build properly on my system, that or it upgraded/replaced some library that the fglrx driver needed.

so after all that my question i guess would be is their any way I can just install an older version of the fglrx driver? where would i get it? how would i go about doing it? if thats a wash is their any way I can undo the updates i did after adding the repositories? is their any way I can just undo the graphics card related repository and keep jack2?

I know this is a long question so thanks in advance for sticking with it this whole time, also any other suggestions on how to get my graphics card working with the current build would be much appreciated.

---

### Post by cheph on 2010-11-11
Just an update i have tried the advice on the following website: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) under the section labeled 
**[SIZE=2][FONT=Trebuchet MS][SIZE=2]Problem:  Need to fully remove -fglrx and reinstall -ati from scratch[/SIZE][/FONT][/SIZE]**

 to no avail

also I have found a bug report who's seres of events seems close to mine but without more spasifics I cant be sure, if it is this but then it cropped up like 2 weeks ago and I would prefer to just to reverse the updates and just wait till they have solved this bug, still not sure how to do that though

oh the bug report is here BTW:[https://bugs.launchpad.net/kxstudio/+bug/667290?comments=all](https://bugs.launchpad.net/kxstudio/+bug/667290?comments=all)

---

### Post by cheph on 2010-11-12
Hey just FYI to anyone else with this problem, a workaround that solved it for me is available on that bug report in the previous post. Basically all I did was added the ppa from this site [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)  **(ppa:ubuntu-x-swat/x-updates)** to my third party sources

updated rebooted ran the following in the terminal:

```

sudo aticonfig --initial -f

```

rebooted again and got my effects + graphics driver back. (it also reinstalled pulse audio form what I can tell, which i had installed earlier)

---

