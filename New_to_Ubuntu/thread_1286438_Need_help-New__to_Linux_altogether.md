---
title: "Need help-New  to Linux altogether"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by bigchefjoe on 2009-10-09
I was trying to get Movie Player or VLC player to play Regular Motion Picture DVD.
I thought i was doing it right then i got this error:

E: Type '--2009-10-08' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

im not sure what i did wrong or how to fix it. been searching different articles on line but no help

Joe

---

### Post by ccleanerfan on 2009-10-09
I think dvd isnt supported by ubuntu naturally, you need some program somewhere. not sure.

---

### Post by rippin on 2009-10-09
> **bigchefjoe said:**
> I was trying to get Movie Player or VLC player to play Regular Motion Picture DVD.
I thought i was doing it right then i got this error:

E: Type '--2009-10-08' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

im not sure what i did wrong or how to fix it. been searching different articles on line but no help

Joe

Not enough information given, but let's try some guesses:

1) failed install
2) post your /etc/apt/sources.list
3) user (sorry, that's you) goofed following adding that source to list, doing apt-get update or another related step
4) what's the Ubuntu version and kernel in use

-- 
rippin

---

### Post by bigchefjoe on 2009-10-09
i was adding the following:
[INDENT]sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list


 sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update


 sudo apt-get install libdvdcss2
[/INDENT]when i got the following error:

E: Type '--2009-10-08' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I am trying to figure out how to correct the error

any help?

---

### Post by PrePenguin on 2009-10-09
when i got the following error:

E: Type '--2009-10-08' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I am trying to figure out how to correct the error

any help?[/quote]
  
I am noticing that the date is listed maybe it does not like the file name or something to that effect.. As u can see it is specifically refering to the date.

---

### Post by bigchefjoe on 2009-10-09
Rippin,

Hope i can find what you need, still new at this. Here is the sources list.

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by bigchefjoe on 2009-10-09
yes, i see the date. how does one correct this error?

---

### Post by rippin on 2009-10-09
> **bigchefjoe said:**
> Rippin,

Hope i can find what you need, still new at this. Here is the sources list.
<snipped>



Sorry guy, my bad. Didn't notice "/etc/apt/sources.list.d/medibuntu.list" as the whole path earlier. Post that file content. Plus, that command is NOT what I used. Maybe you will find this link useful: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) . I had no problems getting DVD playback and mp3 to work using those instructions.

-- 
rippin

---

### Post by bigchefjoe on 2009-10-09
here is the new info.

--2009-10-08 16:57:38--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 276 [text/plain]
Saving to: `hardy.list'

     0K                                                       100% 7.92M=0s

2009-10-08 16:57:38 (7.92 MB/s) - `hardy.list' saved [276/276]

---

### Post by PrePenguin on 2009-10-09
So it was looking for a mirror to correct this issue? Am i getting this right?

---

### Post by bigchefjoe on 2009-10-09
it looks like the date entry is the problem, but is there anyway tojust back the whole thing off and try it again?

---

### Post by rippin on 2009-10-09
> **bigchefjoe said:**
> here is the new info.

--2009-10-08 16:57:38--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
Resolving [www.medibuntu.org]("http://www.medibuntu.org")... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80]("http://www.medibuntu.org%7C87.98.242.110%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 276 [text/plain]
Saving to: `hardy.list'

     0K                                                       100% 7.92M=0s

2009-10-08 16:57:38 (7.92 MB/s) - `hardy.list' saved [276/276]

That looks like an output of an action. Is that from "/etc/apt/sources.list.d/medibuntu.list"?:confused:
Thought you are using 9.04, yes? Why then is it for "hardy.list"? You may want to rename that file and go through the URL I mentioned command-by-command. Ask here about it if you'd like.

---

### Post by bigchefjoe on 2009-10-09
yes this is from "/etc/apt/sources.list.d/medibuntu.list"?
yes it is 9.04, i may have tried to use the 8.04 version by mistake. yes comand by comand please, treading in new territory here for me

---

### Post by rippin on 2009-10-09
> **bigchefjoe said:**
> yes this is from "/etc/apt/sources.list.d/medibuntu.list"?
yes it is 9.04, i may have tried to use the 8.04 version by mistake. yes comand by comand please, treading in new territory here for me

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list

 ... use sudo to grab file and output it to another file

&& 

... if that command works, go to the next

sudo apt-get -q update 

... update apt-get database "quietly"


&& sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring

... seems obvious 

&& sudo apt-get -q update

... update apt-get database

sudo apt-get install libdvdcss2

... installs libdvdcss2 (for encrypted playback of DVD)

"**With individual packages**

 If you wish to install just libdvdcss2, you can first download the individual package and then install the package. "
... obvious, arranged by arch (i386, **amd64**:, and **powerpc**)

"[SIZE=2]Playing Non-Native Media Formats[/SIZE]

[LIST]
[*]For **i386**, the package is called **w32codecs**: 
sudo apt-get install w32codecs
[*]For **amd64**, the package is called **w64codecs**: 
sudo apt-get install w64codecs
[*]For **ppc**, the package is called **ppc-codecs**: 
[LEFT]sudo apt-get install ppc-codecs[/LEFT]
[/LIST]
[LEFT][FONT=sans-serif].[/FONT][FONT=sans-serif].. again, obvious
[/FONT][/LEFT]

---

### Post by bigchefjoe on 2009-10-09
sudo apt-get -q update 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Fetched 198B in 1s (133B/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

i ran  apt-get update and gothe the same error

---

### Post by bigchefjoe on 2009-10-09
also i tried to rename the file but it was greyed out and wouldnt let me

---

### Post by rippin on 2009-10-09
> **bigchefjoe said:**
> sudo apt-get -q update 
<snip>
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

i ran  apt-get update and gothe the same error

Get the key ... tried that URL yet? ;)

---

### Post by rippin on 2009-10-09
> **bigchefjoe said:**
> also i tried to rename the file but it was greyed out and wouldnt let me

sudo <your preferred editor> <file name>

---

### Post by bigchefjoe on 2009-10-09
seems to be loading and exracting.
all is working fine. Just tried a DVD loaded and played fine, no problems.

Thank You so much for all your help

BigChefJoe

---

