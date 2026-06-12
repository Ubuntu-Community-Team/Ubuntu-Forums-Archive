---
title: "Installing Samba"
date: 2022-02-05
forum: Networking &amp; Wireless
---

### Post by torbentf on 2022-02-05
Hi,
I am trying to install samba on Ubuntu 20.04 on a workstation using the instructions on:

[https://ubuntu.com/tutorials/install-and-configure-samba#4-setting-up-user-accounts-and-connecting-to-share](https://ubuntu.com/tutorials/install-and-configure-samba#4-setting-up-user-accounts-and-connecting-to-share)

They are supposed to apply to Ubuntu 16.04 and a server. Does it matter?

I got to the point where:

"On Windows, open up File Manager and edit the file path to:

\\ip-address\sambashare

Note: ip-address is the Samba server IP address and sambashare is the name of the share.

You’ll be prompted for your credentials. Enter them to connect!"

I have opened Windows File Manager and the only place where I can see a file path to be filled in is where it says "Network>" and I have filled in with 192.168.110.19 (which I think is the address of my Linux machine)and pressed Enter. Then nothing happens.

Can anyone tell me what went wrong here?  
Best regards
torben

---

### Post by TheFu on 2022-02-05
Samba has changed drastically since 20.04 due to changes both in samba and the most common clients (Win10) altering their default settings.  Also, MSFT has changed how network services are located.  "Browsing the network" doesn't work.  Though the guide you followed is fine for everything except where it suggested sharing files. Don't share files under any user's HOME.

If you don't have the correct IP address for the server, nothing will work.  Servers should always have static IPs that are known.

For troubleshooting samba, run **testparm** on the samba server and post the results here. Someone should see the issues.  The entire config should show up. If it doesn't, then I think the setup is incorrect. There are other ways that claim to work for setting up samba, but they seem to just cause problems.  

Making any CIFS/Samba share underneath a user's HOME directory is asking for problems.  Put shared files elsewhere OR use the [homes] samba option instead. That will share the HOME directories for each uesrid once the **smbpasswd -a** command is run for each userid.

The format of the [homes] is this:
```
[homes]
        comment = Home Directories
        create mask = 0644
        read only = No
        valid users = %S
        wide links = Yes
```
Add that to the bottom of the smb.conf file, restart samba.

---

### Post by Morbius1 on 2022-02-05
[ATTACH=CONFIG]289968[/ATTACH]
Is that what you did?

And please tell us how you are using this samba share.

Is it to be used as a central samba server for all other systems to access where a [homes] share may or may not make sense? Or is it for you to share one folder with others on the local network.

---

### Post by torbentf on 2022-02-06
Hi TheFu,
Thank you for your answer. It has apparently advanced me:

Torben@torben-Aspire-E5-773G:/etc/samba$ testparm
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed
WARNING: The 'netbios name' is too long (max. 15 chars).

Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
    bind interfaces only = Yes
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    workgroup = SAMBATF
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[homes]
    comment = Home Directories
    create mask = 0644
    read only = No
    valid users = %S
    wide links = Yes
torben@torben-Aspire-E5-773G:/etc/samba$ 

Here is the answer I get from Windows:

"You cant get access to \\192.168.110.19\sambashare"

and when I press diagnostics I get:

"check that sambashare is spelled correctly and try again"

There seems to be name confusion here. "samashare" is a leftover from an earlier attempt - even though that I have uninstalled correctly Samba. The same goes for "workgroup = SAMBATF". 
I dont see 'netbios name' anywhere.

I dont really understand what is going on here, but I have only 1 user (torben) and I have input a passwd for him (me). I think I need to have an overview of Samba in order to understand.
best regards
torben

Hi TheFu,<br>Thank you for your answer. It has apparently advanced me:<br><br>Torben@torben-Aspire-E5-773G:/etc/samba$ testparm<br>Load smb config files from /etc/samba/smb.conf<br>Loaded services file OK.<br>Weak crypto is allowed<br>WARNING: The 'netbios name' is too long (max. 15 chars).<br><br>Server role: ROLE_STANDALONE<br><br>Press enter to see a dump of your service definitions<br><br># Global parameters<br>[global]<br>&nbsp;&nbsp; &nbsp;bind interfaces only = Yes<br>&nbsp;&nbsp; &nbsp;log file = /var/log/samba/log.%m<br>&nbsp;&nbsp; &nbsp;logging = file<br>&nbsp;&nbsp; &nbsp;map to guest = Bad User<br>&nbsp;&nbsp; &nbsp;max log size = 1000<br>&nbsp;&nbsp; &nbsp;obey pam restrictions = Yes<br>&nbsp;&nbsp; &nbsp;pam password change = Yes<br>&nbsp;&nbsp; &nbsp;panic action = /usr/share/samba/panic-action %d<br>&nbsp;&nbsp; &nbsp;passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .<br>&nbsp;&nbsp; &nbsp;passwd program = /usr/bin/passwd %u<br>&nbsp;&nbsp; &nbsp;server role = standalone server<br>&nbsp;&nbsp; &nbsp;server string = %h server (Samba, Ubuntu)<br>&nbsp;&nbsp; &nbsp;unix password sync = Yes<br>&nbsp;&nbsp; &nbsp;usershare allow guests = Yes<br>&nbsp;&nbsp; &nbsp;workgroup = SAMBATF<br>&nbsp;&nbsp; &nbsp;idmap config * : backend = tdb<br><br><br>[printers]<br>&nbsp;&nbsp; &nbsp;browseable = No<br>&nbsp;&nbsp; &nbsp;comment = All Printers<br>&nbsp;&nbsp; &nbsp;create mask = 0700<br>&nbsp;&nbsp; &nbsp;path = /var/spool/samba<br>&nbsp;&nbsp; &nbsp;printable = Yes<br><br><br>[print$]<br>&nbsp;&nbsp; &nbsp;comment = Printer Drivers<br>&nbsp;&nbsp; &nbsp;path = /var/lib/samba/printers<br><br><br>[homes]<br>&nbsp;&nbsp; &nbsp;comment = Home Directories<br>&nbsp;&nbsp; &nbsp;create mask = 0644<br>&nbsp;&nbsp; &nbsp;read only = No<br>&nbsp;&nbsp; &nbsp;valid users = %S<br>&nbsp;&nbsp; &nbsp;wide links = Yes<br>torben@torben-Aspire-E5-773G:/etc/samba$ <br><br>Here is the answer I get from Windows:<br><br>"You cant get access to \\192.168.110.19\sambashare"<br><br>and when I press diagnostics I get:<br><br>"check that sambashare is spelled correctly and try again"<br><br>There seems to be name confusion here. "samashare" is a leftover from an earlier attempt - even though that I have uninstalled correctly Samba. The same goes for "workgroup = SAMBATF". <br>I dont see 'netbios name' anywhere.<br><br>I dont really understand what is going on here, but I have only 1 user (torben) and I have input a passwd for him (me). I think I need to have an overview of Samba in order to understand.<br>best regards<br>torben<br><br>

Hi Morbius1,
As I told TheFu I need a description of Samba even to undestand your questions, but:

Yes, that is what I did.
and:
I want to access the files I have on a Windows machine on the same router (192.168.119.1) from my Linux machine which is the one I am using now.
best regards
torben

---

### Post by Morbius1 on 2022-02-06
[1] Please verify the ip address of your Ubuntu box by running this command:
```
hostname -I
```

[2] Turn off your Ubuntu firewall if you enabled it:
```
sudo ufw disable
```

[3] Can you ping that Ubuntu ip address from Windows - Open Command Prompt and run:
```
ping 192.168.110.???
```
*[COLOR="#0000FF"]Using the ip address you found in step [1][/COLOR]*

[4] Just in case you have done so do you get any output from this command:
```
net usershare info --long
```
If there is no output that is OK.

[5] Did you add torben to the samba password database:
```
sudo smbpasswd -a torben
```

[6] Please tell us which version of Windows you are using.

With ufw disabled and a possible change to the ip address try to access it again with one of these:

```
\\192.168.110.???
\\192.168.110.???\homes
\\192.168.110.???\torben
```

---

### Post by TheFu on 2022-02-06
```
\\192.168.110.19\sambashare
``` should probably be 
```
\\192.168.110.19\torben
``` now.
It needs to be the UNIX username.  The username you log into the Linux box using.  The [homes] section provides access to the HOME directories for usernames , if they have a smbpasswd added.

This all assumes the IP is correct. If the IP address is wrong, nothing will happen. It will try to connect to the wrong system.

---

### Post by foxsquirrel on 2022-02-06
Samba on windows will connect using hostname and share folder

just type \\hostname\yoursambasharename

If its visible to the win box it will autofill.

Hope you did not follow old information and activate smb1.0 on your winbox that is not a good thing to do.

Just so you are not chasing your tail, first try to ssh into the server from your win10 box.

from a cmd prompt

```
c:\xx\yy>**ssh username@hostname**
```


If that works its an issue configuring your sambashare. Take one step at a time.

---

### Post by torbentf on 2022-02-06
Hi Morbius1,
I can ping 192.168.110.19

torben@torben-Aspire-E5-773G:~$ net usershare info --long
torben@torben-Aspire-E5-773G:~$ 
No output

torben@torben-Aspire-E5-773G:~$ sudo smbpasswd -a torben
New SMB password:
Retype new SMB password:
torben@torben-Aspire-E5-773G:~$

Windows 8.1

\\192.168.110.19 I get a list of network addresses
\\192.168.110.19\homes I get a list of files in my home directory
\\192.168.110.19\torben I get a list of files in my home directory
best regards
torben

Hi Morbius1,
I can ping 192.168.110.19

torben@torben-Aspire-E5-773G:~$ net usershare info --long
torben@torben-Aspire-E5-773G:~$ 
No output

torben@torben-Aspire-E5-773G:~$ sudo smbpasswd -a torben
New SMB password:
Retype new SMB password:
torben@torben-Aspire-E5-773G:~$

Windows 8.1

\\192.168.110.19 I get a list of network addresses
\\192.168.110.19\homes I get a list of files in my home directory
\\192.168.110.19\torben I get a list of files in my home directory

best regards
torben

Hi TheFu,

\\192.168.110.19\homes I get a list of files in my home directory
\\192.168.110.19\torben I get a list of files in my home directory
best regards
torben

Hi Foxsquirrel,

torben@torben-Aspire-E5-773G:~$ ssh torben@192.168.110.19
The authenticity of host '192.168.110.19 (192.168.110.19)' can't be established.
ECDSA key fingerprint is SHA256:qATadk9NGsiAN6x/9iFwVr1OfjZbJFqCirtZ2n2KS58.
Are you sure you want to continue connecting (yes/no/[fingerprint])? y
Please type 'yes', 'no' or the fingerprint: yes
Warning: Permanently added '192.168.110.19' (ECDSA) to the list of known hosts.
torben@192.168.110.19's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.11.0-44-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

15 updates can be applied immediately.
To see these additional updates run: apt list --upgradable

Your Hardware Enablement Stack (HWE) is supported until April 2025.
*** System restart required ***
Last login: Sat Jun  5 12:23:42 2021 from 192.168.110.12
torben@torben-Aspire-E5-773G:~$ 

That qualifies as "it works" ?
best regards
torben

Hi everybody,
I seem to have lost some of the answers I thought I had sent. I will try to reconstruct.

Answer to TheFu:
\\192.168.110.19\homes I get a list of files in my home directory
\\192.168.110.19\torben I get a list of files in my home dire

Answer to oxsquirrel:
The first time I used "ssh" I got a comprehensive answer that indicated that it was not a sambashare issue. No I get the answer that "ssh" is not recognized.....
torben

---

### Post by TheFu on 2022-02-06
So ... everything is working.  IF so, please mark the thread as SOLVED, using the  _thread tools_ button near the top of the page.

It would be very helpful is everything typed and output in a terminal were wrapped in 'code-tags' when posting to these forums.
[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) a how-to.

---

### Post by foxsquirrel on 2022-02-06
It looks like you do have a valid connection to the server using ssh.

Your big issue is windows 8.1. Pretty sure that only supports smb1.0 and don't recall it having ssh installed, but you have connected.

If you must share with 8.1, not sure if I am correct on this, server and client might have to be set to run smb1.0, that is not good if you are connected to the internet.

---

### Post by torbentf on 2022-02-07
Hi
Can you help me with the overall picture?
- I have installed the **server** on my Linux machine? That means I can access my Linux files from the Windows machine? Can I also access my Windows files from my Linux machine?
- I have 2 users which both access my home-files from the windows machine: one comes from the addition of [homes] in the conf file, the other from my making a user (torben) with a password? What is the difference between them? 
- on my Linux machine I have a lot of files from my many attempts at installing Samba. Are they needed?
best regards
torben[FONT=comic sans ms][FONT=courier new][/FONT][/FONT]

---

### Post by Morbius1 on 2022-02-07
>  - I have installed the server on my Linux machine? That means I can access my Linux files from the Windows machine? Can I also access my Windows files from my Linux machine?
Yes, you just need to do so with a slightly different syntax.

Open Files ( Nautilus ) > Other Locations > Connect to Server and enter it's network path:
```
smb://windows-ip-address/windows-share-name
```
Like this example:
[ATTACH=CONFIG]289983[/ATTACH]

[COLOR="#0000FF"]Note: Ubuntu already comes with client side SMB access capability. One is in the Linux Kernel itself with mount.cifs and the other are samba client libraries installed beacuse of Nautilus.[/COLOR]

> I have 2 users which both access my home-files from the windows machine: one comes from the addition of [homes] in the conf file, the other from my making a user (torben) with a password? What is the difference between them? 

Are you talking about the smbpasswd command?

Share definitions ( like [homes] ) determines what can be shared on the server. In Windows a given user name and password is used both locally to log into the physical machine itself and also across the local network.

In Samba there are two: THe local Linux user name and password used to log into the physical Linux machine and another to access the samba share. The smbpasswd command tells samba that the local Linux user name should be added to the samba password database.

[COLOR="#0000FF"]Note: File this under .. My Opinion.

I've yet to find a use case for the traditional [homes] share in a typical home network. It allows userA on MachineA to access his home directory on the Linux machine. The presumption is that UserA has a home directory on the Linux box to access. If the intent is to share Folders on the Linux machine with many users on the network how does this help. Do you want userB on machineB to have access to your home directory - by using your user name and password?

Creating a share of a folder in your home directory better fits the situation where all of the machines on your local network are peers to each other. But again I do not know how you are using this samba share. If a [homes] share works for you ignore my opinion[/COLOR]

>  - on my Linux machine I have a lot of files from my many attempts at installing Samba. Are they needed?

That I cannot answer since I don't know what these files contain or why they were created.

---

### Post by torbentf on 2022-02-08
Hi Morbius1,
smb://windows-ip-address/windows-share-name:
-I have "windows-ip-address", but is "windows-share-name" something I make and how? I can't find it in the data I have "filled in" when setting up Samba.

Files:
I will rename them one by one and see if it has an effect

Setting up the system:
I have been through a lot, but I found this:

[https://computingforgeeks.com/install-and-configure-samba-server-share-on-ubuntu/](https://computingforgeeks.com/install-and-configure-samba-server-share-on-ubuntu/)

I followed it (the instructions are easy to follow) until I came to (near the end):

cat /.sambacreds

when I got the message: No permission.
I tried (i think) every way to set up /.sambacreds and at the same time give it the right permissions, but to no avail.
What can I do?
I have sent an email to "computingforgeegs"/Josphat Mutai, but maybe you can help
torben

---

### Post by Morbius1 on 2022-02-08
> smb://windows-ip-address/windows-share-name:
-I have "windows-ip-address", but is "windows-share-name" something I make and how? I can't find it in the data I have "filled in" when setting up Samba.
It is the name of the share you created on your Windows box.

Go to your Windows box, open Command Prompt, and run the following command:
```
net share
```

Ignore any "Share name" that ends in a $ and the Users share name. If you don't have any left you haven't created any share so there is nothing for the Linux client to access.

---

### Post by torbentf on 2022-02-08
Hi Morbius1,
Thank you!
torben

---

### Post by torbentf on 2022-02-09
Hi Morbius1,
I am sorry, but I am lost.
There was no shared drives left as a result of "net share". So I have to create one on Windows? Is there a simple way to do that?
torben

---

### Post by Morbius1 on 2022-02-10
This one looks more or less correct: [How to Create A Shared Folder on Windows 8/8.1]("http://https://www.isunshare.com/windows-8/create-a-shared-folder-on-windows-8-8.1.html")

I would start this in a more conventional way by creating a folder off the C drive rather than in one's user directory and sharing that. Something like C:\Shared for example

---

