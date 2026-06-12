---
title: "Newbie, first time here and a question."
date: 2011-04-20
forum: New to Ubuntu
---

### Post by vulcaninvt on 2011-04-20
Hello All,

I am very new to Ubuntu and look forward to getting my feet wet! 

I am writing a tutorial for a class that I am taking and I would like to give the tutorial on how to install a program in Ubuntu. I am going to be using [FONT=Verdana][SIZE=1][SIZE=2]the synaptic program manager. I would like to download a program from the web and install it using the manager, could anyone point me in the direction of a program to use in this demonstration?

Thanks for the help!
Ryan 
[/SIZE][/SIZE][/FONT]

---

### Post by LOIREE on 2011-04-20
Hey! :)

Use my guide:
[http://www.wawuk.net/ubuntu/basics/step10](http://www.wawuk.net/ubuntu/basics/step10)

---

### Post by XubuRoxMySox on 2011-04-20
> **vulcaninvt said:**
> Hello All,

I am very new to Ubuntu and look forward to getting my feet wet! 

I am writing a tutorial for a class that I am taking and I would like to give the tutorial on how to install a program in Ubuntu. I am going to be using [FONT=Verdana][SIZE=1][SIZE=2]the synaptic program manager. I would like to download a program from the web and install it using the manager, could anyone point me in the direction of a program to use in this demonstration?

Thanks for the help!
Ryan 
[/SIZE][/SIZE][/FONT]

Hi, and welcome!

One of the reasons that Linux is so awesomely secure is that you don't ordinarily download anything from the web to install on your 'puter! You might add a trusted software *repository* to your sources (using Synaptic), then refresh Synaptic and use it to download from the repository you added.

One trusted repository that alot of folks add is "[getdeb]("http://www.getdeb.net/welcome/")." The "**deb**" part on the name refers to the way software is packaged for **Deb**ian and Ubuntu.

Most Linux folks strongly discourage users - especially new users - from downloading software directly from the web.

Hope that helps,
Robin

---

### Post by vulcaninvt on 2011-04-20
Thanks!

I appreciate the quick feed back and advice! I am really digging Linux and Ubuntu and all this fun new learning. I do not think it will be too long before I am addicted... It all started with my Android phone :)

---

### Post by centaurusa on 2011-04-20
You didn't say which version of Ubuntu you are using, but I assume it is current, in which case you will not have the GIMP available.  

This is a really good digital image editor (a bit like Photoshop) and used to be part of the Ubuntu installation.  It's simple to locate and install from Synaptic Package Manager.  Just type GIMP in the search box and hit return.

Obviously, there are many programs that you could install for your purposes, but this is the one that I always load first after a fresh install of the latest Ubuntu release.

---

### Post by vulcaninvt on 2011-04-21
Thanks Centaurusa,

I am running 10.10 at this time, I will find that program and do a step by step for installing it and using that as my tutorial for class!

I have a few questions, well several, but I will start with a few.

1.) after installing Ubuntu onto my system (duel boot) I restarted the computer and was prompted with the GRUB which OS to choose. It seems somewhere down the line of installing something got corrupted and I was brought to a DOS screen and for the life of me couldn't get it booted, so I started over and with a 2nd attempt have Ubuntu up and running.   With the GRUB option I see Vista on there, no clue how that is on there I run a Windows 7. Any thoughts? 

2.) The 2nd time I installed Ubuntu it only gave me an option for Vista (Loader) and very little hard drive space, about 8G, the minimum to set it up.  Any thoughts on how I can grab some more space from the other drive?

Sorry if this is all convoluted and doesn't make sense!

---

### Post by centaurusa on 2011-04-21
>With the GRUB option I see Vista on there, no clue how that is on there I  run a Windows 7. Any thoughts?

GRUB (actually GRUB2, GRUB is now termed Grub Legacy) is sometimes "confused" about which actual version of Windows is available.  On my Vista dual-boot system, it refers to the Windows 7 loader - but, I know what it means.

>The 2nd time I installed Ubuntu it only gave me an option for Vista  (Loader) and very little hard drive space, about 8G, the minimum to set  it up.  Any thoughts on how I can grab some more space from the other  drive?

I like to set up a block of unallocated space on my hard drive, by resizing partitions before I start installing Ubuntu, by using a bootable GParted disk.  In theory, you can do this from the Ubuntu Live-CD, but I don't have problems when I use a "real" version of GParted.

There is lots of info. posted on the web on how to use GParted.  See, for example:

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Blasphemist on 2011-04-21
This is a great link to installation of dual boot configuration.

[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

And welcome to the world of ubuntu!

---

### Post by Fraoch on 2011-04-21
> **vulcaninvt said:**
> Hello All,

I am very new to Ubuntu and look forward to getting my feet wet! 

I am writing a tutorial for a class that I am taking and I would like to give the tutorial on how to install a program in Ubuntu. I am going to be using [FONT=Verdana][SIZE=1][SIZE=2]the synaptic program manager. I would like to download a program from the web and install it using the manager, could anyone point me in the direction of a program to use in this demonstration?

Thanks for the help!
Ryan 
[/SIZE][/SIZE][/FONT]

If you wanted to teach something, then yes, Synaptic.

If you wanted to impress them, then the Ubuntu Software Centre.  That's something not even Windows has - a central location where you can locate any software you might need by typing its name or a description.  The software comes from official sources, is just about guaranteed to work and is protected against malicious alteration.  It installs in a single click.  You don't even have to save an .exe file.  I view it as a response against the old "it's hard to install software in Linux" argument.  In fact, it's now *easier*.

N.B. - the pros do not like the Software Centre.  I got used to Synaptic and also apt-get so I do most things using those methods.  Synaptic will give you lots more information and is also useful for finding out information about what programs are already installed and where their files are, plus it can search for programs you haven't installed.  Apt-get is useful and fast if you know what the program names are.  However for newbies and those skeptical about Linux and Ubuntu, the Software Centre is pretty neat.

---

### Post by vulcaninvt on 2011-04-21
Thank you everyone for the help, I am doing this for a class and want to make sure that I am providing accurate information. One thing that I am noticing when I attempt to install digiKam, I am getting a warning "Requires installation of untrusted packages", I am doing this though the software center, I was getting similar messages from Synaptic.  

Is this normal? I do not want to set up a tutorial using software that may be harmful, but I have tried a few and received that same message.  

Thank!

---

### Post by oldos2er on 2011-04-21
"Requires installation of untrusted packages" means you're missing one or more gpg keys. Synaptic should show you the repositories that are missing keys; or if you run **sudo apt-get update** in a terminal, it will also show you the repos missing a key.

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

### Post by Fraoch on 2011-04-22
> **vulcaninvt said:**
> Thank you everyone for the help, I am doing this for a class and want to make sure that I am providing accurate information. One thing that I am noticing when I attempt to install digiKam, I am getting a warning "Requires installation of untrusted packages", I am doing this though the software center, I was getting similar messages from Synaptic.  

Is this normal? I do not want to set up a tutorial using software that may be harmful, but I have tried a few and received that same message.  

Thank!

This is another great thing about installing software this way - it must all be trusted and authenticated and if it isn't it won't let you!  It's the package manager doing what it's supposed to do.

GPG keys are only issued to new developers whom more established developers have personally met.  See [http://en.wikipedia.org/wiki/Key_signing_party](http://en.wikipedia.org/wiki/Key_signing_party)

Go to the home page of the repository you're trying to install from.  Most of them have instructions how to add their key to your system.  Be wary of the ones that don't list their keys.

---

### Post by vulcaninvt on 2011-04-22
Thanks! 

I poked around a bit, I installed Ubuntu through VMware and that is where I was having some trouble with the keys and downloading. I was able to use the Software Center with no problem on my Dual Boot machine.  I have found that if I am not connected to the internet and trying to install Ubuntu it really doesn't give a clean install.  At work now with no connection so I am going to have to try again later tonight !

---

### Post by mastablasta on 2011-04-22
that's because when you click install it will download the necessary files form internet and connect them with your local libraries, create any shortcuts (if necessary) and thus install the programme :-)

---

### Post by vulcaninvt on 2011-04-22
Mastablasta,

I am having issues getting a clean install here at work, I am not able to connect to the internet, do you think this is the reason for it not installing cleanly? 

I try and boot into Ubuntu and I am only getting to a DOS command line, with my username/passord.. no GUI.

---

### Post by Blasphemist on 2011-04-22
Not being able to connect to the internet is not your issue. Some people recommend not connecting during the installation. Please post more detail about what happens and when.

---

### Post by vulcaninvt on 2011-04-22
I will not be able to attempt again until later on this evening. 

This issue that I have ran up against twice is after I try to boot into Ubuntu.  I get all sorts of text, is this a script? At the end of the text it asks for my username, I type that it and then it asks for my password, I type that in and then I am brought to a command line.  

As or right now I have a 100gb empty partition that I will be using to install Ubuntu.

I will post my results, I have had a couple of successful installs and a couple that have ended as I stated above.

---

### Post by jramshu on 2011-04-22
> **vulcaninvt said:**
> Thanks!

I appreciate the quick feed back and advice! I am really digging Linux and Ubuntu and all this fun new learning. I do not think it will be too long before I am addicted... It all started with my Android phone :)

You and me both. It all started with my EVO. I wanted to learn to write apps and realized Android used Linux. Then I started looking at all the distros available and came across Ubuntu. Now I'm hooked.

Made it to this post and had to comment, so similar to how I got involved. Now I will read on.

---

### Post by K_45 on 2011-04-22
If you want to install application the easiest way it to open up a terminal and

```
sudo apt-get install *app*
``` where app is the name of the application you want to install, such as VLC.

---

### Post by JKyleOKC on 2011-04-22
> **vulcaninvt said:**
> This issue that I have ran up against twice is after I try to boot into Ubuntu.  I get all sorts of text, is this a script? At the end of the text it asks for my username, I type that it and then it asks for my password, I type that in and then I am brought to a command line.That sounds as if your boot options, which are normally set automatically to "quiet splash" at install time, are set to nothing at all or to "text" (the latter would explain why you do not get a desktop, but there can be other reasons too, which I explain below).

What you are seeing is the running report of what is going on behind the scenes during the boot process, which as you can see is much more complicated than most of us realize. The "quiet" boot option simply prevents it from being shown. I personally remove that option on my systems because I want to see what is going on. It's especially useful if the boot fails, because knowing just where the listing stops gives important clues as to what might be wrong. However it **IS** quite confusing when you don't know why it's being shown, so the "quiet" option was introduced to hide it by default.

Seeing this list doesn't really have anything to do, directly, with the absence of a desktop -- unless it's due to a scrambling of the boot options. Normally, a process known as "GDM" (for **G**nome **D**isplay **M**anager) starts automatically just before that login prompt is displayed. The GDM process sets up a login desktop and lets you log in, then turns control over to your window manager to display your personal desktop.

The "text" boot option prevents GDM from launching, so you see the command-line login. However, if for any reason GDM is unable to set up the graphic display, it will quietly get out of the way and the result is the same: a text-mode login prompt and command line.

To find out what is happening with GDM, type the command "startx" at the command prompt after logging in. If it gives you a desktop, then you will know that GDM is not being launched at all and we can troubleshoot that problem. However it's more likely that the command will fail, producing one or more error messages to tell you why. Copy those and paste into a message here and we'll troubleshoot that problem (which is a different kettle of worms than the failure to launch GDM).

---

### Post by vulcaninvt on 2011-04-23
Thank you for the information!

I have successfully installed Ubuntu and it appears to be nice and stable.  I now have two boot managers first is Grub and then Windows boot manager. If I boot into Win 7 I then get the Win 7 boot manager.  Any idea of how I can get only one boot manager?

---

