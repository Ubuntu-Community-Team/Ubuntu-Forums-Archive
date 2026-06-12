---
title: "Cannot install Lubuntu 11.04!"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by gigenieks on 2011-08-22
Hi all,


I have friend and we are trying to install Lubuntu.
His [COLOR="DarkRed"]**hardware specs are**[/COLOR]:
[LIST]
[*]CPU: Intel Celeron 900MHz
[*]RAM: 384MB SDRAM (PC100)
[*]VGA: Intel 82810E Graphics Controller (32MB)
[/LIST]
need more?

What have we tried / done?

[LIST=1]
[*]LiveCD install --> **freeze**
[*]Alternate Install --> **freeze**
[*]Minimal CD install - "Command Line install" --> [COLOR="DarkRed"]**screen is blinking**[/COLOR] (~5 times / sec) and nothing happens.
[/LIST]

Note both LiveCD & Alternate freeze on pressing enter on "Install"..

I have some experience with *buntus (around 2 weeks) he is very new. I have to explain what to do.

So what is the issue? :confused: And more importantly how can we fix it - install Lubuntu 11.04? :confused:

Please help.

---

### Post by gigenieks on 2011-08-22
Update: He found PCI videocard: Trident 94.
[Wikipedia - Trident Microsystems:]("http://en.wikipedia.org/wiki/Trident_Microsystems")
> 
TVGA 9000 - first integrated (VGA+RAMDAC) VGA chipset

It seems, that VGA is from 1994!! :shock:

We will try it! Does *buntu support such old hardware in any way?

---

### Post by whatthefunk on 2011-08-22
> **gigenieks said:**
> Update: He found PCI videocard: Trident 94.
[Wikipedia - Trident Microsystems:]("http://en.wikipedia.org/wiki/Trident_Microsystems")

It seems, that VGA is from 1994!! :shock:

We will try it! Does *buntu support such old hardware in any way?

The 810 graphics card should work.  How long did you let it try when you did the alternate install?  It might take a while...

---

### Post by gigenieks on 2011-08-22
> 
The 810 graphics card should work.

I agree. [Intel:]("http://www.intel.com/support/graphics/sb/cs-010512.htm")
> 
Most versions of the Linux* operating system include Intel® graphics drivers.

> 
How long did you let it try when you did the alternate install?

Friend says max 20minutes.

---

### Post by whatthefunk on 2011-08-22
> **gigenieks said:**
> Friend says max 20minutes.

Hmmm...it should have done something in 20 minutes.  When you burnt the CD, did you do it at a slow speed?  It could be a faulty CD burn.  The LiveCD install method probably wont work on your system, so maybe try to burn another CD with either the alternate install or the minimal install on it and try again.

---

### Post by gigenieks on 2011-08-22
He told me, that he is using CD RW (meaning 1 CD which he rewrites). I will ask at what speed he burned. ;)

Edit: He told me, that he didn't notice at what speed he was burning. Just used default settings. I instructed him following:

1) Buy Verbatim CD (not CD RW)
2) Burn **Alternate CD** with Infra Recorder (*[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto") section "2000/ XP / Vista / 7: Infra Recorder")*
3) Use slowest speed possible while burning.
4) Before going to sleep, leave installing Lubuntu.
5) Next day tell what happened.

Let's see tomorrow if that helped.

---

### Post by gigenieks on 2011-08-22
Update:

He bought new Verbatim CD (not RW). Burned Alternate Install CD at 4x. And booted from it successfully.

Note: Got .ISO [[COLOR="Navy"]here[/COLOR]]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall") and downloaded [l[COLOR="navy"]ubuntu-10.10-alternate.iso[/COLOR]]("http://phillw.net/lubuntu-10.10-alternate.iso") 

1. Isn't there **lubuntu-11.04-alternate.iso** yet?

Anyway, I wanted to found Hash for it, so I went [[COLOR="navy"]Ubuntu Hashes[/COLOR]]("https://help.ubuntu.com/community/UbuntuHashes").
I found hashes only for:
> 
lubuntu-11.04.iso
lubuntu-10.10.iso

**_NO_** [COLOR="Indigo"]**lubuntu-10.10-alternate.iso**[/COLOR] !

2. Why is that so?

Further: I downloaded same .iso and we both got md5sum:
> 
1932a563c99ae40721d1f37c3804c372

So, I assumed it is save to burn that Verbatim CD. :)


[COLOR="DarkRed"]**_Finally_**[/COLOR], when I suggested him to do [COLOR="Purple"]**"Check CD for defects"**[/COLOR] he got this:
> 
Integrity test failed
the ./isolinux/boot.cat file failed the MD5 checksum verification
Your CD-ROM or this file may have been corrupted


And, if I understand him correctly, **before OR while** doing "Check CD for defects" he got following --->

> 
undefined video mode number 314, press enter for video modes available, space to continue or wait 30 seconds

Now I am really confused.



[SIZE="3"]How should we proceed? [/SIZE]

Edit: maybe this thread is somehow related (dunno): [http://ubuntuforums.org/showthread.php?t=1830222](http://ubuntuforums.org/showthread.php?t=1830222)

---

### Post by whatthefunk on 2011-08-22
So did he get it on his computer successfully?  
I havent been able to find a 11.04 alternate install either, so maybe they havent released it yet.  If your friend can get 10.10 on successfully then he can upgrade using the update manager.
Weird about the hashes too...dont know where you can find them.

About the undefined video mode message....I think I got that as well when I installed.  I just pressed space to skip that part and everything went fine.

---

### Post by gigenieks on 2011-08-22
> 
So did he get it on his computer successfully?

Not yet.

I probably don't have enough experience to fix this on my own. [Googled]("http://www.googlubuntu.com/") what I could. There is just too much information out there; problem is not that, but that I don't know what EXACTLY I have explore (read) to find a fix.

So now I am just waiting for SOMEONE to reply.. :/ Can't do nothing more. And I can bump only around 1-2 in 24h. :/

HELP!!!

---

### Post by whatthefunk on 2011-08-22
What exactly happens when he tries to install the OS?  Does it still freeze?

---

### Post by gigenieks on 2011-08-22
[Answer]("http://ubuntuforums.org/showpost.php?p=11175599&postcount=1")
Do you need something to clarify?

---

### Post by gigenieks on 2011-08-24
UPDATE:

He managed to install Lubuntu on other HDD (80GB; first he tried to do that on 10GB). While he was using Alternate CD to install he got some error about "not available network" can't really tell.. 

Now he can use Lubuntu, but there are 2 issues:

1) There is no network capabilities!
2) It is way too slow if you compare it to XP SP2.

While 2) you can solve, in my opinion, by activating "additional drivers", you need to solfe 1) first, because of that.

How do he connect to internet? It goes something like this --->

His PC is in 2nd floor but his modem is in 1st. Modem is having DSL internet and modem is connected with router. And router is connected with his PC.
I hope I explained it correctly and understandable? :confused:

**How do we troubleshoot this?** :confused:

---

### Post by Rex Bouwense on 2011-08-24
Sorry about your problems.  I have played around with Lubuntu and it is smoking fast so something is wrong.  To correct the Internet problem, take the computer to the first floor and connect it to the router using an Ethernet cable.  That will get you on the Internet.

---

### Post by gigenieks on 2011-08-24
I'm really confused... :confused:
> 
take the computer to the first floor and connect it to the router using an Ethernet cable

If he do that, only difference is in which floor is that PC. Nothing else changes. :D

P.S. [QUOTE='Rex Bouwense]
I have played around with Lubuntu and it is **smoking fast** so something is wrong.
[/QUOTE]
Can you tell specification of that PC? (CPU, RAM, VGA)
Because my friend has very OLD pc. (he haven't got AGP slot :shock:)

---

### Post by Rex Bouwense on 2011-08-24
Sorry, I guess that I misunderstood.  I thought that he could not connect to the Internet on the second floor.  If the computer is already plugged into the router with an Ethernet cable and still cannot get on the Internet, have him ensure that he has enabled networking.

---

### Post by gigenieks on 2011-08-24
> enabled networking
Doesn't it supposed to be enabled by _default_?
And how exactly can he check if there is "enabled" networking?

---

### Post by Rex Bouwense on 2011-08-24
Have him right click on the connection ICON in the panel and he should be able to see if networking is enabled and also if wireless is enabled.

---

### Post by amjjawad on 2011-08-28
Hello there,

I have skimmed through the thread and I noticed few things so I'll try to highlight some steps that IMHO is better to do:

1- Lubuntu and any other LXDE OS "should" work without any problem on such machine - speed wise. Best approach IMHO from A-Z will be:

a- Download Lubuntu 11.04
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Downloading%20Lubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Downloading%20Lubuntu)

b- Check MD5SUM and compare with the hashes.
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

c- Burn a CD (CD-R) with a low burning speed (8x) and there are many apps or programs to do that job:
- Nero for Windows
- K3b for Linux
- [InfraRecorder]("http://infrarecorder.org/?page_id=5")

d- Turn the machine ON, insert the LiveCD and enter BIOS. Make sure CDROM is the first device to boot from.

e- Before Installing, better to check Lubuntu from the LiveCD and see how well it will perform on that machine. If everything or most of the things will work out-of-the box then go a head and install.

f- IMHO, best approach in such case and ONLY IF Lubuntu will be the ONLY OS installed on that machine, better to create NEW Partition Table. 
Usually, I do that with GParted but I can't remember now whether GParted is included with Lubuntu 11.04 LiveCD or not? most probably it's not as far as I remember but that should NOT be a problem. During installation, there is an option to Create New Partition Table.

There is Terminal Command that will reset the HDD (write Zero to all sectors) but hopefully this won't be needed in your case. I do that ONLY when there are tons of problems with the HDD and when Create New Partition Table doesn't help.

g- Install Lubuntu and make sure to create two important partitions:

Root (/) which is ext4
and Swap Partition which is: [Size of SWAP = Size of RAM] OR [Size of SWAP = Size of RAM * 2]

Yes, I'm talking about Manual Installation. If you go for the automatic installation, you won't find that option for create new partition table.

h- After 30mins or so, everything should be ok UNLESS there is a hardware issue or something. The installation Process shouldn't take too long.


2- For the networking issue, first of all, make sure the Wireless Signal can be received . Connecting the machine through LAN Cable is and will be the best approach.

Then, make sure there is a driver for your Network Cards.

Accessories > LXTerminal 

Please run:

```
sudo lshw -C network

```

Please post the result here and wrap up the text with "CODE" tags or highlight the text and click "#".

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]



Good luck :)

---

### Post by verymadpip on 2011-08-28
GParted is indeed on the Lubuntu 11.04 Live CD.
Which is nice.  Makes life a tad easier too.

---

### Post by whatthefunk on 2011-08-28
> **amjjawad said:**
> Hello there,

I have skimmed through the thread and I noticed few things so I'll try to highlight some steps that IMHO is better to do:

1- Lubuntu and any other LXDE OS "should" work without any problem on such machine - speed wise. Best approach IMHO from A-Z will be:

a- Download Lubuntu 11.04
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Downloading%20Lubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Downloading%20Lubuntu)

b- Check MD5SUM and compare with the hashes.
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

c- Burn a CD (CD-R) with a low burning speed (8x) and there are many apps or programs to do that job:
- Nero for Windows
- K3b for Linux
- [InfraRecorder]("http://infrarecorder.org/?page_id=5")

d- Turn the machine ON, insert the LiveCD and enter BIOS. Make sure CDROM is the first device to boot from.

e- Before Installing, better to check Lubuntu from the LiveCD and see how well it will perform on that machine. If everything or most of the things will work out-of-the box then go a head and install.

f- IMHO, best approach in such case and ONLY IF Lubuntu will be the ONLY OS installed on that machine, better to create NEW Partition Table. 
Usually, I do that with GParted but I can't remember now whether GParted is included with Lubuntu 11.04 LiveCD or not? most probably it's not as far as I remember but that should NOT be a problem. During installation, there is an option to Create New Partition Table.

There is Terminal Command that will reset the HDD (write Zero to all sectors) but hopefully this won't be needed in your case. I do that ONLY when there are tons of problems with the HDD and when Create New Partition Table doesn't help.

g- Install Lubuntu and make sure to create two important partitions:

Root (/) which is ext4
and Swap Partition which is: [Size of SWAP = Size of RAM] OR [Size of SWAP = Size of RAM * 2]

Yes, I'm talking about Manual Installation. If you go for the automatic installation, you won't find that option for create new partition table.

h- After 30mins or so, everything should be ok UNLESS there is a hardware issue or something. The installation Process shouldn't take too long.


Thats all fine an dandy except that, due to hardware restrictions, the OP was using an alternate install CD which means that there is no LiveCD option and no md5sums to be found.  Also, his installation issue has been solved so...  Lets read a little better:P

---

### Post by amjjawad on 2011-08-28
> **whatthefunk said:**
> Thats all fine an dandy except that, due to hardware restrictions, the OP was using an alternate install CD which means that there is no LiveCD option and no md5sums to be found.  Also, his installation issue has been solved so...  Lets read a little better:P

Please "read" the first line in my previous post and you'll understand why I posted it to begin with ;)

Forms for everyone. When I post something, it doesn't mean it's for one user or for one thread, it's for the whole world and whoever have similar issue OR want to learn something new. I still login here not just to post, but to learn as well.

---

### Post by coolbrook on 2011-08-28
Consider installing Wary Puppy Linux, recently updated, if you want a tolerable desktop experience using  those specs.

---

### Post by amjjawad on 2011-08-28
> **verymadpip said:**
> GParted is indeed on the Lubuntu 11.04 Live CD.
Which is nice.  Makes life a tad easier too.

Yes. I'm on Lubuntu Live Session and it's included

System Tools > GParted

Thanks :)

---

