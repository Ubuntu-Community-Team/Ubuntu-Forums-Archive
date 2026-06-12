---
title: "Can see, but can't access, WinXP network"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by jhmiller42 on 2008-05-06
My network connection through my router works fine, internet connection is good, and I can see my existing WinXP network in Ubuntu's File Browser, but when I click the network's icon it "thinks" about it for 30-60 seconds and then displays an empty folder.

Weirdly, under 'Windows Network' in File Browser, it lists both my existing WinXP network and 'MSHOME', the default name for Windows networks -- though no such network exists. Also, my Ubuntu system is apparently included under MSHOME.

Any pointers? I'm on Hardy, BTW.

---

### Post by renzokuken on 2008-05-06
You need to set up **Samba** to share files between XP and Linux.....have a look in the wiki or just google "samba + ubuntu", there ae tons of guides

---

### Post by kg4wih on 2008-05-06
I'm having the same problem, I'm sure its something simple..... But when I was using 7.10 it would ask for my credentials but not anymore. And I never setup Samba, I thought it was just for sharing files with windows machines.


forgot this........ if you know the share/folder name, and your looking at the "empty folder" as you mentioned, click the button under the "back button" that toggles the text based location bar and add the share/folder name after the "/".....

or just enter the full address "smb://servername/sharename"

it will ask for you credentials then.....

---

### Post by Fraoch on 2008-05-06
Hmm, I'm seeing the same thing after upgrading from 7.10 to 8.04.  The 8.04 machine can't see my Windows laptop or my other 7.10 machine.

At first I thought I needed to reconfigure samba, but my smb.conf hasn't changed and the big sign that samba is working properly is that the Windows XP Pro laptop can see the 8.04 machine's shares just fine.  But not the other way around...

The symptoms are the same as the OP, which is why I'm posting in this thread.    Places - Network "thinks" for 20-30 seconds before even displaying (I thought it wasn't working at all first).  It displays "WORKGROUP" pretty quickly, which is indeed the name of my workgroup, but on clicking WORKGROUP it thinks for ~30 seconds and ends up with an empty screen devoid of all shares.  If I try to connect to the server name with "smb://server/share" it does the same, thinks then an empty folder.

Oddly a share on the 7.10 machine I have mounted via CIFS on the 8.04 machine appears just fine?  But I can't browse to the 7.10 machine's shares on demand.

---

### Post by renzokuken on 2008-05-07
have you added a samba login credentials

```
sudo smbpasswd -a *username*
``` then enter a password

---

### Post by Fraoch on 2008-05-07
Thanks for the help.  I followed this guide:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

and yes, I used:

```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```

as recommended in the guide.

I'm wondering if the smb.conf file in the article needs to be changed for Hardy?

Some progress though, I managed to get the 7.10 share to appear once by entering the server and share name, I can sometimes get to it but often it times out.  I can't browse to it though and it doesn't always come up.  I should be able to add the Windows XP laptop the same way but I never had to do it this way before and it's not very reliable.

---

### Post by SonicSteve on 2008-05-07
Did following the stuff above really work? In the past ie. Gutsy, Feisty etc. I could always see computers and shares before tweaking anything. 

Currently I can see the computers in the Network, I just can't see the root shares. If I add the path of the share to the address bar I can browse the share. 

for instance. 
We have a server called Jehu 
It has about 40 shares in it's root. When I browse the Network shares and I click on Jehu I get an empty window. If I then add the name of the share I want it then opens that share and is accessible. This can all be done before doing any of the above Samba setup guides. Those guides help make your files accessible to a windows computer. It used to be that by default a windows share was accessible without any tinkering at all. This new behaviour seems more like a change in Samba policy or a bug.

I've seen this behaviour both in fresh installs of hardy and from upgrades from Gutsy.

---

### Post by jhmiller42 on 2008-05-07
So, more folks having a similar problem. If anybody can figure out why we can't browse the network, it'd be much appreciated. Heck, I don't even need to serve files to other computers on the network, just need to read/write files on my WinXP desktop from my Ubuntu laptop.

---

### Post by SonicSteve on 2008-05-07
> **jhmiller42 said:**
> So, more folks having a similar problem. If anybody can figure out why we can't browse the network, it'd be much appreciated. Heck, I don't even need to serve files to other computers on the network, just need to read/write files on my WinXP desktop from my Ubuntu laptop.

Have you tried typing into the address bar of Nautilus?
smb://computer/sharename  ie substitute computer and sharename for you your xp machine and sharename.

When I do this I can see the shares and access the files, it's just browsing the shares that doesn't work. I should also add to this that sharing files through the Ubuntu share gui is not working very well right now.

---

### Post by jhmiller42 on 2008-05-08
I can't even get that working. It tells me it "failed to mount the Windows share." The network works properly when I dual-boot into XP, so I don't think I've configured the Windows computers in any unusual way.

Just out of curiosity's sake, are network addresses case-sensitive? I've tried both ways, no luck.

> **SonicSteve said:**
> Have you tried typing into the address bar of Nautilus?
smb://computer/sharename  ie substitute computer and sharename for you your xp machine and sharename.

When I do this I can see the shares and access the files, it's just browsing the shares that doesn't work. I should also add to this that sharing files through the Ubuntu share gui is not working very well right now.

---

### Post by SonicSteve on 2008-05-08
> **jhmiller42 said:**
> I can't even get that working. It tells me it "failed to mount the Windows share." The network works properly when I dual-boot into XP, so I don't think I've configured the Windows computers in any unusual way.

Just out of curiosity's sake, are network addresses case-sensitive? I've tried both ways, no luck.

I'm honestly not sure. I doubt that shares from a windows machine would be. However I think that Unix shares likely would be.

EDIT
I was doing some tinkering and I noticed that somehow my the default workgroup was set to "workgroup" with that setup I again could see but not browse the shares. After changing the workgroup back to "mshome" and then restarting samba, and networking (restarting the computer is probably the easiest way to do this) everything was working properly again.

So tomorrow at school I'll try setting the domain name and changing the workgroup names. I'll let you now how it goes.


Edit Friday after school,
Tried the above ideas and it made no difference.

---

### Post by SonicSteve on 2008-05-12
OK I just want to confirm that in a fresh install of Gutsy Gibbon 7.10 I can see the domain Shares, I can browse them, I then get prompted for Authentication, at which point I can access them. This is all without any modifications except to the IP addressing. Which I did to Hardy Heron also. I haven't installed Samba or smbfs.

Something has happened in Hardy Heron 8.04. I had to reinstall gutsy because this is my office WS. I just can't spend all day tinkering and trying new things. So Gutsy it is for now. Hardy Heron actually gave me quite bit of trouble on my office Workstation. Update manager kept freezing, I kept getting an annoying terminal error every time I used sudo. It doesn't seem like it should have been released yet.

---

### Post by jhmiller42 on 2008-05-13
Yeah, I've had way too many problems with 8.04, but then again, I have no idea how many of those are owed to my screwy hardware rather than Hardy.

So nobody's worked out yet why some of us can't access Windows shares, even by entering the network address manually?

---

### Post by Malfet on 2008-05-14
Exactly same problem for me, guys.
When I try to access the server from Hardy I get an "empty folder", but once I just add the path of the share to the address bar I can browse it without problem.
And that is an **Hardy problem**. I have few computer updated from Gutsy to Hardy and few not updated yet. Gutsy is working as was working before. Windows server immediately asks for login and pass and all sharing is fine, but not in Hardy. Hardy does not ask and display an empty folder, since I can add a path and get it to work then I presume Samba is OK. 
So, we have a question to solve "How to solve this Hardy bag"??? 
Honesyly, I don't want to downgrade now all Hardy computers...

---

### Post by Fraoch on 2008-05-14
I upgraded another PC to Hardy last night and it's behaving exactly the same as my first.

I'm beginning to think that the smb.conf posted here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) just doesn't work for Hardy.

I might try reinstalling samba and overwriting smb.conf, but I don't want to break the one thing that is working, Windows writing and viewing of Ubuntu shares.

---

### Post by SonicSteve on 2008-05-14
> **Fraoch said:**
> I upgraded another PC to Hardy last night and it's behaving exactly the same as my first.

I'm beginning to think that the smb.conf posted here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) just doesn't work for Hardy.

I might try reinstalling samba and overwriting smb.conf, but I don't want to break the one thing that is working, Windows writing and viewing of Ubuntu shares.

I installed a "fresh" from hardy repositories smb.conf file and it behaved exactly as the upgraded from Gutsy smb.conf file did.

---

### Post by SonicSteve on 2008-05-14
> **jhmiller42 said:**
> Yeah, I've had way too many problems with 8.04, but then again, I have no idea how many of those are owed to my screwy hardware rather than Hardy.

I love Ubuntu and to this point I have tried it quite a few different hardware platforms. I've seen problems with hardware not working quite right like USB or wireless. I've haven't seen anything like Update manager freezing or sudo errors till now though. I know it's working for some people but I've run 8.04 HH now on two or 3 different hardware platforms and 2 of the three have had weird quirks.

---

### Post by Fraoch on 2008-05-14
Overall I have to admit that 7.10 -> 8.04 was the best upgrade by far for me.  The worst was 6.10 - 7.04 on one PC, it trashed the system and I had to reinstall from scratch.

I've gone from 6.04 - 6.10 - 7.04 - 7.10 - 8.04.  Most of these upgrades broke many, many packages, required days of reconfiguration, etc.  But 7.10 - 8.04 has been the best for me yet (about 15 minutes of reconfiguration!) apart from this file sharing/networking error and an odd drive reassignment that popped up today:

[http://ubuntuforums.org/showthread.php?t=793995](http://ubuntuforums.org/showthread.php?t=793995)

On that new upgrade I did manage to see the samba shares but as before, not through Network.  I had to force it using "Connect to Server..." and try several times, first it said it didn't know how to open the smb://[server IP] file, then it said it was already mounted.  When I did connect to it, I added it as a bookmark in Network.  Now it has an entry in Places.  This is the same as the first PC.  So I guess it works but it's a kludge and Network does not work.

---

### Post by compgeek83 on 2008-05-14
I'm having the same issue, installed Hardy saturday and started playing with it on monday, was able to browse and authenticate to windows shares but oddly today I'm unable to do that. I dont think I tried yesterday at all from Ubuntu itself.

I have XP running in VirtualBoxon this Ubuntu machine for running Quickbooks and I am able to browse and authenticate to another XPPro box acting as a server with no problems.  That was working Monday, Tuesday and is still working today.

Any ideas? I assume I'm facing the same problem as everyone else?

---

### Post by compgeek83 on 2008-05-14
ok, I've found a work-around from someone else's non-related problem in another thread, install Konqueror, it browses the windows shares perfectly.... so it may be a Nautilus issue....

---

### Post by SonicSteve on 2008-05-14
> **compgeek83 said:**
> ok, I've found a work-around from someone else's non-related problem in another thread, install Konqueror, it browses the windows shares perfectly.... so it may be a Nautilus issue....

I had this suspicion myself. I guess it's still unconfirmed but that seems like pretty good evidence.

---

### Post by Malfet on 2008-05-15
> **SonicSteve said:**
> I had this suspicion myself. I guess it's still unconfirmed but that seems like pretty good evidence.

No, looks like that's a clear bug in gvfs
[http://ubuntuforums.org/showthread.php?t=762525&page=2](http://ubuntuforums.org/showthread.php?t=762525&page=2)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

---

### Post by Skeorx13 on 2008-05-15
I'm having a similar problem but just the opposite. I could not get my XP system to access the Ubuntu system. When using Gutsy I couldn't even see the Ubuntu system on the network on my XP system or even itself (in the places/network). I tried a lot of things but nothing would even show it over the network. I upgraded to Hardy and now both systems can see the Ubuntu system over the network but only the Ubuntu system can access the shares. The XP system can see it but when I try to access it in file manager I get this error: 
"//blah-desktop server (Samba, Ubuntu) is not accessible. You might not have permission to access this resource. Contact the administrator of this server, blah blah

The parameter is incorrect."

Nautilus lists the shares correctly and adds the ones I pick but when I try to share a folder in my ntfs hard drives (dual booting on the Hardy system) it won't share them and says the share name is too long (even when it is only three letters long) and even when it isn't I get a "Could not change permissions" error. Now on my Hardy system I can see the XP system and transfer files to the Hardy system with no problems what so ever. I've never had a problem with transferring this way (XP->ubuntu) only the other way around. I just don't get why it is so hard...

---

### Post by Jamikest on 2008-05-17
i just upgraded to 8.04(Kubuntu) and lost samba access. Found that opening a window to browse in Dolphin as ROOT, I could then access my windows network. Still cant get into it using my normal dolphin.

---

### Post by SonicSteve on 2008-05-21
> **Malfet said:**
> No, looks like that's a clear bug in gvfs
[http://ubuntuforums.org/showthread.php?t=762525&page=2](http://ubuntuforums.org/showthread.php?t=762525&page=2)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)


Yep,
Based on the previous post about Dolphin I'd have to fully agree. I did anyway but now we see that clearly nautilus is not the issue.

---

### Post by jesrani on 2008-05-22
I have a similar problem, accessing Win98 network and I have posted this here
[http://ubuntuforums.org/showthread.php?t=803025](http://ubuntuforums.org/showthread.php?t=803025)
Can anyone please reply on that post.

---

### Post by Gramps on 2008-05-26
I didn't do an upgrade but a fresh install, was running 6.10 and I don't like updating from one version to another, had paroblems in the past doing this.

Installed Hardy 8.04 and could not access the shares on my Windows machines. I could browse to the machine itself but couldn't see any shares. By reading some of the other post in the forums I can across a work around that works. In the location bar type smb://<server ip_address> then a screen popped up asking for username and password, clicked remember forever as this is at home and I am the only one using it. NOw I have a list of the shares that are available on the machine. Clicked the one I wanted and now I can browse.

To make it easier I used Bookmarks/Add Bookmark now if I want to got to a share I just use the Bookmarks.

Works for me, you milage may very

---

### Post by ZeusABJ on 2008-05-28
So sorry to come in on the tail end of this conversation, but I'm having the exact same issues with the windows shares as you guys. Did anyone come up with a viable workaround?

---

### Post by A$h X on 2008-05-29
There is no workaround, accessing windows networks from hardy is borked. 
Worked fine in gutsy too, if it ain't broke then don't fix it.

The response time from clicking on a workgroup name and it being displayed is ridiculously long. You are much better typing the machine's IP into nautilus the form of smb://IP.address.goes.here
But once your shares appear, don't think you can cut and paste files into them! Oh no, that's too convenient for us, you must drag'n'drop your files into the share.

Seriously, what the hell were the dev's thinking when they tinkered with samba in hardy?

---

### Post by bushwacker on 2008-05-31
Here are some other interesting symptoms. Tell me if You've had this one:

I can browse my workgroup through the CUPS SMB printer add dialog box (only shows printer resources), but not through anything else, including smbc, which is a Midnight Commander like SMB browser in curses. I can print, but only sometimes, and it takes dozens of minutes when it does do it. This is all while having iptables disabled...

---

### Post by jhmiller42 on 2008-06-04
I can confirm that entering the server's IP address works. Any ideas why we can't identify the root problem if such a simple workaround does the trick?

---

### Post by sea_monkey987 on 2008-06-04
Hey guys.  I'm relatively new to Ubuntu, so I don't know exactly what the problem is here (i.e. why this won't work in Hardy if it does in Gutsy).  Anyway, I have found a solution that works for me.

First let me describe the problem I had because there are various problems posted in this thread with little varying details.  I could type in smb://IPADRESS/ to view my windows xp shares.  I could click on windows network and even enter the MSHOME workgroup.  After this though, things used to go awry.  Sometimes, I had all my logged on computers listed.  Sometimes I didn't.  Although, I could NEVER double click on one to view its shares.  The sole exception was viewing the samba shares of my own ubuntu machine from the MSHOME workgroup.  Also, I could not do smb://netbios-name/ to view the computers' shares - I was forced to use an IPADRESS.

EDIT: I seem to have left out the fact that I have "samba" installed.  I tried this on a fresh install without installing samba and it didn't work.  So, - in short - install samba also.

Step 1)
To solve it simply go to [http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

This guy has posted a simple HOWTO to convert the netbios name of a computer (known as the 'Computer Name' in windows) to an ipaddress.  For me pinging was very sluggish with the netbios name after this procedure; nevertheless it worked.  BTW, I restarted my computer after the install winbind procedure just to be safe :).
[COLOR="Red"]EDIT:  Note - as dmizer pointed out, wins should be before dns.
[/COLOR]
P.S. my /etc/nsswitch.conf file did not orginally read
       hosts: files dns
instead it was 
       hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
so, I created a backup of the file and changed the line to
       hosts: files wins dns mdns4
Thankfully, nothing seems to be broken after an hour or so ;)

Also, go to Places > Computer now.  Type 'smb://netbiosname/' (replace netbiosname with an actual name) and check to see if it works.  DON'T TRY DOUBLE-CLICKING FROM THE PLACES > NETWORK GUI YET.  This is just to double-check that netbios name resolution works.



Step 2)
Next, go to the /etc/samba/smb.conf file with your favorite editor.  The default samba file will read a line
;     wins support = no
Remove the semi-colon (to uncomment it) and change no to yes.

That's it!  Restart the samba service by "sudo /etc/init.d/samba restart"  Now go to Places > Network.  The computers should be listed inside your workgroup and double-clicking on them should work.  If it doesn't, restart your comp. one more time (sorry: windows convert talking here).

Sorry for the long post.  I just wanted to be detailed and specify my experience since I really don't know why this doesn't already work in Hardy.  Out of curiosity, can somebody explain to me why i had to do step 2.  Like I said above, I could use smb://netbiosname after step 1.  It just still wouldn't work my listing the computers in MSHOME.  Also, for me this works in both konqueror and nautilus. :)

---

### Post by jhmiller42 on 2008-06-04
Another wrinkle: I figured, since I can finally access the network by using the IP, I'd try to set up my network printer, which is hooked up to my WinXP desktop.

I started up the "add new printer" dialog, and whaddaya know, I could browse right to the network printer. So at least some apps can browse the network.

Which isn't to say the printer works. It doesn't, of course. I mean, this is Ubuntu we're talking about, after all. What would a Hardy setup be without dozens of hours of head-bangingly frustrating bugs and incompatibilities?

---

### Post by Skeorx13 on 2008-06-10
Took me forever to find it but all I had to do was put 
"guest ok = yes" in one of the shared directory entries in the smb.conf file and restart samba and it works perfectly. So stupid...

---

### Post by SonicSteve on 2008-06-27
> **sea_monkey987 said:**
> Hey guys.  I'm relatively new to Ubuntu, so I don't know exactly what the problem is here (i.e. why this won't work in Hardy if it does in Gutsy).  Anyway, I have found a solution that works for me.

First let me describe the problem I had because there are various problems posted in this thread with little varying details.  I could type in smb://IPADRESS/ to view my windows xp shares.  I could click on windows network and even enter the MSHOME workgroup.  After this though, things used to go awry.  Sometimes, I had all my logged on computers listed.  Sometimes I didn't.  Although, I could NEVER double click on one to view its shares.  The sole exception was viewing the samba shares of my own ubuntu machine from the MSHOME workgroup.  Also, I could do smb://netbios-name/ to view the computers' shares - I was forced to use an IPADRESS.

Step 1)
To solve it simply go to [http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

This guy has posted a simple HOWTO to convert the netbios name of a computer (known as the 'Computer Name' in windows) to an ipaddress.  For me pinging was very sluggish with the netbios name after this procedure; nevertheless it worked.  BTW, I restarted my computer after the install winbind procedure just to be safe :).

P.S. my /etc/nsswitch.conf file did not orginally read
       hosts: files dns
instead it was 
       hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
so, I created a backup of the file and changed the line to
       hosts: files wins dns mdns4
Thankfully, nothing seems to be broken after an hour or so ;)
Also, go to Places > Computer now.  Type 'smb://netbiosname/' (replace netbiosname with an actual name) and check to see if it works.  DON'T TRY DOUBLE-CLICKING FROM THE PLACES > NETWORK GUI YET.  This is just to double-check that netbios name resolution works.



Step 2)
Next, go to the /etc/samba/smb.conf file with your favorite editor.  The default samba file will read a line
;     wins support = no
Remove the semi-colon (to uncomment it) and change no to yes.

That's it!  Restart the samba service by "sudo /etc/init.d/samba restart"  Now go to Places > Network.  The computers should be listed inside your workgroup and double-clicking on them should work.  If it doesn't, restart your comp. one more time (sorry: windows convert talking here).

Sorry for the long post.  I just wanted to be detailed and specify my experience since I really don't know why this doesn't already work in Hardy.  Out of curiosity, can somebody explain to me why i had to do step 2.  Like I said above, I could use smb://netbiosname after step 1.  It just still wouldn't work my listing the computers in MSHOME.  Also, for me this works in both konqueror and nautilus. :)

Has anyone tried Sea_monkey987's idea? I just came back to this thread after dealing with other things. I've been testing this bug from time to time after each update and on any Hardy machine the bug is there. I don't understand why after 2 months this hasn't been fixed yet. This a fairly major bug.

---

### Post by Chipesh on 2008-06-28
I have been messing around for months with this. Tried the above and it WORKS! I can now browse Vista and XP shares from network.
You need a samba password ( "sudo smbpasswd -a <username>" use your login password ).

After a restart and time for it to find the network & keyring prompts it's  OK. This was in Mint Elyssa so it should work in 8.04.

I can't understand how this isn't better documented and/or easier to set up.

I had looked at "; wins support = no" and wondered. 

How many threads are there saying "install samba" and "make sure you have the same workgroup name in smb.conf"
.
Thank you very much sea_monkey987 
.
Bob

---

### Post by celem on 2008-06-28
I noticed that last night smbclient updates were downloaded and installed so I thought that I'd check to see if the Windows share issue had been fixed. Nope - still fails. Works if IP address is put into Natulis but fails with the graphical access.  I am not interested in Ubuntu hosting files for XP access, so I haven't installed samba - only smbclient is supposed to be needed to see Windows shares. I have in the past and it doesn't help this issue.

---

### Post by sea_monkey987 on 2008-06-28
> **Chipesh said:**
> I have been messing around for months with this. Tried the above and it WORKS! I can now browse Vista and XP shares from network.
You need a samba password ( "sudo smbpasswd -a <username>" use your login password ).

After a restart and time for it to find the network & keyring prompts it's  OK. This was in Mint Elyssa so it should work in 8.04.

I can't understand how this isn't better documented and/or easier to set up.

I had looked at "; wins support = no" and wondered. 

How many threads are there saying "install samba" and "make sure you have the same workgroup name in smb.conf"
.
Thank you very much sea_monkey987 
.
Bob

I'm glad it worked for you.  For me, this is becoming ever more perplexing.  I talked to a person who says that he can browse windows shares by just using the default Hardy installation.  On top of that, my ubuntu box's listing under the Places > Network window is gone when trying to view from said box's interface (however, I can still browse the box's shares from any computer).  Can anybody confirm if in a network running multiple ubuntu computers, the linux computers are listed under Places > Network using only samba file sharing?  To add more to the confusion, my ubuntu box is listed and can be browsed fine from an xp computer.

---

### Post by Chipesh on 2008-06-28
I have never been able to browse Windows shares with a default 8.04 install.
I have just repeated the above on another up to date 8.04 ( not mint ) install and it worked. However I didn't modify the nsswitch.conf file, although it seems more reliable with this and each "server" appears on its own as well as under "windows network".
.
I have a fresh Elyssa install elsewhere on the network and I can't see this machine's shares from that.Though I can see shares on that from this (modified) one.
.
Also in 8.04 the default user (admin) can't share files on the network
Administration /users and groups/user settings/properties/user privileges/share files with the local network
'
Seems this is all too restrictive to me.:confused:
Bob

---

### Post by sea_monkey987 on 2008-06-28
> **Chipesh said:**
> I have never been able to browse Windows shares with a default 8.04 install.
I have just repeated the above on another up to date 8.04 ( not mint ) install and it worked. However I didn't modify the nsswitch.conf file, although it seems more reliable with this and each "server" appears on its own as well as under "windows network".
.
I have a fresh Elyssa install elsewhere on the network and I can't see this machine's shares from that.Though I can see shares on that from this (modified) one.
.
Also in 8.04 the default user (admin) can't share files on the network
Administration /users and groups/user settings/properties/user privileges/share files with the local network
'
Seems this is all too restrictive to me.:confused:
Bob

Well, my own solution seems to be half broken for me.  This is after I did a fresh install and updated everything and then applied my solution.  Although, I have tried this on a fresh install numerous times and it has worked, so I'm assuming a latest update killed it.  I just hope I can fix it.  As far as the admin sharing files, I'm not quite sure what you mean.  I edit the /etc/samba/smb.conf file to define file shares.  Make sure you add the user 'admin' as a samba user using
```
sudo smbpasswd -ae admin
```

and specifying a password.
I just remembered, make sure you have installed the 'samba' package otherwise filesharing will not work!  You'll only be able to 'see' other file sharing servers.

---

### Post by celem on 2008-06-29
Just because I've tried everything else in the past, I tried the solutions posted above by chipesh and sea_monkey987. I can ping the machine name but it is slow. Pinging just the IP is fast. No improvement with this fix for me. As before, I can only open the Windows XP shares if I use the IP instead of the machine name, meaning that the graphical route of Places->Network still fails.

This used to work so well in the past but it has been broken for me ever since an update in Dapper.

---

### Post by Chipesh on 2008-06-29
What I mean is that in 8.04 they have introduced the right click sharing options. As well as smb.conf and I have shared folders as well. I had to give authorization to share in "users and groups".
I have samba installed.

Most people are totally turned off by authorizations, keyrings and configuration files etc so I am trying to do things graphically.

It's still working fine for me
.
Bob

---

### Post by sea_monkey987 on 2008-06-29
> **celem said:**
> Just because I've tried everything else in the past, I tried the solutions posted above by chipesh and sea_monkey987. I can ping the machine name but it is slow. Pinging just the IP is fast. No improvement with this fix for me. As before, I can only open the Windows XP shares if I use the IP instead of the machine name, meaning that the graphical route of Places->Network still fails.

This used to work so well in the past but it has been broken for me ever since an update in Dapper.

I just did a fresh install and realized I also had install the "samba" package for the samba-server in order to get the Places > Network to work.  However, using
```
smb://IPADDRESS/
```
in nautilus also worked after installing winbind and enabling wins etc.  Pinging machine name is also slow for me.:confused:

---

### Post by cyrusmedora on 2008-07-03
I cannot add any constructive help on this issue, but I did just want to add my voice to the many who have expressed frustration about this problem. I dual boot at work (some of my legal software only works under Windoze) and would prefer to use Ubuntu as much as possible, but all my files are in a shared folder, which is hosted by a Win 2k3 box. Previous versions of Ubuntu had no problem auto-mounting the folder at startup, but now the best I can use is the old "smb//ip.add.re.ss/share name trick - rather frustrating though. 
Oh and before you ask - I have tried every fix and workaround that Mama Google has thrown my way.

---

### Post by alliance1975 on 2008-07-03
> **jhmiller42 said:**
> My network connection through my router works fine, internet connection is good, and I can see my existing WinXP network in Ubuntu's File Browser, but when I click the network's icon it "thinks" about it for 30-60 seconds and then displays an empty folder.

Weirdly, under 'Windows Network' in File Browser, it lists both my existing WinXP network and 'MSHOME', the default name for Windows networks -- though no such network exists. Also, my Ubuntu system is apparently included under MSHOME.

Any pointers? I'm on Hardy, BTW.

It's probably my dumb luck. My first deployment of Hardy and I had the same problem. Something weird though. My workgroup name had a space in it, (i.e. the dingles). Hardy showed the name as the%20dingles. I went in to all my winxp pcs and changed the workgroup to just plain dingles. I completely reloaded hardy and was finally successful in copying files from windows share files to my hardy laptop.

---

### Post by stevepb on 2008-07-07
Hi Guys,

Exactly the same issue, Can see windows domains/workgroups but cannot see the computers themselves in Hardy.

I have tried a myriad of different ways to fix the problem, but i'm just not getting anywhere after weeks of trying.

It's a bit embarrassing being the Head of IT where I work and I can't even print or transfer files correctly to windows machines from my HP DV9000 Hardy Laptop - everything is fine the other way around, next point of action is to figure out how to get my laptop to make me a coffee by pressing a button on the remote control, then i'm going to face the impossible task of getting Samba working :lolflag:. (AGAIN!)

I pray the Devs will find a permanent solution to this problem and provide it in an update soon. It seems every Hardy install I've come across suffers the same issues with samba.


I hope you all have some luck with this.

Steve

---

### Post by sea_monkey987 on 2008-07-07
> **stevepb said:**
> Hi Guys,

Exactly the same issue, Can see windows domains/workgroups but cannot see the computers themselves in Hardy.

I have tried a myriad of different ways to fix the problem, but i'm just not getting anywhere after weeks of trying.

It's a bit embarrassing being the Head of IT where I work and I can't even print or transfer files correctly to windows machines from my HP DV9000 Hardy Laptop - everything is fine the other way around, next point of action is to figure out how to get my laptop to make me a coffee by pressing a button on the remote control, then i'm going to face the impossible task of getting Samba working :lolflag:. (AGAIN!)

I pray the Devs will find a permanent solution to this problem and provide it in an update soon. It seems every Hardy install I've come across suffers the same issues with samba.


I hope you all have some luck with this.

Steve
So, my workaround didn't work for you?

---

### Post by wmf on 2008-07-07
> **sea_monkey987 said:**
> So, my workaround didn't work for you?
I have a somewhat similar problem with Hardy. I have tried numerous fixes, including Seamonkey's with out solving the problem. I will mention that samba worked perfectly as far as I know in Gutsy.

After configuring my smb.conf file to recognize our domain:
 ```
workgroup = <DOMAIN> 
```

and enabling the WINS support:
```
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
   wins server = <IP Address of WINS server>

```

I can browse to the shares using Nautilus. Then one of two things happens:
[LIST=1]
[*]If the share has unrestricted access, I can open or copy a file to the Ubuntu machine, but cannot write or copy back. This fails with a "You do not have adequate permissions. See your administrator" error message.
[*]If the share does have permissions, the contents will not even display accompanied by essentially the same error message. This includes shares that I have permissions on via Windows AD.
[/LIST]

I have tried everything the forums offer (I think) without success. I really don't want to backversion to Gutsy, but that might be my only option. 

[WHINE] It seems pretty unbelievable that the developers would release Hardy with known issues with Windows network shares. In my research on this issue, I have found bug reports going back to April and May (pre-release) that identify this type of problem. I suppose that based on the number of people NOT complaining, we are a pretty small part of the user base. Still, a Linux distro with Samba broken? [/WHINE]

---

### Post by Chipesh on 2008-07-08
There is an article in this months Personal Computer World (UK) about this, "Hardy Heron hassle", by their resident networking writer. His hope is that this would be resolved in 8.04.1 . I have just done a fresh install of that and it's the same. Apparently all this is supposed to be handled by "Gnome Virtual File System" without the need for additional software.

On my Elyssa System I can still browse the Windows share with the above fix but I can't now see the Linux shares from Windows !

Bob

---

### Post by oygle on 2008-07-09
I have similar problems, was able to see the XP computer with Gutsy, but after reformatting the HDD and installing Hardy, have not been able to use Nautilus to even see the XP network.

However, as soon as I installed Samba, I ran Firefox, and it was able (and still is) to see the XP network, either by IP address or computer name.

I did keep seeing a msg in logs, and at the terminal "unable to resolve host xxxx" , but found the solution at [http://ubuntuforums.org/showthread.php?t=723361&page=2](http://ubuntuforums.org/showthread.php?t=723361&page=2)  . It seems if you use the Network manager, it goes and adds a domain back in, great.

As I said, using Samba/nautilus with Gutsy worked fine. My setup is simple, I don't have any shares at all on Ubuntu, and only need to browse the XP network, and sometimes write files to the XP, from Ubuntu. This is usuallt a simple copy/paste in Nautilus.

I have read through this as well - [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) (not all, just a few pages at the start) , and even used backups from Ubuntu, from the Gutsy version, and compared the smb.conf file from Hardy, to see if I could pickup any potential problems.

I'm sure I have tried everything possible.

If I can browse/view files okay with Firefox, but not with Nautilus, surely the problem is Nautilus ??

Any clues please.  :confused:

---

### Post by oygle on 2008-07-09
I see from [http://www.mattcutts.com/blog/six-annoyances-in-hardy-heron-ubuntu/](http://www.mattcutts.com/blog/six-annoyances-in-hardy-heron-ubuntu/) , that a new package called 'nautilus-share' is required.

Will that fix the problem ?

---

### Post by oygle on 2008-07-09
Post #4 at [http://ubuntuforums.org/showthread.php?p=5343228#post5343228](http://ubuntuforums.org/showthread.php?p=5343228#post5343228) states ..

> 
GVFS and authenticated smb browsing

*The GVFS filesystem layer used in GNOME 2.22 does not support password authentication when browsing the list of shares on an SMB server, which can result in empty share lists in nautilus when connecting to Windows 2003 hosts in some configurations. Workarounds for this issue include:
-use Kerberos authentication with preconfigured Kerberos credentials (i.e., running 'kinit' in an Active Directory realm)
-connect directly to an individual share using smb://<server>/<share> as the target location 


So, in Nautilus, I tried 

smb://<server>/<share> , and was able to actually view the contents of the XP folder. It did ask me for a password though (Firefox can view/browse the same XP share, without a password).

Finally, it works (kinda).  :)

This **REALLY** needs to be a sticky in this forum, the workarounds to this problem with Hardy/Nautilus, try doing a search on Nautilus in all forums, and you will see the magnitude of this problem.

---

### Post by dmizer on 2008-07-09
> **sea_monkey987 said:**
> Hey guys.  I'm relatively new to Ubuntu, so I don't know exactly what the problem is here (i.e. why this won't work in Hardy if it does in Gutsy).
the problem is that hardy does not come configured with the smbfs module.  it uses cifs to connect to windows/samba shares.  cifs cannot resolve host names without a winbind server.

> **sea_monkey987 said:**
> First let me describe the problem I had because there are various problems posted in this thread with little varying details.  I could type in smb://IPADRESS/ to view my windows xp shares.  I could click on windows network and even enter the MSHOME workgroup.  After this though, things used to go awry.  Sometimes, I had all my logged on computers listed.  Sometimes I didn't.  Although, I could NEVER double click on one to view its shares.  The sole exception was viewing the samba shares of my own ubuntu machine from the MSHOME workgroup.  Also, I could not do smb://netbios-name/ to view the computers' shares - I was forced to use an IPADRESS.

Step 1)
To solve it simply go to [http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

This guy has posted a simple HOWTO to convert the netbios name of a computer (known as the 'Computer Name' in windows) to an ipaddress.  For me pinging was very sluggish with the netbios name after this procedure; nevertheless it worked.  BTW, I restarted my computer after the install winbind procedure just to be safe :).

P.S. my /etc/nsswitch.conf file did not orginally read
       hosts: files dns
instead it was 
       hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
so, I created a backup of the file and changed the line to
       hosts: files wins dns mdns4

note here:
the howto you linked is good except it shows that the nsswitch.conf file should read like so:
```
hosts: files dns [COLOR="Red"]wins[/COLOR]
```
however, it's very important to have wins placed before dns like so:
```
hosts: files [COLOR="Red"]wins[/COLOR] dns
```
unless this is done, the netbios name will not be resolved before dns, and the problem will still exist.

good for you for figuring this all out!

---

### Post by oygle on 2008-07-09
I see on the Nautilus homepage ( [http://www.gnome.org/projects/nautilus/index.html](http://www.gnome.org/projects/nautilus/index.html) ) they recommend the latest version of eel, which is version 2.23

However, when I searched for eel on Hardy, it seems the version is 2.22

Is this a problem ??  :confused:

---

### Post by dmizer on 2008-07-09
> **oygle said:**
> I have similar problems, was able to see the XP computer with Gutsy, but after reformatting the HDD and installing Hardy, have not been able to use Nautilus to even see the XP network.

However, as soon as I installed Samba, I ran Firefox, and it was able (and still is) to see the XP network, either by IP address or computer name.

I did keep seeing a msg in logs, and at the terminal "unable to resolve host xxxx" , but found the solution at [http://ubuntuforums.org/showthread.php?t=723361&page=2](http://ubuntuforums.org/showthread.php?t=723361&page=2)  . It seems if you use the Network manager, it goes and adds a domain back in, great.

As I said, using Samba/nautilus with Gutsy worked fine. My setup is simple, I don't have any shares at all on Ubuntu, and only need to browse the XP network, and sometimes write files to the XP, from Ubuntu. This is usuallt a simple copy/paste in Nautilus.

I have read through this as well - [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) (not all, just a few pages at the start) , and even used backups from Ubuntu, from the Gutsy version, and compared the smb.conf file from Hardy, to see if I could pickup any potential problems.

I'm sure I have tried everything possible.

If I can browse/view files okay with Firefox, but not with Nautilus, surely the problem is Nautilus ??

Any clues please.  :confused:

the purpose of the howto you linked is to allow ubuntu to share files to windows, not to allow ubuntu to browse windows shares.

you can browse with firefox but not nautilus because nautilus is using cifs.  you will need to follow step 1 under sea_monkey987's post here: [http://ubuntuforums.org/showthread.php?p=5115956#post5115956](http://ubuntuforums.org/showthread.php?p=5115956#post5115956) in order to resolve your problem.

step 2 is not necessary.

---

### Post by oygle on 2008-07-09
> **dmizer said:**
> the purpose of the howto you linked is to allow ubuntu to share files to windows, not to allow ubuntu to browse windows shares.


Oh, okay, thanks for clearing that up.

> **dmizer said:**
> 
you can browse with firefox but not nautilus because nautilus is using cifs.  you will need to follow step 1 under sea_monkey987's post here: [http://ubuntuforums.org/showthread.php?p=5115956#post5115956](http://ubuntuforums.org/showthread.php?p=5115956#post5115956) in order to resolve your problem.

step 2 is not necessary.

I'm 99% sure I have done all that was stated there (installed winbind and even restarted), however nothing has changed. I still can't copy a file from Ubuntu to XP, like I could before with Gutsy.

Under Nautilus, it won't show the XP shares under 'Places | Network' , however I can browse to it by entering in the netbios name under Nautilus. But browse is all I can do, not copy files over.

---

### Post by oygle on 2008-07-09
> **dmizer said:**
> the purpose of the howto you linked is to allow ubuntu to share files to windows, not to allow ubuntu to browse windows shares.


Are you saying that I should not have any need at all to modify smb.conf then ?  That I should leave it in it's original (post Hardy install) format ?

---

### Post by dmizer on 2008-07-09
> **oygle said:**
> Are you saying that I should not have any need at all to modify smb.conf then ?  That I should leave it in it's original (post Hardy install) format ?

no ... i just said that you're not addressing the problem by focusing your effort on smb.conf.

make a backup of what you have now (so you can return to it if necessary):
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-old
```

now, if you ONLY want to access shares on your windows computer, delete everything in it, and change it so it has the following lines:
```
[global]
    netbios name = UBUNTU_HOSTNAME
    workgroup = WINXP_WORKGROUP
```
change "UBUNTU_HOSTNAME" to whatever you've named your ubuntu computer, and "WINXP_WORKGROUP" should be changed to whatever the XP computer has listed as it's workgroup under control panel > system > computer name [tab]

reboot before testing.

if that doesn't work, take a look at the second link in my sig.

---

### Post by Minus_Fireal on 2008-07-09
You could try installing fusesmb, that fixed my slow network browsing.

---

### Post by celem on 2008-07-09
At least in my case, fusesmb is not even installed.

---

### Post by rickatnight11 on 2008-07-09
So, is there a working fix yet?  I have read through and tried most of what's posted in this thread, but I still can't browse the Windows network.  It appears in the Network window of Nautilus, and I can even see my own computer's workgroup, but none of the local machines pop up.  I can access them manually via IP address and share, but no browsing.  I guess it has to do with not being able to resolve the netbios names.

The samba server is working wonderfully.  Other machines can access my machine perfectly, and whatever package I installed to give me the Samba utility in the Administration menu is so easy and useful.  Kicks Windows' sharing's ***.

---

### Post by celem on 2008-07-09
There is no fix that I know of, and the developers may not even be working on a fix - at least they are silent on the issue. The problem is that this feature works for some people and not for others. I happen to be among the others.

---

### Post by oygle on 2008-07-09
> **dmizer said:**
> no ... i just said that you're not addressing the problem by focusing your effort on smb.conf.

make a backup of what you have now (so you can return to it if necessary):
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-old
```

now, if you ONLY want to access shares on your windows computer, delete everything in it, and change it so it has the following lines:
```
[global]
    netbios name = UBUNTU_HOSTNAME
    workgroup = WINXP_WORKGROUP
```
change "UBUNTU_HOSTNAME" to whatever you've named your ubuntu computer, and "WINXP_WORKGROUP" should be changed to whatever the XP computer has listed as it's workgroup under control panel > system > computer name [tab]

reboot before testing.

if that doesn't work, take a look at the second link in my sig.

Okay, thanks, I did all that (stopping & starting samba appropriately, and rebooting), however still no go at all in Nautilus. I checked the 'event viewer' in XP, and as far as XP was concerned, there were no probs with authentication, etc.

Nautilus just simply refused to be able to browse through the 'network' side of things, I could 'force' it to view the shares on XP, by using the location and smb://hostname/sharename/ , but it would only view, I could not copy a file over from Ubuntu to XP, and could not even open a file on an XP share, using Nautilus.

I did start to read the info in the second link, but it seemed to be for Samba shares (and the title was "Mount samba shares with utf8 encoding using cifs" ), and I have no need of a Samba share, only to use the XP shares, and copy backups, etc over to the XP.

Decided it was just not worth pursuing Nautilus anymore, then remembered using Konqueror years back, and I think it could browse Win shares. After the install, Konqueror would open okay, but if I tried any function, it just did nothing.  :)

Then installed smb4K, and as soon as I opened it, it had the workgroup name, and showed all the XP shares. It asked for a pwd, and then displayed the contents of the XP share in another window, running Konqueror.

Now I can browse any XP share, copy files from Ubuntu to XP, and even open files on the XP share (something Nautilus could never do). I also notice that by leaving the mouse pointed on a file on an XP share, it displays all the file info, and displays the file contents, ....... very nice.  :)

So, thanks very much for all your help on Nautilus/Samba. I'll be using smb4K/Konqueror though for accessing any XP shares.

---

### Post by dmizer on 2008-07-10
> **oygle said:**
> I did start to read the info in the second link, but it seemed to be for Samba shares (and the title was "Mount samba shares with utf8 encoding using cifs" ), and I have no need of a Samba share, only to use the XP shares, and copy backups, etc over to the XP.
the howto i linked was designed to allow you to mount windows shares (aka samba shares) from ubuntu.  so it would have allowed you to use the xp shares, copy backups and other files to xp.

> **oygle said:**
> So, thanks very much for all your help on Nautilus/Samba. I'll be using smb4K/Konqueror though for accessing any XP shares.
glad you got it working to your satisfaction.

---

### Post by rickatnight11 on 2008-07-10
> **oygle said:**
> Decided it was just not worth pursuing Nautilus anymore, then remembered using Konqueror years back, and I think it could browse Win shares. After the install, Konqueror would open okay, but if I tried any function, it just did nothing.  :)

Then installed smb4K, and as soon as I opened it, it had the workgroup name, and showed all the XP shares. It asked for a pwd, and then displayed the contents of the XP share in another window, running Konqueror.
Thanks for the tip.  I can now browse the network, but if I select any of the shares on my Vista machine it throws an error (with a very annoying breaking glass sound) that "mount error 2 = No such file or directory."  Any idea why that is?

---

### Post by sea_monkey987 on 2008-07-10
> **dmizer said:**
> 
note here:
the howto you linked is good except it shows that the nsswitch.conf file should read like so:
```
hosts: files dns [COLOR="Red"]wins[/COLOR]
```
however, it's very important to have wins placed before dns like so:
```
hosts: files [COLOR="Red"]wins[/COLOR] dns
```
unless this is done, the netbios name will not be resolved before dns, and the problem will still exist.

good for you for figuring this all out!

Thanks.  I will edit my original post accordingly.  Although, I did put wins before dns in my file.  Don't know why!

---

### Post by SonicSteve on 2008-07-31
Morning guys,

I'm hoping I can finally get this resolved. Just so you know I think this issue stems more from you're environment then it does from a hardware or machine specific problem. I could be wrong but here are my observations.

At home, workgroup environment,
My hardy heron laptop can see the XP machines and browse the shares 
PS I've tried countless different hardware setups, every hardy machine I've tried has this issue at my school, without fail!

At School, Domain environment, We use DNS not wins
My hardy workstation can see the XP machines, but can't see the root of the shares. I can browse the shares by adding a share name to the end of the path ie, smb://computename/sharename. 
Just to be utterly specific and redundant and I know you all know this but...
It used to work just by typing 
smb://computename and all the root shares would display after I typed a password.

At home in the workgroup environment this problem doesn't seem to exist though. 

Anyway here is my edited nsswitch.conf file 

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

#hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
hosts:          files wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:    nis
```I have until August 29th or so to get this sorted out. I'm the IT admin at the school and I would really love to use this downtime in the summer to get this fixed. Is there anyone willing to help me tackle this?

---

### Post by celem on 2008-07-31
It is a confirmed bug. See:
[http://tinyurl.com/582fcg](http://tinyurl.com/582fcg)

I have gotten it to work on my system by the simple workaround suggested, at the LaunchPad link pasted above, by  Steve Langasek. Namely:
Setting /etc/samba/smb.conf to: name resolve order = lmhosts wins bcast host also makes it work for me. It hasn't worked since Dapper - hooray!

---

### Post by SonicSteve on 2008-07-31
I'm not sure that's the same bug. I can find the servers I just don't see any shares unless I add the sharename to the end of the address. I just get a blank white window without a prompt for username and password like it's supposed to do. 

The bug you quoted gives an error when you try to access the share. I don't get anything. It worked nicely under Gutsy Gibbon. I wish they had left this alone until more bugs were worked out of it.

EDIT/update 

OK so it seems that this bug may be a while in the fixing stages. So I cheated kind of...
I installed the KDE desktop along side my Ubuntu desktop. Now I use the KDE wallet with Dolphin. It's not perfect but at least I can browse the shares in My domain. If anyone has any suggestions I'll be happy to try to get Gnome fixed but for now this is at least a mostly functional work-around.

---

### Post by Fraoch on 2008-11-02
Don't mean to whine about an otherwise great release, but this error seems to still be present in Intrepid. :(

---

### Post by rickatnight11 on 2008-11-02
Same for me.  This seems like a feature that the Ubuntu devs would want fixed if they are trying to attract Windows users.  Network sharing is a basic feature in today's OSes.  The only way I have been able to get it to work is by manually mounting a network share via the terminal with smbfs.  It shouldn't take that much work.  The Windows Network area in Ubuntu should do what it says.

---

### Post by SonicSteve on 2008-11-02
> **rickatnight11 said:**
> Same for me.  This seems like a feature that the Ubuntu devs would want fixed if they are trying to attract Windows users.  Network sharing is a basic feature in today's OSes.  The only way I have been able to get it to work is by manually mounting a network share via the terminal with smbfs.  It shouldn't take that much work.  The Windows Network area in Ubuntu should do what it says.

I think this is one of the most annoying bugs out there. I don't understand why more people aren't experiencing it. It has been present on every system I've ever tested with Hardy Heron. 

I don't know if the Ubuntu Devs can do much about it. This bug is part of GVFS the newly appointed file system. It's a Gnome thing, and they might need to fix it and release it upstream before we will see the fix. I don't know how much Gnome cares about existing nicely with Windows, Ubuntu might but if Gnome doesn't the fix might be a way off still. Ultimately I don't know.

---

### Post by sea_monkey987 on 2008-11-02
I have used this fix numerous times now in three separate environments and it has worked quite well every time.


Install winbind, samba, and smbfs.
```
sudo apt-get install winbind samba smbfs
```

open /etc/nsswitch.conf for editing.  change the line "hosts..." line to read
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```

save /etc/nssswitch.conf and open /etc/samba/smb.conf for editing.
```

change the line:
**;        wins support = no**
so that it reads:
**wins support = yes**
```
save and restart.

---

### Post by Halbarad on 2008-11-02
I have a similar problem: two ubuntu pcs suddenly became unable to browse the samba shares (both in xp machines and in the other ubuntu machine) after a hardy recommended upgrade. I have already tried the changes suggested by sea_monkey, and several others that are similar, but they don't work. Even writing the smb address and share in the address bar doesn't work. This happens at the same time in two very different machines (one is a laptop); if I dual-boot in xp, all works fine.
One thing I can say is, we are truly left in the dark: to my taste, this kind of Linux development is too much like Windows development. Another thing is, networking was important to me, I have now to run from one pc to another handling a flash drive ;-)

---

### Post by funchords on 2008-11-02
> **sea_monkey987 said:**
> I have used this fix numerous times now in three separate environments and it has worked quite well every time.


Install winbind, samba, and smbfs.
```
sudo apt-get install winbind samba smbfs
```

open /etc/nsswitch.conf for editing.  change the line "hosts..." line to read
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```

save /etc/nssswitch.conf and open /etc/samba/smb.conf for editing.
```

change the line:
**;        wins support = no**
so that it reads:
**wins support = yes**
```
save and restart.

Does this mean I'll have to run a WINS server or will it also find servers on a network that relies on Broadcast-style browsing?

---

### Post by sea_monkey987 on 2008-11-02
it will find servers using the broadcast method of the netbios names.

---

### Post by dmizer on 2008-11-02
> **sea_monkey987 said:**
> open /etc/samba/smb.conf for editing.
```

change the line:
**;        wins support = no**
so that it reads:
**wins support = yes**
```
save and restart.

This is very common advice, but it is inadvisable. From man smb.conf:
>           wins support (G)
             This boolean controls if the [noparse]nmbd(8)[/noparse] process in Samba will act as
             a  WINS  server. You should not set this to yes unless you have a
             multi-subnetted network and you wish a particular nmbd to be your
             WINS  server.  Note that you should NEVER set this to yes on more
             than one machine in your network.

             Default: wins support = no
This means that setting wins support to yes is only advisable if all the following conditions are met:
[LIST]
[*]you have more than one subnet
[*]you have either a static network with correctly configured /etc/hosts file, or a properly configured local DNS server
[*]you do NOT have a Windows machine on the network (Windows already has a wins server)
[/LIST]

This option has nothing to do with making Ubuntu able to see Windows networks. It's really only useful when configuring Ubuntu as a AD controller. This option can cause conflicts with Windows computers on the network and cause slowdowns.

More information here: [http://www.onlamp.com/pub/a/onlamp/excerpt/samba_chap7/index.html?page=2](http://www.onlamp.com/pub/a/onlamp/excerpt/samba_chap7/index.html?page=2)
> If you enable this option, remember that a Samba WINS server currently cannot exchange data with other WINS servers, so do not allow any other WINS servers on the network.

---

### Post by bab1 on 2008-11-03
> It's a Gnome thing, and they might need to fix it and release it   This is most definitely the case.  Gnome is redoing the gvfs system with GIO.  There are I/O issues and modernization concerns. 

I feel that I should relate my experiences with Ubuntu and Samba. I have successfully installed and maintained Samba on 7.04, 7.10 and 8.04 (Feisty, Gutsy and Hardy). My clients have been XP Pro and Ubuntu. I don't mount any drives via fstab. I don't use winbind, I don't use NetBios. I have never had a problem. I feel this is due to my configuring samba manually. I do not configure anything using Gnome (Nautilus) or any of it's tools.

IMHO the problems arise from the use of the GUI interface to try to configure "shares". Then when it fails, trying to solve the problem problem by manually modifying /etc/samba/smb.conf file. Why does this fail? Because Gnome (Nautilus) uses /var/lib/samba to configure the "shares". These files are binary and can't be modified with a text editor. As a side issue , the gvfs and the new GIO libraries are changing. There are other concerns for the Gnome developers.

I believe that the Samba daemon will always work when the /etc/samba/smb.conf file is used to configure the "shares". it sure has for me. I the upcoming future I will be upgrading to 8.10 (Intrepid). I'm sure that it will work too.

Edit: For clarity -- [COLOR="Blue"]**There does not seem to be any problem browsing the network or accessing Samba shares with Gnome (Nautilus)**[/COLOR] when Samba is properly configured via /etc/samba/smb.conf

---

### Post by dmizer on 2008-11-03
> **bab1 said:**
> I believe that the Samba daemon will always work when the /etc/samba/smb.conf file is used to configure the "shares". it sure has for me. I the upcoming future I will be upgrading to 8.10 (Intrepid). I'm sure that it will work too.

Edit: For clarity -- [COLOR="Blue"]**There does not seem to be any problem browsing the network or accessing Samba shares with Gnome (Nautilus)**[/COLOR] when Samba is properly configured via /etc/samba/smb.conf

Although this may be partially true, /etc/samba/smb.conf has very little to do with Ubuntu seeing Windows shares. The /etc/samba/smb.conf file is for configuring Ubuntu as a samba server. Configuring a samba server does _not_ mean that you can browse Windows shares from Ubuntu.

Perhaps you could elaborate by sharing what you mean by a "properly configured smb.conf" file?

---

### Post by bab1 on 2008-11-03
> Although this may be partially true, /etc/samba/smb.conf has very little to do with Ubuntu seeing Windows shares. 

On the contrary, it has everything to do do with browsing shares.  I have only smbd running and the interaction between the client and the smbd is what allows browsing.

This is my smbtree output```
bruce@malibu:~>smbtree
Password: 
BEACHBEES
        \\RINCON                        Storage
                \\RINCON\bruce                  Home Directories
                \\RINCON\IPC$                   IPC Service (Storage)
                \\RINCON\Backup                 Beachbees Backups
                \\RINCON\Share                  Public Share
                \\RINCON\Archive                Archived Data
        \\MALIBU                        malibu
                \\MALIBU\bruce                  Home Directories
                \\MALIBU\LaserJet_2200          LJ2200dn
                \\MALIBU\Print2PDF              Malibu_Print2PDF
                \\MALIBU\IPC$                   IPC Service (malibu)
                \\MALIBU\print$                 Printer Drivers
                \\MALIBU\Backup                 Beachbees Backups
                \\MALIBU\Share                  Public Share
bruce@malibu:~>

```
I am running 2 Samba server daemons.  On 2 boxes of course!

What I mean by a properly configured smb.conf file is that all configuration of the smbd daemon is handled by smb.conf.  No point and click GUI config that alters and breaks the smb.conf (I have done that while experimenting).  As I have said previously the GUI config of Samba via /var/lib/samba/<files> seems to be broken at this time.

Here are some relevant parts of my smb.conf file:
```
        workgroup = BEACHBEES
        server string = %h
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        guest account = smbguest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spas
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

```

Nothing unusual with this part

```
[Share]
        comment = Public Share
        path = /smb/share
        read only = No
        create mask = 0775
        force create mode = 03775
        directory mask = 03775
        guest ok = Yes

[Backup]
        comment = Beachbees Backups
        path = /smb/backup
        valid users = bruce, +smbusers
        force group = smbusers
        read only = No
        create mask = 0770
        directory mask = 03770


```

This all seems normal

```
[homes]
        comment = Home Directories
        path = /smb/home/%S
        valid users = %S, +smbusers
        force group = smbusers
        read only = No
        create mask = 0770
        directory mask = 0770
        browseable = No

```

Note the use of "browseable = No".  **[COLOR="Magenta"]This stops the browsing of this share.[/COLOR]**  The default (no need to even state it in the share) is 
"browseable = Yes".  Unless you have **[COLOR="Red"]NOT DEFINED[/COLOR]** the share in smb.conf.  You can't browse what is not defined!  IMHO, this is part of the problem.  The user has not really configured the smbd daemon.  The gvfs (or GIO now) configs through a vfs system and it is not fully compatible.  Samba devs and Gnome devs do not always see things in the same way.

@dmizer,

I am aware and respect your good work.  I sympathize with the average user who would like the same functionality for sharing  folders in a GUI environment as one gets with XP/Vista.  But, sad to say it is not here now.  What are we to do?  These are upstream dev concerns.  How do we resolve these types of situations?  I will say that the last Samba setup to me all of 10 minutes. I did this last week.  I use the same smb.conf file   (with minor tweaks) and same the directory structure.  The CLI still rules.  :-)

Edit: Here are the outputs of the smbclient listings for both hosts.  First malibu as the client of rincon:```
bruce@malibu:~>smbclient -L rincon
Password: 
Domain=[RINCON] OS=[Unix] Server=[Samba 3.0.28a]

        Sharename       Type      Comment
        ---------       ----      -------
        Archive         Disk      Archived Data
        Share           Disk      Public Share
        Backup          Disk      Beachbees Backups
        IPC$            IPC       IPC Service (Storage)
        bruce           Disk      Home Directories
Domain=[RINCON] OS=[Unix] Server=[Samba 3.0.28a]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        BEACHBEES            RINCON


```

And second, rincon the client of malibu:```
bruce@rincon:~>smbclient -L malibu
Password: 
Domain=[MALIBU] OS=[Unix] Server=[Samba 3.0.26a]

        Sharename       Type      Comment
        ---------       ----      -------
        Share           Disk      Public Share
        Backup          Disk      Beachbees Backups
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (malibu)
        Print2PDF       Printer   Malibu_Print2PDF
        LaserJet_2200   Printer   LJ2200dn
        bruce           Disk      Home Directories
Domain=[MALIBU] OS=[Unix] Server=[Samba 3.0.26a]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        BEACHBEES            RINCON
```

---

### Post by dmizer on 2008-11-03
I'm sorry bab1, maybe I'm too dense, but what you've pointed out is a problem which will prevent Windows from properly accessing Ubuntu. I still do not see anything which will allow Ubuntu to access Windows.

Ubuntu should be able to access Windows shares without any configuration of smb.conf, and without configuring any samba shares whatsoever. There were a whole bunch of GVFS updates in Hardy today ... I wonder if anything has changed for the folks in this thread.

---

### Post by Halbarad on 2008-11-03
> Ubuntu should be able to access Windows shares without any configuration of smb.conf, and without configuring any samba shares whatsoever.

That's it. I just wonder if Ubuntu networking is open to people having less than 4 degrees in different branches of computer science :roll:
@ bab1: I hope you're right, since I'm going to invest some more time to learn about your way of configuring the smb.conf. This is the point: to learn, not just to copy and paste some lines into my file. And it would be great if we had a guide (not a mere howto) that did the following:
(1) explain what kind of **functions** are involved in smb networking;
(2) consequently, what kind of **info** must be provided to the operating system;
(3) **where** and how such info has to be correctly fed into the system.
This may require some further explanations -- it's as if I could see the guide already: a high level description with links to more detailed guides for users who want to know more. Clear explanations telling you the meaning of the lines you write. This would require time and work, especially in order to decide which kinds of info are actually required for different kinds of users -- sort of different layers.

Another remark: dmizer is entirely right when he says that the ability to browse Win shares should be there with no need to tinker etc. This is one of the basic functions in an operating system. It is a strategic thing. The fact that crucial functions are being disregarded while much attention is devoted to mere candy is a very bad omen for Linux, and afaics is against the entire Linux philosophy. I mean: having a new release every sixth month and displaying flapping windows is not what is important. Linux is born to be a truck or a camper -- not a fancy car.

---

### Post by celem on 2008-11-03
Loading SAMBA will not resolve this issue - it is a different issue. SAMBA's purpose is to provide Windows access to Linux shares. The problem of this thread is to access Windows shares from a Linux box. SAMBA isn't even necessary for this to work. For example SAMBA is not loaded on my Ubuntu box yet I can access Windows shares. Loading SAMBA never solves this particular problem.

As I said in an earlier post to this thread, it is a confirmed bug. See:
[http://tinyurl.com/582fcg](http://tinyurl.com/582fcg)

The simple workaround suggested in the LaunchPad link pasted above, by Steve Langasek. Namely:
Setting /etc/samba/smb.conf to: name resolve order = lmhosts wins bcast host, ususlly works. It certainly does for me. I noticed that Ubuntu 8.10 has changed the order, placing lmhosts first, and 8.10, for me at least, was able to work "out of the box", although very slowly.

I agree with previous statements in this thread. For Ubuntu to take a serious place in the workplace environment of mixed machine genealogy, this MUST work better. The Launchpad bug lists it as a medium priority but, in my opinion, it should be high priority.

So, while I can access Windows shares with 8.10, it still isn't working well. It certainly isn't working as well as a Windows-toWindows share. This issue remains an embarrassment for Ubuntu/Linux, i.e., something that Windows performs FAR better and easier.:(

---

### Post by bab1 on 2008-11-03
> **dmizer said:**
> I'm sorry bab1, maybe I'm too dense, but what you've pointed out is a problem which will prevent Windows from properly accessing Ubuntu. I still do not see anything which will allow Ubuntu to access Windows.

Ubuntu should be able to access Windows shares without any configuration of smb.conf, and without configuring any samba shares whatsoever. There were a whole bunch of GVFS updates in Hardy today ... I wonder if anything has changed for the folks in this thread.

@dimizer,

Not dense at all.  The XP/Vista host also has a server builtin.  That's why ports 135/139 and 445 are open on the Winodws hosts.

Her is smbclient on Malibu (Ubuntu) to Manila (XP):
```
bruce@malibu:~>smbclient -L manila
Password: 
Domain=[MANILA] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        SharedDocs      Disk      
        CMaxData        Disk      Transfer Point from CMAX
        Disks           Disk      
        Printer3        Printer   Adobe PDF
        Printer2        Printer   HP LaserJet 2200 Series PCL 5e
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        Printer         Printer   Microsoft Office Document Image Writer
Domain=[MANILA] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```

It woks in both directions!  XP (client) --> Ubuntu (server) and Ubuntu (client) --> XP (server).

Here is

---

### Post by bab1 on 2008-11-03
> **Halbarad said:**
> That's it. I just wonder if Ubuntu networking is open to people having less than 4 degrees in different branches of computer science :roll:
 I would say yes, but just barely.  Remember the OS is created and maintained by volunteers and a core staff of professionals.  It's a long intensive process.
>      
@ bab1: I hope you're right, since I'm going to invest some more time to learn about your way of configuring the smb.conf.
Remember that you have to have all the network support services correctly configured BEFORE you mess with the smb.conf file.
>  This is the point: to learn, not just to copy and paste some lines into my file. That is my point exactly (see above).  >   And it would be great if we had a guide (not a mere howto)  I have been chastised before for over explaining how it all works.  I have been told flat out that I am wrong.  I guess my degree and 25 years experience mean nothing. Sorry for the rant, I'm all better now. :D  >   that did the following:
(1) explain what kind of **functions** are involved in smb networking;
(2) consequently, what kind of **info** must be provided to the operating system;
(3) **where** and how such info has to be correctly fed into the system.
This may require some further explanations -- it's as if I could see the guide already: a high level description with links to more detailed guides for users who want to know more. Clear explanations telling you the meaning of the lines you write. This would require time and work, especially in order to decide which kinds of info are actually required for different kinds of users -- sort of different layers. I have posted most of this before see: [[COLOR="DarkOrange"]**here**[/COLOR]]("http://ubuntuforums.org/search.php?searchid=50836073").  I have saved notes from the last install to provide an upto date guide for myself.  I will post these in the next few days.  I would prefer to share them with dmizer first.  I've nothing to hide, I would like advice on the best way to post these notes.  It seems this problem comes up again and again and ...>   

Another remark: dmizer is entirely right when he says that the ability to browse Win shares should be there with no need to tinker etc. This is one of the basic functions in an operating system.  I guess I can start right here.  Browsing is not a function of the OS.  It is specifically a IBM/lanman-Windows or Samba convention.  Samba has been back engineered as MS would not release the code until last year (thanks to an EU court ruling).    > It is a strategic thing. The fact that crucial functions are being disregarded while much attention is devoted to mere candy is a very bad omen for Linux, and afaics is against the entire Linux philosophy. I mean: having a new release every sixth month and displaying flapping windows is not what is important. Linux is born to be a truck or a camper -- not a fancy car. Hmmmm...  Linux can and is whatever you want it to be.  I was involved with a "supercomputer" that was a Linux Beowulf cluster of 100+ nodes.  On the other hand eye candy to some people is important.  All should be taken care of.

---

### Post by Halbarad on 2008-11-03
> I have posted most of this before see: here. 
Are you sure?
> vBulletin Message
Sorry - no matches. Please try some different terms. 

---

### Post by bab1 on 2008-11-03
> **Halbarad said:**
> Are you sure?

Hmmmm...  I'm sure of the search.  Just search on "bab1 and samba"  for the entire forum and you will see what I was trying to hyperlink. Sorry about that!

---

### Post by celem on 2008-11-03
bab1: I would be interested in hearing your comments concerning the confirmed bug ( [http://tinyurl.com/582fcg](http://tinyurl.com/582fcg) ) that causes this problem for some, but not all users?

---

### Post by Halbarad on 2008-11-03
@bab1
I'd be grateful if you replied to the critics instead of merely reacting to them.
> I have been chastised before for over explaining how it all works. 
This is by no means the case: you have been criticized for stating something that other people regarded as not true, i.e. that the bugs with samba shares browsing can be fixed or avoided by correctly configuring samba. If you hold to this, you might simply reply and explain what is wrong in the line of argument of your critics. This would help us to form an idea. Degrees do not  normally provide immunity to criticism, even though they may provide an ability to face it.

I may add that networking is widely regarded as a function of operating systems (even if individual browsers are generally not) -- but I am not presently interested in such issues, because the matter at hand is both well-defined and urgent. For similar reasons, I shall not question any of the general points you make, even though they might make good topics for intriguing conversation. The only point I am inclined to insist on in this connection is that networking is vital and strategic, whereas eye candy is not.

---

### Post by bab1 on 2008-11-03
> **Halbarad said:**
> @bab1
I'd be grateful if you replied to the critics instead of merely reacting to them.

This is by no means the case: you have been criticized for stating something that other people regarded as not true, i.e. that the bugs with samba shares browsing can be fixed or avoided by correctly configuring samba. If you hold to this, you might simply reply and explain what is wrong in the line of argument of your critics. This would help us to form an idea. Degrees do not  normally provide immunity to criticism, even though they may provide an ability to face it.

I may add that networking is widely regarded as a function of operating systems (even if individual browsers are generally not) -- but I am not presently interested in such issues, because the matter at hand is both well-defined and urgent. For similar reasons, I shall not question any of the general points you make, even though they might make good topics for intriguing conversation. The only point I am inclined to insist on in this connection is that networking is vital and strategic, whereas eye candy is not.

So...are you asking for help?

---

### Post by bab1 on 2008-11-03
> **celem said:**
> bab1: I would be interested in hearing your comments concerning the confirmed bug ( [http://tinyurl.com/582fcg](http://tinyurl.com/582fcg) ) that causes this problem for some, but not all users?  I lightly skimmed over the bug report.  It looks like a DNS config problem for one of the users.  

I feel that part of the problem with tracing intermittent samba GUI config problems is that the VFS system is constantly changing every time the user opens a dialog box and clicks on something.  I don't know exactly what is modified and I'm sure the user in the post doesn't either.  So it is hard to diagnose.  The reference to /etc/hosts is further confirmation that there was a DNS problem.  I have local (LAN) DNS set up and so hostname to IP address is not an issue with me.

Does this help?

---

### Post by celem on 2008-11-03
I concur that it is DNS related but ordinary users with simplistic setups shouldn't encounter this issue, yet they do. I am impacted and my installation is simple, straightforward and comparable to most typical user installations. Namely, I have a retail D-Link wireless router connected to the ISP's service. The DNS resides with the ISP. All simple plug and play stuff that simply works with Windows and should work with Linux, yet it far too often does not. This is not simply a Ubuntu problem as I have seen it in other releases as well. Possibly the developers don't see the problem because their setups are not the simple Plug-n-Play installations of most users but are more complex, with their own DNS, such as yourself.

I didn't see this problem until about 3 or 4 releases ago, so something changed. Personally, I find it rather irritating even though I have a functional workaround.

Your advice is appreciated and useful - please keep contributing.

---

### Post by bab1 on 2008-11-03
> **bab1 said:**
> I lightly skimmed over the bug report.  It looks like a DNS config problem for one of the users.  

I feel that part of the problem with tracing intermittent samba GUI config problems is that the VFS system is constantly changing every time the user opens a dialog box and clicks on something.  I don't know exactly what is modified and I'm sure the user in the post doesn't either.  So it is hard to diagnose.  The reference to /etc/hosts is further confirmation that there was a DNS problem.  I have local (LAN) DNS set up and so hostname to IP address is not an issue with me.

Does this help?

@celem,

i think i did not answer you question as well as I should have. In reading a little deeper I see that there is a discussion regarding wins/nsswitch and "name resolve order = lmhosts wins bcast host". This is by my estimation unfortunate.  MS stopped using NetBIOS (and therefore WINS) with the release of Win2K.  

Looking at pre-built NAS boxes one should take into consideration that there still are OS's that rely on NetBIOS and WINS for name resolution (Linux/XP/Vista/Mac OSX not being among them).  I'll bet, but I'm not sure, that these NAS devices are setup to use WINs to resolve names, so as to include the lowest common denominator.  

In that case you HAVE to use a WINS server.  This surly will cause confusion as some setups will require WINS while others do not.  Look before you leap when purchasing an off-the-shelf NAS device.  

In the end, as I said before , the basic networking (connectivity) must be up and running before you attempt configuration of Samba.

---

### Post by bab1 on 2008-11-03
@celem,

> The DNS resides with the ISP.Global DNS rersides at the ISP.  Our private NAT'd, no IANNA domain name networks are not in that DNS system.  If you can't provide local (LAN) DNS with your router you can use DNSmasq (this is also used in Linksys frmware).  Either way you must provide LAN side DNS.

> didn't see this problem until about 3 or 4 releases ago, so something changed. Personally, I find it rather irritating even though I have a functional workaround.  I agree.  Gnome is responsible.  They are changing the libs.  Until Gnome stabilizes with the new GIO (Gnome I/O libs) we all have to live with it.

Just a thought.  If you have only a few hosts in your network, the etc/hosts (on Linux) will suffice for hostname resolution.  There is a similar hosts file at (as I remember it) C:\WINDOWS\system32\drivers\etc\hosts.  I have setup Samba with hosts file name resolution.  It works just as well.

---

### Post by celem on 2008-11-03
You are missing the point of my post. While there is twiddling that cat be done, such as lmhosts order or possibly the Windows hosts file, none of this should be necessary for a typical generic setup for a typical user. While the lmhosts order is a viable workaround for me personally, I shouldn't have to do it at all to simply see a Windows share. There is no justification, given Ubuntu's desire to be a mass market replacement for Windows, for Linux not to be able to access Windows share as easily as Windows does. Personally, I still suspect that this happens because the developer's own installations are far from generic and thus they simply never encounter it.

---

### Post by SonicSteve on 2008-11-03
I've mentioned this before also. To browse and access windows shares in the past -gutsy, fiesty et al- required nothing. You installed the OS and had instant network access to any windows share on you network. Proof of this comes from KDE, 
If you don't believe me install KDE and then try browsing with Dolphin or Konqueror. It works perfectly. That's the bug in GVFS, that doesn't exist in KDE. When Gnome replaced the previous virtual file system with GVFS they broke it plain and simple. What ever the reason is they haven't fixed it I don't know. They've (Gnome developers) had more than enough time to get it done.

---

### Post by bab1 on 2008-11-03
@Celem,

I agree with you.  I understand exactly what you are saying.  I watch my TV, but I can't fix it.  I drive a car and other than few simple things things (checking the oil in the engine and the air in the tires), I don't service it.  As far as a personal computer is concerned, that too should fall into this category.

But at this time the Ubuntu distro doesn't.  At least the Gnome desktop or Nautilus (and therefore Ubuntu) doesn't.  This does cause Linux fans to suffer.  Apple and MS supply machines that do work.  I'm not a OS religious zealot.  I use what works.  

I think these problems are out of the Ubuntu developers hands.  Gnome is independent of Ubuntu. The Linux kernel is too.  Ubuntu is also downstream of Debian and it's package developers.  What I'm saying here is that Ubuntu is not a monolithic entity.  Apple is, MS is.  Both control end to end their distro.
  
How about this interesting idea. Nexenta, a Debian derivative, uses a Sun Solaris Kernel.  This kernel implements the SMB protocol with it's own libs.  No Samba used at all to share and browse smb/cifs shares.  It's just an interesting sidelight, but it is an alternative that is being developed

it is unfortunate that Gnome.org and to some extent Samba are not under one set of marching orders.  A bright spot is the EU ruling requiring  MS to show how they implement all of Network Neighborhood code.  Show us the source code!  When this becomes available  we should have what you are looking for, true point and click file sharing.

But until then, what do you want to do?

@SonicSteve,

Exactly!  I think Gnome are trying to improve the user space I/O with GIO.  As I have said before, they seem to be working on it.  I think in this instance the twice yearly release harms Ubuntu rather than helps.  KDE has decided to use their stable code and it does work.  Gnome is a moving target.  That's why for now I manually configure.  I do use the GUI as everyone else does to browse folders, view, modify and add files.

Nautilus is the real culprit here.

---

### Post by dmizer on 2008-11-03
> **SonicSteve said:**
> When Gnome replaced the previous virtual file system with GVFS they broke it plain and simple. What ever the reason is they haven't fixed it I don't know. They've (Gnome developers) had more than enough time to get it done.

Certainly the problem has been with GVFS, but it is not a recent problem by any stretch of the imagination. I have never been able to get samba browsing to work correctly, and I've been using Ubuntu since Breezy. My knowledge of SAMBA is a direct result of my battling this frustrating issue for the past 3 years.

Recent updates, including moving away from GVFS, and depreciating SMBFS for CIFS are improvements. To me, this seems to be an investment in the future and a genuine attempt by the developers to fix this problem. To be sure, the problem is not fixed yet, but it's important to be aware that work is being done.

---

### Post by celem on 2008-11-03
All interesting comments. 

I have used Ubuntu for years on my laptop, and my primary desktop dual boots Windows Xp and PCLinuxOS. I just recently built up a new, more powerful machine that will become my new primary desktop. My plan was to make the shift away from a dual-boot machine and use Linux as the only OS. Some legacy programs that I need will run under WINE and I plan on using a virtual machine, such as QEMU (which I've used in the past) should there be a killer Windows ap that I must have access to.

I haven't ported my files over yet for a variety of reasons, one involving a decision about RAID, but I also haven't finalized my decision about the distro. I tested Sabayon for a period and I really liked it but the small size of its developer group gives me concern for its long term viability. I also have used PCLinuxOS for quite a while and it is probably the best distro that I've tried but it has similar long term viability issues. I even tried the Mint spinoff of Ubuntu, which is better than Ubuntu itself. However, most recently I've been leaning towards keeping the Ubuntu 8.10 loaded in it, primarily because of the huge community support, such as demonstrated by this thread. In my opinion, Ubuntu's greatest current strength is its large installed base and resultant community support. That said, KDE is fine with me - I use it with PCLinuxOS. I may consider switching to Kubuntu - hmmm?

---

### Post by dmizer on 2008-11-03
> **celem said:**
> That said, KDE is fine with me - I use it with PCLinuxOS. I may consider switching to Kubuntu - hmmm?

That's probably the most headache free way of solving the problem ;)

---

### Post by Halbarad on 2008-11-05
I have installed the new recommended updates. I have a local network with two Ubuntu and 2 XP machines. On my Ubuntu laptop, Nautilus is very slow, but it eventually shows the network machines. I double-click a PC icon and its folders are correctly shown. But when I double-click a folder, an error message pops up > Couldn't display "smb://morgenstern/e/".
However, if I write the IP address of the machine into the Nautilus' address bar (smb://192.168.1.98 -- it's a static address), I have smooth access to all the shared folders and can perform the usual operations on them (I have bookmarked this location, which also shows up in the Places menu, and Nautilus almost appears to work now...). I also have access to my shares if I browse the local network with Firefox or with Gnome Commander. I know that other users experienced the same behaviour before. But my question is: does this not suggest that the bug is **mainly with name resolution**?

And here, I get a bit lost for lack of consistent information. Does anyone really know what happens with name resolution? In connection with browsing, is name resolution performed by the program (Nautilus, Gnome Commander, Firefox) or by the operating system, and if so, by which part of it? Netbios name resolution seems to be okay in my Ubuntu laptop:
> a@traveller:~$ nmblookup morgenstern
querying morgenstern on 192.168.1.255
192.168.1.98 morgenstern<00>

but which role does netbios exactly play in samba shares browsing?
I read that Netbios was employed only up to Win98 but modern Op Systems in fact use a variant of it that still assigns Netbios names as well as IP addresses. See: [http://en.wikipedia.org/wiki/NetBIOS](http://en.wikipedia.org/wiki/NetBIOS)

Sorry for asking so many questions in a single post -- but they are closely related.

---

### Post by bab1 on 2008-11-05
@Halbarad,

I think you have correctly identified your problem.```
Does anyone really know what happens with name resolution?
```

Name resolution is a protocol supporting the networking protocol.  At this point TCP/IP is the dominant networking protocol.  In an earlier time NetBIOS was used by IBM and later MS for networking.  With the advent of TCP/IP (IP for short).  DNS (Domain Name Services) has become the preferred name resolution protocol over the earlier WINS/NetBIOS for technical reasons.  Either protocol will resolve (map) human readable host/computer names to IP addresses.  DNS servers resolve DNS and WINS servers resolve NetBIOS names. Only DNS will resolve a name like myhost.mydomain.com. This resolution goes one step further.  The IP address is mapped the Ethernet card (wireless or wired) MAC address via ARP.

```
but which role does netbios exactly play in samba shares browsing?
```  The Samba protocol locates the shares by hostname (DNS) or COMPUTER NAME (WINS) or by IP address.  If the Samba protocol browse request sees a text based name it asks for name resolution by the name resolution protocol you define in the smb.conf file.  If the the protocol sees a number value in the browse requests it does not ask for any name resolution, it just displays the data.

EDIT: The choice is your as to which naming protocol you use.  I would use DNS if you are integrating with workgroup or MS Active Directory or Linux LDAP.  I would only use WINS if I had W95/98 clients.

---

### Post by rickatnight11 on 2008-11-05
bab1, you are the first person I have found who seems to have a grasp on this entire thing.  You know what causes the problem, and you know what is the most effective way to compensate for the current bugs.  Could you possibly help me determine what the best thing to do for my Ubuntu machine is?

I have a wired network running all over my apartment.  All IPs are assigned by the router into the 192.168.1.xxx range.  I have one Ubuntu 8.10 machine, freshly installed (no smb tweak attempts yet) acting as a file host and XBMC media center.  The rest of the computers on the network are Windows XP with the exception of one Windows Vista laptop.  All of the Windows machines are able to detect the others without any comfiguration.  What would be the best method for my Ubuntu machine to see all of the other Windows machines just as seamlessly?

---

### Post by bab1 on 2008-11-05
> **rickatnight11 said:**
> bab1, you are the first person I have found who seems to have a grasp on this entire thing.  You know what causes the problem, and you know what is the most effective way to compensate for the current bugs.  Thanks! >  Could you possibly help me determine what the best thing to do for my Ubuntu machine is?Sure I will.

> I have a wired network running all over my apartment.  All  IPs are assigned by the router into the 192.168.1.xxx range.  Do you have some absolute need for DHCP?

> I have one Ubuntu 8.10 machine, freshly installed (no smb tweak attempts yet) acting as a file host and XBMC media center. Do you have any SMB file sharing on this host?


 > The rest of the computers on the network are Windows XP with the exception of one Windows Vista laptop.  All of the Windows machines are able to detect the others without any configuration.   I'm guessing you are saying that the Windows hosts see each other but the Ubuntu host can't be seen or see the Windows hosts.  Is this correct?

 > What would be the best method for my Ubuntu machine to see all of the other Windows machines just as seamlessly?

First, a few caveats.  I have my opinions.  They are based on my experience.  Some of the technology that I will refer to, I have not used in years.  It is entirely possible that these have been either improved or deprecated.  I would not know.

I am not the definitive voice on any of these issues.  These are only my experience or impressions.  As I indicated, I have not even tested some of these techniques recently.  You are welcome to try and of my ideas, but remember, YMMV.

I think the short answer would be: Install and configure Samba as both a server and a client.  Installing Samba (smbd) takes care of the server.  Installing smbfs will takes care of the client.  There is another client out there but I do NOT recommend it.  It is smbuserfs.  This runs in the userspace and has I/O problems under high load.  The smbfs client runs in the Gnome vfs and should faster. 

Now the long version.  I will break it up into sections.

_**[COLOR="Blue"]Defining some terms[/COLOR]**_

```

Server = a process (service) running in the background 
  (aka daemon) listening for a request from a client.  
   Some common server daemons are: dhcpd, smbd and named.

client = a process asking for a service or data from a server.

host = A device (hardware) with an installed operating system.

hostname = name of the host (resolved by DNS)

COMPUTER NAME = NetBIOS name
 (resolved by WINS)

box = bare hardware

```

_**[COLOR="Blue"]Networking infrastructure[/COLOR]**_

```

a. If you use static IP addresses and your router has basic DNS
   you can map the IP to hostname there.

b. If you have DHCP that is able to reserve IP addresses, you
   can also use the router's DNS to map the IP to hostname.

c. If you need to install DNS, I would use DNSmasq.  This is a
   basic DHCP server with simple DNS mapping via an /etc/hosts
   file. 

d. If you can not use DNS, then use WINS to bind a COMPUTER name
   to the IP address.  This is very simple and dynamic.  DHCP and
   WINS work well together.  

```

<My Opinion>because you do not have much to configure with WINS when using DHCP and Samba understands it, this is the easy (but not modern) way of implementing name resolution for an DHCP IP network. That's why the "it just works" developers use it.</My Opinion>

Whichever method you use, once it is implemented, you need to confirm that it works as it should.  Ping the host by name.   If it works, remember which one you configured and we will use it when we install and configure Samba.

_**[COLOR="Blue"]Shared File System[/COLOR]**_

```

I like the orderliness of configuring all my Samba Server shares
on their own partition or drive. This can be a single partition,
HDD, an LVM or RAID array. 
I always use /smb as the file system root.  This is the mount
point of the partition we create.  See below.

As this is local to the Samba server we format it to ext3 and
automount it in /etc/fstab.  We can use ACL's on this partition
to have windows style file permissions and we can run Quota to 
restrict the users share size.  This is not mandatory but they 
are nice additions. 

Create the partition and make it automount.

```

_**[COLOR="Blue"]Users and Groups[/COLOR]**_

```
My setup at home is a workgroup (no domain controller).  
I have only local accounts on my Windows  hosts and  use
/etc/passwd on each of my Ubuntu hosts.  In doing this I have the
EXACT SAME login/password combo's on each host.  Samba needs
this.  If you insist on different login/passwords, you will have
to create maps between the client login and the server login. 
This is done in the /etc/smbusers file.  Either way Samba will
compare the computer users login to its own Samba users login.
See below. 
```

_**[COLOR="Blue"]Samba Server (smbd) and Client (smbfs)[/COLOR]**_

```

Now we are ready to install Samba.  You don't want any Gnome
involvement.  Do not use Network Manager to configure anything
and no file sharing with using Nautilus.

1. Install all of Samba (Server and Client and support) packages.
   You can use Synaptics or apt-get from the command line.

We need to add the Samba users now.  These users are compared to
the computer users and allowed access to Samba.
  

<opinion> I believe that if you do not add a user (say user1) to
the Samba users database he will not be able to access the
shares.  If user1 is not the logged in user but can supply
user1's correct login/password he gets access.  No login or
password is needed if the logged in user is in the database. 
Said in short: You should to be in the Samba user database for
access.  I do not allow guest access.

2. Add the Samba users

   sudo smbpasswd -a <username>  

    (you will be prompted to create a password)
     -- remember EXACT SAME login

3. Enable the user

   sudo smbpasswd -e <username>

     If you forget this the user will be in the database but 
     will not be used.

4. we need to create a /etc/samba/smbusers file

   sudo touch /etc/samba/smbusers

   You need at least a 0 byte file for Samba to work.

      This is the file that maps Windows users to Samba users
      if they are not the same as the Ubuntu users.

If you are using DNS for name resolution then no further action 
with DNS is needed.



A. If you are going to use WINS then you need to create a WINS 
server

    To install WINS see here: http://ubuntuforums.org/showthread.php?t=88206&page=1

      NOTE: If you have installed Ubuntu Samba Server then WINS
      is already installed        

```

Now for the good part!  :D  

```

a. Modify the /etc/samba/smb.conf file
   1. make a copy first:
       sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.original
      Now we modify the smb.conf file without worry. 

b. restart the Samba server (smbd)

   sudo /etc/init.d/./samba restart


Browse for the existing shares
```

I know this not a howto with specific steps needed to implement Samba.  I'm sure there are mistakes and omissions.  There are to many variables at this point for me to make more detailed instructions.  See if it makes basic sense to you.  Please ask questions.   

Once we design what you want to do we can create a smb.conf file.  That is the easiest part of the whole deal.

I have used my own notes from my last install (last week).  I want to create a up to date install tutorial.  This is just the first step for me too.

---

### Post by dmizer on 2008-11-06
First thing I see right off the bat is the same mistake most people make. Referring to this guide for netbios name resolution: [http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

The above guide has a critical flaw. The order of the hosts option DOES matter. So, for people who have hosts who forward bad DNS requests to a search page the hosts request never polls wins because DNS resolved to the provider's search page. I had this problem because I was using OpenDNS. Took me forever to figure out what the problem was.

/etc/nsswitch.conf must be configured so that "wins" is in front of "dns" like so:
```
hosts: files wins dns
```

I suspect that this is the cause of a large percentage of samba browsing problems. In fact, it's so much a problem that I'll probably just edit the guide.

---

### Post by bab1 on 2008-11-06
@dimizer,

Yes, now that you mention it.  I remember you saying that.  I don't use WINS or Winbind.  But it should try wins first if WINS is used.  On the other hand if WINS is NOT used will it err out or pass on to the next protocol?  I use only what I know I need; files and dns.

---

### Post by dmizer on 2008-11-06
> **bab1 said:**
> On the other hand if WINS is NOT used will it err out or pass on to the next protocol?

This will ONLY happen if your DNS servers do not resolve unknown requests.

Here's an example:
You have two computers, foo and bar. foo is configured to use OpenDNS for WAN hostname resolution.

foo tries to access bar with the following:
```
smb://bar/shared
```
bar is an unknown name, so foo queries /etc/nsswitch.conf for directions. First foo looks at /etc/hosts, but there is nothing there, so "files" times out. Next is "DNS". So now foo queries OpenDNS.com for hostname "bar". OpenDNS does not recognize "bar". However OpenDNS has a feature which 1) attempts to resolve improperly written URLs and 2) sends unknown hostnames to a search page like [this](http://guide.opendns.com/?url=www.blmraoin.com). Since the "helpful" OpenDNS search page counts as a completion for the hosts query, wins is never triggered.

Many ISPs are moving to a similar method because it helps prevent phishing schemes and other nasties on the internet. Unfortunately, it also means that DNS is effectively resolved. So, if you do not put wins in front of dns, your samba browser is essentially sitting at your DNS search page.

---

### Post by bab1 on 2008-11-06
@Dimizer,

> ...configured to use OpenDNS for WAN hostname resolution

I'm a firm believer in using local LAN DNS to resolve my hostname only requests.  I only require that WAN side DNS resolve FQDN requests.  The reason you mention is (which is a corruption of the DNS protocol) is enough to make one think twice about using a WAN side server you don't administer.
> Many ISPs are moving to a similar method because it helps prevent phishing schemes and other nasties on the internet.   This is is a violation of the DNS protocol.  If you request an incorrect FNQN, DNS should return that message.  No Verisign like switching to another page advertising the hosts wares.  Boo on them!  :-(

I would highly recommend (and I will try it out myself) running DNSmasq to resolve your LAN side DNS queries.  I'm looking for a trivial DNS server that will interface with DHCP.  So far DNSmasq fills the bill on paper.  At the present time I use my router to provide DNS services for the LAN side.  Unfortunately I can't do reserved DHCP addresses or internal dynamic DNS.

With winter comes testing time!  :D

---

### Post by dmizer on 2008-11-06
> **bab1 said:**
> I'm a firm believer in using local LAN DNS to resolve my hostname only requests.  I only require that WAN side DNS resolve FQDN requests.  The reason you mention is (which is a corruption of the DNS protocol) is enough to make one think twice about using a WAN side server you don't administer.
That's all well and good, but a vast majority of users aren't going to be able to wrap their heads around a proper LAN DNS.

> **bab1 said:**
> This is is a violation of the DNS protocol.  If you request an incorrect FNQN, DNS should return that message.  No Verisign like switching to another page advertising the hosts wares.  Boo on them!  :-(
As far as I know, it's not. Especially since the request is not a FQDN. I think OpenDNS is configurable to do at least part of this if you sign up for an account.

---

### Post by Halbarad on 2008-11-06
Sorry for replying so late. Many thanks to both of you (bab1 and dmizer) for your very interesting discussion. Regrettably, other probs I had with my machine (dim screen etc) suddenly got worse and I now experience erratic behaviour and responses (weird as it may seem, I have access to /etc/samba/smb.conf only via the Nautilus GUI since nothing happens when I use "gksu gedit" in Terminal... I'm writing from an XP machine right now). Thus... high time to make a fresh install. And the thought keeps buzzing in my head that I should give Fedora a try -- even if this might require a good deal of new learning and even if I already miss apt-get, even before losing it... ;-)
But I might come back to some kind of Ubuntu. Thus, I keep my account in this forum active, and I'll especially follow your discussion about samba, name resolution etc., which is very good for trying to understand the fundamentals (and at any rate, Fedora also has samba). I have also found much online material about protocols, smb, dns and netbios. My feeling is that the situation is very complicated because several versions of the same protocols coexist. Old protocols (like Netbios) have not been abandoned but they have been reintroduced in new (and not always clearly defined) variants. The overall impression I have formed is of a very messy field.
Just a naive question: in case I wish to throw away all the Microsoft stuff and only use Linux in my local network, is there a non-samba approach to network sharing and browsing for Linux machines? (in the hope that the Linux way would be more clearly defined and consistent.)

---

### Post by Halbarad on 2008-11-06
Huh... sorry... is that NFS?

---

### Post by rickatnight11 on 2008-11-06
> **bab1 said:**
> Do you have some absolute need for DHCP?
Yes.  I frequently have people come over with laptops (almost always with Windows) that like to hop on the network.  DHCP lets them connect with just the wireless password and doesn't require any static IP configuration on my part.  I would like them to also be able to browse any file on my Ubuntu machine that I deem as "public" (ie my media files.)

> **bab1 said:**
>   Do you have any SMB file sharing on this host?
Not yet.  Since I had so much trouble setting up SMB with 8.04 I have not done anything with my new and fresh 8.10 install.  I wanted to wait until I found a viable solution.

> **bab1 said:**
> I'm guessing you are saying that the Windows hosts see each other but the Ubuntu host can't be seen or see the Windows hosts.  Is this correct?
The Ubuntu host cannot see any Windows hosts.  Going to Network->Windows Network leads to a blank screen.
I have not tried accessing the Ubuntu host from any Windows hosts because it is not sharing anything yet.

 > **bab1 said:**
> 
a. If you use static IP addresses and your router has basic DNS
   you can map the IP to hostname there.

b. If you have DHCP that is able to reserve IP addresses, you
   can also use the router's DNS to map the IP to hostname.

c. If you need to install DNS, I would use DNSmasq.  This is a
   basic DHCP server with simple DNS mapping via an /etc/hosts
   file. 

d. If you can not use DNS, then use WINS to bind a COMPUTER name
   to the IP address.  This is very simple and dynamic.  DHCP and
   WINS work well together.

a.) I use DHCP, but as far as DNS goes I am not sure.  I have the router set up to use OpenDNS instead of my ISP's, but I don't know if it has any sort of LAN DNS.  I admit that this is one part of networking I didn't know about until mentioned in this thread.

b.) My router *can* reserve IP addresses, and I have been toying with this idea recently.  Because sometimes I add shares to my XBMC based on another machine's IP, once it changes those media files in the library go stagnant.  Reserving IP addresses for my machines that are always there would solve that problem *and* be helpful for always knowing what machine has what IP address.

c.) Because I prefer keeping my network in the basic default configuration (DSL modem plugs into Netgear router which takes care of DHCP, port forwarding/triggering, etc) I would rather not have another one of my machines doing this.  Because power consumption is becoming a problem, I try to keep my "always on" devices as small and low-powered as possible.  I will soon be buying a nice NAS to be my media/file server so that my Ubuntu box does not need to be on all the time.

d.) It seems as though this option and option b seem to be the most suited for my needs.  Could you explain in more detail what you mean by setting up WINS?



> **bab1 said:**
> I like the orderliness of configuring all my Samba Server shares
on their own partition or drive. This can be a single partition,
HDD, an LVM or RAID array. 
I always use /smb as the file system root.  This is the mount
point of the partition we create.
All of the files that I am interested in hosting (music, videos, etc) are on a 1TB external USB drive.  In the future I will be moving that over to a NAS (2 x 250gb SATA + the 1TB USB) as I mentioned about.  So it's not the sharing *from* Ubuntu that I am mostly worried about.  I used a package (although the name escapes me now) that made setting up shares VERY easy and intuitive.  It made an entry in the Administrative menu that simply let you choose folders to share, add users to each, and set permissions.  I believe it edited the smb.conf for that.  Worked better than Windows' sharing in my opinion.  Because the Ubuntu machine will only be the host for a little bit longer that is not my priority.  What *is* my priority is getting the Network->Windows Network section in Ubuntu to browse the Windows network just like someone coming from Windows would expect it to.  I understand that there are issues preventing that right now, but perhaps with this information you will be able to provide your specialized opinion.


> **bab1 said:**
> My setup at home is a workgroup (no domain controller).  
I have only local accounts on my Windows  hosts and  use
/etc/passwd on each of my Ubuntu hosts.  In doing this I have the
EXACT SAME login/password combo's on each host.  Samba needs
this.  If you insist on different login/passwords, you will have
to create maps between the client login and the server login. 
This is done in the /etc/smbusers file.  Either way Samba will
compare the computer users login to its own Samba users login.

All of my Windows hosts have the user name of **Rick, **but my Ubuntu host uses **rickatnight11**.  I'm not sure if that matters in this case, since I assume that Ubuntu will, by default, send the **rickatnight11** username and password for authentication.  Upon failure (Windows doesn't know that username) I would assume it would prompt for the actual username and password, which I could then input and save to the keyring if I so choose.
[U][B][COLOR=Blue]

[/COLOR][/B][/U]> **bab1 said:**
> We need to add the Samba users now.  These users are compared to the computer users and allowed access to Samba.
Would this be the users of the local Ubuntu host, so that they may have access to the smb daemon, or is this a list of users of the Windows machines I want to connect to?
  
> **bab1 said:**
> <opinion> I believe that if you do not add a user (say user1) to
the Samba users database he will not be able to access the
shares.  If user1 is not the logged in user but can supply
user1's correct login/password he gets access.  No login or
password is needed if the logged in user is in the database. 
Said in short: You should to be in the Samba user database for
access.  I do not allow guest access.
I *would* like guest access, but like I said above, sharing from Ubuntu is not a priority.


Thanks again for all your help.  In summation, I would like to keep my network in what I believe to be the standard default configuration: DSL modem to Netgear router (DHCP, Port Forwarding/Triggering, DNS, etc) to wireless and wired (series of passive switches).  Because I like keeping my "always on" devices as low-powered as possible, I prefer that the router keep these responsibilities, I will soon be moving my file storage to a low-power NAS, and I will be treating all of my computers as "clients".  I would like those clients to be able to easily browse the shares of the other clients.  Windows can currently do this.  Ubuntu cannot see the Windows shares.  Thank you for all of your solutions.  I hope this information will help you wean it down a little further.

---

### Post by dmizer on 2008-11-06
> **Halbarad said:**
> Just a naive question: in case I wish to throw away all the Microsoft stuff and only use Linux in my local network, is there a non-samba approach to network sharing and browsing for Linux machines? (in the hope that the Linux way would be more clearly defined and consistent.)

NFS indeed. See the fourth link in my sig for directions on how to configure that. The method works for all Linux clients I've tried (including Fedora).

---

### Post by bab1 on 2008-11-06
@Rick,

I see what you are trying to do.  If you want only smb client functionality you wil need to install smbfs. ```
sudo apt-get install smbfs
```  This should install the client and the supporting libs.

At this point you *should* be able to browse the shares on the Windows hosts using Nautilus. Vista might be a problem as it has upgraded encryption.

> ...I will be treating all of my computers as "clients". I would like those clients to be able to easily browse the shares of the other clients. Windows can currently do this.

Windows does this because the BOTH the client and server are incorporated into "windows sharing".  See post #84 of this thread. In this post the Ubuntu host (malibu) is requesting info from an XP host (manila).  ```
Domain=[MANILA] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
```

Later I will answer all of your points in your previous post if you like.

---

### Post by rickatnight11 on 2008-11-12
Thanks again, bab1, for all your help.  For some reason the thread didn't email that you had responded and I am just now checking it.  After installing a bunch of updates today (I have been away from my Ubuntu machine since I last posted) and having yet to try any of your suggestions I tried to access my Windows SMB network.  Lo and behold it popped right up!  I don't know if those updates fixed something or if I just was not being patient before, but everything is working swimmingly.

---

### Post by SonicSteve on 2008-11-18
I'm sure someone has mentioned this already, the problem is still there on initial installation of Ibex 8.10. sighh

---

### Post by rickatnight11 on 2008-11-18
Mine resolved itself somehow.

---

### Post by rectangle on 2008-11-26
Fixed for me since update today. Hooray!

---

### Post by celem on 2008-11-26
I felt that I'd chime in with a little more info. In the process of trying to build a new system that fully suits me, in the past couple of months, I had loaded and tried out about eight different distributions, both KDE and Gnome. I can report that this problem is present in both KDE and Gnome. Also, even though reordering the hots, lmhost, etc. in /etc/smb.conf will make the shares visible, the process remains very, very slow. I was also building up a new XP machine and was amazed at how it could access the same shares as fast as if they were on the same box.

---

### Post by shwallace on 2008-11-28
I'm really miffed that nautilus doesn't allow me to browse my network computers without typing in the whole IP address and share name. I finally put a bookmark in the network file browser so I don't have to type in the entire address each time I want to access a shared file.

Thanks to Gramps and others for that suggestion!

---

### Post by gregphil on 2008-11-28
Before you all get to carried away, Samba **browsing** of Windows **authenticated** shares is currently broken (as of hardy and above).  Hardy uses a new gnome library to do authentication for GUI applications, and it is broken.  Windows does not allow other machines to even get a list of the available shares, if Windows shares are configured so authentication is required, and the other machine (ubuntu) does not offer up the correct password.

You could 

a) wait for a fix to the gnome library involved

b) change the shares on the windows boxes to allow anonymous connections (which would be a huge security risk)

c) From the client machine, enter the **FULL path** to the **share** on the Windows box (browsing is broken but actual connections still work)

d) Try to setup some other sharing protocol (other than Samba)

I have been waiting for a fix since Hardy came out, I really hoped the 8.10 update would fix it, but no such luck.

---

### Post by SonicSteve on 2008-11-29
It seems we will have to wait. I have tried many of the suggestions in this thread and every time some one says they've been fixed I get hopeful. For now I just have to use KDE. A previous user said that samba browsing in KDE was broken as well but I haven't found that at all.

I still use Gnome as the default session but when browsing new shares I use Dolphin which uses the KDE samba backend (assuming that you installed either all of KDE or enough for Samba's sake)

---

### Post by gregphil on 2008-11-30
I agree, I just use kubuntu 8.10 for now, which does not have the Windows share browsing problem because it does not use the gnone library for authentication.

See:  (applies to all authenticted shares, not just ADS networks)
[]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520")[Bug #207072 in gvfs (Ubuntu Hardy): “nautilus does not display samba shares for machines inside an ADS network.”]("https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072")

---

### Post by celem on 2008-12-07
Even though I could get a connection using the changes to smb.conf that I discussed above I finally couldn't stand any longer how slow the process was, so I reserved my PC's IP in my router and edited it into the hosts file. NOW i connect to my Windows shares just as fast as Windows itself does.

It's a shame that Linux can be Plug-and-Play with smbclient services!

---

### Post by SonicSteve on 2009-03-27
It seems that the waiting method has paid off.
I upgraded my workstation at school today from Hardy to Intrepid. After installing the updates I can now browse all computers in the domain and see all the shares without having to supply either IP address or share names. 

I didn't install samba or anything. It just works, just like the way it used to.

---

