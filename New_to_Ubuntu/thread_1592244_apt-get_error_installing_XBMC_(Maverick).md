---
title: "apt-get error installing XBMC (Maverick)"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by bprins on 2010-10-09
Hi,

I might be asking a very dumb question, but I really would like to learn the answer anyway.

I am using Maverick since alpha3 (and as everybody else, quite impressed by its performance). There is 1 problem, I still can't install XBMC from any repository.

Now, as far as I understood, the official XBMC PPA will not be added before Maverick is released. 

1) Did I understand that correctly? 
2) If so, what is the rationale behind this? Doesn't early integration yields helpful feedback for either XBMC, Ubuntu, or both?

Then, moving on, without official PPAs there are still unsupported and untrusted PPAs. 

3) Who are the maintainers of those PPAs? Developers of XBMC? Random users of Ubuntu / XBMC?
4) Why are the PPAs untrusted? Does untrusted mean that there is no key signing? If not, what does it mean?

Curious as I was, I tried to add the untrusted PPA:
```
apt-add-repository ppa:mario-smitz/ppa
sudo apt-get update
sudo apt-get install xbmc
```

which gave me the following error:
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xbmc : Depends: xbmc-data (= 2:10.00~svn34523-maverick1~ppa1) but it is not going to be installed
        Depends: xbmc-skin-confluence (= 2:10.00~svn34523-maverick1~ppa1) but it is not going to be installed
        Depends: xbmc-web (= 2:10.00~svn34523-maverick1~ppa1) but it is not going to be installed
E: Broken packages
```

Thanks a million in advance for answering any of my questions.

Regards, Bas

PS: if you can refer me to a website where this concept is explained, that's also more than welcome of course.

---

### Post by ubunterooster on 2010-10-09
There is no 10.10 ppa :(

1) Yes 
2) No idea
3) Developers of XBMC, I think
4) I believe you are correct in thinking it is because of the signing; that is what I have come to think.

---

### Post by JustinR on 2010-10-09
Hi, here's how to get XBMC working:

Go to Applications > Ubuntu Software Center > Edit > Software Sources.

Under the 'XBMC Maverick PPA' click 'Edit', under 'Distribution' change 'Maverick' to 'lucid' and press okay. Update your package list and install XBMC from there.

---

### Post by ubunterooster on 2010-10-09
> **JustinR said:**
> Hi, here's how to get XBMC working:

Go to Applications > Ubuntu Software Center > Edit > Software Sources.

Under the 'XBMC Maverick PPA' click 'Edit', under 'Distribution' change 'Maverick' to 'lucid' and press okay. Update your package list and install XBMC from there.
Won't that be likely to cause more problems later on?

---

### Post by JustinR on 2010-10-09
It works fine - nothing, especially things like directory structure have not been changed to the point of XBMC not working - once they release the new Maverick PPA then all you have to do is change the 'Distribution' back to Maverick and upgrade XBMC.

---

### Post by bprins on 2010-10-10
Hi,

Doesn't seem to work either.
```
W: Failed to fetch http://ppa.launchpad.net/xbmc-team/ppa/ubuntu/dists/lucid/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/xbmc-team/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

```

1) Nobody uses the mario-smitz PPA?

I can probably wait a few more days until the PPA for Maverick becomes available, but still I would like to have alternatives (like to use unofficial PPAs) while testing an alpha / beta.

2) Who knows what I am after :-)?

Updated:
Now I tried to add ppa:team-xbmc-svm, did the trick Justin tought me (edit the distro to lucid), ran sudo apt-get update and tried to install Xbmc. Now I receive the following error:
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xbmc : Depends: xbmc-data (= 2:10.00~svn33778-lucid1) but it is not going to be installed
        Depends: xbmc-skin-confluence (= 2:10.00~svn33778-lucid1) but it is not going to be installed

```

3) How to resolve that error?

I tried to install the dependencies first (just to see if it was an doable scenario), but then I just get a new error that also that package depends on something, etc etc etc until I have a leaf that isn't depending on things, which throws me:
```
E: Package 'libfaac0' has no installation candidate

```

So, this isn't working very well either.

4) Who can help me further?

Many thanks!

Bas

---

### Post by JustinR on 2010-10-10
Hi,

Is Ubuntu fully updated? And what release of Maverick are you using?

---

### Post by bprins on 2010-10-10
Hi Justin,

Running latest & greatest in maverick. Have been on maverick since alpha3, but ran the updates every day, so shouldn't be missing anything.

You have XBMC running in maverick?

Any idea when the official XBMC repos get updated for maverick?

Thanks for helping out btw :) Appreciated!

---

### Post by JustinR on 2010-10-10
> **bprins said:**
> Hi Justin,

Running latest & greatest in maverick. Have been on maverick since alpha3, but ran the updates every day, so shouldn't be missing anything.

You have XBMC running in maverick?

Any idea when the official XBMC repos get updated for maverick?

Thanks for helping out btw :) Appreciated!

Yep, I have XBMC running in maverick. What have you done so far to try to get XBMC to install? Have you followed any guides - like the one on the XBMC site?

---

### Post by bprins on 2010-10-10
Well, didn't really follow a guide. What I did so far:
try to add maverick repo for team-xbmc (didn't work)
compiled from source (worked, but can't get HDMI sound working)
tried the trick posted in this forum:
- added maverick team-xbmc and team-xbmc-svn, renamed distro to maverick (didn't work, strange errors when installing xbmc posted in this forum)

how did you pull this off? compiled? repos? if so, which one? tutorial? if so, please link.

many thanks !

---

### Post by JustinR on 2010-10-10
> **bprins said:**
> Well, didn't really follow a guide. What I did so far:
try to add maverick repo for team-xbmc (didn't work)
compiled from source (worked, but can't get HDMI sound working)
tried the trick posted in this forum:
- added maverick team-xbmc and team-xbmc-svn, renamed distro to maverick (didn't work, strange errors when installing xbmc posted in this forum)

how did you pull this off? compiled? repos? if so, which one? tutorial? if so, please link.

many thanks !

> 
sudo apt-get install python-software-properties pkg-config
sudo add-apt-repository ppa:team-xbmc
[COLOR="Red"]**From here to go Applications > Ubuntu Software Center > Edit > Software Sources > Other Software > Click on 'http://ppa.launchpad.net/team-xbmc/ppa/ubuntu maverick main' then press 'Edit', Change 'Distribution' to 'lucid'. Press Ok and press Close.**[/COLOR]
sudo apt-get update
sudo apt-get install xbmc xbmc-standalone
sudo apt-get update


Thats how I did it.

---

### Post by bprins on 2010-10-10
Then something else is broken here.

I'll wait for the official XBMC maverick PPA.

following your steps (exactly) gives the following error.

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xbmc : Depends: xbmc-data (= 2:10.00~svn33778-lucid1) but it is not going to be installed
        Depends: xbmc-skin-confluence (= 2:10.00~svn33778-lucid1) but it is not going to be installed
 xbmc-standalone : Depends: xbmc-data (= 2:10.00~svn33778-lucid1) but it is not going to be installed
                   Depends: xbmc-skin-confluence (= 2:10.00~svn33778-lucid1) but it is not going to be installed
E: Broken packages

``` 

Strange isn't it... :)

if you have an idea how to solve this problem, ideas are always appreciated.

Thanks anyway!

Cheers Bas

---

### Post by JustinR on 2010-10-10
> **bprins said:**
> Then something else is broken here.

I'll wait for the official XBMC maverick PPA.

following your steps (exactly) gives the following error.

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xbmc : Depends: xbmc-data (= 2:10.00~svn33778-lucid1) but it is not going to be installed
        Depends: xbmc-skin-confluence (= 2:10.00~svn33778-lucid1) but it is not going to be installed
 xbmc-standalone : Depends: xbmc-data (= 2:10.00~svn33778-lucid1) but it is not going to be installed
                   Depends: xbmc-skin-confluence (= 2:10.00~svn33778-lucid1) but it is not going to be installed
E: Broken packages

``` 

Strange isn't it... :)

if you have an idea how to solve this problem, ideas are always appreciated.

Thanks anyway!

Cheers Bas

You could try removing all other XMBC data and other PPA's and see if it works.

---

### Post by bprins on 2010-10-10
already remove it.

I'll try a new thread with the specific question how to resolve the apt-get error. Somebody must have this error before and know how to get rid of it.

Thanks for your time!

---

### Post by bprins on 2010-10-10
Hi guys,

I've added the XBMC repository and changed the distribution from maverick to lucid (I got this tip in another thread).

Now, I get the following error trying to install XBMC from the lucid repo:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xbmc : Depends: xbmc-data (= 2:10.00~svn33778-lucid1) but it is not going to be installed
        Depends: xbmc-skin-confluence (= 2:10.00~svn33778-lucid1) but it is not going to be installed
 xbmc-standalone : Depends: xbmc-data (= 2:10.00~svn33778-lucid1) but it is not going to be installed
                   Depends: xbmc-skin-confluence (= 2:10.00~svn33778-lucid1) but it is not going to be installed
E: Broken packages

```

I've tried to resolve this with google, but no luck. What does this mean? How can I resolve this error? 

Thanks a lot in advance.

Bas

---

### Post by cariboo on 2010-10-10
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by bprins on 2010-10-10
ah sure thing didn't realise this also qualified as same subject.

but, found out something else,.

where apt-get fails, aptitude does have a solution.

```


The following NEW packages will be installed:
  libqt3-mt{a} librtmp0{a} libvdpau1{a} mesa-utils{a} python-qt3{a} 
  python-sip{a} xbmc xbmc-bin{ab} xbmc-data{a} xbmc-skin-confluence{a} 
  xbmc-standalone 
0 packages upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 45.7MB of archives. After unpacking 103MB will be used.
The following packages have unmet dependencies:
  xbmc-bin: Depends: libfaac0 (>= 1.26) but it is not installable.
            Depends: libmodplug0c2 (>= 1:0.7-4.1) but it is not installable.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     xbmc [Not Installed]                               
2)     xbmc-bin [Not Installed]                           
3)     xbmc-data [Not Installed]                          
4)     xbmc-skin-confluence [Not Installed]               
5)     xbmc-standalone [Not Installed]                    

```

and I can install XBMC, how about that :)

---

### Post by bprins on 2010-10-10
Final solution for those who run into the same thing:
- remove the team-xbmc PPAs
- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-add-repository ppa:team-xbmc
- sudo apt-get update
- sudo apt-get install xbmc xbmc-standalone

Did the trick here.

PS: Thanks Justin for the help!

---

### Post by bjb1959 on 2010-10-10
didn't work. just get errors that the ppa doesn't exist because, well, it doesn't yet. I tried changing to lucid but it downloaded 244 packages and tried to downgrade my entire kubuntu install so that isn't going to work. probably just need to wait I guess.

---

### Post by krisvek on 2010-10-26
Try again. It very much sounds like you changed 'maverick' to 'lucid' for the wrong repository.

---

### Post by shirine on 2010-10-27
I Finally installed XBMC from svn.

This is what i followed.

- remove the team-xbmc PPAs
- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-add-repository ppa:team-xbmc
- Edited Distribution from maverick to lucid.
- sudo apt-get update

Next step holds the trick .Thanks to the thread [http://forum.xbmc.org/showthread.php?p=625407](http://forum.xbmc.org/showthread.php?p=625407)

I installed libmodplug0c2 from this link here [https://launchpad.net/ubuntu/maverick/i386/libmodplug0c2/1:0.8.7-1build1](https://launchpad.net/ubuntu/maverick/i386/libmodplug0c2/1:0.8.7-1build1)

Now try installing from synaptic.It should work.Worked for me.

Thank you all here.

---

### Post by moonoiuk on 2010-12-18
Thanks guys :D , that last reply fixed my issue but I needed the 64 bit version of libmodplug0c2.

For those that have the 64bit version of Ubuntu, this can be installed from the following link.
[https://launchpad.net/ubuntu/maverick/amd64/libmodplug0c2/1:0.8.7-1build1](https://launchpad.net/ubuntu/maverick/amd64/libmodplug0c2/1:0.8.7-1build1)

---

