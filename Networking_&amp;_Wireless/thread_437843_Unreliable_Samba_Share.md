---
title: "Unreliable Samba Share"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by Yakyb on 2007-05-09
ok so before i made this post i searched through the forums (went baack 25 pages) to see if i could find an answer although no joy

i recently bought a new comp in the aim of running it as a file server running Feisty after previously running tests using an older box and edgy.

the file server acts on a Windows XP network with 2 XPsp2 machines connected 
xpmachine1 name = BLACKOMP     static ip = 192.168.2.5
xpmachine2 name = SILVCOMP      Static ip = 192.168.2.15
both with username YAKYB and no password

i installed onto a 80GB hdd using comp name SERVER and user YAKYB and password = *******
then permanently mounted two 400GB hdds using ext3 to 
/media/hdd1
/media/hdd2

i then setup a static ip 192.168.2.10 on SERVER to allow easy use of VNC which worked fine.


I then followed this tutorial to setup a simple Samba share [Stormbringer's tutorial]("http://ubuntuforums.org/showthread.php?t=202605")

all was going swimmingly as i shared the DVD drive and two hard drives then mapped them as 
X:\                                    (HDD1)
y:\                                    (HDD2)
Z:\                                    (DVD)

on both SILVCOMP and BLACKOMP

i could access all shares (testing with small files) from every machine and i thought hell that was easy then problems started.

upon trying to Upload about 20Gb of backed up dvds from BLACKOMP to SERVER (first large file transfer) it was going okay 
although only at 8MB/s (both GIGABIT NICS) according to system monitor.
until at about 30%  the connection was lost and mapped drives where disconnected :confused: as well as all internet connection.

i restarted the xp machine and the Mapped drives and internet reconnected automatically so i tried again and the exact same thing happened.:confused: :confused: 

so i changed the SERVER from Static IP to DHCP but this did not help.

my guess is that there is something wrong on the Windows (timeout issue maybe?) side as restarting that box fixes the problem. only for it to reoccur again

i have roughly 500GB worth of stuff i need to upload (photos, videos, music, disk images and documents) and dont really want to have to upload 5 GB at a time

does anyone have anyideas regarding my problem

---

### Post by tl3000 on 2007-05-09
I experienced similar problem with Ubuntu Fiesty Desktop version and Samba.  The networked WinXP PC would be accessible at startup of the Ubuntu PC, and transfers files OK--tested with a file that's ~3GB, nothing as big as your 20GB though.  Anyway, over time, at idle on both machines, the connection to the WinXP PC would become inaccessible--contents cannot be displayed when I try to browse the shared folders.  I could re-establish the connection if I ping the WinXP PC several times from the Ubuntu PC, and contents could be displayed again.  The connection will drop again, after some time at idle--seems like something is timing out.  Pinging seems to wake up and re-establish the connection.  I removed all the power management services on both PCs but no difference.  Again, I'm running Desktop instead of Server so I don't know if this is related and a common bug with Samba and/or Fiesty... you might check to see if you're experiencing  this same behavior.

---

### Post by Yakyb on 2007-05-09
thanks for reply does sound very similar

just to clarify although this will be running as a fileserver im still using the desktop verion (would it be a more stable connection on server version?)

oh and its not one huge 20GB file more like about 50 files making up the 20GB

---

### Post by tl3000 on 2007-05-09
> **Yakyb said:**
> just to clarify although this will be running as a fileserver im still using the desktop verion (would it be a more stable connection on server version?)

Sounds like we have the same network setup then.  I'm not familiar with the Server version of Ubuntu... never tried it.

---

### Post by Martin Macleod on 2007-05-09
Hi there,

I too have been having problems with samba shares.  I have Ubuntu set up as a fileserver and when you stop accessing the files for a while the server becomes disconnected, if I leave a window open  on my Windows box it seems to keep the connection.

You guys get anywhere with it?

I just noticed this problem today, Ill let you kow if I find a solutioin.

Martin

---

### Post by Yakyb on 2007-05-10
did some more testing last night and thought that setting up an ftp server on my windows box would solve the problems of transfering the large amounts of data.  got it setup without a hitch but again after a short time transfering the connection was lost couldnt ascertain which side caused the problem this time 

any help guys

---

### Post by Martin Macleod on 2007-06-19
Been a while since I've had a look at this problem again.  it is still happening to me.  We have a couple of computers accessing the samba fileserver at the same time, as the same user.  Dont know if this is an issue but i might try having separate samba user names.

I have found out if I ping the server from the computer that is having connection problems it will reconnect after the ping has completed.

I am still none the wiser as to why the connection seems to disconnect and "wakes" after a ping!

Madness

Martin

---

