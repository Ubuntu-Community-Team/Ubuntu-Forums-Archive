---
title: "Ubuntu 10.10 can't &quot;see&quot; Windows network - Samba issue?"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by bomber1712 on 2010-11-19
I have my printers attached to a Win XP system.  I have another XP system with a shared drive.  I also have a Win 7 Pro machine with a couple of shares, and a Win 7 Home Premium with a share.  All machines are on "MSHOME" workgroup.

I have a laptop running Ubuntu 10.10 and another running 10.04.  Neither of these machines can "see" the windows network, nor can they find the printers.  

I have been all over the net looking for an answer, but have come up empty.

Can anyone help?

---

### Post by AgentZ86 on 2010-11-19
I'm assuming you went to Places/Network then clicked Windows Network

---

### Post by bomber1712 on 2010-11-19
Er, yep.  I do that, and I see MSHOME.  Double click, and it shows me just the computer I am on!  Funny thing is, I did have access to printers and shares at some point.......I think before I reformatted and dual installed XP and 10.10

---

### Post by AgentZ86 on 2010-11-20
> **bomber1712 said:**
> Er, yep.  I do that, and I see MSHOME.  Double click, and it shows me just the computer I am on!  Funny thing is, I did have access to printers and shares at some point.......I think before I reformatted and dual installed XP and 10.10

Strange

Try to share a folder on your ubuntu system

It should not require you do this, but try to create a folder for a dummy share in your home folder.
Then right click the dummyfolder and then share options

I don't know if guest access or allow others would make any difference but I know it will normally say it's installing other stuff and then wants you to restart.

Anyhow, it's worth a try


NOTE:
One last thing

Try to go to Systems/Administration/Users and Groups

Then - Manage Groups
Then - samabashares
Then - click Properties
Then - make sure your Group members are checked for the members you want to access windows shares. (may need to restart to activate)

Thats about all I can think of for now

---

### Post by AgentZ86 on 2010-11-20
Forgot to ask

Is the Ubuntu Computers connection to the router/server via wired ? or wireless ?

You may also want to double check your router/server to be sure the group name is also the same MSHOME

---

### Post by bomber1712 on 2010-11-20
I set up a share, no luck.  I went through the steps you outlined, no luck.  The only computer I can see in MSHOME is the Ubuntu system that I am on.

I am trying to connect the 2 Ubuntu systems wirelessly (Linksys WRT54G).

---

### Post by AgentZ86 on 2010-11-22
Ok try this

I think you need to change the Samba to the correct workgroup for the windows shares even though your computer workgroup may be right.

[http://www.liberiangeek.net/2010/08/change-set-samba-workgroup-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/08/change-set-samba-workgroup-ubuntu-10-10-maverick-meerkat/)

**Change the line from workgroup = WORKGROUP to : workgroup = MSHOME**
Or is should say MSHOME already if it's already setup correctly

You can also tell what you got you add printer

Then select Windows Printer via Samba and then you can browse and it will show you your samba shares.

If you see one called workgroup then this likely means your ubuntu samba shares are setup as workgroup and needs to change to MSHOME

So anyhow this instruction above will set your samba workgroup

And I would plugin to the machine wired first just to be sure the wireless access is not causing any problem with access to your shares also.

Anyhow, Hope this helps

Let me know what happens

---

### Post by bomber1712 on 2010-11-22
I already checked the smb.conf file and changed it to MSHOME.  I will try connecting via wire to see what happens.  I should be able to "see" all of the shares if I connect "wired", right? I will let you know.

---

### Post by yankysunny on 2010-11-22
I had a similar but not same problem a week ago, that I can see MSHOME in network in my ubuntu but when I double click it says cannot mount. I am not able to solve the problem but, I run nautilus smb://IP ADDRESS/ of the machine and then it opens the network share.
I have no idea abt the printers or may be the same command can do some help.

---

### Post by AgentZ86 on 2010-11-22
> **bomber1712 said:**
> I already checked the smb.conf file and changed it to MSHOME.  I will try connecting via wire to see what happens.  I should be able to "see" all of the shares if I connect "wired", right? I will let you know.

Yes they should be there when connected with the wire.

And at least we can try to confirm ubuntu config topic.

---

### Post by AgentZ86 on 2010-11-22
> **bomber1712 said:**
> I already checked the smb.conf file and changed it to MSHOME.  I will try connecting via wire to see what happens.  I should be able to "see" all of the shares if I connect "wired", right? I will let you know.

This is starting to sound like a windows firewall topic or something ?

Also try going to Places/Connect to Server
-then select windows share from the pulldown menu
-then type MSHOME in the box and see what happens.

And all this is assuming that your windows machines already has file shares and print share (enabled)

I don't know why this should be different then just browsing the network but worth a try and simple enough

---

### Post by lswartz on 2010-11-22
Your printer on the Win XP computer must be shared.

My printer is no longer on Win XP, but when it was, I went to System, Administration, Add, Network Printer, Windows Printer via SAMBA, & finally Brouse. Both printers were found & I added them 1 at a time. Both computers need to be on a few minutes. Even with both computers on Ubuntu, you need the the host with the printer connected to be on for a few minutes before your other computer will find the printer to print.

My printer is now on a Ubuntu computer & is easily shared with 2 Ubuntu computers & 1 Win 7.

---

### Post by AgentZ86 on 2010-11-24
Hi

Sorry I didn't suggest this sooner

I have never really been happy with the default sharing options for gnome

Please installed Smb4K, You will not be unsatisfied.

The problem I've always had with Ubuntu default sharing is the following:

[LIST]
[*]When you use the Places/Network option it mounts the shares, OK fine, but when you want to open a file from within an application then those network places are not there. For example open gthumbs and then open a location or file from a share. You can't browse to it, You can save to that share either
[*] You can create a location shortcut which will work and the mount will be there, however the shortcut share is not really pointing to the location of the actual shared folder. It defaults the the main directory so you have to browse to your location everytime. For example Open Kompozer, create a webpage, then save as. Where does it go ? NO shares are available from the save-as menu.
And when you open a document or webpage editor from within the share itself you cannot save it to the share either.
[*]Creating a bookmark for the shared folder or shared sub-folder helps but not complete solution either.
[*]The better solution for complete compatibility is Smb4k which I've been using for years and you simply setup your wallet to login to other K apps also.
[/LIST]

You can install the Smb4K from the Ubuntu Software Center and it works perfectly. I was trying to help you with a solution with the defaults because you were already using it that was from what I thought. But believe me you will be more then happy with Smb4k because you can open document and it saves them to the same location on the share/server etc. And when you save-as those locations are in the Places and everywhere else you can think of as well. More logical, and all applications gnome or K can find all the shares and save to the defaulted location from which is was opened. etc.

When you open an open office or word document and click save it saves to that location, unless you save-as and want a different location on the server etc.

Anyhow Smb4K will provide what you want, I'm not sure what problem is going on with your gnomified sharing but Smb4k won't care about it either way.

Hope this helps.

---

### Post by cariboo on 2010-11-24
Before you go much further, I would suggest you open a terminal and type:

```
smbtree
```

this will show you all the shares on your network. The output will look something like this:

```
smbtree
Enter cariboo's password: 
APLUS
	\\WILLY          		willy server (Samba, Ubuntu)
		\\WILLY\IPC$           	IPC Service (willy server (Samba, Ubuntu))
		\\WILLY\TV2            	TV shows part 2
		\\WILLY\TV1            	TV shows part 1
		\\WILLY\Images         	iso images
		\\WILLY\Iso            	Mounted iso's
		\\WILLY\Stuff          	Everything Else
		\\WILLY\Documents      	Documents
		\\WILLY\Music          	Music
		\\WILLY\Movies         	Ripped DVDs
		\\WILLY\print$         	Printer Drivers
	\\RISKY          		XP Computer
		\\RISKY\C$             	Default share
		\\RISKY\ADMIN$         	Remote Admin
		\\RISKY\EPSONSty       	EPSON Stylus Photo R340 Series
		\\RISKY\All Users      	
		\\RISKY\SharedDocs     	
		\\RISKY\print$         	Printer Drivers
		\\RISKY\IPC$           	Remote IPC
		\\RISKY\John 
```

In my case I only have one Windows system on my network, all the rest run a Linux variant, and I use NFS to share between them. As you can see from  the above output all my shares are listed in one place, this should make it easier to connect to them. If you don't get a similar listing, you have to check your windows systems to see if sharing is setup correctly.

---

### Post by AgentZ86 on 2010-11-24
WOW, Sorry about this

Smb4K not working on Ubuntu 10.10

This really stinks.

Some sort of permission errors on shares. It sees the shares fine, but produces the following error messages when trying to mount them or look inside them etc.

mount.cifs: permission denied: no match for /home/agent86/smb4k/AUCTION/iclbiz found in /etc/fstab

I think this may be a bug or something missing.

I didn't have to do anything special on all 5 of the other machines running 9.10 and previous.

Not sure how to diagnose this and this does not help your sharing problem at all sorry.

---

### Post by Thinkin on 2010-11-27
I have the same problem and am looking for updates.

---

### Post by Thinkin on 2010-11-27
Try this:  I have a Dlink router and discovered that the unicast feature was turned on.  Disabling this fixed the problem.


Use Unicasting : (compatibility for some DHCP Servers)

was turned on, when unchecked I am back to normal!

---

### Post by Nicolice on 2010-12-03
Hello, I'm one of the person who having this problem...when I tried run smbtree, it gave me this error
> session request to 192.168.123.100 failed (Called name not present)
session request to *SMBSERVER failed (Called name present, but insufficient resources)
session request to MIYUKI-TORRENT failed (Called name present, but insufficient resources)
session request to *SMBSERVER failed (Called name present, but insufficient resources)

192.168.123.100 is the windows xp that have folder shared turned on, which can be accessed by other computers that is using Windows OS, but not this Ubuntu 10.10

Any helps? Thanks!

---

### Post by jay_y on 2010-12-10
Been chasing the same thing since the 10.10 install on 3 machines.  Did all the smb.conf stuff, set workgroup, shares etc.  I had given up more less.  So unrelated to the Windows network shares issue I was messing around with different DNS servers.  So I was in System->Preferences->Network Connections.  For both wired eth0 and wireless wlan0 I changed the IPV4 settings Method=Automatic(DHCP) to Method=Automatic(DHCP) addresses only.

Then entered my alternate DNS server address in the DNS servers entry. Then re-booted.  To my amazement I could see my other Ubuntu machines that had not been changed yet and the XP, Win Home Server, and a Win7 machine.  Wow Wow Wow...  This was all a result of testing alternate DNS server addresses but also resolved the other issues.  Now can anyone explain what changed since 9.10 ???

---

### Post by bomber1712 on 2010-12-11
OK, so I have tried EVERYTHING that was suggested here!  I connected my Ubuntu 10.10 to my network "wired".  In that formation, I was able to "see" all of the Windows shares, but unable to mount them.  I received an "failed to retrieve from server" error.

NOTHING ELSE HAS WORKED!

---

### Post by HermanAB on 2010-12-12
Howdy,

The only real way to debug Samba problems is with smbclient, so that you can see the error messages returned.  The GUI programs are fine when things work, but useless otherwise.

See this:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

---

### Post by cjbiiv on 2011-01-07
I too, have been having problems connecting to an XP share and a  Synology Diskstation until today.  I changed/implemented the following:

1) Installed Smb4K per AgentZ86
2) Changed my network to "Method=Automatic(DHCP) addresses only" per jay_y
3) Changed my log-in account type from custom to administrator per me

I'm connecting to everything now.  So, tomorrow, further testing and  attempting to access my USB XP printer from Ubuntu.  FYI, my distro is  10.10 Netbook.  Thanks, folks, for the helpful posts!

cjbiiv

---

### Post by shaggy76 on 2011-01-10
> **cjbiiv said:**
> I too, have been having problems connecting to an XP share and a  Synology Diskstation until today.  I changed/implemented the following:

1) Installed Smb4K per AgentZ86
2) Changed my network to "Method=Automatic(DHCP) addresses only" per jay_y
3) Changed my log-in account type from custom to administrator per me

I'm connecting to everything now.  So, tomorrow, further testing and  attempting to access my USB XP printer from Ubuntu.  FYI, my distro is  10.10 Netbook.  Thanks, folks, for the helpful posts!

cjbiiv

:P
DUDE!!! YOU ROCK...
I have been fighting with this for weeks. searcing google reading forums trying diffrent things and nothing work. I tried your sugestion and BOOM!!! everything works great. I can see all my shares and now my Uuntu 10.10 Desktop can be used as a Media Server.
THANK YOU....

---

### Post by bomber1712 on 2011-01-10
Well, I'm really glad that SOMEONE got this to work!  I, however, have not been so lucky.  I maybe missed something.  I am not sure how to change the log-in from Admin to custom.

I had installed Samba, GADMIN-SAMBA. and Smb4k, in that order.  I "played" with many of the settings.  Then, I read this post.  I changed the IPv4 setting to "Automatic (DHCP) Addresses only".  

That did not fix my problem, so I thought I would remove all of the Samba type programs.  I removed all three of the above mentioned packages.  

What should I do, now?  Just install Smb4k? Do I need Samba or GADMIN-SAMBA? How do I change the log-in?

Please help, now that some of you have this working, I feel like I am close!

---

### Post by Kreacher on 2011-01-10
From terminal type sudo gedit

Open and edit the below:

In smb.conf located in /etc/samba

workgroup = your-workgroup

name resolve order = lmhosts wins bcast host

Remove the semi-colon from the start of any line.

In nsswitch.conf located in /etc 

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

You will need to remove the semi-colon from the beginning of the config lines if they are present.

Note the order of the items in smb.conf and the addition in nsswitch.conf as they are important.  Reboot the system. Patience. The other machines will show up. Windows 7 has a bit of a problem with passwords that might require editing the registry to solve. I don't remember the exacts of that, but found it with a Google search. 

Scream and yell at someone else if it doesn't work. ;-)

---

### Post by bomber1712 on 2011-01-10
I did what you said, and still nothing.  Any other thoughts?

---

### Post by Kreacher on 2011-01-10
bomber1712,

That is all I do/did on my install/machine. I run 10.04, but should work for 10.10 as well, I think. You do need Samba installed. Install it from the Ubuntu Software Center if you don't have it currently installed. When installing, you might be asked about keeping the current config file. Keep it, or replace it and then edit it again. Sorry it didn't fix your problem.

Once I get the other machines to show up on my Ubuntu system, I right click on the Ubuntu directories I want to share with other machines and tell it to share. I am asked the first time if I want to install the software needed to share the Ubuntu directories. I answer yes and let it install. Then set the allows how I want.

---

### Post by bomber1712 on 2011-01-10
OK, well, it is not working on my setup.  Maybe I have tweaked too many things, and really screwed it up!  Another strange (maybe related) thing is that when I "ping win-client -c 3" it returns 3 good packets.  The issue is, though, that it is pinging 204.232.162.151?

My home is on 192.168.1.1.  I have no idea what I am pinging when I run that command, but I would bet that's part of my issue.

---

### Post by Kreacher on 2011-01-10
Try to ping the ip of your Windows machine. 

You also might try to connect to a Windows server on your local network. From the menu "Places>Connect to Server" and then choose Windows Share from the pulldown menu. Then type in the ip of your windows machine. Should at least give you a connection. If not, I am lost.

Side note: Make sure that your Windows box, Router and Ubuntu box are all using the same Workgroup, Local Domain (or whatever your router might call it) name. And case can be important.

---

