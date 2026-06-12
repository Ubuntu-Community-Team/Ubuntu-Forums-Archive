---
title: "Ubuntu to Windows XP networking"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by mollydoggy1971 on 2008-11-26
I am very new to Ubuntu, and Linux in general.  I have installed the latest Ubuntu over the past weekend.  I cannot get it to connect to my Windows network.  I have no idea what I am doing in Linux, so please, if you're going to offer me some help, I ask that you make it VERY detailed, step-by-step instruction.  I don't know where anything is in Ubuntu, and don't know how to access anything.  I have been given a bit of advice on linuxquestions, but I'm not getting anywhere with them, as most of them are not using Ubuntu, so they can't give me specific direction.  I do not even know whee to type commands, so if you want me to type commands, please tell me how to do that also.  
I have been told to go to Places, Connect to Server.  I go there, and change the drop down box to Windows Share.  I was told to put in the Server name, and it would find the server.  My network's name is MSHOME, and the windows pc name is MAINPC.  The shared drive on there is C.  So, I put in MSHOME for the server name, and it doesn't work.  I put in MSHOME for the server name, and MAINPC for the Share box, and it doesn't work. I also added C to the Folder box, with the same results.  
If I go to Places, Network, it gives me an icon that says Windows Network.  When I double click it, it shows 0 results.  
Any DETAILED help you folks could offer would be greatly appreciated.  I'm getting close to deleting Ubuntu and giving up on Linux forever.

Thanks,
Jeff

---

### Post by philetus on 2008-11-26
Hi Jeff,

Install Samba.

Here's a link with everything you need.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by mollydoggy1971 on 2008-11-27
> **philetus said:**
> Hi Jeff,

Install Samba.

Here's a link with everything you need.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

OK.  After about 30 minutes of trying to figure out where to type commands, I finally figured it out.  Again, I need VERY DETAILED STEP-BY-STEP instructions.  I followed the instructions, which were confusing, to say the least.  I don't know that I changed the things I was supposed to change properly, as I do not understand what I am doing.  I got to the point where it says to type "sudo chmod 0777 /media/samba" and when I typed that, it said "chmod: cannot access `/media/samba': No such file or directory"

What have I done wrong, and why isn't it working?  As an aside note, I was told on another forum that I didn't need to install Samba, and, in fact, was told NOT to install it several times by the Administrator of the forum.  So I'm approaching this very cautiously.

---

### Post by philetus on 2008-11-27
Use this tutorial:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Scroll down to "Configuring your computer"

make both computer's workgroups "MSHOME"

Use IP 192.168.1.102

---

### Post by philetus on 2008-11-27
Use this:

[http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/](http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/)

to set up your shared folder

---

### Post by mollydoggy1971 on 2008-11-27
> **philetus said:**
> Use this tutorial:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Scroll down to "Configuring your computer"

make both computer's workgroups "MSHOME"

Use IP 192.168.1.102

That looked like a wonderful link, but the first thing it says is the following:
Configuring your computer

Start the network configurator using the following menu:

System -> Administration -> Network

I do not have a Network option under Administration.  The closest thing I have to that is Network Tools, and when I choose that, it does not look like the picture displayed in the link you provided, so I could not continue any further.

Outdated links + total n00b = confusion and nothing learned :/

---

### Post by mollydoggy1971 on 2008-11-27
> **philetus said:**
> Use this:

[http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/](http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/)

to set up your shared folder

I followed this link, and it told me to create a folder on the desktop (it did...something actually worked!).  After creating the folder, it asked me to click Sharing Options, which I also did.  It opened a box that offered me a choice to Share this folder.  The link said to click it, and I did.  I did not, however, get the rest of what the link said I should get.  I continued under the assumption that the sharing services were indeed installed, and that the link was incorrect.  Skipping down a bit further, I followed the step that said to click the box to allow other people to write in this folder.  I did, and clicked Create Share.  It gave me the following error:  'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.

So, again, I have a suggestion that is not working.  If I am doing something wrong (I am following the instructions EXACTLY in every case, except where I skipped ahead a bit, as explained earlier), please let me know that A) I am doing something wrong, and B) EXACTLY what I am doing wrong.

I really do appreciate the help being offered, and am very frustrated at the lack of basic networking connectivity that Ubuntu is offering me.  Windows networking takes about 5 minutes to set up properly.  If Linux is supposed to be so much better, and a viable alternative to Windows, then why should I be having to take at least 1 week to do the same thing, with no success as of yet?

---

### Post by benhur99ph on 2008-11-27
> **mollydoggy1971 said:**
> I really do appreciate the help being offered, and am very frustrated at the lack of basic networking connectivity that Ubuntu is offering me.  Windows networking takes about 5 minutes to set up properly.  If Linux is supposed to be so much better, and a viable alternative to Windows, then why should I be having to take at least 1 week to do the same thing, with no success as of yet?

Hmmmm... network sharing with Ubuntu is just as easy as it is with Windows. This has been said already or you might have read it in the guides that the others sent you, samba is the way to do it.

This is how I do it from a fresh install of Ubuntu.

First, I create a folder.
Then, right-click the folder and select "Sharing Options".
Then, click the checkbox that says "Share this folder".
After that, if SAMBA is not yet installed (which I assume it is not since this is a fresh install), Ubuntu will prompt you that SAMBA needs to be installed and asks you if you want to.
Click yes.
Ubuntu will automatically download and install the files.
After installation, go to System>Administration>Users and Groups.
Click "Unlock" and type your password.
Then click "Manage Groups" and scroll down to "sambashare".
Select "sambashare" and click "Properties".
Then click on the checkbox of the users that you want to include. (Your username).
After that log-off and log-in again.
Then right-click the folder again (or any folder that you want to share) and select "Sharing Options".
This time you will be able to select the checkbox that says "Share this folder".
After that, you can now access your Ubuntu shared folder from Windows.

To access your Windows files from Ubuntu. Since you have already installed Samba. Go to Places>Connect to Server...
Then from the drop down list choose Windows Share.
Under Server: Type the IP address of your Windows machine.
Under Share: Type the folder name of the shared Windows folder.
Then click on "Connect".

This works for me 100% of the time and I have been doing this process since Ubuntu Feisty and now I'm using Hardy. I have also tried it with Intrepid. 

Hope this helps...

---

### Post by joerdie on 2008-11-27
> **benhur99ph said:**
> Hmmmm... network sharing with Ubuntu is just as easy as it is with Windows. This has been said already or you might have read it in the guides that the others sent you, samba is the way to do it.

This is how I do it from a fresh install of Ubuntu.

First, I create a folder.
Then, right-click the folder and select "Sharing Options".
Then, click the checkbox that says "Share this folder".
After that, if SAMBA is not yet installed (which I assume it is not since this is a fresh install), Ubuntu will prompt you that SAMBA needs to be installed and asks you if you want to.
Click yes.
Ubuntu will automatically download and install the files.
After installation, go to System>Administration>Users and Groups.
Click "Unlock" and type your password.
Then click "Manage Groups" and scroll down to "sambashare".
Select "sambashare" and click "Properties".
Then click on the checkbox of the users that you want to include. (Your username).
After that log-off and log-in again.
Then right-click the folder again (or any folder that you want to share) and select "Sharing Options".
This time you will be able to select the checkbox that says "Share this folder".
After that, you can now access your Ubuntu shared folder from Windows.

To access your Windows files from Ubuntu. Since you have already installed Samba. Go to Places>Connect to Server...
Then from the drop down list choose Windows Share.
Under Server: Type the IP address of your Windows machine.
Under Share: Type the folder name of the shared Windows folder.
Then click on "Connect".

This works for me 100% of the time and I have been doing this process since Ubuntu Feisty and now I'm using Hardy. I have also tried it with Intrepid. 

Hope this helps...

I know Windows very well and am just getting started with Linux. To be honest, I was losing hope. But this post was exactly what I needed. I can't thank you enough. I hope this helps the thread starter.

---

### Post by benhur99ph on 2008-11-27
> **joerdie said:**
> I know Windows very well and am just getting started with Linux. To be honest, I was losing hope. But this post was exactly what I needed. I can't thank you enough. I hope this helps the thread starter.

Hey! I'm glad that I helped you out. Ubuntu and Linux in general is a wonderful OS. Be sure to explore it. I also hope that this helps the thread starter. If you have any questions, feel free to ask me and I'll help if I can.

---

### Post by mollydoggy1971 on 2008-11-28
> **benhur99ph said:**
> Hmmmm... network sharing with Ubuntu is just as easy as it is with Windows. This has been said already or you might have read it in the guides that the others sent you, samba is the way to do it.

This is how I do it from a fresh install of Ubuntu.

First, I create a folder.
Then, right-click the folder and select "Sharing Options".
Then, click the checkbox that says "Share this folder".
After that, if SAMBA is not yet installed (which I assume it is not since this is a fresh install), Ubuntu will prompt you that SAMBA needs to be installed and asks you if you want to.
Click yes.
Ubuntu will automatically download and install the files.
After installation, go to System>Administration>Users and Groups.
Click "Unlock" and type your password.
Then click "Manage Groups" and scroll down to "sambashare".
Select "sambashare" and click "Properties".
Then click on the checkbox of the users that you want to include. (Your username).
After that log-off and log-in again.
Then right-click the folder again (or any folder that you want to share) and select "Sharing Options".
This time you will be able to select the checkbox that says "Share this folder".
After that, you can now access your Ubuntu shared folder from Windows.

To access your Windows files from Ubuntu. Since you have already installed Samba. Go to Places>Connect to Server...
Then from the drop down list choose Windows Share.
Under Server: Type the IP address of your Windows machine.
Under Share: Type the folder name of the shared Windows folder.
Then click on "Connect".

This works for me 100% of the time and I have been doing this process since Ubuntu Feisty and now I'm using Hardy. I have also tried it with Intrepid. 

Hope this helps...

Those were wonderful directions.  I followed the directions exactly, and I have something new, but not quite what I'm looking for.  After using Places?Connect to Server, I typed in the IP address of the other machine (192.168.1.100).  Then the window went away, with no confirmation or anything.  So I opened Places>Network.  It shows a computer tower icon with the name UBUNTU and another icon showing a tower and two monitors named Windows Network.  When I click on Windows Network, it opens to show an icon named WORKGROUP.  When I click on that one, it shows the UBUNTU tower icon!  If I click that icon, it shows the print$ icon and the Test Folder icon (which I made by following the first set of steps you gave me).  So, while I have indeed gotten further than I ever have before, I still can't access anything on my other pc.  It looks like I'm on the right path though.  Thanks for the help so far, and any further help would be greatly appreciated (especially if it's written as detailed as this post was!).

Jeff

---

### Post by mollydoggy1971 on 2008-11-28
By the way, if anyone wants to connect remotely to me, in order to verify what I am doing, or if you think it may be easier to instruct me that way, let me know and we will connect at your convenience (when I'm not working).  I do, however, work until 3:30am Mon, Tues, Thurs and Fri, and until around 11pm Sat & Sun.  All times are Central.  

Thanks again!

---

### Post by mollydoggy1971 on 2008-11-28
After some fiddling about for a while, I somehow am now able to see the Workgroup network place under the XP machine, and am able to access the Test Folder folder that I created in Ubuntu on both machines.  I now also see the MSHOME as well as WORKGROUP options under the File Browser.  I do not, however, see any of the shared folders in MSHOME; it just opens to a blank area.  I'm excited that I can now move files between computers, but I would really like to access my shared folders on the other machine (MSHOME network).  Any ideas?

Jeff

---

### Post by benhur99ph on 2008-11-28
@mollydoggy1971

Try this out...

At the Places>Connect to Server... after typing 192.168.1.100, type the name of the folder on your XP machine "Under Share".

It should directly open the shared folder of XP machine. 

Then post again what happens. Hopefully this works.

---

### Post by mollydoggy1971 on 2008-11-28
> **benhur99ph said:**
> @mollydoggy1971

Try this out...

At the Places>Connect to Server... after typing 192.168.1.100, type the name of the folder on your XP machine "Under Share".

It should directly open the shared folder of XP machine. 

Then post again what happens. Hopefully this works.

Well, now I've lost the windows machine's icon under Windows Network.
And no, it didn't open the folder I specified :(

---

### Post by mollydoggy1971 on 2008-11-28
Ok, on a hunch, I shut off ZoneAlarm on the windows pc.  Now I can access the shared folders on the windows pc!  YAY!  The next question is, how do I configure ZoneAlarm to allow access from the Ubuntu machine?  I really don't want to run without a firewall.

Thanks to you all for your help thus far!

---

### Post by mollydoggy1971 on 2008-11-28
WOOHOO!!!  After a bit of messing with ZoneAlarm, I figured out how to allow the Ubuntu computer's IP.  So I am running well now!  I may do a little dance now :P

THANK YOU ALL VERY VERY MUCH!!!

Jeff

---

### Post by benhur99ph on 2008-11-28
> **mollydoggy1971 said:**
> WOOHOO!!!  After a bit of messing with ZoneAlarm, I figured out how to allow the Ubuntu computer's IP.  So I am running well now!  I may do a little dance now :P

THANK YOU ALL VERY VERY MUCH!!!

Jeff

Hahaha! That gives! ZoneAlarm can be pretty picky with these things. Congratulations! Happy Ubuntu-ing!

---

