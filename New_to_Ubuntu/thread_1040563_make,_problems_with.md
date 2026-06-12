---
title: "make, problems with"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by fairy._.queen on 2009-01-15
Hi all!

I'm having some problems with the make command.
I'm trying to install ndiswrapper from source (it's necessary for my bro's pc to make kubuntu see the wireless adapter), so I downloaded the tar.gz file and ran
```
tar -zxvf ndiswrapper-x.xx.tar.gz
cd ndiswrapper-x.xx
make

```

But when it came to the "make" command, it just said "No rule to make target [...] Stop."

I have the build-essential package, as well as (I hope) all the other it needs to run.
Can you please help me?

---

### Post by theozzlives on 2009-01-15
ndiswrapper is in the repositories, just install it with Adept

---

### Post by fairy._.queen on 2009-01-15
I can't, I need to have it in a computer which can't connect to the internet.
That's what I need that package for.
Thanks anyway :-)

---

### Post by abn91c on 2009-01-15
ndiswrapper is in the repositories, try a wired connection in he computer to download the program

---

### Post by Shazaam on 2009-01-15
3 steps usually after extraction...
```

./configure
make
make install
```
For the last one (make install), depending on the app, you may need to put sudo in front of it...
```
sudo make install
```
There should be a README or an INSTALL file, check it/them for specific install directions.

---

### Post by abn91c on 2009-01-15
> **fairy._.queen said:**
> I can't, I need to have it in a computer which can't connect to the internet.
That's what I need that package for.
Thanks anyway :-)
go to the ubuntu website and download the .debs
go here to get them: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by stefangr1 on 2009-01-15
There's usually a README.txt file with the source code that tells how to compile it. Usually this means first running ./configure, sometimes you have to run "make all", you really can't know on forehand.

---

### Post by fairy._.queen on 2009-01-15
i tried with an ethernet connection but it didn't work... :-(
can you please give me an offline solution?
Thanks

---

### Post by wirelessmonkey on 2009-01-15
cd ndiswrapper.x.x.x.x


./configure
make 
sudo make install

---

### Post by fairy._.queen on 2009-01-15
> **stefangr1 said:**
> There's usually a README.txt file with the source code that tells how to compile it. Usually this means first running ./configure, sometimes you have to run "make all", you really can't know on forehand.

There is no configure. I found the README, though, and it said:
```
Make sure there is a link to the kernel source from the modules
directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.
```

As a matter of fact I don't have the "include" nor the .config
What should I do?

---

### Post by abn91c on 2009-01-15
> **fairy._.queen said:**
> There is no configure. I found the README, though, and it said:
```
Make sure there is a link to the kernel source from the modules
directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.
```

As a matter of fact I don't have the "include" nor the .config
What should I do?
go here to get the ubuntu ndiswapper .debs : [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)

---

### Post by fairy._.queen on 2009-01-15
> **abn91c said:**
> go here to get the ubuntu ndiswapper .debs : [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)

I had looked there before, but it said it was far better to compile from source, as there could be fatal errors...
can you help me?
Thanks anyway!

---

### Post by abn91c on 2009-01-15
> **fairy._.queen said:**
> I had looked there before, but it said it was far better to compile from source, as there could be fatal errors...
can you help me?
Thanks anyway!
if you are having problems already just use the debs and install with the default GDEBI, it usually takes care of the dependencies, it would not hurt anything since you are stuck now

---

### Post by fairy._.queen on 2009-01-15
> **abn91c said:**
> if you are having problems already just use the debs and install with the default GDEBI, it usually takes care of the dependencies, it would not hurt anything since you are stuck now

I'm stuck again! modprobe ndiswrapper gives a fatal error... ](*,)

Summarizing, I can't compile it from source and I can't install it from repos. Any ideas?

EDIT:

I have in fact installed ndiswrapper from repos, but i can't load the module (modprobe doesn't work)

---

### Post by fairy._.queen on 2009-01-15
I just found out THIS is the fatal error supposed to occure when you don't get ndiswrapper from source. Can someone please answer my initial question?
Thanks!

---

### Post by fairy._.queen on 2009-01-15
As I said, one of the problems seems to be that I don't have .config in /lib/modules/2.6.27-7-generic/build

Can anyone help?

---

### Post by abn91c on 2009-01-15
what kind of wireless card? post output of ```
sudo lshw -C network
```also do you get anything in applications>system>hardware drivers
and look at this other thread [http://ubuntuforums.org/showthread.php?t=1040312](http://ubuntuforums.org/showthread.php?t=1040312)

---

### Post by fairy._.queen on 2009-01-15
Here is the output:

```
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:a0:a9:6f
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:25:90:5d:95:71
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by abn91c on 2009-01-15
are you on  a MAC?

---

### Post by fairy._.queen on 2009-01-16
nope, PC. Thnx

---

