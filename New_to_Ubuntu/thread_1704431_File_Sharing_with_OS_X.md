---
title: "File Sharing with OS X"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by Nwwmac on 2011-03-10
I'm having trouble with file sharing between my iMac and Linux PC. The Linux machine is running Mint 10 64-bit and the Mac is running Snow Leopard 10.6.6. 

The Linux machine can access the Mac's public folder with no problems. 

The iMac can see the Linux machine - it shows up in the Finder as a PC. It can't access it at all. The "connect as" button gives an error saying the Linux server may not exist or may not be available, please re-check. Using the "Go" menu and typing in the IP (afp://XX.X.X.X) gives no result - it just tries and tries and ends with the same error. 

I know very little about networking but I think the two are using samba. The iMac has Samba turned on, and using SWAT on the Linux machine shows that it is running version 3.5.4. SMBD and NMBD are running and Winbindd is not. SWAT also shows no active connections. 

My question is, what do I have to do on the Linux box so that when the iMac tries to connect, I get prompted for my username and password, so that the public folder there can be accessed? 

I have tried turning off the firewall on the Linux machine but that made no difference. I did edit the public folder's properties so that sharing is enabled, but only by me, ie. under group I chose my username. 

Suggestions for how to proceed would be very welcome! :)

---

### Post by Nwwmac on 2011-03-10
I thought I should add that both machines are connected to a Time Capsule via Ethernet.

---

### Post by Ranko Kohime on 2011-03-11
The address should be smb://, and not afp://, if you're utilizing Samba.

---

### Post by Nwwmac on 2011-03-11
Thanks for the suggestion - but it didn't work. 

Is Ubuntu / Mint networking "shut off" by default, ie. is there something I need to turn on, or ok? 

On the Mac it was simple - go to preferences and tick the right box. I can't find anything like that in Admin --> Networking Tools. 

I have something called 'Samba' and it has a space for a 'workgroup'. I don't know what my mac's 'workgroup' is; I don't recall setting one. I have a wireless network name but I didn't think I would need that since both computers are wired into the Airport. 

I also see options to 'create samba user' so I selected myself in the list and added a simple password. 

Nothing. The Linx machine will not respond to the Mac.

---

### Post by Ranko Kohime on 2011-03-12
> **Nwwmac said:**
> Nothing. The Linx machine will not respond to the Mac.
Did you setup any shares on the Linux box?  I'm not sure, but I think the server doesn't respond when it has nothing shared.  You would set this up in the properties dialog for a folder.

---

### Post by coffeecat on 2011-03-12
You're running Mint, which might make a difference when trying to configure things. Although based on Ubuntu, there are some important differences.

First, when you right-clicked on the Public folder to enable sharing, were you prompted to allow the system to download something and restart your session? The download was the samba package and this enables nautilus-shares which are based on smb/samba but which are not set up in the /etc/samba/smb.conf file, but in /var/lib/samba/usershares/.

> **Nwwmac said:**
>  I did edit the public folder's properties so that sharing is enabled, but only by me, ie. under group I chose my username. 

I don't follow that, or perhaps it's a Mint thing. See my screenshot for how the share tab of properties of the Public folder appears on my Maverick system. I had to tick the guest access box for my Mac to be able to access the folder, but it does so from the Finder window just fine. Without the guest access box ticked, when I tried to access it with my Ubuntu username and password, MacOS told me I had entered the wrong password which is nonsense. I haven't solved that, but that's an issue different from yours.

> **Nwwmac said:**
>  I have tried turning off the firewall on the Linux machine but that made no difference.

What firewall configurator is that? Does Mint have its own firewall GUI? All other things excluded, firewall problems are most likely when you encounter difficulties browsing shares, so you are correct to look at that. If Mint doesn't have its own firewall GUI, what did you install? I hope it wasn't firestarter. :(

---

### Post by Morbius1 on 2011-03-12
There are two applications people should never user: SWAT and Gadmin-Samba. 

I think it's time for full disclosure. Please post the output of the following commands so we can see how you are set up:
```
net usershare info --long
```
```
testparm -s
```

---

### Post by Nwwmac on 2011-03-12
Ranko and Coffeecat - I have sharing enabled on the public folder in my  home directory. My settings match Coffeecat's posted image (the  properties tag is identical in Mint). 

The Firewall I'm running is the default one - ufw. I don't think I've  made any changes to it. It's set up to deny incoming and allow outgoing.  No custom rules. 

**sudo lshw** returned a lot of stuff, but right at the end it says: 

```

     *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
configuration: broadcast=yes multicast=yes
```After that I tried to ping a few sites and all of them failed.  That was not expected; I have no problem getting on the Internet with  Mint. 

The commands Morbius1 suggested: 

**1. net usershare info --long**

```

     [public]
path=/home/xxxxx/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y
```**2. testparm -s**

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, LinuxMint)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Public]
    path = /home/xxxxx/Public
    valid users = xxxxx
    read only = No

```

---

### Post by coffeecat on 2011-03-13
> **Nwwmac said:**
> The Firewall I'm running is the default one - ufw.

Aha. The combination of ufw and smb. :sound_of_teeth_grinding:

I only discovered this about the time you started this thread. Have a look at Paqman's posts in this thread:

[http://ubuntuforums.org/showthread.php?t=1705328](http://ubuntuforums.org/showthread.php?t=1705328)

You can also read my post if you want a heavily-censored sense of my feelings on the subject. :wink:

When I posted yesterday I had ufw disabled. Following Paqman's helpful post I did the /etc/default/ufw edit he suggested and also added the samba rules in gufw. I'm not sure if the latter are still necessary.

One slightly rhetorical question for you to consider for your own situation, presuming you have a standard modem-router with firewall to connect to the internet. Why do you need to enable ufw anyway on your internal network? Is there anything on your internal network that you need to protect yourself from?

---

### Post by Morbius1 on 2011-03-13
You do have one other issue. 
This is a Samba Usershare ( aka nautilus-share):
> [public]
path=/home/xxxxx/Public
comment=
usershare_acl=Everyone:F,
guest_ok=yThis is a Samba Classic-share:
> [Public]
    path = /home/xxxxx/Public
    valid users = xxxxx
    read only = NoThe usershare allows everyone and your Aunt Tilly full read / write access to /home/xxxx/Public.

The Classic-share of /home/xxxx/Public can't be more restrictive as it allows only one user read / write access.
I have no idea which type of samba share will win this battle. I would remove one or the other.

---

### Post by Morbius1 on 2011-03-13
>  One slightly rhetorical question for you to consider for your own  situation, presuming you have a standard modem-router with firewall to  connect to the internet. Why do you need to enable ufw anyway on your  internal network? Is there anything on your internal network that you  need to protect yourself from? 
I don't usually comment on firewalls because most of my assets here are desktops and I'm behind a router so I really don't need one. But I did stumble upon something when I tried to help someone with a laptop: There already exists a Samba ( and Cups ) firewall rule.

Running this command details how it is set up:
```
sudo ufw app info Samba
```> Ports:
  137,138/udp
  139,445/tcpWhat I had the laptop user do was set up a desktop launcher named AllowSamba with this command when inside the safety of the home LAN:
```
sudo ufw allow Samba
```And another one ( DenySamba ) with this command when they were out and about:
```
sudo ufw deny Samba
```

I suppose you could take this one step further and set up launchers to just enable ( sudo ufw enable ) and disable ( sudo ufw disable ) the firewall entirely depending on where you are.

---

### Post by mapes12 on 2011-03-13
I don't know about Mint but networking with a Mac a Ubu is a breeze (you're posting on a Ubu forum so Ubu is what I will refer to).

I have a Macbook laptop and Ubu on a Desktop. 

Go to the Ubu machine then right click the folder you want to share with your Mac. Click the sharing option. It may prompt you to download a package to enable sharing. Do it. The folder should then have 2 arrows on it. One pointing left and the other right to show that it's shared.

Then go to your Mac>Finder>Go>Network and you will be able to see the shared folder and transfer stuff between the 2 machines.

If it's all of your /home folder you want to share then the easiest thing to do is create a folder in your /home and call it something like "My Documents" then cut and paste whatever you want into this new folder and enable sharing.

There is no need to get bogged down with any command line stuff to share a Mac and Ubu.

Best wishes.

Mark

---

### Post by Morbius1 on 2011-03-13
@mapes12, that's exactly what he did - this is the share he created with nautilus:
> [public]
path=/home/xxxxx/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y                      You can see how your shares look by issuing the same command:
```
 net usershare info --long
```

---

### Post by Nwwmac on 2011-03-13
Thanks a bunch for sharing this information with me. I'm learning as we go here. 

I'm still muddling here, but this is what I have this morning - 

Mapes - I wish it was as easy as you suggest. That is what I first tried. It did not work, so here I am still plodding along. 

Coffeecat - If ufw is to blame, why is there no change when I turn it off? Both my machines are desktops in my house. They are connected to a Time Capsule which is connected to the modem my cable company gave me. I've always run firewalls on all my computers because I want them safe. Have I been making my life complicated for no reason? 

Mobius1 - Thanks for pointing the dual Samba rules out. I never would have found that. I've tried to fix that by deleting the rule I made with the Samba tool. I did not know that Nautilus was also creating Samba rules. **Testparm - s** no longer has an entry for [Public]. 

I also read Paqman's post and opened up the file as he suggested. Here's the thing though - I'm not sure of the syntax. Can someone show me exactly how it should look after it's edited?

More questions - 

Why does the Linux machine sometimes not show up in the Finder sidebar? Usually it's there, but sometimes it drops out (like today). This happens even when I'm not mucking with anything so it's puzzling. When it's there I can't access it, but it makes me nervous when it drops out. 

I am successfully running Synergy so that I can share one keyboard and mouse with both machines. The Mac is the server and the Linux machine is the client. That works even with ufw on. Why does that work so well and so easily, and Samba does not? What protocol is working there?

---

### Post by Morbius1 on 2011-03-13
From the ubuntu machine post the output of the following command:
```
smbtree
```
It doesn't fix anything it's just a reporting tool that might give an error if something is messed up.

---

### Post by Nwwmac on 2011-03-13
Well, this is interesting. 

smbtree prompted me for my password, and then gave nothing.

---

### Post by Morbius1 on 2011-03-13
Restart the following service:
```
sudo service nmbd restart
```[COLOR=Blue]EDIT:[/COLOR] If it gives you an incoherent message about nmbd not there just start it:
```
 sudo service nmbd start
```Then run smbtree again.

If it lists your share and has no error messages try to access it from OSX.

---

### Post by Nwwmac on 2011-03-13
restarting nmbd gives

```
nmbd start/running, process 5435

```smbtree response did not change after doing that.

---

### Post by coffeecat on 2011-03-13
I won't make any more comments about samba because Morbius1 knows more than I and you're in good hands. I'll just pick up a couple of your questions about the firewall and then get out of the way.

> **Nwwmac said:**
> If ufw is to blame, why is there no change when I turn it off?

Probably because of the issue in samba that Morbius1 is helping you with. However, it's sensible to disable ufw while you're trying to get shares to work. At least then you know it's not a firewall problem.

> **Nwwmac said:**
> They are connected to a Time Capsule which is connected to the modem my  cable company gave me. I've always run firewalls on all my computers  because I want them safe. Have I been making my life complicated for no  reason? 

OK, you've got a Time Capsule, your iMac and Ubuntu PC all connected to the cable modem somehow, but they can't all be connected directly. There must be a router in there somewhere otherwise your local network wouldn't work - or see below. Are you sure that's not a modem-router? If you have a router, you have a firewall built into it, and if this firewall is configured correctly, then your local network is protected from the internet. Which means that Ubuntu only needs an active firewall if you need to protect it from another device on your local network. This was the point of the rhetorical question I posed. If you do have a router with a properly setup firewall then you probably don't need to enable ufw in Ubuntu.

Or...

> **Nwwmac said:**
> I am successfully running Synergy so that I can share one keyboard and  mouse with both machines. The Mac is the server and the Linux machine is  the client.

How does that work? I'm not familiar with Synergy but from a bit of googling it seems that you still need a local network - which would mean a router somewhere.

That being said...

> **Nwwmac said:**
> 
I also read Paqman's post and opened up the file as he suggested. Here's the thing though - I'm not sure of the syntax. Can someone show me exactly how it should look after it's edited?

If you really want to use ufw, this is the edited IPT_MODULES line in /etc/default/ufw:

```
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_pptp nf_conntrack_netbios_ns"
```

---

### Post by Morbius1 on 2011-03-13
I hate to disagree with your kind words coffeecat,  but I'm running out of ideas. 

The only thing left that would explain smbtree not showing anything - assuming the firewall is off and nmbd and smbd are running - is the length of the host name.

By default the samba server will broadcast it's name using the host name of the box it's on. But that name to be visible must be less that or equal to 15 characters in length.
 Bring up a terminal and type: hostname

If it's more that 15 characters long override it in /etc/samba/smb.conf by adding a line in [global] section:
```
netbios name = something-15-characters-or-less
```Then restart all the samba services:
```
sudo service smbd restart
sudo service nmbd restart
```

---

### Post by Nwwmac on 2011-03-13
> OK, you've got a Time Capsule, your iMac and Ubuntu PC all connected to  the cable modem somehow, but they can't all be connected directly. There  must be a router in there somewhereI think the Time Capsule is the router. It's between the cable modem and  all the Internet devices in the house, wired and wireless. I've never  heard about it having a firewall though. There's a [discussion of the issue here]("http://discussions.apple.com/thread.jspa?messageID=6744663"). For the time being I have ufw off. 

> By default the samba server will broadcast it's name using the host name  of the box it's on. But that name to be visible must be less that or  equal to 15 characters in length.The machine name / host name is "Linux" (no quotes), so I don't think  that's the issue. I noticed when I was figuring out Synergy (which is  terrifically useful!) that the Linux machine shows in the Finder as  "linux". One of the things I had to do to make that connection work was  to specify the Mint machine in the Mac server with the lower case L. The  hostname command in Mint gives the name of the machine with a capital  L. 

I've attached a shot of the Synergy server settings on the Mac in case it's not clear. 

[IMG]http://www.flickr.com/photos/9898677@N08/5525071138/[/IMG]Would it be worth a try to rename the Mint PC 'linux'? If so, how would I do that? 

A few people have mentioned that first creating a share in nautilus  prompts a download. I don't really recall that happening but according  to a Mint forum on sharing, that's because it's [included in the install]("http://forums.linuxmint.com/viewtopic.php?f=42&t=23169#p199564"): 

> This HowTo is about Nautilus-share as it has become the default method  to create shares on Mint and Ubuntu. Nautilus-share definitions are  located in /var/lib/samba/usershares as opposed to /etc/samba/smb.conf  in "Classic Samba".

This method is invoked by Opening Nautilus > right clicking on the directory you want to share > Sharing Options. Please
note  that you can only share folders that you own ( i.e., folders in your  own home directory or mount points to partitions where you are the  owner, for example ) although there are ways around this limitation. 

This method relies on the following package:
**nautilus-share** ( this should be part of the base install )Sadly, this Forum How To is a few years old and did not help me much at all. 

A look in the Software Manager shows nautilus-share is installed but I  don't know what it would be called in the process list. By the Terminal  results Samba does seem to be running: 

```
xxxxx@Linux ~ $ sudo service nmbd restart
[sudo] password for xxxxx: 
nmbd start/running, process 5938
xxxxx@Linux ~ $ sudo service smbd restart
smbd start/running, process 5944

```My decidedly amateur ideas are to 
1) rename the Mint machine or, 
2) see if there are other protocols I could use. Is Bonjour / Zerconf an option?

---

### Post by Morbius1 on 2011-03-14
> A few people have mentioned that first creating a share in nautilus   prompts a download. I don't really recall that happening but according   to a Mint forum on sharing, that's because it's included in the install.The reason for the confusion between Mint and Ubuntu references concerning a prompt for a download is that Samba itself is included in the base install in Mint but not in Ubuntu. When you first use nautilus to share a folder in Ubuntu it will prompt for an install for samba - it's already there in Mint. Has nothing to do with nautilus-share.

When you run **[COLOR=Blue]smbtree[/COLOR]** it should show you all the shares on every machine in your network. But smbtree can't even see the shares on the very machine it's being run from. You aren't going anywhere until that is resolved first. 

Install nmap:
```
sudo apt-get install nmap
```Run the following command substituting 192.168.0.100 with the ip address of the Ubuntu machine:
```
sudo nmap -sS -sU -T4 192.168.0.100
```You should get an output that looks something like this:
> Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-03-14 07:22 EDT
Interesting ports on 192.168.0.100:
Not shown: 1992 closed ports
PORT     STATE         SERVICE
[COLOR=Blue]139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds[/COLOR]
631/tcp  open          ipp
68/udp   open|filtered dhcpc
[COLOR=Blue]137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm[/COLOR]
631/udp  open|filtered ipp
5353/udp open|filtered zeroconfThe one's in blue are samba related.

Edit: Another possibility is the share at /home/xxxxx/Public is in an encrypted home directory or the permissions have been messed with:
```
 ls -al /home/xxxxx
```

---

### Post by joffe on 2011-03-14
Thank you so much Morbius1 for solving my problem!!!!!

I have gotten file sharing to work with earlier releases but with my half year old new notebook running Natty I have been totally unable to share files with my girlfriends MacBook.

It turns out that when I installed Natty the wizard proposed the hostname "johan-aspire-3820". That's 17 characters. Now that I saw your post I immediately changed the hostname to a much shorter one in:

```
/etc/hostname
/etc/hosts
```

A reboot later and voilà! I can now share files with OSX!

I will file a bug on this as soon I get around the software-center bug. Thanks again!

---

### Post by Nwwmac on 2011-03-14
I did as requested and this is the terminal output from **sudo nmap -sS -sU -T4**

```
Starting Nmap 5.21 ( http://nmap.org ) at 2011-03-14 16:06 PDT
Nmap scan report for Linux (xx.x.x.x)
Host is up (0.0000080s latency).
Not shown: 1993 closed ports
PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
901/tcp  open          samba-swat
68/udp   open|filtered dhcpc
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.83 seconds

```Thanks again for your efforts! This has been a bigger job than I expected. :o

---

### Post by spook1980 on 2011-03-14
> **Nwwmac said:**
> I'm having trouble with file sharing between my iMac and Linux PC. The Linux machine is running Mint 10 64-bit and the Mac is running Snow Leopard 10.6.6. 

The Linux machine can access the Mac's public folder with no problems. 

The iMac can see the Linux machine - it shows up in the Finder as a PC. It can't access it at all. The "connect as" button gives an error saying the Linux server may not exist or may not be available, please re-check. Using the "Go" menu and typing in the IP (afp://XX.X.X.X) gives no result - it just tries and tries and ends with the same error. 

I know very little about networking but I think the two are using samba. The iMac has Samba turned on, and using SWAT on the Linux machine shows that it is running version 3.5.4. SMBD and NMBD are running and Winbindd is not. SWAT also shows no active connections. 

My question is, what do I have to do on the Linux box so that when the iMac tries to connect, I get prompted for my username and password, so that the public folder there can be accessed? 

I have tried turning off the firewall on the Linux machine but that made no difference. I did edit the public folder's properties so that sharing is enabled, but only by me, ie. under group I chose my username. 

Suggestions for how to proceed would be very welcome! :)

try NFS it works way better then samba i only use samba when i got no choice (like my modded xbox) everything else in my house is by nfs and nfs is easy on mac as it is also part of the linux/unix family.

[http://www.cyberciti.biz/faq/apple-mac-osx-nfs-mount-command-tutorial/](http://www.cyberciti.biz/faq/apple-mac-osx-nfs-mount-command-tutorial/)

---

### Post by Nwwmac on 2011-03-14
Hmm. I've tried the other step now. Either I've not got the syntax right or something is weird. 

The Home folder is not encrypted (how can I verify that?). To see if the problem is specific to the Public folder, I created a new folder called Share, and used Nautilus to set its properties. The result was the same. 

```
xxxx@Linux ~ $- ls -al /home/public
ls: cannot access /home/public: No such file or directory
xxxx@Linux ~ $  ls -al /home/Public
ls: cannot access /home/Public: No such file or directory
xxxx@Linux ~ $ ls -al /home/Share
ls: cannot access /home/Share: No such file or directory
```

---

### Post by flyingsolo on 2011-03-14
Quick note of thanks--I've struggled for ages with the mac to ubuntu sharing and couldn't understand why the macs could see but not connect to the ubuntu machines.  Who knew it was as simple as shortening the computer name under 15 characters!?  That's an obscure little gem!

---

### Post by joffe on 2011-03-15
I filed a bug regarding the hostname that was set by the installer. Please chime in using the "This bug affects you" button if you were bitten by the bug.

[[COLOR="Navy"]Bug #735072 in Ubuntu: “The hostname proposed by installer is too long for file sharing to work correctly.”[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/735072")

---

### Post by Morbius1 on 2011-03-15
@Nwwmac, According to your post your only shared folder has this definition:
> [public]
**[COLOR=Blue] path=/home/xxxxx/Public[/COLOR]**
comment=
usershare_acl=Everyone:F,
guest_ok=y                      You did this:
> ls -al /home/public
ls: cannot access /home/public: No such file or directoryThat's a fact - there is no such thing as /home/public

I assume [COLOR=Blue]**xxxxx**[/COLOR] is your user name and that the Public folder is in your home folder so what I'm after is the ownership and permissions of your home folder , it's parent folder, and it's contents:
```
ls -al /home/xxxxx
```Where **[COLOR=Blue]xxxxx[/COLOR]** is your user name

[I]SIDE NOTE: @joffe, The 15 character limit on the host name is a Samba requirement not a Linux requirement. I think the Linux limit is 64 characters - don't hold me to that.;). Most of the people who put together Linux distros eat, sleep, and breath only Linux. If they bought an iPad they already removed the native OS and replaced with Linux. Samba is a foreign protocol ( Windows SMB ) and they don't understand why anyone uses it and why they have to add it to the repository. You might get a response from your bug report but ....
[/I]

---

### Post by joffe on 2011-03-15
> **Morbius1 said:**
> [I]SIDE NOTE: @joffe, The 15 character limit on the host name is a Samba requirement not a Linux requirement. I think the Linux limit is 64 characters - don't hold me to that.;). Most of the people who put together Linux distros eat, sleep, and breath only Linux. If they bought an iPad they already removed the native OS and replaced with Linux. Samba is a foreign protocol ( Windows SMB ) and they don't understand why anyone uses it and why they have to add it to the repository. You might get a response from your bug report but ....
[/I]

True, but then why is the samba hostname set equal to the linux hostname? If they have different boundaries that would be asking for trouble. I'd say better setting the hostname to something less than 16 chars if it has to be the same for samba and use a dns alias or something if there has to be a longer description as well for the box.

---

### Post by Morbius1 on 2011-03-15
@joffe, I agree with your comments and it would eliminate many forum posts about this problem. My only point was that Samba bug reports in any distro's bug reporting system seem to end up in electron heaven :wink:

---

### Post by Nwwmac on 2011-03-15
> there is no such thing as /home/publicRight you are. Here is the second attempt. I hope this is what you are looking for. 

I don't know what the permissions code mean but it's interesting that the properties for "Public" and "Share" are different.

```
ls -al /home/xxxxx
total 38532
drwxr-xr-x 57 xxxxx xxxxx     4096 2011-03-15 17:14 .
drwxr-xr-x  3 root root     4096 2011-03-04 14:43 ..
drwx------  3 xxxxx xxxxx     4096 2011-03-04 15:31 .adobe
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-06 09:37 .aptoncd
drwxr-xr-x  3 xxxxx xxxxx     4096 2011-03-11 12:18 .avidemux
-rw-r--r--  1 xxxxx xxxxx     7469 2011-03-05 10:11 .banter.log
-rw-------  1 xxxxx xxxxx     2745 2011-03-14 17:50 .bash_history
-rw-r--r--  1 xxxxx xxxxx      220 2011-03-04 14:43 .bash_logout
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-08 17:38 .burg-manager
drwx------ 16 xxxxx xxxxx     4096 2011-03-13 12:26 .cache
drwx------  3 xxxxx xxxxx     4096 2011-03-05 13:04 .compiz
drwxr-xr-x 25 xxxxx xxxxx     4096 2011-03-09 14:48 .config
drwx------  3 xxxxx xxxxx     4096 2011-03-04 14:50 .dbus
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-09 14:44 Desktop
-rw-r--r--  1 xxxxx xxxxx       41 2011-03-13 12:26 .dmrc
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-08 20:02 Documents
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-15 16:49 Downloads
drwxr-xr-x 16 xxxxx xxxxx     4096 2011-03-13 12:26 Dropbox
drwxr-xr-x  3 xxxxx xxxxx     4096 2011-03-14 19:32 .dropbox
drwxr-xr-x  5 xxxxx xxxxx     4096 2011-03-04 15:53 .dropbox-dist
drwxr-xr-x  3 xxxxx xxxxx     4096 2011-03-10 14:18 .dvdcss
-rw-------  1 xxxxx xxxxx       16 2011-03-04 14:50 .esd_auth
drwx------  3 xxxxx xxxxx     4096 2011-03-05 09:39 .evolution
-rw-r--r--  1 xxxxx xxxxx     2192 2011-03-06 12:04 .face
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-04 19:07 .fontconfig
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-04 19:07 .fonts
-rw-r--r--  1 xxxxx xxxxx      766 2011-03-04 19:07 .fonts.conf
drwx------  4 xxxxx xxxxx     4096 2011-03-15 14:06 .gconf
drwx------  2 xxxxx xxxxx     4096 2011-03-15 17:14 .gconfd
-rw-r-----  1 xxxxx xxxxx        0 2011-03-13 22:17 .gksu.lock
drwx------  9 xxxxx xxxxx     4096 2011-03-13 18:39 .gnome2
drwx------  2 xxxxx xxxxx     4096 2011-03-04 14:50 .gnome2_private
drwx------  2 xxxxx xxxxx     4096 2011-03-06 19:01 .gnupg
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-07 16:50 .gstreamer-0.10
-rw-r--r--  1 xxxxx xxxxx      132 2011-03-13 12:26 .gtk-bookmarks
-rw-r--r--  1 xxxxx xxxxx      132 2010-04-23 13:28 .gtkrc-2.0
dr-x------  2 xxxxx xxxxx        0 2011-03-13 12:26 .gvfs
drwxr-----  2 xxxxx xxxxx     4096 2011-03-06 12:34 .hplip
-rw-------  1 xxxxx xxxxx     2516 2011-03-13 12:26 .ICEauthority
drwxr-xr-x  5 xxxxx xxxxx     4096 2011-03-08 20:40 .icons
lrwxrwxrwx  1 xxxxx xxxxx       62 2011-03-04 16:38 Link to x.html
drwxr-xr-x  7 xxxxx xxxxx     4096 2011-03-04 15:19 .linuxmint
drwxr-xr-x  3 xxxxx xxxxx     4096 2011-03-04 14:43 .local
drwxr-xr-x  3 xxxxx xxxxx     4096 2011-03-04 15:24 .macromedia
-rw-r--r--  1 xxxxx xxxxx      363 2011-03-05 10:03 MobileMe Mail - Inbox.desktop
drwx------  4 xxxxx xxxxx     4096 2011-03-04 15:17 .mozilla
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-07 16:02 .mplayer
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-04 14:50 Music
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-04 14:50 .nautilus
drwxr-xr-x  3 xxxxx xxxxx     4096 2011-03-06 11:45 .nowplaying
drwxr-xr-x  3 xxxxx xxxxx     4096 2011-03-06 11:42 .openoffice.org
drwxr-xr-x 16 xxxxx xxxxx     4096 2011-03-09 14:43 .opera
drwxr-xr-x  6 xxxxx xxxxx     4096 2011-03-08 18:08 Pictures
drwx------  3 xxxxx xxxxx     4096 2011-03-04 15:31 .pki
-rw-r--r--  1 xxxxx xxxxx       37 2011-03-06 12:33 .printer-groups.xml
-rw-r--r--  1 xxxxx xxxxx      675 2011-03-04 14:43 .profile
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-13 18:39 Public
drwx------  2 xxxxx xxxxx     4096 2011-03-13 12:26 .pulse
-rw-------  1 xxxxx xxxxx      256 2011-03-04 14:50 .pulse-cookie
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-13 12:29 .quicksynergy
drw-------  2 xxxxx xxxxx     4096 2011-03-04 17:11 .recently-used.xbel
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-06 11:43 .screenlets
drwxrwxrwx  2 xxxxx xxxxx     4096 2011-03-13 18:39 Share
drwx------  3 xxxxx xxxxx     4096 2011-03-13 13:28 .Skype
drwx------  2 xxxxx xxxxx     4096 2011-03-06 19:01 .ssh
-rw-r--r--  1 xxxxx xxxxx        0 2011-03-04 14:50 .sudo_as_admin_successful
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-04 14:50 Templates
drwxr-xr-x  6 xxxxx xxxxx     4096 2011-03-12 09:45 .themes
drwx------  5 xxxxx xxxxx     4096 2011-03-07 14:05 .thumbnails
drwx------  3 xxxxx xxxxx     4096 2011-03-10 17:45 .thunderbird
drwxr-xr-x  4 xxxxx xxxxx     4096 2011-03-14 17:29 Videos
drwxr-xr-x  2 xxxxx xxxxx     4096 2011-03-10 14:10 .VirtualBox
drwxr-xr-x  3 xxxxx xxxxx     4096 2011-03-10 14:08 VirtualBox VMs
drwxr-xr-x  8 xxxxx xxxxx     4096 2011-03-05 11:54 .xbmc
-rw-r--r--  1 xxxxx xxxxx     1446 2011-03-09 15:58 .xscreensaver-getimage.cache
-rw-------  1 xxxxx xxxxx 13658125 2011-03-15 17:14 .xsession-errors
-rw-------  1 xxxxx xxxxx 25487735 2011-03-13 12:24 .xsession-errors.old
xxxxx
```

---

### Post by Morbius1 on 2011-03-16
No matter what you post everything looks textbook correct. You do have a quirk on the permissions of /home/user/Public which nautilus-share should have automatically corrected but perhaps you overrode the setting yourself. That would cause an inability to write but you should have access.

I keep coming back to one fundamental problem: smbtree will not show the shares on it's own box. If Linux can't see it's own shares no one else can either. 

If you installed Mint from the DVD then I would suggest an experiment. Mint comes with Samba pre -installed so everything you need for samba to work is available even on the LiveDVD.

Boot into the install DVD and then :

Open "mint's Home"
Right Click on Documents
Select Sharing Options and then select all the boxes - then create share.

Then type:
```
smbtree
```It should come back with this:
> WORKGROUP
\\Mint
\\Mint\documents
If it does that then see if your Mac can access it.

[COLOR=Blue]EDIT[/COLOR]: And to bypass whatever networking issues you may be having access it by ip address, for example:
```
 smb://192.168.0.101
```If all of that works then something has happened since your initial install. It's either a bad update, something you added ( SWAT is the first culprit ), or something you enabled.

---

### Post by Nwwmac on 2011-03-20
Sorry I've been unable to get here for a few days. Life reared up and then I spent some time trying to get away from Samba and see if I could use Bonjour / zerconf to work. Despite finding [a pretty good guide]("http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/") I have been unable to get anywhere with this. 

Well, I did get the Linix machine to show in the Finder as a Mac Pro, and then drop out and show as not one but two PCs. Props for me. ;) I probably have a few protocols running in an incomplete manner. 

Then I remembered your suggestion to boot from the install CD and share a folder. 

What a surprise! Everything works. Linux can access the Mac's shared folders (something that has broken in this 'fixing' process) and the Mac can access the newly created public folder on Linux. 

smbtree gives a nice detailed list of the everything on the network too. 

I have no idea where it all went wrong. I never would have bothered with SWAT or avahi or any of it if it had worked when I first tried to use it. 

I'm close to admitting defeat until there is a new version of Linux I want to try - Natty or Mint 11 or even Elementary if it ever gets released. At the least of it I know what to look for. I should never have been this complex. 

If you have more suggestions for me, I'm willing to try them. If not, thanks a bunch for all you've done. I will make note of your terminal commands for future reference.

---

### Post by Nwwmac on 2011-03-23
It looks like [Apple will be dropping Samba]("http://www.appleinsider.com/articles/11/03/23/inside_mac_os_x_10_7_lion_server_apple_replaces_samba_for_windows_networking_services.html") in the next release of OS X, due to a stricter license on it's usage. 

I wonder what this means for Ubuntu? 

Apple will have their own support for Windows networking in Lion.

---

### Post by 8dogsbarking on 2011-03-24
I am having a similar file share problem with OS X 10.5.8 and a USB hard drive share.  Here is the print out of smbtree:

ubuntu@ubuntu-Dimension-4600i:~$ smbtree
Enter ubuntu's password: 
WORKGROUP
    \\UBUNTU-DIMENSION        ubuntu-Dimension-4600i server (Samba, Ubuntu)
cli_start_connection: failed to connect to UBUNTU-DIMENSION<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

I saw where the computer name length had something to do with it, but I don't know how or where to change the names.  Any help would be great!  Thank you.

---

### Post by Morbius1 on 2011-03-25
8dogsbarking, you're machine name "ubuntu-Dimension-4600i" is 7 characters too long. See post #20 to fix.

---

### Post by joffe on 2011-03-30
I think I finally got the developers' attention on this!!! My bug is confirmed with high priority:

[[COLOR="Navy"]The hostname proposed by installer is too long for file sharing to work correctly.[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/735072")


According to their ranking it seems to be their top priority:

[URL="https://bugs.launchpad.net/ubuntu/+source/samba"][COLOR="Navy"]https://bugs.launchpad.net/ubuntu/+source/samba
[/COLOR][/URL]
Please click the little yellow pen next to "Does this bug affect you?" to add yourselves to the list if you were bitten by this bug.

---

### Post by joffe on 2011-03-30
Oh yeah, and thanks again for your help Morbius1!

---

### Post by stmiller on 2011-03-30
Samba- yuck!! :) There are two other good options I wanted to throw in here:

NFS
AFP

Apple's native network file share is fully supported in Linux to share, host, read, write, etc.

It takes a bit to setup though. In Linux the project is called netatalk.

[http://netatalk.sourceforge.net/](http://netatalk.sourceforge.net/)

You can google for 'netatalk ubuntu' for lots of how-tos. Random Ex:

[http://maketecheasier.com/ubuntu-intrepid-how-to-share-file-with-mac-os-x-via-netatalk/2008/11/05](http://maketecheasier.com/ubuntu-intrepid-how-to-share-file-with-mac-os-x-via-netatalk/2008/11/05)


NFS works as well with Linux / OS X:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

