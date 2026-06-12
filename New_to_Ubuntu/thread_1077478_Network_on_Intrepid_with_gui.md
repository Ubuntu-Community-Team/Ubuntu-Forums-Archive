---
title: "Network on Intrepid with gui?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Beezgetz on 2009-02-22
Hello Ubuntu!

I am fairly new to linux via ubuntu, I started with Hardy, so I'm still fresh...
I am looking for several answers, since Intrepid came out, (I had Video issues, I reinstalled ubuntu, only to find out that all i have to do is turn off visual effects on compiz for any video to work, heh, that was a day well spent)) and I am going solid with shell. Most of the answers I get from our local ubuntu forum community in Slovenia, but this one is a bugger..

Right, I can not access Network. I can see MSHOME and WORKGROUP via file browser, but as I try to access mshome I get this warrning:
Unable to mount location
Failed to retrieve share list from server

I tried Nautilus, but that does not even open network link:
Unable to mount location
Failed to retrieve share list from server


So I was directed to shell.
right, so I looked up smbclient --help and --usage
and I tried smbclient -L , or -B, and here is what I got:

grom@ubuntu-lep-tich:~/Desktop$ smbclient -L
Usage: smbclient [-?EgBVNkPe] [-?|--help] [--usage]
        [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST]
        [-t|--terminal=CODE] [-m|--max-protocol=LEVEL]
        [-T|--tar=<c|x>IXFqgbNan] [-D|--directory=DIR] [-c|--command=STRING]
        [-b|--send-buffer=BYTES] [-p|--port=PORT] [-g|--grepable]
        [-B|--browse] [-d|--debuglevel=DEBUGLEVEL]
        [-s|--configfile=CONFIGFILE] [-l|--log-basename=LOGFILEBASE]
        [-V|--version] [-O|--socket-options=SOCKETOPTIONS]
        [-n|--netbiosname=NETBIOSNAME] [-W|--workgroup=WORKGROUP]
        [-i|--scope=SCOPE] [-U|--user=USERNAME] [-N|--no-pass]
        [-k|--kerberos] [-A|--authentication-file=FILE]
        [-S|--signing=on|off|required] [-P|--machine-pass] [-e|--encrypt]
        service <password>
grom@ubuntu-lep-tich:~/Desktop$ smbclient -l
Usage: smbclient [-?EgBVNkPe] [-?|--help] [--usage]
        [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST]
        [-t|--terminal=CODE] [-m|--max-protocol=LEVEL]
        [-T|--tar=<c|x>IXFqgbNan] [-D|--directory=DIR] [-c|--command=STRING]
        [-b|--send-buffer=BYTES] [-p|--port=PORT] [-g|--grepable]
        [-B|--browse] [-d|--debuglevel=DEBUGLEVEL]
        [-s|--configfile=CONFIGFILE] [-l|--log-basename=LOGFILEBASE]
        [-V|--version] [-O|--socket-options=SOCKETOPTIONS]
        [-n|--netbiosname=NETBIOSNAME] [-W|--workgroup=WORKGROUP]
        [-i|--scope=SCOPE] [-U|--user=USERNAME] [-N|--no-pass]
        [-k|--kerberos] [-A|--authentication-file=FILE]
        [-S|--signing=on|off|required] [-P|--machine-pass] [-e|--encrypt]
        service <password>
grom@ubuntu-lep-tich:~/Desktop$ smbclient -B
DNS-SD browsing is not supported on this platform
grom@ubuntu-lep-tich:~/Desktop$ 


So my first question is, is there a way in Itrepid to use GUI to connect to windows network, and if there is not, where can I find shell-walkthrough for making it happen?

Sorry for my English, 
kind regards, Beezgetz

---

### Post by llamakc on 2009-02-22
```

smbtree

```

May be of some help.

---

### Post by Beezgetz on 2009-02-22
Hello llamakc

well, I guess not, but lighting fast replay, thanks:

grom@ubuntu-lep-tich:~$ smbtree
Password: 
WORKGROUP
	\\UBUNTU-LEP-TICH		ubuntu-lep-tich server (Samba, Ubuntu)
		\\UBUNTU-LEP-TICH\download       	
		\\UBUNTU-LEP-TICH\filmi_risanke_serije	
		\\UBUNTU-LEP-TICH\print$         	Printer Drivers
		\\UBUNTU-LEP-TICH\IPC$           	IPC Service (ubuntu-lep-tich server (Samba, Ubuntu))
MSHOME
grom@ubuntu-lep-tich:~$ smbclient -L MSHOME
Connection to MSHOME failed (Error NT_STATUS_BAD_NETWORK_NAME)
grom@ubuntu-lep-tich:~$

---

### Post by clive littlewood on 2009-02-22
Hi

If you are trying to share files with windoze then do the following.

Create a new file in nautilus called shares.

Right click on this file and click the share tab.

If you do not have Samba shares installed it will offer to install it for you.

Accept and when the install is finished you will be able to share this folder with windoze.

When going from windoze you will see your ubuntu box visible and will be asked for your username and password.

Hope this helps            :D

Clive

---

### Post by Beezgetz on 2009-02-22
ola Clive,

I guess my English is no good after all...

I did that, so other people can use files that i share from my share folders.

I have a problem as i want to access their shared folders. I can not access their shared folders, i dont know why I wrote that twice...

And my main question is, is there a gui for accessing network (if it is not, why it is shown in left part of a filebrowser/nautilus?), and if there is not, I would appreciate shell commands, since being a begginer I can mkdir, cp, amarok -p and such...

kind regards, Beezgetz

---

### Post by spiderbatdad on 2009-02-22
Places>>Network
If your windows share is not there then windows needs to be configured for network sharing. From your error, looks like MSHOME is not the network name.

---

### Post by clive littlewood on 2009-02-22
Hi

Your English is fine !!!!

If you have setup Samba shares then going onto the network tab in nautilus should give you access to workgroup (in windoze)

Works great for me :D

Ubuntu Intrepid >>>>> windoze Vista using my local network.

Regards

Clive

---

### Post by Beezgetz on 2009-02-22
Hello spider-like-bat-dady,

heh, I get same error:
Unable to mount location
Failed to retrieve share list from server


I might forgot to say, that under Hardy it was working fine...

I have a room.mate and girlfriend, and we are using one internet line, so we kind of 'see' each others sharing folders. They still do now, but not me. They can use mine (with pass, can I change that?) but I can not use theirs.... This problem occured as I upgraded Hardy to Intrepid. I, as I mentioned, did a completely new boot of Intrepid last week, and I am not so pleased, since sharing is essential, you know from people to people - UBUNTU!!!!

I have to make this work, since I share job files with my girl, and bluetooth is just not an option for 10-50 mega files...

kind regards, Beezgetz

sorry, edit:

Hey clive,

I did your steps last week, it did ask me to install (samba- I guess...) but I am still getting this error message...

kind regards. Beezgetz


another edit!
I have dozen of downloaded books on linux, and I read that machines running on linux need to be rebooted every 6 months, for maintenance reasons only...
what I did, is I opened synaptic, reinstalled samba that was already installed, and restarted the laptop. 
Now it seems to work nicely!?!

Thanks guys and galls, for quick support!

kind regards, Beezgetz

---

### Post by PatchesTheCaveman on 2011-01-01
Happy New Year everyone!

Do you have Windows Live Essentials installed on the computer you are trying to access?  The Windows Live Sign-In Assistant changes the way Windows communicates via the SMB protocol such that Samba cannot talk to it.  While the Samba developer have fixed this bug, Canonical has not yet released an updated package for Ubuntu.

To work around this issue, uninstall Windows Live Essentials.  Please note that Microsoft sometimes installs this software as part of Windows Update, so you might not be aware it's installed.

For more information, see this thread:  [http://ubuntuforums.org/showthread.php?t=1655434](http://ubuntuforums.org/showthread.php?t=1655434)

---

