---
title: "why is ubuntu 8.10 so slow ?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by smooth3006 on 2009-01-03
here are my specs:

HP Pavilion dv6809wm Entertainment Notebook :
AMD Turion 64X2 2.0GHz.
Nvidia Geforce 7150m
4GB DDR2 Ram
320GB Hard Drive
Atheros AR5007 802.11 b/g

this is really getting old too, doesn't matter what distro i use, ubuntu, kubuntu, xubuntu it just drags. web browsing is slow and the overall system performance is slow as a snail. with my specs it should be flying man.

the only tweak i did was by disabling ipv6 and that wouldn't affect system performance. even windows 7 beta is 10x faster and im not here to bash anything. 

i need some advice before i give up on linux for good. :(

---

### Post by taurus on 2009-01-03
Slow as in performing or slow as in graphic?  Have you installed an nvidia driver for your graphic card, System -> Administration -> Hardware Drivers?

---

### Post by Paqman on 2009-01-03
It shouldn't be slow on that system. Have you installed the graphics drivers?

---

### Post by smooth3006 on 2009-01-03
> **Paqman said:**
> It shouldn't be slow on that system. Have you installed the graphics drivers?

yes i installed the restricted nvidia drivers.

---

### Post by smooth3006 on 2009-01-03
it really is frustrating man, i love linux but this is crazy anymore. 

can anybody give me some advice ?

---

### Post by smooth3006 on 2009-01-03
> **taurus said:**
> Slow as in performing or slow as in graphic?  Have you installed an nvidia driver for your graphic card, System -> Administration -> Hardware Drivers?

overall all performance and web surfing too. i have zero issues in vista & windows 7 beta.

---

### Post by taurus on 2009-01-03
Are you running x86 or x86_64 version?

Did you install Ubuntu on it own partition or did you use wubi?

---

### Post by smooth3006 on 2009-01-03
> **taurus said:**
> Are you running x86 or x86_64 version?

Did you install Ubuntu on it own partition or did you use wubi?

x86 and yes its on it's own partition.

---

### Post by taurus on 2009-01-03
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
free -m
```

---

### Post by joukez on 2009-01-03
Try; sudo gedit /etc/hosts 
Then you see a file like this:
127.0.0.1	localhost 
127.0.1.1	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Change it in to this:
127.0.0.1	localhost ubuntu
127.0.1.1	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Ubuntu is the name of my box.

---

### Post by sadaruwan12 on 2009-01-03
Try installing x86_64 with your system I think it might solve your problem

---

### Post by AlexBellisBrown on 2009-01-03
> **sadaruwan12 said:**
> Try installing x86_64 with your system I think it might solve your problem

What is that? Surely 64bit is whats needed. What does x86 mean? :confused:

---

### Post by taurus on 2009-01-03
> **AlexBellisBrown said:**
> What is that? Surely 64bit is whats needed. What does **x86** mean? :confused:

32bit.

---

### Post by smooth3006 on 2009-01-03
> **taurus said:**
> What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
free -m
```


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe78ced41

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28715   230648824    7  HPFS/NTFS
/dev/sda2           28715       34213    44161016    7  HPFS/NTFS
/dev/sda3           34214       34279      530145   82  Linux swap / Solaris
/dev/sda4           34280       38913    37222605   83  Linux


 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=ade9e6bc-c843-4044-b1c3-bacdf6cfa1ea /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=208c125b-629d-49f1-8fa7-62ac2db84b6b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              35G  3.8G   30G  12% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  208K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.7M  1.5G   1% /dev
tmpfs                 1.5G  132K  1.5G   1% /dev/shm

total       used       free     shared    buffers     cached
Mem:          3039        859       2179          0         58        404
-/+ buffers/cache:        397       2641
Swap:          517          0        517

---

### Post by smooth3006 on 2009-01-03
> **sadaruwan12 said:**
> Try installing x86_64 with your system I think it might solve your problem

ive done x64 before and still had issues, all it would allow ubuntu to do is see the full 4gb of ram.

---

### Post by sadaruwan12 on 2009-01-03
> **smooth3006 said:**
> ive done x64 before and still had issues, all it would allow ubuntu to do is see the full 4gb of ram.
You mean same kind of issuse like you're having right now or some other stuff

---

### Post by AlexBellisBrown on 2009-01-03
> **taurus said:**
> 32bit.

Thanks, would never have guessed x86 meant 32 bit :popcorn::D

---

### Post by smooth3006 on 2009-01-03
> **sadaruwan12 said:**
> You mean same kind of issuse like you're having right now or some other stuff

same, slow

that's why it's frustrating.

---

### Post by AlexBellisBrown on 2009-01-03
> **smooth3006 said:**
> same, slow

that's why it's frustrating.

If you look in system moniter when your using your computer, what kind of work its your CPU doing? What percent is it running at? Idle?:popcorn:

---

### Post by smooth3006 on 2009-01-03
> **AlexBellisBrown said:**
> If you look in system moniter when your using your computer, what kind of work its your CPU doing? What percent is it running at? Idle?:popcorn:

right now cpu 1 is at 10% cpu 2 is at 20%

---

### Post by AlexBellisBrown on 2009-01-03
> **smooth3006 said:**
> right now cpu 1 is at 10% cpu 2 is at 20%

Then it shouldnt be running "slow". And how much RAM is being used?

---

### Post by smooth3006 on 2009-01-03
> **AlexBellisBrown said:**
> Then it shouldnt be running "slow". And how much RAM is being used?

339mb out of 3gb

honestly i have 4gb installed but im running an x86 system.

---

### Post by smooth3006 on 2009-01-03
so nobody has any ideas as to whats going on ?

---

### Post by DforVendetta on 2009-01-03
I am using x64

2.4 ghz quad core
6 gigs of ram

My box is blazing fast.

---

### Post by teh_yodeler on 2009-01-03
I'd say try the 64 bit version as well...  My laptop has a 1.8 ghz dual core processor and 2gb ram.  It blows me back in my seat it's so fast :guitar:

If that doesn't work maybe your computer just doesn't like ubuntu:confused::confused::confused:

---

### Post by smooth3006 on 2009-01-03
> **teh_yodeler said:**
> I'd say try the 64 bit version as well...  My laptop has a 1.8 ghz dual core processor and 2gb ram.  It blows me back in my seat it's so fast :guitar:

If that doesn't work maybe your computer just doesn't like ubuntu:confused::confused::confused:

i honestly don't see how x64 is going to help ? even with 3gb of ram it should be fast. i also don't feel like formatting again either. 

i agree about my laptop maybe not playing nice with linux. :confused:

---

### Post by teh_yodeler on 2009-01-03
Hmm... have you tried another, similar-load linux distro?  Maybe Mandriva or Fedora?

I wonder if it would be the same with those?

Oh I just thought of a good one - if you feel like it, install XFCE and use that for your session.  That wouldn't require a reformat.  I just did it the other day, and I like it a lot.

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by smooth3006 on 2009-01-03
> **teh_yodeler said:**
> Hmm... have you tried another, similar-load linux distro?  Maybe Mandriva or Fedora?

I wonder if it would be the same with those?

Oh I just thought of a good one - if you feel like it, install XFCE and use that for your session.  That wouldn't require a reformat.  I just did it the other day, and I like it a lot.

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

i tried mandriva before, didn't like it, much different than ubuntu. i just wish i could get my current install to work properly, i have it looking just the way i want it. i guess i could try xubuntu x64 but the themes suck for it.

---

### Post by DarkDancer on 2009-01-03
Actually he said you computer may not play nice with Ubuntu. If no one can come up with a solution, I would try another distro myself. My fried had to do that. Ubuntu and his computer were on shaky terms at best. So he tried Mint, that was better, but then he tried (among other things mind you, he tried a lot of distros just to play with them) Siddux and he likes it. It actually works well on his computer, has a rolling release (he doesn't have to chage every 6 months) and, it's Debian, so he knows the basic architecture of the system.

Just a reminder that just because Ubuntu may not work for you, no reason to scrap Linux in general.

---

### Post by teh_yodeler on 2009-01-03
The xfce option man... Try the xfce option

**Definitely** no reason to scrap linux in general.

I liked dreamlinux (which it xfce also)

---

### Post by Copernicus1234 on 2009-01-03
I think we need some real numbers here. How long does it take you to load the browser? To load ubuntu forums? To reply to a thread?

Firefox in Ubuntu can be slower to start than Internet Explorer in Windows since IE preloads with Windows, but that just shortens the startup time. For browsing, Firefox should always be faster.

---

### Post by smooth3006 on 2009-01-03
> **teh_yodeler said:**
> The xfce option man... Try the xfce option

**Definitely** no reason to scrap linux in general.

I liked dreamlinux (which it xfce also)

i may try linux mint or xubuntu x64 later.

---

### Post by smooth3006 on 2009-01-03
> **Copernicus1234 said:**
> I think we need some real numbers here. How long does it take you to load the browser? To load ubuntu forums? To reply to a thread?

Firefox in Ubuntu can be slower to start than Internet Explorer in Windows since IE preloads with Windows, but that just shortens the startup time. For browsing, Firefox should always be faster.

its not just about the Internet speeds, it's the overall lagging performance of the operating system.

---

### Post by zietbukuel on 2009-01-16
Whats the output of "top" (without quotes)?

---

### Post by airbornemist6 on 2009-01-19
I have just about the same problem.

Setup:

AMD Phenom X4 @ 3.0GHz
4GB RAM
64GB Ubuntu Partition
nVidia GeForce 9600GT (latest drivers)


Most of my problem is just with Firefox. Firefox is so ridiculously slow it's hard to do anything these days. I tried living in Ubuntu for 3 days... couldn't take it, had to reinstall Vista 64-bit. It was THAT bad.

On another note, I can boot off of my FSF membership card into gFreeSense. It works worlds faster than Ubuntu. It's using Icecat though, which is actually Firefox as well, but either way, it technically shouldn't be going that much faster.

---

