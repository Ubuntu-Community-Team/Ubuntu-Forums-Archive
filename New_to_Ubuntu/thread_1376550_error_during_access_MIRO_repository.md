---
title: "error during access MIRO repository"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by onegallon on 2010-01-09
;)In reponse to Welcome screen's suggestion to try Miro's flash player, attempted to follow Miro's Installation Instructions, but at step 4. "Add repository line for the version you're using", entered deb for Karmic (9.10). Marked and was prompted
to Reload, which did. Error window appeared as follows:
                           'update-manager '
                           'package and include'
'E: malformed line 54 in source list/etc/apt/sources.list (dist parse)
E: the list of sources could not be read.
go to repository diaolog to correct problem
E:_cache_open () failed, please report
 
Toggled red X 
 
Error window also blocked access to synaptic packaging manager.
Recovered by >system>software sources>other sources, unmarking MIRO
deb file and reloading.
 
Does toggling red X automatically report error to UBUNTU? I subsequently
got message to report error of malformed line 54, etc. If toggling red X doesn't
automatically report, where, then, should manual report be made?
 
Seems like cited error may be corrupted file in MIRO's source list. Does ubuntu
share relevent  error reports with MIRO?

---

### Post by Elfy on 2010-01-09
You need to check your sources list

```
cat /etc/apt/sources.list
```

All lines should start with #, deb or deb-src

If you're not sure post it here

---

### Post by onegallon on 2010-01-09
> **forestpiskie said:**
> You need to check your sources list
 
```
cat /etc/apt/sources.list
```
 
All lines should start with #, deb or deb-src
 
If you're not sure post it here
 
Did as recommended and read. Noted many disclaimer comments.
 
Noted following listed debs:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) partner
deb src [http://src archive](http://src archive).canonical.com/ubuntu karmic partner
 
My software sources>other software currently has original two listings:
http:archive.canonical.com/ubuntu Karmic partner
http:archive.canonical.com/ubantu Karmic partner (source code)
 
Both are marked and apparantly implemented.
 
Not sure how your reference then applies to error experienced.
 
Temporarily on hold for accesssing MIRO pending further advice.
 
Thanks for your help.:)

---

### Post by Elfy on 2010-01-09
Please run the command in a terminal and post the resulting output here - the error is on line 54.

---

### Post by onegallon on 2010-01-09
> **onegallon said:**
> Did as recommended and read. Noted many disclaimer comments.
 
Noted following listed debs:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) partner
deb src [http://src archive](http://src archive).canonical.com/ubuntu karmic partner
 
My software sources>other software currently has original two listings:
http:archive.canonical.com/ubuntu Karmic partner
http:archive.canonical.com/ubantu Karmic partner (source code)
 
Both are marked and apparantly implemented.
 
Not sure how your reference then applies to error experienced.
 
Temporarily on hold for accesssing MIRO pending further advice.
 
Thanks for your help.:)
 
Confused. Is the "command" you asked me to run in Terminal the "deb http:\\ftposuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu karmic/" I
entered and enabled in Other Software? Please further advise. Thanks

---

### Post by Elfy on 2010-01-09
Sorry - open the terminal and run

```
cat /etc/apt/sources.list
```

it will return a long list, paste that all into a reply.

---

### Post by onegallon on 2010-01-09
> **forestpiskie said:**
> Sorry - open the terminal and run

```
cat /etc/apt/sources.list
```it will return a long list, paste that all into a reply.
Pasted terminal contents:;)

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by Elfy on 2010-01-09
mmm - odd

Open a terminal and run this please

```
sudo apt-get update
```

once it is run - please paste the whole of the terminal output here.

---

### Post by onegallon on 2010-01-09
> **forestpiskie said:**
> mmm - odd

Open a terminal and run this please

```
sudo apt-get update
```once it is run - please paste the whole of the terminal output here.

terminal copy paste:

frank1@ubuntu:~$ sudo apt-get update
[sudo] password for frank1: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                     
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]             
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [128kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [39.7kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [78.5kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [19.1kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [6,860B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [3,831B]
Fetched 320kB in 23s (13.8kB/s)                      
Reading package lists... Done
frank1

---

### Post by onegallon on 2010-01-09
Not sure what you're asking for-when I clicked quick reply token on last message this window came up. Please advise which posts and the location of the tokens (lower right of postings?). If so, do I say anything in the message window?

---

### Post by Elfy on 2010-01-10
there's nothing wrong there.

Try doing whatever it was you did last time that gave you the error.

If it fails again - tell us where you are going to get the miro repository from and any other information you mihgt have.

---

### Post by onegallon on 2010-01-10
Thanks for the help. The error occurred at step four of the MIRO installation instructions. Somehow
I managed to enter the deb file directly on the window first and toggle "add" second (Murphy's Law). I recall that the deb file appeared on the screen as a deb rather than an http, and that apparantly precipitated the error. This time I toggled "add" first and the pop-up screen prompted me to enter the deb file, which I did, and the repository loaded fine. For "Dilberts" like me, it would have been helpful if  Miro instruction 4. had read something like "toggle add and then enter the repository line for the version of ubuntu you're using when prompted". Part of the problem is that the MIRO instructions seem to have been written for other or older versions of UBUNTU. Will now go back and try to determine how I managed to enter the deb file directly to the window and advise.

---

### Post by onegallon on 2010-01-10
Tried to enter deb on screen directly, but couldn't; however, found I could enter a bad repository line in the pop-up window (left out [http://)]("http://%29") and the bad line appeared on Other Packaging window as entered. On reload this caused error window to pop up and block synaptic packaging manager window as before, with the same or similar error description "malformed line 55 in source list" etc. 

Recovered as before:system>administration>software sources>other software, then unmarking and removing the defective entry. Will mark thread solved. Thanks again for your help.

---

### Post by Elfy on 2010-01-11
Not really sure what it is that you are doing that causes the error - I just followed the miro instructions [here]("http://www.getmiro.com/download/for-ubuntu/") and it worked fine - although in karmic I do not have a 3rd party tab.

Glad you are sorted now though.

---

### Post by onegallon on 2010-01-11
You can cause error by dropping "http//" when entering the repository line after the "enter complete APT" prompt. Error window will persistantly block Synaptic Packaging Manager Window by refusing to
"close". Interestingly, this did not happen when I deliberately made the simple omission of "p" from "pculture".

---

