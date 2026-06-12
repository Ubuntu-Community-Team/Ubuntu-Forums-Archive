---
title: "Networking with other Linux computers"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by poscomp on 2009-05-28
How can I link via the router to other Linux computers? I can see windows to windows and I can also see Linux to windows. I can't see windows to Linux or Linux to Linux. I'm sure the fix is easy but I'm al a loss. Please help.

---

### Post by Bölvaður on 2009-05-28
Are you looking for help with Samba, NFS or SSH ?

if NFS then look for my answer in this thread [http://ubuntuforums.org/showthread.php?t=1165077](http://ubuntuforums.org/showthread.php?t=1165077)

---

### Post by nothingspecial on 2009-05-28
Assuming you`re using 9.04.```


sudo apt-get install openssh-client
```

on all your ubuntu boxes

Figure out all your ip adresses - right click on the network manager doobry on your panel then select connection information.

On computer A select Places > Connect to server

Change the top box to ssh

Second box type username@ipadress_of_computerB

Tick add bookmark

Choose a name for Computer B

Computer B will be in Computer A`s Places menu forever more........

Or at least until you break something .

---

### Post by powel212 on 2009-05-28
Option one:
Please use ADD/Remove to install Samba,(system-config-samba).

Once installed go  to System/Administration/Samba

Click Add, choose the folder you want to share. 

Then under preferences/security Change authentication mode to "Share"

and guest account to "your-own-user-name" click ok

Once this is done you will be able to see windows shares and windows will be able to see ubuntu shares.

It may seem like a lot to set up file sharing but it is the best way.

there is another easier way but it is not as comprehensive and therfore can run into trouble with it later but this is the secondary way;

Option two:
Right click any folder in Ubuntu choose sharing options, share this folder, allow others and guest access. then click create share.

You will be told that this service is not installed and needs to be installed now. click ok and proceed. 

Reboot and repeat;
Right click any folder in Ubuntu choose sharing options, share this folder, allow others and guest access. then click create share.

Now you are done.

If you chose the first option you do not need to use the second option.

---

### Post by superprash2003 on 2009-05-28
if you are new to ubuntu , try samba , its easy to configure..

---

### Post by mrbinitie on 2009-06-12
I did exactly that (powel212 advice)- but - no joy at all. I can ping 192.168.1.64 from 192.168.1.68 but when I try to see the computer via Samba or SSH it says its not able to mount the volume

---

### Post by gradinaruvasile on 2009-06-12
try typing in a terminal
ssh username@ip
username=the user name on the target computer
ip=ip address of target computer
answer yes if asked (typing yes, not y )
Ssh must be installed on both computers
See if this works.

---

### Post by rlogan on 2009-06-12
Personally I use SSH to link to other pc's on out network.

I have bookmarks setup on each machine to link to the relevant machine as required

---

### Post by clive littlewood on 2009-06-12
Hi

I use "Giver" it's in the repos and is very simple with good info of who has sent a file etc.

Check out my Blog for more details.

Clive

---

