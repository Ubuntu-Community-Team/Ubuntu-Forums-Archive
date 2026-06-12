---
title: "Offline Synaptic Manager"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Ratul Saha on 2010-08-26
[FONT=Comic Sans MS][SIZE=4]Hi,
I have gone through severe problem while installing ubuntu in an offline computer. As all the packages are suitable for online installation, it is very very hard to solve dependency for even small softwares.

I am currently trying to make an offline-mode (almost) synaptic manager, which will come with a CD/DVD, which will have lots of software package files (with dependent ones). I am currently saving them from my /var/cache/apt/archives.

The problems I am facing are following:

1. What is the minimal GUI application which will run in a just started ( no update ) ubuntu? At least after minimal package installation?

2. I want to keep track of the dependency tree totally. All I can get is the level wise list from synaptic or packages.ubuntu.com, which makes life harder to keep track of.

If anyone knows any work on this, or is working, or is willing to help me, please come forward. To spread ubuntu locally, it is the hardest hurdle.

Thanks in advance,

Ratul.
[/SIZE][/FONT]

---

### Post by mastablasta on 2010-08-26
What about Ubuntu DVD? Doesn't it have more programmes on?

---

### Post by Ratul Saha on 2010-08-26
They don't give a chance. I don't mean finding one by one and uninstalling. And why should I install large things while I get beautiful simple ubuntu, and then installing the software one by one?

Hope you get my point,

Thanks a lot for your concern,

Ratul.

---

### Post by jazzerit on 2010-08-26
If you have another computer connected to the internet, you can use the Ubuntu live CD and a memory stick.
First, boot up the live cd. Once it has booted up, go to the synaptic package manager with system>administration>synaptic manager It may ask to reload the package list; if it does, allow it to do so. Once it's done that, search for the program you need, and mark them. Now,  click on file>generate package download script. Choose where to save it. Close synaptic package manager. Finally, run the download script, and put the .deb files on your memory stick. Then you should be able to install those on the other computer. Hope this helps.

---

### Post by Ratul Saha on 2010-08-26
This is how I installed vlc in my firend's comp. Absolutely no cyber cafe, at least in India, run linux, so I used my lappy and generated the script. The pain was when I had simple library files installed earlier ( which we overlook when upadating and a lot of stuff ) and which the script will not generate.

I don't see why ubuntu, the coolest linux distro does not have a way of complete software collection. I don't want to frighten first users with library files ( which they have no idea about ).

No one is excited about making it in one CD? ( I know upgrading matters, but it is worth having in countries like India where internet is not that available ).

Thanks a lot for your concern,

Ratul.

---

### Post by jazzerit on 2010-08-26
another thing you could look at on an online computer is [http://portablelinuxapps.org/](http://portablelinuxapps.org/)- not many apps yet, but they are executables which contain everything a program needs to run. You could also look at [keryx]("http://keryxproject.org/")- I haven't had time to look at it very much, but it looks promising... Also, it's got a windows binary, so you can run it from windows computers as well...

---

### Post by gpdas on 2010-08-26
Hi Ratul
I think exactly the same way you think. I am trying with APTonCD right now. But in case u get a better solution be in touch with me via email.
[EMAIL="gpdas.bsnl@gmail.com"]gpdas.bsnl@gmail.com[/EMAIL]
All the best.

---

### Post by Ratul Saha on 2010-08-26
@[jazzerit]("http://ubuntuforums.org/member.php?u=992568")
Thanks for the sites, they are giving some good softwares. And the idea of portability is really cool.

@gpdas
Thanks for your concern. I will keep in touch with you.
PS: What ApTon cd do is pretty trivial, you canfind them in /var/cache/apt/archives. But if you run some cleaner software ( like amazing bleachbit ), they are deleted.

Thanks,

Ratul

---

### Post by Ratul Saha on 2010-10-17
Hi,
I solved the dependency problem with **apt-cache --recurse depends** *:), but unfortunately it is not working in offline computer. Is there any way to get dependency from the package file itself( before installing )?

---

