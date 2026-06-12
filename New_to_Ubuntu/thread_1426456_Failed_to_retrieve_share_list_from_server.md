---
title: "Failed to retrieve share list from server"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by edempco on 2010-03-10
The error pop-up is titled "Unable to mount location" and it continues with "Failed to retrieve share list from server."

I am using 8.04 LTS and have only this machine set up on Ubuntu. This machine was able to access the Windows network through a wired connection to a Cradlepoint router. Sometime over the last two weeks, it stopped connecting. This machine cannot see the other Windows machines, nor can the Windows machines see this machine. 

I've tried a couple of suggestion that I found that used gedit to add and rearange network shares, but with no change. All machines are "MSHOME." This machine has a static IP. But, something seems to be in the way and will not let all machines communicate.

I could use some more ideas, please.

---

### Post by edempco on 2010-03-12
I can see that this is a popular problem, but I haven't found any solutions that work ... and I've tried a few. Could it be that I tried enough of the solutions to have created a Windows shares, mounting problem?

As mentioned, I was able to see the Ubuntu machine from Windows, but I can no longer do that. I've always had the problem with seeing the Windows machines from Ubuntu.

Networking can have it's difficulties and I've experienced quite a few with Windows, but even the old DOS machines seem easier to get networking working in comparison. Is it really this difficult, or have I not had the right resource?

---

### Post by louieb on 2010-03-12
Running 8.04.4 too.
Double check the Ubuntu IP (ifconfig) and the IP of the windows (ipconfig).
Try to ping  the windows machine.
this tries 3 times 

```
ping <ip of target> -c3
```These threads have some other things to check too. (Used the 1st when setting up file sharing on the home network)
[Mount samba shares with utf8 encoding using cifs - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=288534&highlight=samba") 
[Howto: Fix Windows share browsing issues - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1169149")

---

### Post by edempco on 2010-03-12
Thanks for the reply!

The ping works, but the machines can't see one another:
ed@Ubuntu:~$ ping 192.168.0.17 -c3
PING 192.168.0.17 (192.168.0.17) 56(84) bytes of data.
64 bytes from 192.168.0.17: icmp_seq=1 ttl=128 time=5.30 ms
64 bytes from 192.168.0.17: icmp_seq=2 ttl=128 time=0.300 ms
64 bytes from 192.168.0.17: icmp_seq=3 ttl=128 time=0.292 ms

--- 192.168.0.17 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.292/1.965/5.304/2.361 ms


I haven't gone through all 120 pages of the first hyperlink, but I've found reference to this resource. Those references indicated that the last few pages held out promises - they didn't work.

I've been through the entire second hyperlink - no luck.

Should I go through the entire 120 page document? Most of it are comments from other users. Is there another succinct resource that goes through it step-by-step without all of the other stuff thrown in?

Do you think there was a change in a firewall-like update to the LTS?

---

### Post by louieb on 2010-03-12
Those threads are in the how to section - the 1st post is the one that describes the process. Some how tos continue on to the 2nd post. The others are questions, comments - general discussion of the how to.  Sometimes useful - sometime not so much.  

It may be your windows share(s) - for example with Vista and Win7 you can't share a drive - only folders on the drive. (With XP you can share the drive). 

Which flavor of Windows? 

If you go to Places>network>

Can you see the windows computer?
If yes click on the computer - does it show the shares?
If you have not changed any firewall settings - that should not be a problem. (I use the default - have not done any firewall setting change)

---

### Post by edempco on 2010-03-15
Oops, my fault for not identifying the version of Windows; it is XP. 

Everything was working. I could see all windows machines from Ubuntu and Ubuntu from all windows machines. All files could be opened and saved with either MS Office or Open Office. Now, the Network icon in Ubuntu Places will not mount; thus the title of this thread. I can ping and get a response. It is as if there is a door that is shut, but a ping can slip under it.

I've been through both resources you pointed out and followed all of the instruction. It seems to me that I have a "Nautilus" and one resource was referring to "Samba". I feel as if I have exacerbated the problem by following the instructions from these and other resources. 

It seems to me that all of the terminal (DOS-like) work should not be necessary. I should be able to go to "System" and "Network" and make all of the settings required. That is obviously not a possibility, since there is limited access to Network settings.

No luck so far. Any other suggestions?

---

### Post by JoeEndUser on 2010-03-16
I'm beating my head against the wall because my shares stopped working after being fine for months. I have not fixed, but today I noticed that when I set the router to acting as a router instead of a gateway in the Advanced Routing section (WRT54G2), my shares work again, but I lose the WAN side.

I think in my case Samba is having a problem with an ill-defined LAN - double-nat problem (cable modem DMZ'd to router).

Sorry, it isn't a fix, but maybe a different direction.

---

### Post by Helkaluin on 2010-03-16
For the 'Failed to retrieve . . .' error, try opening the following ports:

137/UDP
138/UDP
139/TCP
445/TCP

---

### Post by JoeEndUser on 2010-03-16
Thank you for the firewall suggestion. I turned UFW off, but I think that results in blocking everything. I will give it a try and report back.

---

### Post by edempco on 2010-03-17
> For the 'Failed to retrieve . . .' error, try opening the following ports:

137/UDP
138/UDP
139/TCP
445/TCP

Not sure how to do this. Can't do it under Networking; there is no access. Are there some instructions?

---

### Post by JoeEndUser on 2010-03-17
The firewall that is installed by default along with Samba is UFW. I'm lazy so I installed a gui for it in terminal:

sudo apt-get install gufw

launch in terminal:

gufw

I tried allowing the recommended ports in the Simple tab and that did not work for me. Now I'm opening a wider range of ports in the Advanced tab to see if I can get it to work (I wouldn't recommend unless you are working behind a hardware firewall or at least a router).

I will get back with the results.

---

### Post by JoeEndUser on 2010-03-17
edempco,

After playing/looking around I believe this is not a firewall issue, but an issue with nautilus share and specifically with it not seeking authentication when it needs it. There are lots of bug reports regarding similar issues with it.

I permanently mounted the share I was trying to get to using cifs and it works just fine. Loosing the instant browsing for shares is a bummer, but maybe just permanently mounting it is better in the long run.

If you would like me to give a summary of how I do the permanent mount, let me know. I'm giving up on nautilus share for now.

---

### Post by edempco on 2010-03-17
My wireless printer works just fine with either the Ubuntu or Windows computers, but my windows computers and Ubuntu computer will not find each other. 

Yes, I would like a summary of how you permanently mounted the share. I've read and followed two sources of information that describes the same thing, with no results.

Why hasn't there been a notice that there is a bug or a problem with Nautilus?

---

### Post by JoeEndUser on 2010-03-18
If someone cannot reproduce the problem in a number of different environments then it's just a bug for some and a fix might break something else, especially in an LTS, I believe.

I just ran across some notes from when I used Hardy (I use Jaunty now):

After Samba install:

nautilus-share broken instead

use 

shares-admin (enter in Terminal)

Please give that a shot and I will post about the permanent mount.

---

### Post by JoeEndUser on 2010-03-19
Permanently Mount Windows Shares

I have tested explicitly from these instructions on a Gnome Hardy Box, but use same in Intrepid and Jaunty as well. I have to waive liability for anyone messing up their machine as a matter of course

This is all gleaned from dmizers guide [http://ubuntuforums.org/showthread.php?t=288534&highlight=Samba]("http://ubuntuforums.org/showthread.php?t=288534&highlight=Samba"), but hopefully a little more user friendly for Gnome Users that are new or not fond of terminal (not terminal free).

Step 1 - Open Synaptic Package Manager in System - Administration; search for smbfs; check the box next to it and hit the Apply button (SAMBA should show that it is already installed - if not install it); Yes you want to install.

Step 2 - Navigate to your home directory and create a folder with the share name (doesn't need to match the actual share name, but without spaces in the name is easier later).

Step 3 - Open Application - Accessories - Terminal; hit Enter after you copy and paste this:

sudo nano /root/.smbcredentials


Type in all of the information below with the user name and password of the windows machine (replace me and mypassword with your login info) like so with no spaces:

username=me
password=mypassword

hit ctrl-x - type: y - hit Enter

While terminal is still open hit enter after you copy and paste this:

sudo chmod 700 /root/.smbcredentials

Finally, hit enter after you type the following in terminal: 

sudo nautilus

*Warning: you have root privilege and can delete/change any system file.*

Notice that the file browser that opens say root - File Browser at the top

In the root file browser navigate to Filesystem - etc; find the file named "fstab"

Copy and paste it to someplace safe (i.e. Desktop).

Double click and display fstab from the etc folder you opened with the filebrowser as root.

scroll to the end of the fstab file and hit enter and paste the following:

//netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

You will need your LAN ip address (type ifconfig in Terminal if you don't know).

Supposing your linux box is ip 192.168.1.101 and your linux username is john and your windows share is called Share and you created a folder in home called Share in step 2 above - you would change the line to the following:

//192.168.1.101/Share    /home/john/Share        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

If your share name in windows has a space like: "My Share" then use \040 in the space - like so:

//192.168.1.101/My\040Share    /home/john/Share        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Save the file and reboot your machine.

You should have a mounted file on your desktop.

You may have a bit of a hang at shut down and get a CIFS VFS error. If so look at dmizers guide above and search for CIFS VFS.

If you get a Mount Error 13 - search dmizers guide for nounix.

---

### Post by edempco on 2010-03-19
This really looked promising. I followed all of the steps, but may have gotten lost with the format and information required in adding the line to fstab:
> //netbiosname/sharename /media/sharename cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_ mode=0777 0 0I understand that netbiosname is the IP address; like 192.168.0.22, but the following is not under stood:
- sharename = ?
- media = ?
- sharename = ?

The windows machines have no username or password, should I leave those blank after the equal sign?

I have also read the acronym "cifs" a thousand times, but nowhere is there a spelled out name to understand what this is, but this may not be important at this point.

You gave an example of the modification needed, but in Windows terms, does:
- sharename = the computer name?
- media = the folder name?

How important are capitals and lower case? I saw in your example a capitalized "Share" instead of "sharename." 

You mentioned that you are using Hardy and Intrepid, but I am using Gutsy the LTS 8.04. The bottom line is that it did not work for me ... at least not yet.

I hope you have some more suggestions for me, please?

---

### Post by JoeEndUser on 2010-03-20
If you've stuck with it this far you are really close.

Let's break this down, the first part:

//netbiosname/sharename

This is the Windows side. Like you said the netbiosname is your LAN IP:

The sharename here would be the name of whatever folder you wish to share in Windows. Say you have a folder on your Windows desktop that you want to share. Let's say that folder is "Music". You right click on the folder and go to Sharing and Security and click on the line warning you of the risks with sharing, then mark the boxes for sharing the folder on the network, then assign it a share name ENTER THIS NAME INTO THE SHARENAME AFTER NETBIOSNAME then allow others to change files if you wish.  You don't need a full path like you would if you were mapping a drive in windows.

The second part:

/media/sharename

This is the Linux side. Let's say you want your linux name for your windows Music file to be "Swing": In my example from step 2 you created a folder in you home directory in linux to be the share name. so you would create a folder in your home directory and name it "Swing". Say your linux user name is John.

So the line /media/sharename above would become /home/John/Swing.

Be carefull to keep the spaces between windows and linux and after. The whole line in this example would be:

//192.168.0.22/Music /home/John/Swing cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_ mode=0777 0 0

I believe linux will try to resolve the line with or without capitals. But provide the capitals just in case.


Windows Password

Are you sure you did not set up a password with your Windows? If not you probably should. You can go to Control Panel - User accounts and give your user account a password or try the following in place of the line above and forget .smbcredentials:

//netbiosname/sharename    /media/sharename        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

CIFS: Common Internet File System. This is just the protocol in which the shares are connecting. It means nothing as long as you have smbfs installed.

I hope that was more helpful.

---

### Post by edempco on 2010-03-22
JoeEndUser; I will stick to it, but I need to leave this machine for a week to participate in a conference. If you don't hear from me until the end of the month, it's not because I don't want to follow through with this. You've been a great help! I will respond upon my return to try your suggestions.

THANKS for the help thus far!

---

### Post by JoeEndUser on 2010-03-23
Thank you for that.

One thing that may be confusing is that I changed:

/media/sharename

to:

/home/john/sharename

Linux just needs a container (folder) to put the data in from the windows share. It doesn't really matter where the folder is or what it is named as long as you point to it correctly in the fstab file.

I like it in my home folder because then there is a "shortcut" in home with all the windows data. Some like it in the media file, which is where the system mounts cd drives, ipods etc. (see Places - Computer - Filesystem - Media). You need to be root (sudo) to create a folder within the Media folder.

If in doubt where a folder is just right click on it to see the path.

Good luck!

---

### Post by edempco on 2010-03-30
Hi, I'm back and trying to get this to work. 

	 	 	 	 	  Here is where is where I am:
The line added to fstab that you suggested was:
//netbiosname/sharename /media/sharename cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_ mode=0777 0 0

When I indicated that I have no user or password on any of the windows machines, you suggested the alternative line:
//netbiosname/sharename /media/sharename cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07 77 0 0

Ideally, I want to have the Ubuntu machine access the root directory of the windows machine named "Tablet2." "Tablet 2" is the name of the C: drive. For this exercise, I placed a folder named "Windows" in the "home/ed" directory, as you instructed.

I have modified the fstab line in the following way:
//192.168.0.22/Tablet2 /home/ed/Windows cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07 77 0 0


Saved the file and rebooted. The folder is not mounted to the desktop, but is in the home directory. There is nothing in the folder. No other messages came to the screen upon reboot.


Have I done something wrong in the code?

---

### Post by JoeEndUser on 2010-03-30
Two things I see:

1. remove the space in the last set of 7's in either line:

//192.168.0.22/Tablet2 /home/ed/Windows cifs guest,rw,iocharset=utf8,file_mode=0777,**dir_mode=0777** 0 0

2. I forget what version of windows you are using, but most won't let you share C: Did it for you? If you go to properties and say share does it not give you a warning that windows can't share c?

However, if you adjust some settings in Vista it will allow you to browse the user files, which is goofy (that is in the part that broke for you in me: nautilus-share).

I would try perma-mount a test folder. That isn't C:.

---

### Post by egalvan on 2010-03-30
> **edempco said:**
> 
You mentioned that you are using Hardy and Intrepid, but I am using **Gutsy the LTS 8.04.**

Check which version you have...

Gutsy is not LTS.
Gutsy is 7.10
EOL 9.04  April 2009

Hardy is LTS.
Hardy is 8.04 LTS
to April 2011 on Desktop
to April 2013 on Server

---

### Post by egalvan on 2010-03-30
swerdna is a forum member, and often has excellent advice.

these HowTo's he wrote are very good...
I've used them quite often to set-up and to diagnose network problems.


[http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

---

### Post by edempco on 2010-03-31
I stand corrected; Hardy Heron 8.04LTS. Gutsy was my first install, Hardy is the one have now. Thank you, egalvan. I will also check out swerdna.

I am interfacing with Windows XP, Professional. 

I removed the space between the 7's. I also renamed the folder on the Ubuntu machine and created a folder on the windows machine instead of C: drive. The windows machine has a folder named "UFolder" and the Ubuntu folder was renamed WFolder (instead of Windows). Here is where is where I am:
The last line in fstab is now:
//192.168.0.22/UFolder /home/ed/WFolder cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Saved the file and rebooted. Still no mounted folder and nothing in the WFolder on the Ubuntu machine using Places to open the folder (or visa versa).

Thoughts?

---

### Post by JoeEndUser on 2010-04-01
I'm going to test the guest login in my Hardy machine. In the meantime, can you tell me what you get back, if anything, when you enter the following in Terminal:

smbclient -L //192.168.0.22


Also, are you using simple file sharing in XP Professional?

---

### Post by edempco on 2010-04-01
Here is what I get, after the P.W.:

> ed@Ubuntu:~$ smbclient -L //192.168.0.22
Password: 
Domain=[ED] OS=[Unix] Server=[Samba 3.0.28a]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    Public          Disk      
    Documents       Disk      
    Downloads       Disk      
    Work Folder     Disk      
    home            Disk      
    IPC$            IPC       IPC Service (Ubuntu server (Samba, Ubuntu))
    Officejet_7400_series_fax Printer   Fax queue for HP Officejet 7400 series
    Officejet_7400_series Printer   HP Officejet 7400 series-USB
    OfficeJet_7400  Printer   All-in-One 7410
    DeskJet_5800    Printer   Deskjet 5800
    photos          Disk      
    pictures        Disk      
Domain=[ED] OS=[Unix] Server=[Samba 3.0.28a]

Yes, I'm using simple file sharing, nothing special.

Does this help?

---

### Post by JoeEndUser on 2010-04-02
Yes. 192.168.0.22 is a linux machine. If you go to Start, Run, type, cmd, then ipconfig in your Windows machine, what do you get?

I tested the guest login on my hardy machine and it works. Your fstab line looks good.

Hope that changes things.

---

### Post by JoeEndUser on 2010-04-02
Oh yeah, I should have said, replace 192.168.0.22 with the IP address you get from Windows.

---

### Post by edempco on 2010-04-05
The Windows machine is: 192.168.0.199, but it changes each time it logs in (DHCP; no static IP).

I replaced the Linux IP with the Windows IP for the one windows machine I am working with; rebooted; but no change. Still cannot see either machine in either of the folders (shares). Both folders have been set up to share, as well. 

I have always been able to use the Windows machine to search for the Ubuntu machine. When that occurs, I can see the Ubuntu listed as one of the machines on the Mshome network, but when I click on it, the message is that I do not have permission.

Any further thoughts?

---

### Post by edempco on 2010-04-05
Here's the result of using the Windows IP:
> ed@Ubuntu:~$ smbclient -L //192.168.0.199
Password: 
Domain=[TABLET2] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Sharename       Type      Comment
    ---------       ----      -------
    Printer10       Printer   HP Officejet 7400 series - USB
    Printer11       Printer   hp deskjet 5800 series - Wireless
    Printer12       Printer   hp deskjet 5800 series (USB)
    Printer13       Printer   Canon iP90
    IPC$            IPC       Remote IPC
    print$          Disk      Printer Drivers
    SharedDocs      Disk      
    UFolder         Disk      
    C-Tablet2       Disk      
    Printer7        Printer   Powered by HP Instant Share.
    Printer8        Printer   HP Officejet 7400 series fax
    D-Tablet2       Disk      
    Printer4        Printer   Microsoft XPS Document Writer
    Printer5        Printer   Microsoft Office Document Image Writer
    Printer3        Printer   Journal Note Writer
    Printer9        Printer   HP Officejet 7400 series - Wireless
    ADMIN$          Disk      Remote Admin
    C$              Disk      Default share
    Blank           Disk      
    Printer         Printer   Send to OneNote 2003
    Printer14       Printer   Adobe PDF
session request to 192.168.0.199 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[TABLET2] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------


Does that help?

---

### Post by JoeEndUser on 2010-04-07
Further below is a copy of my fstab file from Jaunty for comparison purposes. A couple of thoughts:

Interesting that Samba is recognizing Ufolder as a disk, but not mounting it. You might try some searches on the error you are getting: session request to smb failed (Called name not present).

Did you mess with the firewall before? If you installed gufw, you can go to System - Administration - firewall configuration and disable the firewall (uncheck enable firewall) to make sure it's not getting in the way.

How long have you had that linux machine? I find that linux has about the same life cycle as windows - a year or so of use and the operating system degrades enough to be worth reinstalling. I'm going to reinstall to an extra hard drive on my machine and see if my network is at fault or if software conflicts etc have messed up in nautilus/network manager.

I have had Jaunty on this machine for almost exactly a year, so I'm thinking degradation is the problem for me.

Two cents: my experience was that Jaunty has a more stable network environment over intrepid and hardy. 


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=db58d76e-f7b6-4041-8f5f-e4227b113a02 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c6cb96dc-937b-4a5d-a30b-a3497abf4745 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#Shares added

//192.168.1.103/My\040Pictures    /home/joe/My\040Pictures        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

//192.168.1.100/Users    /home/joe/Users        cifs    credentials=/root/.smbcredentials1,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

---

### Post by JoeEndUser on 2010-04-07
You asked about Windows seeing the Ubuntu machine. Windows can see that there is a Unix type machine, but can't read the ext3 filesystem. You would need to have a FAT or NTFS partition or external drive on the Ubuntu machine in order for Windows to read it.

Let me know if I missed the mark there.

---

### Post by edempco on 2010-04-07
Well guess what ...

I started to read "http://ubuntu.swerdna.org/ubulanprimer.html" and began with turning off any firewall, as per directions. The next time I looked, I had a mounted "WFolder" from the windows machine on the desktop. Yes, it has the files that I placed in the "UFolder" in Windows. When I add files in the WFolder they show up in the UFolder, no problem. 

Now, this arrangement allows file sharing, if all of the files from both machines are placed in the same folder. This is not very convenient, but it works. At least, some files can be shared.

Regarding your last note and in relationship to what you helped me to do, it seems to me that the same concept could be applied to both root drives ... change the names of the folders in fstab and I should have shared folders and files. Thoughts? This also should apply to my inability to open the Ubuntu machine from the windows machine. Using "Search for computers" in "My Network Places", I can see the Ubuntu machine, but when I click on it, the message says "\\Ed is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. The network path was not found." I was able to click on it and read the files in the past. To me this indicates that I don't have the domain, password, or file sharing correct. What do you think?

You have certainly stuck with me as I bumbled my way through this problem. With your help, we have successfully created a tunnel that can be used to share files. I want to thank you very much for your support!!

---

### Post by edempco on 2010-04-08
I have recently determined that the system does not allow mounting of the shared folder every time the system is rebooted. What I am required to do is to boot, then enter "sudo ufw disable" in the terminal window and reboot. 

This procedure is very cumbersome and eliminates the firewall (I think). Is there something else I need to do?

---

### Post by JoeEndUser on 2010-04-08
Great! I'm glad you got it working.

Try using the GUI:

sudo apt-get install gufw

Go to System - Administration - firewall configuration and disable the firewall (uncheck enable firewall). That works for me.

Also, I was under the impression that Windows can't see native Linux folders with Samba. I was definitely wrong. If you right click on a folder in Ubuntu and check the boxes in the sharing tab in properties, Windows will pick it up in My Network Places.

Windows won't allow C: to be shared, but you could make another partition (you can even fire up the linux live cd and grab the partitioner out of the System folder once linux boots up). I have a G: for this purpose (although no different than a folder really). The partitioner may not work on a old install that may be really fragmented.

What about just permanently mounting My Documents and Desktop in Ubuntu?

---

### Post by edempco on 2010-04-08
THE FIREWALL!
THAT, MY FRIEND, IS WHAT CHANGED! 
EVERYTHING IS WORKING AGAIN!

In "Places", Network shows all of the Windows machines, folders, sub-folders, and files. All of the files are accessible and can be opened and written to by either the windows or ubuntu machine. The entire C: drive of any windows machine can be mounted so that all of the Ubuntu programs can see and use files, etc, etc, etc!!! 

This whole business and the reason for my very first, original question was that I could not get to my Ubuntu machine from windows and visa versa; now I know why it simply stopped working!

THE ONLY THING THAT CHANGED WAS THE FIREWALL!

I did not ask about the firewall in this help posting, but I did in two other postings and tried to find if Ubuntu changed something along the way ... they did! It was an installation and update of the firewall! Turning off the firewall was part of the answer. The other part was that I needed to "change" the permissions on the Ubuntu folders (shares). It said they were shared; they were marked that they were shared, but the little icon that indicated shared folders was not present! I noticed the icon was missing  when the WFolder was shared during our (4-page) exercise. What I needed to do was to unmark and then remark "share this folder" to get the double arrow icon to appear next to the folder in the files system called "Places." WHAT A BUNCH OF HUEY!

[COLOR=Purple]**You my friend, by your diligence, perseverance, and dogged determination helped me to forcibly mount a folder on my machine and I appreciate it very much - THANK YOU! **[/COLOR]

The knowledge you gave me and the accomplishment of mounting the folder was the only thing that led to something, so simple, that anyone should be able to replicate it; able to fix their own mounting problem (if they suffered my same fate). [B]

Now I know! Do 2 things:[/B]
[B][COLOR=Red]1. Turn off the firewall!
2. Reset the previously shared folders (shares)![/COLOR][/B]

THAT's ALL! THAT's IT! 

Why couldn't someone have told me and everyone else who asked how to get the network to talk to other windows computers? The answer, if you could see and work with the other computers on the network before, is a simple two-step truth.

---

### Post by JoeEndUser on 2010-04-08
That is what I love about the Ubuntu community, that people help each other and that you learn by teaching, or sharing what you know. Or at least problem solving together.

For me, I'm interested in this, from what you posted:

The entire C: drive of any windows machine can be mounted so that all of the Ubuntu programs can see and use files, etc, etc, etc!!!

Can you summarize what you discovered? How did you get there? Did you right click and share the C drive? Or was it just there for you?

Did you use gufw to solve your firewall problems?

I definitely learned some things during this process. Thank you.

Cheers.

---

### Post by edempco on 2010-04-09
When I discovered the command to turn off the firewall (sudo ufw disable) and used it in Terminal, I noticed that the UFolder (on the Windows machine) and the WFolder (on the Ubuntu machine) were visible and had the dummy files that I placed in both. What is interesting about the shares (folders), that you helped me with, is that a file can be placed in either of the respective files by either of the machines and opened by either machine.

Previously, I had been able to see all of the other machines on the network, so when the firewall was removed and the folders reset, I was in business again ... just like before.

To set this all up, it works the same way as any windows network. Any windows folder (including drive) needs to be shared; right click on any folder or drive and use the "Sharing and Secruity." Click the Sharing tab and make "Share this folder on the network." You can also (as I do, at a risk) mark "Allow network users to change my files." Doing this allows the Ubuntu machine to open a Word(tm) document with Open Office; keeping it in the same location, in the same folder, with the same name - very convenient.

Passwords can be set up, but I do not use them for easy access. If there were more people working on the network, than there is now, I would institute a policy of passwords, static IP addresses and the use of the "Shared Folder" (that is part of the Windows structure).

On the Ubuntu machine, the folders (shares) have to be shared, too. You can share the entire root or individual folders by clicking the right mouse button and then "Sharing Options." This precludes that all of the SAMBA programs are installed. The easies way to do this is to go to Synaptic Package Manager, under Administration, and look down the alpha list for SAMBA, mark all the boxes for installation, and click Apply. You can also download and install SAMBA from Applications. Search for SAMBA and install it. It will be loaded to Administration, under System, and gives you the ability to add or subtract shares (folders) with a GUI (graphical user interface).

When everything on both the Windows machine and the Ubuntu machines have been shared, make sure that all machines are on the same domain. XP machines use the default MSHOME. Make sure that all machines are using the same domain and that all of them are spelled with capital letters (that'll goof up things if you mix capitals and lower case, for some reason). If the DHCP doesn't work (mine does), you can assign the Ubuntu machine a static IP address by using the Network, under Administration and System.

If any of this helps in any small way, that's great!

---

### Post by JoeEndUser on 2010-04-14
My problems were solved by dmizer's post [http://ubuntuforums.org/showthread.php?t=1169149&highlight=failed+retrieve]("http://ubuntuforums.org/showthread.php?t=1169149&highlight=failed+retrieve")

Specifically by completing the steps in Problem 3.

I must not have had the search mojo when I started looking at this problem!

---

### Post by edempco on 2010-04-19
Case closed.

Thanks for your help!

---

