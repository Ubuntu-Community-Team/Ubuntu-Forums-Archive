---
title: "Samba server"
date: 2021-03-13
forum: Networking &amp; Wireless
---

### Post by lwhite46 on 2021-03-13
I am near clueless on server setup. I have samba on raspian, raspberrypi, all current updates. The sharing file mounted as a new drive on Windows 10 with full write permissions. But I go to my Ubuntu 20.04 desktop and in networking the raspian shows but I get the error message "Failed to retrieve share list from server: Connection timed out". But I can ssh into the server. I see this has been discussed a lot here. 
My question is should Ubuntu not mount the server share file as a drive?

---

### Post by TheFu on 2021-03-14
If you want any storage mounted, then you need to mount it. It isn't automatic.

There are a few different ways. Using the GUI is the worst for a few reasons.  Plus, you can use nfs or sftp to access files between Unix systems really easy after setup.
[LIST]
[*]In most Linux file managers, we can use sftp:// URLs to access storage on other systems securely. If ssh-keys are setup, this can can be seamless.That's just 2 commands to crate and xfer a key. The same keys for ssh are used for sftp, scp, rsync, and 50 other connection programs. The keys are worth setting up.
[*]NFS is a little harder to setup, but more convenient. NFS appears like local storage on clients and has excellent performance. It also supports native Unix permissions. The *Ubuntu Server Guide* has setup steps.
[*]Samba uses CIFS. It is user-to-server and a little more complex to setup than the methods above.
[/LIST]
All can be setup concurrently.  
sftp can be used from anywhere in the world with internet.
NFS is the fastest and better for streaming media for some reason.  NFSv4 can be strongly encrypted and server-to-server authenticated.  All users have access to the storage based on Unix permissions. Each fle and directory can have different owners, groups, ACL, and permissions.
CIFS is fast and usually needed for Window clients. Permissions are controlled at mount-time only and support only 1 owner, 1 permission mask.

So, pick which you'd like to use, post the working smb.conf and someone should be able to help with a client-side config.

---

### Post by lwhite46 on 2021-03-15
Here is the smb.conf file from the server. Works for windows 10, Ubuntu 20.04 sees it but is denied access "Share list error".[ATTACH=CONFIG]288139[/ATTACH]

---

### Post by Morbius1 on 2021-03-16
I ran an experiment where I installed raspian on a VBox guest and so far I have the opposite results.

This is how I set things up so let me know how far off my setup is to yours:

I installed raspian ( 2021-01-11-raspios-buster-i386.iso ) in a VBox guest.
I replicated your [gloabl] parameters by including the rather odd reference to "client min protocol = SMB3' and making the [homes] share browseable.

My result:

There is no way a Win10 box can discover ( Explorer > Network > Raspberry ) then connect to any shares because by default Win10 doesn't enable SMB1 which in turn disables NetBIOS host discovery. I can make it work by enabling SMB1 on the Win10 client but you didn't mention you did that in your post. I could connect to the box explicitly in explorer: \\raspberry.local but you didn't mention you did that either.

Just the opposite result from a Ubuntu 20 client: Nautilus > Other Locations > Raspberry. 
[ATTACH=CONFIG]288140[/ATTACH]
It will work using the Windows-way as well: Nautilus > Other Locations > Windows Network > Workgroup > Raspberry
[ATTACH=CONFIG]288141[/ATTACH]

---

### Post by lwhite46 on 2021-03-16
I do have SMB1 enabled in Windows. I am running Raspian GNU/LINUX 10 (buster) version 10 on a raspberrypi 3. In Windows the folder shows up as "pi(\\raspberrypi)(Z)" with all privileges. I see RASPBERRYPI in other locations in Ubuntu but clicking on it gives me the error message "Failed to retrieve share list from server. Connection timed out."  Using smb://raspberry.local gives the same result.

---

### Post by Morbius1 on 2021-03-16
> In Windows the folder shows up as "pi(\\raspberrypi)(Z)" with all privileges.
Ah, you are "mapping" a "network drive". That wasn't clear.

If your questions is can you do a "map" in Ubuntu? Yes you can.

For a temporary mount if I mount my raspberry share which I labeled Test:
```
sudo mount -t cifs //raspberry.local/Test /home/tester/Public -o guest,uid=1000
```
I will end up with a mount icon the left side panel of Nautilus to that location and when selected I will have r/w access to that share..

I would have to add an appropriate entry in fstab to make it permanent.

As far as your error message when browsing for the share I can't reproduce it. It appears we are sing the same version of debian but I'm wondering if we are using different versions of samba. On the pi run:
```
samba -V
```
My version is:
> Version 4.9.5-Debian

Side note: Running "smb://raspberry.local" is not going to get you far if your hostname is raspberrypi

---

