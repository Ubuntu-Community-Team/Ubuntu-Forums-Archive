---
title: "Setting up an Ubuntu only home network"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by applet3typod on 2010-05-08
I have been looking high and low and can not seem to find ANY info on how to network two Ubuntu computers with the latest OS (Lucid). Everything I find is for 8.0 or older, and is for networking with Windows which I would not in my right mind ever think of doing. lol

How do I setup a basic wired network to be able to share files between two systems both running Ubuntu 10.4(Lucid) that are already connected to the same router and both have the same Internet connection (duh?). lol I don't *think* I'm a total idiot, but I am less than a week old in terms of Linux. I know Mac and Windows pretty well if anyone has a simple comparison.

---

### Post by spiky001 on 2010-05-08
hi insatll ssh open server in synaptic manager you can go from there then if you need more advice come back an d ask

---

### Post by applet3typod on 2010-05-08
Ok, I had no clue what you were talking about so I did my research and I now have ssh installed correctly. I've been looking for the next step, or what to do with what I have so far, and it's not slapping in the face yet.

next? or at least where to look? lol

---

### Post by r-senior on 2010-05-08
It should be pretty much plug & play. Have you tried running the two machines and checking you've got connectivity, e.g. with ping?

If you look in Nautilus (file manager) you could then try the "Sharing Options" that you get when you right-click on a folder? Also have a look at Places -> Network and see what you can see.

---

### Post by applet3typod on 2010-05-08
ok, under ~places-network, I have a Windows network? (no clue how it got there as I am on a wired network and am proud to be a Linux only family.) and when I click to see whats is in it, it says it's unable to mount?

And (hate sounding dumb here) I don't know where I can find the "network address" (to ping), and I have the feeling thats something I need to set up maybe?

---

### Post by applet3typod on 2010-05-08
Ok, you guys have been extremely helpful! here's where I am... I got it set up, and I can see the files that I am sharing, BUT! when I go to open any of them, it's asking for a user-name and password, and it's not accepting that info for either computer. What exactly is it asking for?

---

### Post by nothingspecial on 2010-05-08
If you just want full access to both machines from each other, this is so easy it`s embarrasing.

```
sudo apt-get install openssh-server openssh-client
``` on both machines.

On each machine right click on the network icon and choose connection information.

Note down the ipaddress of each machine.

Then in your menu, go places > connect to server.

In the top box choose ssh

In the next box type username@ipaddress_of_other_computer.

Put a tick(check) in the add bookmark box.

Choose a name for the other computer.

Click connect.

Type the password of the other machine.

Check the remember password forever box.

Repeat process on the other machine.

You will now have a bookmark in your places menu, on each machine that will give you full access to the complete filesystem of the other computer.

Cool isn`t it?

---

### Post by applet3typod on 2010-05-08
ok, what you just showed me (nothingspecial) was freaking amazing BUT! (lol) I'm getting a loop on both machines where it's asking for me to enter the password. I type it in (the password for the other machine like you said) I click "connect", it disappears and then pops back up. 

Suggestions on this one?

(Also: I tried to open one of the now visible shared folders and it does the same thing, asks for password, and then just keeps looping.)

---

### Post by applet3typod on 2010-05-08
new box popped up saying:
> Cannot display location (my user and IP)

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.The connection is good, and I have no clue what gibberish the rest was saying.

And apparently the box won't allow me to click "ok" or close out of it...

---

### Post by applet3typod on 2010-05-08
anyone?

---

### Post by spiky001 on 2010-05-08
hi 1st off you need to know the ip address of the machine you installed ssh on, then we,ll go to next step

---

### Post by applet3typod on 2010-05-08
ok, I think I found it, but it's the same IP on both machines... how should I be finding the IP? 

I went to: system>administration>network tools and looked under devices.

---

### Post by spiky001 on 2010-05-08
ok open a terminal Applications accessories Terminal in the terminal type

```
ifconfig
```

do this on the machine with ssh on look for the eth0, the 2nd line down is the address of that machine
int addr :10.xx.xx.x

---

### Post by tad1073 on 2010-05-08
If you are using samba, or nfs for that matter, you need to have user accounts for each user on all computers unless of coarse you have a server running ldap.

[https://calomel.org/samba.html](https://calomel.org/samba.html) may be of some use

---

### Post by Ethan McWinston on 2010-05-08
> **applet3typod said:**
> ok, I think I found it, but it's the same IP on both machines... how should I be finding the IP? 

I went to: system>administration>network tools and looked under devices.

To see your IP which is assigned by the router go to the top-right corner of the screen and right click on the NetworkApplet Manager. Then select Connection Information and your IP address in your home network is the one after "IP Address:".
The other computer will have a different address.

---

### Post by applet3typod on 2010-05-08
Hell Freaking Yeah guys!!! I've got my network all set up, and I learned a ton while I was at it. Thank you all!

Big thanks to: nothingspecial and spiky001, and everyone else for helping me understand what they were saying. lol

---

### Post by spiky001 on 2010-05-08
we do try

---

### Post by nothingspecial on 2010-05-08
Sorry. Replied to your question then took the kids to the cinema.

Glad to here you got it sorted.

---

### Post by grj23 on 2010-05-11
By the way, you can just right click on a given folder and go to properties and then sharing, and make it accessible via the network.  Then other computers on the same local network will be able to see those folders.

On the other hand, if you're using something like Unison, then you want to ssh.

---

### Post by steve-o1983 on 2010-09-12
> **nothingspecial said:**
> If you just want full access to both machines from each other, this is so easy it`s embarrasing.

```
sudo apt-get install openssh-server openssh-client
``` on both machines.

On each machine right click on the network icon and choose connection information.

Note down the ipaddress of each machine.

Then in your menu, go places > connect to server.

In the top box choose ssh

In the next box type username@ipaddress_of_other_computer.

Put a tick(check) in the add bookmark box.

Choose a name for the other computer.

Click connect.

Type the password of the other machine.

Check the remember password forever box.

Repeat process on the other machine.

You will now have a bookmark in your places menu, on each machine that will give you full access to the complete filesystem of the other computer.

Cool isn`t it?


I have been beating me head against the wall trying to figure this out for the last couple days, until I found this.  Thanks, it was so easy and I feel rather silly considering it took so long.

---

### Post by audballbandit on 2011-08-19
hi all!

i'm trying to connect three ubuntu 11.04 machines (desktop, 2 laptops).  i've followed the directions posted earlier.  being a total n00b, i'm a little confused.  when it asks for username@ipaddress_of_other_machine, is it just that?  if the desktop is named bob and laptopA is named joe, would it be joe@ipaddress?  also, when i click connect and am asked for a password, it loops but never opens.  any help would be greatly appreciated!

---

### Post by ccroy on 2012-01-08
> **nothingspecial said:**
> If you just want full access to both machines from each other, this is so easy it`s embarrasing.

```
sudo apt-get install openssh-server openssh-client
``` on both machines.

On each machine right click on the network icon and choose connection information.

Note down the ipaddress of each machine.

Then in your menu, go places > connect to server.

In the top box choose ssh

In the next box type username@ipaddress_of_other_computer.

Put a tick(check) in the add bookmark box.

Choose a name for the other computer.

Click connect.

Type the password of the other machine.

Check the remember password forever box.

Repeat process on the other machine.

You will now have a bookmark in your places menu, on each machine that will give you full access to the complete filesystem of the other computer.

Cool isn`t it?

Nothing Special, Thanks for the clear instructions!

I am trying to install a home network on 2 PC's. My old PC is running 10.04 and the new one is running 11.10 64 bit.

On the 10.04 PC I can follow your instructions exactly and I have a bookmark in Places for the filesystem of the new PC.

When I try to log into the old PC from the new (11.10) PC I am denied access.

The 11.10 dialog box is different than the 10.04 and has box for a folder. Do I need to create a folder on the 10.04 machine? 

When I try to login to the old PC I get a message "Please Verify your user details" or "Access Denied"

Anybody know what I am missing?

Thanks!

Chris

---

### Post by nothingspecial on 2012-01-08
Just put / in the folder box.

rather than user@ipaddress in one box, now you put the ip address in the top box and there is a seperate box for the username.

There isn't an add bookmark box any more. When you are connected an entry should appear in the left hand pane starting "SFTP for ...".

Right click that and you can add a bookmark. You can rename the bookmark by right clicking it.

---

### Post by ccroy on 2012-01-09
Thanks,
 
I think I still have an issue with the 10.04 PC. If I go into System>Preferences>Personal File Sharing I get a dialog box with 3 connections: Network, Bluetooth, and wireless maybe (sorry I'm at work, not at my 10.04 PC). 
 
Anyway, the option to enable file sharing over the network is greyed out so I can't enable it. It says I do not have the required packages installed, but of course being Ubuntu, it doesn't tell me what packages to install! ;)
 
I also check the start up menu and file sharing is check to load upon startup, if enabled, but due to the above it's currently disabled.
 
I think I will have to do a little more reading and searching on ssh to understand how it works and if I really need to enable  System>Preferences>Personal File Sharing 
 
Maybe it's still a naming or IP issue? From the 10.04PC I can connect to the 11.10PC, open a document and save a copy locally. I just can't access the 10.04 PC from the 11.10 PC.
 
Any thoughts post away!

---

### Post by nothingspecial on 2012-01-09
Ah I see your problem. There is no places menu anymore.

Open your file browser and go to the global menu (in the top bar). It doesn't appear until you hover your mouse over it.

Then click File > Connect To Server

And proceed as in my previous post.

---

### Post by ccroy on 2012-01-13
Thanks!

On the 11.10 PC that was it! IP address of the old PC and username/password and it let me in!

Chris

> **nothingspecial said:**
> Just put / in the folder box.

rather than user@ipaddress in one box, now you put the ip address in the top box and there is a seperate box for the username.

There isn't an add bookmark box any more. When you are connected an entry should appear in the left hand pane starting "SFTP for ...".

Right click that and you can add a bookmark. You can rename the bookmark by right clicking it.

---

