---
title: "Beginner, MiniDLNA"
date: 2017-11-05
forum: Networking &amp; Wireless
---

### Post by Jarubell on 2017-11-05
New to this but I'm trying to get my son's Xbox One to play videos from my computer with Ubuntu 14.04.5 LTS. I've installed MiniDLNA, had troubles but I now can see my computer on the Xbox, however, I'm unable to see any files. Most of my troubles was with all my files are being a second internal drive and, I just changed user to root.

Not sure where to go from here?

Any help would be appreciated.

---

### Post by SeijiSensei on 2017-11-05
Just to make sure, you have one or more media_dir entries in /etc/minidlna.conf that point to the directories holding the files you wish to share like this:

```
media_dir=A,/path/to/my/music
media_dir=V,/path/to/my/videos

```

If so, first make sure the server is stopped with 

```
sudo service minidlna stop
```

Now force a reindexing of your files with 

```
sudo minidlnad -d -R
```

You should see entries fly by in the terminal window as the indexing takes place. When the indexing is finished, hit Ctrl-C to stop the program.  Now restart the server normally with 

```
sudo service minidlna start
```

Can you browse the entries now?  On my DLNA clients, the server appears as servername:minidlna.

One other important tip.  MiniDLNA keeps a log in /var/log/minidlna.log if the log_dir and log_level directives in /etc/minidlna.conf are set.  I have

```

log_dir=/var/log
log_level=general=info,artwork,database,inotify,scanner,metadata,http,ssdp,tivo=error

```

---

### Post by Jarubell on 2017-11-06
I tried ```
sudo minidlnad -d -R
``` But it returned 'command not found'

Here's what I have in minidlna.config
```

user=root
media_dir=V,/media/2GB/2GB_Videos
media_dir=V,/home/folder/Downloads
friendly_name="Ubuntu"
inotify=yes

```

Prior to trying SeijiSensei's help, after changing the config file I used
```
 
sudo service minmidlna restart 

```
Followed by
```

sudo service minidlna force-reload

```

I have never seen entries fly by in the terminal window.

SeijiSensei, I'm going to look into your last important tip as well as I have no clue, yet.

---

### Post by SeijiSensei on 2017-11-06
> **Jarubell said:**
> I tried ```
sudo minidlnad -d -R
``` But it returned 'command not found'

I don't know why that would be, since minidlnad is stored in /usr/bin on my 14.04 system, and everyone should have a path to that directory.  Try running
```
sudo /usr/bin/minidlnad -d -R
```
instead.  Any better?

You did install minidlna from the Ubuntu repositories, right?

---

### Post by Jarubell on 2017-11-06
I looked at it again, I misspelled, forgot the second 'd' in minidlnad. So it tried to run but crashed with SIGSEGV in strlen(). I hope that makes sense, I'll have to look up what SIGSEGV is or means.

As for installing minidlna from Ubuntu repositories, I don't know, I just used 
```
sudo apt-get install minidlna
```

I just noticed that the instructions have a banner across the to indicating the process needs updates due to newer versions of Ubuntu, sigh.

Is the a better app for DLNA?

---

### Post by SeijiSensei on 2017-11-07
The version in the repositories runs without error on my 14.04 installation. I've never seen the error you report.  Perhaps you should try
```

sudo cp /etc/minidlna.conf /etc/minidlna.conf.old
sudo apt-get remove --purge minidlna
sudo apt-get update
sudo apt-get install minidlna
sudo mv /etc/minidlna.conf /etc/minidlna.conf.dist
sudo mv /etc/minidlna.conf.old /etc/minidlna.conf

```
and start over with a new copy.  

I know other programs like Kodi support DLNA, but that's a much bigger installation than just minidlna.

A quick Google search shows that the bug you encountered was supposedly fixed a couple of years ago: [https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/1363069](https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/1363069)

---

