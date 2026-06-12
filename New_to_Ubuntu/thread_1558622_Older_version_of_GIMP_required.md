---
title: "Older version of GIMP required"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by hatrack on 2010-08-22
Hi All !

I have been running Linux (Hardy) for the past two years and during all of that time, I have found it to be excellent and stable. Foolishly, however, I accepted the suggestion from the Repos to up-grade to Ver 10.04 ... and that is where all my problems have arisen. Every attempt to install, either from a commercially-available DVD, or from an ISO image made from a down-load from Canoniacal has failed at the very last stage with the error message "Irrevocable Error !" ... which doesn't help the diagnosis of the problem one little bit !

I am totally exasperated with this Distro after more than three very long days spent working on the problem and I have therefore decided to go back to Hardy. I have installed this from a commercially-produced DVD without any difficulty whatsoever but I have now encountered a further problem in getting a copy of GIMP for my photo-processing.

The latest version available in Synaptic is 2.4.5-1 , which I know is full of bugs. For the past year ... I have been using Ver 2.6.6., with total satisfaction. However, I have searched but cannot find this Ver (which I know works with Hardy and is totally suitable for my needs). 

Can anyone on this Forum kindly advise me where I can get the older version of GIMP (2.6.6.) ?

Best regards to all ...

---

### Post by marshmallow1304 on 2010-08-22
Did you try a fresh install rather than an upgrade?

In any case, you can get GIMP 2.6.6 here:
[http://packages.ubuntu.com/jaunty/gimp](http://packages.ubuntu.com/jaunty/gimp)
though you may need to also download some newer versions of its dependencies if those are not available in Hardy.

---

### Post by hatrack on 2010-08-22
Thank you Marshmallow !

In answer to your question, all of my installations were complete ... wiping out the old Op Sys and installing to the whole of the disc.

However, I've decided to stay with Hardy, because (a) Lucid is very difficult to install and (b) It just doesn't really have any enhancements which would make all this trouble worth-while.

Following on from your suggestion, I have followed up the link you kindly provided and have down-loaded GIMP 2.6.6. but, because of un-satisfied dependencies, installation of this failed (as you anticipated). Unfortunately, I am now "a bit out of my depth". There is a whole list of dependent files on the site ... do I down-load these one-at-a-time and try to install them individually ... or is there some way to turn them into an installable package ?

Sorry for daft "newbie" questions but ... I'm stuck and don't know enough yet to find the answer for myself.

Many thanks and best regards ...

---

### Post by lykeion on 2010-08-22
Hi
From what I can gather you want to:
* Use Ubuntu Hardy
* Use Gimp 2.6.6 (from Ubuntu Jaunty)

You could download and install manually like above poster suggests 
- and, yes, you would need to do this with all the dependant files. 
Plus all the dependencies of the dependant files as well.

I guess a simpler way would be to temporarily use the jaunty repositories, 
install gimp and all its deps, then revert back to hardy.

But why do you think a Lucid installation is harder than installing Hardy? 
Download the iso image and burn to a CD, 
then proceed just like you did with Hardy.

There are benefits with Lucid:
* It's a LTS release and very stable
* Better hardware support

---

### Post by marshmallow1304 on 2010-08-22
I don't know how well this works on Ubuntu, but a similar process works on Debian, so it might be worth a shot.

This basically tells the system to use the Hardy repositories by default, then adds entries for the Jaunty repositories and installs GIMP from the Jaunty repositories.  Open Applications->Accessories->Terminal and paste this in.
```
sudo su
echo APT::Default-Release \"hardy\"\; >> /etc/apt/apt.conf
echo >> /etc/apt/sources.list
echo \# Jaunty repository for GIMP >> /etc/apt/sources.list
echo deb http://uk.archive.ubuntu.com/ubuntu/ jaunty main >> /etc/apt/sources.list
echo deb http://uk.archive.ubuntu.com/ubuntu/ jaunty-updates main >> /etc/apt/sources.list
apt-get update
apt-get install -t jaunty gimp
exit
```

---

### Post by hatrack on 2010-08-22
Hi All !

My thanks for your replies to my enquiry.  

There are several points here which need an answer from me but, as it is now after mid-night, I will have to leave this task for tomorrow when I will be able to write a proper answer.

Regards to all for now ... more within 24 hrs ... I promise !

---

### Post by hatrack on 2010-08-23
Hi All !

As promised last night, I submit the fuller report on my activities so far --

Essentially, there are two matters being discussed here --
(1)  My un-satisfactory experience trying to up-grade to Lucid and the activities that followed from this

(2)  My efforts to get a copy of GIMP which I can trust (Ver: 2.6.6.)

Dealing with these in order --
My system had been running Hardy without problems for nearly two years and I had GIMP Ver: 2.6.6. installed on this. This Ver of GIMP handled my photo-processing perfectly for my needs.

I have always downloaded the up-grades offered automatically by the Repos and recently, having done this, I was foolishly tempted to accept the automatic up-grade to Lucid which was offered. The download and subsequent installation ran perfectly until, right at the very end of the process, an "Un-recoverable error" was reported. The system then locked up with keyboard and mouse completely disabled. The ONLY way to regain control of the machine was to turn off the power ! ... NOT GOOD !

When I re-booted, I got the error message "Analog Screen ... not supported" and again, the computer locked up. So, effectively, it could not now be booted at all. I had to therefore boot from a DVD. I had a commercially-produced Lucid DVD available, so I used this and regained access to the computer. Since the original up-grade process had obviously become corrupted in some way, I felt the logical course was to do a full installation ... reformatting the Drive and using all of this. This drastic course was selected since I judged it likely to produce the most stable final installation. Again, this ran nearly to completion until reporting an error on the DVD. Again, the installation had failed whilst incomplete and so, again, the computer could not be booted.

Fortunately, I had still available an old copy of a commercially-produced DVD for Hardy. I used this to re-boot the machine and then did a complete install of this Ver. This worked perfectly, including automatically requesting and installing about 200 upgrades that had accumulated in the Repos since this old DVD was made. Initially, at that point, I decided that I wouldn't mess about any further with Lucid and proceeded to re-create my old configuration. It was at this point that I found I was apparently unable to any longer get a copy of GIMP 2.6.6. and I was loathe to down-load more-recent Vers because I anticipated problwems with dependencies.

Since I was unable to down-load a copy of GIMP 2.6.6., I then decided to try another installation of Lucid. I down-loaded from the Repo and burned an ISO image to DVD, as suggested by Lykeion. This was tested for possible corruption after burning and was reported to be OK.  When, however, I tried to do a complete new install from this DVD, once again, the process failed right at the end and the machine locked up yet again. So ... re-install Hardy ... again !

At least I can now write to the Forum and seek help and advice.

Turning now to the procedures suggested by Marshmallow, all have failed because of un-satisfied dependencies. This applies equally to the suggestion to access the Jaunty Repos, using Terminal.


I'm now beginning to wonder if I have some sort of incompatibility between Lucid and my hardware.

My computer is a Dell Optiplex GX-520 (3.2 Mhz processor) with 1 Gb of DRAM installed.

Any comments or suggestions will be most gratefully received. I apologise for the length of this Post.

Regards to all ....

---

### Post by marshmallow1304 on 2010-08-23
All right, it was worth a shot.  You can go ahead and undo what was done by hitting Alt+F2 and entering
```
gksudo gedit /etc/apt/apt.conf
```
and removing the line beginning with
```
APT::Default-Release
```
Save and close, hit Alt+F2 again and enter
```
gksudo gedit /etc/apt/sources.list
```
and remove the jaunty lines (should be the last 3).
Save and close then open System->Administration->Synaptic and reload.


I have one more idea: if you go to System->Administration->Software Sources, is there any option there to enable backports?  You could enable backports and see if there's a newer version of GIMP available from those.  EDIT: I checked out Hardy backports and the GIMP available there is 2.4.6.

Otherwise, you could try to download GIMP and the necessary dependencies (and their dependencies) manually from the link above, but that could take a while.

---

### Post by hatrack on 2010-08-23
Thank you Marshmallow !

I'm a bit tied up this evening but I'll try your idea in the morning and report back to you tomorrow.

This is what I like about Ubuntu ... super support from the Forums ... far better (and cheaper) than one ever gets for any version of the "'Doze" ! ...

Best regards ...

---

### Post by jtarin on 2010-08-23
> The latest version available in Synaptic is 2.4.5-1 , which I know is full of bugs. For the past year ... I have been using Ver 2.6.6., with total satisfaction. However, I have searched but cannot find this Ver (which I know works with Hardy and is totally suitable for my needs).

Can anyone on this Forum kindly advise me where I can get the older version of GIMP (2.6.6.) ?Gimp 2.6.6 is not older than 2.4.5-1..... 2.6 version is readily available....you might try to compile or [this]("http://angpilipinogimp.wordpress.com/2008/10/07/install-gimp-26-on-ubuntu-804-hardy-heron/")

---

### Post by hatrack on 2010-08-24
> **jtarin said:**
> Gimp 2.6.6 is not older than 2.4.5-1..... 2.6 version is readily available....you might try to compile or [this]("http://angpilipinogimp.wordpress.com/2008/10/07/install-gimp-26-on-ubuntu-804-hardy-heron/")


I apologise for causing some confusion here ... my searching revealed that the latest Ver of GIMP is 2.6.10.  The ver I have been using with Hardy is 2.6.6. Hardy will be at the end of its LTS life next year, so it's unlikely that the Repos for this will be up-dated further. The latest ver of GIMP held there is 2.4.5.

It is in the sense that ver 2.6.6. preceeds ver 2.6.10. that I referred to GIMP 2.6.6. as "old".

I have considered downloading and compiling but it is something that I have never tried before ... so I could encounter some problems. With that said ... I will look at the link you kindly provided.

An alternative for me is to convert the whole machine to Win2K for my photo-processing work, since I have a copy of GIMP 2.6.6. which runs in that environment.  I presently do have another computer networked to the Linux machine which runs legacy hardware for which I cannot get Linux drivers. My idea would be a very good solution all round. I could put Hardy on the old Pentium III machine and use this solely for secure comms to the 'Net so as to get the security of Linux. Meanwhile, I could exploit the easy installation characteristics of Win2K for my photo-processing work and keep this larger machine isolated from the outside world .

My thanks and Best regards to all ...

---

### Post by lykeion on 2010-08-24
Hi
To get back to your problem with installing Lucid on your Dell Optiplex GX520. 
I have googled and searched in the forum and found people both having successfully installed Lucid, 
and people having troubles. 
Someone with problems installing 8.10 on his Dell GX520  had success with the Alternate Install CD 
(instead of the usual Desktop CD). Maybe you could try that?

Alternate CD ISO is found here:

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

It's a text-based installation but otherwise it's the same as the usual CD.

---

