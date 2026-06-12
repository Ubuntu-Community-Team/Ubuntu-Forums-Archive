---
title: "How you do file share between two ubuntu machines?"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by PiggiePaul on 2008-04-01
Must admit, I never thought I'd be asking this as it seems quite a bizarre question, though to be fair I've never done this before, but I kinda guessed it "Would Just Work"

I have a Windows PC (with file sharing enabled) and when I first installed ubuntu I was amazed to see I could just browse my home network and access the shared folders on my windows PC without installing or setting up anything.

It just worked (and as I said, I was amazed and very impressed.

Anyhow, I now have another PC, but this time instead of windows I've installed Ubuntu 7.10 on it.  The same as my main machine I'm typing this on.

But you know what, they can't connect to each other. 

Guess it's due to some settings I need to get going.

I have highlighted a folder on both the PC's and said to share them. But still nothing.

Is there (or can someone tell me) step by "simple" step what I need to do on both machines (they should be identical) so either machine can browse a shared folder on the other.

Many thanks.

---

### Post by Jim_1981 on 2008-04-01
I assume it's a windows network so you'll need to use samba. Make sure samba is installed - go to system -> administration -> synaptic and search for samba. Then go to system -> administration -> shared folders and share all the folders you want to share.

you'll also need to create a samba account. in a terminal type

```
sudo smbpasswd -L -a COMPUTER_NAME
```

where you've changed COMPUTER_NAME to the actual name of you computer. Then use the command 

```
sudo smbpasswd -L -e COMPUTER_NAME
```

to enable it. Once you've done that, you should just be able to go to places -> network and see your machines there.

---

### Post by PiggiePaul on 2008-04-01
> **Jim_1981 said:**
> I assume it's a windows network so you'll need to use samba. Make sure samba is installed - go to system -> administration -> synaptic and search for samba. Then go to system -> administration -> shared folders and share all the folders you want to share.

you'll also need to create a samba account. in a terminal type

```
sudo smbpasswd -L -a COMPUTER_NAME
```

where you've changed COMPUTER_NAME to the actual name of you computer. Then use the command 

```
sudo smbpasswd -L -e COMPUTER_NAME
```

to enable it. Once you've done that, you should just be able to go to places -> network and see your machines there.


Thanks, but having a bit of a problem (prob me being a bit dim!

Samba is already installed so that's ok.

Say my computer (this one) is called "banana" (not my username - but the machine name)

Then I typed 

[COLOR="Blue"]sudo smbpasswd -L -a banana[/COLOR]

It responded with:

[COLOR="Blue"]New SMB password:[/COLOR]

I then typed my normal machines password in (as it's easy to keep the same password on things)

After pressing return it then asked:
[COLOR="Blue"]
Retype new SMB password:[/COLOR]

I did, and pressed return and it said:

[COLOR="Blue"]Failed to modify password entry for user banana[/COLOR]

---

### Post by Superslobberface on 2008-04-01
Use SSH.  It's a simple way to share between two Linux computers

_[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)_

On the server:
```
sudo apt-get install openssh-server
```

On the client:
```
sudo apt-get install openssh-client
```

From Gnome on the client computer:
Nautilus can access remote computers via SSH, and browse and transfer files.
```
Click Places -> Connect to Server. Select SSH for Service Type
Write the name or IP address of the computer you're connecting to in Server
the user you'd like to connect as in User Name
and a name for the connection if you wish.

```

Files can be copied by dragging and dropping between this window and other windows.

---

### Post by PiggiePaul on 2008-04-01
> **Superslobberface said:**
> Use SSH.  It's a simple way to share between two Linux computers

_[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)_

On the server:
```
sudo apt-get install openssh-server
```

On the client:
```
sudo apt-get install openssh-client
```

From Gnome on the client computer:
Nautilus can access remote computers via SSH, and browse and transfer files.
```
Click Places -> Connect to Server. Select SSH for Service Type
Write the name or IP address of the computer you're connecting to in Server
the user you'd like to connect as in User Name
and a name for the connection if you wish.

```

Files can be copied by dragging and dropping between this window and other windows.


Thanks for the suggestion.

Will this method work like normal file sharing?

I'd like to just have a shortcut icon (for a shared folder on a remote machine) that I can just click on and open up to access the files.

---

### Post by stefangr1 on 2008-04-01
Yes, that will work just fine.

---

### Post by jabeez on 2008-04-01
I think this is one issue that should be ironed out ASAP. I've posted on it before, and don't understand why Linux>Windows is easier than Linux>Linux. Anywho, for simple file sharing between 'Buntu boxes, I've found Samba to be easy, although not great. On KDE, all you have to do is go into Control Panel>Sharing and set up whatever folders you want to share. I haven't delved into NFS, which I hear you "should" use between Linux boxes, but it seems harder to set up.

It's also annoying that while I use my laptop with Vista (just for testing purposes:)), I can browse the folders shared on my Linux box and use them as if they were right on the hardrive, yet I browse around from the wifes Linux box and can't really open any media files. What gives?

(not meaning to hijack your thread here)

---

### Post by Eiríkr on 2008-04-01
@PiggiePaul --

I would strongly recommend you read the man page for smbpasswd (type "man smbpasswd" in a terminal).  It notes that, among other things, you can only add usernames to the Samba password list that already exist on your Ubuntu machine.  So if your user "banana" doesn't exist as a regular Ubuntu user, no dice.

Cheers,

Eiríkr

---

### Post by PiggiePaul on 2008-04-02
> **Eiríkr said:**
> @PiggiePaul --

I would strongly recommend you read the man page for smbpasswd (type "man smbpasswd" in a terminal).  It notes that, among other things, you can only add usernames to the Samba password list that already exist on your Ubuntu machine.  So if your user "banana" doesn't exist as a regular Ubuntu user, no dice.

Cheers,

Eiríkr

Ahh, perhaps that it.

He said to put in Computer-Name

Should it have been User-Name ?

I have the name of the Machine (banana as an example)
The Username (me)
the Password (password)

---

### Post by Herman on 2008-04-02
+1 for SSH, I've been using it for years, it's great.
Samba is only good for Ubuntu to Windows and printers and is quite a lot more complicated to set up and secure, as far as I know.
SSH is for Linux users, and is easy to set up and secure from the start, although you can add more security to it later if you think you need to.

---

### Post by PiggiePaul on 2008-04-02
If I use this SSH method, suggested a few posts ago by "Jim_1981" Can I install both the server and the client on both machines?

As I'd like it to work in both directions depending on which machine I'm sitting at, at the time.

---

### Post by Eiríkr on 2008-04-02
Just install the [font=courier]ssh[/font] package via Synaptic or [font=courier]apt-get install[/font] in a terminal, and you get both the client and server halves.  So for two-way sharing, just make sure you've installed this package on both machines, and you should be good to go.  

Cheers,

Eiríkr

---

### Post by Redline21 on 2008-04-02
Yea, SSH works great. Once it is setup, you can simply enter "ssh://ipaddress" (where ipaddress is the ip of the destination machine) in the location bar of any folder browser window. It will let you browse all files and folders on the destination machine regardless of whether they are shared or not. 
And yes, it is easy to make launchers on the desktop. Just set the type to "Location", give it a name, enter ssh://destinationip for the location and you are all set!

---

### Post by hooligan36 on 2008-04-02
Here's a problem i'm having with my setup. I have gutsy on both my laptop and desktop/server. I have ssh, samba, and have shared a couple of files. I also connect to server on my laptop for my music, videos and pics. 

My problem is that after about a day or so, I can't access my server from my laptop. Everything is running ok o the server, I can even remote desktop to it from the laptop. I just can't access files and what not, when I click on the links on my desktop, I get nothing.

How do I keep this from happening?

---

### Post by Herman on 2008-04-02
> If I use this SSH method, suggested a few posts ago by "Jim_1981" Can I install both the server and the client on both machines?
Ubuntu comes with the SSH client installed by default, so you can always access any machine with SSH server installed from any Ubuntu, even the Live CD. 
That is good to know if you ever need to use a LiveCD for performing a file rescue.
You can also use the scp command to import files into your machine from a SSH server, or the other way without installing SSH server in the machine you're working from.
All Ubuntu systems are SSH clients.

SSH Server is quite secure. You can run a port scan from another Ubuntu machine or LiveCD in your LAN and there should be no open ports in a fresh Ubuntu installation, but after you install SSH Server, you can run the scan again and you will see that port 22 will be 'open'. ('Administration'-->'Network Tools', and use the port scan tab, and enter the IP address of the machine to be scanned.
However, anyone trying to access your machine through SSH requires a username and a password, so as long as you have a good secure password you should be pretty secure.
Later if you need to (if your server is directly exposed to the internet, or just if you want to, you can change the port number and switch to RSA keys for logging in, that gives you even more security.
SSH is able to be configured so it is secure enough to port forward to your router and make your server available to the internet so you can travel with your laptop or Ubuntu in a USB flash memory stick and be able to access all the files stored in your home PC from anywhere.

---

### Post by Herman on 2008-04-02
> My problem is that after about a day or so, I can't access my server from my laptop. Everything is running ok o the server, I can even remote desktop to it from the laptop. I just can't access files and what not, when I click on the links on my desktop, I get nothing.

How do I keep this from happening?
hooligan36, Try running the command 'ifconfig' to see what your IP addresses are.

If your IP addresses are given out dynamically (they are different every day because you don't boot your computers up in the same sequence), then SSH will not connect.
It depend what kind of hardware you have (router). 
Try to go into your router setting and look for a setting the enables you router to remember which computer is which and set your router to give each computer the same IP address every morning. I think that will be somewhere in 'DHCP Server' settings if your router has that feature.

What brand of router do you have anyway? Maybe I can help you more if I know that.

---

### Post by hooligan36 on 2008-04-02
They both (laptop and server) have reserved IPs from my dlink router. I am having to re-boot teh server to get the sharing/server connections going again.

---

### Post by Eiríkr on 2008-04-02
Run the following from a terminal on the server (or via ssh) to make sure that the Samba processes haven't crashed:
```
ps aux | grep mbd
```
Look specifically for instances of smbd and nmbd.

Cheers,

Eiríkr

---

### Post by chili555 on 2008-04-02
plus another for ssh.

> I think this is one issue that should be ironed out ASAP. I've posted on it before, and don't understand why Linux>Windows is easier than Linux>Linux.It's not and there is nothing to iron out. With ssh, it works perfectly. An icon appears on your desktop, you browse folders, drag-n-drop, etc. Frankly, I don't know how to make it any easier.

As was noted above, if you want the folder to stick, the server must have a static IP address. All the desktops, including the server, have static IP addresses here. Being a bit OCD, I even gave them names, like *frankenputer*  and then added them to /etc/hosts:```
frankenputer 192.168.1.101
```Then you can ssh and ping by name and don't have to remember the IP address.

---

### Post by koenn on 2008-04-02
> **jabeez said:**
> I think this is one issue that should be ironed out ASAP. I've posted on it before, and don't understand why Linux>Windows is easier than Linux>Linux. 
not meaning to hijack anything either, but I could not let this pass. 
Linux > WIndows (or Windows > WIndows for that matter) is easy because in WIndows filesharing is enabled by default, newly created shares are created with everyone:Read permission by default (Everyone;Full Controll in pre-XP versions), and the enire hard disk is shared by default "for administrative purposes". And therefore any windows machine directly attached to the internet is offering file sharing to the whole world as soon as you create 1 share OR didn't set an administrator password. 
There's easy, and then there is plain silly.

NFS is trivial to set up, by the way, so for Linux > Linux, I'd go NFS, or SSH like others are suggesting.

---

### Post by Herman on 2008-04-02
[File Ownership and Permissions]("http://users.bigpond.net.au/hermanzone/p10.htm#File_Ownership_and_Permissions") :)

---

### Post by hooligan36 on 2008-04-04
Ok, so when I get home I am gonna try the launcher with ssh advice for access to my media files. 

I still can't figure out why I can not see the server after a while. What protocol/app causes the machine to be seen when I open "network" on my laptop?

---

### Post by koenn on 2008-04-04
NETBIOS broadcasting ?

---

### Post by hooligan36 on 2008-04-05
Ok, I did what Erikir said and this is what I got. There are two instances of smbd, but I have o idea what they mean. Help?

---

### Post by Eiríkr on 2008-04-05
Hey there Hooligan --

Your results show that smbd is running, which is good (and no problem with there being multiple instances).  However, we also see that nmbd, the name resolution side of things, is *not* running.  Restart your Samba server, then check again using the "ps aux | grep mbd" command to see if nmbd is up.  
```
sudo /etc/init.d/samba restart
ps aux | grep mbd
```

If nmbd is *still* missing, it must be failing out for some reason.  Have a look in the nmbd log to see if there are any clues as to why.
```
less /var/log/samba/log.nmbd
```

HTH,

Eiríkr

---

### Post by hooligan36 on 2008-04-22
It did it again so this is the resulting log.......



[2008/04/20 23:14:13, 0] nmbd/nmbd.c:reload_interfaces(229)
  reload_interfaces: No subnets to listen to. Shutting down...
[2008/04/22 05:31:29, 0] nmbd/nmbd.c:main(697)
  Netbios nameserver version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2008/04/22 05:31:29, 0] nmbd/nmbd_subnetdb.c:create_subnets(190)
  create_subnets: No local interfaces !
[2008/04/22 05:31:29, 0] nmbd/nmbd_subnetdb.c:create_subnets(191)
  create_subnets: Waiting for an interface to appear ...
/

any help?

---

### Post by koenn on 2008-04-22
looks like nmdb thinks you have no network interfaces up.
what's the output of 
```
sudo ifconfig
```

---

### Post by jabeez on 2008-04-22
> **chili555 said:**
> plus another for ssh.

It's not and there is nothing to iron out. With ssh, it works perfectly. An icon appears on your desktop, you browse folders, drag-n-drop, etc. Frankly, I don't know how to make it any easier.

As was noted above, if you want the folder to stick, the server must have a static IP address. All the desktops, including the server, have static IP addresses here. Being a bit OCD, I even gave them names, like *frankenputer*  and then added them to /etc/hosts:```
frankenputer 192.168.1.101
```Then you can ssh and ping by name and don't have to remember the IP address.



It's not? Funny that, I simply set which folders to share in Windows, go to my Linux box and voila, shared folders!! Using Samba is almost as easy for Linux>Linux, but still only for copying/moving files, not actually using them as if they were locally stored. I use SSH to work on my Myth box, when does said icon appear on your desktop? I use KDE, maybe it's different in Gnome. But after reading your response in comparison to accessing Windows shares, yeah, it most certainly could be easier.....

---

