---
title: "(help! my package and update manager have crashed"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by reikidude on 2009-03-03
Hi All,

I've got a bit of a problem. I wanted my desktop to look nicer and install an OSX like panel, so I looked up OSX style panel and saw a post that explained that. I started with putting in terminal the following line:

"echo 'deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) intrepid main'"

Then I had to type a vertical bar which is in the top left corner but I don't know how to type it (I've tried all key combinations I know) so I thought I enter and start a new line (I thought it meant that)
and continued typing the rest of the sentence which was:

"sudo tee -a /etc/apt/sources.list"

I entered this and then terminal froze and all package managers stopped working giving me the following error:

E: Type ‘sudo’ is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

Slowly panic is creeping in my brain and i do not know what to do.

Ofcourse it is rather stupid :redface: of me not to follow the correct coding but anyway it has happened.

I hope there is someone who can give me advice.

many thanks!

Martijn

---

### Post by taurus on 2009-03-03
Do you have this line in your /etc/apt/sources.list?

```
sudo tee -a /etc/apt/sources.list
```
You need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove it (line 56).  Otherwise, just post your /etc/apt/sources.list here.

---

### Post by kellemes on 2009-03-03
You just have some gibberish in your /etc/apt/sources.list
If you post it we'll fix it.

---

### Post by reikidude on 2009-03-03
how do I get my etc/apt/sources.list (might be a stupid question but....)

I type "edit etc/apt/sources.list and I get the following code

Warning: unknown mime-type for "etc/apt/sources.list" -- using "application/octet-stream"
Error: no write permission for file "etc/apt/sources.list"

Thanks,

Martijn

---

### Post by kellemes on 2009-03-03
> **reikidude said:**
> how do I get my etc/apt/sources.list (might be a stupid question but....

You can type the following from a terminal window and use your mouse to copy/paste the text into your post..
```
cat /etc/apt/sources.list
```

**or**

```
gedit /etc/apt/sources.list
```
and same story.. just copy/paste into your post.

---

### Post by kellemes on 2009-03-03
> **reikidude said:**
> 
I type "edit etc/apt/sources.list and I get the following code


As Taurus wrote.. if you want to edit a system-file..
```
gksudo gedit /etc/apt/sources.list
```
type your password when asked, so you get permission.

---

### Post by reikidude on 2009-03-03
this is what I got when I put in "cat etc/apt/sources.list":

deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
sudo apt-get update

---

### Post by kellemes on 2009-03-03
remove the last line (sudo..) and save the file..

Now from a terminal window enter..
```
sudo apt-get update
```

You should be fine now..

---

### Post by taurus on 2009-03-03
Are you running hardy or intrepid because I see you have both releases in /etc/apt/sources.list?

```
lsb_release -a
```

---

### Post by reikidude on 2009-03-03
It is solved thanks:D

---

### Post by kellemes on 2009-03-03
> **reikidude said:**
> It is solved thanks:D

Still Taurus's question remains.. (sorry I overlooked)
> Are you running hardy or intrepid because I see you have both releases in /etc/apt/sources.list?

It's **very unwise** to use repositories of several releases, this will inevitably kill your system sooner or later..

---

### Post by reikidude on 2009-03-03
I use intrepid. Shall I take the hardy repositories out?

Martijn

---

### Post by kellemes on 2009-03-03
> **reikidude said:**
> I use intrepid. Shall I take the hardy repositories out?

Martijn

You better do so indeed..
As far as I know you should be set after..

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by reikidude on 2009-03-03
have done everything and all is well.

Thank you very much for the help!!

Martijn

---

