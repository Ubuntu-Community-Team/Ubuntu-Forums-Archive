---
title: "NFS between two Lucid machines?"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by Shelbsterina on 2010-09-16
I have never done anything relating to setting up a home network before. This is one area in computing I can honestly say I know absolutely nothing about.

I've been trying to get my laptop and desktop to communicate so I can share files. I've tried a few step by step instructions I've found here and other various sites, and nothing has worked. From what I understand, Samba is not the way to go, so I would like help on setting this up the NFS way. I tried Samba, I think, and get an error message something along the lines of "Cannot find share folder". Last night, I could see my desktop's name in the network folder on my laptop, but kept getting that same message. On my desktop, I could briefly see my laptop in network. I got the same error message until my laptop wouldn't appear at all.

I've tried disabling firewall on both machines using a command in terminal. Since that didn't seem to be the problem, I have enabled them both again.

Also, I would like to be able for both machines to share files from one another, but I'd be content with having my desktop as the server only for now. I was also wondering if I would be able to access my external HDD connected to my desktop via NFS.

---

### Post by Charlie-Omega-Nine on 2010-09-16
Hi, I managed to get this set up following malco2001's Guide here:
(though I used gedit instead of vi)

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

I set up each computer as a server and client, and it worked out with no problems.


-C

---

### Post by Shelbsterina on 2010-09-16
Is there another file I need to create? Here's what's going on:



shelby@FluffyGonzales:~$ sudo gedit /etc/exports
shelby@FluffyGonzales:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/24:/files".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: Warning: /files does not exist
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ] 
shelby@FluffyGonzales:~$ sudo exportfs -a
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/24:/files".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: Warning: /files does not exist



Edit: Never mind, sorry. I see that I didn't insert the "#" right before the new bit in /ect/exports

---

### Post by Shelbsterina on 2010-09-16
Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.
cd /
sudo mkdir files

to mount the share from a terminal type

sudo mount server.mydomain.com:/files /files

Note you may need to restart above services:
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart


I'm stuck on this part. How do I know what the name of the server is? Is it the name of my computer? And what exactly is the "name of the share on the NFS server"?

Edit: Alright, I think I got that part. Server is the name of the host computer, right? And those file names are what I'm mounting and to where, correct?  Here's what's happening now:

shelby@FizzyGonzales:~$ sudo mount FluffyGonzales:/home/shelby /home/shelby
mount.nfs: mount system call failed


Both the directory I want to mount, and where I want to mount it have the same name. Should I create a folder in the client specifically for mounting the server?

---

### Post by Shelbsterina on 2010-09-16
I restarted both computers and created a new folder in the client directory, and I'm getting the same error. Both computers are returning this error when I try to mount.

---

### Post by Charlie-Omega-Nine on 2010-09-16
You're right that it's the computer name, but in order to tell the computer what the other computer's name is, you have to edit the /etc/hosts file to provide that info...

so to the bottom of the /etc/hosts file add:

ComputerA    192.168.0.50
ComputerB    192.168.0.51

so that computerA and computerB are the names, and the IPs are as above...

you can get the IP info from "connection information" in the network manager applet on your panel in the top right of the screen (assuming gnome)

though you may want to set manual IP addresses in the network manager from the "edit connections" option in the applet. This will prevent the IPs from changing when you restart your machines.

the last thing you will probably have to do (i hope) is allow the computers access to each other. you can restrict it to NFS, but I usually grant full access as ssh, scp etc. are really useful. so to do that in the policy tab right click in the "Allow connections from host" window and type in the IP address of the other computer and click "add" then "apply policy" (top right on the toolbar).
now you should be able to get a response when you type:

ping computerA

in a terminal window from computerB

then the mount command that you used above will work, provided the folder you are trying to access is specified in /etc/exports on the server machine and you've run exportfs...

I hope this helps

-C

---

### Post by Shelbsterina on 2010-09-16
> 
though you may want to set manual IP addresses in the network manager from the "edit connections" option in the applet. This will prevent the IPs from changing when you restart your machines.

I can't seem to find any options like that when I go to "edit connections".

> the last thing you will probably have to do (i hope) is allow the computers access to each other. you can restrict it to NFS, but I usually grant full access as ssh, scp etc. are really useful. so to do that in the policy tab right click in the "Allow connections from host" window and type in the IP address of the other computer and click "add" then "apply policy" (top right on the toolbar).

I can't find where this is, either. I tried looking in everything that has anything to do with "network".

Edit: I am getting information when I ping each computer. However, when I type the command for my laptop on my desktop, the information is ongoing. But for my desktop on my laptop, I get a single line of information and nothing more.
Could this have to do with the fact that my laptop is using a wireless connection, and my desktop is not? Forgive me if this is a silly question, as I've said, I know absolutely nothing about networking. Maybe I'll enroll in some networking classes at school next semester, haha

---

### Post by Charlie-Omega-Nine on 2010-09-16
the "edit connections" is a separate option from "connection information" when you right-click the applet.

you can also get to the same place by going through system -> preferences --> Network connections

then you select the appropriate tab (wired/wireless)
highlight your connection (probably something like "Auto eth0" if it's wired or "Auto wlan0" if it's wireless.
and press edit on the right side, then click the IPv4 Settings tab
choose "manual" as the method, and copy the information from the "connection information" window in the applet for address, netmask, gateway and DNS servers (if you have more than one DNS server you can separate them by commas (e.g. xxx.xxx.xxx.xx1, xxx.xxx.xxx.xx2) you can leave search domains blank.

for the "address" section it is a good idea to stay away from the IP range set by your router (generally 192.168.x.100 - 192.168.x.200) I have mine set to 192.168.x.10 for computerA and 192.168.x.11 for computerB) where the x is whatever your router uses.

for firewall configuration, firestarter is not installed by default so you will probably have to ```
sudo apt-get install firestarter
```

and it will appear in System --> Administration --> Firestarter
or you can type ```
firestarter
``` from the terminal window.

it looks like the laptop firewall is probably ok, but the desktop one is blocking the laptop's access so it'll need the (desktop) firewall to be opened up to it (the laptop). The wireless / wired thing shouldn't matter so long as they are connected to the same router. I don't know if classes are necessary it just takes a little trial and error sometimes to see where the snag is :)

let me know how it goes -- I hope i haven't left anything else out... 

-C

---

### Post by Shelbsterina on 2010-09-16
I disabled both firewalls with "sudo ufw disable", installing firestarter didn't want to work on my computers for some reason, but I assume it's just the same.

I tried editing the IPs to be manual as you said, but that caused both computers to be unable to establish a connection to the internet.

Now when I try to mount I get this:

shelby@FizzyGonzales:~$ sudo mount FluffyGonzales:/home/shelby /home/shelby
mount.nfs: DNS resolution failed for FluffyGonzales: No address associated with hostname

Am I forgetting something in this command anywhere?

---

### Post by Charlie-Omega-Nine on 2010-09-16
that error message is probably because the /etc/hosts file is pointing to the old IP address, if you update that to the new, manually set address it should work.

some other things to consider:

when you put in the manual ip address the first three numbers (192.168.1) must be the same as the ones automatically assigned by the router, and the last number must be unique on the network or else you will wind up with problems down the line :). For example: my original IP was 192.168.1.101 and I changed it to 192.168.1.10.

It's a little strange that they can't see the internet anymore -- just until it gets going, it might be easier to set the addresses back to Automatic (DHCP) and use the mount command with IP addresses rather than hostnames... then you should be able to change one thing at a time to make it work. (e.g. set up the manual IP addresses after, and hopefully not break the internet connection). it's more work, but probably safer.

just to try things out, you should make a safe mount point, generally these are placed in /mnt/<something> or /media/something (if you want it to appear on your desktop) so you don't accidentally hide important files that you are working on or config files in the home directory

I have mine set up at /mnt/music

and the command to mount it is ```
sudo mount 192.168.1.10:/home/myself/Music /mnt/Music
```

by editing /etc/hosts to include the line at the end:

```
192.168.1.10    serverbot
```

I can modify that command to be 
```
sudo mount serverbot:/home/myself/Music/mnt/Music

```

depending on what you are trying to do, there may be an easier way to get this sorted out... 

if all you need to do is share a single folder across computers you can right click on that folder and select "sharing options" from that menu, then click "share this folder" and give it a name etc... then you should be able to see it in Places --> Network on the other computer ( though the two computers will have to be able to "see" each other on the network, so they will need to get that ongoing 

```
64 bytes from 192.168.1.10: icmp_seq=1 ttl=64 time=11.2 ms

```
message (which you can end with ctrl-c on the terminal)


-C

---

### Post by Shelbsterina on 2010-09-16
Oh my goodness, replacing the computer names with their IP addresses definitely worked! I have been working on this anytime I'm not at school or work for the past three days, and literally ALL day today. I was about to give up. Thank you so much!

Could I use this same method for my external hard drive connected to my desktop, so I can access those files on my laptop?

---

### Post by Charlie-Omega-Nine on 2010-09-16
Yeah, it should work, so long as you put the path to the external drive in /etc/exports.

---

### Post by Shelbsterina on 2010-09-16
Awesome. Again, thank you so much. This was beginning to look hopeless. That's why I love Linux and Ubuntu, always something new to learn, and always someone willing to help. I made the switch two years ago and I still consider myself a beginner. I don't know what I'd do without this place.

---

