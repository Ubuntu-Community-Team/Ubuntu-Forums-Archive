---
title: "How do I make a home server?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by PoisonSerpent on 2009-05-16
Hello everybody,

My 2nd question to the Ubuntu Forums. This time, I am wanting to make a home server to share to computers on my network. I know Windows XP will not do the job, so I thought I should use Ubuntu. Well, I think it's harder to choose than I thought it would be. It will be a very simple network. All computers (other than the "server") will be connected to the Router (for Internet). They will all be connected to the server for file sharing, though. For example: I want to transfer a file from my upstairs laptop to the server, but I want to be able to retrieve it later with my downstairs tower. I transfer the file from my laptop to my "server", and then later on, I retrieve it from my "server" to my tower. What is the fastest way I could do this? Here are the specs for the "server"

2 Hard Drives (1 20GB "Primary")
              (1 40GB "Slave")
1GB RAM
?? Processor
(Not too sure about the processor. I do not have an OS on it quite yet, but it is no more than 2 years old)

Also, I would not have file sharing set up between the two computers, just the computer and the server. And is there any main difference b/w the Server Edition of 9.04 and the Desktop?

Thanks,

PoisonSerpent

---

### Post by anewguy on 2009-05-16
Try this - I used it to initially set up the server I ran for a while (until I lost one of my computers):

[http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

Dave :)

---

### Post by Iusedtowearatie on 2009-05-16
You don't need a server for those things. I use one of these:
[http://www.lacie.com/se/products/product.htm?pid=11247](http://www.lacie.com/se/products/product.htm?pid=11247)

I access it from WinXP, Ubuntu and Mandriva machines simultanously.

---

### Post by ninjapirate89 on 2009-05-16
True but that involves buying additional hardware. Why do that when you can just share over a home network?

---

### Post by stinger30au on 2009-05-16
just a pc with a few hdds on it and create a directory on the hdds and share them out on the lan

restart the pc and its all good

just a normal ubuntu 8.04 or 9.04 will do this standing on its head

---

### Post by pbpersson on 2009-05-16
> **PoisonSerpent said:**
>  And is there any main difference b/w the Server Edition of 9.04 and the Desktop?



From what I have been told, the server version does NOT have a GUI - it is all command line.  The theory is that if the machine is just a file server you will never need a GUI to do point and click anything, you can remote to the machine and do everything from a command line.

Also, there is something called WebMin that will allow you to use a web browser to remotely administer your Ubuntu server using a GUI.

---

### Post by Iusedtowearatie on 2009-05-16
> **ninjapirate89 said:**
> True but that involves buying additional hardware. Why do that when you can just share over a home network?

Agreed. But I kind of like it... It's just a small box behind a photo in my book shelf, not a big noisy computer box.

---

### Post by ninjapirate89 on 2009-05-16
> **Iusedtowearatie said:**
> Agreed. But I kind of like it... It's just a small box behind a photo in my book shelf, not a big noisy computer box.

It would be a good thing to buy if you only had a laptop and you didn't want to store all of you media on it.

---

### Post by lisati on 2009-05-16
I'm watching this thread with interest. I have successfully used the tutorial at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) as the basis for file sharing amongst my machines, starting with Feisty (7.04), skipping Gutsy (7.10), skipping Hardy (8.04), and using Intrepid (8.10) and Jaunty (9.04)

Edit: <aside>I'm checking out that some over-3-year-old backup CDs are usable, prior to deleting one machine's recovery partition. The process seems rather slow (Yawn!), perhaps they're suspect, but I don't know what's normal for this set, not having used them before, it's been over an hour, and there are still 3 disks of 9 to go after the current one. I'll be reviewing my options for using this machine as a server once it's finished</aside>

Edit 2: <aside>The recovery CDs have finished recreating the recovery partition, over two hours! eeek! no sign of error messages. I'm probably safe to delete the recovery partition after I've checked that XP can be started</aside>

---

### Post by sloggerkhan on 2009-05-16
Install ubuntu server. Install samba. Configure samba, you're good to go.

---

### Post by pbpersson on 2009-05-16
There is a GUIDE?  Heck, I did it all by trail and error :o

If only I had known ;)

Although, once I got one machine working I used the samba.conf from that machine to configure the rest  :)

---

### Post by Elfy on 2009-05-16
> just a normal ubuntu 8.04 or 9.04 will do this standing on its headI did exactly that with 8.04 - figured it would be better to use the LTS. I wanted a GUI as I have it plugged into tv for films etc.

---

### Post by lisati on 2009-05-16
> **pbpersson said:**
> There is a GUIDE?  Heck, I did it all by trail and error :o

If only I had known ;)

Although, once I got one machine working I used the samba.conf from that machine to configure the rest  :)

There are a handulf of tutorials and "how tos" scattered through the forums. I can't remember how I came across the one I used but bookmarked it, saved my Firefox bookmarks with the "foxmarks" add-on (it's now called ["xmarks"]("http://www.xmarks.com/")), and when I do a fresh install on one of my machines, all I have to do is reload xmarks, and go to the link to remind myself of what to do.

---

### Post by gn2 on 2009-05-16
> **ninjapirate89 said:**
> True but that involves buying additional hardware. Why do that when you can just share over a home network?

Works out cheaper long term, the additional electricity cost for a full PC running 24/7 will be more than the cost of a new NAS drive.
I have an NSLU2 and can thoroughly recommend it.

---

### Post by ugm6hr on 2009-05-16
Not wanting to rain on Ubuntu's (or XP's) parade, but I would recommend FreeNAS over both if all you want is a file server for backups etc.  If you decide you want to use SMB or NFS, it will cope with both.  It will also rsync or unison backups easily.

See the link below (in my sig) for complete details on how easy it is.

Essentially, the hardware you are proposing will achieve this feat with any OS (including Windows).  However, I think power consumption is reduced by using a minimal OS like FreeNAS.

Additionally, FreeNAS is much easier to manage from any of the other networked computers; all that is required is a web browser (i.e no VNC or SSH etc required).  You also don't need a keyboard, mouse, monitor etc.

The only problem I foresee is that you say the server is not going to be connected to the router.  If not, how exactly do you intend to connect to it?

> **gn2 said:**
> Works out cheaper long term, the additional electricity cost for a full PC running 24/7 will be more than the cost of a new NAS drive.
That is true, I'm sure.  However, I'm not sure it makes that much difference.  I have my FreeNAS box plugged into an electricity meter, and it runs at around 40-50W which will cost around £30-40/yr; I suspect a standalone NAS would be closer to 10-20W, which will be half as expensive to run.  Obviously, FreeNAS has more options than most standalone boxes though (torrents, web server etc).

---

### Post by sloggerkhan on 2009-05-16
> **ugm6hr said:**
> Not wanting to rain on Ubuntu's (or XP's) parade, but I would recommend FreeNAS over both if all you want is a file server for backups etc.  If you decide you want to use SMB or NFS, it will cope with both.  It will also rsync or unison backups easily.

See the link below (in my sig) for complete details on how easy it is.

Essentially, the hardware you are proposing will achieve this feat with any OS (including Windows).  However, I think power consumption is reduced by using a minimal OS like FreeNAS.

Additionally, FreeNAS is much easier to manage from any of the other networked computers; all that is required is a web browser (i.e no VNC or SSH etc required).  You also don't need a keyboard, mouse, monitor etc.

The only problem I foresee is that you say the server is not going to be connected to the router.  If not, how exactly do you intend to connect to it?

The one downside to FreeNAS is that it will note be a Router/Firewall OTB, also not sure how it is for RAID.

---

### Post by ugm6hr on 2009-05-16
> **sloggerkhan said:**
> The one downside to FreeNAS is that it will note be a Router/Firewall OTB, also not sure how it is for RAID.

OP mentions they have a router; presumably this is a modem-router with built-in firewall.  I don't use RAID, but FreeNAS will act as a software RAID if you ask it to.  There are plenty of people who use this function successfully.

---

### Post by mc0yad on 2009-05-16
Talking servers, can you help.
my educated friend set up my home server.
for our club site.
we had a power failure and now I / WE or anyone else cant access it
Please help
Ken

---

### Post by anewguy on 2009-05-16
The link I recommended in my first post is very simple, and very easy to follow.  It allowed me to share files between Linux and Windows (I normally just left the file on the server) and to backup as well.  I'm not sure why this is being made more complicated than it is.  It's simple.  I even had my server running wireless.  My router had MAC filtering on it, plus the network stayed on my side of the router and was not accessable from the internet side by normal means.  I never had any problems with it.  Extremely simple to set up.

Dave :)

---

### Post by 3rdalbum on 2009-05-16
I built myself a home server box recently. I installed Ubuntu 8.10 Desktop onto a USB thumb drive (an actual installation, not just a startup disk), configured Samba using *system-config-samba*, and unplugged the monitor and keyboard. Oh, I also installed *ssh* so I can remotely administer it; some people swear by *Webmin* too but honestly *ssh* is all I need. In case you don't know, Ssh allows me to access a command-line prompt on my server, from another machine on the network. Handy.

The machine is even running a Gnome desktop so I can run graphical administration/configuration tools using forwarded X. Basically I open an SSH connection with the "-X" option:

```
ssh 192.168.0.12 -X
```

And then I can type the program's name to run it, and the window will appear on my desktop rather than the server's desktop. Very handy and very cool :-)

I also have it set up to run *transmission-daemon* on login, which provides a web-based interface and downloads and uploads torrents without me having to leave my full desktop computer turned on all night. I can control *Transmission* from the web interface or by sending commands directly through ssh and the *transmission-remote* program.

---

### Post by PoisonSerpent on 2009-05-16
> **anewguy said:**
> Try this - I used it to initially set up the server I ran for a while (until I lost one of my computers):

[http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

Dave :)

I think I'll stay with the Ubuntu Desktop, and then if I want to, I'll switch to Server.

Thanks for all the help.

---

### Post by anewguy on 2009-05-16
You can add the gui to the server just by installing the gnome desktop package.

Dave :)

---

