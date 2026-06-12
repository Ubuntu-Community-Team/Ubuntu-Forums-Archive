---
title: "Utorrent installation"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by soccerguy18 on 2011-08-24
I just can't understand how to install things!
anyways
I am trying to download utorrent client
but i dont know what to type into terminal.
I need to know exactly what to type and when to do that

I am sorry, I am a noob

---

### Post by dave01945 on 2011-08-24
installing depends on what sort of file it is if it's a tar.gz then you usually use

```
tar zvf someprogram.tar.gz
cd someprogram
./configure
make
**sudo make install**
```

the last step in **bold** can be replaced with

```
sudo checkinstall
```

that way the package manager can keep track of the package which makes it easier to uninstall later you may have to install checkinstall using

```
sudo apt-get install checkinstall
```

hope this helps

---

### Post by oldos2er on 2011-08-24
Are you trying to install the Linux version, or the Windows version with Wine? 

Is there some reason you're not using Transmission (Ubuntu's default torrent client)?

---

### Post by lovinglinux on 2011-08-24
> **dave01945 said:**
> installing depends on what sort of file it is if it's a tar.gz then you usually use...

Don't scare the noob :-)

Most of the time, you don't need to look for applications on the web. All you need is to launch Ubuntu Software Center, search what you want and install.

Utorrent for linux is on early development and doesn't have a graphical interface, just a server and a web interface. I don't recommend it for you. If you still want to try it, just extract the tar.gz file somewhere and execute the file utserver. You can fi9nd more info in the docs folder.

If you are looking for a client like utorrent, then I recommend qBittorrent. It is very fast and the interface is based on utorrent. You can find it in the Software Center.

---

### Post by Mauroblack on 2011-08-25
> **oldos2er said:**
> Are you trying to install the Linux version, or the Windows version with Wine? 

Is there some reason you're not using Transmission (Ubuntu's default torrent client)?

Sorry to hijack the thread.

But I find that the default client for Ubuntus "limits" the speed of my torrents.

Ie: with utorrent on windows I can get 990 Kb/s on campus but the same torrent won't get that speed on ubuntu in the same location at the same time with the same computer.
Why is that?

I am a bit above noob-ish but a noob regardless.

---

### Post by mhgsys on 2011-08-25
@Mauroblack

You should check your ports being used... and set the same ports as campus forwards in router.

---

### Post by ikt on 2011-08-25
> **soccerguy18 said:**
> I just can't understand how to install things!
anyways
I am trying to download utorrent client
but i dont know what to type into terminal.
I need to know exactly what to type and when to do that

I am sorry, I am a noob

[http://deluge-torrent.org/](http://deluge-torrent.org/)
[http://qbittorrent.sourceforge.net/](http://qbittorrent.sourceforge.net/)

Are better torrent clients, there are many others in the software centre.

---

### Post by pqwoerituytrueiwoq on 2011-08-25
> **Mauroblack said:**
> Sorry to hijack the thread.

But I find that the default client for Ubuntus "limits" the speed of my torrents.

Ie: with utorrent on windows I can get 990 Kb/s on campus but the same torrent won't get that speed on ubuntu in the same location at the same time with the same computer.
Why is that?

I am a bit above noob-ish but a noob regardless.
i noticed that the other day
check the settings in transmission
edit->preferences 
speed tab

---

