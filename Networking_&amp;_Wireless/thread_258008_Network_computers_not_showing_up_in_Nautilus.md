---
title: "Network computers not showing up in Nautilus"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2006-09-15
WHo can help me?????
I have setup samba on my xubuntu and ubuntu from the repositories. I followed pretty much every guide I could find using gogle so it should be working!! If I go to network neighborhood in WINXP, I can see all the computers and access all of them just fine!!! SO I am thinking, great everything is working. I go over to Ubuntu and when I click on view network servers, I see a thing that says windows network then I see 2 networks, LINUX and MSHOME. I have a roommate that has MSHOME as her workgroup and I have made my workgroup, LINUX. WHen I click on LINUX, an erro comes up that says Could not display all contents or something along those lines. I have tried over and over to get this to work and I just can't figure it out???? Can onyone help me? This is my smb.conf file.
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = LINUX
   netbios name = UBUNTU
   announce version = 5.0
   local master = yes

# server string is the equivalent of the NT Description field
   server string = %h server

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = hosts wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
  interfaces = lo, eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = yes
   invalid users = root

# Map my silly windows username to a unix username
        username map = /etc/samba/username.map

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

############ Misc ############

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
  comment = Home Directories
   browseable = yes
  force user = daniel
    force group = daniel
    public = yes
    writable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
   create mask = 0664

# Directory creation mask is set to 0700 for security reasons. If you want to# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

Help me!!!!!

---

### Post by Iowan on 2006-09-15
Do you have the Samba client package installed?  > If I go to network neighborhood in WINXP, I can see all the computers and access all of them just fine!!!  Sounds like the server side of Samba is working fine.

---

### Post by myname on 2006-09-15
I think this to be a problem with Nautalus.  I installed Kubuntu and was able to browse the network just fine.  As I ran into this issue last week.

If you go to Place/Connect to Server can you connect to your Samba server?  I was able to do this from within Ubuntu, but the Network Servers would not work.

--Kevin

---

### Post by dannyboy79 on 2006-09-16
WHen you say do you have the samba client package installed, exactly what are you referring to??? I have samba installed, it works fine if I mount shares using the smbmount commmand, I can smbclient -L WINXP or whatever server I want and it'll list all the shares available so I am sure it has soemthing to do with the way nautilus interacts qwith samba. It doesn't give me a chance to enter any username or passwordm, it just says, sorry all contents of this folder could not be displayed or something similar. Nautilus can't even view it's own contents thru the "show network server" pull down within Nautilus? What gives, can anyone help???? I would be willing to take someones smb.conf, hosts, resolv.conf and all important files and modify them to be applicable to my own network and that should hopefully do it. I also do have the libgnome-vfs thingy installed as well as smbfs installed. I have read thru tons of forums but it's always a no go, please help.!

---

### Post by dannyboy79 on 2006-09-19
I just can't believe the total lack of support. There has got to be so many Ubuntu users that have a WINXP and UBUNTU networked together and not one person can help???? I don't feel that these forums are only for people that need help, I believe they should be a place that experts go to provide people help so that Ubuntu catches on faster. I mean, I am still a newbie but when I look thru the tons of threads and I see a subject line that I know I can provide some insight to I enter the thread and help someone out. Why aren't there more people like me??? 

I have figured out how to get all the computers XP and linux to show up in Nautilus however when I click on WINXP, it stalls and then finally says, the contents of blah blah couldn't be displayed. and YES, I have googled it for hours, I have read thru 100's of threads and have not found the answer. Please help! Thank you very much if you can help.

---

### Post by tbonius on 2006-09-19
I understand your frustration Dannyboy.  Sometimes the forums are filled with quite a few new users that do not always have the answers.  This is a community forum that is pretty much lept up to date by the community itself.. and not a bunch of "devs" or "experts" that can help in every single area.

I too have had many issues with the Gnome based Nautilus explorer windows and the smb slave-io that it interfaces with.  I have done a few things to try and make it run a little more fluidly.. but have never really gotten the general browse function to work.

On the Windows computers.. make sure that the "force guest" option is turned off:

1. At the Run command, type Regedit and click Enter.
2. Navigate to HKLM\System\CurrentControlSet\Control\LSA.
3. Select the ForceGuest registry value. Set ForceGuest=0 (Disabled).
4. Exit Regedit.

On your Ubuntu computer, try and simplify things for your SMB configuration file.  Make a backup copy of it and try something simple like:

```
# Global parameters
[global]
        workgroup = HOME
        server string = Ubuntu
        security = SHARE
        preferred master = No
        local master = No
        domain master = No

[Share]
        path = /share
        read only = No
        guest ok = Yes
```

Of course you would replace the WORKGROUP and SHARE options with whatever your configuration is, then restart Samba.  Now open Nautilus and choose the connect to server option.. type the IP address string witht he correct handler:

smb://192.168.0.5

Or whatever the IP address of the Windows computer is.  Are you prompted for a username and password?  DO you still get the Nautilus error message?  If so then this definitely sounds like Nautilus misbehaving.

T

---

### Post by Iowan on 2006-09-19
> I can smbclient -L WINXP or whatever server I want and it'll list all the shares available 
Yes, that's what I meant - so smbclient appears to work.
Did you try the "Connect to Server" suggestion? I see the same "Could not display..." message occasionally, but if I "Connect to Server" first, life seems better... sometimes.

---

### Post by dannyboy79 on 2006-09-21
tbonius, what is the difference between security=share and user because I am using user because I have people on my network that I don't want them to have access to my shares or files. I have done the "connect to server" and that works fine. I can mount dirtectories from other computers in my network, it's just that when I use Nautilus to view network computers, then I click  on WINXP, it stalls and then finally says Couldn't display blah blah. WHy is that??? It doens't make any sense!!!! Thank you for trying to help though! Why is when I do do the Connect to Server thingy, i notice that at the top it states that it is trying to connect as guest@winxp, what's that all about? Why isn't it allowing me to connect as daniel since that my username for both machines and that what I am logged in as before I hit the connect to server selection? All my usernames and passwords are the same for every machine on my network named LINUX, all my computers are on the same workgroup, LINUX! Anyway, thanks again for all your help. I guess I'll just have to accept this.

---

### Post by myname on 2006-09-23
I noticed that in a standard Ubuntu and a standard Kubuntu system, the Kubuntu install sees my Windows XP shares where Ubuntu does not. 

Any reasons why?

--Kevin

---

### Post by dannyboy79 on 2006-09-25
wow, that is weird, can you post your smb.conf and any other related config files so I can view the difference between the Kubuntu ones and my Ubuntu one. You are saying that you didn't change anything on the WINXP side correct?

---

### Post by Melcar on 2006-09-25
I'm experiencing a similar problem with Nautilus; it just won't show my Windows network, but I can still access my Ubuntu shared folders on my Windows machines.

---

### Post by warjowuch on 2006-10-03
I have managed to see my windows-computer on the network, but when I enter it in nautilus, it says the good old 'sorry, can't display all contents' thing.

Have tried to set the force guest setting from the windows registry to zero, no restart, no connection. Very frustrating.

I have set the WINS to 'off' in my smb.conf

---

### Post by dannyboy79 on 2006-10-03
same here, i have given up trying to get this to work. i simply just share whatever folders I want within xp and then do a smbclient -L WINXP to see there exact share names, then make a folder and mount them using smbmount. below is cut from a great web site: 

Providing Security when mounting windows shares
The /etc/fstab is readable by everyone so it obviously wouldn't be a good idea to have your Windows password in it. The way to get around this is by using what is known as a credentials file. This is a file that contains just the username and password. The best place to put this file would be in your home directory. Here is how to do it. 

Create a file in your home directory named .smbpasswd (the period at the start of the filename makes it a hidden file). Modifify the permissions on the file so only you have permission to read and write to it. The only thing in the file is your Windows username and password. Here's the commands you would enter to create the credentials file: 

cd
echo username=mywindowsusername > .smbpasswd
echo password=mywindowspassword >> .smbpasswd
chmod 600 .smbpasswd

Substitute your Windows username and password in the commands. No one else except root would be able to read the contents of this file. 

Once that is created, you would modify the line in the /etc/fstab file to look like this: 

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/.smbpasswd 0 0

You can also use the credentials option in the smbmount command for security reasons. That command would look like this: 

smbmount //servername/sharename /mountdirectory -o credentials=/home/myhomedirectory/.smbpasswd

Providing Read/Write Access to the Share 

Another problem with mounting the Windows share as shown in the /etc/fstab file above is that only the root user would have read/write access to the share. All other users would have read only access to it. If you wanted read/write access to it for yourself, you need to specify your userid or groupid. That would change the line in /etc/fstab to look like this: 

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/. smbpasswd,uid=mylinuxusername,gid=mylinuxgroupname 0 0

Whatever user and or group you specified in the line would have read/write access to the mounted share. You can use either the user or group name or the user or group numerical ID. Either should work. 

If you had several users you wanted to have read/write access to it, create a group and add those users to the group. Then specify just that groupid in the /etc/fstab file. You wouldn't need to specify a userid. The line in etc/fstab would look like this: 

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/. smbpasswd,gid=sambausersgroup 0 0

You can see the man pages on smbmount, smbumount, mount, and fstab for more details. 
in case I may have missed something here is the link: [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by warjowuch on 2006-10-03
hmm, thanks for telling you've given up :-) Saves a lot of time I think.
THanks for this little tutorial!

One question though: you told about smbclient -L WINXP
-L = really uppercase, and WINXP must be it's computername/username/IP?
Computername gives me nothing, IP says connection timed out...

---

### Post by dannyboy79 on 2006-10-03
the -L is correct and yes WINXP is the machine name of my WINXP box. well, this will only work if you are able to ping each and every machine by ip as well as machine name, as well as the router, then once you can ping each and every machine by machine name and ip you should be set to share stuff obvisouly after you setup samba. pinging by ip and machine name have nothing to do with samba, ping deals with the tcp/ip protocol. i am at work and don't have my smb.conf files with me so I can't help you totally. also, I am really busy tonight, just gogle. if you have trouble with name resolution start out by seeing if you can get it work with ip address. i have all my computers being statis, not dynamic. which may help. here is a link to using smbclient. but you really need to be able to ping all your machines as well be able to ping itself.

---

### Post by warjowuch on 2006-10-03
THanks,
I tried your ping-thing. The weird thing is, I cannot ping the winXP computer from my ubuntubox, but from the winXP-computer, i CAN ping my ubuntu-pc. This is very strange.

---

### Post by dannyboy79 on 2006-10-03
that means that your windows firewall is blocking ping requests. the reason I set all my machine up to static is for this reason and many others. if you had static you could modify your windows firewall to allow all connections from whatever the ip was on your ubuntu box! now were you able to ping by ip as well machine name or are you not gonna worry about machine name until later?

---

### Post by warjowuch on 2006-10-04
Haye there dannyboy79,
THanks for your help. Your reaction disturbs me a bit. This is a windows a installed myself on my wife's pc. Everywhere I install it I turn off the windows firewall, because there is a hardware-firewall existent in the modem itself. 
But this means (I guess?) I have to double verify that I really turned it off... Or is it only 'virtual' that it is turned off in winXP? That it has a hidden service or something like that?

---

### Post by dannyboy79 on 2006-10-04
well don't let it disturb you to much. i am only guessing that is what it is. there are few things that it could be. did you go to the windows box and check out the firewall settings? can you configure your modem or router to let certain ip's thru to each other? are you sure you don't use a softwall firewall other than what winxp has? also, what did you try to ping it by, name or ip? what does smbtree tell you when you type it in at the terminal. try sudo smbtree also.

---

### Post by warjowuch on 2006-10-04
Will try these things soon, thanks for your attention/help!
Now busy with other stuff, more soon

---

### Post by warjowuch on 2006-10-12
A very weird thing here: I have the following configuration:

Modem incl. switch -> ported to lanport of another switch
other lan-ports for computers

Now I plugged the WinXP computer to the second port of the modem+switch device, now I can reach the thing fantastically. It also shows up in Nautilus. Weird problem, but now I can finally reach the thing.

---

