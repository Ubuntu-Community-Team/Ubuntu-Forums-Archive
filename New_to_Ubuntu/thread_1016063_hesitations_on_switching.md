---
title: "hesitations on switching"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by libihero on 2008-12-19
I am new to linux/ubuntu, and i am thinking bout switching my vista to ubuntu.  i am willing to learn everything about ubuntu and how to run it, but i have a few issues that are causing me to hesitate (i'm sorry these questions may seem extremely stupid.):
1.  Will i lose my files if i switch my operating systems
2.  I don't know if my built in web cam will work, I tried using live CD but i couldn't figure out how to open the webcam
2.  Will i lose all the software i had downloaded (ms office especially)
3.  if i wanna switch back, how would i do that?
thanks :)

---

### Post by HotShotDJ on 2008-12-19
> **libihero said:**
> 1.  Will i lose my files if i switch my operating systems
2.  Will i lose all the software i had downloaded (ms office especially)
3.  if i wanna switch back, how would i do that?
thanks :)[LIST=1]
[*]No.  Besides, you would never consider making major changes to your computer without making an external backup of your files anyway.... right? :)
[*]There are many ways to run Windows software (such as MS Office) after you upgrade your system to Ubuntu.  There is virtualization (such as VirtualBox), emulation (such as WINE), or Dual-Booting
[*]Just reinstall Windows.  Or if you decide on Dual-Boot, just delete the Ubuntu partition(s) and then use SuperGrub to fix the MBR.... but you can cross that bridge if you come to it
[/LIST]

---

### Post by halitech on 2008-12-19
> **libihero said:**
> I am new to linux/ubuntu, and i am thinking bout switching my vista to ubuntu.  i am willing to learn everything about ubuntu and how to run it, but i have a few issues that are causing me to hesitate (i'm sorry these questions may seem extremely stupid.):
1.  Will i lose my files if i switch my operating systems
2.  I don't know if my built in web cam will work, I tried using live CD but i couldn't figure out how to open the webcam
2.  Will i lose all the software i had downloaded (ms office especially)
3.  if i wanna switch back, how would i do that?
thanks :)

1. depends. if you don't backup first and you don't opt for a dual boot then yes you will. If you backup and dual boot then no.

2. webcams are touchy so it might, do a google search on your model and go from there

3. not if you backup your files

4. depends on if you dual boot or single boot.

---

### Post by som1special2 on 2008-12-19
definitely try using the live for more than a couple of days. You can save ALL of your office programs to a disk and the inherent office program in Ubuntu, (open office 2.4) reads ALL MS office formats. All of you files in what type? When I switched I brought the basics along and have not had a problem, (MP3's, avi videos, office saves, pictures and favorites from internet). Just about all the software you have downloaded and more than likely paid for can be re-downloaded should you decide Ubuntu isn't for you. Linux offers just about any type of program you can think of FREE right from your desktop. Switching back to windows is pretty easy too, look at this link:

[http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_install_Ubuntu](http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_install_Ubuntu)

As far as the webcam goes, it depends on what CPU you are using. use this link to search for your cpu and webcam info with Ubuntu:    [http://www.google.com/linux](http://www.google.com/linux)

Check this link for more on switching from windows:

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

I used windows for over 15 years and was NEVER happy. I am ecstatic with Ubuntu for over 6 months! I learn something new every day and there are a lot of nice users out there to help. Welcome!

---

### Post by donkyhotay on 2008-12-19
Install ubuntu with wubi if your uncertain. This will give you the chance to use ubuntu without having to worry about repartitioning or otherwise affecting your windows installation. It will then give you a chance to mess around with linux and if you break something your windows install is still there for you. Once you've gotten to the point where your pretty comfortable with linux and are able to do everything you need then you might start thinking about dumping your windows.

---

### Post by Michael.Godawski on 2008-12-19
Switching from old habits to new horizons is not easy but worth the hassle.

You will find a great, may I say unique, community on this forums, which never leave you alone on your way to Ubuntu.

I would start with dual-booting. So you have your safe haven. 

Have a look at this basic guides dealing with ubuntu:

[http://godawski.oxyhost.com/](http://godawski.oxyhost.com/) <--- still working on it but it will be great :p
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

For dual-booting see:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Cl0ud9 on 2008-12-19
You could try installing [Wubi]("http://wubi-installer.org/") inside Windows just to try Ubuntu out and decide if it will work for you. If you don't like it, you could just uninstall the program leaving Windows exactly the way it is now.

---

### Post by waspbr on 2008-12-19
don't feel intimidated, this is a beginners forum, there's no such thing as a stupid question[LIST=1]
[*]As hotshot said. It is unlikely that you will lose your files, very unlikely, but whenever dealing with your (any) OS, make a back up of your essential files, the fact that a livecd works already is a good point but it is best to be on the safe side
[*] since you have a built in camera, I am assuming you are using a laptop, before installing ubuntu in mine, I googled around  for "<mylaptopsModel> ubuntu intrepid " (or hardy) whatever version your are planning to install.

but a quick check on the live cd would be to press ALT + F2 and paste (or type) this

```
gstreamer-properties
```

a window should pop up, there go to the video tab, and go to output section, there test different plugins,i.e. select one and press test, though the autodetect option should work. 

on the unlikely event that it doesn't work, googling or asking in the forums should help.


[*] yes you can, provided you don't erase your windows partition. If you are starting out (and u are) I would recommend a dual boot, so you can take your time to figure things out at your own pace. If you can't figure out how to do something you will always have windows to fall back on.

[/LIST]

you can dual boot in two ways,

[LIST]
[*]wubi, windows installer
[*]Make a partition for ubuntu with the live CD
[/LIST]

you can find information about wubi at [http://wubi-installer.org/]("http://wubi-installer.org/"), it is a good start up if you don't feel confident enough to play around with partitions, though the performance is slightly reduced.

There's a great wealth of information on the partition dual boot install, documentation and youtube videos. Feel free to ask anything if you have any questions

---

### Post by HotShotDJ on 2008-12-19
> **libihero said:**
> 2.  I don't know if my built in web cam will work, I tried using live CD but i couldn't figure out how to open the webcamHEY!  :mad:  That wasn't there when I posted my answer!  No fair changing the question.

:lolflag:

---

### Post by SunnyRabbiera on 2008-12-19
> **libihero said:**
> I am new to linux/ubuntu, and i am thinking bout switching my vista to ubuntu.  i am willing to learn everything about ubuntu and how to run it, but i have a few issues that are causing me to hesitate (i'm sorry these questions may seem extremely stupid.):
1.  Will i lose my files if i switch my operating systems
2.  I don't know if my built in web cam will work, I tried using live CD but i couldn't figure out how to open the webcam
2.  Will i lose all the software i had downloaded (ms office especially)
3.  if i wanna switch back, how would i do that?
thanks :)

1: Not if you back them up and when setting up you set up a dual boot.
2: Webcams are tricky, this is no fault of linux but I know some webcams wont work.
3: Ms Office will be fine if you dual boot, or you can install wine to help you out.
Plus we do have alternatives to MS office like open office to offer.
4: you can just repartition, no one is really forcing you to use linux

---

### Post by donkyhotay on 2008-12-19
> **SunnyRabbiera said:**
> 1: 4: you can just repartition, no one is really forcing you to use linux

Yep, remember linux is about choice, even if that choice is for a poorly-designed buggy piece of software like windows...

---

### Post by libihero on 2008-12-19
wow that was unexpectedly fast haha thanks for all the help
would information on how to partition my hard drive be on this forum?
and does running two os on my computer slow it down at all?

---

### Post by SunnyRabbiera on 2008-12-19
> **libihero said:**
> wow that was unexpectedly fast haha thanks for all the help
would information on how to partition my hard drive be on this forum?
and does running two os on my computer slow it down at all?

Partition guides can be found all over the web, as well on the forum, there is a guided mode on the live CD too to help you dual boot.
One piece of advice I can give is to please defrag your hard drive and compress your filesystem on windows.
Slowdown should not happen that much, unless you have a small hard drive you should be fine.
If you have a 70GB hard drive you are good, any hard drive above 20GB should be good enough for a dual boot.
Under that dont waste your time :D

---

### Post by chris200x9 on 2008-12-19
> **HotShotDJ said:**
> [LIST=1]
[*]There are many ways to run Windows software (such as MS Office) after you upgrade your system to Ubuntu.  There is virtualization (such as VirtualBox), emulation (such as WINE)
[/LIST]


I am shocked SHOCKED! :confused: Wine Is Not an Emulator :lolflag:

---

### Post by SunnyRabbiera on 2008-12-19
> **chris200x9 said:**
> I am shocked SHOCKED! :confused: Wine Is Not an Emulator :lolflag:

Yeh but despite that wine acts like a windows emulator :D

---

### Post by HotShotDJ on 2008-12-19
> **chris200x9 said:**
> I am shocked SHOCKED! :confused: Wine Is Not an Emulator :lolflag:Thats only because WITAE (Wine Is To An Emulator) was an even stupider name. ):P

---

### Post by libihero on 2008-12-19
haha sorry for being such a bother :P
but ya i have 250 gig harddrive, and i partitioned and it allowed 40 gig.  i forgot to format so i'll do that and then add more to the other volume.
now do i download ubuntu on this other hard drive, and thats all i have to do to run both?  how do i switch between the two?

---

### Post by jerome1232 on 2008-12-19
> **libihero said:**
> I am new to linux/ubuntu, and i am thinking bout switching my vista to ubuntu.  i am willing to learn everything about ubuntu and how to run it, but i have a few issues that are causing me to hesitate (i'm sorry these questions may seem extremely stupid.):
1.  Will i lose my files if i switch my operating systems
2.  I don't know if my built in web cam will work, I tried using live CD but i couldn't figure out how to open the webcam
2.  Will i lose all the software i had downloaded (ms office especially)
3.  if i wanna switch back, how would i do that?
thanks :)

1: Assuming you mean doing a complete format and install of Ubuntu, yes

2: With the same assumption, yes

3: Well I actually would recomend Dual booting the two operating systems, this way you a) don't lose any files and b) don't lose your installed software. 

You are just given the option of booting into Ubuntu or Windows during the boot process.

There are two methods of doing this:

A) Wubi, basically while in Windows insert the Ubuntu cd into your computer, an installation Window will pop up and will install Ubuntu onto your system without re-partitioning your drive or formating anything. I think it's great for those who are wanting to get their feet wet and are wary of re-partitioning their drives.

B) First of all ALWAYS backup your data before messing with partitioning scheme's, there's always the chance all hell breaks loose and you accidently format the whole drive or something similiar.

Boot your system with the Ubuntu cd in the drive and proceed through the normal installation process and make sure you tell ubuntu to resize your drive and install Ubuntu to the free space.

edit: Wow I must of had a cached version of this thread up becuase I swear there were no replies when I started this now I'm seeing one's that were posted an hour ago

---

### Post by bodhi.zazen on 2008-12-19
Best to dual boot for a while while you are learning a new OS.

After you install Ubuntu, when you boot, you will get a text menu that will allow you to select which OS to boot.

---

### Post by Georgia boy on 2008-12-19
Dual boot is a good way to go. I went that way. I go to Windows once in a while mainly to check on the updates. Which reminds me that the Internet Explorier patch came out. Guess I should go and do that one. 
Believe me, there aren't any stupid questions here. I would have been slammed quite a few times if there was.:lolflag:
These people here are great!!! Trust me when I say that. I've been helped quite a bit here in this forum. There's still things I have to question on at times and I don't feel bad about asking.
Tom

---

### Post by medley on 2008-12-19
> **libihero said:**
> I am new to linux/ubuntu, and i am thinking bout switching my vista to ubuntu.  i am willing to learn everything about ubuntu and how to run it, but i have a few issues that are causing me to hesitate (i'm sorry these questions may seem extremely stupid.):
1.  Will i lose my files if i switch my operating systems
2.  I don't know if my built in web cam will work, I tried using live CD but i couldn't figure out how to open the webcam
2.  Will i lose all the software i had downloaded (ms office especially)
3.  if i wanna switch back, how would i do that?
thanks :)

I switched, for a while, from Vista to Kubuntu on my Dell m1330. My solution was to buy a second hard drive, which I switched out with the one in my laptop. HDs are cheap these days, and I bought a 120GB 2.5 inch for about $65. I did this because I didn't want to blow away my nicely configured Vista machine and have to rebuild from scratch again. In the end I switched back, because there are still too many things that don't work out of the box, even with a great distro like (K)Ubuntu. I am using Kubuntu 8.10 as I type this, but in a VirtualBox VM inside of Vista on a quad core desktop.

If you're a Linux newb, I'd take it slow, and do it in a way that allows you a graceful fall back. There is a very good chance that you'll have some challenges getting some piece of hardware to work, or network sharing with other Windows systems, etc. Linux is great, but you have to enjoy tweaking, investigating and problem solving. On the other hand, with some of the desktops available, you can do things that the Macs can't match for eyecandy.

Good luck.

---

### Post by donkyhotay on 2008-12-19
Occasionally you get some jokers on here but the mods are pretty good about keeping them under control. Most of us went through the difficulties of learning linux for the first time and know what it's like. I didn't have the luxury of dual-booting when I was learning because the only version of windows I had was a beta (legit) that had expired! (This was the reason I started using linux in the first place.) Now I'm a dedicated linux user and refuse to go back.

---

### Post by Michael.Godawski on 2008-12-19
Inspired by this thread I have written this small essay, article call it what you like,

aimed at new linux users, or linux-users-in-spe :p


[LIST]
[*][http://godawski.oxyhost.com/switch.html](http://godawski.oxyhost.com/switch.html)
[/LIST]

---

### Post by Georgia boy on 2008-12-19
Michael, went to your site. Very interesting. Wish I was technical and knowledgeable to help you out. But alas, still a newbie myself and always learning. Just wanted to tell you that it's a damn good site.
Tom

---

### Post by Michael.Godawski on 2008-12-19
> **Georgia boy said:**
> Michael, went to your site. Very interesting. Wish I was technical and knowledgeable to help you out. But alas, still a newbie myself and always learning. Just wanted to tell you that it's a damn good site.
Tom

thank you Tom,
I like to give something back from this community which taught me, and still teaches me everything. If you are interested in participating just go to


[LIST]
[*][http://ubunturesources.wikidot.com/](http://ubunturesources.wikidot.com/)
[/LIST]
and add yourself as a supporter to the list. :p If you wish to write articles as a writer.

---

