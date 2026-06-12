---
title: "[SOLVED] Need help setting up a wired network"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by lrs52200 on 2008-10-27
Hi everyone.  I'm brand new at this and don't want to mess it up.  Not very familiar at all with Linux, but I know where the terminal is and can type in whatever you tell me to....

Here's my situation.  I just installed Ubuntu 8.04 on 3 of my machines.  The other still has WinXP Home SP3 (and he won't let me install Ubuntu on it).  Prior to the Ubuntu install, our wired network was already set up.  Now that I've got Ubuntu on 3 of the 4 machines, I'm wondering how to make the network work.  Everything is still wired, but when I go to System> Administration> Network, all I see is the Network Settings Window with "wired connection" ticked.  It doesn't list anything under "Location."  Going to the General tab, it shows my host name as: pamela-desktop.  There is no domain name listed.  Moving on to the DNS, there are 2 sets of numbers there, as well as "hvc.rr.com" under 'search domains.'

I connect to the internet via road runner, using a Linksys router, model WRT546.  I downloaded Samba because I read somewhere in the forums that I will need that to allow the WinXP computer to use my printer.  

The network printer is on my machine (Ubuntu).

I need someone to walk me through (or direct me to a page) that will tell me how to get our computers to see each other, as well as to allow them to use my printer.  I've read so much on this forum as well as google pages, but most of what is written seems to be for people familiar with linux - and I am not.  

I do not know how to find my:  domain name, host name, server name, or domain/workgroup - and I know I need that to set this up.  I know my IP & Mac addresses, but that is about it.  So if you have the patience, can you explain this to me?


p.s., I also installed Firestarter, if that makes a difference

---

### Post by pfisher on 2008-10-27
The part you appear to have missed is setting the "properties" of you connection. In "network settings" highlight "wired connection" and click on "properties". The dialog that opens will allow you to configure a fixed IP or select "automatic configuration (DHCP)". The router should default to running as a DHCP server. Unless you have changed you router's configuration, stay with DHCP on your computers.

The router is the device that gets the IP from your provider. The computers on this side of the network will be part of a private network that get their IPs from the router (something like 192.168.1.1xx) if you havn't changed the router configuration). Run "ipconfig eth0" in terminal to see your machine's IP.

Your Firestarter should be configured to allow conections from machines on your network. In Policy > inbound traffic > allow connections from host add 192.168.1.0/24
this will allow all of the other machine on your network to connect.

---

### Post by Iowan on 2008-10-27
Not to dump-and-run, but [here]("http://ubuntuforums.org/showthread.php?t=202605") and [here]("https://help.ubuntu.com/community/SettingUpSamba") are good Samba intro's. [This]("http://ubuntuforums.org/showthread.php?t=288534") is a good How-To for permanent mounting.  **ifconfig** (in terminal) will show [COLOR="Red"]i[/COLOR]nter[COLOR="red"]f[/COLOR]ace [COLOR="red"]config[/COLOR]uration on Ubuntu machine(s). Hostname can be viewed by running **hostname** command (also from terminal).  When you open a terminal, it's likely that the "prompt" will include username@hostname.  Most of the Samba information is in */etc/samba/smb.cfg*.

---

### Post by lrs52200 on 2008-10-27
I must be doing something wrong. I still can't see the other computers, neither can they see me or print from my printer.
I must be inserting the wrong information when I'm trying to set things up.

---

### Post by lrs52200 on 2008-10-27
I've really messed up my daughter's computer.  She cannot connect to the internet, updates, and I am not able to open up the network or network tools in System> Administration.
I must have inserted the wrong information......

Can this be fixed?

---

### Post by blueturtl on 2008-10-27
Ok, this requires multiple things to be in order for it to work.

Firstly, we have to make sure that all the computers on the network connect to the router and get IP addresses. If you're able to access the web on all machines, this is a no brainer (everything ok).

You can try pinging the machines if you know their ip addresses to see if they can send/receive packets from each other. In Ubuntu you do this by opening Applications->Accessories->Terminal and issuing the command:

```
ping 192.168.1.x
```
(where 192.168.1.x is the address of the machine you want to send packets to).

You can interrupt ping by pressing Ctrl+C.

If sending packets is ok, the next step is to make sure that all machines communicate via the same workgroup. The default is WORKGROUP, check that all the machines running Windows XP are using the same workgroup name.
Windows networking relies heavily in this being correct to browse resources.

Ubuntu can now be set up to share resources to this workgroup. You need to install and configure Samba. I assume you've already installed Samba, so now all you have to do is configure it.

All Samba configurations are written in a human-readable file located in
/etc/samba/smb.conf

I recommend you backup this file before modifying it.
To edit the file, type:
gksu gedit /etc/samba/smb.conf

You will be prompted for your password.

Here is my smb.conf for reference.

Bits you may need to change if you use my file as a template are marked in bold font.

```
[global]
# What your machine is called
**   netbios name = your computer's name here!**

# Which workgroup will it join
**   workgroup = name of the workgroup the windows pc(s) are using**

# Additional comment/info
   server string = anything you want

   domain master = no
   local master = yes
   preferred master = yes
   os level = 0

   wins support = no
   dns proxy = no
   name resolve order = lmhosts host wins bcast

# if you have more than one network card or connect wirelessly, you may need to change this
   interfaces = eth0
   bind interfaces only = true

# Typically machines connected to the same router will have IP addresses that are from the same pool (aka only the last number will differ). This setting limits the IP addresses of the machines that can use your shared resources to a an address pool you designate (popular alternatives: 10.0.0.0/24 or 192.168.0.0/24)
   hosts allow = 192.168.1.0/24

   log file = /var/log/samba/log.%m
   max log size = 100
   log level = 2
   syslog only = no
   syslog = 0

   panic action = /usr/share/samba/panic-action %d

# The setting below makes Samba act like a Windows workstation, aka security will be based on if you set a password or not. User authentication won't be used!
   security = share

   passdb backend = tdbsam

# The guest account is allowed access to shares
   guest account = nobody
# You never want people with root privileges accessing your files!
   invalid users = root

   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

   domain logons = no

   load printers = yes
   printing = cups
   printcap name = cups

   socket options = TCP_NODELAY IPTOS_LOWDELAY

[B][readonly_folder_for_share]
   comment = Photo gallery
   path = /path/to/folder
   browseable = yes
   writable = no
   public = yes

[folder_anybody_could_write_in]
   comment = Sandbox full-rights share
   path = /path/to/folder
   browseable = yes
   writable = yes
   public = yes
   create mode = 664
   directory mode = 775
   group = users[/B]

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

```

After editing the file and saving it, you can restart Samba by issuing
sudo /etc/init.d/samba restart

It may take a while after this before the Windows machines pick up yours.
Ask away if you need more help, or if you need me to clarify something!

---

### Post by blueturtl on 2008-10-27
> **lrs52200 said:**
> I've really messed up my daughter's computer.  She cannot connect to the internet, updates, and I am not able to open up the network or network tools in System> Administration.
I must have inserted the wrong information......

Can this be fixed?

If possible you should try to reset the configuration.
Setting up the network for shared resources is not configured in System->Administration->Network, this is used for getting connected to the router/internet.

Please read my post above if you manage to fix the internet connection, it explains how you can share your printer.

---

### Post by lrs52200 on 2008-10-28
Blueturtl-

  Thank you for responding so quickly.........

I'm looking at Gadmin-Samba 0.2.7 - is that what I'm supposed to be using?

Also, I tried to ping the windows machine and the 2 other ubuntu machines - from my (ubuntu) machine, and the only one that doesn't work is the windows machine.  All of the ubuntu machines can send/receive packages.  

What now?

---

### Post by Iowan on 2008-10-28
Check firewall settings on Windows box.

---

### Post by blueturtl on 2008-10-29
> I'm looking at Gadmin-Samba 0.2.7 - is that what I'm supposed to be using?

Gadmin-Samba is a program that will generate the configuration file for you by letting you enter settings via graphical windows and ticking checkboxes. It's really up to you which way you prefer, the configuration file I have provided you with should share your printer just the same as long as you modify the parts I've highlighted.

Does the Windows machine connect to the web ok? If it seems to network fine other than responding to ping your firewall/security suite on the computer may have locked down this function. This does not automatically mean printer sharing shouldn't work! The firewall may refuse ping, but allow for shared folder/printer access.

I suggest that you configure the Ubuntu machine sharing the printer and attempt to add the printer on the Windows machine.

You can backup your /etc/samba/smb.conf by typing the following command into the terminal:

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup

```

Instructions for creating the new configuration file are in my previous post as well as instructions for restarting Samba.

---

### Post by lrs52200 on 2008-10-29
Iowan-

  He's running CA Firewall - but I don't know what to change his settings to.  BTW, he said he doesn't care if he can print off my printer anyway - so do I still have to hook him up for the other computers to be able to print?  Or can I just leave him out?

---

### Post by lrs52200 on 2008-10-29
Blueturtl-

  Thank you agani for responding so quickly.  The windows machine connects to the internet fine.  I am embarassed to say this, but I tried to add the printer on one of the other Ubuntu machines, but I don't know what the port number is.  I have it hooked up on LPT1 on my machine, but apparently I have to enter a port number on the other machines that I'm trying to allow access from.  How do I find out what number it is?

---

### Post by blueturtl on 2008-10-29
> The windows machine connects to the internet fine. I am embarassed to say this, but I tried to add the printer on one of the other Ubuntu machines, but I don't know what the port number is. I have it hooked up on LPT1 on my machine, but apparently I have to enter a port number on the other machines that I'm trying to allow access from. How do I find out what number it is?

The port number Ubuntu is referring to here is the port of the service where Samba is running, and not an actual physical port. You should be able to spesify the printer without the port if everything is in order, at least I don't remember having to ever enter a port number.

When adding the printer in Ubuntu select the
Windows printer via Samba option
and into the text field enter the printer address like so:

smb://workgroup/netbios-name/print

You can also use the button labeled 'browse' which will allow you to click through the workgroup tree and locate the printer. This will automatically generate the required address for the printer. If the browse is not showing any computers or printers then there may still be an issue with the configuration.

I would like to note that while I have done this several times my memory is not flawless. Please forgive me if it turns out I've let something slip my mind. :)

---

### Post by lrs52200 on 2008-10-30
Blueturtl-

  When I typed the following command into the terminal - gksu gedit /etc/samba/smb.conf, the output doesn't look exactly like yours - can you look at it and tell me if I'm editing the correct file, or is that something I shouldn't post here?

---

### Post by blueturtl on 2008-10-31
> When I typed the following command into the terminal - gksu gedit /etc/samba/smb.conf, the output doesn't look exactly like yours - can you look at it and tell me if I'm editing the correct file, or is that something I shouldn't post here?

I did some heavy editing on my own file, so most likely it is different than the unedited file you have. That said, feel free to post yours here. I can go over it with you if you want.

Also -- it happens I'm currently visiting my parents and my little sister has Ubuntu set up to share a printer. If you want, I can post her configuration file here for you. It is a battle tested copy so you should be able to get away with simply replacing your own file with it and have printer sharing instantly working.

Let me know how you want to proceed.

---

### Post by lrs52200 on 2008-10-31
Blueturtl-

---

### Post by lrs52200 on 2008-10-31
Guess what?!  The other 2 Ubuntu machines can now print to my printer!!!!  However, the WinXP machine still cannot.  I try to 'browse' for the network printer, but it still doesn't see it.  It keeps telling me that it is either because no printer is hooked up, or I'm typing in the wrong name of the printer........
Can you help? (that WinXP machine is using CA Security Suite with the firewall)

---

### Post by blueturtl on 2008-10-31
I'm sorry, but I don't know the firewall product you've mentioned. :( You should consult it's documentation to see if it allows for shared services by default or not.

Alternatively you could try just turning it off temporarily to see if it is really the problem. If you can use the printer with the firewall off, then you know that it needs to be configured.

---

### Post by lrs52200 on 2008-10-31
Thank you so much Blueturtl for helping me.  My daughter just came home and is ecstatic!  :)

---

### Post by blueturtl on 2008-10-31
> **lrs52200 said:**
> Thank you so much Blueturtl for helping me.  My daughter just came home and is ecstatic!  :)

Thank *you* and may the spirit of Ubuntu be with you. :)

---

