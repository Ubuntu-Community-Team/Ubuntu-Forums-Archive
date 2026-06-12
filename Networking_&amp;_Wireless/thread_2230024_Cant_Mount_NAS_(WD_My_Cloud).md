---
title: "Cant Mount NAS (WD My Cloud)"
date: 2014-06-16
forum: Networking &amp; Wireless
---

### Post by tony49 on 2014-06-16
so this is my first time trying a linux OS and so far really enjoying it. That is, besides one issue i have been having. so i installed ubuntu 12.04 on my Dell Chromebook and tried connecting/mounting my NAS to have access to the contents but failed. i then installed a fresh version of ubuntu 13.10 thinking maybe the older version just had some issues.. again i failed mounting. i have tried several ways:

first i followed these instructions [http://cocoaallocinit.com/2014/01/04/wd-my-cloud-nas-on-ubuntu/](http://cocoaallocinit.com/2014/01/04/wd-my-cloud-nas-on-ubuntu/)

but i get "no such device" on the final command line (i know the IP address of the drive)

then i tried a few ideas from this forum including:
[COLOR=#000000]- Create a mount point in /media[/COLOR]
[COLOR=#000000]e.g. [/COLOR]
[COLOR=#000000]Code:
sudo mkdir /media/mybooklive[/COLOR]
[COLOR=#000000]- then mount it as a 'CIFS' mount[/COLOR]
[COLOR=#000000]i.e. [/COLOR]
[COLOR=#000000]Code:
sudo mount -t cifs -o username=,rw,users,uid=1000 //mybookipaddress/Public /media/mybooklive[/COLOR]
[COLOR=#000000](uid is your Ubuntu uid - usually 1000)[/COLOR]
[COLOR=#000000](mybookipaddress is the ip address of the MYBOOK device)[/COLOR]
[COLOR=#000000](You may need to install the 'cifs-utils' package first).

Still no luck as i get error: 
cifs file system not supported by the system
no such device

i tried Samba and [/COLOR][COLOR=#000000]pyNeighborhood to connect directly but still no luck.
[/COLOR][COLOR=#000000]
what am i missing here?

[/COLOR]also, not sure if this is related or not but when i open up file manager and go to networks>browse networks i see windows network but can get access. error msg is "no such file or directory" 

so yeah, im at a loss. maybe someone here can guide a newb

Thanks

---

### Post by Toz on 2014-06-16
Hello and welcome to the forums.

> **tony49 said:**
> Still no luck as i get error: 
cifs file system not supported by the system
no such device
Make sure that you have the **cifs-utils** package installed. Search for it in the Software Centre or from a terminal window:
```
sudo apt-get install cifs-utils
```

---

### Post by tony49 on 2014-06-16
thanks for the response but i already have the newest version installed.

i know im missing something though..

---

### Post by Toz on 2014-06-17
Can we confirm its status?
```
apt-cache policy cifs-utils
```

Have you rebooted recently? Perhaps after a recent kernel upgrade?

What does the following return? Any messages?
```
sudo modprobe cifs
```

---

### Post by tony49 on 2014-06-17
> **Toz said:**
> Can we confirm its status?
```
apt-cache policy cifs-utils
```
[I]cifs-utils:
  Installed: 2:6.0-1ubuntu2
  Candidate: 2:6.0-1ubuntu2
  Version table:
 *** 2:6.0-1ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages
        100 /var/lib/dpkg/status[/I]



Have you rebooted recently? Perhaps after a recent kernel upgrade?* i have rebooted, not sure about the kernel upgrade.*

What does the following return? Any messages? *hmm maybe this is the issue?*
```
sudo modprobe cifs
```
*FATAL: Module cifs not found.*


thanks for following up

---

### Post by Toz on 2014-06-17
Have you rebooted?

What does the following return:
```
uname -a
```

---

### Post by tony49 on 2014-06-17
Linux localhost 3.8.11 #1 SMP Mon Jun 9 02:39:27 PDT 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Toz on 2014-06-17
Have you rebooted?

---

### Post by tony49 on 2014-06-17
yes a few times since attempting.

---

### Post by steeldriver on 2014-06-17
"[COLOR=#000000]cifs file system not supported by the system" sounds strange for a Linux error message - I wonder if that's coming from the remote system and indicates some kind of protocol mismatch?[/COLOR] Have you tried adding a **sec=** parameter to your mount options? I don't know too much about cifs but I'd guess if you really are supplying an empty username ('username=,...') the appropriate mode would be 'none? e.g.

```

[COLOR=#000000] sudo mount -t cifs -o **sec=none,**username=,rw,users,uid=1000 //mybookipaddress/Public /media/mybooklive[/COLOR]

```

If still no luck you could try **sec=ntlm**

---

### Post by tony49 on 2014-06-17
so i just found that i can connect to the hard drive doing the following

Type in the addresslocator: afp://ip address NAS
 
but once i am in and try to access a folder a prompt opens that says "open File System and other files of types 'unkown' with:"

i select file manager and that folder is then mounted..but

when i try to access the files some open and others dont. 

text files and images files open but music and video wont. (im trying to open those with VLC)

also, the sub folders have X's on them..

any ideas? and is this a valid way of mounting?


EDIT:
i go the files to open.

VLC needs credential to access the files on the drive. through the VLC preferences you can set up smb credentials. so i just changed the address to smb://<IPADDRESSOFDRIVE> and was able to open them.

now the question is, is this a "good" way of doing what i needed? what will be the experience of my connection?

---

### Post by Morbius1 on 2014-06-18
> VLC needs credential to access the files on the drive. through the VLC  preferences you can set up smb credentials. so i just changed the  address to smb://<IPADDRESSOFDRIVE> and was able to open them.

now the question is, is this a "good" way of doing what i needed? what will be the experience of my connection?                 
It works, right?

"smb://..." doesn't rely on cifs to do it's magic so the problem was avoided. By the way since it recognizes an "afp"://..." it must be OSX compatible so you should be able yo use a host name ( mDNS limited ) instead of an ip address. Something like this: "smb://wdmycloud.local"

Anywho, the original cifs problem sounds an awfull lot like this : [https://answers.launchpad.net/ubuntu/+source/cifs-utils/+question/192701](https://answers.launchpad.net/ubuntu/+source/cifs-utils/+question/192701)

---

### Post by Toz on 2014-06-18
> **Morbius1 said:**
> Anywho, the original cifs problem sounds an awfull lot like this : [https://answers.launchpad.net/ubuntu/+source/cifs-utils/+question/192701](https://answers.launchpad.net/ubuntu/+source/cifs-utils/+question/192701)
+1. 
I was wondering if the OP's system was in a state where a reboot was required after a kernel update.

@OP, is your system fully updated? Can you run:
```
sudo apt-get update && sudo apt-get upgrade
```
...error-free?

---

### Post by tony49 on 2014-06-19
just ran the line error free.

so far been working this way. vlc i inputted my credential to access video. rhythmbox connects through DAAP for all my audio.

not sure why those other routes didnt work..

---

### Post by tony49 on 2014-07-13
[COLOR=#000000][INDENT]the issue was crouton. as its not a full version of ubuntu i guess mounting the drive in such a way to allow full capabilities is impossible. i solved this by factory resetting the chromebook and install chrubuntu. my NAS was visible and accessible under Network which was not possible before. i then could choose it as a local drive in my torrent save location. thanks for the help guys![/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by kdavies on 2014-11-27
Hi

I have a 4TB NAS WDMyCloud
showmounts -e wdmycloud
Displayed /nfs*

I created a share Shared and there is a Public share already.
I could mount the shares using nfs in the usual manner.
As root creading a directory /mnt/wdmc.Public
mount -t nfs wdmycloud:/nfs/Public /mnt/wdmc.Public

And to make that permanent edit the /etc/fstab with
wdmycloud:/nfs/Public	/mnt/wdmc.Public	nfs	 _netdev,auto 0 0
and issue mount -a

An issue I still have is with my personal directory, to gain access on the NAS, I have had to resort to making that 'public' via the web interface.

I would much prefer to keep that priviate with r/w permissions for me.

Hey ho.
Makes me laugh when you log in via ssh as root, on to a debian box wd-2.2-rel armv7l.
editing the /etc/ssh/sshd_config and commenting out AllowUsers root means I can ssh into the NAS as normal user.

---

### Post by kdavies on 2014-11-27
Some more digging around and examining the exports file and hey presto, can now nfs to my directory on the NAS.

NAS export file was and copied it to export.nas (just in case)
/nfs *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)

So removed the asterisk, specified all the directories, added no_root_squash and it all worked.
/nfs/Public (rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)

And for my private directories
/nfs/username (rw,no_root_squash,sync,no_subtree_check,insecure,crossmnt)

yeah

---

