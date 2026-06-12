---
title: "BOINC Manager only works with old version [6.4.5]"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by fuwkej on 2010-01-17
The standard BOINC ([http://boinc.berkeley.edu/](http://boinc.berkeley.edu/)) manager is version 6.4.5. Unfortunately, this version is in the official Ubuntu repositories, and it doesn't support ATI GPU's to increase computational power. The newest version, supposedly compatible with Ubuntu 9.10, is 6.10.17 ([http://boinc.berkeley.edu/download.php?dev=1](http://boinc.berkeley.edu/download.php?dev=1)). I downloaded the install file manually, removed 6.4.5, and installed 6.10.17. It loaded up, but was nothing more than an empty shell, could not connect to projects.

I know some of you don't like BOINC, but for me, I have to leave a computer on 24/7, and the minor increase in electrical usage is really very minor; it's fine in winter time, because it's like a very small electric heater. I compute for the Rosetta program (medical research).

Anyhow, does anyone know why Ubuntu is set to use the oldest version?

---

### Post by oldos2er on 2010-01-17
Are you sure you completely removed the old boinc manager? Anyway, if you install the getdeb.net repository, it has 6.10.17. [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

---

### Post by egalvan on 2010-01-17
> **laverabe said:**
> 
, and it doesn't support ATI GPU's to increase computational power. 
 I** compute for the Rosetta program** (medical research).

Anyhow, does anyone know why Ubuntu is set to use the oldest version?

There are far older versions of BOINC available.
generally, an Ubuntu release stays with the main BOINC release...
unless you use the getdebs as laverabe suggested.

And also, Rosetta doesn't show GPU support.
Neither BOINC's nor Rosetta's page has any mention of it.

---

### Post by fuwkej on 2010-01-17
Yes, I definitely removed all of the older version of boinc (client and manager), and I had used the getdeb version. It installed fine, but it would not connect to any projects.

6.4.5 is the oldest listed in the download section on BOINC's website, so it appears that Ubuntu uses the oldest possible one in the official repository.

I was reading on the boinc forums that Rosetta supports ATI GPU's with versions 6.8 and newer, from a BOINC forum administrator. Either way, it couldn't hurt to get the newest version to see if he was right; unfortunately 6.10 doesn't work with Karmic Koala.

---

### Post by egalvan on 2010-01-18
Hardy Heron 8.04 uses BOINC v6.2.14 :D

My Jaunty machine is down for drive replacement, so i can't check the version.

I haven't installed Karmic yet, will probably bypass it for Lucid LTS.

As I stated, Ubuntu tends to stay with the major version numbers of software, 
in order to help with stability.
Using newer major versions can require a lot of testing.

Note that it IS possible to use newer versions, 
I think that is what "back-port"-"Un-supported Updates" repos are for...
Not ALL software is updated though...
I don't use them, so i can't comment further...
hopefully others will chime in...


On my two working machines, I value stability over "newness",
so my software tends to be older versions...
but they work well.

I've got a fairly new machine that I will be using for playing with, and will use Lucid when it comes out.
And I will try to get the latest and greatest software running on it.
Including the latest BOINC.
I'll keep you posted.

BTW, any clues on the BOINC forums?



...New machine coming together...
AMD Quad Core,
8GB RAM,
one 160GB for the OS, two 1TB drives for storage,
nVidia graphics card with 1GB RAM,

That is gross overkill, but the parts were cheap...
how can anybody resist 8GB of RAM for a mere $72? :D
AMD Quad for $65?
two TB drives for $130? (the 160gb was $10, so I bought four)
nVidia card was $55
all I can say is WOW...

---

### Post by oldos2er on 2010-01-18
"unfortunately 6.10 doesn't work with Karmic Koala."

It's working fine for me.

---

### Post by fuwkej on 2010-01-18
Would you mind reviewing how you installed it? It's possible I missed something, though using the getdeb version, I don't see what I could have missed. Thanks.

---

### Post by oldos2er on 2010-01-18
I downloaded it from the Boinc website, ran sh ./boinc_6.10.17_x86_64-pc-linux-gnu.sh in my /home/user/Downloads directory, then ran ./run_manager and attached to the two projects I run, SETI@home and World Community Grid. Also I created a startup application launcher /home/user/Downloads/BOINC/run_client

---

