---
title: "need help with ubuntu and i've researched for hours"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by bniyx7 on 2009-12-24
hey guys... im at my wicks end with this ubuntu.... 

I think its a great OS and would prefer to use it over windows but its soooo taxing to understand.  

I try to connect with SSH from a windows client and it wont and says connection refused and everyone is giving all of these complex commands in the forums and I still have yet to understand anything that they are talking about.  

My internet runs slow and I attempted to do the IPv6 disable and in that aliases file ( i did the sudo gedit /etc/modprobe.d/aliases and not one letter is in that file...) but i am finding everywhere that the file contains information (lots). 

As far as a server.. im trying to host teamspeak and I cant get the IP's to work correctly (im getting 0.0.0.0 stuff) and it wants a license key and I cant find anywhere on the web where to get this key.  

I honestly have many more problems and I finally got TELNET to work and I have spent honestly hours upon hours trying to make it work and it will not.  I can connect to server within my network but not outside.  The Serverini file doesnt exist.

It seems like all these tips are great people are giving... but for some reason my computer with ubuntu contains NO information in what they are talking about.  Ideas...???


AND YES.  i have looked on youtube and have followed example videos of exactly what to do and they do not work.  i have ubuntu 9.10 installed...

---

### Post by taurus on 2009-12-24
You forgot to mention the most important question.  Is your machine connected to a router?

If you want to allow people to ssh to your machine, you need to install the ssh server, openssh-server, on your machine first.

---

### Post by bniyx7 on 2009-12-24
oh ya im connected to a router.. im pretty darn sure i installed all that but to be honest i cant even remember my brain is fried.  I will attempt that and let you know.. after i install the sshserver and the other one you said.. the ssh should just connect?

---

### Post by taurus on 2009-12-24
Actually, you still need to go into your router and open port 22 for ssh.  Make sure you rout that to the machine that you want to connect to.  Depending on which router you have, ssh (port 22) should be on the list so you just need to add that to the active list or whatever your router calls it.

---

### Post by bniyx7 on 2009-12-24
Ok.  Also any idea with this aliasas file?  and why there is nothing in there??? 

and anything else u can help explain about this.. lol.

---

### Post by taurus on 2009-12-24
I don't even have it, /etc/modprobe.d/_aliases_, on my machine.

---

### Post by bniyx7 on 2009-12-24
> **taurus said:**
> I don't even have it, /etc/modprobe.d/_aliases_, on my machine.

Well as usual this does not make sense...  i did the following.

sudo apt-get install openssh-server  THEN

sudo /etc/init.d/ssh restart   - it finally told me that the restart command was not found.  so i have no clue.  i use putty and it will connect with ssh (i think) but i cant find a file transfer program that will connect.  i use cuteftp and i think it should work anyway.. but its not.

---

### Post by taurus on 2009-12-24
When you install it, it should automatically start.  See if it shows up on this list.

```
ps -A
```

---

### Post by Some Penguin on 2009-12-24
> **bniyx7 said:**
> Well as usual this does not make sense...  i did the following.

sudo apt-get install openssh-server  THEN

sudo /etc/init.d/ssh restart   - it finally told me that the restart command was not found.  so i have no clue.  i use putty and it will connect with ssh (i think) but i cant find a file transfer program that will connect.  i use cuteftp and i think it should work anyway.. but its not.

1) sshd restart, most likely.  (d) for daemon
2) Get 'pscp' from the same place you got putty.
3) ftp != ssh, so don't expect an ftp client to talk to an ssh server or vice versa.

---

### Post by mikewhatever on 2009-12-24
Apparently, /etc/modprobe.d/aliases does not exist in Karmic, which, for the lack of info, I assume you are using. However, you can still disable ipv6 using **Method 3** of the guide below.
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by bniyx7 on 2009-12-25
> **mikewhatever said:**
> Apparently, /etc/modprobe.d/aliases does not exist in Karmic, which, for the lack of info, I assume you are using. However, you can still disable ipv6 using Method 5 of the guide below.
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

ok I will try those things... What do you suggest for a SSH client?  and you even have to break it down for me a little more because some commands that you gave me above still dont make any sense.  I get the jist but whenever i do them its a "command unknown" error so i get frusterated.

---

### Post by Shazaam on 2009-12-25
--I get the jist but whenever i do them its a "command unknown" error so i get frusterated.--

"command not found" (or unknown) usually means that you need to add sudo in front of the command to install/check/configure/run an app/service as root. Take this disk check command for instance...
```
fdisk -lu
```
returns nothing, but..
```
sudo fdisk -lu
```
would get you something similar to this...
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000096f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312576704   156288321    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00047d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   419665994   209832966    5  Extended
/dev/sdb5             126     4369679     2184777   82  Linux swap / Solaris
/dev/sdb6         4369743   214194644   104912451   83  Linux
/dev/sdb7       214194708   419665994   102735643+  83  Linux

```
Another reason you may get that error is that what you are trying to run is either not installed or is partially installed (not configured, missing/incorrect dependancies, broken, etc).
Does that help?

---

### Post by mikewhatever on 2009-12-25
> **bniyx7 said:**
> ok I will try those things... What do you suggest for a SSH client?  and you even have to break it down for me a little more because some commands that you gave me above still dont make any sense.  I get the jist but whenever i do them its a "command unknown" error so i get frusterated.

Right, so that was Method 3 and not 5, sorry for the typo.
The commands are pretty straight forward, but if you run into problems, do past the output here.

---

### Post by sandyd on 2009-12-25
> **bniyx7 said:**
> ok I will try those things... What do you suggest for a SSH client?  and you even have to break it down for me a little more because some commands that you gave me above still dont make any sense.  I get the jist but whenever i do them its a "command unknown" error so i get frusterated.
ssh client -> putty.

---

### Post by bniyx7 on 2009-12-26
to mikewhatever:

I went to use method 3 (gksudo gedit  /etc/default/grub) and like everything else it seems like.. there is no information in this file that shows up so there is no way to diable anything.  Any other ideas?

---

### Post by mikewhatever on 2009-12-26
Are you really running Karmic? Can you post the outputs of the following commands:

cat /etc/lsb-release

cat /etc/default/grub

Don't just tell us you got this or that error, but post the actual output.

---

