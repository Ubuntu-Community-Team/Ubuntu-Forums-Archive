---
title: "Is it possible to get iPod updates using Ubuntu?"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by MibunoOokami on 2011-06-03
Hello,

I think my iPod needs updated software/drivers so I want to know if it is possible to get updates for an iPod using Ubuntu, or should I say, without using Windows? 

Thanks

---

### Post by frankbooth on 2011-06-03
Unless there's a way to update the firmware *without* iTunes, then the answer is no. It's not possible since iTunes won't run under Ubuntu, not even through Wine (correct me if I'm wrong)

---

### Post by syntr on 2011-06-03
Your best bet is to install VirtualBox and make a Windows XP virtual machine, and install iTunes in that virtual machine. 

[iTunes does work with Wine](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347), but I don't know if I'd trust it to flash an iPod's firmware. :)

---

### Post by wolfen69 on 2011-06-03
Just keep in mind that if you update your ipod, it may no longer work in linux.

---

### Post by MibunoOokami on 2011-06-03
Thanks for all the replies.

> **frankbooth said:**
> Unless there's a way to update the firmware *without* iTunes, then the answer is no. It's not possible since iTunes won't run under Ubuntu, not even through Wine (correct me if I'm wrong)

I had a feeling this may be the case but I was hopeful.

> **syntr said:**
> Your best bet is to install VirtualBox and make a Windows XP virtual machine, and install iTunes in that virtual machine. 

Is VirtualBox a software program? It sounds a bit complicated, is it? I'm not terribly good with computers.

 > **syntr said:**
>  [iTunes does work with Wine]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347"), but I don't know if I'd trust it to flash an iPod's firmware. :)

Why is that?

> **wolfen69 said:**
> Just keep in mind that if you update your ipod, it may no longer work in linux.

How come?

---

### Post by wolfen69 on 2011-06-03
> **MibunoOokami said:**
> Thanks for all the replies.
How come?
Because every time apple comes out with an update, the linux devs wind up playing catch up to figure out the changes they've made. So if you update, it may be a while until it works again.

---

### Post by MibunoOokami on 2011-06-03
> **wolfen69 said:**
> Because every time apple comes out with an update, the linux devs wind up playing catch up to figure out the changes they've made. So if you update, it may be a while until it works again.

Oh... That's discouraging.

---

### Post by wolfen69 on 2011-06-03
It may be worth it to have windows in virtualbox just in case. Not the best solution, but since Apple purposely makes it hard on linux users, we have to do what we have to do.

---

### Post by fabricator4 on 2011-06-03
> **MibunoOokami said:**
> Oh... That's discouraging.

Hi again Mibuno.  :-)

I'll throw my vote in for VirtualBox too.  It's great, and I wish I'd tried it much earlier as it would have let me ditch my dedicated (work) windows machine much sooner.  I'm now in the process of seeing if I can do without a dedicated windows machine altogether, which means I'll be able to migrate my "main" machine over to the faster newer dual core desktop.

It's not as complicated as it sounds, though as you might expect there is a bit of a learning curve.  I'd say you've done much harder things, such as recovering your data after the 11.04 upgrade went wrong, setting up a separate /home, and re-configuring 10.04 so that you can work again.

Running VirtualBox will depend on two things: how much memory you have in the machine and having your Windows installation disks.  I'm currently running on a machine with 1 GB so memory is a little tight but it does work quite well.  I set up a virtual XP machine using 256Kb of RAM and it runs well, but slowly.  When I allocate 512Kb to Windows it runs well, but slowly.  (OK, a bit faster :-)

Running with the larger memory allocation still leaves enough RAM for Linux to do most things, but of course when the virtual machine is not running it does not use any RAM at all.  Keep in mind that if your version of Windows is Vista or 7 then the memory requirements may be greater.

There's two versions of VirtualBox, OSE (Open Source Edition) that is in the repositories, but it does not have USB support.  The second version is only available from Oracle, and includes USB 1.1 support, with USB 2.0 supported included in the extension pack.

Go [here]("http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html") to download the appropriate .deb package and the extension pack .deb.  Double click on the .deb files to install them (after you've downloaded them).

Chris.

---

### Post by MibunoOokami on 2011-06-03
Just so I got this straight, virtualbox will do anything windows can? Is virtualbox like one of those programs that allows you to create a virtual drive and mount iso images without a disk? 

> **fabricator4 said:**
> Hi again Mibuno.  :-)
It's not as complicated as it sounds, though as you might expect there is a bit of a learning curve.  I'd say you've done much harder things, such as recovering your data after the 11.04 upgrade went wrong, setting up a separate /home, and re-configuring 10.04 so that you can work again.

I think the only reason I was able to do all that was because a kind person wrote out a step by step tutorial and had the patience to answer about 10,000 questions. ;)

> **fabricator4 said:**
> Running VirtualBox will depend on two things: how much memory you have in the machine and having your Windows installation disks.  I'm currently running on a machine with 1 GB so memory is a little tight but it does work quite well.  I set up a virtual XP machine using 256Kb of RAM and it runs well, but slowly.  When I allocate 512Kb to Windows it runs well, but slowly.  (OK, a bit faster :-).

Memory is one thing my computer has a lot of, 4GB using 1.3 in Ubuntu. That's one thing I have in my favour.

> **fabricator4 said:**
> There's two versions of VirtualBox, OSE (Open Source Edition) that is in the repositories, but it does not have USB support.  The second version is only available from Oracle, and includes USB 1.1 support, with USB 2.0 supported included in the extension pack.

Chris.

Option 2 sounds like the best bet. I couldn't imagine using a computer without USB support.

---

### Post by ICEhockeyGOALTENDER on 2011-06-03
Yes...

Step #1
Download Songbird. As an alternative to iTunes, Songbird allows you to add music to your iPod, and purchase music through the 7digital online music store. Additional features of Songbird include concert alerts when your favorite musician is in town, music lyric look-up and Last.fm synchronization. Songbird is free to use, and can be downloaded from the official Songbird site for the Windows, Mac and Linux operating systems.

Step #2
Download CopyTrans Manager. This shareware application allows you to manage your music and update information on your iPod by simply connecting it to your computer via USB cable. As an iTunes replacement, CopyTrans Manager also provides support for audiobooks, videos and podcasts. As of 2010, CopyTrans Manager is only available for Windows XP, Vista and 7, and requires at least 128MB of RAM.

Step #3
Download GTKPod. As a free application that is compatible with the Windows, Mac and Linux operating systems, GTKPod allows you to edit, re-arrange and upload your music, videos and audiobooks to your iPod. Podcasts are not supported, but can be managed by downloading a third-party application. The one drawback of GTKPod is the lack of a music store in the application, which means you'll need to purchase music from online music sites if you wish to avoid using iTunes.

Songbird for Linux... [https://wiki.songbirdnest.com/Developer/Articles/Builds/Contributed_Builds#Linux](https://wiki.songbirdnest.com/Developer/Articles/Builds/Contributed_Builds#Linux)

---

### Post by Chronon on 2011-06-03
None of those are methods to update the firmware on the player.  

As someone mentioned upthread, updating the firmware may not be a good idea for compatibility with Ubuntu.

---

### Post by wolfen69 on 2011-06-03
> **MibunoOokami said:**
> Just so I got this straight, virtualbox will do anything windows can? Is virtualbox like one of those programs that allows you to create a virtual drive and mount iso images without a disk? 


Virtualbox allows you to run windows from within ubuntu. It's a real install, not an emulation. And yes, there is usb support. In full screen mode, (you need guest additions for that) you wouldn't even be able to tell you were using windows in ubuntu. And you can have a shared folder(s) that can be viewed by both os's. Virtualbox is awesome.

---

### Post by fabricator4 on 2011-06-04
> **wolfen69 said:**
>  And yes, there is usb support. In full screen mode, (you need guest additions for that) you wouldn't even be able to tell you were using windows in ubuntu.

Just a small clarification, I think you are saying that you need guest additions for the full screen mode, not USB support.  (It was a bit confusing when I read it the first time.)

For the benefit of others:
The PUEL (Personal Use and Evaluation License) version from Oracle has USB 1.1 support out of the box, and USB 2.0 support with the installation of the extension pack.  This is different to the "Guest Additions" mentioned in the above post.  Guest Additions adds some features to the VirtualBox GUI such as seamless mouse pointer support, full screen mode, and a very nice feature which will make it appear that Windows apps are running seamlessly on the Ubuntu desktop.

> 
And you can have a shared folder(s) that can be viewed by both os's. Virtualbox is awesome.

Agreed.  When considering the achievement of the VirtualBox developers I'm having trouble finding suitable adjectives: "awesome" doesn't seem to be quite enough somehow.


Chris.

---

### Post by fabricator4 on 2011-06-04
> **MibunoOokami said:**
> Just so I got this straight, virtualbox will do anything windows can? Is virtualbox like one of those programs that allows you to create a virtual drive and mount iso images without a disk?

Nearly correct. You have a virtual disk that gets a real installation of windows.  You can make this disk as large as you like, but it only takes up as much room as it needs - for example my virtual XP disk is set to 60Gb, but it's current size is only about three or four Gb.  You can also mount ISO images as though they are a disk in the virtual machine, so for example you can get an ISO of one of the Ubuntu LiveCD's and run it in "try without installing" mode.  The same goes for floppy disk images and probably other types as well.

When you start the virtual machine it is the equivalent of pressing the power button on a desktop PC.  You shutdown the same way you would do if the OS was on a real PC - by performing a correct shutdown wrt to that OS.

> 
I think the only reason I was able to do all that was because a kind person wrote out a step by step tutorial and had the patience to answer about 10,000 questions. ;)

Thanks  :redface:

It wasn't all me though, it's easiest to help those who will help themselves.  If you take the experience and use it as a learning tool my wish for all users of of Linux and the future widespread acceptance of the OS is one step closer.  Sad, geekish, but true :-)

> 
Memory is one thing my computer has a lot of, 4GB using 1.3 in Ubuntu. That's one thing I have in my favour.


Cool. Really Cool.  :-)
Do you have XP installation disks?  You could give XP 1Gb of RAM to play in and still have plenty left over to not even stress the system.  If you have any other applications you'd like to run in Windows you could install those as well.

Virtual Box is also a great way to test new Ubuntu releases.  Set up a new virtual machine, then boot (the virtual machine) with the LiveCD ISO and do a full disk install.  You can quickly see if the new release is good for you, and when you're finished you just delete it.  I think I may be testing 11.10 this way, though I do have extra partitions to burn so I haven't decided yet.  I might do it just to see how it works though.

> Option 2 sounds like the best bet. I couldn't imagine using a computer without USB support.

Absolutely.  The OSE version in the repositories is OK to test things out, but you soon miss the lack of USB support.  I didn't realise how much I took it for granted.  USB pendrives were almost science fiction only a dozen years ago, but now I can pick one up from Woolworths for less than $10. Amazing.

Chris

---

### Post by rrinjapan on 2011-06-04
I liked VirtualBox as well but I couldn't get it to recognize my iPod. I  suspect that I didn't have the USB support set up right ... 

If you can get iTunes in VirtualBox to recognize the iPods I think  that's the best way to go ... I dual boot XP and Mint 11 on my netbook  ... mostly so that I can format the iPods in Windows ... It was easier  to set up for me but if VB can be made to recognize the iPods that would  probably be a better choice. 

I'm not sure if I'm the second (or third) to post this but I've recently  (5 days ago) updated my iPods on a Windows machine and I can sync with  banshee and I suspect the other players as well ...

---

### Post by MibunoOokami on 2011-06-04
> **wolfen69 said:**
> Virtualbox allows you to run windows from within ubuntu. It's a real install, not an emulation. And yes, there is usb support. In full screen mode, (you need guest additions for that) you wouldn't even be able to tell you were using windows in ubuntu. And you can have a shared folder(s) that can be viewed by both os's. Virtualbox is awesome.

> **fabricator4 said:**
> Nearly correct. You have a virtual disk that gets a real installation of windows.  You can make this disk as large as you like, but it only takes up as much room as it needs - for example my virtual XP disk is set to 60Gb, but it's current size is only about three or four Gb.  

When you start the virtual machine it is the equivalent of pressing the power button on a desktop PC.  You shutdown the same way you would do if the OS was on a real PC - by performing a correct shutdown wrt to that OS.



I'm sorry, but I'm confused. A virtualbox is a real installation that starts up and shuts down like a real pc but isn't real? How does it differ from a dual boot OS?

---

### Post by wolfen69 on 2011-06-04
> **MibunoOokami said:**
> I'm sorry, but I'm confused. A virtualbox is a real installation that starts up and shuts down like a real pc but isn't real? How does it differ from a dual boot OS?

It differs because in a dual boot situation you can only run 1 OS at a time. They are completely separate installs. With virtualbox, you stay in linux and fire up windows and use it as you normally would. Then when you're done, shut windows down, and you are still in linux. No rebooting needed with virtualbox.

---

### Post by fabricator4 on 2011-06-05
> **MibunoOokami said:**
> I'm sorry, but I'm confused. A virtualbox is a real installation that starts up and shuts down like a real pc but isn't real? How does it differ from a dual boot OS?

As wolfen69 said, the virtual box runs windows on your Ubuntu desktop.  The attached screenshot may help.  The desktop is Xfce, not Gnome because I'm trying out Xubuntu at the moment. (It works just as well under Xfce as it did under classic Gnome)

Chris

---

### Post by fabricator4 on 2011-06-05
> **fabricator4 said:**
> As wolfen69 said, the virtual box runs windows on your Ubuntu desktop.  The attached screenshot may help.  The desktop is Xfce, not Gnome because I'm trying out Xubuntu at the moment. (It works just as well under Xfce as it did under classic Gnome)

Chris

Oh, and we go...  Shutdown!  :-)


Chris

---

### Post by MibunoOokami on 2011-06-05
Oh, so it's just like opening another window? That makes better sense.

---

### Post by Chronon on 2011-06-05
The guest system will display in its own window by default.  You can also tell Virtualbox to display in a couple of other modes (seamless or fullscreen, in particular).

---

### Post by ixtok on 2011-06-06
I have virtualbox 4.0.8 installed in my Ubuntu 10.10. I installed guest additions. I am using a HP mini netbook with 2gb ram. Windows XP runs very well, usb devices such as pen drives are no problem. I installed Itunes and am able to attach my third gen Ipod nano. Itunes acknowledges the ipod however it reports it as in a state of repair and will not list music, sync or perform any normal ipod function. It will go through a repair sequence which I believe updates the ipod. When finished it still reports the ipod as in a repair state. Of course doing this deletes all the files on the ipod. 

So my answer to the original question is yes, using virtualbox you can update an ipod  (nano third gen), but you will loose everything in it and will not be able to restore anything from Itunes running in a Windows XP guest.

I have tried version 8 and version 10 Itunes with the same results.

---

