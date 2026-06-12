---
title: "Network performance problem Ubuntu 7.10"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by mkz on 2008-03-17
Hi all,

I recently installed Ubuntu 7.1 on my Thinkpad T61 laptop.
I've been using Windows for years and I've heard a lot of nice comments regarding Ubuntu ... I told my self ... let's try it ! :)

Well, almost everything is working fine but I'm getting a network performance problem.

When I try to copy some files from a smb network disk (Western Digital WorldBook) the transfer ratio is horrible !

I tried to install lastest e1000 module but nothing changes :(

this is the "ethtool eth0" output
```

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

```

I've taked a curious screenshot of system monitor while copying those files ... (take a look at network graphic) (see attached png file)

Any ideas ?


Thank you.

Mkz.

---

### Post by mkz on 2008-03-19
Well,

I've recently installed a new e1000 driver version released 2 days ago and ...

it Works !!! :D

Downloaded from : [http://sourceforge.net/projects/e1000/](http://sourceforge.net/projects/e1000/)
The release that worked for me is : 7.6.15.5

I'm at work now and it's working here, this afternoon I will try it at home too.

Kind Regards,

Mkz.

---

### Post by mkz on 2008-03-19
ermmmm...

I'm going crazy :-k

I've tested on my home network (1 Win XP, 1 Western Digital MyWorldBook, 1 Linksys switch 10/100) and ...


When I power on my laptop and start some network traffic (i.e. amarok playing an internet radio station) my network graphic showed in system monitor is like de png I've attached on my first post, I mean it seems to drop and goes up again every second.

I execute
```

sudo rmmod e1000
sudo modprobe e1000

```

And now the graphic seems to be stable.

But regarding the transfer ratios ...

I made some tests :

**1 .- Copying 1 Gb file from Win XP shared folder to my Ubuntu Laptop :**
The downstream ratio goes near 4 MBytes/sec. Well, it isn't the best transfer ratio for a 100Mbits connection but ... it's acceptable

**2 .- Copying 1 Gb file from WD Disc to Win XP :**
It copies the file in 3 minutes ~ 5,5 MBytes/sec (1 Gb / 180 secs)

And now the horrible tests :

**[COLOR="Red"]3 .- Copying 1 Gb file from WD Disc to Ubuntu Laptop :[/COLOR]**
The downstream ratio goes to [COLOR="Red"]1,6 MBytes /sec[/COLOR] :shock::shock:
It wastes more than 13 minutes to finish the copy.


[COLOR="DarkGreen"]**[SIZE="5"]And now ... the great surprise !!![/SIZE]**[/COLOR]

**4 .- Copying 1 Gb file from WD Disc to a virtual machine with Win XP running inside my Ubuntu Laptop**
The downstream ratio goes to **[SIZE="4"]6.7 MBytes / sec[/SIZE]** :lolflag:

What the hell is happenning ?!?!?!?!?


Kind Regards,

Mkz.

---

### Post by mkz on 2008-03-21
well, I've been doing some more tests ...

It seems that the problem only appears when I'm trying to copy files from/to my Ubuntu Laptop to/from my Western Digital My World Book NAS disc.

Well, I've hacked my WD Disc and ... surprise !!  there is a little Linux system running inside !  :D

I installed a wsftp server inside my WD disc and I continued doing some more tests ...

But ... 

The results continues being horrible :

**_[SIZE="4"]getting a file using sftp :[/SIZE]_**
/shares/internal/PUBLIC/tests/largefile.iso   0% 8896KB [COLOR="Red"]533.3KB/s[/COLOR]   53:13 ETA

**_[SIZE="4"]getting a file using scp :[/SIZE]_**
largefile.iso                                      0%   11MB [COLOR="Red"]680.5KB/s[/COLOR]   41:39 ETA

Well, I bought this disk to make backups (near 80 Gb size per backup) and it works perfectly copying from/to Windows XP system.

Another interesting test is that I've get horrible performance doing the same tests using my Laptop wireless adapter instead the ethernet adapter.

I know that I'm the only one who is posting in this thread, but I hope may somebody could read it some day and throws some light over this problem.



Any Ideas ?


Kind regards,

Mkz.

---

### Post by djamu on 2008-03-28
i'm having a similar issue now...
after observing this at a friends house, I thought it was just a router issue.
but all of a sudden Inoticed this too on my setup ( I usually sftp ).

So for a good understanding the whole network is gbs..
all other protocols just work fine

I got several nics in my fileserver most of them directly connected to my workstations ( I do 3D stuff so I need fast connections )

using samba 

server <> XP boxes 30-50MBs 
server > ubuntu desktops 200kBs
server < ubuntu 30-50MBs

now if I copy multiple files from the server to the ubuntu desktop and / or I generate extra traffic using a ping flood ( ping -i 0.0125 192.168.1.11 which pings server every 0.0125 sec )  then the speed normalizes ( 30-50MBs )...

to OP can you also confirm that with multiple files copying the speed normalizes ?
tried also messing with the smb.conf socket opptions but that doesn't change anything ..



:confused:

---

### Post by mkz on 2008-04-05
Hello again :)

I tried to copy some files while I was pinging to same IP at same time and ...

no luck for me :(

The results are the same.

Kind Regards,

Mkz.

---

### Post by djamu on 2008-04-08
Well I fixed my issue, turns out to be a borked nic driver,  which is weird because only samba had transfer issues, all other protocols worked flawless making one to believe it can't be a driver issue.
I was quiet skeptical against the "buy a new nic" solution which is essentially a "get other chip set / other driver" solution...

but it worked ( just used an updated driver ), tested this first on a hardy machine ( which one can assume uses newer drivers )...

---

### Post by spectro on 2008-05-02
being lurking the forums and googling around for this same reason. I solved this by setting my network cards to half duplex:

```

sudo ethtool -s eth0 speed 100 duplex half autoneg off

```

With this in both my desktop and laptop I improved download speed to laptop from 16 Kb/s to 8.5 MB/sec.

---

### Post by mkz on 2008-05-30
Well,

I don't know why but ...

yesterday I tried to copy a large file again from my WD Disk to my laptop computer and ... it works with succesful transfer ratio (5,4 Mbytes/sec)

What are the changes I made from the original situation to final situation ?

mmmm...

I've installed Hardy 8.04 with 2.6.24-17 Kernel.

I'm happy again :D


Kind Regards,

Mkz.

---

