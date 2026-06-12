---
title: "Can no longer connect to windows shared folder after software update ubuntu 15.10"
date: 2016-04-19
forum: Networking &amp; Wireless
---

### Post by Martin_Finnemann on 2016-04-19
Hi guys

I am going mad here. After a software update I can no longer connect to my shared folders on my windows desktop. I use the Ubuntu computer as a media center by my flatscreen, and have all the media stored on a external drive by the windows desktop. The windows computer has been setup to share the folders with everyone on the network, and without password. 
Before yesterday (the software update in ubuntu) i could easyli connect to the windows share via the networks tab in the file browser. But now it asks for credentials, but will not accept the credintials of my windows user. Tried installing kodi and se if that would help, same prblem. It does not accept the credentials. Have tried to connect to it as a server in file browser, same problem it does not accept the credentials. Tried reinstaliing windows 10, no change.
From my andrid devices I can still acces the shares via the ES file app witout any issues and without having to put in any credentials at all. Seems like the ubuntu software update messed it all up.

Any ideas on a fix??

---

### Post by Chris_Ronk on 2016-04-19
There has obviously been something that broke Samba in the 4.3.8 update... there are all sorts of threads about it....

This one showed a possible fix:

[http://ubuntuforums.org/showthread.php?t=2320960](http://ubuntuforums.org/showthread.php?t=2320960)

It did not work for me.

---

### Post by scpatl4now on 2016-04-20
Did not work for me either

---

### Post by Alex_TNT on 2016-04-20
Same problem. If you install a fresh copy of ubuntu and update you can no longer connect to windows shared folder. It asks for credentials

---

### Post by taouk on 2016-04-20
I have the same problem. After updating Samba i cannot access share folders in windows stations. I' m using Ubuntu 14.04

---

### Post by Martin_Finnemann on 2016-04-20
> **Chris_Ronk said:**
> There has obviously been something that broke Samba in the 4.3.8 update... there are all sorts of threads about it....

This one showed a possible fix:

[http://ubuntuforums.org/showthread.php?t=2320960](http://ubuntuforums.org/showthread.php?t=2320960)

It did not work for me.

I don't even have the **security = share **in my smb.conf file.... So not working for me either....:confused:

[COLOR=#000000]And to make it even more confusing, I have another Ubuntu laptop which has not been updated and can still acces the windows share. I copied the smb.conf file from that laptop, put it in the other one which could not acces the windows share but no luck. Still cannot access the windows share from the updated computer. [/COLOR]
[COLOR=#000000]So maybe it isn't the smb.conf file thats makes the problem, but something else in the latest update!![/COLOR]

[COLOR=#000000]Any ideas??????[/COLOR]:confused:

---

### Post by Chris_Ronk on 2016-04-20
I did the same thing with the same result.  This is definitely a bug, but I don't know how to submit it...

---

### Post by cheawick on 2016-04-20
I'm having the same issue, thankfully I have an non-updated VM running an install of Ubuntu Desktop that I can still push Unison data synchronizations through with. While I'm not new to LINUX I'm still struggling to learn my way around with terminal commands, so does anyone know of a way to roll back an update? Don't know if this helps, but I'm trying to link to a Mac OS X data share.

---

### Post by Nahuel_ on 2016-04-21
In a way Im happy Im not alone. Exactly same problems. I posted a question on askubuntu.com, but no replies yet.
[http://askubuntu.com/questions/759560/re-configure-samba-file-sharing-stop-it-from-asking-for-passwords](http://askubuntu.com/questions/759560/re-configure-samba-file-sharing-stop-it-from-asking-for-passwords)

I hope someone figures out how To solve it! It's making work really unconfortable ay the office.

---

### Post by Chris_Ronk on 2016-04-21
These are interesting:

[http://comments.gmane.org/gmane.network.samba.general/156583](http://comments.gmane.org/gmane.network.samba.general/156583)

[https://bugzilla.redhat.com/show_bug.cgi?id=1327072](https://bugzilla.redhat.com/show_bug.cgi?id=1327072)

---

### Post by Martin_Finnemann on 2016-04-21
[COLOR=#000000]No one?? Has anybody found a fix?[/COLOR]:confused:

---

### Post by Taz8du29 on 2016-04-21
Try to re-share the folder !

---

### Post by Nahuel_ on 2016-04-21
> **Taz8du29 said:**
> Try to re-share the folder !

I don't think that would work. The problem is that an Ubuntu client can't connect to other samba servers (running windows).

---

### Post by cheawick on 2016-04-22
Very interesting with similar results using end to end Wireshark listening... The computers can communicate briefly then there is something that borks the process even though I have been granted access and can view the target computer file structure that I'm granted access and permissions to. It's almost like the Time To Live (TTL) connection allowance has been reduced to nearly nothing. Please note that I'm in no way an expert on this issue and I'm seeking guidance just like the other folk here.

EDIT: I really should have saved those Wireshark dives, perhaps someone with more experience could have used them to identify the problem and help out the community more quickly. =+S

---

### Post by Morbius1 on 2016-04-22
Use cifs to mount the share until Samba figures out what it did wrong or someone comes up with a reliable work around:

[1] Make sure a package is installed:
```
sudo apt-get install cifs-utils
```
[2] Create a mount point for the Windows share:
```
sudo mkdir /media/WinShare
```
[3] Then do a temporary mount:
```
sudo mount -t cifs //server-name/share-name /media/WinShare -o guest,uid=1000
```
If you are successful I can show you how to automate this process so you don't have to use the terminal/

---

### Post by Nahuel_ on 2016-04-22
> **Morbius1 said:**
> Use cifs to mount the share until Samba figures out what it did wrong or someone comes up with a reliable work around:

[1] Make sure a package is installed:
```
sudo apt-get install cifs-utils
```
[2] Create a mount point for the Windows share:
```
sudo mkdir /media/WinShare
```
[3] Then do a temporary mount:
```
sudo mount -t cifs //server-name/share-name /media/WinShare -o guest,uid=1000
```
If you are successful I can show you how to automate this process so you don't have to use the terminal/

YES! Thanks a lot! That works a dream. My share-name had spaces, so I put the whole address in single quotes and it mounted it instantly!

I can now patiently wait for the samba bug fix :)

---

### Post by Chris_Ronk on 2016-04-22
Doesn't really work for me...

I have a Samba server running as a DC for an entire network....I have roaming profiles setup and the whole ball of wax....I need a patch or I'll have to scrap this DC, install the old version from scratch, and then re-authenticate all the workstations...

I'm in dire straights....

What do they need from me to help fix it? :P

---

### Post by Morbius1 on 2016-04-22
That's above my pay grade I'm afraid. You can add your "me too" to the ubuntu bug report if you want: [URL="https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572824"]Samba Domain Member cannot check passwords against Samba AD DC after "Badlock" update 

[/URL]
[h=1][/h]

---

### Post by davehenson on 2016-04-23
Well at least there's misery in company.  I noticed this when I had 15.10 and figured since it was broke then I'd just do a fresh install of 16.04.  Now I see its also broken in 16.04.  Looking forward to the fix!


Looks like samba is borked all over. This seems to be the primary bugzilla bug [https://bugzilla.samba.org/show_bug.cgi?id=11841](https://bugzilla.samba.org/show_bug.cgi?id=11841)

---

### Post by Martin_Finnemann on 2016-04-24
Found a fix. Reinstalled ubuntu 15.10 from scratch and turned off software updates. Both in the installation and after. Works like a charm. Just seems kind of stupid, no offense developers, to do software updates which deminishes the possibilities of the system. And furthermore release a new version 16.04 where the problem has not been rectified... Besides that, I really like Ubuntu...:D

---

### Post by hivar on 2016-04-29
I have fresh install of Xubuntu 16.04 and the problem persist. Anyone have a solution or workaround? The main goal for me is add an Windows printer.

---

### Post by Morbius1 on 2016-04-29
See if this works for your printer:

Stop cups:
```
sudo service cups stop
```
Edit the printer config file:
```
gksu gedit /etc/cups/printers.conf
```
Modify the printers URI and insert "guest@" before the host name of the Windows machine like this but with existing values for xxx and yyy:
```
 DeviceURI smb://guest@xxxx/yyyy
```
Then save the file and restart cups:
```
sudo service cups start
```

---

### Post by Nahuel_ on 2016-04-29
> **Morbius1 said:**
> See if this works for your printer:

Stop cups:
```
sudo service cups stop
```
Edit the printer config file:
```
gksu gedit /etc/cups/printers.conf
```
Modify the printers URI and insert "guest@" before the host name of the Windows machine like this but with existing values for xxx and yyy:
```
 DeviceURI smb://guest@xxxx/yyyy
```
Then save the file and restart cups:
```
sudo service cups start
```

Unfortunately, that didn't work for me. It still seems to ask for authentication. Weirdly though, in Ubuntu's printer configuration window, if I go to the printer's properties, the URI shows without @guest, but it's there in the file. 

[IMG]http://upload.nahueljose.com.ar/uploads/1461945457_screenshot-from-2016-04-29-12-55-41.png[/IMG]

---

### Post by Morbius1 on 2016-04-29
But if you just hit enter when it asks for credentials does it not connect?

---

### Post by Nahuel_ on 2016-04-29
> **Morbius1 said:**
> But if you just hit enter when it asks for credentials does it not connect?

It doesn't ask for credentials. If I right-click there and go to "authenticate" it asks for password using my username as default. No matter what I try (guest and no password, no user no password, my user my password, my user no password, etc.) nothing happens. It shows that error again.

 In printer status, it shows:
```
Idle - Tree connect failed (NT_STATUS_ACCESS_DENIED)
```

Which is the error smbclient shows when trying to access shares.

---

### Post by hivar on 2016-05-03
> **Morbius1 said:**
> But if you just hit enter when it asks for credentials does it not connect?

In my case it ask for credentials but nothing work, even if I just hit enter.

---

### Post by davehenson on 2016-05-03
I believe this might be the primary Ubuntu issue in their bug databas (Launchpad).  I encourage everyone to go there and add pressure to get this fixed!  

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572876](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572876)

Looking at samba.org, its already fixed upstream so we're just waiting on Ubuntu to package it.

Mod edit: the proper way to "add pressure" is to sign up with Launchpad and then tick the "affects me too" box. Please don't add comments if you have no new information to add.

---

### Post by Nahuel_ on 2016-05-04
They did a regression today:
[http://www.ubuntu.com/usn/usn-2950-2/](http://www.ubuntu.com/usn/usn-2950-2/)

```
sudo apt-get upgrade
``` to install the update. 

Didn't fix the problem in my case. I still can't access the windows shares.

-edit-
Spoke too soon. I entered my password (for my Ubuntu user) and it opened the server shares. Printer works, windows shares work, it's all good.

:)

---

### Post by davehenson on 2016-05-04
> **Nahuel_ said:**
> They did a regression today:
[http://www.ubuntu.com/usn/usn-2950-2/](http://www.ubuntu.com/usn/usn-2950-2/)

```
sudo apt-get upgrade
``` to install the update. 

Didn't fix the problem in my case. I still can't access the windows shares.

-edit-
Spoke too soon. I entered my password (for my Ubuntu user) and it opened the server shares. Printer works, windows shares work, it's all good.

:)


I ran the ```
update-manager
```, accepted the update (noticed it was the samba one mentioned) and then rebooted for good measure. I cannot still connect to my samba share. Although in my instance I have a share set up on my network with the username of "readonly".  Of course I do not have a user on my Ubuntu system with the name "readonly".  I also ran ```
sudo apt-get upgrade
``` as well, accepted another patch and rebooted again. Still no luck. 

Would the fact that my share username is different than my Ubuntu username have any difference?  It would seem not but I'm wondering now.



To add, I just checked to verify that the update was applied and it appears its there.  

I ran dpkg -s samba-libs and it returned the Version 2:4.3.9+dfsg-0ubuntu0.16.04.1.  My OS is 16.04.

---

### Post by bab1 on 2016-05-04
[QUOTE= davehenson]I have a share set up on my network with the username of "readonly". [/QUOTE]  What the heck does this mean?   Shares themselves don't have usernames.  Files and directories have user user or user-group ownership and permissions, not shares.

> Would the fact that my share username is different than my Ubuntu username have any difference?Any misconfiguration can cause you problems.  I don't think your problem is related to the OP.  You should start your own thread.  Describe *your* problem and provide examples.

---

### Post by davehenson on 2016-05-04
> **bab1 said:**
> What the heck does this mean?   Shares themselves don't have usernames.  Files and directories have user user or user-group ownership and permissions, not shares.

Any misconfiguration can cause you problems.  I don't think your problem is related to the OP.  You should start your own thread.  Describe *your* problem and provide examples.


Sorry. I'll explain a little and then maybe start my own thread. I didn't want to since this is the same issue only I'm using 16.04 and the OP is using 15.10.

to explain, I have a home router with a USB drive attached. within the router you can set up samba shares with any username you like.  I have some folders that I share with a username (admin) that has full permissions, and another user named (readonly) who has....readonly permissions.  I could have named the user (potato) but wanted to keep it simple. 

The router setup has worked flawlessly for several years and has no issues with windows attaching or Linux (prior to the samba snafu update that caused everyone issues). Since this is the same issue, should I still start another thread?  I can, I just didn't want to add clutter with a duplicate.

---

### Post by bab1 on 2016-05-04
> **davehenson said:**
> Sorry. I'll explain a little and then maybe start my own thread. I didn't want to since this is the same issue only I'm using 16.04 and the OP is using 15.10.

to explain, I have a home router with a USB drive attached. within the router you can set up samba shares with any username you like.  I have some folders that I share with a username (admin) that has full permissions, and another user named (readonly) who has....readonly permissions.  I could have named the user (potato) but wanted to keep it simple. 

The router setup has worked flawlessly for several years and has no issues with windows attaching or Linux (prior to the samba snafu update that caused everyone issues). Since this is the same issue, should I still start another thread?  I can, I just didn't want to add clutter with a duplicate.

So you mean the share name is [admin] or [readonly]?  This is not a duplicate problem.  You are not the OP and your problem does not appear to be the same as the OP.   Open a new thread for your problem.  FWI, it appears that the Samba *server* you are referring to is on the router.  You are only using the Samba *client* on your Ubuntu machine.

---

### Post by davehenson on 2016-05-04
> **bab1 said:**
> So you mean the share name is [admin] or [readonly]?  This is not a duplicate problem.  You are not the OP and your problem does not appear to be the same as the OP.   Open a new thread for your problem.  FWI, it appears that the Samba *server* you are referring to is on the router.  You are only using the Samba *client* on your Ubuntu machine.

Bingo! Yes I am using the client.  I'll open a new thread.

---

### Post by Alex_TNT on 2016-05-05
I managed to make it work by installing a fresh copy of ubuntu. Did all the update/upgrade and it still requested for my username and password 
It did work by adding the username of the share in my case the default between windows pc is `Everyone` and adding the password for my current ubuntu platform
it may ask you again for a password, leave it blank if doesn't work type your Ubuntu password again.

TLDR :
Windows Share Username = Everyone
Ubuntu Password =
Check Forever

---

### Post by taouk on 2016-05-10
It has been fixed. Samba was updated. Now you can connect to the windows shared folder using your username and password (for your account in your pc)

---

### Post by mirankajin on 2016-05-22
> **taouk said:**
> It has been fixed. Samba was updated. Now you can connect to the windows shared folder using your username and password (for your account in your pc)

you mean username and pass that you use to login into your windows computer? or which username and pass?
what if i dont use password in my win7 comp?

---

### Post by Morbius1 on 2016-05-22
> **mirankajin said:**
> you mean username and pass that you use to login into your windows computer? or which username and pass?
what if i dont use password in my win7 comp?
The original bug reporter noticed an odd anomaly after samba released 4.3.9 to fix the bug. From the bug report: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572876](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572876)
> [TABLE]
[TR]
[TD][greg (xeon-greg)]("https://launchpad.net/%7Exeon-greg")             wrote             on 2016-05-05:[/TD]
[TD="class: bug-comment-index"]           [ #27]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572876/comments/27")[/TD]
[/TR]
[/TABLE]
                               no need to use
client use spnego = no
client ntlmv2 auth = no
client ipc max protocol = NT1
 [COLOR=#0000cd]for UNprotected share just use your local ubuntu account credentials (login and password)[/COLOR]
for protected share use credentials that was set on share-host machine




When asked for credentials on the Linux machine for an "unprotected" Windows share you pass your linux user name and password.

*** Does that make any sense? 
No it does not. 
*** Why doesn't selecting "anonymous" when asked work as it does when connecting to a Linux box?
I do not know.
*** Would it work just as well if you were to pass the user name of guest with a non null password ( like selecting the space bar )?
I have no idea.

There's is no way for me to test any of this since I don't create guest accessible shares on Windows machines. I don't even understand the concept of not requiring a user name and password to log into a Windows machine or any computing device so there is no way for me to see if guest / non-null would work. 

I do know that a mount.cifs connection specifying guest appears to work as it always has so this peculiar anomaly suggests either an smbclient ( actually a libsmbclient ) thing, a gvfs thing, a miscommunication between gvfs and smbclient thing. or some other .. um ... thing.

---

### Post by mirankajin on 2016-05-22
> [COLOR=#0000cd]for UNprotected share just use your local ubuntu account credentials (login and password)[/COLOR]
yes, it works:
but!
you have to use username and password that you are not using anywhere:
lets say that my username on my win7 machine is "bob" , and i use no password on my win 7 machine
and
my username at my ubuntu machine is "robert" and my password is "tooth"
then
to authenticate it will only work if i use username that is not equal to "bob" or "robert" but i have to invent some other name for occasion, lets say "monkey"
and
password needs to be NOT EQUAL TO "tooth"
lets say i invent a pass "yuckie"

only then it will work!

which makes no sense at all  :confused:

but it works

---

