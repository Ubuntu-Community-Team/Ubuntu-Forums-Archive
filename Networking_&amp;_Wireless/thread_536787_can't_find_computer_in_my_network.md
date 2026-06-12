---
title: "can't find computer in my network"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by kornface13 on 2007-08-28
I have been doing ALOT of tinkering with this and that sicne I installed Ubuntu.

Now I'm running into a simple problem that I can't figure out.  I'm very good with networking, so feel free to skip the simple stuff, but I can't share files from one computer to another (both Ubuntu)

Neither computer is running a firewall.  I am x.x.13.213     He is x.x.13.116


I set my share folder called "Programs" to allow the entire 192.160.0.0 255.255.0.0 (Unix share)
He set his share for pretty much the same.

Neither one of us can go to "Places" - "Network" and see each others computers/shares.  Any idea why?  Maybe I removed something I need while tinkering, but then I should still be able to see his shares.  

Let me know if you want more info and I'll be glad to tell ya.

---

### Post by callan79 on 2007-08-28
> **kornface13 said:**
> INeither one of us can go to "Places" - "Network" and see each others computers/shares.  Any idea why?  Maybe I removed something I need while tinkering, but then I should still be able to see his shares.

Hi,

I've posted a few messages - [example](http://ubuntuforums.org/showthread.php?t=526896) - helping out with network sharing, as I've been messing around with it a fair bit here too. Took a bit of getting used to :)

If you're sharing via SAMBA, then instead of browsing PLACES for the other computers, what happens if you go to PLACES >> COMPUTER, and then in the address bar you type smb://192.160.13.x, where this IP is the IP of the other computer. Do the shares show up?

Also, if you're going to be doing a lot of sharing, you're best to mount the shares properly. I found that when I just browse the network and transfer files, it was slow and my CPU usage was pretty high. When I mounted the share properly, the speed increased but the major impact was that my CPU hardly blipped the graph.

Cheers
Callan

---

### Post by kornface13 on 2007-08-28
Cool thanks.  I reinstalled Ubuntu and got it working, but only via Samba.  i figured if I set it as a Unix share then it would pop right up without using Samba.  No big deal either way.  i'm happy that it works.  Thanks.

what exactly do you mean by mount the shares properly??

something along the lines of mount smb://192.168.x.x/folder_name ???

---

### Post by callan79 on 2007-08-29
> **kornface13 said:**
> what exactly do you mean by mount the shares properly?? something along the lines of mount smb://192.168.x.x/folder_name ???

Yes, to MOUNT the shares in Ubuntu is the equivalent of MAP NETWORK DRIVE in WIndows. This means that instead of you having to browse the network for shares, the share will just appear on your PLACES menu.

This is what you need to do :

```

cd /media
sudo mkdir elephant
sudo mount -t smbfs //192.168.x.x/share_name /media/elephant -o uid=AAAA,gid=BBBB,defaults,username=CCCC,password=DDDD,dmask=0777,fmask=0777

```

In the above :
AAAA = the ubuntu username on the current machine
BBBB = the ubuntu groupname on the current machine (probably the same as the username)
CCCC = the ubuntu username on the machine which has the share
DDDD = the ubuntu password on the machine which has the share


Once this is done, if you don't get any errors then you should see an item called 'elephant' on your places menu.

If you want this to be a permanent share, then you can add it to your ftstab file so it auto-mounts on boot.

Cheers,
Callan

---

### Post by mgriggs13 on 2008-02-08
I tried to do the above mounting given by callan but it wouldn't work. I got the error "mount: wrong fs type, bad option, bad superblock on..."

I am somewhat new to ubuntu and so for all the other newbies out there, make sure you install the smbfs (samba filesystem)

```
sudo apt-get install smbfs
```

---

