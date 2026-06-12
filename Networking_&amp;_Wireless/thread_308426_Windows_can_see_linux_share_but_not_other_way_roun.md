---
title: "Windows can see linux share but not other way round"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2006-11-28
im trying to share a netdrive from my windows pc to linux pc

No joy, i cant even see the machine in network servers.

Windows on the other hand can access the linux one just fine.

---

### Post by alamba on 2006-11-28
Are you trying to map the drive/share in ubuntu? One way of doing that is places>> connect to server and then choose Samba share and enter the connection details.

A

---

### Post by dgrafix on 2006-11-28
tried that, a message appears saying contents of window could not be displayed.

Before, i had it showing wp as an icon in network servers but something has happened and it has disappeared (not that i could browse it anyway)

---

### Post by alamba on 2006-11-28
Not sure what the problem is. Are you able to access the same share via another Win box? Any error messages in /var/log/messages or /var/log/debug?

A

---

### Post by scxtt on 2006-11-28
have you tried using the (local) IP address of the windows host explicitly?

something like smb:/192.168.1.100/XP_Share [in konqueror or nautilus, if 192.168.1.100 is the IP address of your XP host?]  there's certain ports that allow the "neighborhood network" browsing [135-137, i think] -- it's always 50/50 for me seeing shares like that ... but specifying the IP is 99% effective :D

---

### Post by cdinoz on 2006-11-28
I too am having issues with Ubuntu no connecting to my Windows network - I can see my Linux box in windows - but not the other way around.

Can someone explain in easy to understand jargon how to get my Ubuntu box to connect to my Windows box (running Edgy) ](*,)

---

### Post by stickboy2642 on 2006-11-29
There are a couple of things to check.  First off, can you connect to the share from another Windows box?  If not, then it could be that Windows Firewall is blocking network shares (would allow you to connect to shares on other machines, but you won't be able to connect to shares on that machine).  Also, check to make sure that file and printer sharing is in fact installed.  I don't think you would even be able to create the share if this was the case, but not 100% sure on that.

As suggested before, try connecting via the IP address.  Sometimes linux has problems with netbios and is not able to connect via name.  Using the IP address usually works.

Also, do you have smbfs installed?  You usually have to install that before you will be able to connect to the shares.  I am assuming since you say you can see the linux box from windows that it is there, but it's maybe something to check.  :-)

```

sudo apt-get install smbfs

```

---

### Post by namich on 2006-11-29
> **dgrafix said:**
> im trying to share a netdrive from my windows pc to linux pc

No joy, i cant even see the machine in network servers.

Windows on the other hand can access the linux one just fine.


I have been having the same problem on a new Edgy install I did a few days ago.Determine to solve this problem this is what i did:

I installed the SmbK4 package and configured it, with the admin acount username and password of my windows machine.By default, Edgy uses Firefox 2.0 as the prefered web -browser.

To browse to you windows share,you have to use conquerer web browser. For some strange reason the firefox browser would not allow me see my windows share.However when I open Conqueror web browser,one of the desktop option is "network folder".Click on this link, then click "Samba shares". This takes you to your workgroup, from there the machine hosting the share.Accessing the shared folder on the hosting machine would require you to input the Username and Password for the Windows machine.Once you have correctly meet these requirements, all your shared data should be visible and accessable.

---

### Post by dgrafix on 2006-11-30
its strange sometimes its there but not other times. Hitting the ip seems to work no problem.

Couldnt find that smbk4 thingy. Mabe cos Im still on dapper (as it hasnt said an upgrade is available under update manager and i DONT want to re-configure my entire machine, as its been working perfectly for ages (except for this problem))

---

### Post by dckirba on 2006-11-30
I have a similar problem.

Our proxy server is also our file sharing server. It's also what we use to print.

I was able to find it when I browsed for a printer and I can print with no problem. I can also browse the internet - no problem.

However, I cannot access the files on the computer. Can't even see it when I browse the network.

I tried the IP address thing and it doesn;t work...

I'm in the process of installing smbfs. 

Cheers,
David K

EDIT: I was able to connect by doing the following:

- Connect to server
- Choose custom location
- Enter smb:/IP address of windows share

Forgive me if this is what you meant by 'use the IP address' all along :)

Cheers,
David K

EDIT 2: I think it was the smbfs plugin that made it worked because now I can browse the network and see all the other computers (windows) on the network with no problem. This is a bit confusing because before we installed the proxy server at office I was still able to see other windows computers in the network...?

---

