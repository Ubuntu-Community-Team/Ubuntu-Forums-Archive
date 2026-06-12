---
title: "minimum requirements"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by gmknobl on 2010-10-28
I'm not entirely new to ubuntu but the last time I ran it was version 5.

I have an old dell computer, old even then, that came with Windows 98 but ran XP without a hitch though it was slow (30 Gig HD, who knows what graphics, I assume agp).  I inherited it from my dad.  It had it's issues recently with a dying hard drive.  I intend to get a cheap 7200 rpm IDE drive and maybe an older agp card but that's it.  I assume it either has 256 MB of memory or more.  I also assume I can get more memory for it which may be a faulty assumption.

My question is will this run 10.10 well or should I get an older version of Ubuntu?  I intend for my kids to run this when they get old enough (they are 8 and 5).  It is a very quiet system.  I'm also hoping for a performance boost over XP (it was running SP3 fully patched).  Is that also realistic?

Summary: 
  1) Will my old Dell system run 10.10 or should I get an older system?
  2) Will my system run faster than it did under XP SP3?

---

### Post by ubunterooster on 2010-10-28
Recommendations say 512MB RAM :(


Mint LXDE runs on 193MB RAM though: [http://blog.linuxmint.com/?p=1473](http://blog.linuxmint.com/?p=1473)

Edit: Even with MInt LXDE, I recommend a SWAP partition: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by JKyleOKC on 2010-10-28
For several years I ran an older version of Linux on a 1995-model custom machine that had just 80 MB of RAM, and it worked nicely. That box finally succumbed to a short in its power switch. I now run Xubuntu 10.04.1 LTS on all my machines, one of which has only 256 MB of RAM and some 15 GB of hard disk available (it's dual-booted with Win98SE although I seldom fire up the Win98 side any more; however it has lots of data that I want to keep and have been too lazy to transfer over).

That machine runs much slower than the others, mostly due to the limited RAM forcing heavy swapping. However it's still much snappier than when it's running Win98SE, and I never considered putting XP on it because of its limited resources. I'd think your Dell should be at least as fast with Xubuntu as with XP (I chose Xubuntu originally because it was lighter, and have stayed with it because I prefer its features to those of main-line Ubuntu).

I don't know how 10.10 would run on older hardware; I stick with the LTS releases because I don't want to update every six months. It usually takes me at least half that long to find all the quirks of a totally new release!

---

### Post by gmknobl on 2010-10-28
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#System%20Requirements](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#System%20Requirements)

256 according to this page

---

### Post by NightwishFan on 2010-10-28
At 256mb it might not be fun. I would say 386mb for 32-bit, 512mb 64-bit. At 386mb, enable compcache and vm.swappiness=100, and disable anything you arent running at startup. Or use a lighter WM. A lighter WM would probably run most things fine.

I hear Xubuntu 10.10 is much trimmer than the last few versions, so perhaps give that a try if you are under 512. (Or Lubuntu, but I have never tried it myself).

---

### Post by RJARRRPCGP on 2010-10-28
> **NightwishFan said:**
>  enable compcache and vm.swappiness=100

What is "compcache"? I never heard of that config option.

---

### Post by gmknobl on 2010-10-28
> **JKyleOKC said:**
> I stick with the LTS releases because I don't want to update every six months. It usually takes me at least half that long to find all the quirks of a totally new release!

That sounds good.  I'll see about dl-ing that iso.

My secret hope is that my sons will start to use the darn thing out of curiosity and turn into Linux gurus so I don't have to.  This will also guarantee them a job in a few 8 to 10 years.  Well, that's my hope at least.

Hope springs eternal.

---

### Post by gmknobl on 2010-10-28
> **NightwishFan said:**
> At 256mb it might not be fun. I would say 386mb for 32-bit, 512mb 64-bit. At 386mb, enable compcache and vm.swappiness=100, and disable anything you arent running at startup. Or use a lighter WM. A lighter WM would probably run most things fine.

I hear Xubuntu 10.10 is much trimmer than the last few versions, so perhaps give that a try if you are under 512. (Or Lubuntu, but I have never tried it myself).

I'm assuming all these would be found in system preferences somewhere but other than that, you've lost me.  Of course, disk caching is what slowed the system down when it was running XP.  But heck, I don't even know what type of memory a year 2000 era machine would have.  A previous poster had a good point about using the long term service version.  Do you think Xubuntu 10.10 is better for older systems?

---

### Post by NightwishFan on 2010-10-28
Compcache adds a layer of compressed ram swap, should help under memory pressure, it certainly SEEMS to help my laptop run ok using 386mb of ram.
[http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

It is a bit of a dilemma to me because someone told me (and a few sources confirm this) that to enable it in Ubuntu you just have to enable it in initramfs.conf and the update the initramfs, and it seems to work, but I also have read it should show up in the list of swap files, and it does not. The normal method to swapon the /dev/ramzswap does not work either. So essentially I can not confirm if it is enabled or not. :/ Off topic, if anyone has the answer to this, please PM me so I can get this right.

[http://askubuntu.com/questions/5374/how-to-enable-compcache](http://askubuntu.com/questions/5374/how-to-enable-compcache)

However, it is designed in Ubuntu to enable live cd installs on older hardware, however I have no idea if it is even in use or not.

---

### Post by bioterror on 2010-10-28
> **ubunterooster said:**
> Recommendations say 512MB RAM :(


Mint LXDE runs on 193MB RAM though: [http://blog.linuxmint.com/?p=1473](http://blog.linuxmint.com/?p=1473)

Edit: Even with MInt LXDE, I recommend a SWAP partition: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://wiki.ubuntu.com/Lubuntu#Intended%20Audience]("https://wiki.ubuntu.com/Lubuntu#Intended Audience")
says: > A Pentium II or Celeron system with 128 MiB of RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. It should be possible to install and run Lubuntu with less memory, but the result will likely not be suitable for practical use. If you have less than 160 MiB of RAM, you will need to use the Minimal installation instructions. Please note that especially on lower powered machines (older CPU's) or low RAM systems, that the installation may seem to 'hang' at about 95%, don't worry, it has not; it can just take some time (possibly over an hour). As support for i586 chipsets has been dropped from the kernel for the 10.10 series (These include VIA C3, AMD K6, National Semiconductor and AMD Geode) you will need to use the 10.04 Release.

Go with the [COLOR="RoyalBlue"]Lubuntu[/COLOR], it's not [COLOR="SeaGreen"]Green[/COLOR] ;)

Edit: There's also an alternate installation CD for lubuntu. You dont have to use mini.iso to build your Lubuntu Desktop.

---

### Post by NightwishFan on 2010-10-28
Enabling vm.swappiness=100 will make sure you have more ram for the applications you are currently running, and it will swap the idle stuff out more often. I have found this improves performance a lot on old machines. Here is how to enable, just make sure you replace "100" with "10" as the tutorial recommends 10, but that is not what you want.

[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

---

### Post by georgetom on 2010-10-28
+1 with NightwishFan. 384 MB RAM should be ideal for Ubuntu 10.10. I just installed 10.10 on my friend's HP laptop with 512 MB RAM. He was using XP SP3 and testifies ubuntu is at least 300% faster!

Also, if you are on a low RAM machine, don't forget to go to System>Preferences>Appearance>Visual Effects and chose none. 

In Short
1. Find out how much RAM you have and go for 10.10 if its 384 MB or more
2. Absolutely!

---

### Post by ubunterooster on 2010-10-28
Xubbuntu is actually not that much better and Lubuntu is still buggy, hence I mentioned Mint Lxde. The one I linked to is a LTS and 193 is recommended not absolute minimum.

---

### Post by ubunterooster on 2010-10-28
> **bioterror said:**
> [https://wiki.ubuntu.com/Lubuntu#Intended%20Audience](https://wiki.ubuntu.com/Lubuntu#Intended%20Audience)
says: 

Go with the [COLOR=RoyalBlue]Lubuntu[/COLOR], it's not [COLOR=SeaGreen]Green[/COLOR] ;)

Edit: There's also an alternate installation CD for lubuntu. You dont have to use mini.iso to build your Lubuntu Desktop.
I have used both and Mint's Lxde is lighter and more consistent. And the color can be changed easily.

---

### Post by NightwishFan on 2010-10-28
Nothing wrong with recommending Mint either though I have a suspicious Xubuntu is moving forward, so do not entirely rule it out.

I will reboot my laptop with 386mb of ram and see how it works (yes you can do this), I shall return.

---

### Post by beew on 2010-10-28
> **NightwishFan said:**
> Enabling vm.swappiness=100 will make sure you have more ram for the applications you are currently running, and it will swap the idle stuff out more often. I have found this improves performance a lot on old machines. Here is how to enable, just make sure you replace "100" with "10" as the tutorial recommends 10, but that is not what you want.

[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")

I have an old machine (512MB ram) I found it to be rather sluggish, but setting swappiness to 10 greatly improves it performance. Before that I tried setting swappiness to 100 for exactly the reason you gave but performance ended up even worse with everything basically grinding to a halt.

I think perhaps if swappiness is set too high, the threshold to switch to swap from ram may be too low so any process which requires a bit more ram would be using swap and thus performance takes a great hit. It is just a speculation, I could be wrong of course.

---

### Post by gmknobl on 2010-10-28
Thanks for all the replies but I'm starting to get confused.

It sounds like I should try Xubuntu and cross my fingers, then go with Mint Lxde (whatever that is) if it doesn't install well.  I'll look for the swapiness setting after/during? install and see what that does, assuming it installs and boots at all with a new HD in it.  This will be a few weeks.

It seems Mint lxde is not out for version 10 yet.  It definitely looks to be aimed at older system as many people with older systems were commenting on at least one forum as to the speed running things.

---

### Post by ubunterooster on 2010-10-28
Linux Mint 9 LXDE is a Ubuntu based OS focused on ease of use and usability and features a complete desktop  computing experience while being easy on system resource usage thus  making it suitable for older hardware and situations where speed is a  crucial factor. Featured improvements in this release: LXDM, improved  PCManFM2 file manager, VLC installed by default, 30,000 applications  catalogued and reviewable both online and in the new software manager,  brand new incremental backup tool for both data and software selection,  three years support. See the [release announcement]("http://www.linuxmint.com/blog/?p=1473") and [release notes]("http://linuxmint.com/rel_isadora_lxde_whatsnew.php") for further information.

---

### Post by gmknobl on 2010-10-28
> **ubunterooster said:**
> Linux Mint 9 LXDE is a Ubuntu based OS focused on ease of use and usability and features a complete desktop  computing experience while being easy on system resource usage thus  making it suitable for older hardware and situations where speed is a  crucial factor. Featured improvements in this release: LXDM, improved  PCManFM2 file manager, VLC installed by default, 30,000 applications  catalogued and reviewable both online and in the new software manager,  brand new incremental backup tool for both data and software selection,  three years support. See the [release announcement]("http://www.linuxmint.com/blog/?p=1473") and [release notes]("http://linuxmint.com/rel_isadora_lxde_whatsnew.php") for further information.

Thanks.  It's downloading (slowly) now.  So I have Live/Install CDs for Ubuntu 10.04, Xubuntu 10.04, Xubuntu 10.10 and Mint 9 lxde.  Geesh!  That ought to be enough.

---

### Post by NightwishFan on 2010-10-28
After install, Linux needs a swap file or partition to swap data anyway, anything under 1gb I would most certainly say to use a swap file.

Also, with swappiness=10 being faster seems very wrong to me (at least on old hardware) At that point, it would fill your ram and struggle against swapping as early as it should.

For example, set it to 100 then you opened firefox and shotwell. Use shotwell for a while it would swap out firefox, and shotwell would run quickly. Switch back to firefox and it would take time to swap firefox back out to ram, once done it would run quickly as well.

Set to 10 and reboot, and do the same, you will find it tries to keep too much in ram, and buffer everything, and constantly swap. For me, at 386mb firefox does not even start at all using vm.swappiness of 10.

My experience at 386mb is do not use the server kernel, it was slow. I had to switch back to the generic one. (At the moment I have no idea why it was so slow). I am using a 64-bit system, so I assume anyone using 32-bit would have better results than me here. Getting to the login screen and desktop was very very fast, opening the three programs took around a minute though.

Fresh boot:
[[IMG]http://img513.imageshack.us/img513/8726/freshboot.th.jpg[/IMG]](http://img513.imageshack.us/i/freshboot.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)


With Rhythmbox, Firefox, and Shotwell open:
[[IMG]http://img188.imageshack.us/img188/7305/progamsopen.th.jpg[/IMG]](http://img188.imageshack.us/i/progamsopen.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

The specs:
[[IMG]http://img714.imageshack.us/img714/3784/specsz.th.jpg[/IMG]](http://img714.imageshack.us/i/specsz.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Sir Jasper on 2010-10-28
Hi,

As you are posting here it us likely you have a CD drive and you can also download data.

Lucid Puppy 5.1.1 (google: download lucid puppy 5.1.1) can be run from a CD (made from the ISO download of about 130 MB). The CD loads into RAM (and can then be removed - or not). It should configure your hardware automatically and it doesn't need a Hard Drive to try it and because it runs in RAM it will operate in its fastest mode immediately after first loading which may take a minute.

It is unlikely that you will find a better or faster OS for your machine and it has the many optional installation methods - though when you get your new drive (to maximise speed on other distros) you can try Xubuntu, Lubuntu or whatever to see which you prefer. 

My regards

---

### Post by ubunterooster on 2010-10-28
> **NightwishFan said:**
> After install, Linux needs a swap file or partition to swap data anyway, anything under 1gb I would most certainly say to use a swap file.

Also, with swappiness=10 being faster seems very wrong to me (at least on old hardware) At that point, it would fill your ram and struggle against swapping as early as it should.

For example, set it to 100 then you opened firefox and shotwell. Use shotwell for a while it would swap out firefox, and shotwell would run quickly. Switch back to firefox and it would take time to swap firefox back out to ram, once done it would run quickly as well.

Set to 10 and reboot, and do the same, you will find it tries to keep too much in ram, and buffer everything, and constantly swap. For me, at 386mb firefox does not even start at all using vm.swappiness of 10.
gmknobl, for more information see: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

> **gmknobl said:**
> Thanks.  It's downloading (slowly) now.  So I have Live/Install CDs for Ubuntu 10.04, Xubuntu 10.04, Xubuntu 10.10 and Mint 9 lxde.  Geesh!  That ought to be enough.LOL, I have over 70 distros

---

### Post by bioterror on 2010-10-28
> **ubunterooster said:**
> Xubbuntu is actually not that much better and Lubuntu is still buggy, hence I mentioned Mint Lxde. The one I linked to is a LTS and 193 is recommended not absolute minimum.

Okay, I would like to know what's your #define for the word buggy.
As I have a Mint 9 desktop machine running downstairs I checked package PCManFM version from it and it says Version: 0.5.2+svn20091029-1ubuntu3.1

Then I made a check from my Lubuntu 10.10 and it says Version: 0.9.7-1ubuntu1

As PCmanFM is the first module on LXDE, I think that means alot for the whole Envinroment. And you're suggesting others to use outdated packages with bugs and bashing around saying that Lubuntu is "still buggy".

And what I know about Lubuntu, Lubuntu works closely with LXDE.

But as we all know, opinnions are like... and we all have one. We can only argue about taste things.

But still, I would rather suggest someone to use 10.10 version of Ubuntu if he's going to install a Desktop Envinroment which is young.

This is my 2 cents for this thread.

---

### Post by ubunterooster on 2010-10-28
Mint is built to have the benefits of Ubuntu without as many papercuts or "unwanted features" ( I call them "Bugs") 

Yes, Lubuntu works closely with LXDE but remember how much Ubuntu emphasizes being a development OS; it is not as stable

---

### Post by gmknobl on 2010-10-28
Didn't mean to sir up controversy 

;)

(but I can with a nasty crack at neocons if you want)...

or maybe 

8^>

---

### Post by WeAreLinux on 2010-10-28
I ran Ubuntu 10.04 on a 800mhz Celeron, 256MB RAM, Integrated Intel graphics machine. Excluding minor lag, it wasn't that bad. I only used the computer for basic computing though.

>  1) Will my old Dell system run 10.10 or should I get an older system? 

It should. A lot of people would suggest using Xubuntu though.

>  2) Will my system run faster than it did under XP SP3? 

From my experience, XP Sp3 was noticeably faster compared to Ubuntu on the machine I listed above.

---

### Post by NightwishFan on 2010-10-28
Xp will probably certainly be more interactive than a gnome desktop on 256mb. May or may not process as well though.

---

### Post by ubunterooster on 2010-10-28
> **gmknobl said:**
> Didn't mean to sir up controversy 

;)

(but I can with a nasty crack at neocons if you want)...

or maybe 

8^>
LOL, it's okay. Linux users are known for minor squabbles but we don't hold grudges.

---

### Post by DirtyPC on 2010-10-28
> **gmknobl said:**
> I'm not entirely new to ubuntu but the last time I ran it was version 5.

I have an old dell computer, old even then, that came with Windows 98 but ran XP without a hitch though it was slow (30 Gig HD, who knows what graphics, I assume agp).  I inherited it from my dad.  It had it's issues recently with a dying hard drive.  I intend to get a cheap 7200 rpm IDE drive and maybe an older agp card but that's it.  I assume it either has 256 MB of memory or more.  I also assume I can get more memory for it which may be a faulty assumption.

My question is will this run 10.10 well or should I get an older version of Ubuntu?  I intend for my kids to run this when they get old enough (they are 8 and 5).  It is a very quiet system.  I'm also hoping for a performance boost over XP (it was running SP3 fully patched).  Is that also realistic?

Summary: 
  1) Will my old Dell system run 10.10 or should I get an older system?
  2) Will my system run faster than it did under XP SP3?
Xubuntu is more compatible for you, or you could always try the netbook version I suppose?

---

### Post by beew on 2010-10-28
> **NightwishFan said:**
> 
Also, with swappiness=10 being faster seems very wrong to me (at least on old hardware) At that point, it would fill your ram and struggle against swapping as early as it should.

For example, set it to 100 then you opened firefox and shotwell. Use shotwell for a while it would swap out firefox, and shotwell would run quickly. Switch back to firefox and it would take time to swap firefox back out to ram, once done it would run quickly as well.

Set to 10 and reboot, and do the same, you will find it tries to keep too much in ram, and buffer everything, and constantly swap. For me, at 386mb firefox does not even start at all using vm.swappiness of 10.

My experience at 386mb is do not use the server kernel, it was slow. I had to switch back to the generic one. (At the moment I have no idea why it was so slow). I am using a 64-bit system, so I assume anyone using 32-bit would have better results than me here. Getting to the login screen and desktop was very very fast, opening the three programs took around a minute though.



I am sure I am breaking some rules, but at least for me the improvement in changing to vm.swappiness =10 is almost miraculous. Before I couldn't watch videos in full screen without some freezing(or at least very choppy) but now (except for hd mp4 files) I can watch very good quality avi video in full screen even with firefox and Compiz running. Other than videos opening and closing windows are also a lot faster, programs seem a lot more responsive. Tried setting vm.swappiness=100 and videos keep freezing up like a slide show and it took a few minutes for openoffice to open a doc file with pictures in openbox (I use it as a kind of benchmark thing) and with vm.swappiness =10, it takes < one minute (with full compiz, firefox opened and vlc playing music). 

I get further performance boost by removing pluseaudio,

Now everything is actually quite smooth even with Compiz, a lot smoother than when WindowsXP sp3 was installed. If I want additional speed and performance I can disable Compiz and drop down to openbox.

I am not sure why that is because what you say seems to make a lot of  sense. It must have something to do with the hardware configuration I am running 32bit, 2.2 Ghz cpu 512Mb or ram and the laptop comes with a Nvidia Geforce4 ti 4200 graphic card, it took me a while to get it to work in Maverick (basically downgrading xorg to the Lucid version)

---

### Post by JKyleOKC on 2010-10-28
To respond to your comment that you don't have any idea what type of RAM your old Dell box has, it's probably either PC133 or DDR (not DDR2 or DDR3). Both kinds are obsolescent now and consequently may be fairly high priced; but if you have local non-chain computer stores they just might provide a market for used RAM sticks at really reasonable costs. My favorite here in OKC sells both kinds, when they have them, for less than half the cost of new -- and guarantees them, to boot.

To find out what your box has inside without having to open it up and look, boot from any of those Live CDs and open a terminal window. Then issue the command "sudo lshw | less" which will give you a detailed list of your hardware. It should contain information about the RAM sticks in each bank, including manufacturer. It will tell you the type for each bank. 

The box I mentioned before that has only 256 MB of RAM dates from around the same time as yours, and it can use either PC133 or DDR but only two sticks maximum and does not permit me to mix the types. I have a pair of 128 MB PC133s in it but have considered replacing them with used 512 MB sticks to give it a full gigabyte, which should bring its performance into line with my more recent machines (which have 2 and 3 GB respectively, and also hundreds of GB of drive space).

I've not found Xubuntu to be significantly lighter in resource usage than the main line Ubuntu, but use it because I prefer its interface (much simpler; not as much eye candy or frills). I've tried some of the others mentioned in this thread but keep coming back to the XFCE interface...

---

### Post by gmknobl on 2010-11-08
Perhaps it's time I moved this to another forum but I'll start here at least.  Thanks to everyone who responded.

I installed XUbuntu finally.  I upgraded the box to 512 MB RAM and replaced the HD with an 80 Gig model with 2MB buffer.  I think the greatest slow down for this computer, aside from the buses the motherboard uses is likely the video which is an ATI 128 Rage Pro.  I'd like to find a suitable upgrade that won't tax the 180 watt power supply.  It's AGP of course.

But my main question now is about accessing stuff on the network.  It connects to the web just fine, video is SLOW and buffers frequently (see above - a similar problem occurred in XP on this computer too).  However, at my home I'm running a Thecus N2100 NAS.  Under its native firmware I have a few shares such as a regular file share for file so I can back up from my windows or OS/X computers and an iTunes share for music.  It's not a fast unit but it gets the job done.  

I've found that I don't see a darned thing, not even a listing the for the n2100.  I did some reading and found I should run the gigolo program to look at the network.  It couldn't find anything either.  It listed I have no shares on my windows network.

What gives?  What should I use to get the NAS listed?  I'd rather not turn samba on if I don't have to.  Would that be the necessary step?  Is there some other way of seeing the shares the thecus already has?  Any ideas are appreciated.

---

