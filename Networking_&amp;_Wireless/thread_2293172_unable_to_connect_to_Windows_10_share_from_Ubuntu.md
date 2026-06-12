---
title: "unable to connect to Windows 10 share from Ubuntu"
date: 2015-09-03
forum: Networking &amp; Wireless
---

### Post by Dok_Jest on 2015-09-03
*I'm not 100% sure if this is a Windows or an Ubuntu issue, so if this is in the wrong location, my apologies.*

Background of the problem:
I have a Windows 10 environment (3 Windows 10 machines with user-level shares to the same *username*@outlook.com) with a Ubuntu Mate 15.04 desktop that is acting as a LAMP to host my media server. The Ubuntu system has not USB ports and the media files are stored on an external USB drive shared by one of the Windows 10 machines. I  would attach to the share with:
**sudo mount -t cifs //192.168.1.68/Media /mnt/Media -o username=*username*@outlook.com,password=*password***

The username is the Microsoft username/password and this worked until the machine that the external drive was attached to died.

I moved the external USB drive to one of the other machines, went into the folder properties, took ownership on the new machines and recreated the share. I adjusted the IP address accordingly and started getting:
**Mount://192.168.1.73/Media: can't Read SuperBlock**

I read what I could find and installed the *cifs-utils*, and this seemed to help a little bit, but now I get:
[B]Mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

[/B]I read and tried the following:
[B]sudo mount.cifs //192.168.1.73/Media /mnt/Media --verbose -o username=*username*@outlook.com,password=[I]password
[/I][/B]The output of this is:
[B]mount.cifs kernel mount options: ip=192.168.1.73,unc=\\192.168.1.73\Media,user=*username*@outlook.com,pass=********
[/B]**mount error(5): Input/output error**

Help:
I'll admit I'm over my head here, and while I could probably rebuild the Linux box easily enough, I won't learn that way. Also I'm not convinced that it is the problem, or at least the entire problem. I can access \\192.168.1.73\Media from the other Windows 10 machine (leading me to think this isn't a Windows problem) and here's the odd part, I can open Caja (Mate's file manager) and when I select Browse Networks, without drilling down to Windows Networks, I can see the Windows computers listed. If I double-click on any of the machines (all have a simple share) I get the expected login prompt, but NONE will let me login, it just returns back to the login prompt.

Any help on this is greatly appreciated. 

Dok Jest

---

### Post by Morbius1 on 2015-09-03
I might be able to answer one issue you mentioned:
> here's the odd part, I can open Caja (Mate's file manager) and when I  select Browse Networks, without drilling down to Windows Networks, I can  see the Windows computers listed. If I double-click on any of the  machines (all have a simple share) I get the expected login prompt, but  NONE will let me login, it just returns back to the login prompt.
How are you passing the username and password?

It's different when you use the Microsoft account to authenticate. The domain becomes the domain of your account:
[ATTACH=CONFIG]264205[/ATTACH]
As for the "Mount error(5): Input/output error" error that is something I can't reproduce on my system yet. I will keep trying when I get a few minutes free.

---

### Post by Dok_Jest on 2015-09-03
That definitely got me further, Thanks for that Morbius! (I got tricked into thinking the workgroup was the domain - I feel both a little stupid at not seeing and trying that, and thankful that at least that was straight forward)

Using Caja I can see the shares, but at the moment cannot authenticate to them (I get the login prompt again, but this time it will not let me proceed) 

(Probably unrelated, but I know that the more I share, the better the chances of finding a fix)
I also took a look and just confirmed that my /etc/fstab only lists my main and swap partitions. I was testing with an auto-reconnect earlier, but when I made no progress, restored the backup of the fstab I made at the time. The credential file still exists, and although I am not using it during my troubleshooting, I did update it to reflect the changes you shared above (change username to dokjest, add a domain=outlook.com) 

On the Windows machine I added "everyone" as full control access, and am a little confused that trying to connect as anonymous didn't work, but also understand other things are going on here. 
Tonight I am going to bring a Windows 8 laptop home and just see if that has any success.

Thanks again Morbius and everyone else for your input!

Dok Jest

---

### Post by Morbius1 on 2015-09-03
The problem for me is that this type of mount works fine for me:
> sudo mount -t cifs //vwin10.local/shared /home/morbius/Test -o username=blzebub@hades.com,password=xxxxxxx,uid=1000
And "everyone" isn't everyone. It's every local user present on the Win10 system. Are you sure that [EMAIL="dokset@outlook.com"]dokset@outlook.com[/EMAIL] actually exists on Win10? 

Even if he wasn't though it doesn't explain this error:
> **Mount error(5): Input/output error**
If the user didn't exist you would get an access denied error. Or in the case of Caja you would be in an infinite loop of it asking for credentials.

The only possible difference between what you are doing and what I am doing my be that I set up this shared folder the way I would do it on Linux. Not through the C:\Users\username.... path but I created a folder at C:\Shared, shared it, and am accessing that share.

---

### Post by Dok_Jest on 2015-09-06
Well I brought a couple machines home to work with, including my Xenserver and another Windows 10 laptop. 
The share was view-able by the other Windows machines, but not by any machine that didn't have a Microsoft OS.
I setup the share on the other Windows 10 machine and it also replicated the same problem.

On a whim I backed up all the data on the share drive (thankfully had enough room to do that) and reformatted it on the other Win 10 machine with USB ports (again with NTFS) and tried to share it from that machine and I was finally able to see it from the Ubuntu machines!! I moved the drive back to the original Win 10 machine and set the share back up and it was NOT seen. This tells me that the problem is most probably 2 fold, the Shared drive partition, and the original Win 10 machine. I'm going to rebuild the OS on the suspect machine later in the week, and I expect that to be the end of things.

Thanks for your help Morbius! you helped me come up with a couple ideas I would not have had otherwise, and ultimately got me to where I need to be.

Dok Jest!

---

### Post by mgbertiaux on 2016-05-29
I could connect to my Desktop (windows 10 pro) from my linux laptop
I'm not Ubuntu's user. I'm using Linux Mint (fork) and my default file manager is "nemo": When I wrote in my dirbar "smb://DESK001_PC" it threw a login request. In that login it asked my  "user", "domain" and "password".


In my desktop-pc I have a MS-account (outlook account) like main user: [email]MyAccout@outlook.com[/email]. My "Domain" is DESK001_PC and my work group is "WORKGROUP" as default. 
At first time I tried:


user: [email]myaccount@outlook.com[/email]
domain: DESK001_PC 
pass: *******


But It didn't work. Then at second time I tried:


user: [email]myaccount@outlook.com[/email]
domain: WORKGROUP
pass: *******


And It didn't work again. So I looked in my laptop (in windows 10 partition) that when I connected to my Desktop, using [email]myaccout@outlook.com[/email] / ******* It works and IT SAID (DOMAIN OUTLOOK.COM). It looked so stupid but I said to myself; I've got nothing to lose.


At third time  I tried:


user: [email]myaccount@outlook.com[/email]
domain: outlook.com
pass: *******


And IT WORKED PERFECT! 


That is my experiencia. I hope to help someone in the future

---

### Post by UltraAnders on 2016-06-26
Thanks mgbertiaux. Been trying to work this out today. My account is [email]something@hotmail.com[/email] and so the domain needed is hotmail.com

---

### Post by cliveo2 on 2016-09-24
> **mgbertiaux said:**
> I could connect to my Desktop (windows 10 pro) from my linux laptop
I'm not Ubuntu's user. I'm using Linux Mint (fork) and my default file manager is "nemo": When I wrote in my dirbar "smb://DESK001_PC" it threw a login request. In that login it asked my  "user", "domain" and "password".


In my desktop-pc I have a MS-account (outlook account) like main user: [EMAIL="MyAccout@outlook.com"]MyAccout@outlook.com[/EMAIL]. My "Domain" is DESK001_PC and my work group is "WORKGROUP" as default. 
At first time I tried:


user: [EMAIL="myaccount@outlook.com"]myaccount@outlook.com[/EMAIL]
domain: DESK001_PC 
pass: *******


But It didn't work. Then at second time I tried:


user: [EMAIL="myaccount@outlook.com"]myaccount@outlook.com[/EMAIL]
domain: WORKGROUP
pass: *******


And It didn't work again. So I looked in my laptop (in windows 10 partition) that when I connected to my Desktop, using [EMAIL="myaccout@outlook.com"]myaccout@outlook.com[/EMAIL] / ******* It works and IT SAID (DOMAIN OUTLOOK.COM). It looked so stupid but I said to myself; I've got nothing to lose.


At third time  I tried:


user: [EMAIL="myaccount@outlook.com"]myaccount@outlook.com[/EMAIL]
domain: outlook.com
pass: *******


And IT WORKED PERFECT! 


That is my experiencia. I hope to help someone in the future
Thanks very much for this solution. I found that (in my case) it was unneccessary to change the domain from "workgroup" which is the default.

---

### Post by wildmanne39 on 2016-09-24
Old thread closed.

---

