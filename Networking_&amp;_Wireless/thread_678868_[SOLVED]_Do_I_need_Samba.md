---
title: "[SOLVED] Do I need Samba"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by tad1073 on 2008-01-26
I have samba installed and set up using [ this tutorial ](http://ubuntuforums.org/showthread.php?t=202605). i want to be able to access my files on the shared computer, which is an XP, as well as the printer but it is not working.

```

[global]
    ; General server settings
    netbios name = thomas
    
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, wifi0
    bind interfaces only = true
    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = thomas
    force group = thomas
available = yes
browsable = yes
public = no
writable = yes

```

---

### Post by runemaste644 on 2008-01-26
Ive also had trouble with samba and never got it to work. I simply gave up :/

---

### Post by tad1073 on 2008-01-26
I can't even get "My Documents" in the "My Network Places" folder on the XP machine any more. We were using "Network Magic" but we were only allowed so many devices and files and if you wanted to add extra's you had to pay for there service, which is stupid, because you can do the same thing with XP for free.

---

### Post by Iowan on 2008-01-26
Samba client should already be installed on Ubuntu.  Accessing files on the XP machine from Ubuntu would use the client - sharing files from Ubuntu to XP would require the Samba server. So (IMHO) you shouldn't need the server installed (but it shouldn't adversely affect filesharing either).

Depending on how sharing is set up in XP, Places>Connect to Server>(Service type:Windows Share),Browse Network should yield results.

---

### Post by jonandrews on 2008-01-26
Have a look at my step-by-step guide to networking between Ubuntu / Windows PC's:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by tad1073 on 2008-01-26
Will your how-to work for a wireless conection. that is the only connection i have on my ubuntu box.

---

### Post by tad1073 on 2008-02-01
I have been giving this another go to avail what am I doing wrong? the computer I want to access is running XP Home Edition if that s makes any difference.

Network Magic see's "computer Sever (Ubuntu,Samba)" see's "MyFiles" the only problem with Network Magic is you have to pay for the service after the trial priod and why would i pay someone for me to have access to my own files that is kinda an oxymoron wouldn't you say. 

anyway-->HELLLLP!!!

---

### Post by Iowan on 2008-02-01
Start simple - can you ping the XP box from the Ubuntu box?  I'm probably mis-remembering something about XP Home edition being network-handicapped.

Especially considering [THIS]("http://support.microsoft.com/kb/813936/") series of articles.

---

### Post by tad1073 on 2008-02-01
I tried last night and i can't ping the xp box, i just tried again and stll can't ping the xp machine. there is norton anti-virus suite w/ firewall on that machine by the way.

---

### Post by tad1073 on 2008-02-03
bump

---

### Post by swerdna on 2008-02-03
Suggest you change as indicated:
>     netbios name = thomas
    workgroup = MSHOME
    announce version = 5.0
**    socket options = TCP_NODELAY IPTOS_LOWDELAY**
**#    interfaces = lo, wifi0**
**#    bind interfaces only = true**
    passdb backend = tdbsam
    security = user
    null passwords = true
**#    username map = /etc/samba/smbusers**
**    name resolve order = bcast lmhosts wins host**

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

#etc etc etc etc 

[MyFiles]
    path = /home/samba
    read only = no
    guest ok = no
    force user = thomas
#the rest is perhaps superfluous
======================
Then make sure the owner of the directory /home/samba is thomas and that thomas as been added to the samba user database with this command: **sudo smbpasswd -a thomas**

And restart the lan coputers in sequence, Ubuntu first -- then the other/s then ubuntiu again. Have a cup tea for it all to seep around the network

Swerdna

---

### Post by tad1073 on 2008-02-03
my netbios name? Should it be thomas or computer (thomas@computer:~)

I am having trouble with xp also. I can share filess but they do not show up in "My Network Places"

---

### Post by swerdna on 2008-02-03
> **tad1073 said:**
> my netbios name? Should it be thomas or computer (thomas@computer:~)[
computer is your hostname. It's traditional to use the hostname. Saves confusion (unless computer is used somewhere else on the network)
> **tad1073 said:**
>  having trouble with xp also. I can share filess but they do not show up in "My Network Places"
If you have manipulated the windows firewall away from the defaults, try turning it off, otherwise if defaults only and either w2000 or wxp then is OK. But if you have a third party firewall on windows that usually will interfere until you let the IP range of the LAN through or turn the third party firewall off.

If firewall on Ubuntu (probably not) then turn it off.

If you have enabled windows for a wins server then un-enable that.

What is the IP address of windows (ipconfig/all)
What is the ip address of Ubuntu ([COLOR="RoyalBlue"]sudo ifconfig[/COLOR] for wired, [COLOR="RoyalBlue"]sudo iwconfig[/COLOR] for wireless)
Swerdna

---

### Post by tad1073 on 2008-02-03
iptables for ubuntu w/firestarter interface and norton suite on xp home edition

Also, I have installed Network Magic that came with the router. It see's ubuntu, the files I shared on ubuntu and the files i shared on xp.

---

### Post by swerdna on 2008-02-03
> **tad1073 said:**
> iptables for ubuntu w/firestarter interface and norton suite on xp home edition

Also, I have installed Network Magic that came with the router. It see's ubuntu, the files I shared on ubuntu and the files i shared on xp.
You can vastly simplify troubleshooting by turning off all firewalls until your Linux/Windows network is running nicely. Otherwise it can be a decision-pathways-nightmare. So do that then attend to the other points I mentioned.

Swerdna

---

### Post by Iowan on 2008-02-06
Wireless isn't my cup-of-tea...  You can check **ifconfig** on Ubuntu, and  **ipconfig** on XP to see if the machines have addresses in the same subnet.  Did you manually set addresses - or are you using DHCP?

Sorry - missed this post:> **swerdna said:**
> What is the IP address of windows (ipconfig/all)
What is the ip address of Ubuntu ([COLOR="RoyalBlue"]sudo ifconfig[/COLOR] for wired, [COLOR="RoyalBlue"]sudo iwconfig[/COLOR] for wireless)
Swerdna

---

### Post by tad1073 on 2008-02-06
I manualy set the address on the windows machine and using DHCP on Linux because I can't get wirless if I set the ip manually.

---

### Post by Iowan on 2008-02-07
Are the two machines in the same subnet? (what are their IP addresses?).

---

### Post by tad1073 on 2008-02-07
The windows machine that the files are on has been set back to auto dhcp. I also have changed the firewall setting on the xp machine and now I can ping that box, but I still can't see the folders I am sharing.

---

### Post by Iowan on 2008-02-07
Places>Connect to Server>(Service type:Windows Share),Browse Network should yield results. Is it showing the XP box?

---

### Post by tad1073 on 2008-02-07
I have tried that already and nothing shows up.

---

### Post by totalnub on 2008-02-07
try smbtree from the command line
should list available network shares

---

### Post by tad1073 on 2008-02-07
again, nothing.

---

### Post by tad1073 on 2008-02-07
I can ping the Linux box from xp, so I am a little closer.

---

### Post by totalnub on 2008-02-07
how are your shares set up in xp? just right-click -> sharing and security etc?

---

### Post by tad1073 on 2008-02-07
i have both boxes checked that are in Network sharing and Security.

---

### Post by tad1073 on 2008-02-07
WHOOOT!!!! I got it working. I can see all my files from ubuntu. Now for printer sharing, I am going to need some help with that.

---

### Post by Iowan on 2008-02-07
GREAT!!! Mark this one [SOLVED] and start researching the printing.  My printer has a built-in print server, but I had to address it by IP address instead of by name.

---

### Post by tad1073 on 2008-02-13
I have another problem. i can ping my ip address form xp and I can ping xp's ip address from ubuntu. i can access files that are on the xp machine but I can not access ubuntu from xp. Any suggestions?

---

### Post by tad1073 on 2008-02-13
bump

---

### Post by Iowan on 2008-02-13
Sharing from Ubuntu to XP WILL require Samba. If share security=user (as your earlier posted config suggests), the user will need a valid Samba (and UBUNTU?) account.  Samba will need to be in the same workgroup as the XP machine. Did the link in Post#5 help?

---

### Post by tad1073 on 2008-02-13
no, not realy, to be honest. I skimmed it, went through the steps but no beans. But I am able to access my files on the xp machine now. I still can't print to the network printer though. 

I changed "security=user" to "security=my_login_name" do you think that will help?

when i try to access mshome from xp i get the error shown below:
```
Mshome is not accessable. You might not have permission to use this network 
resource. Contack the administrator of this server to find out if you have 
access permissions. 

The list of servers for this workgroup is not currently available.
```
I have administrator priviliges on the xp machine, I have tried all the suggestions, answers, etc. that i have come across but nothing seems to work.

---

### Post by Iowan on 2008-02-13
> **tad1073 said:**
> I changed "security=user" to "security=my_login_name" do you think that will help? Probably not - AFAIK, the only valid **security=** options are **share, user, server** or **domain.**

Have you set up a user account on Samba? (Check **man smbpasswd** - the **-a** option in particular.)
BTW, to which machine is the printer connected?

---

### Post by tad1073 on 2008-02-13
> Probably not - AFAIK, the only valid security= options are share, user, server or domain.

Have you set up a user account on Samba?

Yes, I have, I think??? Is there something I can do to check if I have?

---

### Post by Iowan on 2008-02-13
You could try **security=share**... but that's very insecure.  _**IF**_ you try it (to see if the shares appear on your XP box), plan to change it back.

On a tangent...My server has a section:```
[homes]
   comment = Home Directories
   valid users = %S
   browseable = no
   writable = yes

```You might modify your **smb.conf** accordingly.  This should enable a share for your user.

---

### Post by tad1073 on 2008-02-13
I don't know if my issue is with windows xp or ubuntu. I think it is with ubuntu because I can ping ubuntu from xp.

---

### Post by dmizer on 2008-02-14
> **tad1073 said:**
> I don't know if my issue is with windows xp or ubuntu. I think it is with ubuntu because I can ping ubuntu from xp.

i don't believe your issue is with ubuntu, i think your issue is still with firewalls.  you can now access xp because you disabled your xp firewall.

> **tad1073 said:**
> [COLOR="Red"]iptables for ubuntu w/firestarter interface[/COLOR] and norton suite on xp home edition

since you have installed the firestarter interface, you also have a configured iptables script which is preventing access to your samba shares from xp.  you must either disable firestarter (closing it in the system tray is NOT disabling firestarter), or you must configure firestarter to allow external access to your samba shares.

it's been my experience that in order to actually disable firestarter, you must use the interface.  sometimes, that is not even enough.  there have been situations where the only solution to work was to completely uninstall firestarter.

> **tad1073 said:**
> Also, I have installed Network Magic that came with the router. It see's ubuntu, the files I shared on ubuntu and the files i shared on xp.

since you have a router (a firewall), your local network should be trusted.  iptables and an xp firewall are redundant and IMHO unnecessary.  at the very least, they are the root cause of your immediate problem.

certainly if you are running either computer in a DMZ or if you have completely disabled your hardware firewall, a local firewall will be necessary.  while i don't necessarily advocate removing security precautions, in this case it seems to be more than necessary for safe browsing, and internal network sharing.

---

### Post by tad1073 on 2008-02-14
> **dmizer said:**
> i don't believe your issue is with ubuntu, i think your issue is still with firewalls. you can now access xp because you disabled your xp firewall.
I have my firewall configured properly accepting samba and microsoft in and out plus connections to and from the host computer. I can access my files on the xp machine. I have xp firewall configured with the same rules more or less.

> **dmizer said:**
> since you have a router (a firewall), your local network should be trusted. iptables and an xp firewall are redundant and IMHO unnecessary. at the very least, they are the root cause of your immediate problem.

certainly if you are running either computer in a DMZ or if you have completely disabled your hardware firewall, a local firewall will be necessary. while i don't necessarily advocate removing security precautions, in this case it seems to be more than necessary for safe browsing, and internal network sharing.
I am not using the router firewall, rather I am using local firewalls. My mom gets a little ill when i start messing with "Her" computer.

---

### Post by tad1073 on 2008-02-14
> **Iowan said:**
> You could try **security=share**... but that's very insecure.  _**IF**_ you try it (to see if the shares appear on your XP box), plan to change it back.

On a tangent...My server has a section:```
[homes]
   comment = Home Directories
   valid users = %S
   browseable = no
   writable = yes

```You might modify your **smb.conf** accordingly.  This should enable a share for your user.

i changed my smb.conf to the example you have above. Now whem I try to access ubuntu from xp  get a new error message:

```
Mshome is not accessable. You might not have permission to use this network 
resource. Contack the administrator of this server to find out if you have 
access permissions. 

The network path was not found
```

---

### Post by dmizer on 2008-02-14
take a look at this post for detailed information on configuring firestarter:

[http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542)

if you've already done everything that post details, i apologize.

---

### Post by tad1073 on 2008-02-14
> **dmizer said:**
> take a look at this post for detailed information on configuring firestarter:

[http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542)

if you've already done everything that post details, i apologize.

I did this:
```

# Allow response traffic
$IPT -A INBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -p udp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

```
this:
```

hosts:          files dns mdns wins

```
and I just saw this:
```

# Allow response traffic
$IPT -A INBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow response to netbios name broadcasts from the local network.
$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT

```
and will adjust accordingly.

---

### Post by tad1073 on 2008-02-14
i keep getting the error that is shown below.

```
Mshome is not accessable. You might not have permission to use this network 
resource. Contack the administrator of this server to find out if you have 
access permissions. 

The network path was not found.
```

---

### Post by dmizer on 2008-02-14
okay ... you've done some changes to your smb.conf file, please repost it.

as an asside, you should use cups for printer sharing instead of samba.  i've yet to figure out how to share a printer to windows through samba, but cups has never been a problem.  printer sharing can be found in the printer applet in the administration menu.

---

### Post by tad1073 on 2008-02-14
I can't post or upload the file.

---

### Post by dmizer on 2008-02-15
you posted it in the very first post of this thread.  is there something preventing you from doing so again?

---

### Post by tad1073 on 2008-02-15
guess there were too many people on the site causing congestion

```
[global]
        netbios = computer
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        guest account = thomas
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = bcast host lmhosts wins
        socket options = IPTOS_LOWDELAY TCP_NODELAY
        printcap name = cups
        domain master = No
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        printing = cups
        print command = 
        lpq command = %p
        lprm command = 

[homes]
        comment = Home Directories
        path = %S
        valid users = thomas
        read only = No
        create mask = 0700
        directory mask = 0700

[printers]
        comment = All Printers
        path = /var/spool/samba
        read only = No
        create mask = 0700
        guest ok = Yes
        printable = Yes
        use client driver = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /usr/share/cups/drivers
        write list = root, thomas
        guest ok = Yes

[home]
        path = /home
        guest ok = Yes

[mnt]
        path = /mnt
        guest ok = Yes

```

---

### Post by Iowan on 2008-02-15
> **tad1073 said:**
> 
```
...Mshome is not accessable. 
```Kinda looks like you're trying to access the workgroup as a machine.

---

### Post by tad1073 on 2008-02-15
> **Iowan said:**
> Kinda looks like you're trying to access the workgroup as a machine.

What do you mean by that?

---

### Post by Iowan on 2008-02-15
If I tried to connect to a machine named **Server** that was "locked down", I'd expect to see that error.  Ordinarily, I wouldn't expect to see that kind of message when trying to browse a workgroup.  Maybe it's normal, and just looks odd to me.

---

### Post by tad1073 on 2008-02-15
the path  take to get that error is ">My Network Places>Entire Network>Windows Network>Mshome" and that s is when the error occurs. When clicing that icon I expect to see my computer there, but instead, i get the error messege.

---

### Post by dmizer on 2008-02-15
okay, just for testing purposes (we can fine tune it later), let's try something i know works.  this is all done in the terminal, but all you need to do is copy and paste the commands.

first, double check to make sure that you have samba server installed:
```
sudo aptitude install samba
```

make a backup of your current configuration file (so you can return to it later if desired)
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf-backup
```

prepare a new, blank smb.conf file:
```
sudo touch /etc/samba/smb.conf
```

prepare a directory for your share, and make sure permissions are set correctly for it (we can change this to your desired directory later):
```
sudo mkdir /media/share
sudo chmod 777 /media/share
```

edit your samba server config file with a commandline text editor:
```
sudo nano /etc/samba/smb.conf
```

copy the following samba server config and past it into the terminal:
```
[global]
    netbios name = computer
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[MyFiles]
    path = /media/share/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
    force group = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
```
**be sure to change "UBUNTU-USERNAME" (marked in red text) with your actual ubuntu login id.**

after you've edited UBUNTU-USERNAME;
[LIST]
[*]save the configuration by hitting <ctrl>+'X'
[*]type the letter 'Y' to save the modified buffer
[*]and hit <enter> to write the file.
[/LIST]
make sure your ubuntu username is added to the samba usergroup:
```
sudo smbpasswd -L -a [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
sudo smbpasswd -L -e [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
```
**again, make sure to replace "UBUNTU_USERNAME" with your actual ubuntu login id.**

restart samba:
```
sudo /etc/init.d/samba restart
```

see if you can browse to the share then.

---

### Post by tad1073 on 2008-02-15
I still can't access ubuntu from xp.

---

### Post by dmizer on 2008-02-16
okay ... any errors?  same error?

in windows:
try right clicking on "my computer", select "map network drive"
pick a drive letter (really doesn't matter which one)
in the "folder" box, type \\computer\MyFiles

click ok, and open "my computer".  look for your new mapped drive.  see if you can save a file to it or something.

if it's still not working, there's something blocking samba between your xp machine and your ubuntu machine.

---

### Post by tad1073 on 2008-02-16
My Network Places>Entire Network>Microsoft Windows Network>Mshome
```

Mshome is not accessable. You might not have permission to use this network 
resource. Contack the administrator of this server to find out if you have 
access permissions. 

The list of servers for this workgroup is not currently available.

```

```

Could not map network drive, no nerwork found

```
i even disabled iptables for a minute and checked to see if I could access ubuntu from xp but no go.
I can ping my ip address from xp though.

---

### Post by tad1073 on 2008-02-16
bump...

---

### Post by dmizer on 2008-02-16
okay ... double check to make sure that you have "file and printer sharing" enabled in XP.

control panel > network connections > 
right click on "local area connection" and select "properties"
make sure there is a checkmark next to "file and printer sharing for microsoft networks"

from ubuntu, please post the output of this command:
```
smbtree
```

---

### Post by tad1073 on 2008-02-16
there is nothing there.

---

### Post by dmizer on 2008-02-17
do you see any errors if you perform the following command:
```
sudo /etc/init.d/samba restart
```

if not, the problem is very likely related to firestarter.

---

### Post by tad1073 on 2008-02-18
I have to decided to use widblows for now. i really don't have time to waste trying to figure this stuff out and try to get it working . Thanks for all your help.

P.S. If i had larger hd's I would dual boot but considering the hd's are only 9.1gb's each kind of makes it difficult. I added the cost of 4x512mb ram, a new video card, a sound card, a new monitor and new hd's which totals about $800 and figured it would be easier ust to buy a new computer.

Again, thanks for all your help.

---

### Post by dmizer on 2008-02-18
no problem.  better luck next time.  if you're still even mildy interested, i suggest you try completely uninstalling firestarter as a final test before completely ditching ubuntu.

---

