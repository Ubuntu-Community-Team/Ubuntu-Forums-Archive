---
title: "can't see windows shares in nautilus"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by Mangus on 2008-04-22
With Hardy, when with nautilus I browse my windows-domain network, I can see the list of all servers and client, but when I double-click on one object, I cannot see any shares !
Nautilus give me "0 objects".

When I insert the complete share path (like: smb://server/share), it ask me for authentication and lets me enter.

Reading varius bugs reports, I learnd that it seems to be a gvfs bug.

do you know if there is a solution to this bug ?
It should be a priority bug !! It causes me a lot of problem when I use my ubuntu laptop at work !!

---

### Post by Impact_666 on 2008-04-24
I have the same problem.

I went chasing down bug reports, and found that there is a problem with Nautilus.  It appears the coders broke something either in Nautilus or gvfs.

If you're not familiar with it, gvfs allows your applications to access remote filesystems (like ftp, smb) seamlessly as if they were on your local system, without having to mount it.  Nautilus used to use gnome-vfs, which was quirky.  It seems the migration needs a little work :)

I'm surprised, and dissapointed that Hardy was released with this bug.  It's a show-stopper for many people who are not wise in the ways of the force, er...  network file paths :)

There is a patch for it, but i'd recommended you wait for the update, and use the exact path to your shares for now.

---

### Post by s5demigh on 2008-04-25
It's weird. I haven't had this problem until recently. I installed a hard drive onto my homemade server just for the purpose of backing up my stuff on Ubuntu, lol. I will say though that it will start working at random times which is weird...

---

### Post by nlangmaid on 2008-04-25
I have a similar problem. When I use Places > Network to browse the network, the system can see all the servers, but not the shares on those servers.  No error message, just a blank window.

My workaround while waiting for better brains to fix the problem is to use Places > Connect to Server ... This seems to work.

---

### Post by Impact_666 on 2008-04-27
> **nlangmaid said:**
> My workaround while waiting for better brains to fix the problem is to use Places > Connect to Server ... This seems to work.

I concur, this does work.  It will have to do until the problem is fixed, or we all give up and switch over to another file manager.

---

### Post by ShaunBrown on 2008-04-28
Man I thought I was going NUTS! At least I'm not the only one with this problem. KDE works fine but Nautilus in Gnome doesn't work for browsing windows network shares. I spent the whole weekend tooling around with things. Using any Gnome distro like Ubuntu Studio doesn't allow me to browse network shares. Connecting manually works. Using KDE 3 or 4 works immediately. Wonder if XFCE has the same bug.

---

### Post by ger_mulvey on 2008-04-28
I can not get the connect to server to work as in Gutsy. Pointing at the path works and doesn't work. Often asks for login and then i cant proceed. Searching for help almost suggests it's only happening to me. There is as mentioned a nautilus bug which was fixed to resolve this. But as I can not just connect to server it has been a show stopper for me and I've had to go back to Gutsy.

Any help would be appreciated!!

Ger.

---

### Post by NTolerance on 2008-04-29
I have all my data stored on Windows network shares, so I can't use Hardy because of this bug.  Booted into XP for now.  :(

I'd also like to add that if a workaround method is used to access the passworded share, the ~/.gvfs folder still gets messed up.  If you run an ls on it you'll see a bunch of ????? instead of the normal folder permissions/info output.  

It's kinda strange to only see a relatively small number of people commenting about this bug.  Does everyone use unsecured Windows shares? :shock:

---

### Post by Impact_666 on 2008-04-29
> **NTolerance said:**
> 
It's kinda strange to only see a relatively small number of people commenting about this bug.  Does everyone use unsecured Windows shares? :shock:

Probably.  I tell people, from day 1, use passwords, and lock everything down, even if they think it's trivial.  Many people think passwords are inconvenient (more so than being hacked?).

---

### Post by Impact_666 on 2008-04-29
> **ger_mulvey said:**
> I can not get the connect to server to work as in Gutsy. Pointing at the path works and doesn't work. Often asks for login and then i cant proceed. Searching for help almost suggests it's only happening to me. There is as mentioned a nautilus bug which was fixed to resolve this. But as I can not just connect to server it has been a show stopper for me and I've had to go back to Gutsy.

Any help would be appreciated!!

Ger.

What are you entering into the "Connect to Server" dialog?

Are your network shares password protected?

Are you specifying the correct domain?

Please provide some additional information.

PS:  I'm not an expert, but I'll try to help, provided my 11 month old son continues taking his 3 daily naps.

---

### Post by tanman on 2008-04-29
This is the problem I am having. I have 4 desktops and a laptop on my network. Hardy desktop, Hardy Laptop, Gutsy desktop, XP desktop, and a Vista Desktop. Since I installed Hardy on both the laptop and the desktop I can not see the shares from the Vista computer. It shows up on the network but when I open it up it does not show the shared folders. I can though see the XP shares and the Gutsy shares. From the Gutsy computer I can see the Vista shares. The really strange thing is when I boot to the Hardy live CD I can see and access the Vista shares. If this is a nautilus problem then why does it work on the Live CD, but not once the installation is done. 
     If I try the network server and try to access the vista computer that way it gives me an error that it is already mounted.
     Any Ideas.
Thanks

---

### Post by NTolerance on 2008-04-30
> **Impact_666 said:**
> Probably.  I tell people, from day 1, use passwords, and lock everything down, even if they think it's trivial.  Many people think passwords are inconvenient (more so than being hacked?).

I bet they're using Windows Simple File Sharing.  It's the default sharing method on Windows XP and it allows anonymous access.  Gnome Keyring makes passwords quite convenient.  Shame we can't use it here.  :(

---

### Post by aaaantoine on 2008-05-01
With mine, I can't even see the computer names... Only the workgroup folders.

---

### Post by verm69 on 2008-05-02
i can't see shares on a server, but if i tyep "smb://server/share" i can see inside.

but then inside some of those folders i can't see any further! :( 

gives me the error..

"The folder contents could not be displayed.

Sorry, couldn't display all the contents of "Accounts": Invalid argument"

i kinda need to be able to see inside this folder as it holds the 1000 pupils account folders!

pretty dissapointed...

---

### Post by NTolerance on 2008-05-07
Still surprised at the seemingly small number of users affected by this issue.  Anyways, I found the leading bug report at launchpad:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

A patch has been submitted which appears to work.  There are instructions on how to recompile gvfs with it.  I imagine this is going to be like recompiling any other part of repository software in that you basically break updates for that component if you choose to compile a non-repo version.  If anyone knows of a fix for that let me know.

---

### Post by SonicSteve on 2008-05-15
> **NTolerance said:**
> Still surprised at the seemingly small number of users affected by this issue.  Anyways, I found the leading bug report at launchpad:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

A patch has been submitted which appears to work.  There are instructions on how to recompile gvfs with it.  I imagine this is going to be like recompiling any other part of repository software in that you basically break updates for that component if you choose to compile a non-repo version.  If anyone knows of a fix for that let me know.

I'm having the same trouble, I've seen it now on 2 different computers. They were both fresh installs of Hardy. Mind you the same thing happened in upgrades.

Here is another thread about this bug.

[http://ubuntuforums.org/showthread.php?t=784259&page=2](http://ubuntuforums.org/showthread.php?t=784259&page=2)

---

### Post by aldeby on 2008-05-20
it occures to me too... with a fresh hardy install

---

### Post by pwebster25 on 2008-06-05
> **nlangmaid said:**
> I have a similar problem. When I use Places > Network to browse the network, the system can see all the servers, but not the shares on those servers.  No error message, just a blank window.

My workaround while waiting for better brains to fix the problem is to use Places > Connect to Server ... This seems to work.
I have a similar problem.  I have set up bookmarks to network Windows shares on a server on our domain.  All of my data is on this server folder.  It almost always works but periodically when I browse to a specific sub/sub/sub folder it will not open.  It throws an error message that says "could not display all of the contents of "0708 Reqs": Invalid Argument"

Oddly enough, sometimes I can go to an email in evolution and navigate to an attachment just fine in this network shared folder.  Also, the sub-folders (and the documents inside) that are parallel to this one work just fine.

---

### Post by dmizer on 2008-06-05
anyone willing to do a bit of work in the command line can fix this fairly easily.  please see the second link in my sig.

---

### Post by bradrourke on 2008-06-24
I have a similar set of problems and have discovered some of the workarounds people have been discussing. But there is another layer to my woes, as well.

My Ubuntu HH machine has recently been added to an all-Windows share network. Some of the baoxes are Vista, some XP. The shares all work in Win. They all have a workgroup name of "WYZ."

Over on the Ubuntu box, I have learned that:

1) If I use "Places" to browse the network, I see the "XYZ" network but cannot see the machines within it.

2) If I manually add "XYZ" as my "domain" in the Manual Configuration of the Network Connections, then I can see the machines in "XYZ" . . . but cannot see the shares on the machines. (I know this is a reported bug already, and the workaround is #3, below).

3) If I use "Places / Connect To Server" and enter "COMPNAME/ShareName" then I can actually browse the share and it is mounted. I can save the share as a bookmark in places and all is well.

Or so it seems.

The problem is that the new domain (or workgroup) of "XYZ" does not persist after rebooting. I have edited the smb.conf file to add "Workgroup = XYZ" and lots of other things too, but to no avail. EVERY time I reboot, if I want to see the window shares, I need to do steps 2 and 3 above.

So, here is my question . . . is there any way to make new domain names persist across sessions? I have tried so many things my head is spinning. There must be something that I am missing, where domain is wiped on boot or something.

Help?

---

### Post by ftmichael on 2008-06-26
There are a ton of threads regarding using Nautilus to connect to Windows shared files; have a look around.  As for more general Connect to Server issues in Nautilus, particularly the timeout error, see [http://ubuntuforums.org/showthread.php?t=554555](http://ubuntuforums.org/showthread.php?t=554555) .  The advice in that thread fixed the problem for me, but interestingly it didn't help on my boyfriend's computer at all, even though we have the same setup.  Still trying to figure out what the issue is on his system.

Michael

---

### Post by cpane on 2008-07-23
OK, so a new twist on this issue. 

I am currently developing an application that is going to leverage the libsmbclient library to browse samba shares. I am having the same issue, where for some reason, one of my test computers (Windows XP with public shares) is found, but no shares reported. The interesting twist, is this computer used to share just fine. It had a fixed IP address (I run my program in an isolated network for testing). Yesterday, I needed to activate the copy of Windows XP I had on the machine, so I plugged it into my companies main network to DHCP and get on the internet. That worked fine. Once activated, I changed the IP back to fixed and plugged it back into my test network. Since then, no shares are found. its almost like our company DHCP server, or the act of getting a DHCP address in Windows  turned off something in samba on the XP box that was not turned back on when I went back to fixed IP.  

I get the SAME behavior using the Gnome file browser to view shares on that computer. It sees the Windows XP computer, but no shares are reported back. 

Now - If I open firefox, and simply do a smb://ip-address, I see the shares fine and can browse from there. 

Does the Nautalis use libsmbclient.a ? Any thoughts ?


-Chris

---

### Post by Hakkatuka on 2008-09-01
GNOME Commander works for me, it sees all the shares.

---

### Post by blumagic on 2008-09-02
I dont understand why Nautilus and now Gnome-Commander isnt working properly. I was able to browse my windows network since I first installed Hardy, several months ago. Now after several updates, I cant browse my network. I did find that I could use firefox and use smb://ipaddress. This works just fine, as does using samba from the command line.Has anyone figured out what is wrong with Nautius and Gnome-Commander?

thanks,
blu.....

---

