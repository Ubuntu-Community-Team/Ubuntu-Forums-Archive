---
title: "networking"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Bigadada_saba on 2008-01-11
can someone explain to me how to network 2 or more Ubuntu systems together so that they can see each other and communicate to each other using Ubuntu.

---

### Post by chewearn on 2008-01-11
> **Bigadada_saba said:**
> can someone explain to me how to network 2 or more Ubuntu systems together so that they can see each other and communicate to each other using Ubuntu.

Simplest way, just connect them together with a cross ethernet cable.  Find out the IP address and use ping command to see if they can "see" each other.  

Then, enable "Share Folder".

Further set-up will take more explanation, just try the cable connection first; once ping is ok, post back with your ifconfig for both PC.

---

### Post by pytheas22 on 2008-01-11
If you mean you want to create a shared folder available to different Ubuntu machines on your network, just click on System>>Administration>>Shared Folders, install the file sharing packages that it will probably prompt you to install, and from there it should be pretty intuitive.

If you're talking about using remote desktop, take a look at [http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/)

or possibly

[http://ubuntuforums.org/showthread.php?t=314697](http://ubuntuforums.org/showthread.php?t=314697)

---

### Post by Herman on 2008-01-11
Sure, it's easy, I use SSH Networking, which is nice and secure and easy to set up too.
I'm working on a web page about it for helping people get started with it as quickly and as simply as possible.
I want to improve the web page, so if you want to try it out and you have any comments on how I can get the web page any simpler, please let me know.
I've been using SSH networking for years now in my home LAN without any security issues at all, or any problems whatsoever.
I don't know how many other people use it, but I don't know why anyone would want anything else. I haven't really tried the other kind though.
Anyway, here's the link, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")** :**Secure Linux Networking,  easy to set up too                           

Regards, Herman :)

---

### Post by Herman on 2008-01-11
After reading that cool link from pytheas22 about vncviewer, maybe my way is a little old fashioned and slow after all. 
I didn't know it could be done that easily.
That way would be good for a lot of people because most people now have a hardware firewall in both their broadband modem and their router, so it might be all you need if it's just for inside you home LAN.

I'm curoius about what AstalaVista was going to say next too, I wish now I had waited instead of jumping in here. 

I see there's another thing called 'tight vnc', which uses vcn and ssh or ssl combined, for more security.

Can anyone tell me the pros and cons of using vcnviewer? It must be secure enough if it comes bundled with Ubuntu.

Looks like I'll have to try it out.

---

### Post by chewearn on 2008-01-11
> **Herman said:**
> After reading that cool link from pytheas22 about vncviewer, maybe my way is a little old fashioned and slow after all. 
I didn't know it could be done that easily.
That way would be good for a lot of people because most people now have a hardware firewall in both their broadband modem and their router, so it might be all you need if it's just for inside you home LAN.

I'm curoius about what AstalaVista was going to say next too, I wish now I had waited instead of jumping in here. 

I see there's another thing called 'tight vnc', which uses vcn and ssh or ssl combined, for more security.

Can anyone tell me the pros and cons of using vcnviewer? It must be secure enough if it comes bundled with Ubuntu.

Looks like I'll have to try it out.

Actually, vncviewer (and default ubuntu remote desktop) is unfortunately not secure.  The login is hashed, so it was not transmitted in the clear, but the session data is not encrypted.  Therefore, it is only suitable for internal network.

The tightvnc (vnc in ssh) is secure for internet access, but the drawback is it does not open your current desktop that you see locally.  Instead, it create a second session.  So, any open graphical applications running on your local desktop cannot be view remotely.  Conversely, any remote apps that you launch does not appear in the local desktop.

A more complicate set-up is VPN to establish the secure remote link to your local lan, then use vncviewer.  But this is something I have not tried before.

---

### Post by Herman on 2008-01-11
> Actually, vncviewer (and default ubuntu remote desktop) is unfortunately not secure. The login is hashed, so it was not transmitted in the clear, but the session data is not encrypted. Therefore, it is only suitable for internal network.

The tightvnc (vnc in ssh) is secure for internet access, but the drawback is it does not open your current desktop that you see locally. Instead, it create a second session. So, any open graphical applications running on your local desktop cannot be view remotely. Conversely, any remote apps that you launch does not appear in the local desktop.:) Oh, I see, thanks AstalaVista, so if I have an LAN with a hardware firewall in the broadband modem and another hardware firewall in my router, it is safe for me to use vcnviewer while my entire LAN is connected to the internet? 
Would the hardware firewalls be enough to protect me?
Or is it recommended to unplug from the internet while vcnviewer is in use?

My wife uses Frostwire a lot, she loves it, and of course, other people from the internet are able to come in through the two firewalls somehow in order to access my wife's Frostwire share folder. 
Does that mean  they can also access any other box with an open port?

I want to try out vcnviewer for myself, the linked article from pytheas22 explains how to enable it at the server, but it doesn't say how to connect to it from the client. Am I missing something? I'll probably figure it out pretty soon if I keep trying, but any tips would be appreciated.

Regards, Herman :)

---

### Post by chewearn on 2008-01-11
> **Herman said:**
> :) Oh, I see, thanks AstalaVista, so if I have an LAN with a hardware firewall in the broadband modem and another hardware firewall in my router, it is safe for me to use vcnviewer while my entire LAN is connected to the internet? 
Would the hardware firewalls be enough to protect me?
Or is it recommended to unplug from the internet while vcnviewer is in use?

It is not necessary to disconnect internet, if the firewall is properly set-up (which should be the case), all access from internet side is block, except those you specifically allow.


> 
My wife uses Frostwire a lot, she loves it, and of course, other people from the internet are able to come in through the two firewalls somehow in order to access my wife's Frostwire share folder. 
Does that mean  they can also access any other box with an open port?

I'm not familiar with Frostwire, and I'm not sure how it's opening the firewall, so that internet users can access your wife's computer.  Normally, you need to manually open specific ports in your firewall configuration.


> I want to try out vcnviewer for myself, the linked article from pytheas22 explains how to enable it at the server, but it doesn't say how to connect to it from the client. Am I missing something? I'll probably figure it out pretty soon if I keep trying, but any tips would be appreciated.


ALT+F2 at the client side, then:
```
vncviewer <xxx.xxx.xxx.xxx>  # note: ip-address
```

---

### Post by Herman on 2008-01-12
Hey, cool AstalaVista, I have it working now, this is really fun! :) It could be very useful too.
Thanks pytheas22 and thanks AstalaVista ! That's neat! 
Regards, Herman :)

---

### Post by kamicosmos on 2008-01-12
I am having the same issue as the OP.  I find it ironic that when I had 1Ubuntu 7.10 PC and one WinXP PC, samba se tup and worked just fine without any intervention from me, and the two PC's could casually browse each other's shared folders.  But, now that I have 2 7.10 PC's on the same network, I can't for the life of me figure out how to get them to see each other's shares!  I set up a test shared folder on each PC, and installed the samba and unix file sharing stuff that Ubuntu prompted me to do, and set the proper hosts and such.  But, when I go into Network, both PC's just see their 'previous life' window versions, but no linux shares.

I can ping them, and I can use VNCViewer to remote into both PCs from each other, and I have the printer shared and that is working.  So, they obviously see and talk to each other on some level.  I do plan on setting up ssh, but .... call me lazy, but I really like having a graphical interface when I'm moving files around between to PCs.

So....what am I doing wrong?
:confused:

---

### Post by Herman on 2008-01-12
SSH will give you a nice graphical interface when used between PCs inside you LAN, it does in my LAN.
I have read that ti doesn't if we use it to connect over the internet though, I haven't tried that yet, I will some day.

Give SSH a try! :)
Let us know how you get along. Any feedback would be welcome.

Regards, Herman :)

---

### Post by chewearn on 2008-01-12
> **kamicosmos said:**
> I am having the same issue as the OP.  I find it ironic that when I had 1Ubuntu 7.10 PC and one WinXP PC, samba se tup and worked just fine without any intervention from me, and the two PC's could casually browse each other's shared folders.  But, now that I have 2 7.10 PC's on the same network, I can't for the life of me figure out how to get them to see each other's shares!  I set up a test shared folder on each PC, and installed the samba and unix file sharing stuff that Ubuntu prompted me to do, and set the proper hosts and such.  But, when I go into Network, both PC's just see their 'previous life' window versions, but no linux shares.

I can ping them, and I can use VNCViewer to remote into both PCs from each other, and I have the printer shared and that is working.  So, they obviously see and talk to each other on some level.  I do plan on setting up ssh, but .... call me lazy, but I really like having a graphical interface when I'm moving files around between to PCs.

So....what am I doing wrong?
:confused:

Well, I was in the same situation sometime ago, and it took a bit of digging to get it working.  For some reasons, samba and NFS doesn't immediately work just by turning it on and sharing folders from GUI.

1. samba (tip from [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605))
After turning on the samba server from GUI, you still need to do this extra step from terminal to get it seen by a samba client:
```
sudo smbpasswd -L -a <user>
```Replace <user> with your log-in username.  It will prompt you for the sudo password, followed by the  smb password; use your log-in password for the smb password.

Then:
```
sudo smbpasswd -L -e <user>
```2. NFS (tip from [https://wiki.ubuntu.com/SettingUpNFSHowTo?action=show&redirect=NFSServerHowTo](https://wiki.ubuntu.com/SettingUpNFSHowTo?action=show&redirect=NFSServerHowTo))
Every time you share a new folder thru NFS, you need to run this command:
```
sudo exportfs -ra
```

---

### Post by kamicosmos on 2008-01-12
Asta:

Thanks.  I tried those commands, and got closer, but it still wasn't wanting to connect.

Herman:
Thanks!!  openssh is exactly what I was wanting!  I got that se tup and working just fine, and now I can transfer files between my two ubuntu PC's..  I wasn't aware that ssh had a GUI, I was under the impression it was just a more secure cmdln version of ftp...

Anyway, thanks to you both!

(Now, back to getting DVDs to rip and burn properly, and get my Creative Zen working.  You know, the essential stuff!  :wink: )

---

