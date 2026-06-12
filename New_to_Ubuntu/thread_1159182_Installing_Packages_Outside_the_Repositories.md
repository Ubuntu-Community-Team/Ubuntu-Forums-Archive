---
title: "Installing Packages Outside the Repositories"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by guv999 on 2009-05-14
Hi 
I am loving Ubuntu so far, but one thing is causing me a lot of confusion, its all around installing new packages.

I am fine if the package is in one of the repositories.   My issues come when it is other software.   A typical example would be my experience installing BitDefender.     Although I got there in the end (by referring this forum), there was work to do in the command line to get it installed.  What I do not know is why I had to do this, and why it could not be installed via Gdebi.   

There are other programs where I have had this issue and gave up, but I believe if I just had a bit of more knowledge of understanding why and a few common commands to follow I would be fine

Thanks for any advise

---

### Post by Didius Falco on 2009-05-14
> **guv999 said:**
> Hi 
I am loving Ubuntu so far, but one thing is causing me a lot of confusion, its all around installing new packages.

I am fine if the package is in one of the repositories.   My issues come when it is other software.   A typical example would be my experience installing BitDefender.     Although I got there in the end (by referring this forum), there was work to do in the command line to get it installed.  What I do not know is why I had to do this, and why it could not be installed via Gdebi.   

There are other programs where I have had this issue and gave up, but I believe if I just had a bit of more knowledge of understanding why and a few common commands to follow I would be fine

Thanks for any advise

Hi and welcome to the Ubuntu community.

Just going by what you have posted, it sounds to me like what you had to do with BitDefender was to compile the program.

Some programs you get off the net come already compiled in the proper format for the "flavor" of linux that you use. In the case of Ubuntu, that would be *.deb files, since Ubuntu is part of the Debian branch of linux.

Other times, you won't be able to find a pre-compiled version, or more advanced users may want to compile the package in a custom way. When that happens you will usually be downloading a compressed file that contains the "raw" code, which you then have to extract and run a series of commands on (one you'll see/use a lot is "make"  - is that familiar?) in order to compile the source code into a format that can be installed.

GDebi installs deb files, but can't compile the source code into one.

I hope this helps...

Regards,

Didius

---

### Post by bacardiandwatermelon on 2009-05-14
From memory Bit Defender is a run file... Most of the time the files a deb files and you can just double click them :-)

---

### Post by NESFreak on 2009-05-14
indeed, try looking if someone is offering a .deb file. You could just double-click them and they'd install. Most software makers provide them these days, however some may not. Luckily there are many people using ubuntu, so even if the softwaremaker didn't create a .deb file, someone might have posted it here on the forum. Another site to look for .deb files is [www.getdeb.net](www.getdeb.net) 

The problem with bitdefender however is that it is a proprietary piece of software, probably even forbidding people to create their own installers.

BTW since your new to linux, may i ask why you'd want to use a virusscanner? It looks to me as if the only useful application would be in an server like environment.

nesfreak

---

### Post by XCan on 2009-05-14
> **Didius Falco said:**
> Hi and welcome to the Ubuntu community.

Just going by what you have posted, it sounds to me like what you had to do with BitDefender was to compile the program.

Some programs you get off the net come already compiled in the proper format for the "flavor" of linux that you use. In the case of Ubuntu, that would be *.deb files, since Ubuntu is part of the Debian branch of linux.

Other times, you won't be able to find a pre-compiled version, or more advanced users may want to compile the package in a custom way. When that happens you will usually be downloading a compressed file that contains the "raw" code, which you then have to extract and run a series of commands on (one you'll see/use a lot is "make"  - is that familiar?) in order to compile the source code into a format that can be installed.

GDebi installs deb files, but can't compile the source code into one.

I hope this helps...

Regards,

Didius

Just wanted to add that usually, by following the instructions in a readme or an install file the user can manage to compile the code. However, the next step which is according to me very confusing and unclear, is where to put the binaries, and how to make them accessible easily.

---

### Post by sgosnell on 2009-05-14
Binary files go in /bin or /usr/bin, preferably the latter for user-installed programs.  Both directories should be in the path.

---

### Post by guv999 on 2009-05-14
Hi everyone - thanks for all the help - it is all much clearer now.

Hi NESFreak - the only reason I am looking to run a virus scanner at all is because I occasionally use my PC for work purposes and receive//send emails and attachments from//to a Windows network so just want to be sure what I am sending is clean. What is great about Linux is not having to constantly have anti-virus and spyware protection running in the background all the time

---

