---
title: "Setting up a home network...how?!"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by Dunchillin on 2010-05-26
I am trying to set up a home network between an Ubuntu pc and a Windows pc.  Is this possible?  I have been reading the Ubuntu pocket guide which seems to say it is possible, but also seems to say it should happen automatically, which it hasn't.

I'm pretty slow at understanding all the techspeak that goes on, though I do know how to use terminal after a fashion and synaptic, so I'm wondering if some wonderful person out there could give me an 'idiots guide to setting up a network', laymans terms and all!

Please pretty please? :)

---

### Post by Nythain on 2010-05-26
depends on what you mean by a "network"

---

### Post by Dunchillin on 2010-05-26
I want to be able to share files between the two computers.  Unfortunately I still have to run a windows comp for photoshop and dreamweaver, and want to be able to transfer files quickly rather than the horrible process I have now of saving to memory stick, unmounting, plugging in, copying to the right file, unmounting, unplugging... driving me crazy!!

---

### Post by lisati on 2010-05-26
One way is to connect both computers to a router (either with ethernet or Wifi, or both) and have Samba running on your Ubuntu machine(s).
A tutorial I've found helpful in the past can be found here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by jerome1232 on 2010-05-26
Right click the folder you want shared, check Share this Folder, allow it to install service and change the permissions. You will probably need to log out then log back in for a few settings to take affect.

If you click Places->Network->Windows Network->YourWorkgroupHere-> you should see a list of shares on your network.

If you don't see it you need to a) share something from your windows box and b) set the windows computers firewall to allow windows file and printer sharing.

Both computers should be able to see each other.

---

### Post by gandaran on 2010-05-26
> but also seems to say it should happen automatically
and it does, just mark the folder to share over the network? do the same on the windows computer, then you should find it (the windows shared folder) in places/network/windows network/workgroup  or whatever you name your windows network.

---

### Post by 3rdalbum on 2010-05-26
The Ubuntu Help program (System > Help And Support) has directions for setting up a shared folder on Ubuntu. I imagine if you want the shared folder to reside on the Windows computer instead, you'd need to find a HOWTO for setting up folder sharing on Windows.

---

### Post by Dunchillin on 2010-05-26
I love this site, you're all very helpful!

I'm getting there.  I've got the 2 comps plugged into my broadband modem and have successfully accessed files from my windows comp on my ubuntu comp. I haven't managed the other way yet though.  Have shared the folders I want to share on Ubuntu but can't find them on windows.  Anyone game to give me windows advice?! :eek:

---

### Post by gandaran on 2010-05-26
> **Dunchillin said:**
> I love this site, you're all very helpful!

I'm getting there.  I've got the 2 comps plugged into my broadband modem and have successfully accessed files from my windows comp on my ubuntu comp. I haven't managed the other way yet though.  Have shared the folders I want to share on Ubuntu but can't find them on windows.  Anyone game to give me windows advice?! :eek:

on windows XP, go to any open window menu bar » tools » connect to network » open search box, you should be able to locate the network you created and shared folders, select the shared folder give it a drive letter so you can access the folder from 'My Computer' 
don't know about vista or seven but must be more or less the same, just look for your network and search for the shared folders and printers too.

---

### Post by Objekt on 2010-05-26
> **lisati said:**
> One way is to connect both computers to a router (either with ethernet or Wifi, or both) and have Samba running on your Ubuntu machine(s).
A tutorial I've found helpful in the past can be found here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I'm not sure that walkthrough is still applicable, as it hasn't been updated since 2006.

I have one computer running Windows 7 Ultimate and one running Ubuntu 9.10.  I have NO idea how to configure Samba or whatever it is I need to share files between the two (Samba?  NFS?  Something else?).

Adding to the complication, the Windows 7 machine sometimes runs Windows XP.  I would like to be able to exchange files between it and the Ubuntu desktop in that situation also.

I also want to access files on the Ubuntu desktop from my netbook, which runs Ubuntu Netbook Remix 9.10.  In fact that would be pretty awesome, because then I could watch DVDs residing on my Ubuntu desktop from the netbook, without the lengthy process of copying 4 to 8 GB image files.

Expanding on that, is there some way I can set up a "generic" share on the Ubuntu desktop, so that any computer connected to my home LAN can access the shares residing on it, without having to reconfigure the client & desktop every stinking time?  For instance, I would like to have people visting my house, who brought their own computer, able to read files from my Ubuntu desktop.  It would be best if they could do so after a simple login of some sort, without going through an hour and a half of configuration & rebooting nonsense.

Simply designating the desired folders as "Shared" in Nautilus on the Ubuntu desktop doesn't work.  I don't have the slightest idea where to go from here.

---

### Post by sandyd on 2010-05-26
```
sudo apt-get install system-config-samba && gksudo system-config-samba
```. go to edit -> server settings, and change the workgroup to the same workgroup you have in windows. click ok, and the click the "+" sign. set the directory, and in the second tab, choose allow access to everyone. then, in the first tab, make sure the "writable" and "visible" boxes are checked. click ok and restart

---

### Post by Objekt on 2010-05-26
Windows 7 doesn't have "workgroups," it has "Homegroups."  According to Microsoft ([http://technet.microsoft.com/en-us/library/ee449408%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/ee449408%28WS.10%29.aspx")), only other Windows 7 machines can be in a Homegroup.  So I have no idea what "workgroup" name to use.

---

### Post by bredman on 2010-05-26
To access an Ubuntu share from a Windows PC...

On the Ubuntu machine, check the name of the share, you can see this by right-clicking on the shared folder and selecting "Sharing Options". In my case, the share name is "public".

On the Ubuntu machine, open the terminal (Ctrl-Alt-t) and enter the command
ifconfig
to find the IP address of the Ubuntu machine. In my case, it is 192.168.1.20.

On the Windows machine, open a Windows Explorer, and enter the following in the address bar
\\192.168.1.20\public
(remember to change it to suit your Ubuntu machine)

If you like this method, you may wish to set a hostname on the Ubuntu machine instead of having to find the IP address each time.

---

### Post by Objekt on 2010-05-26
That doesn't work.  I put in the IP address and share name on the Windows 7 machine, but it just opens a Web browser.  The browser gets an error message as if the share didn't exist.  It DOES exist, because I very carefully shared the folder in Samba Server Configuration, making sure I set it as "visible" and "Allow access to everyone."

The most I can get is the default Apache "It Works!" page, by entering the Ubuntu machine's IP address in the Windows 7 machine's browser.

The Ubuntu machine is not showing up anywhere in the Windows 7 machine's networking stuff.  I don't even see the "MSHOME" workgroup that Samba should be creating on the network.

---

### Post by gandaran on 2010-05-26
> **Objekt said:**
> That doesn't work.  I put in the IP address and share name on the Windows 7 machine, but it just opens a Web browser.  The browser gets an error message as if the share didn't exist.  It DOES exist, because I very carefully shared the folder in Samba Server Configuration, making sure I set it as "visible" and "Allow access to everyone."

The most I can get is the default Apache "It Works!" page, by entering the Ubuntu machine's IP address in the Windows 7 machine's browser.

The Ubuntu machine is not showing up anywhere in the Windows 7 machine's networking stuff.  I don't even see the "MSHOME" workgroup that Samba should be creating on the network.
maybe the windows firewall is blocking the network!

---

### Post by jerome1232 on 2010-05-26
Did you log out and log back in after sharing the folder? Do you have a firewall running in Ubuntu?

You also don't have to be in the same whatevertheycallitnowgroup, Windows will show all whatevertheycallitnowgroups it can find on the network, as will Ubuntu.

---

### Post by Objekt on 2010-05-26
Yes, I've restarted a couple of times since making the changes.

Not running any firewalls on the Ubuntu machine.  It is patched with everything current as of today, except for the kernel.  I run a realtime kernel (2.6.31-9-rt).

---

### Post by VastOne on 2010-05-26
> **Objekt said:**
> Yes, I've restarted a couple of times since making the changes.

Not running any firewalls on the Ubuntu machine.  It is patched with everything current as of today, except for the kernel.  I run a realtime kernel (2.6.31-9-rt).

Open Windows explorer and navigate to your Computer

Click on Map Network Drive

Put in \\192.168.1.whatever your ip is\share name on Ubuntu

Click to reconnect at login

If you have shared the folder in Ubuntu, this will work.

---

### Post by Objekt on 2010-05-26
That almost works.  If I enter, for example:

```
\\192.168.1.10\objekt910-desktop[HTML][/HTML]
```

I'm prompted for a username and password.  But, nothing works.  I tried my usual Ubuntu username and password, no dice.

Also tried this:

```
\\192.168.1.10\dvds
```

because "dvds" is the literal name of the folder I'm trying to share from the Ubuntu machine.  That didn't work either.

---

### Post by MacKennedy on 2010-05-26
I'm not sure about files/sizes and whatnot that you are trying to share, but someone posted this in another thread and I gave it a try since I was having trouble with sharing between the two.
[http://www.dropbox.com/](http://www.dropbox.com/)

---

### Post by Dunchillin on 2010-05-26
All sorted.  You are all extremely helpful, quick and friendly! Thanks again :)

---

### Post by Dunchillin on 2010-05-26
> I'm prompted for a username and password.  But, nothing works.  I tried my usual Ubuntu username and password, no dice.

I found the same thing, but then the username needed turned out to be the workgroup name (in my case 'JOHNS' rather than my username 'john') and the password was the same.

---

### Post by VastOne on 2010-05-26
> **Dunchillin said:**
> All sorted.  You are all extremely helpful, quick and friendly! Thanks again :)

What was the resolution so that others may learn from your experiences, please!

Glad you got it sorted out...:guitar:

---

### Post by Dunchillin on 2010-05-26
First I did this on my Ubuntu computer:
> 
Code:

[QUOTE]sudo apt-get install system-config-samba && gksudo system-config-samba[/quote]

This opened up a Samba box, where I followed the rest of the advice, except the tab was 'preferences', not 'edit' as below:

> . go to edit -> server settings, and change the workgroup to the same workgroup you have in windows. click ok, and the click the "+" sign. set the directory, and in the second tab, choose allow access to everyone. then, in the first tab, make sure the "writable" and "visible" boxes are checked. click ok and restart

Then I did this on my windows xp computer:
> To access an Ubuntu share from a Windows PC...

On the Ubuntu machine, check the name of the share, you can see this by right-clicking on the shared folder and selecting "Sharing Options". In my case, the share name is "public".

On the Ubuntu machine, open the terminal (Ctrl-Alt-t) and enter the command
ifconfig
to find the IP address of the Ubuntu machine. In my case, it is 192.168.1.20.

On the Windows machine, open a Windows Explorer, and enter the following in the address bar
\\192.168.1.20\public
(remember to change it to suit your Ubuntu machine)

If you like this method, you may wish to set a hostname on the Ubuntu machine instead of having to find the IP address each time.

and it all worked well - I can now easily access folders from my windows xp computer on my Ubuntu one and vice versa.  

I did find that some (ubuntu) sub-folders were still inaccessible on windows, but simply followed this same process in Ubuntu with each of them that I wanted access to and hey presto!  As I said in my last post it took a few minutes messing around to realise windows wanted my Ubuntu share group name rather than login name as 'username' but once I sussed that it was all done. I love Ubuntu :D  If it had good photoshop and dreamweaver substitutes available (gimp is crap sorry!) I would obliterate windows from my home and business for ever with glee!

---

### Post by Objekt on 2010-05-28
Still no luck here.

The Ubuntu machine is definitely running SAMBA and is showing up on the network when the Windows machine is running Windows XP.  I understand Windows XP networking a lot better than Windows 7 networking, so I'm going to try to get sharing working in XP first.

Like I said, the Ubuntu machine and its "MSHOME" workgroup (generated by Samba) does show up on the Windows XP machine, under its proper name, which you might have gathered from my cut-n-pastes above is "objekt910-desktop."  But, I can't access anything on it.  If I try, I get an error message.  I'll try to post the exact message later, but it's something to the effect that I "don't have permission" to access anything on ubuntu910-desktop, similar to what you get if you have a Windows XP machine in a network with all sharing turned off.

---

### Post by Objekt on 2010-06-01
FWIW, here is the exact error message I get when trying to access my Ubuntu machine (objekt910-desktop) from Windows XP:

```
---------------------------
Workgroup
---------------------------
\\Objekt910-deskto is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found.

---------------------------
OK   
---------------------------

```

The Ubuntu machine does show up on the Windows XP machine's network view as "Objekt910-deskto" so I guess that's a sign the Samba server is at least making itself a member of the default-named "WORKGROUP" workgroup.  However, I'm wondering why the name is cut off ("Objekt910-deskto" vs. "objekt910-desktop"), and whether that has anything to do with the inability to access the shares that should be showing up.

---

