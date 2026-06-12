---
title: "Cannot Access Microsoft Workgroup on Windows 7 PC with SAMBA"
date: 2015-02-20
forum: Networking &amp; Wireless
---

### Post by oldefoxx on 2015-02-20
Running Ubuntu 14.04 on laptop, and have Virtualbox installed with Windows 2000 client.

Want to share home workgroup on wife's pc as she has printer attached.  She is eunning Windows 7.  Have some folders and printer flagged as shared on her pc.

Searched Ubuntu Software Center using term SAMBA and tried each package in effort to be able to browse Microsoft Workgroup for wife's PC.  Nothing shows up.

Tried copy and paste of several /etc/samba/smb.conf examples found, but most complained of improper parameters, and the Microsoft Workgroup shows up under Network but with nothing in it.

Tried loading up Windows 2000 client and checked under Network/Computens Near Me. and can see and access wife's pc that way.  Want to do same from Ubuntu with Samba.

Another related problem, but somehow involves Linksys EA3500 SmartWiFi router:  Changed pc name under Windows 2000, and both old and  new names show up in the Computers Near Me view, though the old name is no longer valid.  Doesn't seem to be a way to remove the invalid ones.

Any ideas?

P.s.  Read that smp4k is intended for KDE, not Gnome.  So what is Gnome equivalent?

---

### Post by SeijiSensei on 2015-02-20
Samba is primarily designed as a server program for sharing share data on a Linux machine to Windows computers.  It sounds like you're asking about the reverse situation, connecting to data and printers shared from your wife's Windows computer.  Am I right?

If so there are a variety of methods to do this.  See:

[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)
[http://www.7tutorials.com/how-access-windows-7-shared-folders-ubuntu](http://www.7tutorials.com/how-access-windows-7-shared-folders-ubuntu)

Try rebooting your router to fix the duplicate name problem.  If that doesn't help reboot all the computers.

If you happen to be using KDE, you can type a URL of the form smb://server/share into the address line in Dolphin. This may also work in Nautilus, but I can't say for sure.

If you want to use your wife's printer, the most direct method is to access the "CUPS" printing system on your computer by pointing your browser to [http://localhost:631/](http://localhost:631/).  Follow the Administration link, and click on Add Printer.  Choose "Windows Printer via SAMBA" and enter the name or IP address of your wife's machine and the name assigned to the shared printer in the smb://server/printername format.  Enter your regular Ubuntu username and password when prompted.

---

### Post by oldefoxx on 2015-02-21
Thanks for replying.  Yes, idea is to use my laptop/Ubuntu in den to access printer on wife's desktop/Win7 pc on other side of house.  I'm disabled and pretty much confined to my recliner.

Resetting router and restarting pcs has done nothing to  help.  If there is a file to be edited to remove invalid Windows Network icons, I don't know what it is.

Workgroup shows up in Ubuntu Network, but won't browse or let me connect to server.  Efforrts to do either returns nothing or reportd invalid URL.  SMB4K asks for UNC Address, which I guess I will need access to wide's pc to determine.

I removed SAMBA since you said I don't need it.  I can use VM client Win2k to see contents in workgroup, but I get request for Network Password id I try to open or explore wife's PC.  Not sure what password is sought, but suppose I need access to her pc to resolve this.

So  still stuck and needing more instructions and/or details.  Thanks for your help.

---

### Post by SeijiSensei on 2015-02-21
Let's put Samba back and try a test using the terminal and the command-line smbclient program. Open a terminal and type the following.  Enter your Ubuntu login password whenever prompted:
```

sudo apt-get update
sudo apt-get install smbclient
smbclient -L localhost 

```
After entering your password, you should see a listing like this:
```

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (fuzzface server (Samba, Ubuntu))
        Public          Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

        Server               Comment
        ---------            -------
        FUZZFACE             fuzzface server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        WORKGROUP            FUZZFACE

```
"FUZZFACE" is the name of my Ubuntu machine.  It's running an instance of the Samba server and sharing the directory /home/username/Public.  The server component was installed and started automatically as a dependency to smbclient.

I can connect to that Public share on my local machine by typing the command "smbclient //localhost/Public".  I can also list the shares on other machines with "smbclient -L machine_name".  See if you can connect to a share on your wife's machine with "smbclient //her_machine/some_sharename".  If Ubuntu cannot resolve the name "her_machine", use its IP address like "smbclient -L ip.addr.of.machine".  If you can connect using smbclient, you can connect from the GUI as well.  An even better method, if your wife's machine is visible all the time, is to add an entry to /etc/fstab so the shares on her machine will be [mounted every time you boot]("https://wiki.ubuntu.com/MountWindowsSharesPermanently").

---

### Post by oldefoxx on 2015-02-22
I appreciate your help.  while waiting responsds (from you or possibly othere), I've continued online searches,putting the question in different termd, to see what I could turn up with.  There is  a slew of links out there, but they are over my head.  One says do it this way, then another says go that way, and some show dialog windows that don't match what I encounter.

Some indicate using smb4k,,but elsewhere, I find  that smb4k means samba management block for KDE.  The /etc/samba/smb.conf file that installs with samba complains of two invalid value assignments.

My Linksys SmartWiFi EA3500 wired/wireless router has the address of 192.168.1.1.  My Wife's Windows 7 pc has the ip of 192.168.1.106.  My laptop has two possible addresses, 192.168.1.107 (wired) or 192.168.1.45 (wireless).  My wife's pc is named Betty-HP.
Retaining an old pc model number, my laptop is named gm5661e..  I have two users on my laptop thst I want to have access to my wife's printer:  root and oldefoxx.

My question now is, what should a fairly somple /etc/damba/smb.conf look like thst should make this happen?

Here is what I got when I followed your request:

root@oldefoxx-Satellite-L355:~# smbclient -L localhost
Enter root's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
root@oldefoxx-Satellite-L355:~# 

Note the difference in thisas to my pc name, and the Don-fm5661e that shows up in the workgroup when I check the contents of Workgroupd from my Vm Windows client on my laptop.

---

### Post by bab1 on 2015-02-23
> **oldefoxx said:**
> I appreciate your help.  while waiting responsds (from you or possibly othere), I've continued online searches,putting the question in different termd, to see what I could turn up with.  There is  a slew of links out there, but they are over my head.  One says do it this way, then another says go that way, and some show dialog windows that don't match what I encounter.

Some indicate using smb4k,,but elsewhere, I find  that smb4k means samba management block for KDE.  The /etc/samba/smb.conf file that installs with samba complains of two invalid value assignments.

My Linksys SmartWiFi EA3500 wired/wireless router has the address of 192.168.1.1.  My Wife's Windows 7 pc has the ip of 192.168.1.106.  My laptop has two possible addresses, 192.168.1.107 (wired) or 192.168.1.45 (wireless).  My wife's pc is named Betty-HP.
Retaining an old pc model number, my laptop is named gm5661e..  I have two users on my laptop thst I want to have access to my wife's printer:  root and oldefoxx.

My question now is, what should a fairly somple /etc/damba/smb.conf look like thst should make this happen?

Here is what I got when I followed your request:

root@oldefoxx-Satellite-L355:~# smbclient -L localhost
Enter root's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
root@oldefoxx-Satellite-L355:~# 

Note the difference in thisas to my pc name, and the Don-fm5661e that shows up in the workgroup when I check the contents of Workgroupd from my Vm Windows client on my laptop.
It is never a good idea to use the root account for regular user needs.  Your normal user account should be able to use the command *smbclient * successfully. 

The default smb.conf file is all you need to act as a Samba client (smbclient).  You don't need to add anything.  Your problem appears to be user authentication  ```
[COLOR="#FF0000"]NT_STATUS_LOGON_FAILURE[/COLOR]
```...on the other hand, why are you using the *localhost* name.  That doesn't work across the network.  The proper way is to use the host name, if you are using the *hosts *parameter in the smb.conf file), or the NETBIOS name if you are using the *bcast* parameter.

If you post the output of ```
smbclient **-d3** -L localhost
```...using your normal user account we should have enough debug info to see what the problem is.

---

### Post by SeijiSensei on 2015-02-23
> ...on the other hand, why are you using the localhost name.

I told the OP to start with localhost because installing smbclient also installs an instance of the Samba server on the machine.  It begins serving $HOME/Public when installed.  So as a simple basic test, I suggested he start first by connecting to the new server on localhost.  If that worked, he could try connecting to his wife's machine over the network.

oldefoxx, you shouldn't use root for any of these tasks. Ubuntu doesn't create a Samba userid for the root user since the [root user has no password in Ubuntu]("https://help.ubuntu.com/community/RootSudo").  Just open a terminal in your username and follow the steps I gave you above. If prompted, enter your Ubuntu username and password.  

If you have been trying all sorts of documentation from all over the Internet, the chances are good that your system is now sufficiently unique that it could be difficult for us to diagnose.  That's certainly true if you have a root password, unless you are a really experienced Linux user and know what you're doing.  If so, carry on.  If not, I would strongly recommend that you reinstall Ubuntu, then install smbclient and try the steps above.

---

### Post by bab1 on 2015-02-23
> **SeijiSensei said:**
> I told the OP to start with localhost because installing smbclient also installs an instance of the Samba server on the machine.  It begins serving $HOME/Public when installed.  So as a simple basic test, I suggested he start first by connecting to the new server on localhost.  If that worked, he could try connecting to his wife's machine over the network.

oldefoxx, you shouldn't use root for any of these tasks. Ubuntu doesn't create a Samba userid for the root user since the [root user has no password in Ubuntu]("https://help.ubuntu.com/community/RootSudo").  Just open a terminal in your username and follow the steps I gave you above. If prompted, enter your Ubuntu username and password.  

If you have been trying all sorts of documentation from all over the Internet, the chances are good that your system is now sufficiently unique that it could be difficult for us to diagnose.  That's certainly true if you have a root password, unless you are a really experienced Linux user and know what you're doing.  If so, carry on.  If not, I would strongly recommend that you reinstall Ubuntu, then install smbclient and try the steps above.
You shouldn't need to reinstall the entire OS.  I doubt you even need to reinstall Samba.  The  smb.conf is the only conf file for Samba standalone configuration.

Let's see what we get from```
smbclient -d3 -L locahost 

or 

smbclient  -d3 -L <server_name>
``` ...where <server_name> is the name of the machine you are trying to connect to.

---

### Post by oldefoxx on 2015-02-24
oldefoxx@oldefoxx-Satellite-L355:~$ smbclient -d3 -L Betty-HP
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
added interface wlan0 ip=192.168.1.107 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter oldefoxx's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name Betty-HP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name Betty-HP<0x20>
resolve_hosts: Attempting host lookup for name Betty-HP<0x20>
Connecting to 192.168.1.106 at port 445
E2BIG: convert_string(UTF-8,CP850): srclen=24 destlen=16 - 'OLDEFOXX-SATELLITE-L355'
Connecting to 192.168.1.106 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb9425a60] mpx_fde[(nil)] fd[7] - disabling
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE
oldefoxx@oldefoxx-Satellite-L355:~$
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
This is what catches my eve as I go over the above:
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied

tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied

samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb9425a60] mpx_fde[(nil)] fd[7] - disabling

Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE

My first reaction is that oldeffoxx may not be a user on my wife's pc.  Likely my real name was used on her machine, which is my
First M. Last.  I could add that as a user on Ubuntu, or go  with Administrator, but neither is currently a Ubuntu user or a smbclient.

Thank you for joining the discussion, Bab1.  I've long known and appreciated the fact that under the right circumstance, the more active minds involved, the more certainty of eventual success.

---

### Post by coldraven on 2015-02-24
> This may also work in Nautilus, but I can't say for sure.
In Nautilus you can select File>Connect to server or by pressing Ctrl+L and then pasting the address into the location bar.
Tip: Then save it as a bookmark!
As the song goes "this much I know" :)

---

### Post by SeijiSensei on 2015-02-24
> **oldefoxx said:**
> My first reaction is that oldeffoxx may not be a user on my wife's pc.  Likely my real name was used on her machine, which is my First M. Last.  I could add that as a user on Ubuntu, or go  with Administrator, but neither is currently a Ubuntu user or a smbclient.
You don't need a matching user on the client.  Just pass the username string like this:
```
smbclient -U "First M. Last" -L Betty-HP
```
I avoid usernames with embedded spaces, so I can't guarantee this will work, but give it a try.  

If you continue to have authentication problems, I'd rename the account on Windows to oldefoxx for simplicity.

---

### Post by bab1 on 2015-02-24
> **oldefoxx said:**
> 
```
oldefoxx@oldefoxx-Satellite-L355:~$ smbclient -d3 -L Betty-HP
....
[COLOR="#0000CD"][B]E2BIG: convert_string(UTF-8,CP850): srclen=24 destlen=16 - 'OLDEFOXX-SATELLITE-L355'
Connecting to 192.168.1.106 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb9425a60] mpx_fde[(nil)] fd[7] - disabling[/B][/COLOR]
...
[COLOR="#FF0000"]session setup failed: NT_STATUS_LOGON_FAILURE[/COLOR]
oldefoxx@oldefoxx-Satellite-L355:~$
```
It helps if you post the output of your commands between [noparse]```
 
```[/noparse] code blocks.  That can be easily done by clicking on the [SIZE=5]**#**[/SIZE] icon located at the top right of the advanced reply editor.
> 

This is what catches my eve as I go over the above:
```
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied

tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied

samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb9425a60] mpx_fde[(nil)] fd[7] - disabling

Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE
```
IMO there are only 2 pertinent  sections.  The one in blue above is caused when you have a computer name (NETBIOS NAME) of more then 15 characters.  Ultimately the error noted in red above is the problem at hand.
> 
My first reaction is that oldeffoxx may not be a user on my wife's pc.  Likely my real name was used on her machine, which is my
First M. Last.  I could add that as a user on Ubuntu, or go  with Administrator, but neither is currently a Ubuntu user or a smbclient.

You can map those names if you don't want to change thats what the */etc/samba/smbusers * file is for.  The format is ```
<Linux user> = <Windows user>
```
> 
Thank you for joining the discussion, Bab1.  I've long known and appreciated the fact that under the right circumstance, the more active minds involved, the more certainty of eventual success.
Hmmm, I find multiple _opinions _ bothersome.  I'd be looking to diagnose the problem from facts.

---

### Post by oldefoxx on 2015-02-24
The Ubuntu Software Center tells me that Nautilus can be removed, but it does not show up in Dash.  What comes up is Nautilus-Action Configuration Tool.  Launching that shows all choices greyed out.  Typing nautilusin the terminal pops up a ~/<userid> view and goes right back to the terminal..  Typing gksudo nautilus brings up another view of Home which only shows the Desktop.    If I select Network/Browse Network returns an error that This Location could not be displayed.  Sorry, could not display all the contents of "network:///".  Operation not supported.

Whatever Nautilus is meant to be, it does not equate to the way it responds on my current setup of Ubuntu.  Nothing suggested thus far has done much to stear me towards a solution.  Any solution.  So what's the answer to my situation?  More in depth help is needed.
But all efforts thus far are appreciated.

---

### Post by coldraven on 2015-02-25
> Running Ubuntu 14.04 on laptop,
> The Ubuntu Software Center tells me that Nautilus can be removed, but it does not show up in Dash
If you are running the default Ubuntu 14.04 then Nautilus is the file manager that opens when you click the second icon from the top in the launcher. If you hover over the icon it says "Files". If you have somehow deleted it,run this to restore the launcher icons.
```
unity --reset-icons
```

---

### Post by oldefoxx on 2015-02-25
My wife and I are both challenged physically,  I can't stand and walk without a walker, she has lung and heart issues, so I am restricted as to when she feels capable of fetching my narrow walker, and she then helping me to her crafts room where her pc is.  Sometimes we go days or weeks between periods when she is up to it.  We are in a bad episode period right now.  Just trying to explain why I can't immediately rush to her pc to check things out there.  What I can do from my laptop I am up to trying daily. 

Now I have something else to relate.  

Trying some examples of how to do certain things, I have at last gotten Connect to Server to return a dialog box which says this:

Password required for betty-hp

Username oldefoxx

Domain    WORKGROUP

Password  ____________

[x]  Forget password immediately
[  ]  Remember password until logout
[  ]  Remember forever 

         Cancel       Connect

I've tried using my oldefoxx name and password, First M. Last name and password, and Administrator with Windows7 passwprd.  None of these work.  What should I be loking for now?

Oh, as to what I tried that seemed to halp, I tried using a cat command to copy my passwprd file over my samba passord file.  I just did a copy and paste of the provided example.

---

### Post by oldefoxx on 2015-02-25
I found where I can  access the smbusers file.  getting to it with sudo gedit, I find only the followinf in it:

# Unix_name = SMB_Name1 SMB_Name2 ...
root = Administrator
nobody = guest smbguest pcguest

---

### Post by oldefoxx on 2015-02-25
Okay!  Finally made some progress.  You know, my posts and yours have gone over to page 2, and I was still going to page 1, so I fell behind recent activity.  Now I am a bit caught up.  That info about my Ubuntu host name being too long made me look at how to change the name permanently, and I changed it in the /etc/hostname and the /etc/hosts files and did a reboot.  Now I see my pc, my wife's pc, and the SmartWiFi,  as well as the Windows Workgroup folder.

But when I click on my wife's pc, I get this error response:

Unable to access location

Failed to retrieve share list from server.   No route to host.

So what have I got to do to fix this?  While I await a possible reply, I will conduct my own search.  I mean I have to try to so some things for myself, right?

------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Dang!  Trying to fix this problem, I made a small change I am back where nothing shows up under Network except a Windows Network folder, and it show nothing under it either.  Loots like my wife is resting on the couch, so she probably turned off her pc.

When she gets up, I guess I will ask her to leave it on during the whole of the day until I get this resolved.

---

### Post by oldefoxx on 2015-02-25
I am looking at a tutorial on sharing a workgroup printer, and this is  part of what I read:

Step 3: Configure Ubuntu to Access the Printer

From your main panel, go to 'System -> Administration -> Printing' to open the printer configuration manager.

Problem is, I don't have the option of Printing appearing there.  In fact, I don't know where it is under 14.04.  Can someone help with this?

---

### Post by bab1 on 2015-02-26
> **oldefoxx said:**
> I am looking at a tutorial on sharing a workgroup printer, and this is  part of what I read:

Step 3: Configure Ubuntu to Access the Printer

From your main panel, go to 'System -> Administration -> Printing' to open the printer configuration manager.

Problem is, I don't have the option of Printing appearing there.  In fact, I don't know where it is under 14.04.  Can someone help with this?

This question is OT (off topic); not relevant to the original problem.  It deserves its own thread.  I think your should concentrate on the original problem as it may help you with this problem.

Never the less;  you can look at  System Settings>>Printers>>Add>>Network Printer.  On the other hand (again), if the instructions are incorrect, how will you ever know when you drive off into the weeds?

---

### Post by oldefoxx on 2015-02-27
Years ago I rejected the move to XP and beyond, and went with Ubuntu instead.  But I still wanted Windows 2000 as an option, so I also adopted Virtuallbox and installed Win2K as a client.  Been a rewarding experience.  However, other members of the hamily moved on to Windows 7/  This includes my wife.  She paid the Geek Squad at Best Buy to clean up my brother-in-laws pc for her use after he died.  She remembers the fact that I did not reach out and clean the pc for her, so now she rulws that I can't have hands on her pc with this shared workgroup issue.  Fair enough.  That limits my entitled access to remote and only while she is using it herself.  In between times, her pc shuts down and there is no remote access to it.

You may think I should talk her out od her position, but she a wonder to live with, and entitled to hold with her preferences/

---

### Post by oldefoxx on 2015-03-02
Okay!  Finally made some progress.

Nope.  Lost it on the next reboot.  Back to where nothing shows up exceot Windows etwork under Network.  I'm doing a copy-and-paste text file od helpful hints that have been posted here and elsewhere, but I can't get that dog to wag its tail again.  I also  have two other drive partitions with Ubuntu 14.04 installed on  them, and I have the same visibility problem  it comes to the workgroup withj them.  14.04 is the only OS i I am currently working  with, aside from a windows 2000 client running under Virtualbox.  I used rhw client, and can see all the workgroup devices there, but have the same problem trying to connect to my wife's pc.  Invalid password or user name.  I guess I will have to get back into her crafts room and make sure her pc is set up with the right accounts data and sharing priveleges.

Right now I want to get back  on the matter of nothing showung up on the Network except the  the next reboot.Windows Network folder with nothing in it, and why I can't connect to a server either.  I got it one time, but lost it on reboot.

---

