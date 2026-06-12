---
title: "Networking"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by bharath-v on 2009-04-01
Hello guys,
            I have 4 systems and have installed ubuntu server on all of them. I have to make these 4 systems networked to use printer and my system to act as server to them.I m totally new so please give me a step by step tutorial.please


thanks you all

---

### Post by albandy on 2009-04-01
Have you ever used linux? I need to know it to explain it according to your knowledge

---

### Post by superprash2003 on 2009-04-01
why would you install ubuntu server on all 4 machines?

---

### Post by Iowan on 2009-04-01
Depending on which version you installed, [this]("https://help.ubuntu.com/8.04/serverguide/C/index.html") help page may be useful.  Did you install LAMP server, or any other servers (FTP, DHCP, DNS, etc.)?

---

### Post by rhcm123 on 2009-04-01
> **bharath-v said:**
>  4 systems networked to use printer

Which server is the printer attached to?

---

### Post by egalvan on 2009-04-01
> **superprash2003 said:**
> why would you install ubuntu server on all 4 machines?

Why not?

The server version is much smaller, uses less resources.

The server kernel has some differences over the standard (desktop) version.

One doesn't need to run server apps to run a server.

It's more a name, not so much a job description :)

I run  a server core on a couple of my work-a-day machines.
With Kubuntu installed.
It lets me access more than 4G RAM with a 32-bit install...

---

### Post by bharath-v on 2009-04-02
thank u guys


My system is connected to the printer.And the other 3 will be acting as clients.

I have installed LAMP and i dono how to make others send the doc to be printed from my system. Please help

---

### Post by bharath-v on 2009-04-02
Also enlighten me on ebox and how to use.




thank u

---

### Post by rhcm123 on 2009-04-02
You will probably need samba and cups to share your printer. (there's a gui way to do this, but ima command line kinda guy).

PROTIP: SET YOUR PC TO HAVE A STATIC IP. OTHERWISE YOU WILL HAVE TROUBLE MAINTAINING CONSTANT CONNECTION BETWEEEN THE SERVERS AND THE CLIENT.

IF YOU WANT TO USE THE GUI:
Go to System -> Administration -> Printing. Hit your printer, select "policies", then set share. Add any other options you want. Done.

EDIT: As far as i know, there is no samba gui. Samba is the windows networking file server/print server for linux.

IF YOU WANT TO USE THE COMMAND LINE: (EDITED)
1. Download the tar i've attached, extract it to your desktop.
2. sudo apt-get install samba cups
3. sudo mkdir /printer
4. sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
5. sudo cp /etc/cups/cupsd.conf /etc/cups/cupsd.conf.backup
6. sudo cp /home/!!YOURUSERNAME!!/Desktop/configs/smb.conf /etc/samba/smb.conf
7. sudo cp /home/!!YOURUSERNAME!!/Desktop/configs/cupsd.conf /etc/cups/cupsd.conf
8. sudo /etc/init.d/samba restart
9. sudo /etc/init.d/cupsys restart

This will get a very basic and insecure system working. **USE THESE FILES AT YOUR OWN RISK!!** Post back if you have a problem here.

---

### Post by rhcm123 on 2009-04-02
> **egalvan said:**
> Why not?

The server version is much smaller, uses less resources.

The server kernel has some differences over the standard (desktop) version.

One doesn't need to run server apps to run a server.

It's more a name, not so much a job description :)

I run  a server core on a couple of my work-a-day machines.
With Kubuntu installed.
It lets me access more than 4G RAM with a 32-bit install...

Not really, but ok... the server kernel uses the same ammount as the desktop kernel - just without the gui. add the gui and they use about the same

---

### Post by albandy on 2009-04-03
> **rhcm123 said:**
> Not really, but ok... the server kernel uses the same ammount as the desktop kernel - just without the gui. add the gui and they use about the same

From ubuntu.com Ubuntu Server kernel specs:

Kernels

    * **Default 2.6.24-server Tickless, No Preemption, Deadline I/O, PAE, 100Hz**
    * JeOS 2.6.24-virtual Stripped down kernel for Virtualization

---

### Post by bharath-v on 2009-04-17
Thank u rhcm123 also i want to make this as a centralized server.
Not only use for printing but store files in this system and also have a database here which can be accessed from the other systems.
Please reply as soon as possible. thank u once again

---

### Post by Iowan on 2009-04-17
> **bharath-v said:**
> Also enlighten me on ebox and how to use.[Here]("https://help.ubuntu.com/community/eBox") is a starting point...

---

### Post by rhcm123 on 2009-04-17
> **bharath-v said:**
> Thank u rhcm123 also i want to make this as a centralized server.
Not only use for printing but store files in this system and also have a database here which can be accessed from the other systems.
Please reply as soon as possible. thank u once again

file server youll need samba, see the config file i included. basically that will share the directories /share, /media/backup, and your cdrom drive, as well as all printers.

To serve a database system, you would need to go with somthing like mysql. genterating data tables is complex - i would find a gui for this

---

### Post by bharath-v on 2009-04-19
Thanks for reply guys.

hey what r the steps i need to follow on client system for file server or printer.

---

### Post by bharath-v on 2009-04-20
hey common guys i need a solution

i dont know anything abt client servers,I want to know all the steps to setup the req software and be able to use from the client machines. I dono how to config or wat command to use to send files from client.
So please give a good tutorial to learn everything.please and thank u

---

### Post by mlentink on 2009-04-20
PLease be aware that these forums are for mutual support of users. There are no paid support engineers here. So you might want to consider practising a b it of patience.

Secondly, there's a wealth of information in the wiki's and on help.ubuntu.com. Why not check that out first and come back if you have a specific question? That's what almost all of us do...

---

### Post by nandemonai on 2009-04-20
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Grab a coffee and start reading. ;)

---

### Post by mlentink on 2009-04-20
> **nandemonai said:**
> [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Grab a coffee and start reading. ;)

Invaluable. You might want to read [this]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") as well, but you'll learn less

---

### Post by rhcm123 on 2009-04-20
Firstly, nandemonai said it best - read the guides, you will learn quite a bit about server administration (I lived off these for a good 4 weeks getting my home system setup, and rapidly educating myself in the process :shock: -yeah, right.)
> **nandemonai said:**
> [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Grab a coffee and start reading. ;)

**HOWEVER**
If you are really in a rush to get this all out, then i will help you out. You said you needed help with clients, well assuming you followed my quicky guide [here]("http://ubuntuforums.org/showthread.php?p=7092363") then do the following on your clients: 

**USE THIS AT YOUR OWN RISK**
1. sudo apt-get install smbfs
2. sudo nano /root/.smb1
   In that file place the following (these are your SAMBA users/passwords):
```
username=**YOUR-USER-NAME**
password=**YOUR-CLEARTEXT-PASSWORD**
```
3. sudo chmod 400 /root/.smb1
4. sudo mkdir /media/share
5. sudo nano /etc/fstab
   Add the following line at the bottom:
```
//YOUR-SERVER-IP/share /media/share smbfs credentials=/root/.smb1,umask=000,user,auto   0 0
```
6. Run this guy to prevent shutdown stalls:
```
sudo ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
&& ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh
```

Now, what all that is going to do is get the samba file system for the client, make a permissions file so that your password is not stored in the globally-readable /etc/fstab but the root-only /root/.smb1 (this has the detriment of requiring root to mount the share).

After that it chmods it 400 to make sure only root can read it, makes the mount point /media/share, gives fstab the info it needs to mount the share, and adds a sym-link to runlevels 0 & 6 to prevent [shutdown stalling]("http://ubuntuforums.org/showthread.php?t=1128729"). 

Note that this will only work if you followed my previous guide to the letter and kept your shared directory named [share] in smb.conf.

EDIT:
Whoops, forgot about your printers. This is going to be a bit more complex.
I hope you have the GUI on your server, cause I *really* don't want to do this manually. It's a pain.
Go to System -> Administration -> Printing on your server. Install your local printer (the one attached to your PC as usual. Then "Server Settings", and check "publish shared printers" and "allow users to cancel any job, not just their own".

Hit your printer and check "shared". After that, go to the rest of your clients and setup using their built in GUI's, by checking the box "show printers shared by other systems". Most ubuntu machines will have no trouble spotting the IPP signal from the server machine, and the printer will pop up in the main menu. Make it the default, then exit.

---

### Post by bharath-v on 2009-04-21
Thanks again rhcm123 

How to check whether its working or not and y does ur config file have username USSR should i change anything in that.

And its a bit urgent man please give me more details and i have tried the server guide and help ubuntu. There the NFS i tried but at end gives an mount error.

I have connected my printer, but it says printer not connected What should i do.

Thank u all for replying

---

### Post by bharath-v on 2009-04-21
hey i used openssh.

From a client system places->connect to server. Then when i enter the server, port no,required user. then it asks for password. It mounted my network drive but opens the root files.how to open only the user files and stop client from accessing the root and other user files.

Waiting for the reply

Thank u all

---

### Post by bharath-v on 2009-04-21
Hey rhcm123 

I have followed ur steps. but still the print option in the client system is not detected. 
It detects the printer correctly but when i give a file for print. It asks to select pdf or select the printer,When i select the printer the print option is not active to be clicked. What might be the problem. And i cannot give the test print also, coz it is also not activated.

---

### Post by rhcm123 on 2009-04-21
> **bharath-v said:**
> Thanks again rhcm123 

How to check whether its working or not and y does ur config file have username USSR should i change anything in that.

And its a bit urgent man please give me more details and i have tried the server guide and help ubuntu. There the NFS i tried but at end gives an mount error.

I have connected my printer, but it says printer not connected What should i do.

Thank u all for replying

its working if, when you run mount -a, the drive appears on your desktop. sorry, but yes you need to change your usernames to your own (there is no such thing as a completley cut & paste guide). :D

you are having a mount error? try this command on your server, then try and mount again. **IF YOU FOLLOWED MY GUIDE YOU MUST MOUNT AS ROOT!! (sudo mount -a)**:```
sudo smbpasswd -a
``` (enter the password you want to use to connect to samba shares.


> **bharath-v said:**
> hey i used openssh.

From a client system places->connect to server. Then when i enter the server, port no,required user. then it asks for password. It mounted my network drive but opens the root files.how to open only the user files and stop client from accessing the root and other user files.

Waiting for the reply

Thank u all
openssh is god. :). Are you setting up a samba share or an sshfs share? You've gotten me confuzzled. If you are setting up samba, select "windows share" from da list, the info, then hit connect. If you are opening up / then you probably did not create the directory /share. run sudo mkdir /share on the server to fix this.

Also, please note is forum policy to only bump posts if they have been abandoned for 24 hours. I'm not on all the time, typically only between 1800-2200.

> **bharath-v said:**
> Hey rhcm123 

I have followed ur steps. but still the print option in the client system is not detected. 
It detects the printer correctly but when i give a file for print. It asks to select pdf or select the printer,When i select the printer the print option is not active to be clicked. What might be the problem. And i cannot give the test print also, coz it is also not activated.

Would you mind posting a screenshot? (hit printscreen on your keyboard to do so).

---

### Post by bharath-v on 2009-04-22
Hey i corrected the printer problem ipp://'servername/ip-address':631/printers/hp

the problem was it detects server name,but when i manually tried with ipaddress it worked fine.

but the samba or file share i m not getting it.

I tried open ssh. i.e. from places->connect to server. it connects but it opens the root of the server which is not safe. i want the client system to open only the folder and its contents that i specify.
please elloborate on this and help me as to where i m going wrong  

Here are the screenshots


this is for the samba, when i tried mount

Screenshot1.png

---

### Post by rhcm123 on 2009-04-22
> **bharath-v said:**
> Hey i corrected the printer problem ipp://'servername/ip-address':631/printers/hp

the problem was it detects server name,but when i manually tried with ipaddress it worked fine.

but the samba or file share i m not getting it.

I tried open ssh. i.e. from places->connect to server. it connects but it opens the root of the server which is not safe. i want the client system to open only the folder and its contents that i specify.
please elloborate on this and help me as to where i m going wrong  

Here are the screenshots


this is for the samba, when i tried mount

Screenshot1.png

the IPP string isn't properly formatted but i don't care - it works.

ok, firstly try mounting with sudo - the way your share is setup you must mount as root. 

this is the properformatting you need to connect to a server with the connect to server app on a SFTP supporting system (see attached pic)

---

### Post by bharath-v on 2009-04-23
I m doing the same thing. but i want people using that system to use that as default and not change it to root or home folders. I want them to only access a folder of a particular account.
Thank u man

---

### Post by rhcm123 on 2009-04-23
> **bharath-v said:**
> I m doing the same thing. but i want people using that system to use that as default and not change it to root or home folders. I want them to only access a folder of a particular account.
Thank u man

this should work for the samba configs i gave you, just change the directory from /share to whatever you want, and then restart samba, then you should have a working system

---

### Post by bharath-v on 2009-04-29
i have attached the screen shots which i m entering and getting the error. Please look and tell me how to rectify it

I also want the other systems to be able to detect all the system connected on the network and interact with each other. 

And please tell me on both server and client machines.And  also the windows share 

Thank u

---

### Post by rhcm123 on 2009-04-29
> **bharath-v said:**
> i have attached the screen shots which i m entering and getting the error. Please look and tell me how to rectify it

I also want the other systems to be able to detect all the system connected on the network and interact with each other. 

And please tell me on both server and client machines.And  also the windows share 

Thank u

under the "share" option, you should put in whatever you named your share. That is, if you named your share [share] in smb.conf, put share in the box. leave the "folder" directive blank.

Having all the systems on the network talk to each other is kind of difficult. What are you trying to accomplish (file/folder sharing, desktop sharing, etc)?

---

### Post by bharath-v on 2009-04-29
i m asking whether its possible the same way as in windows i.e all the machines connected on the network are visible in network places as a drive and and files can be copied from that system to the one in the network.

One more thing my printer is HP Officejet 5600 series, In print the 2 sided (back to back) print is disabled.can u tell me how to enable it or any driver i need to rectify it.

---

### Post by rhcm123 on 2009-04-30
> **bharath-v said:**
> i m asking whether its possible the same way as in windows i.e all the machines connected on the network are visible in network places as a drive and and files can be copied from that system to the one in the network.

One more thing my printer is HP Officejet 5600 series, In print the 2 sided (back to back) print is disabled.can u tell me how to enable it or any driver i need to rectify it.

if you want to do that and they all have gui's, then right click the folder you want to share, then hit properties, sharing, etc. If not, use the samba directions i gave you to setup a share for the folder you want.

I don't know how to fix the printing issue - it may be drivers or lack of linux support.

---

### Post by bharath-v on 2009-04-30
i have followed ur steps man but still not able to get it can u please explain me once again to setup in GUI using the connect to serer.
I have given a folder share options but its not visible in other systems.
please help and sorry for asking u again and again.

ANd regarding the printer can u suggest any solution.

thanks for the reply man

---

### Post by rhcm123 on 2009-04-30
> **bharath-v said:**
> i have followed ur steps man but still not able to get it can u please explain me once again to setup in GUI using the connect to serer.
I have given a folder share options but its not visible in other systems.
please help and sorry for asking u again and again.

ANd regarding the printer can u suggest any solution.

thanks for the reply man

oh, sorry, i forgot to say. the gui isnt perfect - you will have to set the workgroup - go to the terminal and edit (use sudo) /etc/samba/smb.conf, find the "Workgroup" option, and set all your servers to the same, then restart samba with sudo /etc/init.d/samba restart

as for your printer you may want to google your model with somthing like "double sided printing ubuntu". i have no soultions in my mind.

---

### Post by bharath-v on 2009-04-30
i did it but he result is same(i.e. nothing)

Let me start from begining what i want:-
1. I have 5 systems, one server(mine)(ubuntu), other 4 clients(ubuntu).
2. Be able to print from all the client systems ,printer is connected to my system (working except for double sided printing).
3. The client system should be able see the systems connected in network.
And be able to share files between them also.
4. A storage place for client to store the file on server(my system).
5. They should be able to access programs installed on server.

Now these are the things i needed man. I have installed samba and using ur config file. Can u please elaborate on what i have to do get this working and i tried reading some tutorials man but its of no use coz i need to know how to use the samba and other stuff to make the above things work.

Thank u rhcm123 for taking time to answer all my queries. thank u very much

---

### Post by rhcm123 on 2009-04-30
> **bharath-v said:**
> i did it but he result is same(i.e. nothing)

Let me start from begining what i want:-
1. I have 5 systems, one server(mine)(ubuntu), other 4 clients(ubuntu).
2. Be able to print from all the client systems ,printer is connected to my system (working except for double sided printing).
3. The client system should be able see the systems connected in network.
And be able to share files between them also.
4. A storage place for client to store the file on server(my system).
5. They should be able to access programs installed on server.

Now these are the things i needed man. I have installed samba and using ur config file. Can u please elaborate on what i have to do get this working and i tried reading some tutorials man but its of no use coz i need to know how to use the samba and other stuff to make the above things work.

Thank u rhcm123 for taking time to answer all my queries. thank u very much

For your points:
1. Very good :D
2. Sorry, but i don't know how to help with dbl sided.
3. If the GUI isn't working, follow the SAMBA guide i provided earlier in this thread for each client, making sure to modify it for the directory you want to share.
4. Is samba working on your system?
5. If they (the clients) install programs on the server (that is, if they are windows systems and you map the drive as x:, the program gets installed onto x: ). Most ubuntu programs are so small it's just more effective to install them all onto the local system.

On my samba example i gave you somthing like this, correct:
```
[share]
        browseable = yes
        read only = No
        writeable = yes
        path = /share
        create mask = 0700
        comment = Main share directory on USSR-MOSCOW.
        directory mask = 0700
        valid users = ussr,elisabeth,fred,carol,root,nobody

```

Change the following values to whatever you want:
[share] - the name of the share; this is what it's called when you connect. (e.g. if you connect in /etc/fstab, and your share is called "Public" you would use //IP.ADDRESS/Public <options>)
browseable - if you want people to be able to browse the files. Leave at yes.
read only - only set to yes if you want people to not be able to modify the files on the share.
writeable - essentially the same thing as read only
path - very important, the directory you want to share
create mask - don't worry about this, leave at 0700
comment - the label for this share, call this whatever you want
directory mask - don't worry about this either
valid users - the users allowed to login.

Now, after you have modified your configuration file to how you want it, restart samba with:
```
sudo /etc/init.d/samba restart
```

Then, you must set the passwords for your users (just enter your normal login password for this, and remember you must re-run it if you ever change your login password:
```
sudo smbpasswd -a <username>
```

---

### Post by egalvan on 2009-05-01
> **bharath-v said:**
> i did it but he result is same(i.e. nothing)
:-
1. ...**5 systems, one server(ubuntu),  4 clients(ubuntu)**.
2. ...print from all the client systems ...
3. ...client system should ...see the systems connected in network.
And ..share files between them.
4. ...client to store the file on server(my system).
5. ...access programs installed on server.

Now these are the things i needed. I have installed samba ...



(I'm just getting to know networking under Linux...)

The entire network (five machines) is Linux, no MS Windows;
would nfs be a better choice for this,
rather than Samba?

Pros and cons of Samba vice nfs?

My (clearly limited) understanding is:
nfs is simpler, designed for *nix-only networks
Samba is more complicated, designed for a mixed environment (*nix & Windows)

Thanks  for any  ideas and input.

ErnestG

---

### Post by rhcm123 on 2009-05-01
> **egalvan said:**
> (I'm just getting to know networking under Linux...)

The entire network (five machines) is Linux, no MS Windows;
would nfs be a better choice for this,
rather than Samba?

Pros and cons of Samba vice nfs?

My (clearly limited) understanding is:
nfs is simpler, designed for *nix-only networks
Samba is more complicated, designed for a mixed environment (*nix & Windows)

Thanks  for any  ideas and input.

ErnestG
Heck, i use samba for all my linux clients, and i've had no problems with setup - it even transfers UID/GID information and other such traditionally Linux info automatically. It actually works better with Linux then Windows, as the windows computers are always complaining about wrong passwords or failing to mount the shares at boot.

Samba and NFS are not really that different, and they are not very different (not so that the average user would notice, anyways), but i prefer samba for cross compatibility with other platforms. I tried NFS and found it does exactly the same thing that samba does - share a network drive, but i found it a little painful to configure (lotta config files). And samba is becoming the default nowadays, as it works for both Platforms.

Essentially, it goes like this:
NFS - older protocol for linux file sharing.
Samba - front end for CIFS (common internet file system), that also supports printer sharing, and provides support for NetBIOS and other windows protocols.

As you can see, i prefer samba :D

---

