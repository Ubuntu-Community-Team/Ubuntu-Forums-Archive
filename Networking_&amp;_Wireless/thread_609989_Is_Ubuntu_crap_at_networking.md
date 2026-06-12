---
title: "Is Ubuntu crap at networking?"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by Wesley on 2007-11-11
Hi guys

I got XP Pro running as server, got few folders shared. Got Ubuntu 7.10 on my laptop, got Samba installed, changed the workgroup MSHOME to WORKGROUP, no matter what i do, it will NOT show up the shared folders from the XP server. 

i can connect the XP server with RDC from Ubuntu no problem, but browse networking, will NOT show up at all. 

can see windows network icon in network manager thingy but when go inside, nothing......

what did i do wrong? 

thanks :)

---

### Post by Fire_Chief on 2007-11-13
Well, actually Windows is pretty bad at standalone networking (not in a Active Directory domain). It uses broadcasts at timed intervals to publish its share info. You would think that systems would broadcast requests for who's sharing what when they "browse" the network. It is not done this way to prevent a storm of broadcasts and replies over the network.

Try browsing to the IP of the Windows system from your Ubuntu box
smb://*ip address*/

---

### Post by rabideau on 2007-11-13
You could also try reading this thread:)

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by nickpaton on 2007-11-25
> **rabideau said:**
> You could also try reading this thread:)

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Yup, this HOWTO by Stormbringer is the one which I've used for ages and always works out of the box.

A slight change to [Files] section of smb.conf I now use is:

```
[Files]
    path = /home/nick/Public
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user =
    force group = 
    available = yes
    public = yes
    writable = yes
    browseable = yes
``` 

This example links to the existing Public folder within my Home directory - change accordingly or make a new folder.

Also if you don't want to have to have to enter a username and password within Windows, in smb.conf change 

```
security = user
```

to

```
security = share
```

Some other tricks you can do.
You can add multiple folders for the remote XP PC to link to, simply by adding more 'Files' as follows:

```
[Ubuntu Home]
    path = /home/nick/Public
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = nick
    force group = nick
    available = yes
    public = yes
    writable = yes
    browseable = yes

[OS Share]
    path = /media/hda5/Master
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = nick
    force group = nick
    available = yes
    public = yes
    writable = yes
    browseable = yes

```

The first one is the same as the top example, except I've changed the name from [Files] to [Ubuntu Home].

The second one (which I call [OS share] on my Gutsy PC) shows how you can link to another hdd or partition.  
To link to the whole of the hdd contents, make a top level folder, which I've called here 'Master', and put every other folder into that one.  
I believe I'm right in saying that Samba cannot link just to a hdd so you need to create such a folder. If an expert thinks this is wrong please tell me & I'll modify accordingly!

The next major thing to remember is to always restart Samba whenever you have gone into the smb.conf file, using the command in Stormbringer's HOWTO.

Having done that, test smb.conf as follows:

Alt-F2 keys.  This brings up a command terminal type box.

Type:

```
smb://localhost/
``` and Enter.

This will list all the folders which are available for networking to your XP PC.  
If you see a folder not listed or listed incorrect for any reason, simply modify smb.conf, restart it, and Alt-F2 and the command again to recheck.

Remember too to restart your XP PC whenever you make changes to smb.conf.

Finally and very important - your firewall settings:

In my experience, the major reason for not being able to network to another PC, is that the Ubuntu firewall has not been set up.

Ubuntu has a built in firewall, and its settings are available using Firestarter.
If you have not already installed Firestarter:

```
sudo apt-get install firestarter
```

Once installed open it via System > Adminsitration > Firestarter.  Follow the installation Wizard to set it up.
Initially I would suggest disabling Firestarter by clicking on the Stop Firewall button.

Once you've got the network working with your XP PC, set up the firewall as follows:

Ideally you should have a static IP address for your Gutsy PC, or at least working within a small range of possible IP addresses if it is dynamic.  
Note the static or dynamic IP address range. 
To set up Firestarter:
Policy > Inbound Traffic Policy tab > Click within 'Allow Connections from host' box.
Click green 'Add Rule' icon. 
For static IP address, type in the IP address of your Gutsy PC.
Click 'Add' button.  This will insert the rule into the main box.
Click green 'Apply Policy' icon.  This sets the rule in stone.
If you have a dynamic IP address, repeat this for every possible IP address in the range.

That's it!

There's a great [video tutorial]("http://www.youtube.com/watch?v=Ad17kma8rNM") (for 6.10 but still applies for 7.10) on how to set up Samba and includes some further excellent tips and tricks.

Nick

---

### Post by The Pinny Parlour on 2007-11-25
Yes

---

