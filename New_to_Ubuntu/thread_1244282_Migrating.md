---
title: "Migrating"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by BobJam on 2009-08-19
Will be getting my new machine this week.

Have Ubuntu on my current machine . . . and currently have it configured the way I want it.

Am looking for a way to migrate what I have (exactly as configured) over to my new machine.  Am sure there's a way.

New machine will come with 8.10 preinstalled . . . a Dell Inspiron 15, 4GB RAM, 250GB HDD (laptop).  I have no idea how it will be partitioned, but I assume it will just be one big 250GB partition, with maybe a small Dell recovery partition, and the usual Dell crapware.

I have two 4GB USB sticks (I don't have an external HDD), one with completely free space, the other almost.  If I can fit a backup on one of them (and as I'm sure many experienced users here know, there are any number of Ubuntu utilities for that, from "Clonezilla" to rsync to "P.I.N.G" - "Partimage Is Not Ghost" - to "MondoRescue" and on and on), then I can use that as the transfer vehicle.

I'd like at least to have my OS duplicated, with all of the settings.  If the image will also include all the apps I have installed (I have one Ubuntu partition, not a separate for the home directory, so I assume all the apps would be on this partition image as well), that will be an extra bonus.

I know with Windows, simply making copies doesn't make the apps bootable . . . they have to be installed and seated in the registry.  Commercial imaging software FOR WINDOWS like Acronis True Image and Norton Ghost will do that.

I have my Firefox profile and Thunderbird emails exported to a USB stick, so that part shouldn't be a problem if I have to restore them separately.

As I understand it though, Ubuntu is a little bit different from Windows in that a backup of the OS is bootable (if made with one of the above mentioned titles).

And there's always networking, but I've never set anything like that up between two Ubuntu machines.  Of course, I've not used any of those backup titles either.

I remember in the old days doing a migration via IR, but I think that technology has long since gone by the way side . . . besides, neither of my machines (old and new) are equipped with IR (if machines even are anymore).

Then too, can I upload a backup to my website host and then recover it on the new machine?

I'm looking for the most painless way to do this.

---

### Post by mapes12 on 2009-08-19
I have an uncompressed partimage of 8.04 which is 3GB in size. I can get it down to 1.3GB using compression but compression and my restores sometimes don't agree with eachg other. But I've never used USB sticks to back up to or restore from. The backup just mentioned is just of the Filesystem i.e. "/". So if you have /home on the same partition as "/" then you might stuggle for space. Ahead of the migration you could always move /home to a partition of its own which would make the task easier: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

> As I understand it though, Ubuntu is a little bit different from Windows in that a backup of the OS is bootable (if made with one of the above mentioned titles).I have never had a problem using partimage in booting from reinstalled images.

> And there's always networking, but I've never set anything like that up between two Ubuntu machines. Of course, I've not used any of those backup titles either.This could be an easy solution using SSH for moving your home stuf once you have your filesystem into the new machine the way you want it. Post back if you want my HowTo for using SSH across 2 UBU boxes.

> Then too, can I upload a backup to my website host and then recover it on the new machine?You can move your backup wherever you have permission and space. If you have enough web storage this would solve your USB limitations. And you have an ISP account to cover the bandwidth back and forth. You would probably have to download the backup image using a Live UBU CD, save it to the HDD on your new machine then boot from the partimage rescue cd to get your filesystem up and running.

> I'd like at least to have my OS duplicated, with all of the settings. If the image will also include all the apps I have installed (I have one Ubuntu partition, not a separate for the home directory, so I assume all the apps would be on this partition image as well), that will be an extra bonus.All you apps will be in "/". So concentrate on that if you can first. /home has all your personal settings. Linux doesn't jumble things up like windoze.

---

### Post by BobJam on 2009-08-19
> **mapes12 said:**
> Post back if you want my HowTo for using SSH across 2 UBU boxes.Yes.  Do you have a link to it?

> **mapes12 said:**
> This could be an easy solution using SSH for moving your home stuf once you have your filesystem into the new machine the way you want it.Huh?  What is "SSH"?

And what do you mean "moving your home stuf once you have your filesystem into the new machine"?  By "filesystem" do you mean the root?

Sorry if these questions seem bone headed . . . I'm a noob and not familiar with all the lingo yet.

---

### Post by tarps87 on 2009-08-19
My usual technique is dd the original drive to the new drive and then repartitioning, this evolves both hard drives being in the same drive. This isn't a problem for me as I build my own pc so the is now warranty to worry about.
If you want to have some fun you can try using dd over a ssh connection, I have never tried this but I will when I get some time.
[B][SIZE="5"]
Please note this comes with the standard lack of guarantees and may destroy all your data. I will post back once I have tried it. It is more of a concept that a solution. Again please don not try until it has been tested on a disposable machine[/SIZE][/B]

The concept is, first set up a ssh server on the old install.
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html)
Basicaly
```
sudo apt-get install openssh-client openssh-server
sudo /etc/init.d/ssh restart
ssh 127.0.0.1
```
Now enter a password

On the new machine boot using a live cd
```
sudo apt-get install openssh-client
```
Test using
```
shh *ipadd_of_old_pc*
```

If this works you can now use dd (note: the new hard drive must be equal or larger in size than the old one)

```

sudo su
ssh -c blowfish *old_pc_username*@*ipadd_of_old_pc* "sudo dd if=/dev/sda bs=1k conv=sync,noerror" | dd of=/dev/sda1 bs=1k
```

---

### Post by mapes12 on 2009-08-19
> And what do you mean "moving your home stuf once you have your filesystem into the new machine"? By "filesystem" do you mean the root?
Sorry! Filesystem and "/" are the same thing to me (others will disagree) but yeh the one and the same thing.

SSH stands for secure shell and it's a very easy way to connect 2 Linix boxes and transfer files back and forth. I'll copy and paste the Howto in a minute.

Coming back to "/" and /home, they hold separate data. I think of "/" as the Windoze directory on an MS machine that has all the OS files in it (but"/" also has the applications). /home I think of as My Documents on MS. Now, if you ever want to upgrade your system the easiest way to do it is just install the new version of "/" and leave /home alone (excuse pun). So, if you can get them onto separate partitions to start with then all you need to do is reinstall a Partimage of "/" and once that is done you can hook up the 2 machine and transfer the content of /home/username via SSH and not worry about how much space you have on those USB sticks. N.B. make sure you copy across /home/*username* otherwise I have experienced strange results when copying across just /home. One final thing regarding /home/username. There is a hidden file in it called .gvfs - make sure you don't copy that over because again I've had weird results with that file. It will be recreated for you in your new install anyway.

Given that you have a laptop you may find using dd difficult. It' fine if you have a desktop where the old and new HDD's can be installed together. I would mention that it works extremely well in a desktop configuartion but I've never used it with a laptop. 

Coming back to the task in hand this is how I would approach it:

1. Boot the new LT with a GParted Live CD and have a look at how Dell have setup the partitons. If I didn't like what I saw I would delete. Then creat a partiton for "/", one for /home and one for Swap. This link will give you the idea. Forget the windoze stuff and go down the page to the Linux stuff. It's not part of the main site but still an excellent guide to partitions: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

2. Install 9.04 from the Ubu live CD. At the partitioning section select "Manual". You will see you partitons. For each one tell it what you want it to be from the list when you select each of them i.e. "/" /home and swap.

3. Once the install has completed copy across your partimage into /home

4. Reboot with the Systemrescue CD and have the partimage installed onto the partition where "/" root has just been installed (yes I know it will wipe it but it's the easiest way I know).

5. Reboot then set up SSH between the 2 machines.

6. Copy across the stuff from /home/username form old machine to /home/username on the new machine noting my comment about the dreaded .gvfs file.

All should then be setup how you want it. 

Now, you might be thinking why install a 9.04 base onto a bare, patitioned HDD? I would do this because by going through the installation the new /home and swap would be setup.

Next post will be my SSH HowTo.

---

### Post by mapes12 on 2009-08-19
Here you go. I have simply cut and paste this from another post I made to help someone out:

I guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved. I only state this because the solution that i am thinking of writing down here will NOT WORK to access windows machines.

I also do not know if there is a simpler way - this is the simplest way I know.

1.) Make sure the openssh-server is installed on both machines. You can check in Places>Connect to Server and make sure SSH is an option in the service type drop down box. If it isn't installed then type this command in both computers Terminal and let them run through.

```
sudo apt-get install openssh-server
```

2.) Find out the IP addresses of your computer. Use the following command to obtain your computers IP address

```
ifconfig
```

this should give you an output just like this one

> eth0 Link encap:Ethernet HWaddr 00:50:da:e0:67:74
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:9 Base address:0xc000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1732 (1.7 KB) TX bytes:1732 (1.7 KB)

wlan0 Link encap:Ethernet HWaddr 00:11:50:dd:a9:16
inet addr:**192.168.1.68** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:50ff:fedd:a916/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1661090 (1.6 MB) TX bytes:342426 (342.4 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-11-50-DD-A9-16-39-31-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter.

So, in my case the address would be 192.168.1.68

3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server.
- Choose SSH as the at the service type
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click OK
You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.

---

### Post by Bucky Ball on 2009-08-19
[Partimage]("http://www.psychocats.net/ubuntu/partimage") sounds perfect if you are backing up your personal data anyway. Just backup up the relevent partitions then dump 'em on again. There is one thing. Might your config be looking for all the wrong hardware if you dump it into a new machine??? (xorg.conf for instance?).



Also, in Jaunty there is software to make a bootable USB stick.

---

### Post by mrbiggbrain on 2009-08-19
ok maybe im the only one...

If its a desktop...

1) install the old PC's HDD into the new pc.
2) Boot up the Gparted Live cd
3) Delete the partitions on the new pc.
4) Select the old PC, and select to copy the old partiton.
5) Select the new pc, and select to paste the old partition onto the new one.
6) Resize the Partition to the correct size.

Note, that this only works when going from smaller, to larger drives. youll have to resize the partition on the old pc if it has a bigger HDD.

---

### Post by mapes12 on 2009-08-19
> **mrbiggbrain said:**
> ok maybe im the only one...

If its a desktop...

1) install the old PC's HDD into the new pc.
2) Boot up the Gparted Live cd
3) Delete the partitions on the new pc.
4) Select the old PC, and select to copy the old partiton.
5) Select the new pc, and select to paste the old partition onto the new one.
6) Resize the Partition to the correct size.

Note, that this only works when going from smaller, to larger drives. youll have to resize the partition on the old pc if it has a bigger HDD.OP states it's a laptop. If it were a desktop then screw driver out, move old HDD into new desktop and then ```
dd if=/dev/sda of=/dev/sdb
```would do the job painlessly

---

### Post by tarps87 on 2009-08-19
Quick update, I have done some testing and it appears to be a success. I am leaving work now so will test it properly when I get home and then post a guide here.

**@BobJam** Do you have a way of connect the two pc's together? i.e. network cable or wireless network.

---

### Post by mapes12 on 2009-08-19
> **tarps87 said:**
> Quick update, I have done some testing and it appears to be a success. I am leaving work now so will test it properly when I get home and then post a guide here.

**@BobJam** Do you have a way of connect the two pc's together? i.e. network cable or wireless network.
Hi tarps87

This looks very interesting. Looking forward to learning more about your testing.

Best wishes.

Mark

---

### Post by tarps87 on 2009-08-19
Success

**@BobJam**

Sorry for the confusing first post, I was thinking out loud.
If you want to make a direct copy/migration you can use the following method.

**Assumptions.**
1) You have a network cable
2) You have ports to plug the table into
3) You have the original install (with connection to the internet)
4) You have a live cd
5) Both machines only have one hard drive/ it is the first hard drive you want to copy

Note: This may take a long time hours - days, depending on the data and network

**Although I have tested this and it works I can take no responsibility for data loss either user or program related. If there is anything you do not understand or are not sure about please ask before trying it**

**On the original computer**
```
sudo apt-get install openssh-server
```
Connect with cable
```

sudo ifconfig 192.168.123.1
ssh 127.0.0.1
```
enter a password

**On the new computer (live cd)**
```
sudo ifconfig 192.168.123.2
ssh *old_pc_username*@192.168.123.1
```
If this connects it is all set up, now:
```
exit
sudo su
ssh -c blowfish *old_pc_username*@192.168.123.1 "sudo dd if=/dev/sda bs=1k conv=sync,noerror" | dd of=/dev/sda1 bs=1k

```
It will ask you for your ssh password and then the sudo password of the original machine, this will be displayed on the screen but as you are on a closed network and as long as no ones looking over you shoulder it is secure.

Let it run until completion, to will list the byte read in and bytes written out.

Now all that there is left to do is resize the partitions using the live cd (this is if the hard drive is bigger)

**Notes:**
**ssh** is a network protocol that allows data to be exchanged using a secure channel between two networked devices.

**blowfish** is the encryption used, this is reported to work faster than other encryption type (including the default)

**ifconfig** is used to manage wire interfaces

**eth0** is the network interface being used

**dd** is a common Unix program whose primary purpose is the low-level copying and conversion of raw data.

**/dev/sda** is the first hard drive

---

### Post by mapes12 on 2009-08-20
> Although I have tested this and it worksHi tarps 87

Did you have to setup partitions on the machine being copied to or was the drive just bare? I'm thinking about how Dell may have setup the partitions on Bobjam's new laptop.

Best

Mark

---

### Post by tarps87 on 2009-08-20
> **mapes12 said:**
> Hi tarps 87

Did you have to setup partitions on the machine being copied to or was the drive just bare? I'm thinking about how Dell may have setup the partitions on Bobjam's new laptop.

Best

Mark

The drive I used was blank but as it is a low level copy of the entire drive it should not be effected by the partitions on the new drive. It will effectively remove them

---

### Post by mapes12 on 2009-08-20
```
ssh -c blowfish old_pc_username@192.168.123.1 "sudo dd if=/dev/sda bs=1k conv=sync,noerror" | dd of=/dev/sda1 bs=1k
```Got this far then it asks for the *old_pc_username* password. So I enter my sudo password but I get "permission denied" :confused:

---

### Post by tarps87 on 2009-08-21
The first password is the ssh password, then it will ask you for the sudo password. Is this the order you have entered them in? (This would be easier with a root account :))

---

### Post by DaddyHoggy on 2009-11-14
Apologies for jumping in to this slightly old thread, but it's the only one from my choice of search words that pulled up some of what I wanted to know.  Although I've been using Ubuntu for a while (since Fiesty) I've never done much with it, so apologies if these appear to be Newbie questions.

Basics:

1x 80GB HD with 40GB Gutsy Gibbon partition with two user accounts (my own and my wife's) + 40GB XP partition

1x 'spare' 80GB HD

2x 'spare' 40GB HDs

Plan:

To upgrade from Gutsy Gibbon to Karmic Koala and give it an 80GB HD of its own (and to give my XP partition an 80GB HD of its own)

To do this I plan on using a copy of Acronis True image to back-up two 40GB images on to 2 40GB HDs

Install Karmic on the 'spare' 80GB HD and then copy back what I want off the original 40GB Gutsy partition (now copied to a separate 40GB HD so I can expand my original XP into the full 80GB of original 80GB disk (the back up of XP on to other 40GB HD is just in case it all goes wrong!).

However, this is where I'm on dodgy ground and would like some help:

/home - if I simply copy the /home dir from the Gutsy disk to the new Karmic disk is that enough to restore all my local files and settings (it will be used in the same machine so settings should be OK (shouldn't they?!) i.e. all my docs, music, photos videos, emails (I use Evolution) and Firefox settings (and those of my wife).  If this is a 'yes' then that's good and half the battle!  If 'no' or 'sort of' what do I need to do?  The second part of my query is that I've installed quite a few apps (as has my wife) - games, OpenOffice, VLC, GIMP and loads of stuff I can't even recall at the moment!  So my secondary question is: Where do they live - and can they be easily moved without being reinstalled? (I don't mind upgrading once they've moved - some stuff (such as VLC) won't upgrade under Gutsy (but that's a different noob question for another day).

Any help very much appreciated - because if I break this - my better half with throttle me! ;)

---

### Post by BobJam on 2009-11-14
I never did end up using a migration routine . . . primarily because I thought I would have first had to network the machines, and that was wayyyy beyond my skill level at the time and I would had to have read up and tried that routine first.  Consequently, I thought that the time it would take to install everything on my new laptop would have been less than the time it would have taken to both network and then migrate.

As it turns out I think I could have done it with a "tar" file on a USB stick.  Not sure about this, because I never tried it.

> **DaddyHoggy said:**
> However, this is where I'm on dodgy ground and would like some help:

/home - if I simply copy the /home dir from the Gutsy disk to the new Karmic disk is that enough to restore all my local files and settingsI think so, but I'm not sure if you would run into any compatibility problems with the Karmic distro.  My suspicion is that you wouldn't because your /home directory files pertain only to your settings and not the kernel . . . but I'm not sure on this.  Perhaps someone more experienced will correct me.

> **DaddyHoggy said:**
> (it will be used in the same machine so settings should be OK (shouldn't they?!) i.e. all my docs, music, photos videos, emails (I use Evolution) and Firefox settings (and those of my wife).  If this is a 'yes' then that's good and half the battle!  If 'no' or 'sort of' what do I need to do?I guess this is a "sort of" (see above), but I have no idea what, or even if anything, you would need to do.

> **DaddyHoggy said:**
> The second part of my query is that I've installed quite a few apps (as has my wife) - games, OpenOffice, VLC, GIMP and loads of stuff I can't even recall at the moment!  So my secondary question is: Where do they live - and can they be easily moved without being reinstalled?As far as I understand it, your apps themselves (not the settings) live in the / directory.

So here's the "USB stick" part.  I agonized over many methods for backing up, including Partimage, Clonezilla, Mondorescue, Grsync, SBackup, FSArchiver . . . etc. (the number of these things makes the head spin), and they were either totally confusing and/or just flat out didn't work. Some of that may be my own shortcoming, so I can't really say that they don't work. But they didn't for me.

(For details on this see [this]("http://ubuntuforums.org/showthread.php?t=1288080") thread.)

I finally settled on the tar method in [this]("http://ubuntuforums.org/showthread.php?t=35087") thread.  (Granted, that's an old thread, and maybe it's been superceded by things better, but as I said above all of that stuff didn't work for me).

So, here's what I would propose.  Use that tar method to make backups of both your / and /home directories (which it does with the command line shown in that thread).  Copy the tar file to a USB stick (my tar file for these backups has grown to 8+ GB, so you'll want to have a USB stick big enough to fit the size of your tar file).

Then with that USB stick you can transfer both your apps and their settings.  CAUTION though . . . restoring from that tar will overwrite your system.  So, there are definitely risks to this method.

> **DaddyHoggy said:**
> if I break this - my better half with throttle me! ;)Better wait for a more experienced person to comment on my proposal . . . don't want to be the cause of you getting "throttled".

---

### Post by Bucky Ball on 2009-11-14
Daddy Hoggy, you should post a new thread with a descriptive title to suit your exact problem. You will get more help than being buried 17 deep on an active one concerning someone else's issue. ;-)

---

### Post by DaddyHoggy on 2009-11-15
> **Bucky Ball said:**
> Daddy Hoggy, you should post a new thread with a descriptive title to suit your exact problem. You will get more help than being buried 17 deep on an active one concerning someone else's issue. ;-)

No worries - always nervous as a noob of getting a screen full of rolling eyes and a jabby finger pointing at another thread (that my search missed) - but I will do as you suggest.

Cheers.

EDIT:  Thanks for the quick reply BJ ;)

---

### Post by Bucky Ball on 2009-11-15
DaddyHoggy. You are in the correct forum for beginner's so nothing to be nervous about. As long as you have had a look before posting; we can all miss things right in front of us sometimes (I sure know I can!) :)

Welcome to the forums and Ubuntu!

---

