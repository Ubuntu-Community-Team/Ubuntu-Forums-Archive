---
title: "Is there a way to join my workgroup on my windows network home lan?"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by leefentress on 2007-11-02
got xp desktop, ubuntu laptop. i can access my desktop through samba from my laptop, but not my laptop from my desktop through my network places. is there a way to join my windows network workgroup?

---

### Post by SpiritIsReality on 2007-11-02
howdy
any help here?
[http://screencasts.ubuntu.com/SAMBA_Filesharing](http://screencasts.ubuntu.com/SAMBA_Filesharing)
see the attached notes and posts also at the above link.

[http://ubuntuforums.org/showthread.php?t=528592&highlight=samba](http://ubuntuforums.org/showthread.php?t=528592&highlight=samba)
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)
trails

---

### Post by froy02 on 2007-11-02
See this link for possible solution:

[http://ubuntuforums.org/showthread.php?t=598887](http://ubuntuforums.org/showthread.php?t=598887)

---

### Post by de_valentin on 2007-11-03
I have a similar setup xp desktop and gutsy desktop.
It is just the other way around the way i see it. 

From Ubuntu I can view and browse the windows share folders, but from windows I can's even see the Ubuntu box. And even from Ubuntu when I go to places -> network 
I can see the windows network and the XP box but not Ubuntu, it seems my ubuntu machine is not a part of the "MSHOME" workgroup but can acces it nonetheless.

:confused:Is there a way to solve this?:confused:

---

### Post by SpiritIsReality on 2007-11-03
howdy  	
de_valentin ... I think, in xp, you go to network places, and run the network wizard. Then it
sees the ubuntu box. I don't know which files to edit in xp manually. When the wizard asks if you want to create a disk, select the choice that is something like just continue.
[http://windowshelp.microsoft.com/Windows/en-US/default.mspx](http://windowshelp.microsoft.com/Windows/en-US/default.mspx)
trails
just for reference
xp manual config nic
[http://itc.virginia.edu/desktop/pc/winxp/netconfig.html](http://itc.virginia.edu/desktop/pc/winxp/netconfig.html)
[http://www.google.ca/search?hl=en&q=xp+configure+nic&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=xp+configure+nic&btnG=Search&meta=)

---

### Post by JayvJay on 2007-11-03
It sounds like you need to install samba?  Go to system > administrations>shared folders and you will be prompted to install the correct packages.  You may also need to add mshome or whatever you workgroup or domain name is to the network settings> general tab.  I use a workgroup and when I installed it wrote mshome and mshome.net I changed it and everything is visible in all directions.  luck!

---

### Post by JayvJay on 2007-11-03
You may also need to add mshome or whatever you workgroup or domain name is to the network settings> general tab.

---

### Post by de_valentin on 2007-11-03
That's the strange part I never had to install any packages when opening 'shared folders' 

In shared folders generals tab the box 'this is a WINS server is checked.

---

### Post by de_valentin on 2007-11-03
Can i install them manually and where would I find them?

---

### Post by de_valentin on 2007-11-03
> **SpiritIsReality said:**
> howdy  	
de_valentin ... I think, in xp, you go to network places, and run the network wizard. Then it
sees the ubuntu box. I don't know which files to edit in xp manually. When the wizard asks if you want to create a disk, select the choice that is something like just continue.
[http://windowshelp.microsoft.com/Windows/en-US/default.mspx](http://windowshelp.microsoft.com/Windows/en-US/default.mspx)
trails

The Problem is not with the windows network since it finds the desktop if its booted in xp

The network just doesn't see linux boxes?

---

### Post by SpiritIsReality on 2007-11-04
howdy

JayvJay ... I think what you say is true, that a ubuntu box who runs samba would show up on the Places -> Network window of another ubuntu box. I have yet to try that. --it does.

de_valentin ... ok. A local area network, with two ubuntu boxes, no samba, is shown on this site. I'm not up on how gui the network is. It mentions one box viewing another boxes web page. I'm not sure about the shared folder gui setup. I'm just workin' thru the network page. Have a look and post back here. I don't know how to pin, target, or whatever to a place on a web page yet, but there is a heading called "At Home", just south of the picture of the book, not guite 1\2 way down the page.
[http://www.aboutdebian.com/network.htm](http://www.aboutdebian.com/network.htm)

this , linux and networkin' is interesting sh...stuff !!! haha !
noob12 has referenced this next link in a post I saw a while back.
[http://linux-ip.net/html/](http://linux-ip.net/html/)

and then there's google
[http://www.google.ca/search?hl=en&q=linux+networking&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+networking&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity+networking&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity+networking&btnG=Google+Search&meta=)
trails

---

### Post by de_valentin on 2007-11-04
I've allready folllowed quite a few threads on how to solve this but still without  any succes. So to give this another go.
This is the setup

==(modem) ==(Server/router)
[INDENT][INDENT][INDENT][INDENT]==XP (desktop)
==Dual XP/Gutsy (desktop)]
==XP (old desktop)
[/INDENT]
[/INDENT][/INDENT][/INDENT]
modem is 192.168.1.1 and provided by DSL-provider
Server/Router is 192.168.1.10 (FSG) (running some form of linux)
desktops are 192.168.2.137-139

And as long as the dual boot is booted in XP everything is fine, meaning there are  4 available computers to browse. As i boot in gutsy it doesn't show on the network but is still able to browse through every other desktop and the server. Also other computers can browse this computer.

Network settings tells me that wired connection is not configured
General tab has my machine name and domain name (MSHOME)
the tab DNS shows only one DNS server (192.168.1.1)

It appears SMB and NFS are installed but maybe something is still missing, how can I check that everyting is where it should be. I also have a few folders made shared so there would actually be something.

---

### Post by JayvJay on 2007-11-04
if samba is installed it still may need to be started>

sudo /etc/init.d/samba start

and to access linux shares from xp you need to have a samba password>

sudo smbpasswd  -a your_username

now you have an opportunity to create a password

you should now see the linux machine from xp when viewing workgroup

Luck!

---

### Post by de_valentin on 2007-11-04
I get te following reply

bla@bla:~$ sudo /etc/int.d/samba start
[sudo] password for bla:
sudo: /etc/int.d/samba: command not found


does this mean samba is not installed?

---

### Post by de_valentin on 2007-11-04
here's the response to the password

bla@bla:~$ sudo smbpasswd -a bla
WARNING: Your 'passdb backend' configuration includes multiple backends.  This
is deprecated since Samba 3.0.23.  Please check WHATSNEW.txt or the section 'Passdb
Changes' from the ChangeNotes as part of the Samba HOWTO collection.  Only the first
backend (tdbsam) is used.  The rest is ignored.
New SMB password:
Retype new SMB password:

where can I find these files

---

### Post by SpiritIsReality on 2007-11-04
howdy
sounds like you need to install samba.
cd /etc/init.d
ls
should see samba
trails

---

### Post by de_valentin on 2007-11-04
Yes Samba is in the list as well as

nfs-common
nfs-kernel-server 

now what? I think I'm stuck

---

### Post by SpiritIsReality on 2007-11-04
> ==(modem) ==(Server/router)

                ==XP (desktop)
                ==Dual XP/Gutsy (desktop)]
                ==XP (old desktop)

modem is 192.168.1.1 and provided by DSL-provider
Server/Router is 192.168.1.10 (FSG) (running some form of linux)
desktops are 192.168.[color=red]2[/color].137-139
is that a typing error, or what do
ifconfig -a 
cat /etc/network/interfaces
say? when run on gutsy.
> 
bla@bla:~$ sudo /etc/int.d/samba start
[sudo] password for bla:
sudo: /etc/int.d/samba: command not found
I get this when I run 
fred@piii:~$ sudo /etc/init.d/samba start
 * Starting Samba daemons                                                [ OK ] 
-------------------------
I'd guess that the samba install on gutsy is somehow broke. There could be a better way of fixing this but what I'd try is this:
fred@piii:~$ aptitude help
 remove ........       - Remove packages
 purge  ........       - Remove packages and their configuration files
-s   ........          Simulate actions, but do not actually perform them.
--------------------
so by running 
fred@piii:~$ sudo aptitude -s remove --purge samba
[sudo] password for fred:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libconvert-asn1-perl{p} libcrypt-smbhash-perl{p} libdigest-md4-perl{p} 
  libdigest-sha1-perl{p} libio-socket-ssl-perl{p} libjcode-pm-perl{p} 
  libnet-ldap-perl{p} libnet-ssleay-perl{p} libunicode-map-perl{p} 
  libunicode-map8-perl{p} libunicode-maputf8-perl{p} 
  libunicode-string-perl{p} smbldap-tools{p} 
The following packages will be REMOVED:
  samba 
0 packages upgraded, 0 newly installed, 14 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 15.6MB will be freed.
Do you want to continue? [Y/n/?] ...(I pressed enter for default Y)
Would download/install/remove packages.
-----------------------
It didn't show any errors or threaten to remove ubuntu desktop or anything drastic, so
to fix your problem, if you get a similar reply from aptitude -s, I'd run
sudo aptitude remove --purge samba
----------------------------
then follow this?
[http://ubuntuforums.org/showthread.php?t=528592&highlight=samba](http://ubuntuforums.org/showthread.php?t=528592&highlight=samba)
as well as the advice from others on this thread about the samba dance boogie.
trails

---

### Post by de_valentin on 2007-11-05
Thanks I will try this as soon as i get home.

Oh and by the way it is correct, the [COLOR="Red"]2[/COLOR] in the ip-adres of the desktops was necessary because the modem is also a router (which is disabled)  but it still wasn't possible to let the server give out ip-adresses with 192.168.1.100 so instead we have to use the 192.168.2.100

This is probably not making things any easier...

---

### Post by de_valentin on 2007-11-05
Well there's another big difference this is my result

:~$ sudo aptitude -s remove --purge samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  refblas3{p} 
The following packages will be REMOVED:
  samba 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 10.0MB will be freed.
Do you want to continue? [Y/n/?]

Looks very similar to your output except that there is a lot less to be removed so I guess I will give it a go. I'll be back to tell how it went

---

### Post by de_valentin on 2007-11-05
Well I followed this [http://ubuntuforums.org/showthread.php?t=528592&highlight=samba](http://ubuntuforums.org/showthread.php?t=528592&highlight=samba) down to a T, but it's no use. On the other hand something very peculiar happened.

When I asked my wife to check if she could see the share folder I created she asked if it is called 'ValentinXP' So, guess what my virtualbox windows that was running has its shared folders visible over our home network, but still no ubuntu to anywhere to be found??? 

Also in places on my ubuntu machine I see the valentinxp 'pc' on the home network but no ubuntu.

On the end of the page you linked me there were a few more links so I guess I will try those. See if there is an answer to be found.

---

### Post by SpiritIsReality on 2007-11-05
howdy
I couldn't get the easy way to work.
I'm working at following this post here:
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)
have a look and see what you think. it looks good, but from what I know about samba,
which aint much, there will be issues. haha!
edit: haven't got it working yet. lol
I can't map the drive on xp box, but ubuntu box shows up in "My Network Places", and I can
access it.

trails

---

### Post by de_valentin on 2007-11-06
Yeah I tried that one too but I received an error when I had to start samba

after installing samba  [ OK ]
after stopping it  [ OK ]

starting it up again...

Code:

sudo /etc/init.d/samba start

the reply

command not found

I'm lost, guess I will start over again

---

### Post by SpiritIsReality on 2007-11-06
howdy
That sudo /etc/init.d/samba start
command not found
is a kicker! Something wrong there somewhere, maybe with sudo .
if that was happening on this rig, I'd reinstall,using the alternate install cd, and make sure the cd iso was good, and burn at a slow speed and ... and choose check the cd , when installing. and then when the installation is happening, I'd check the Alt-F4 screen to watch for errors.Then Alt-F1 to the regular install screen. A lot of them are not fatal, but one I've noticed is that on a bandwidth starved subnet, the pentium 2 rigs have a tough time losing connection to the 
security and ubuntu.com servers. Just trying one now, and let it grind for a while after losing connection, and then it is finishing, "remove cd and reboot" step. hope it works. seems to be ok so far.
but what do I know.
I've seen some posts where users are having some degree of success using the 
original default smb.conf file. I think I'm going to try that some time too.
trails

edit:the user trying to run the sudo /etc/init.d/samba , is a member of the admin group?
the username used to install, the first user, is a sudo user. the next users added are not admin by default, have to be given sudo privileges?
by the first user allowing them to join the admin group. check System -> Admin -> Users and Groups ?
does not look like that's the problem because:
fred@piii:~$ su user2
Password: 
user2@piii:/home/fred$ sudo /etc/init.d/samba
[sudo] password for user2:
user2@piii:/home/fred$ sudo /etc/init.d/samba stop
user2@piii:/home/fred$ 
user2@piii:/home/fred$ sudo /etc/init.d/samba start
user2@piii:/home/fred$ 
---------------------
just ignores user2 (non sudo user)

---

