---
title: "help switching over..."
date: 2009-04-03
forum: New to Ubuntu
---

### Post by thesuperjman on 2009-04-03
... i heard ubuntu was faster and easier than windows and mac, and so far it is. im not really dumbfounded when it comes to computers but im not the smartest either. im enjoying ubuntu and its running better than any other operating system ive had so far. the computer im on used to have windows vista. when i installed ubuntu it said i would also be able to reboot into windows if i needed too. but i dont know how to do this. also i want to know if i can take all my music from itunes on windows and put it into linux without burning multiple cds (i have 1000s of songs) 
im sure there are many threads out the like this, and i apologize if im wasting forum space.

all help is much appreciated.
thanks- john

---

### Post by marco123 on 2009-04-03
When you reboot you should be presented with a screen (see attached screenshot) where you choose which operating system you boot into.

For itunes just mount the Windows partition by clicking on it in the "Removable Media" section in the Places dropdown menu then drag the music folder accross.  You could then import the folder into Rhythmbox: Applications>Sound and Video>Rhythmbox.

Cheers, Marco.

---

### Post by thesuperjman on 2009-04-03
i hate to sound so helpless but i didnt see a removable media in the places menu. do i need to download an app?

---

### Post by marco123 on 2009-04-03
Which version are you using 8.04LTS or 8.10 (the newest one)?

Also could you post the result of:

> sudo fdisk -l

that's a lowercase L

Cheers, Marco.

Edit: That command goes in the terminal:  Applications>Accessories>Terminal

---

### Post by CadetD on 2009-04-03
> **thesuperjman said:**
> i hate to sound so helpless but i didnt see a removable media in the places menu. do i need to download an app?

Your Windows partition may just show up with a weird name. 

If you see a device under PLACES that is not completely descriptive, click on it.

---

### Post by thesuperjman on 2009-04-03
> **marco123 said:**
> Which version are you using 8.04LTS or 8.10 (the newest one)?

Also could you post the result of:



that's a lowercase L

Cheers, Marco.

Edit: That command goes in the terminal:  Applications>Accessories>Terminal

8.10:

this comes up:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc22bc22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19084   153292198+  83  Linux
/dev/sda2           19085       19457     2996122+   5  Extended
/dev/sda5           19085       19457     2996091   82  Linux swap / Solaris

---

### Post by thesuperjman on 2009-04-03
when i booted my computer from the command thing, i didnt see any Windows, just Ubuntu Linux stuff, i hope i didnt accidenaly delete when installing linux.

---

### Post by albinootje on 2009-04-03
> **thesuperjman said:**
> when i booted my computer from the command thing, i didnt see any Windows, just Ubuntu Linux stuff, i hope i didnt accidenaly delete when installing linux.

Sorry to be the bringer of bad news.
But you did overwrite your Windows partition according to the fdisk output you gave.

You can install testdisk and see what you can recover, see here :
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
and here a howto :
[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

Hopefully you have some backups.

---

### Post by halitech on 2009-04-03
as albinootje said, your windows partition is gone. Do you have the music on an ipod/mp3 player of some sort? if you do, then you can plug it in and should be able to copy your music off there.

---

### Post by thesuperjman on 2009-04-03
> **halitech said:**
> as albinootje said, your windows partition is gone. Do you have the music on an ipod/mp3 player of some sort? if you do, then you can plug it in and should be able to copy your music off there.

hm well thats bad news sort of. wont be so bad if i can recover the music, yes i do have an ipod with music on it. how do i get this on my computer?

if this problem is solved there wont be much from windows im missin at all.

ps: how did this happen? i installed the ubuntu on a disk, then did the little 'test drive' and installed it from there. i thought it was supposed to partial it, or whatever thats called. i guess i messed up big somewhere.

but yea, aside from 2 games i had installed (which i can always reinstall) i really only miss my itunes.

---

### Post by albinootje on 2009-04-03
> **thesuperjman said:**
>  ps: how did this happen? i installed the ubuntu on a disk, then did the little 'test drive' and installed it from there. i thought it was supposed to partial it, or whatever thats called.

Yes. The newer partitioner in the 8.10 installation is a bit tricky sometimes (was it already there in Hardy ? I normally use manual partitioning).
You are not the first to have give Ubuntu the whole disk to use, as that (giving Ubuntu the whole disk) is sometimes the default option given in the partitioner part of the installation.

Hmmm, I cannot find this bug in the partitioner bugs yet :
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=partitioner&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=partitioner&search=Search+Bug+Reports&field.scope=all&field.scope.target=)

---

### Post by albinootje on 2009-04-03
> **thesuperjman said:**
> i do have an ipod with music on it. how do i get this on my computer?

Perhaps this is useful :
[https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)
[http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)

---

### Post by halitech on 2009-04-03
> **thesuperjman said:**
> hm well thats bad news sort of. wont be so bad if i can recover the music, yes i do have an ipod with music on it. how do i get this on my computer?

if this problem is solved there wont be much from windows im missin at all.

ps: how did this happen? i installed the ubuntu on a disk, then did the little 'test drive' and installed it from there. i thought it was supposed to partial it, or whatever thats called. i guess i messed up big somewhere.

but yea, aside from 2 games i had installed (which i can always reinstall) i really only miss my itunes.

if its an ipod (true blue apple version) you may want to look at gtpod (I think its called) or look in synaptic for ipod type music programs. Install one of them (some use amarok) and then plug your ipod in. it should be recognized as a diskdrive and put an icon on the desktop you can click to open. To transfer, use whichever app you install.

ps. windows games don't normally run on linux unless you use WINE or a virtual machine to run windows.

---

### Post by thesuperjman on 2009-04-03
ok thanks for the advise.

yea, i have WINE already, and all ive put on it so far is Windows live messenger, but it doesnt work properly.

---

### Post by halitech on 2009-04-03
for windows live messenger, use aMSN, pidgin or 1 of the native linux apps, no need to use WINE to run that when there are native apps that work just as well.

---

### Post by albinootje on 2009-04-03
> **thesuperjman said:**
>  yea, i have WINE already, and all ive put on it so far is Windows live messenger, but it doesnt work properly.

This could be useful too for new Ubuntu users :
[http://www.osalt.com/](http://www.osalt.com/)

And if you really can't find native Linux alternatives for certain MS-Windows based software, take a look here :
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)
[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)

---

### Post by thesuperjman on 2009-04-04
gtkpod is proving to be difficult

aMSN does nothing but say logging in for hours.
i must be missing something here....

---

### Post by albinootje on 2009-04-04
> **thesuperjman said:**
> gtkpod is proving to be difficult

Can you try the alternatives ?
[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)
Quote from that webpage :
> 
AmaroK and Banshee in particular often come highly recommended from Ubuntu Forums members. 

Read also this :
[http://www.ubuntux.org/ipod-vs-ubuntu-the-struggle-for-perfect-synchronization](http://www.ubuntux.org/ipod-vs-ubuntu-the-struggle-for-perfect-synchronization)
Songbird -> [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)
> 
aMSN does nothing but say logging in for hours.
i must be missing something here....

Try these two alternatives mentioned here :
[https://help.ubuntu.com/community/WindowsLiveMessenger](https://help.ubuntu.com/community/WindowsLiveMessenger)
And there's also "kopete" and "gajim" to try.

---

### Post by thesuperjman on 2009-04-04
im going to try out amarok, but on this download page--- [http://amarok.kde.org/wiki/Download](http://amarok.kde.org/wiki/Download) --- i only see kubuntu. will this suffice for regular ubunutu? also with amarok can i put the songs on my ipod into amarok itself, so i can be sure i wont lose them (and be able to play music on my computer as well)?

i know im asking a lot but you guys are real helpful, thanks.

---

### Post by halitech on 2009-04-04
Amarok is a KDE based app but it will work on ubuntu/Xubuntu or any other desktop (just means it will pull some needed libraries to work properly)  You also don't need to download it from the website, just open Synaptic and search for it or open a terminal and type
```
sudo apt-get install amarok
```

---

### Post by thesuperjman on 2009-04-04
ok. i got the amorak now. thanks.

can i transfer songs from my ipod to amarok? ive been looking online and i cant find help elsewhere.

---

### Post by halitech on 2009-04-04
if you open amarok and go to Settings - Configure Amarok and look on the left side, you should see Devices. Click on that and you should see your ipod listed in the upper right. It should say /dev/sdxx and  then Plugin with a drop down window. for an Ipod select Ipod then apply and okay. then click on Connect in the upper  left and you should see all your files on the ipod.

---

### Post by thesuperjman on 2009-04-05
is that supposed to work with the second gen. ipod touch (which i should've mentioned i use earlier)?

---

### Post by CLomax on 2009-04-05
For music -> Banshee: ```
sudo apt-get install banshee
```
iPod instructwords: [http://www.simplehelp.net/2007/07/08/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/08/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/)

For MSN -> Emesene: ```
sudo apt-get install emesene
```

---

### Post by halitech on 2009-04-05
> **thesuperjman said:**
> is that supposed to work with the second gen. ipod touch (which i should've mentioned i use earlier)?

I'm honestly not sure so go with Clommax's suggestion of Banshee which has instructions to go with it for the ipods.

---

### Post by thesuperjman on 2009-04-06
something stupid and wierd is happenin with my firefox. everything is running fine but on the top right where there should be the x button, minimize button, and that square window button, is nothing but a loading symbol. idk why its doing this. the only way to get off fire fox is to file>quit. this is tedious because for some reason i cant see the rest of my open apps at the bottom of the screen unless i quit firfox.

attempted solutions: restarting firefox, and restarting my whole computer.
neither worked.
any ideas?

---

### Post by CLomax on 2009-04-07
> **thesuperjman said:**
> something stupid and wierd is happenin with my firefox. everything is running fine but on the top right where there should be the x button, minimize button, and that square window button, is nothing but a loading symbol. idk why its doing this. the only way to get off fire fox is to file>quit. this is tedious because for some reason i cant see the rest of my open apps at the bottom of the screen unless i quit firfox.

attempted solutions: restarting firefox, and restarting my whole computer.
neither worked.
any ideas?

Can you supply a screenshot?

I speculate that it could be down to Compiz. Try running...
```
metacity --replace
```
...in the terminal.

---

### Post by roger_1960 on 2009-04-07
Hi

Have you tried pressing the F11 key?  This tooggles between full screen and what you describe.

---

### Post by CLomax on 2009-04-07
> **roger_1960 said:**
> Hi

Have you tried pressing the F11 key?  This tooggles between full screen and what you describe.

I suspected that at first but that would still show the 'close/minimise/maximise' buttons. What **thesuperjman** is describing sounds more like a Compiz issue.

---

### Post by nothingspecial on 2009-04-07
Don`t know what your firefox problem is but just a couple of snippets that might make it less annoying till you fix it.

Alt + F9 will minimize a window
Alt + F4 will close it
Alt + F10 will maximize
Alt + F5 will unmaximize
Alt + F8 will let you resize a window without clicking on it`s sides
Alt + F7 lets you move it.

---

### Post by thesuperjman on 2009-04-07
ok, i got it working again. thanks to all.

---

### Post by CLomax on 2009-04-07
> **thesuperjman said:**
> ok, i got it working again. thanks to all.

Just for the benefit of others finding this thread with the same problem. What solved your problem?

---

### Post by thesuperjman on 2009-04-07
well its wierd. i wasnt in full screen before, but i hit F11 and it put me into full screen and when i hit it again to go back to normal, the buttons were back. does that make sense?

edit: my friend today told me rythymbox works with an ipod touch, but i want to know, can i upload the songs from my ipod into rythymbox so i have them on my computer?

---

### Post by thesuperjman on 2009-04-08
any advise on the above ? rythmbox didnt recognize the tough either.

can anyone tell me how to get my computer functioning normally again? i cant youtube, i have no music and for some reason random websites like [www.oneill.com](www.oneill.com) wont work for me.

---

### Post by albinootje on 2009-04-08
> **thesuperjman said:**
> any advise on the above ? rythmbox didnt recognize the tough either.

This is about the Ipod Touch ?
> 
can anyone tell me how to get my computer functioning normally again? i cant youtube, i have no music and for some reason random websites like [www.oneill.com](www.oneill.com) wont work for me.

*) Install the flash plugin :
1) open a terminal
2) type in :
```

sudo apt-get install flashplugin-nonfree

```

The website you mentioned seems to be focused on using flash.
For music, install the "ubuntu-restricted-extras" package.
After this restart Firefox.

Instead of using the terminal you can use Synaptic Package Manager to install these packages :
-> System -> Administration -> Synaptic Package Manager

See also :
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by albinootje on 2009-04-08
Here's more information on the Ipod Touch in Ubuntu :
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
Looks pretty difficult at first sight :|

---

### Post by nothingspecial on 2009-04-08
> **albinootje said:**
> This is about the Ipod Touch ?


*) Install the flash plugin :
1) open a terminal
2) type in :
```

sudo apt-get install flashplugin-nonfree

```

The website you mentioned seems to be focused on using flash.
For music, install the "ubuntu-restricted-extras" package.
After this restart Firefox.

Instead of using the terminal you can use Synaptic Package Manager to install these packages :
-> System -> Administration -> Synaptic Package Manager

See also :
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Did you do this yet?

Also whenever I do a fresh install the very first thing I do is go [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")  (click the red here).

Justcopy and paste everything relevant to 8.10 Intrepid Ibex.

That will sort out youtube, music, video the lot.

Oh yeah, and when you get to the java bit it will ask you to accept the licence, press the tab key to move it to yes - you`ll see what I mean when you get there.

---

### Post by thesuperjman on 2009-04-08
ok nothingspecial i'll try that out because i already have the flash plugin.

---

### Post by thesuperjman on 2009-04-09
how do i know if im 32 bit or 64 bit ubuntu?

---

### Post by albinootje on 2009-04-10
> **thesuperjman said:**
> how do i know if im 32 bit or 64 bit ubuntu?
```

uname -a

```
should show you details about your Linux kernel.
Mine shows this :
> 
Linux ubuntu-desktop 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686 GNU/Linux

From the "i686" you can see that it's 32 bit.

The 64 bit version should show 64 bit as "x86_64".

---

### Post by thesuperjman on 2009-04-10
ok thanks.

---

### Post by F6F Freak on 2009-04-10
Rythmbox does not support iPod touch.
You will have to jailbreak your device to sync up.
[www.redsn0w.com]("http://www.redsn0w.com")
This is still in beta phases, so google iPod touch fans fourm and look around there if you are unsure.
That was for a second gen touch.
If you have a first gen, I think you will have to use Windows or Mac for the Jailbreak.
[iPhone Dev-team blog]("http://blog.iphone-dev.org/") will keep you up to date.

---

### Post by F6F Freak on 2009-04-10
> **albinootje said:**
> Here's more information on the Ipod Touch in Ubuntu :
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
Looks pretty difficult at first sight :|

Whomever wrote that guide is wrong. You don't have to borrow a Windows or mac Machine for the Jailbreaking. If you own a second gen, since there is no need for a restore, you may jailbreak with a Linux machine.

---

### Post by airtonix on 2009-04-10
might want to try out floola before doing something drastic to your ipod.

[http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/)

---

### Post by thesuperjman on 2009-04-11
will this 'jailbreaking' delete all my songs off my ipod? because right now this is the only thing i have that has all my music on it, half of which i paid for and won't be able to redeem if it's lost. so im trying to make sure i do this thing just right.

airtonix, what is this foola thing?

---

### Post by thesuperjman on 2009-04-12
can anyone answer the above?
and i have one more question, which will hopefully be the last on the ipod issue, how do i import music from my ipod into banshee? i know it can be done but i dont know how and google isnt showing good results.

edit: i also looked at the foolah page, im not sure about it, does anyone reccomend this over banshee?

---

### Post by nothingspecial on 2009-04-12
I may be wrong but in Banshee I think y6ou right click on your ipod icon on the left and choose import media(might be music). Have a good look round the menus, it`s something like that.

When I find my bloody ipod I`ll let you know properly.

---

### Post by thesuperjman on 2009-04-12
haha ok thanks. do i need to 'jailbreak' it first, before i can import?

---

### Post by nothingspecial on 2009-04-12
I have never jailbreaked (broken?) an ipod before other than rockboxing it (but that`s something else). If your ipod is the only thing with your music on it I wouldn`t recommend that you do it. 

The thing about linux is that it doesn`t tend to ask you if you`re sure (see my sig), so if you hit the wrong button that might be it. No music.

I would give the same advice for any similar situation. Do not make major alterations to any component of your system without backing up anything you don`t want to loose. Especially if you`ve never done it before.

I can look in to this for you but I wouldn`t do anything yet.

---

### Post by thesuperjman on 2009-04-12
ok yea i'm workin on knowing this stuff better. 
so i probably won't need a jailbreak just to import music from the ipod?

---

### Post by thesuperjman on 2009-04-12
if someone could give me an answer ASAP, it'd be much appreciated. i'm ready to get this situation over with.

---

### Post by thesuperjman on 2009-04-13
bump

---

### Post by thesuperjman on 2009-04-13
good thing my old ipod still has all the same music on it. i just imported it all from that. :)

so guys, im having problems with simple things like youtube and myspace music player, etc. just certain online medias. i downloaded flash player, and the restricted extras. what else should i do to get this stuff running.

---

### Post by CLomax on 2009-04-14
> **thesuperjman said:**
> good thing my old ipod still has all the same music on it. i just imported it all from that. :)

so guys, im having problems with simple things like youtube and myspace music player, etc. just certain online medias. i downloaded flash player, and the restricted extras. what else should i do to get this stuff running.

I'm not sure if this is right but you may need to add the Medibuntu repository if you haven't done so already.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Also, if you have the NoScript extension it may be blocking java scripts, ergo YouTube and MySpace videos.

Other than that I am at a loss as to why they aren't working.

---

### Post by thesuperjman on 2009-04-14
i have medibuntu, and how do i check for this no script thing?
edit, no i dont have no script and i dont know what the problem is now.

---

### Post by thesuperjman on 2009-04-14
can i open openoffice.org documents in windows?

---

### Post by juancarlospaco on 2009-04-15
> **thesuperjman said:**
> can i open openoffice.org documents in windows?

Yes, install **OpenOffice for Windows**, and open the Files.
*(plus the same app in both OS)*

:p

---

### Post by halitech on 2009-04-15
> **thesuperjman said:**
> can i open openoffice.org documents in windows?

I don't think MS Office will open the default file type but Open Office will allow you to save in MS office compatible formats (ie. doc, xls, etc)

Or you can install Open Office in windows and use the default file formats.

---

### Post by thesuperjman on 2009-04-15
it saved it under windows. 

how do i install itunes in wine? will it work there, especially if itunes is the only thing im putting in it?

---

### Post by halitech on 2009-04-15
some nice info here on setting it up in WINE

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13739](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13739)

there are native apps that work almost as well though (amarok, gtkpod, songbird)

---

### Post by thesuperjman on 2009-04-15
not for the new touch though. 
and for somereason (im importing songs with my old ipod classic) it wont import all songs in banshee.

---

### Post by halitech on 2009-04-15
ok, could be they haven't figured out all the coding settings yet for the newer touch ipods. Haven't use banshee or an ipod so not sure what to say there.

---

### Post by thesuperjman on 2009-04-15
hm, ok, well thanks ill check out that link for other things if i need'em.

---

### Post by thesuperjman on 2009-04-16
whenever i turn the computer off and turn it back on the time changes, and i always have to fix it back. how do i stop this?

---

