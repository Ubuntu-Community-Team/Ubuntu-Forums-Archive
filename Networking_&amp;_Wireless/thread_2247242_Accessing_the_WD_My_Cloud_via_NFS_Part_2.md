---
title: "Accessing the WD My Cloud via NFS Part 2"
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by Scooby-2 on 2014-10-06
This is part 2.... split as I can only use 8 images per post. Part 1 is [here]("http://ubuntuforums.org/showthread.php?t=2247237").

10. Now we need to restart the NFS server to make the changes take effect:
```

/etc/init.d/nfs-kernel-server restart

```


[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/9_zps3d569f68.jpg[/IMG]


11. Let's make sure the server is exporting the filesystems correctly by running:
```

showmount -e localhost

```
You should get lines identical to these, but with the username you used in place of janm in my example:


[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/10_zps0cd0bd79.jpg[/IMG]


12. NFS uses UIDs for authentication, not user names and passwords. We need to ensure that the new user has the same UID on both the client and the server.
On both the server, type
```

id -u janm

```
On the server:


[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/11_zps090f6f77.jpg[/IMG]


On the client:


[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/12_zpsead6a29f.jpg[/IMG]


The UIDs must match for the user to have access to the private share. If yours match, skip to step 13.
Without going into details, it is easy to change the UID of a user in Linux. It is also easy to have them suddenly lose access to all the files that they own outside their home directory, as the command we are about to run only affects the files in the user's /home. Therefore, it is best to change the UID of the user on the NAS server to match that of the client. First, we check that the UID we are going to change to is not in use on the server. In the server's terminal window, type
```

cat /etc/passwd|grep {new_uid_we_want} 
```(In my case, we need to change janm's UID to 1002, so the command I used was
```

cat /etc/passwd|grep 1002

```
If nothing is printed out, the UID is not in use and we can continue. See my example:


[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/13_zps6c5cbbc8.jpg[/IMG]


On the terminal on the NAS server type
```

usermod -u 1002 janm

```
Type in the UID in place of the 1002 and the user name janm that I needed. It will take a few minutes to complete, especially if the server is scanning. After it completes. check it has taken effect with
```

id -u janm

```


[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/14_zps3bd367a2.jpg[/IMG]

12a. With thanks for pointing it out, Icreed noticed this section which I overlooked when writing the tutorial.
> [COLOR=#000000][FONT=arial black]Reclaim Ownership of Your Files After Your UID Changes On the Server
[/FONT][/COLOR]
[COLOR=#000000]FYI to those reading this who have to update the UID used on the NAS device because it didn't match the client UID: [/COLOR]

[COLOR=#000000]After the id is updated, the files owned by the old uid will be orphaned. You'll see them when you ls -al a directory. Instead of being owned by a name, the owner will be the former UID which is now not associated with a user. I.e.[/COLOR]

[COLOR=#000000]drwxrwx---+ 3 [/COLOR][B]999 mygroup 4096 Apr 23 2012 DirectoryName

To fix this on a MyCloud device, change to the /shares directory on the server and execute the following command:

find . -uid [B]999 -exec chown [B]1000 {} \;

Replace 999 with the old UID and 1000 with the new UID before running.
[/B][/B][/B]
13. Nearly done! We just need to get NFS installed on the client. In a terminal on the client, type:
```

sudo apt-get update && sudo apt-get install portmap nfs-common

```


14. Create a mountpoints, for example:
```

mkdir -p ~/nas/Public ~/nas/janm

```


15. Check we can see the exports from the client with
```

showmount -e nas # Where nas is the IP address of your server

```


[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/15_zps93da8c3e.jpg[/IMG]


16. Mount the Public share with
```

sudo mount -t nfs -o udp,vers=3,soft,intr,rsize=8192,wsize=8192 nas:/nfs/Public /home/janm/nas/Public # Substitute "nas" with the IP of your server

```
(The options for the mount are beyond the scope of this how-to.)


17. Mount the private share with
```

sudo mount -t nfs -o udp,vers=3,soft,intr,rsize=8192,wsize=8192 nas:/nfs/janm /home/janm/nas/janm/ # Substitute "nas" with the IP of your server

```


18. You should see 2 lines from the following command:
```

mount -t nfs

```


[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/16_zpse0b04947.jpg[/IMG]


19. Test the private share is available and writable with
```

touch ~/nas/janm/mynewfile
ls -l ~/nas/janm

```


20. Check that you have access to the Public directory with
```

touch ~/nas/Public/mynewfile
ls -l ~/nas/Public/mynewfile

```
You should be able to see the three "Shared .." directories and be able to write to them.


If you want to mount your shares at startup there is a good article [here]("http://ubuntuforums.org/showthread.php?t=249889"). 


This how-to does not address any security issues. There are plenty of articles on the web such as this one [here]("http://www.tldp.org/HOWTO/NFS-HOWTO/server.html").


BE AWARE THAT AT THE TIME OF WRITING (6 OCT 2014) THE WD MY CLOUD IS UNPROTECTED AGAINST BASH SHELLSHOCK ATTACKS. I am awaiting a response from WD Support on this subject. UPDATE 7 Nov 2014: version 04.01.00-408 has addressed this.

This how-to does not discuss performance but the mount options are chosen to give the best performance on my 1GB wired network. The network adaptor in the My Cloud could support Jumbo frames which is the one thing that would have provided the biggest performance gain. However WD has chosen to use a driver which doesn't support it and WD Support has advised me that there are no plans to implement it.


Procedure tested on a 2GB WD My Cloud with firmware version v04.00.01-623 and a Linux Mint 17 client running in VM.

NOTE: UPDATING THE WD FIRMWARE WILL RESET THE NFS OPTIONS TO THE DEFAULT. So keep a copy of your new /etc/exports file before you upgrade.

Second edit to add advice re updating the WD firmware.

---

### Post by wormbuntu on 2015-03-09
Hi Scooby-2,

Many thanks for this detailed and hopefully idiot-proof guide.

Quick question - my passwd file contains the target userid (1000) but it looks like it is just the groupid and not the userid. e.g. output is 

alison:1001:1000:Alison Mangan,,,:/shares:/bin/sh

(Alison is another user I've set up on the nas)

Bizarrely mycloud has my main (admin) userID as 999. I thought they would all be set to >1000. Anyway, hopefully this won't cause any problems. Just thought I'd try to run it by you.

Thanks
WB

---

### Post by Scooby-2 on 2015-03-10
@wormbuntu

Your UID is 1001 and GID is 1000. It would probably be better to change the UID of the user on the NAS server as in step 12 above, but bear in mind that if you have any files or folders (on the NAS server) outside the home directory, access to them will be lost until you change their ownership (as root) afterwards.

Hope this helps.

---

### Post by wormbuntu on 2015-03-11
Hi Scooby - thanks for replying.

Just to clarify - The GREP on passwd had the hit above (for a different user) but I think it is just the gid that is 1000. _My_ uid was 999 on the NAS, 1000 on my PC. So I wanted to move my uid to 1000 on the NAS.  
I did the change and then chown'd the relevant share to fix the access. 

The above steps seems to have worked and I can still access from Windows without any problems. So, thank you once again. 

Final question - is there a simple reason why you prefer NFS to CIFS for accessing this drive? Now that it is working with NFS I can't help but want to learn how to do it via SMB.

---

### Post by Scooby-2 on 2015-03-11
@wormbuntu

I'm glad it's all working for you.

The reason I use NFS are 
1. I was brought up on NFS under IBM AIX, which was around and long established before Samba.
 2. Have you compared the config files between the two? The complexity? Samba is considered more secure than NFS V3, but there are steps that you can take to improve scurity with NFS V3 (just Google it). NFS V4 is more secure than Samba but tricky to set up. 
3. NFS is much leaner on resources than Samba, and as the My Cloud is not quite an Intel i-7 with 16GB of memory I need to free up resources (I am running syncthing as a replacement for Dropbox on my My Cloud and, while resource hungry, it doesn't make the My Cloud drop off line while it's scanning). Have a look [here]("http://askubuntu.com/questions/7117/which-to-use-nfs-or-samba") for a brief discussion on NFS vs Samba.

I congratulate you for your determination to learn SMB/CIFS. I ought to as well, if the truth be known, but I am not a fan of Windows and I don't need it. My media centre supports NFS, so no problems there. 

You said [COLOR=#000000] > I can still access from Windows without any problems[/COLOR] Are you sure you are using NFS here, not Samba? The My Cloud supports Samba directly, but not NFS unless you follow the steps in my tutorial. Just a thought.

---

### Post by wormbuntu on 2015-03-11
Cheers Scooby - open source works because of people like you helping out people like me. (And then people like me helping people like my mum & dad)

Re your question - yes my Windows access is just via samba, not NFS. I was just unsure whether changing ID# and ownership of the files might 'break' the windows access. But I guess samba doesn't use ID# so there was no impact to the permissons, which I guess are via ACL.

Cheers

---

### Post by lime4x4 on 2015-03-17
What would i have to do to retore the mycloud back to the way it came out of the box?

---

### Post by Scooby-2 on 2015-03-18
> **lime4x4 said:**
> What would i have to do to retore the mycloud back to the way it came out of the box?
Press the reset button on the back and hold it for 4 seconds (it's above the USB port, and it's recessed, so you will need a straightened paperclip or similar). 

BTW This is in the user manual.

---

### Post by mark.hilt1 on 2015-03-18
what kind of WD my cloud is this for?

---

### Post by lime4x4 on 2015-03-18
I know there is a reset button on the back i didn't know if that would undo what was done by following this tutorial. Something got messed up. I can access it just fine with ubuntu but now my windows machine and mac can no longer write to it for some odd reason

---

### Post by Scooby-2 on 2015-03-18
> **mark.hilt1 said:**
> what kind of WD my cloud is this for?

All of them, though I have not tested it with the latest firmware. It seems WD is trying to lock down the system and as its performance is so poor I no longer use the WD "firmware" as they call it. I just run stock GNU/Debian 7.8 and add whatever programs I want. Feel free to try it. If it works, please post back here.

---

### Post by Scooby-2 on 2015-03-18
> **lime4x4 said:**
> I know there is a reset button on the back i didn't know if that would undo what was done by following this tutorial. Something got messed up. I can access it just fine with ubuntu but now my windows machine and mac can no longer write to it for some odd reason

Nothing in the procedure should affect Samba as NFS and Samba are unrelated. The Samba config is all done from the Web-based GUI, so I would start by checking the settings there.

If you reset your server to factory default be aware that doing a full restore from the GUI securely wipes all your data. Doing a System Only restore from the GUI or by using the reset button keeps your data and share configuration. I also note that the latest instructions from WD say to press the reset button for 40 seconds, and also on their web site there is another option - Quick Restore - in the GUI menu. You would need to read the manual to see what that does. I no longer use the WD firmware due to its poor performance and I am now running stock GNU/Debian 7.8. In this situation you can run Open Media Vault NAS software, miniDNLA media server or others. I am now running Syncthing (an Open Source replacement for Dropbox) on mine, and I use NFS to feed my media centre (it uses less resources than Samba). I am hoping to install OpenVPN which, as it runs on a Raspberry Pi, should have no problems on the WD platform. Incidentally, my media server is a Raspberry Pi running Kodi (formerly XBMC).

---

### Post by lime4x4 on 2015-03-18
U have instruction on how to replace the wd firmware?

---

### Post by Scooby-2 on 2015-03-18
> **lime4x4 said:**
> U have instruction on how to replace the wd firmware?
Yes, all the hard work has been done by member Fox_exe, a Russian who really knows what he is doing. The instructions are on the first page of the posts and he updates them when necessary. He has shared the basic clean Debian install as well as two others with different versions of OMV pre-installed. It's hard work, but it's worth reading all of it - you will get a feel for the amount of work people have done. See the forum [here]("http://community.wd.com/t5/WD-My-Cloud/Clean-debian-and-OpenMediaVault-on-WDMyCloud/td-p/785505"). Amazingly, it's hosted by WD (and not deleted, presumably as there are so many issues with the product and enough people wanting to change the software on it. You will invalidate your warranty but what use is warranty on a product that doesn't perform?

---

### Post by lime4x4 on 2015-03-20
Thanks i don't think i'm gonna be taking the cloud apart. I reset the config files thru the web interface and my windows and mac machine were able to reconnect and write to the drive. I installed ubuntu mate on another computer and that will read and write to the drive without any issues or mods.

---

### Post by Scooby-2 on 2015-03-20
Just to let you know (and anyone else that reads this) there's no need to take the drive apart to install vanilla Debian or revert back to the WD firmware. You only need to do that if you attempt something too adventurous!

---

### Post by lime4x4 on 2015-03-20
U have instructions for that? I was looking thru that forum u linked to and they were talking about taking the disk out and installing it in a pc to load the new firmware

---

### Post by lime4x4 on 2015-03-20
Ok after rereading it i'm still confused...lol do i do the debian clean still then omv install or just the omv install? I use the mycloud as a media server

---

### Post by Scooby-2 on 2015-03-21
> **lime4x4 said:**
> Ok after rereading it i'm still confused...lol do i do the debian clean still then omv install or just the omv install? I use the mycloud as a media server
OMV is NAS software. If you want a media server just install clean Debian and then miniDNLA (which seems to be the favourite).

---

### Post by lcreed on 2015-03-22
[FONT=arial black][FONT=arial]This was an excellent guide that really helped me to convert from cifs to nfs.  I just wanted to add a couple of things.  OP is welcome to add anything he views worthy to the tutorial.[/FONT]

Reclaim Ownership of Your Files After Your UID Changes On the Server
[/FONT]
FYI to those reading this who have to update the UID used on the NAS device because it didn't match the client UID: 

After the id is updated, the files owned by the old uid will be orphaned.  You'll see them when you ls -al a directory.  Instead of being owned by a name, the owner will be the former UID which is now not associated with a user.  I.e.

drwxrwx---+  3    **999** mygroup    4096 Apr 23  2012 DirectoryName


To fix this on a MyCloud device, change to the /shares directory on the server and execute the following command:

find . -uid **999** -exec chown **1000** {} \;


Replace 999 with the old UID and 1000 with the new UID before running.

[FONT=arial black]FSTAB Examples
[/FONT]
For simplicity sake, I decided to export the entire system rather than the individual shares.  It was easier for me to symlink the directories than have multiple mounts.  I scoured the documentation and online examples of fstab entries and came up with the following examples.  I suspect these can be improved on but they worked for now if you're just looking for a quick example.

# /etc/exports Entry

/nfs *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)



# /etc/fstab Entry

###########################################
# MyFloppy NFS Mounts - WD My Cloud NAS #
###########################################
1.2.3.4:/nfs /media/myFloppy nfs user,rsize=8192,wsize=8192,bg,timeo=14,intr 0 0

# substitute 1.2.3.4 with your device's IP address
# substitute /media/myFloppy with your mountpoint

*Note:  I did read that intr is deprecated.  *

---

### Post by Scooby-2 on 2015-03-22
> **lcreed said:**
> [FONT=arial black][FONT=arial]This was an excellent guide that really helped me to convert from cifs to nfs.  I just wanted to add a couple of things.  OP is welcome to add anything he views worthy to the tutorial.[/FONT]

Reclaim Ownership of Your Files After Your UID Changes On the Server
[/FONT]
FYI to those reading this who have to update the UID used on the NAS device because it didn't match the client UID: 

After the id is updated, the files owned by the old uid will be orphaned.  You'll see them when you ls -al a directory.  Instead of being owned by a name, the owner will be the former UID which is now not associated with a user.  I.e.

drwxrwx---+  3    **999** mygroup    4096 Apr 23  2012 DirectoryName


To fix this on a MyCloud device, change to the /shares directory on the server and execute the following command:

find . -uid **999** -exec chown **1000** {} \;


Replace 999 with the old UID and 1000 with the new UID before running.

[FONT=arial black]FSTAB Examples
[/FONT]
For simplicity sake, I decided to export the entire system rather than the individual shares.  It was easier for me to symlink the directories than have multiple mounts.  I scoured the documentation and online examples of fstab entries and came up with the following examples.  I suspect these can be improved on but they worked for now if you're just looking for a quick example.

# /etc/exports Entry

/nfs *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)



# /etc/fstab Entry

###########################################
# MyFloppy NFS Mounts - WD My Cloud NAS #
###########################################
1.2.3.4:/nfs /media/myFloppy nfs user,rsize=8192,wsize=8192,bg,timeo=14,intr 0 0

# substitute 1.2.3.4 with your device's IP address
# substitute /media/myFloppy with your mountpoint

*Note:  I did read that intr is deprecated.  *
@Icreed Many thanks for this. I knew about it as Wormbuntu had this exact problem just last week and I hadn't got round to adding it. I have now added a section 12a above, using your notes.

Regarding the separate mount commands, I separate them because it allows different users to mount Public and their own private shares by using the same script. Hence when I run it, it mounts Public and my private share, my my wife runs it it mounts Public and hers.

---

### Post by simon95 on 2015-04-08
Hi

I have followed this excellent guide so far - Im trying to install NFS but when I come to create the mountpoint for Public it says it does not exist. I've tried it three or four times now, with the mkdir command but with no joy. Any guesses what Im doing wrong?

Thanks!

Simon

---

### Post by Scooby-2 on 2015-04-08
> **simon95 said:**
> Hi

I have followed this excellent guide so far - Im trying to install NFS but when I come to create the mountpoint for Public it says it does not exist. I've tried it three or four times now, with the mkdir command but with no joy. Any guesses what Im doing wrong?

Thanks!

Simon

Hi Simon

You need to ensure you have write access to wherever it is you are trying to create the mount point. If it is (or they are) in your home directory, as in my example```
[COLOR=#000000][FONT=Ubuntu Mono]mkdir -p ~/nas/Public ~/nas/janm[/FONT][/COLOR]
``` the ~ character, as you may know, indicates your home directory where of course you will have write access. However if you want to use /mnt/nas you will not have write access here as a regular user. As you need to run the command as root, you would need to use```
sudo mkdir -p /mnt/nas/public /mnt/nas/janm
```The -p option will create /mnt/nas as well if it doesn't already exist.

---

### Post by simon95 on 2015-04-08
Thankyou for the quick reply! I've tried that, but with the same result. Showmount -e IPADDRESS just returns
/nfs/Simon

no sign of 
/nfs/Public

despite using the command 
sudo mkdir -p /mnt/IPADDRESS/public /mnt/IPADDRESS/simon

Any idea why it's mounting one but not the other?

Thanks again

Simon

---

### Post by Scooby-2 on 2015-04-08
@Simon95
I tried to send you a private message but dor some reason I am unable to send it. Here's what I tried to send:
Hi Simon

To save cluttering up the thread, just to let you know that [COLOR=#000000]showmount -e IPADDRESS[/COLOR] when run from the client will display what the server is making available across the network. It makes no assumption that the client is set up correctly. Think of a file system as a box of screws in your garage. The mount point is simply a location on a pegboard on which to hang it (ie make it, and its contents, available to see and use). To create a mountpoint don't specify the IP address. You should be on the client to do this. Also, when we use the mkdir (**m**a**k**e **dir**ectory) command we are creating an empty directory on which we will see the data that later gets mounted with the mount command. You could even use an existing directory, with data in it, and provided the permissions are correct the mount will take effect and you will see the data in the mounted filesystem at that point (or, effectively, in that directory). The existing data will not be lost - just hidden by what is mounted over the top. So you put another box of screws in the same place that you already have one on your pegboard. The screws in the box (file system) at the back can't be seen because they are hidden by the box in front (the file system you mounted on top, or in front, of it). You have not lost your original data (screws) because they will be visible and available when you remove the box in front (unmount the file system which is on top). I hope this makes sense and helps to explain what is going on. 

As your showmount -e IP shows just /nfsPublic there is a problem with the exports on your server. You should see /nfsPublic and /nfs/Simon, so you need to retrace your steps on the server. Check your exports file for syntax errors.

---

### Post by simon95 on 2015-04-08
Thankyou very much!

Simon

---

### Post by nfpinto on 2015-09-20
[SIZE=2][FONT=arial]Hi , I came across this tutorial when trying to Configure my WD MYCloud throught NFS. I'm stuck at step 12 as i can't change my UID to match the client uid, when i do:
[/FONT][/SIZE][SIZE=2][FONT=arial]WDMyCloud:/etc# usermod -u 1000 nuno

i get the reply 

[SIZE=2][FONT=arial]WDMyCloud:/etc# 
usermod: [/FONT][/SIZE]user nuno is currently used by process 2190



[/FONT][/SIZE][SIZE=2][FONT=arial][SIZE=2]


the ouptup for cat /etc/passwd|grep 1000 is
[/SIZE]
WDMyCloud:/etc# cat /etc/passwd|grep 1000
nobody:x:65534:1000:nobody:/nonexistent:/bin/sh
nuno:x:999:1000:Nuno Pinto,,,:/shares:/bin/sh
guest:x.500:1000::/shares:/bin/sh
daapd:x:501:1000::/shares:/bin/sh
ilda:x:1001:1000:Ilda Filipe,,,:/shares:/bin/sh

I wanted to move my uid to 1000 on the NAS., but can't do it. I searched on google but can't find an answer.
Any help would be apreciated.
Thanks

[/FONT][/SIZE]

---

### Post by Scooby-2 on 2015-09-20
The system won't let you change the UID of a user when that user has processes running. To find out what is running, type
```
ps aux|grep [COLOR=#000000][FONT=arial]2190[/FONT][/COLOR]
```[COLOR=#000000][FONT=arial] or whatever PID you are now getting in the message [/FONT][/COLOR]> [SIZE=2][COLOR=#000000][FONT=arial]usermod: [/FONT][/COLOR][/SIZE][COLOR=#000000][FONT=arial]user nuno is currently used by process 2190[/FONT][/COLOR] You then need to stop whatever is running and issue the usermod command again.

---

### Post by nfpinto on 2015-09-26
ok thanks

---

### Post by alan_aul on 2015-11-07
If i just want to set up the public share is it ok to skip the UID parts? I get to the part when actually mounting the directory and it just sits there and doesnt throw an error or give me a new prompt until i hit control + c. I am able to see it ok with showmount -e IP from the client.

---

### Post by facundo8 on 2015-12-26
Works !! 

here my video:

[https://www.youtube.com/watch?v=S5P_-sX09Mo](https://www.youtube.com/watch?v=S5P_-sX09Mo)

---

### Post by panda4 on 2016-01-11
First, thanks for this. its easy enough to follow that I figured I'd try it, but hard enough for semi computer illiterate me that i may have messed it up.

> HolbrookCloud:~# /etc/init.d/nfs-kernel-server restart
[ ok ] Stopping NFS kernel daemon: mountd nfsd.
[ ok ] Unexporting directories for NFS kernel daemon....
[....] Exporting directories for NFS kernel daemon...exportfs: Failed to stat /nfs/panda: No such file or directory
. ok
[ ok ] Starting NFS kernel daemon: nfsd mountd.

I did nothing with exportfs so this confuses me... I'm stopping until i find out if I have to fix it. (please remember with your response, semi computer illiterate and not great with terminal.) thank you.

sigh, i just want my hd movies to not stutter or stop on osmc on rpi...

---

### Post by Scooby-2 on 2016-01-12
Please post a copy of your exports file.

---

### Post by gavin16 on 2016-02-26
sorry to drag up a really old thread Scooby but i've been trying to find a decent guide to set this up and urs is by far the best i've seen for n00bs like me!
basically, ive got as far as step 10 when i get an error saying invalid user. when i proceed to 11 it gives me my localhost number on the server but says no such user when i do it on my pi. i guess it's because need to configure a user on the pi but i don't know how to. any help/advice would be greatly appreciated!

thanks

edit: worth mentioning that i get the same error as panda...

---

### Post by Scooby-2 on 2016-03-04
You simply need to type "id -u *username*" where *username* is whoever you need to be able to access the server. The default user on the pi is often "pi" but it depends on the distro and also how it was set up during installation. If you set up a user called gavin16 you would type "id -u gavin16"

---

### Post by skiffandr on 2016-07-07
> **Scooby-2 said:**
> This is part 2.... split as I can only use 8 images per post. Part 1 is [here]("http://ubuntuforums.org/showthread.php?t=2247237").

.....

On the terminal on the NAS server type
```

usermod -u 1002 janm

```
Type in the UID in place of the 1002 and the user name janm that I needed. It will take a few minutes to complete, especially if the server is scanning. After it completes. check it has taken effect with
```

id -u janm

```


[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/14_zps3bd367a2.jpg[/IMG]


...



My user ID on macos is 501.
But, if I change UID on NAS for this user to 501, then this user hide from control panel of NAS.

NAS cant see UID less 1000?

Thanks for answer :)
And sorry for my English

---

### Post by gus.ivan on 2016-11-21
Hello I'm seeing similar behavior after changing the UID for my username on the NAS device. It is a sub 1000 UID and after altering it, the USER vanishes from my NAS GUI.  I still see the user in the /etc/passwd file but not in the GUI itself.  My NAS my cloud version is 2.21.119

---

### Post by Scooby-2 on 2016-11-21
> **gus.ivan said:**
> Hello I'm seeing similar behavior after changing the UID for my username on the NAS device. It is a sub 1000 UID and after altering it, the USER vanishes from my NAS GUI.  I still see the user in the /etc/passwd file but not in the GUI itself.  My NAS my cloud version is 2.21.119

I'm sorry to have to tell you that I long ago removed the WD software and I now run native Debian Linux on my MyCloud, which gives me far me control and the machine is no longer frequently CPU-bound and thrashing the disk. Furthermore it does not write thumbnails of 2 or three different sizes for every picture and video uploaded to it (which is what I experienced about two years ago with the then current software - it was so busy creating thumbnails it was unable to maintain its presence on line). As I use my NAS server primarily for photo and video storage, I have found that the pre-installed software (or firmware, as WD prefer to call it) did not meet my requirements. I stress that I am not saying that the WD system is bad, it is just not for me personally.

The upshot is that I am not familiar with the workings of the later WD releases and I am unable to emulate and explore the problem you are experiencing, sorry. :sad: All I can suggest is that you change your UID to something greater than 1000.

---

