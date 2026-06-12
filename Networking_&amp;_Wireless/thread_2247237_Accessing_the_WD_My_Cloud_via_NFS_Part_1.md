---
title: "Accessing the WD My Cloud via NFS Part 1"
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by Scooby-2 on 2014-10-06
The WD My Cloud supports NFS by default and the server itself needs only one configuration file to be changed in order to work correctly with Linux clients running NFS.


This how-to shows you what you need to do to add a user to the My Cloud, add a private share to the server and enable access to it via NFS. I have tried to make it as easy as possible for people who are not comfortable editing files from the command line by using commands which can (with one or two exceptions) be copied and pasted.

[I][COLOR=#ff0000]Edit 2 Nov 2014: This tutorial is applicable regardless of the client OS, be it Windows, OSX, Linux, Solaris, AIX, Haiku or whatever. However you need to know how to access the WD My Cloud UI (for which I recommend reading the WD documentation) and how to run a terminal session from that OS.

Edit 3 May 2015: Changed some of the quotes text to code, as spurious spaces are added by the forum software.[/COLOR][/I]

Please note that following these instructions will entail running commands as root on the WD My Cloud. Be warned that it is VERY easy to brick your server by running commands as root. I accept no responsibility for anyone who manages to brick their system(s) following this guide.


1. If the user you want to use has already been defined, skip to step 3. To add a new user to the server use the the UI. After logging in, click Users (1 in the screen print), then the Add User button (2):


[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/1_zpsa7b22976.jpg[/IMG]

2. In the Add User box, enter the desired user name. I suggest using the same user name on the Linux system that you want to be able to connect to the server. This is the only required field, the others may be left blank. However, for security, you may wish to assign a password (this would be used if you were to connect using SMB). Type in the required user ID - in my example I am adding a user called janm. Click the Save button.

[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/2_zps7eb18d62.jpg[/IMG]

3. If the share you want to use already exists, skip to step 5. Otherwise click on Shares (3 in the screen print below) the Add Folder button (4).

[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/3_zps00aaf77b.jpg[/IMG]

4. Add the folder name that you wish the user to see when they look for their private folder in File Manager. This is the only required field. Click Save.

[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/4_zps2546c234.jpg[/IMG]

5. Turn off Public Access and enable full access for the new user as shown below.

[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/5_zps47c742f6.jpg[/IMG]

6. Turn on SSH by clicking on Settings (5), Network (6) and then SSH (7). Set it to on (if it isn't already).

[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/6_zps89338c08.jpg[/IMG]

7. To log in to the server via SSH, from the client open a terminal window and type
```
ssh root@{IP_OF_YOUR_SERVER}
```If you see something like this: > The authenticity of host 'nas (xxx.xxx.xxx.xxx)' can't be established.RSA key fingerprint is 12:34:56:78:90:AB:CD:EF:00:11:22:33:44:55:66:77.
Are you sure you want to continue connecting (yes/no)? Answer yes. You are getting this message because it the first time you are connecting via SSH. You should then see > Warning: Permanently added 'nas,xxx.xxx.xxx.xxx' (RSA) to the list of known hosts. and you will be prompted for the root password of the NAS server. Type your root password, or if you haven't ever changed it, type welc0me. If you are logged on using the default password CHANGE IT NOW by typing
```
passwd

```and enter a new one.

8. We now need to modify the file responsible for managing the exports on the server. There are two ways to do this - method one is best for inexperienced users, where the file is created on the client using your favourite text editor. Method two is fine if you are comfortable running commands as root on the server (see warning above).

Method 1. Log in to the server and run the following commands to back up and write protect the original file:
```
cd /etc
```
```
cp exports exports.orig
```
This copies your original file in case you mess up and need to restore it.
If you are asked if you want to overwrite exports.orig answer no. It probably means you are running through this for the second time and answering yes will overwrite your original file. Seek advice...
```
chmod 400 exports.orig
```
This command makes the copy read-only, so you will get the prompted before it will be overwritten (see above)/

On your Linux client, open your favourite text editor and create a file named exports with the following text:


```
# Use nobody user (uid 65534) for nfs guest.  This is restricted from private
# shares by ACLs.
#
/nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
/nfs/janm *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
[COLOR=#ff0000]#[/COLOR] [COLOR=#ff0000]Replace janm with the user name you created in step 2.[/COLOR]
```
Save the file in your home directory.
In the terminal window, log out of the server so you are working on your client and type the following:
> cd
and then
> rcp exports [email]root@[COLOR=#ff0000]xxx.xxx.xxx.xxx[/email][/COLOR]:/etc/
[COLOR=#ff0000](#[/COLOR] [COLOR=#ff0000]Replace xxx.xxx.xxx.xxx with your NAS server's IP address)[/COLOR]
The rcp command stands for remote copy, and allows files to be transferred over the network via SSH.

Go to step 9.

Method 2. Log in to the NAS server via SSH. Copy and paste  the following lines (paste is available from the menu in terminal) ONE AT A TIME . 
```
cd /etc
```
```
cp exports exports.orig
```
If you are asked if you want to overwrite exports.orig answer no. It  probably means you are running through this for the second time and answering yes will overwrite your original file. Use method 1 instead.
```
chmod 400 exports.orig
```
```
sed -i 's:^/nfs:/nfs/Public:' exports
```
```
newid=[COLOR=#ff0000]janm
# INSTEAD OF janm TYPE THE NEW USERNAME YOU CHOSE ABOVE IN STEP 2 ABOVE.[/COLOR]
```
```
echo "/nfs/$newid *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)" >> exports

```What we are doing here is:
Changing directory to /etc
Copying the exports file to one called exports.orig
Making the copy read only, so it will not be overwritten without a prompt.
The next line appends /Public to the line which starts /nfs. This is so the the Public directory will be available to everyone.
The newid.... line just sets a variable which is used below.
This line echoes the text and appends it to the exports file, adding /nfs/{newid}. The bunch of text after that makes it private to the new user.
Here it is in action:


[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/7_zps08aa78a8.jpg[/IMG]

9. From the terminal logged on to the server, to view the updated contents of the exports file type
```
cat /etc/exports

```and you should see this, except the username on the last line should match what you entered:

[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/8_zps5ea613fb.jpg[/IMG]

I am only permitted to use 8 images per post, so this post is continued [here]("http://ubuntuforums.org/showthread.php?t=2247242").

Second edit for clarification and add the option to create the new exports file locally, then rcp it to the server.
Third edit to replace a photo with a typo on the screen and to add a description of what the commands do.
Fourth edit to advise that this tutorial is not OS dependent but users need to know how to access the NAS UI and also how to start ssh in a terminal session.

---

### Post by Palindar on 2014-11-20
This is a great guide, thanks Scooby-2! I am teaching myself linux and I am trying to understand in detail the steps you describe. I am stuck at one line though and it would be great if you can point me in the right direction.

> [COLOR=#000000]*/nfs/*[/COLOR][COLOR=#ff0000]*janm*[/COLOR][COLOR=#000000]* *(rw,no_all_squash,sync,no_subtree_check,insecure, crossmnt,anonuid=65534,anongid=1000)*[/COLOR]

After adding this line, I would think that it does not matter which user is accessing the share but yet your instructions further down require uid's to be identical on server and client. Why is that?

---

### Post by zaphod_es on 2014-11-20
This looks to be a great post and I am sure it is going to help me get my new WD NAS configured the way I want it.

My first problem is all those screenshots.  What app are you running or is it in Windows or running in Linux under WINE ?

Until I can allow ssh there is no way I can do much and I cannot work out how to do that in my Linux only house.

---

### Post by Scooby-2 on 2014-11-21
@Palindar
I tried to keep the instructions as simple as possible without going deep into every point. Adding the user and share from the UI, which is detailed in the first 5 steps, gives ownership of the new share to that user. Hence they will be exported with that user's UID (NFS works with UIDs, not user names). As it can only be mounted by a user on a remote system who has the same UID it follows that a user who has a different UID (but may even have the same user name) will get "Permission denied" when they try to mount it.


@zaphod_es
I am running Teminal in Linux but you an also use Putty for Windows (it's free).

---

### Post by zaphod_es on 2014-11-21
> 
@zaphod_es
I am running Teminal in Linux but you an also use Putty for Windows (it's free).


My problem is that I cannot find how to access the  device from the Terminal in Linux. This is becuase the ssh server has not been authorised. I do not have Windows.

To authorise the shh server I need the UI shown in the first 5 steps. Can I get that without Widnows or Mac?

---

### Post by Scooby-2 on 2014-11-21
@[FONT=arial]zaphod_es[/FONT]

> [COLOR=#000000]My problem is that I cannot find how to access the device from the Terminal in Linux. This is becuase the ssh server has not been authorised. I do not have Windows.[/COLOR]

[COLOR=#000000]To authorise the shh server I need the UI shown in the first 5 steps. Can I get that without Widnows or Mac?[/COLOR]

From the Linux terminal, type ```
ssh root@{ip_address_of your_WD_NAS} 
```e.g. ```
ssh root@192.168.1.22 
```Have a look at [this]("https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server-in-ubuntu"). 

This is not relevant to this tutorial so I suggest you research further on the Internet rather than post here. If you have big problems feel free to pm me.

---

### Post by zaphod_es on 2014-11-21
I am an experienced Linux user and routinely use ssh to connect to remote servers. The problem is that the ssh daemon is not running on the NAS device and I need to know how to start it from a Linux box.

The tutorial is on ubuntuforums.org and my question (in the original post and repeated in the second) is how do you access the UI in Ubuntu.  If this were a tutorial for Windows or Mac users the question might not be relevant but in a Linux forum is 100% on topic. Surely it is not too difficult to tell me what OS and or program you used in the UI screen shots.  If the answer is that you did it in Windows and don't know how to do it in Linux: just say so.

---

### Post by Scooby-2 on 2014-11-21
> **zaphod_es said:**
> I am an experienced Linux user and routinely use ssh to connect to remote servers. The problem is that the ssh daemon is not running on the NAS device and I need to know how to start it from a Linux box.

The tutorial is on ubuntuforums.org and my question (in the original post and repeated in the second) is how do you access the UI in Ubuntu.  If this were a tutorial for Windows or Mac users the question might not be relevant but in a Linux forum is 100% on topic. Surely it is not too difficult to tell me what OS and or program you used in the UI screen shots.  If the answer is that you did it in Windows and don't know how to do it in Linux: just say so.

Step 6 above tells you how to start the ssh daemon. I used Ubuntu 14.04 LTS to obtain the screenshots.

---

### Post by cmfelix on 2015-01-09
Thanks for the tutorial, works great! I have a couple of questions about server/client uuid's. In my case I have several windows boxes that also mount Public and a private share from the same My Cloud being used from my Lubuntu box using the same name on all clients, lets just say, noob. I tried to adjust noob's uuid on the server side to match noob's uuid on the Lubuntu NFS client, per your suggestion, but it then blocked noob's access to the private share on Windows. I could only get Windows access again by going back to the uuid as it was before enabling the NFS procedure on the Lubuntu box. As expected, the Lubuntu client now doesn't allow noob's access to the private share. Since you indicated there could be complications in changing the existing client side uuid and the noob user name is the one I provided at installation time, I am considering re-installing Lubuntu with a user name like "install", then adding in noob after the installation is done when I could specify noob's uuid from the My Cloud. Would you expect that might alleviate any issues regarding making changes to noob's uuid, especially if it was the name used for installation? Or do I really need to use the install user name on a regular basis and I should continue to install w/noob and try to change the uuid post-install?

---

### Post by Scooby-2 on 2015-01-09
> **cmfelix said:**
> Thanks for the tutorial, works great! I have a couple of questions about server/client uuid's. In my case I have several windows boxes that also mount Public and a private share from the same My Cloud being used from my Lubuntu box using the same name on all clients, lets just say, noob. I tried to adjust noob's uuid on the server side to match noob's uuid on the Lubuntu NFS client, per your suggestion, but it then blocked noob's access to the private share on Windows. I could only get Windows access again by going back to the uuid as it was before enabling the NFS procedure on the Lubuntu box. As expected, the Lubuntu client now doesn't allow noob's access to the private share. Since you indicated there could be complications in changing the existing client side uuid and the noob user name is the one I provided at installation time, I am considering re-installing Lubuntu with a user name like "install", then adding in noob after the installation is done when I could specify noob's uuid from the My Cloud. Would you expect that might alleviate any issues regarding making changes to noob's uuid, especially if it was the name used for installation? Or do I really need to use the install user name on a regular basis and I should continue to install w/noob and try to change the uuid post-install?
@cmfelix
I wrote the procedure to help anyone wanting to use NFS and Linux to access the WD My Cloud. I suggest you start a new thread asking for help with your problem. I am not familiar with using NFS on Windows so I cannot tell you how to modify the UUID it would use to access a server.

> I am considering re-installing Lubuntu....
The words "sledgehammer" and "nut" spring to mind. I really don't think this should be necessary. I doubt it would solve your problem anyway.

---

### Post by rrichards on 2015-03-03
Hi

I have a problem with the step 11.
When i give the command "[COLOR=#000000][FONT=Ubuntu Mono]showmount -e localhost" it says "[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]showmount: Only one localhost is allowed". What it does mean?[/FONT][/COLOR]

---

### Post by Scooby-2 on 2015-03-03
> **rrichards said:**
> Hi

I have a problem with the step 11.
When i give the command "[COLOR=#000000][FONT=Ubuntu Mono]showmount -e localhost" it says "[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]showmount: Only one localhost is allowed". What it does mean?[/FONT][/COLOR]

Check your name resolution. It looks as though your localhost does not correspond to a unique IP. Try > showmount -e *hostname* where *hostname* is the host name of your server.

---

### Post by jason176 on 2015-05-06
I mistyped [COLOR=#000000][FONT=Ubuntu Mono]anonuid=65534 as amonuid=65534 and the restart command.  [/FONT][/COLOR] Exporting directories for NFS kernel daemon...exportfs: /etc/exports:3: unknown keyword "amonuid=65534"

exportfs: Failed to stat /nfs/Public/Public: No such file or directory.
How can I undo my mistake?

---

### Post by Scooby-2 on 2015-05-06
> **jason176 said:**
> I mistyped [COLOR=#000000][FONT=Ubuntu Mono]anonuid=65534 as amonuid=65534 and the restart command.  [/FONT][/COLOR] Exporting directories for NFS kernel daemon...exportfs: /etc/exports:3: unknown keyword "amonuid=65534"

exportfs: Failed to stat /nfs/Public/Public: No such file or directory.
How can I undo my mistake?

I presume you are at step 8 and you are using Method 2...? So:
Ensure you are in the /etc directory with ```
cd etc
```
Delete the line you made in error with ```
sed 'amonuid/d' exports
```
Set your newid variable with whatever you typed at this step: ```
[COLOR=#000000][FONT=Ubuntu Mono]newid=[/FONT][/COLOR][COLOR=#ff0000][FONT=Ubuntu Mono]janm
[/FONT][/COLOR][COLOR=#FF0000][FONT=Ubuntu Mono]# INSTEAD OF janm TYPE THE NEW USERNAME YOU CHOSE ABOVE IN STEP 2 ABOVE.[/FONT][/COLOR]
```
Retype the command ```
[COLOR=#000000][FONT=Ubuntu Mono]echo "/nfs/$newid *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)" >> exports[/FONT][/COLOR]
```
You should be good to go.

NB COPY AND PASTE THE LINE ABOVE.... I set it this way so that typo's would be less likely!

---

### Post by jason176 on 2015-05-06
After sed command it displays this.  
# shares by ACLs.
monuid/d
#
monuid/d
/nfs/Public/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
monuid/d


monuid/d
/nfs/Public/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,amonuid=65534,anongid=1000)
monuid/d
/nfs/Public/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
monuid/d
/nfs/Public/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
monuid/d
/nfs/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
monuid/d

---

### Post by jason176 on 2015-05-06
Sorry, didn't copy the whole thing.  It says:
 # shares by ACLs.
WDMyCloud:/etc# monuid/d
#
monuid/d
/nfs/Public/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
monuid/d


monuid/d
/nfs/Public/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,amonuid=65534,anongid=1000)
monuid/d
/nfs/Public/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
monuid/d
/nfs/Public/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
-bash: monuid/d: No such file or directory
monuid/d
/nfs/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
monuid/d
WDMyCloud:/etc# #
WDMyCloud:/etc# monuid/d
-bash: monuid/d: No such file or directory
WDMyCloud:/etc# /nfs/Public/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
-bash: syntax error near unexpected token `('
WDMyCloud:/etc# monuid/d
-bash: monuid/d: No such file or directory
WDMyCloud:/etc#
WDMyCloud:/etc# monuid/d
-bash: monuid/d: No such file or directory
WDMyCloud:/etc# /nfs/Public/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,amonuid=65534,anongid=1000)
-bash: syntax error near unexpected token `('
WDMyCloud:/etc# monuid/d
-bash: monuid/d: No such file or directory
WDMyCloud:/etc# /nfs/Public/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
-bash: syntax error near unexpected token `('
WDMyCloud:/etc# monuid/d
-bash: monuid/d: No such file or directory
WDMyCloud:/etc# /nfs/Public/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
-bash: syntax error near unexpected token `('
WDMyCloud:/etc# monuid/d
-bash: monuid/d: No such file or directory
WDMyCloud:/etc# /nfs/ctiadmin *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
-bash: syntax error near unexpected token `('
WDMyCloud:/etc# monuid/d
-bash: monuid/d: No such file or directory

---

### Post by Scooby-2 on 2015-05-06
I have to say I have absolutely no idea what is going on. What are "ctiadmin" and "monuid?" Have you set up aliases? Also, in some lines you have "[COLOR=#000000]cro ssmnt[/COLOR]" with either a space or a non-printable character after the letter "o." That will certainly be a problem.

Type > cat /etc/exports and pm me with the results and I'll help you. No point cluttering up the forum pages.

---

### Post by ludo-surfer on 2015-12-17
Hello
Thanks for this great guide.
I followed everything and it didn't worked for me.

The solution for me was to use this exports file

```

/nfs/Public (rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
/nfs/Username (rw,no_root_squash,sync,no_subtree_check,insecure,crossmnt)

```

I dont understand very well, but it works for me......

---

### Post by facundo8 on 2015-12-25
[[COLOR=#000000]Scooby-2[/COLOR]]("http://ubuntuforums.org/member.php?u=1365919")[COLOR=#000000] , [/COLOR]good morning, Merry Christmas to all.I need your help, I am following the manual and when I get to the part of cp exports exports.orig tells me that no such file exists.
I looking to Ls within the ETC, only I find one called exportfs. is the same? thanks.

---

### Post by facundo8 on 2015-12-25
> **ludo-surfer said:**
> Hello
Thanks for this great guide.
I followed everything and it didn't worked for me.

The solution for me was to use this exports file

```

/nfs/Public (rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
/nfs/Username (rw,no_root_squash,sync,no_subtree_check,insecure,crossmnt)

```

I dont understand very well, but it works for me......

Hello, you have the latest firmware installed 2.10.310 ?, because I have but if you can not find the exports. :icon_frown::icon_frown::icon_frown::icon_frown:  Like you did?. thanks

---

### Post by facundo8 on 2015-12-26
> **facundo8 said:**
> Hello, you have the latest firmware installed 2.10.310 ?, because I have but if you can not find the exports. :icon_frown::icon_frown::icon_frown::icon_frown:  Like you did?. thanks


Works !! 

here my video:

[https://www.youtube.com/watch?v=S5P_-sX09Mo](https://www.youtube.com/watch?v=S5P_-sX09Mo)

---

