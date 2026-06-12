---
title: "play games"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by PhilRogers34 on 2011-02-07
Hi, i've only been using ubuntu for about a week, i know absolutely nothing about developing and programming and computers in general, i have very little knowlegde of how to use windows either. Basicly i want to use my pc for web surfing, music and films and i have decided i want to use ubuntu for this. The only problem i now have is i can't play games like 'The Settlers' with ubuntu, i have tried using wine and after googling thousands of issues i managed to get the game to install in ubuntu but i cannot get it to actually run so i can play the thing!  so here is how i want to set up my pc.    On my pc hard drive (80g) i would like xp so i can play games i intend to only use about 40g on this drive and will be disabling all connections to the outside world.  I have a seagate 500g portable hard drive that i would like to install ubuntu on and keep totally separate from windows. i will set my bios to boot from portable 1st and hard drive 2nd.    i have tried 3 times now to install on this drive but it is refusing to boot.  i have tried disconnecting the pc hd and installing i have tried formatting one big partition and setting it as the root and then a smaller swap partition  I have tried formatting  a ext3 part as the root with ext4 part as home and then a small part for the swap    i have tried selecting individual partitions for the boot    I have googled this and all the answers i have found do not cater for the absolute beginner, they assume i already understand everything and know what i am doing, i do not!!     I have the following set up     Packard bell istart 1360  Asus2 m2ns-nvm/s motherboard Amd Athlon 64  3.2ghz( ithink, it might 2.3)  2.5g ram  80g hard drive 500g seagate portable hd i recently added an nvidia 8400gs 256mb graphics acelerator because the motherboard graphics packed up    I want ubuntu on the 500g so it has more space for storing everything, and i intend to use windows purely for games, nothing else  Can anyone please explain how to get ubuntu to install on the portable hd so i can nuke my hd and install xp?  I do not want a dual boot setup, that is just a chore i want it to just load ubuntu first off and if the potable is disconnected to boot windows  or where am i going wrong?    please note:  I need your answer to be in basic english, i do not understand when someone says 'use this code' or try this code' that means absolutely nothing to me, if you are going to recommend codes please talk me through how to use them, what they do and what i am actually doing to my system,   I have read through loads of how to guides and none of actually helped.    Thanks :-)

---

### Post by PhilRogers34 on 2011-02-07
i should also add i am performing the install with my ethernet cable unplugged, i would rather install the basic system first and then connect and update it all. just to make 100% sure no one can jump in before the os is safe.  i have also tried a virtual box to install xp inside ubuntu, which worked although the xp setup is limited and i can't set enough ram for the vm to run games properly.  cheers!

---

### Post by waynefoutz on 2011-02-07
What you're asking to be done is nearly impossible to put in layman's terms. You're asking to move Ubuntu to an external drive, install Windows on the internal drive, then reinstall grub....hmm 

I'd say the easiest way to do this is, especially for someone with limited computer skills is to let the installation process do the work for you. These are the steps I would take...format the external to fat32, then back up your /home directory on your internal drive to the 500 gig external. Next, disconnect the external and install Windows. Then plug the drive back in, move your data back over to the internal, then install Ubuntu on the external drive. Once that's complete, in Ubuntu, drag your data back over to your Ubuntu install. Ubuntu should install grub so you can choose which OS you want.

---

### Post by PhilRogers34 on 2011-02-07
Thanks mate,  I was hoping to do a totally new install on the portable, not to just move my existing os.  i had it on dual boot on the pc hd for a few days and it used to give me a list to choose ubuntu or xp, i want to avoid this screen and just boot into ubuntu from the portable automaticly, and then if i turn the pc on without the portable connected i want it to boot windows automaticly.  if there is no way i can do this without the screen giving the list then fair enough, i will just have to put up with it.  thanks

---

### Post by PhilRogers34 on 2011-02-07
ok so i've formatted the portable to fat32, how do i back up the home folder? can i just copy it over to the portable? do i need a bit of software to do this? i've googled this and every site is just showing code to put into the terminal, i don't want to do this because it's a chore, is there something that does it for me?

cheers

---

### Post by NightwishFan on 2011-02-07
At the moment I am busy to walk you through it, but I would like to mention that the terminal is not as scary as it seems, and makes some tasks amazingly fast and simple. It is a tool not a hindrance. :)

---

### Post by waynefoutz on 2011-02-07
> **PhilRogers34 said:**
> ok so i've formatted the portable to fat32, how do i back up the home folder? can i just copy it over to the portable? do i need a bit of software to do this? i've googled this and every site is just showing code to put into the terminal, i don't want to do this because it's a chore, is there something that does it for me?

cheers

just plug the drive  in and drag the folder over in a file manager window, just as you would in Windows.  

I have to agree with the last poster. Don't be afraid of the terminal if you find a way to do it better. I've been using Ubuntu since 2005, I might know 2 terminal commands. I just paste in what the article tells me.

---

### Post by PhilRogers34 on 2011-02-07
Thanks guys, i shall try your method wayne though i was hoping to get a fresh install on the ext hd.  I've checked my bios too, it's showing my seagate drive as the portable device in the configuration settings so i can't see why i can't just install to the ext hd and boot.

on the ubuntu set up do i choose ' install alongside other os' or install to other places? will this make a difference to the install on the ext hd?

---

### Post by PhilRogers34 on 2011-02-07
ok well my home folder doesn't want to be copied. if i try and open it from -places- home folder  it trys to open it with wine but nothing happens i get an error message, if i go through -places-computer  it sitting in my file system but when i try and drag it across it throw up an error saying can't copy because blah blah blah

i really don't want both os on the same hard drive with a bloody grub loader screen, i want straight into ubuntu from the usb so for that reason i am going to autonuke all my drives and just go back on windows. ubuntu might be safer with regards to viruses but it a chore getting it all set up and has caused nothing but headaches so far,

---

### Post by Eternal_Light on 2011-02-07
When you say a clean install you mean you dont want to keep any data at all from your old piece of ubuntu. Right?

In that case all you have to do is first install windows xp on your pc and then format the external HDD in fat32 and install ubuntu on it.

All you gotta do is install winxp on the pc, insert the ubuntu disk and do a reboot with the external hdd connected. Move through all steps like you normally would but when its time to pick a location on the disk select the "do things manually" (or something like that) option. Then a list of drives and partitions will appear in front of u. Just find your external, set use as fat32 and put a mounting point "/". Dont forget to pick a small swap area like 2-4 gigas. You are set.

When your external is connected grub will load your ubuntu. If external is not connected your pc will launch windows.
I might be awfully wrong but i don't think its more complicated than that.

---

### Post by PhilRogers34 on 2011-02-07
> **Eternal_Light said:**
> When you say a clean install you mean you dont want to keep any data at all from your old piece of ubuntu. Right?

.

That's exactly  what i want, thank you! i shall have a go at this method. i've already sat through 4 install onto the ext hd with no luck and i tried an install of xp onto the ext hd to see if its the bios that's the problem. so my apologies to everyone if come across as a bit moody  xp wouldn't boot from the ext but my hd is showing in the portable configuration for the bios.   i want to set the pc up before i get too heavy into ubuntu and have to much data on my drives. at the moment it's only a few gig of music that's easy to replace if i lose it.   Its just i want to keep ubuntu as far away from xp as possible, i know its pretty much virus proof but i worry that if someone hacks into windows they can find a way through into ubuntu without me knowing  i am actually getting used to it and i can just feel that it's not draining resources like windoze and runs a lot better, which is why i want to keep it for web surfing and music etc.


Thanks again :-)

---

### Post by Eternal_Light on 2011-02-07
Well it is actually the other way round. The newest ubuntu releases can read and write into NTFS (which is the filesystem that windows support) but windows isnt even close to comprehending an ext4 file format. If the reason you want ubuntu far away from windows is because u r afraid someone might gain access to your linux thru xp i think there is no reason to worry ^^
This is the reason you cannot install windows on an ext3-ext4 formatted disk.

And a final note: Linux is far from virusproof. It's just the fact that linux computers dont own a big enough share of the os-market to attract people to design virii for it.



EDIT: Also, i am running kubuntu and when i installed it i got the choice to encrypt my whole /home folder. This means that even if someone came with another linux distro on a thumbdrive or a livecd, and thus were able to search thru ext3 and ext4 filesystems they wouldnt be able to see what you got in your home folder. I don't know tho if this feature is existent on ubuntu and if it is it would obviously lengthen by a bit the boot time of the os while trying to decrypt the home folder. 
I am a linux rookie just like you are so please excuse me if you find any inaccuracies in the stuff that im writing. Google is, and will always be, our friend.

---

### Post by PhilRogers34 on 2011-02-07
thanks for the suggestion, it's worked and i now have ubuntu on the ext hd with windows on the pc hd. i had trouble removing ubuntu first though, i nuked the hd but the windows disc wouldn't boot and ubuntu was still there. i loaded ubuntu and used gpartition manager clicked make new partition table for the pc hd. shut down and then the cd booted and installed no probs. i used the cd to install to my ext hd, it gives the option if you select 'alongside other os'  then forward, you can choose the location and let it do itself, then put the bios boot order back to its original config and i got the grub screen, chose ubuntu and it worked. takes a minute or two to load from the ext hd but it seems to be running just as smooth and quick as before. i've added all the updates no probs.  only problem now, my windows disc didn't have a network card on it so i can't access the internet to get all the updates, gonna try and download it through ubuntu and put it on a disc then add to xp, will that work???    many thanks :-)

---

### Post by Eternal_Light on 2011-02-07
yea or you can just copy-paste it from ubuntu straight into the internal disk. As i said above ubuntu can see and handle NTFS (thats the filesystem your xp is running on) normally. You just gotta open nautilus from ubuntu and if you look at the places menu the internal disk of the computer should be there.

---

### Post by waynefoutz on 2011-02-07
> **PhilRogers34 said:**
> That's exactly  what i want, thank you! i shall have a go at this method. i've already sat through 4 install onto the ext hd with no luck and i tried an install of xp onto the ext hd to see if its the bios that's the problem. so my apologies to everyone if come across as a bit moody  xp wouldn't boot from the ext but my hd is showing in the portable configuration for the bios.   i want to set the pc up before i get too heavy into ubuntu and have to much data on my drives. at the moment it's only a few gig of music that's easy to replace if i lose it.   Its just i want to keep ubuntu as far away from xp as possible, i know its pretty much virus proof but i worry that if someone hacks into windows they can find a way through into ubuntu without me knowing  i am actually getting used to it and i can just feel that it's not draining resources like windoze and runs a lot better, which is why i want to keep it for web surfing and music etc.


Thanks again :-)

Glad it worked out. I assumed you would want to keep your data.

---

