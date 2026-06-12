---
title: "a few questions before i install ubuntu"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by bambi231991 on 2010-02-28
ok i have been wanting to learn linux, i have been running ubuntu off of a live cd, i currently have windows 7, i like ubuntu alot better than & but i have come across a few problems that i am hoping fix themselves when i install. ok first, with the live cd, it tells me my wireless driver is not recognized and that i need to install driver, now then i install it and it tells me to resart, well when i restart, no settings arew saved and i still cant access internet wirelessly, i can still access via ethernet though, will this fix itself when i fully install? also i have most of my music collection in mp3, when I go to play them they wont play, do i have to convert all thesse to flac or that ogg one first? any help would be appreciated thanks

---

### Post by spiky001 on 2010-02-28
Hi welcome, the 1st issue might be fixed by installif not there are enough ppl on here who can help, 2nd you can mp3s seem to play ok there are a few music players about VLC for 1, are you gonna dual boot with win7

---

### Post by bambi231991 on 2010-02-28
no nott dual booting fully replacing

---

### Post by spiky001 on 2010-02-28
well as i said music not a problem wireless can be fixed mine all worked without a problem, at least if it dont work you will learn abit about linux is all good fun

---

### Post by bambi231991 on 2010-02-28
thanks well hope this works

---

### Post by spiky001 on 2010-02-28
come back lets us know how it gose

---

### Post by quik_lives on 2010-02-28
If I'm not mistaken (I'm still learning majorly myself) the mp3 issue will be resolved by installing the restricted extras package after install, won't it? Anyone?

---

### Post by mickie.kext on 2010-02-28
Wireless problem can be fixed, MP3 is not problem at all. You only need to install "restricted extras" via Software Center, and maybe enable Medibuntu repos.

But I would suggest you to switch your preferred format for music to FLAC from now on, just because it is better:D.

---

### Post by cap10Ibraim on 2010-02-28
I had similar issues 
After installation visit the update manager , check all the libraries

---

### Post by bambi231991 on 2010-02-28
now one more question, will my files be saved on my hard drive? or will i have to re download them?

---

### Post by spiky001 on 2010-02-28
You must back them up or you will loose them sorry

---

### Post by MoebusNet on 2010-02-28
Before you install, I highly recommend you read:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

especially if you intend to save your Windows installation (dual-boot).

Also useful for multimedia:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Welcome to Ubuntu Linux!

---

### Post by dragonboss on 2010-02-28
If you've installed apps or packages while running ubuntu from the live cd you will have to reinstall them when you install ubuntu on the hard drive.

---

### Post by dragonboss on 2010-02-28
Ailurus is a good app if you want to learn linux because it has tips that teach you commands for various tasks and other good features. The way to download it can be found [here]("http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html") along with other useful apps and tweaks

---

### Post by bambi231991 on 2010-02-28
okay got ubuntu fully installed, now back to the problem with the internet wireless card, i am running an inspiron 1545 when i booted from the live cd it gave me the option to install the drivers i had missing now that i have installed buntu i go back to the same place it looks like a card with a lock on it, it is saying i dont have any someone help please

---

### Post by spiky001 on 2010-02-28
I take it you are on wired now? go 2  system administration update manager and run that 1st

---

### Post by bambi231991 on 2010-02-28
> **spiky001 said:**
> I take it you are on wired now? go 2 applications system update manager and run that 1st
applications only has accesories games graphics internet and office and sound/video and ubuntu software center
 
nvm foun it it was under system

---

### Post by spiky001 on 2010-02-28
sorry re read post before I changed it

---

### Post by bambi231991 on 2010-02-28
> **spiky001 said:**
> sorry re read post before I changed it
 its ok i am quick enough i figured it out, its just linux is so different from what i am used to, i am a computer repair tech and this is confusing, but i was told to learn linux

---

### Post by J V on 2010-02-28
> **bambi231991 said:**
> okay got ubuntu fully installed, now back to the problem with the internet wireless card, i am running an inspiron 1545 when i **booted from the live cd** it gave me the option to install the drivers i had missing now that i have installed buntu i go back to the same place it looks like a card with a lock on it, it is saying i dont have any someone help pleaseThe live cd will not save any changes, just run the installed ubuntu, this is the same problem that you had when restarting the live cd reset the settings.

---

### Post by bambi231991 on 2010-02-28
ok now i have followed that advice i ran every update available and now when i boot it says " Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)" what do i do it wond let me into linux, whewn i first installed it it popped up with m y username and asked for a password after the updates it now pops up with something else and a bunch of options what do i press to get back to my desktop
?

---

### Post by mcoleman44 on 2010-02-28
What options does it give you? You do have 9.10 and not 10.04 right? Just making sure because if you do a partial upgrade in 10.04 you will get thes type of results. Does it say:
grub rescue>

---

### Post by bambi231991 on 2010-02-28
> **mcoleman44 said:**
> What options does it give you? You do have 9.10 and not 10.04 right? Just making sure because if you do a partial upgrade in 10.04 you will get thes type of results. Does it say:
grub rescue>
 it says GNU GRUB version 1.97~beta4
Then the options are:
Ubuntu, linux 2.6.31-19-generic
then it says the same thing as above with (recovery mode) added
 
then ubuntu, linux 2.6.31-14-generic then the same option with (recovery mode) 
then Memory test (memtest86+)
then memory test (memtest86+, serial console 115200
 
and at the very bottom it sats press enter to boot selected OS, 'e' to edit the commands before booting or 'c' for a command line

---

### Post by mcoleman44 on 2010-02-28
Did you try booting into recovery mode? Or do you still have the same problem? 
Just try booting into your old kernel 2.6.31-14.

---

### Post by bambi231991 on 2010-02-28
> **mcoleman44 said:**
> Did you try booting into recovery mode? Or do you still have the same problem? 
Just try booting into your old kernel 2.6.31-14.
 it worked omg thank you very very much, to every one . ok now let me see if i can get my wireless working

---

### Post by mcoleman44 on 2010-02-28
A very useful hint for not onlyUbuntu but Linux in general is "if it's not broken, don't fix it". As for mp3s all you have to do is download the restricted extras package. Or if you could open up Rythmbox
and import your music and it will prompt you to install the plugins required to play the media. That's if you backed up your music. You don't need to download vlc or any other specific media player. Rythmbox is under applications>sound an video>rythombox

---

### Post by 3rdalbum on 2010-02-28
> **bambi231991 said:**
> it worked omg thank you very very much, to every one . ok now let me see if i can get my wireless working

Plug your computer into an Ethernet port on your router so you have an internet connection.

Go to System > Administration > Software Sources and check that the first four checkboxes are ticked - these give you access to the Ubuntu software repositories.

Close the window. If you have made changes, it will ask you if you want to reload the package list; click Reload and after it's finished loading the package lists you can go to the Hardware Drivers program and it should offer you a wireless driver, if there is one to load.

If it didn't ask you if you want to reload the package list, then you can go to System > Administration > Synaptic Package Manager and hit Reload there.

---

