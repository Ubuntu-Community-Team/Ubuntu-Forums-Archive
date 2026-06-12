---
title: "Sharing a Windows computer and Ubuntu computer"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by anewguy on 2010-08-03
I did this once a few years ago, but had to get rid of the set up I had then.  Since that time, I seem to have lost my ability to understand what to do.  I thought I had done this samba, but I'm not sure.

What I have:

- 1 laptop running Windows XP
- 1 desktop running Windows XP
- 1 netbook dual-booting Windows XP and Ubuntu 10.04

What I want to do:

- I would like the Windows XP laptop and netbook to be able to see and use an external USB drive and printer on the Windows XP desktop

- I would like the netbook running 10.04 to be able to see and use an external USB drive and printer on the Windows XP desktop


What I *think* I remember:

- I didn't have any computer set up as a server


What I need to know:

- how the heck do I do this? ;)
- do I need to install printer driver software on all the machines in order to use the printer on the Windows XP desktop?


Any guidance, suggestions, even comments calling me stupid ;) are welcome!

Thanks in advance!
Dave ;)

---

### Post by mastablasta on 2010-08-03
XP to XP is easy. you need to right click the folder or disk you would like to share and then enable sharing (you also set any other preferences like reading, writing, password...). same goes for printer. just share it with other users on the network (go to printer and faxes, select printer then right click->preferences->sharing)
 
10.04 to XP for files is the same ( i dont' know how is with the printer in this case and i am also curious about that). Once you set XP disk or folder as shared you can access it form linux through "network" in the file browser. 
 
XP to linux is a bit different as it seems linux needs to have something installed first (or am i wrong?).

---

### Post by Elmer Fudd on 2010-08-03
What have you tried so far? Where are you getting stuck.

Yes, I believe that you must have printer drivers installed on each computer using the shared printer. I just shared a printer on an XP desktop machine. 10.04 on my laptop found the printer, downloaded and installed the driver (strangly my Win7 partition didn't).

---

### Post by soldier1st on 2010-08-03
to share files on ubuntu you need to install samba by simply sharing a folder as that will start the install but then you will need to open the shared folders in system/administration but it will be hidden but after that it will ask to install 2 more things and allow it but don't add anything but as far as a printer goes i am trying to do that same setup with xp and no luck as of yet but with files it is possible.

---

### Post by mastablasta on 2010-08-03
> **Elmer Fudd said:**
>  
 I just shared a printer on an XP desktop machine. 10.04 on my laptop found the printer, downloaded and installed the driver (strangly my Win7 partition didn't).
 
strangely.... if it's a new printer you are installing then you received the drivers on a CD with the printer and you just pop it in. if it's a bit older printer then maybe there are no drivers for Win7. you should contact the printer manufacturer.

---

### Post by tarps87 on 2010-08-03
For this you will need samba client installed on the Ubuntu machine and also cups (probably both already installed).

On the xp desktop right click the USB drive an select share, the options are fairly self explanatory. You all so need to set the printer as shared, right click share.

From Ubuntu you should be able to select add new printer and it should automatically be detected, that is if the netbook is on the network.
For the network share, the quick way, in the address bar of nautilus type:
smb://*ipaddres_of_xp_desktop*

Let us know what happens

---

### Post by Elmer Fudd on 2010-08-03
> **mastablasta said:**
> strangely.... if it's a new printer you are installing then you received the drivers on a CD with the printer and you just pop it in. if it's a bit older printer then maybe there are no drivers for Win7. you should contact the printer manufacturer.

I am a pilot. I was at an FBO where I just set their pilot briefing room printer to share. I had no install disks. I was impressed the Lucid saw the printer on the wireless network, went out and got the driver and just worked. Win7 did not. No question that I could have manually installed the drivers (HP printer) and made it work, just didn't need to.

---

### Post by gordintoronto on 2010-08-03
The shared printer setup will depend on the brand and model of printer. Some brands have not been very Linux-friendly...

So what is the brand and model of the printer?

---

### Post by anewguy on 2010-08-03
Okay, I'm getting ready to try this.

I will install Samba and I'll check to be sure cups is installed.  In Samba's config file I seem to remember a place to set the domain name.  I would prefer not to use the Windows default of MSHOME, so I assume:

- change the domain name on all of the computers to what I want to use, as an example "domainx".  
- change the samba config file to use "domainx"

Also, the printer is a Brother Laser printer which 10.04 detected fine when my desktop still had ubuntu on it, so I assume it should be fine when I share it.

It may take me a day or 2 to try to get this all set up, but I'll let you know how it goes!

Thanks for all the input!

Dave ;)

---

### Post by mapes12 on 2010-08-04
I think this may be easier to do than you think.

Basically, your question is how to use the printer connected to the XP machine from the other machines.

If your LAN uses a conventional router then just go to the XP machine with the printer connected to it and enable "sharing" for that printer. All your other machines should then be able to see it and use it. To see it from the Ubu machine go Places>Network>(the name of your windoze workgroup)>(the name of the printer).

There should be no need to deploy Samba which could cause problems in itself.

Provided the XP machine has the printer driver installed then there will be no need to deploy that driver on any other machine. The XP client will provide this.  

Let us know how you get on.

Mark

---

### Post by anewguy on 2010-08-04
I also want to share an external disk drive from the XP desktop.  As far as I know, this requires Samba.  Add to that a workgroup name, and I believe Samba is needed.  At any rate, slowly working on things as I haven't had much time.  Will post back with results.

Dave

---

### Post by mapes12 on 2010-08-05
> I also want to share an external disk drive from the XP desktop.Same as the printer. Plug it in and enable "sharing" in windoze. In Ubu Places>Network>(your windoze workgroup)>(your drive).

---

### Post by anewguy on 2010-08-13
Enabled sharing on the external drives and the printer.  Went to my netbook (ubuntu 10.04), then places and network.  Showed Windows Network.  Clicked on that and gave an error about smb and passwords.  Edited samba.config and changed the workgroup from WORKGROUP to my actual workgroup name, then rebooted.  Now when I go to places/network it show Windows Network - click on it and get error "unable to get share list from server".

On the Windows machine, I just named the individual devices things like "volsave" - I don't have anything like the //node/path syntax - does that matter?

Dave

---

### Post by mapes12 on 2010-08-14
> "unable to get share list from server".This indicates that windoze does not have sharing configured correctly. Sharing needs to be enabled with an Administrator account otherwise it doesn't work.

---

### Post by mastablasta on 2010-08-14
i just remembered, in windows you don't actually need to install drivers in order to work with the shared printer (unless the printer is connected via LAN on it's own). you just share the printer.

I remembered because i have like 7 printers at work to which i can print to. and i can add them more (from across the company) eventhough i do not have the permission to install anything.

---

### Post by anewguy on 2010-08-14
> **mapes12 said:**
> This indicates that windoze does not have sharing configured correctly. Sharing needs to be enabled with an Administrator account otherwise it doesn't work.

I am an administrator account.

---

### Post by Morbius1 on 2010-08-14
From the Linux machine:

(1) Post the output of the following command:
```
smbtree
```(2) Try to access the WinXP machine ( or any other machine ) by ip address. In a terminal type:
```
nautilus smb://192.168.0.100
```[COLOR=Blue][I]Changing 192.168.0.100 to the ip address of the machine you're trying to access.

[/I][COLOR=Black]If you make a connection "bookmark" it: Nautilus > Bookmarks > Add Bookmark. It will show up on the left panel of Nautilus like a "mapped drive" does in Windows.[/COLOR][/COLOR]

---

### Post by anewguy on 2010-08-14
I'll try those when I'm home so I can get at my netbook and Windows machine together.  Thanks.

I did some more searching on the web and found a few things I thought I'd ask about also:

- there is some mention of a bug in gvcs(spelling may be wrong there) that causes the Windows network devices not to show.  This might explain why it shows Windows Networks under places/networks, but under that it does not show my Windows shared documents or devices.

- there is mention of putting a user name in the samba users.  From what I understand, this would involve both the section in the samba config file as well as using the samba command to add a user.  What user would this be - the Windows user (which at this point in time has no password [yikes!], my Ubuntu userid and password, or something completely different?

Thanks again!

Dave ;)

---

### Post by Morbius1 on 2010-08-14
> there is mention of putting a user name in the samba users.  From what I  understand, this would involve both the section in the samba config  file as well as using the samba command to add a user.  What user would  this be - the Windows user (which at this point in time has no password  [yikes!], my Ubuntu userid and password, or something completely  different?You're trying to access a windows share so there is no need to create a user on the Ubuntu machine. 

You would only need to create a samba user if you created a password protected share on Ubuntu. If you created a guest share on Ubuntu you wouldn't even have to do that. 

If you're specifically referring to the comment in almost all Samba Howto's about the login username and password of the client and the samba usernames and passwords having to match exactly - that's all drivel. The author is confused. And if you think about it is a complete violation of security and privacy.

---

### Post by anewguy on 2010-08-14
Thanks for the latest info - both on the commands to try and on the user/password (I thought that would only make sense for an incoming connection).

As far as smbtree goes, I get the following:

cli_start_connection: failed to connect to 10.0.0.2<20> (10.0.0.2). Error: NT_STATUS_UNSUCCESSFUL

The attempt with nauilus returns:

Error:  Failed to retrieve share list from server

So, here's a thought:  I'm running ZoneAlarm for a firewall on the Windows PC - do I need to open something up in it for this to work?

EDIT:  Just checked the ZoneAlarm log in Windows - it is blocking the traffic.  Any ideas on how to get around that would be appreciated!  In the mean time, I'm going to search the net and see if anything shows up.

Thanks again!

Dave ;)

---

### Post by Morbius1 on 2010-08-14
>  So, here's a thought:  I'm running ZoneAlarm for a firewall on the  Windows PC - do I need to open something up in it for this to work?It seems you're doing a fine job resolving the problem on your own. I don't know Zone Alarm myself but you need to open up the samba ports to make this work. If I remember correctly the following ports ( tcp and udp ) need to be opened:
> 135
137
138
139
445                      

---

### Post by anewguy on 2010-08-14
Okay, I had to allow ZoneAlarm to allow traffic for subnet 10.0.0.1/255.255.255.0 (why my Netgear router changed the dang addresses from 192. to 10. is beyond me, but it explained why I hadn't been able to get into the router for a while - I can now).

Via smbtree, I see a lot of stuff on the net.  I see the external hard drive in nautilus if I use smb://my-pc-name - it shows on the right for available places.  If i go to networks, my Windows PC shows now, but there are some things showing there I don't know what they are and why they are there - perhaps you can help.

I'm sharing the external hard drive as volsave(F).  Since I have no disk currently in the external DVD/RW, it shows as dvd-ram - the name I gave in Windows also.  Now for the ones I don't understand:

[LIST]
[*]A folder called "ADMIN$".  If I click on it it wants a password, but since I have no password currently on my Windows account I can never get passed the prompt.  But.....what is this share?
[*]A folder called "C$" - same password problem.  Again, what is this share?
[*]A folder called F$ with the same password problem.  Again, what is this share?
[*]A share called "print$".  I can open it, but there's nothing there regarding my printers.
[/LIST]

I assume C$ and F$ are referring to my C: and F: drives on my Windows box, but how did they become shared (F I can understand from the standpoint it's my external hard drive, but it makes no sense to me to show that and be password protected and yet show the volume and be open [I did set it up to share the volume].

ADMIN$ I've got no clue on - the same for print$

Any additional help at this point would be greatly appreciated!

Thanks for the help so far!

Dave ;)

---

### Post by Morbius1 on 2010-08-14
Everything with a "$" at the end of it is what Microsoft calls an administrative share. You could actually access those shares if you knew or had the Windows' administrators password. Windows shows you those shares as available across the network because they're insane. The linux equivalent would be to show you "/" - the root directory - and have it accessible if you supplied root's password.

The important thing is that it shows you the share that you shared yourself.

---

### Post by mapes12 on 2010-08-14
It looks like that when you installed Windoze you set up a password for Admin tasks. I haven't installed an MS system in ages so I can't remember at what stage of the install this may have been prompted.

However, you need to recover the password. I found this:-

[http://pubs.logicalexpressions.com/pub0009/lpmarticle.asp?id=305](http://pubs.logicalexpressions.com/pub0009/lpmarticle.asp?id=305)

EDIT - If a password was not set then try just clicking "OK" with nothing in the password field. I remember this works in MS if no password was set.

[Some more resources]("http://lmgtfy.com/?q=ADMIN$ password")

---

### Post by Morbius1 on 2010-08-14
It would be far better to share "C" ( and thus remove the "$" ) than to activate the administrators account. Activating the administrator account on Windows would be the same thing as activating the root account on Linux

---

### Post by mapes12 on 2010-08-14
> A folder called "C$" - same password problem. Again, what is this share?I think C:\ has the same password authentication issue.

---

### Post by Morbius1 on 2010-08-14
You shouldn't be trying to access "C" in whatever form at all. It's where the WinXP system directories are located. Windows is far too vulnerable to chare C. In fact if you try to share "C" you will get a warning that states something like this: " Are you insane ?" - I'm paraphrasing :)

Actually it says this:
> To protect your computer from unauthorized access, sharing the root of a  drive is not recommended.  If you understand the risk but still want to  share the root of the drive, click here

Here's something more official than my ranting: [http://www.windowsnetworking.com/kbase/WindowsTips/WindowsXP/AdminTips/Network/DisableWindowsNTW2KXPHiddenAdministrativeShares.html](http://www.windowsnetworking.com/kbase/WindowsTips/WindowsXP/AdminTips/Network/DisableWindowsNTW2KXPHiddenAdministrativeShares.html)

> The system automatically creates hidden "**administrative shares**" for its  logical drives C:, D:, and so forth which it names C$, D$ and so forth. It also  creates the admin$ hidden share for to the \winnt folder. These shares are  designed for remote access support by domain administrators. 

---

### Post by mapes12 on 2010-08-14
> It would be far better to share "C"Sorry Morbius1 but I couldn't resist your previous quote :rolleyes:

and you are spot on about not enabling share on C:\

---

### Post by anewguy on 2010-08-15
Yeah, I'm smart enough not to share my Windows drive.  All I did was enable sharing on the 2 external devices and my printer - the rest just showed up.  Checking properties on my "C:" drive shows I'm not sharing the drive.  If I was a guessing man, I'd say it has something to do with sharing "My Shared Documents" since it is on drive "C:".  I neve asked to share any documents either, so I guess this must be another added "feature" of Windows.

Dave ;)

---

### Post by willz06jw on 2010-08-20
Howdy,

Use the config-system-samba package (it's a samba GUI). It will make sure you don't overlook some small sambatism. 

If you search in the Ubuntu Software Center for Samba, it will be one of the ones listed (it will be listed as just "Samba" stragely). 

This will put a link to the GUI in your system/administration menu.

I removed some of the security and everything started working hunkey-dory.

Have a good one,
Will from Texas

---

### Post by Morbius1 on 2010-08-20
willz06jw,
> **anewguy said:**
> ...

What I want to do:

- I would like the Windows XP laptop and netbook to be able to see and use an external USB drive and printer on the Windows XP desktop

- I would like the netbook running 10.04 to be able to see and use an external USB drive and printer on the Windows XP desktop

He's trying to access a Windows share and printer. Installing a Samba server GUI isn't going to be of much help to him. Besides there's a Samba GUI already built in to Nautilus.

---

### Post by mapes12 on 2010-08-21
> **Morbius1 said:**
> willz06jw,

He's trying to access a Windows share and printer. Installing a Samba server GUI isn't going to be of much help to him. Besides there's a Samba GUI already built in to Nautilus.Yep! The work needs to be done on the windoze machine.

---

