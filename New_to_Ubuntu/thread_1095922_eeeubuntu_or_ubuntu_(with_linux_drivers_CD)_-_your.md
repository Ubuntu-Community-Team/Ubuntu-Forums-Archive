---
title: "eeeubuntu or ubuntu (with linux drivers CD) - your opinion wanted :-)"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by ggerri on 2009-03-14
Hi there

hehe, feels a bit awkward to start as an ABSOLUTE BEGINNER, asking simple questions - being kind of Window crack which is definitely fed up with MS ;) So I've decided to go for ubuntu. Before I convert my desktop I've decided to get an eeepc 1000H and start learning here. Actually was able to get a Linux version of the eeepc. But 2 things I dont like with that: 1. it's not ubuntu and 2. its German (even I'm german speaking, I hate these translations ;-) ). With the eeepc came the restore CD with german linux and I guess with the hardware drivers :-)

So my questions... What would you gurus do:

Install the eeeubuntu from [http://www.eeebuntu.org](http://www.eeebuntu.org) (standard or NBR)

or

install the ubuntu 8.10 and use the drivers on the cd to get the hardware running (dont have a clue yet how to install drivers here :redface:](*,);) )


Another thing. whats best practice concerning partitions?
in windows you usually have a partition with the OS and installed programs and one with your data, so you can easily restore an image of the OS/Programs if you mess up something - without affecting your data.

Thanks for helping me here humble beginner I am ;)O:)

ps. gnome or kde? whats your favorite guys?

---

### Post by abybaddi on 2009-03-14
I would rather GNOME than KDE even if offers many customisation options. And you don't have to install the hardware drivers all are preinstalled in ubuntu.

---

### Post by carml on 2009-03-14
Not all the people here is a guru on Ubuntu;), a part of them is only a more skilled user.
IMHO to use Ubuntu on a netbook (also known as EEEPC) you should go for the EEE version of Ubuntu,because of the scecification of the EEE PC.
On a normal laptop or PC you'll not install an EEE version because a similar PC is more performant:). 
On Ubuntu as far as I know there aren't recovery partitions in use,you'll simply revover your PC from the net or from the cd,but only if you need to do so.
For what aout Gnome or KDE,that's a matter of preference,Gnome is the default desktop environment for Ubuntu,it's an intuitive and minimalistic one; instead KDE is more eye candy and WinXp-theme like.
I hope this can fit your questions.:)

---

### Post by Bölvaður on 2009-03-14
[http://hehe2.net/linuxhowto/howto-your-perfect-ubuntu-on-your-perfect-eee-pc/]("http://hehe2.net/linuxhowto/howto-your-perfect-ubuntu-on-your-perfect-eee-pc/")

other than eeeubuntu here is also [easypeasy]("http://www.geteasypeasy.com/")
or just plain ubuntu.

partitions:
/data &#8592; this is instead of having /home partition. The gain of this is that only data will be there, no config files and other unwanted stuff. You may need to create links from your /home/user/Documents/ and copy the link into your /data partition (in gnome you just right click the Documents folder and select make link, and then cut and paste...)

normally there are no drivers to be installed. linux has by far the biggest driver collection there is. but there always are few % odds on some hardware needing 3rd party drivers. And more likely... that it needs just some tweaking to work for the current drivers.


btw when you get more accustomed to things, please feel free to explore other than gnome and kde.. like awesome and fluxbox for an example. awesome + firefox plugin named vimperator is pure gold, as it will not require you to use mouse, but not having gnome will make you have to do more things manually.. like connecting to wireless networks (I made a 4 line script which I execute my self when I need to connect, very easy)

---

### Post by ggerri on 2009-03-14
Thanks for your quick reply, appreciate that mucho :P

abybaddi, just read that people had problems with stuff not working after regular ubuntu install on an eeepc (especially the WIFI). So I thought thats the reason for distros like eeepc and easypeasy. 

Thanks for explaining carml. Ok, Ill go for the eeebuntu with GNOME. Sorry if a wasnt that clear about recovery. I didnt mean a recovery partition, just an image you might back up your stuff from time to time. There are tools to make an image of your disk in ubuntu, right? I just want to keep my files and the installed programs/kernel separate. So you mean that with linux you usually only use one partition for progs/kerne/yourfiles?

Thanks :-)

---

### Post by stalkingwolf on 2009-03-14
I ran the EEE8.04 on my EEEPC704.  it did well with exceptional wifi.
I also ran Ubuntu 8.04.2 on it for a while, again with no issues.
Again I ran eeeubuntu 8.04.1 on my desktop for some time and it worked fine.
I ran it on the desktop because the video adapter ( S3 unichrome pro IGA) worked, the only distro ive found that it worked out of the box.  I have since learned to fix this issue so went back to the regular distro.


There is a "recovery partition" in Ubuntu  or at least a recovery mode.
when grub starts ( if you are not dual booting) hit escape and select recovery mode, hit enter.  it will do its thing then a window comes up giving you the options
reboot normally
fix broken packages
drop to root shell
atempt to fix X
make your selection hit enter when finished reboot.

i use it fairly often ( i break things)

---

### Post by ggerri on 2009-03-14
Thanks for the link and info Bölvaður :-)

hehe, have to admit that I dont know yet fully understand the partition thing here ;-) so you still have a /home directory but also a /data...

I think I will just start up my eeepc with the 'live-stick' and start going. any idea if I have to delete the partition first to be sure, that all of the stuff installed by asus is gone? 

ok, having another problem now which I have to fix first be4 I come back to bother you ;-)) Wanted to boot from my usbstick where I've installed eeeubuntu with unetbootin. Getting the message now that the usb stick is an invalid boot device.... 

until then ;-)

thanks guys!

---

### Post by Bölvaður on 2009-03-14
> **ggerri said:**
> so you still have a /home directory but also a /data...

No /home on my setup is just a directory, not placed on a dedicated partition.

[Standard filesystem hierarchy]("http://bnucourse.bnu.edu.cn/course/mathmodel/zuoxinian/Intro-Linux/images/FS-layout.png")

So I just make a new directory /data

(I already have made an empty partition)

Then I config fstab (file which you will get to learn later) to mount my partition to /data


but what you will do is :

1. make partitions
2. install ubuntu
3. during the install you manually select which partitions to use
3b. select the main partition as /. select the data partition to be /data
4. all is set and after the install it will all be good if you remember to select ext3 in the partitioning thingy.

---

### Post by blackened on 2009-03-14
Don't bother with partition and filesystem complexity on your first install. This isn't to say that you're not competent tinkering with the partition layout and setup, but you sound like you just want to get the machine up and running.

The only real difference between eeebuntu and regular Ubuntu is the kernel: eeebuntu comes stock with the array.org kernel that has better driver support for eee-native hardware. I suggest you install eeebuntu if only for the ease of configuration, though you're entirely welcome to install anything you want if you just enjoy tinkering and don't mind roughing it through some problems, though problems are not guaranteed.

I suggest you make a live stick of whichever distro you choose. If you decide to install, just use the guided partitioning to let it use the entire drive. If loosing the default Xandros install makes you uncomfortable, then there is also a guided partitioning that allows you to resize the existing data and install Ubuntu in the free space created.

---

### Post by ggerri on 2009-03-14
Thanks again Bölvaður :-) appreciate it much :-)

finally found out, that the usb stick i've tried had a bug. used another one and =D>\\:D/

hehe, blackened you're amazing! just wanted to ask about the partitioning thing and youve answered it before me writing anything :-) Yes, I'll go the easy way as suggested and will be happy to have a running system where I can try out things, the tips from Bölvaður and read thru that book from APress (love those books)

*** YOU GUYS ARE AMAZING ***

You all get free ice cream when you drop by here in Switzerland :-)

Cant wait to clean MS from all systems in the house (and later in the city ;-)

Ok, have to go and cook now, otherwise I'll have a problem with my lovely wife here ;-)

Cheers and take care
Gerald

---

### Post by ggerri on 2009-03-15
Thanks also to you stalkingwolf for the info about the 'recovery' thing. I hope I wont brake stuff too much here right now. happy my eeepc is running already with the eeeubuntu (still have to figure out if i have gnome or kde coz I was not asked during installation). might do the regular later and definetly on my desktop later....

Take care
Gerald

---

### Post by blackened on 2009-03-15
> **ggerri said:**
> ...still have to figure out if i have gnome or kde coz I was not asked during installation...

The default is Gnome (even in eeebuntu), so unless you installed some variant (Kubuntu, Xubuntu, Fluxbuntu, etc.) or added another DE/WM post-install, then that's what you're using.

---

### Post by ggerri on 2009-03-15
Thanks again blackened :D

---

