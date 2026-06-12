---
title: "whi\y is ubuntu so useless at mounting network drives on my computer?"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by madjack on 2007-11-12
it's easy to do in windows - can't do it in ubuntu. No wonder windows is beating ubuntu hands down if it can't even do simple stuff like this

---

### Post by xpod on 2007-11-12
I cant comment on Samba as i`ve never really used it but i dont have any problems mounting nfs shares.

I generally find that when something is`nt going as the howto`s mabey say it should then it`s usually ME who is actually being useless.:wink:

---

### Post by tombott on 2007-11-12
Care to shed any more light on the matter madjack?
I can happily browse to and to connect to Windows shares without any problems.
This includes Windows XP and Windows Server 2003 shares.

---

### Post by madjack on 2007-11-12
> **tombott said:**
> Care to shed any more light on the matter madjack?
I can happily browse to and to connect to Windows shares without any problems.
This includes Windows XP and Windows Server 2003 shares.

Well, I really just need to find out how to do it. Everything I have seen so far tells me to install smbfs - but that won't install. 
Also everything seems very windows oriented - I want to connect to a ubunto drive, not a windows drive.

here is what I get when I install smbfs

chris@work-laptop:~$ sudo apt-get install smbfs smbclient
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package smbfs has no installation candidate

---

### Post by tombott on 2007-11-12
Well for Ubuntu to Ubuntu file sharing I just use Samba.

To set samba up I just right click on a folder and select Share Folder.
This then prompts you to install samba.

Once installed you need to set a samba user and password.

Enter the following in a terminal

sudo smbpasswd -a *username*

Replacing username with your desired samba user


More info [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service")

---

### Post by madjack on 2007-11-12
> **tombott said:**
> Well for Ubuntu to Ubuntu file sharing I just use Samba.

To set samba up I just right click on a folder and select Share Folder.
This then prompts you to install samba.

Once installed you need to set a samba user and password.

Enter the following in a terminal

sudo smbpasswd -a *username*

Replacing username with your desired samba user


More info [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service")


thanks, I've done that on the server - now how do I actually connect from the client ?

---

### Post by tombott on 2007-11-12
Places - Network
then browse to your share

---

### Post by rumli on 2007-11-12
> **madjack said:**
> thanks, I've done that on the server - now how do I actually connect from the client ?

Open a Nautilus window, press CTRL-L to get to the address line, and type "smb:///" (without the quotes) and then press ENTER.

See the attached screenshot.

---

### Post by madjack on 2007-11-12
> **tombott said:**
> Places - Network
then browse to your share

How do I browse to it? - I've opened places-network, but I don't see the drive

---

### Post by madjack on 2007-11-12
> **rumli said:**
> Open a Nautilus window, press CTRL-L to get to the address line, and type "smb:///" (without the quotes) and then press ENTER.

See the attached screenshot.


nope - still don't see anything

---

### Post by rumli on 2007-11-12
> **madjack said:**
> nope - still don't see anything

Is everything on a LAN?  Did you make sure that the server machine has a static IP address?  Can you successfully ping the server from your client machine?  To ping your server, open a terminal on your client and type:
```
ping 192.168.x.y
```
where 192.168.x.y is your server static IP address.

---

### Post by madjack on 2007-11-13
> **rumli said:**
> Is everything on a LAN?  Did you make sure that the server machine has a static IP address?  Can you successfully ping the server from your client machine?  To ping your server, open a terminal on your client and type:
```
ping 192.168.x.y
```
where 192.168.x.y is your server static IP address.

yes, I can ping everything.

---

### Post by rumli on 2007-11-13
What about trying to enter the server's IP directly into Nautilus?  Type:
```
smb://serverIP
```
in the Nautilus locations bar (accessed by pressing CTRL-L)

---

### Post by madjack on 2007-11-13
> **rumli said:**
> What about trying to enter the server's IP directly into Nautilus?  Type:
```
smb://serverIP
```
in the Nautilus locations bar (accessed by pressing CTRL-L)

Yes, that works! - why can't I see the icons in network places ?

---

### Post by tombott on 2007-11-13
I've no idea, it just works on mine.
Maybe you changed something whilst trying to get smbfs to work.
You can create shortcuts to your shares onto your desktop though.

---

### Post by AgentZ86 on 2007-11-26
> **madjack said:**
> it's easy to do in windows - can't do it in ubuntu. No wonder windows is beating ubuntu hands down if it can't even do simple stuff like this

Windows isn't beating Ubuntu handsdown your just confused.

How is windows beating Ubuntu hands down, If Windows is the competition then Ubuntu beats the competition hands down, but I guess it depends on your perception.

If Windows costs lets say $200 for just the OS, and no office stuff, and no virus protection and vulnerable on the net, And Ubuntu is free, or free to donate, and has all that and lots more. Where does Windows beat Ubuntu, I'm not seeing it.

If your talking about compatiblity then it also depends on what ? 

Ubuntu compatible with windows ? well I guess windows would be more compatible with itself. So thats not really a comparison either.

In anycase just browse the network to your shares and once you get there go to file/connect to sever and boom that will put a desktop share on your desktop, 

Note: that the shortcut does not like file names with spaces so you have to edit the connect to server once you get to that point, So if you see something like Daily$20%Files or some folder like that, basically you need to get rid of the $20% etc. so that it reads Daily Files.
But anyhow it's simple I use my Server with Samba (meaning Windows shares) and host my images for ebay etc. Very simple very easy, but like anything it's simple if you know how.

I hope this helps.

---

### Post by AgentZ86 on 2007-11-26
> **madjack said:**
> Yes, that works! - why can't I see the icons in network places ?

You should see the icons in network places ?

Do you see anything in network places ? Like an icon that says Windows Network or anything at all ??

Please advise.

---

### Post by Wharf Rat on 2007-11-26
> **madjack said:**
> Yes, that works! - why can't I see the icons in network places ?

Are both of your machines using the same GROUP Name?  i.e.  MSHOME

---

