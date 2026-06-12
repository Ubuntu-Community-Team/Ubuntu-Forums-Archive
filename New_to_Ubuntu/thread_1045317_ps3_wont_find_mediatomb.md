---
title: "ps3 wont find mediatomb?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by insanity99 on 2009-01-20
i have changed the config file the way this site tells me to: [http://www.ps3forums.com/showthread.php?t=138248&highlight=mediatomb](http://www.ps3forums.com/showthread.php?t=138248&highlight=mediatomb)

but my ps3 wont find it. i dont need linux on my ps3 do i? also am i ment to set up wireless on ubuntu? because i haven't because i am wired to my router.

thanks

---

### Post by MrWES on 2009-01-20
> **insanity99 said:**
> i have changed the config file the way this site tells me to: [http://www.ps3forums.com/showthread.php?t=138248&highlight=mediatomb](http://www.ps3forums.com/showthread.php?t=138248&highlight=mediatomb)

but my ps3 wont find it. i dont need linux on my ps3 do i? also am i ment to set up wireless on ubuntu? because i haven't because i am wired to my router.

thanks

1) Is the wireless on the PS3 working; can you connect to the Playstation Store?

2) Are you running a firewall; moblocker or IPBlock on your Ubuntu computer?

Bill

---

### Post by philinux on 2009-01-20
I'm just having a go at this. Got fuppes working but it's very slow. Should not need sudo and in the config file it tells you which line to change and uncomment. Just waiting my ps3 returning from my son to try it out. will report back.

---

### Post by insanity99 on 2009-01-20
> **MrWES said:**
> 1) Is the wireless on the PS3 working; can you connect to the Playstation Store?

2) Are you running a firewall; moblocker or IPBlock on your Ubuntu computer?

Bill


yeah i can access the store and i haven't got a firewall

---

### Post by billgoldberg on 2009-01-20
I write that guide a while ago ,I've updated the guide since then on my blog:

[http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/](http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/)

Try that first.

Some questions:

I’m going to start by stating the obvious here, don’t think I presume you don’t know anything about pc’s, it could help other if it isn’t useful for you.

Are the computer and the ps3 on the same network?

Is upnp enabled in the router?

Do you have a firewall running that is blocking mediatomb?

Did you save the changes made to the config file, and are you sure you didn’t make any typo’s?

Is mediatomb running? (type “sudo mediatomb” if you aren’t sure).

---

### Post by philinux on 2009-01-20
Bill, I got this running without sudo. Just waiting my ps3 back to test it at that end. If you use sudo the config file has root access only in your home folder.

---

### Post by insanity99 on 2009-01-20
> **billgoldberg said:**
> I write that guide a while ago ,I've updated the guide since then on my blog:

[http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/](http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/)

Try that first.

Some questions:

I’m going to start by stating the obvious here, don’t think I presume you don’t know anything about pc’s, it could help other if it isn’t useful for you.

Are the computer and the ps3 on the same network?

Is upnp enabled in the router?

Do you have a firewall running that is blocking mediatomb?

Did you save the changes made to the config file, and are you sure you didn’t make any typo’s?

Is mediatomb running? (type “sudo mediatomb” if you aren’t sure).

i haven't setup a network on linux, sorry dont know much about networking.

upnp is enabled on my router. no firewall. and i did save(had to become root user first) and i never opened mediatomb through terminal i went to Applications > sound and video > mediatomb, does that matter?

---

### Post by philinux on 2009-01-20
Ok i got my ps3 back. It found mediatomb without prompting. Shared folders show up in the pc directory on the ps3 just fine. Also works without sudo.

Photo's in slideshow appear really quick, like i was sat at pc. fuppes is getting uninstalled as I type. Thanks for this thread.

---

### Post by insanity99 on 2009-01-20
does it find host folder?

---

### Post by philinux on 2009-01-20
Under the picture icon on the ps3 is a MT mediatomb icon. I click this and I choose pc directory. I can then drill down to my pictures folder which is a shared folder. You have to add these folders to mediatomb from its web page by clicking the + button at the top right from "file System"

---

### Post by insanity99 on 2009-01-20
i cant figure this out :( is mediatomb the best tversity alternative?

---

### Post by insanity99 on 2009-01-21
is mythTV like tyversity?

---

### Post by insanity99 on 2009-01-24
sorry, but i still can't figure this out.

---

### Post by nannus on 2009-01-25
Try to start mediatomb from terminal.
```
$  mediatomb
```

Post output here. That would make it a lot easier to help.

---

### Post by nannus on 2009-01-25
I have Mediatomb compiled from latest SVN (0.12), with support for YouTube content, Apple movietrailer service, and thumbnails for pictures/videos/albumcovers, streaming *.iso dvd's and even rar'ed *.iso's. It's a great uPnP-server if you set it up somewhat correctly.

---

### Post by insanity99 on 2009-01-25
do i need to to anything on ubuntu? like network settings or something?

---

### Post by insanity99 on 2009-01-25
here is the output:
```
neil@ubuntu:~$ sudo mediatomb
[sudo] password for neil: 

MediaTomb UPnP Server version 0.11.0 - http://mediatomb.cc/

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2009-01-25 20:28:18    INFO: Loading configuration from: /home/neil/.mediatomb/config.xml
2009-01-25 20:28:18    INFO: Checking configuration...
2009-01-25 20:28:18    INFO: Setting filesystem import charset to UTF-8
2009-01-25 20:28:18    INFO: Setting metadata import charset to UTF-8
2009-01-25 20:28:18    INFO: Setting playlist charset to UTF-8
2009-01-25 20:28:18    INFO: Configuration check succeeded.
2009-01-25 20:28:18    INFO: Initialized port: 49152
2009-01-25 20:28:18    INFO: Server bound to: 192.168.0.2
2009-01-25 20:28:19    INFO: MediaTomb Web UI can be reached by following this link:
2009-01-25 20:28:19    INFO: http://192.168.0.2:49152/

```

EDIT:it working now...dont know why :D

---

### Post by st14n on 2009-03-01
I had similar problem due to MediaTomb connecting to the wrong IP address. It was confused by several network interfaces. Using the --ip option to pass the IP of my computer solved the problem, e.g. ```
mediatomb --ip 192.168.2.101
```.

---

