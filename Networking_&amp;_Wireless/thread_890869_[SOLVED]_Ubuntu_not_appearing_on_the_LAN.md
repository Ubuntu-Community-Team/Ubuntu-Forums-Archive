---
title: "[SOLVED] Ubuntu not appearing on the LAN"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by rsnow on 2008-08-15
My situation: I have 2 Windows XP and one Ubuntu Studio on my home LAN.

These are connected through a LinkSys DSL router. 
I can access the internet on all three computers. 
I can access shared folders on the XP machines from either XP machine.
I can access shared folders on the XP machines from the Ubunto machine but
only by typing the ip address. 

The Ubuntu machine cannot open folders in the workgroup, although it does bring up the workgroup name.

I cannot even see the Ubuntu machine from either XP machine. 

Is there a way to put the Ubuntu machine into the same workgroup with the XPs?
If so, how? Or would this even help the situation?
I have tried the instructions in the help section but they didn't 'help'.

---

### Post by bab1 on 2008-08-15
have you looked at the /etc/samba/smb.conf file.  In the global section of that file you can assign the windows workgroup.  It needs be the same as your whatever your XP hosts use.

---

### Post by rsnow on 2008-08-15
These are my global settings 

workgroup = MSHOME

server string = %h server (Samba, Ubuntu)

;   wins support = no

;   wins server = w.x.y.z

dns proxy = no

;   name resolve order = lmhosts host wins bcast


What does the ; mean?

---

### Post by bab1 on 2008-08-15
The ; is a marker for comments.  It means this line is not to be read by the program.

What is the workgroup for the XP's?  Are they in a group called MSHOME.  All of the hosts need to be in the same workgroup.

The second line is what is displayed in windows 

The DNS says no Wins lookup.

The big thing is the first line.  Let me know.

---

### Post by rsnow on 2008-08-15
I put both XP machines into workgroup MSHOME. Did the restart and checked both to see if they could locate the Ubuntu machine...No luck.

Also tried to find the XP machines from Ubuntu. I could find the MSHOME workgroup but still get the message saying 'sorry could not open files'

---

### Post by bab1 on 2008-08-15
I think we may have to manually configure Samba.  First off, Samba is a server and the XP hosts should be the the clients.  Samba really has problems in a peer to peer situation. I have all of my "common" files on the Ubuntu/Samba server.  I can see and map to them from any XP on the network.  I have [COLOR="Sienna"]/smb/home[/COLOR] and [COLOR="DarkGreen"]/smb/share[/COLOR] and [COLOR="Indigo"]/smb/backup[/COLOR].  Is this sort of what you had in mind?

Try looking at [[COLOR="Magenta"]this[/COLOR]]("https://help.ubuntu.com/community/SettingUpSamba") first.

---

### Post by rsnow on 2008-08-15
Yes ( I think so), Since doing this with Linux is a new experience for me.

I'd like to be able to share a number of files as one of the XP machines is primarily used by my wife and the other one has all my music, photos and video files. My goal is to become proficient with Ubuntu Studio so that I can copy my music, photos and videos to there and work on them. I want to be able to eventually not need Windows. When I feel comfortable enough with Ubuntu, I'll most likely convert my XP machine to a Linux server (or try to). One needs to have goals.

---

### Post by bab1 on 2008-08-15
I can help.  I kinda want you to learn what is going on.  The only limitation is the Ubuntu to XP browsing.  Ubuntu does not have all of the easy interface that XP has.  You can connect but it is hard to browse.

Some terms need to be defined.
Server = a process that waits for a client to request an action
Client = a process that asks for an action
Host = A computer with an OS installed
Share = A dir that is available to a client to read (r) or write (w) to

I need to know that you want Ubuntu to be a Samba Server (files shared from here).  The XP hosts will be the clients.  If so we can start with a few files on the Samba server and config from there.  BTW do these hosts have hostnames?  If not how about XP1 and XP2 and SAM.

We will need a directory that we can dedicate to the share(s). And we will need to add whatever users you want to the smbusers database.  The Samba login is NOT the Ubuntu login.

---

### Post by rsnow on 2008-08-15
When you say "files shared from here", does that mean only one way sharing is possible?

If hostname is the same as computer name, then one is named "jackie" and the other is named "ronsamd64". The Ubuntu is named ron-eedesktop. Right now I have a folder named "music" and it contains a folder named "ogg" on the Ubuntu machine. In other words, I'm not sure what you mean by "a directory that we can dedicate to the shares". Do you mean something like a folder called "Shared files"?

---

### Post by bab1 on 2008-08-15
> When you say "files shared from here", does that mean only one way sharing is possible?

it's dynamic.  The asking is always the client.  Tthe responder is  always the server.  The "host" can be both.  see my definitions from the last post. What I was trying to convey is that the the ron-eedesktop host has difficulty being the client.  It has minimal abilities that way.

> I'm not sure what you mean by "a directory that we can dedicate to the shares".

A directory is a folder.  You can "share" it.

I made a folder off the root directory called smb.  Every share I create is from the /smb folder.

Question:  Do you know how to use the terminal (command line)?   It's like the "Start>Run>CMD" on your XP.

---

### Post by Iowan on 2008-08-15
Probably a tangent - so feel free to ignore...
If Ubuntu is getting it's address via DHCP, the **/etc/dhcp3/dhclient.conf** file that has a line [B]send host-name "<hostname>";
[/B] that can be edited.  This *might* make Ubuntu visible on network.

---

### Post by bab1 on 2008-08-15
Iowan,

I have seen this mentioned before.  Does this update the DNS records anywhere or... just provides a consistent naming of the hosts?

I ask because I don't use this now, but I have a project where it might be useful.

---

### Post by rsnow on 2008-08-16
I did some command line things while going through the projects in the book _Ubuntu for Non-Geeks_. So I at least know how to open the terminal and type in things that folks tell me to type. I haven't learned all the commands.

If you are willing to work with me, I'd like to give it a try and see what else I can learn. I think that is the best way to learn.

---

### Post by bab1 on 2008-08-16
I will help.  Go back and look at my definitions so we have that clear.  I am answering another guy's question, so bear with me if I am slow to respond.  I'm a bit wordy (sp?), but that comes from teaching a lot.  :-)

---

### Post by bab1 on 2008-08-16
Let's get some housekeeping out of the way, lets ping each of the hosts by name.  Make sure all the hosts are running.  I say this because I myself have forgotten to check that the computers were booted up.  :D

From the [COLOR="Blue"]ron-eedesktop[/COLOR] terminal:
```
ping -c 4 jackie
``` and ```
ping -c 4 ronsamd64
```(the -c 4 limits the ping to 4 packets)

You can try the same from the other hosts.  If this works, then DNS is working.  All we are doing is seeing that the 3 hosts can talk to each other and that the name is resolved to the IP address.  ;-)

Let me know that all is okay.

---

### Post by rsnow on 2008-08-16
I can ping OK both ways with all machines.

Don't worry about slow responses. I get sidetracked myself and I consider learning Ubuntu as a long term commitment. I appreciate your help.

---

### Post by bab1 on 2008-08-16
Good.  See if you have the Samba server running.

Try: ```
ps -ef | grep smb
``` the | is the [COLOR="Red"]shifted[/COLOR] key nest to the "back space" key.  It's called a pipe.

You should get this back:
```
bruce@malibu:~>ps -ef |grep smb
root      4431     1  0 14:49 ?        00:00:00 /usr/sbin/smbd -D
root      4464  4431  0 14:49 ?        00:00:00 /usr/sbin/smbd -D
bruce     5464  5447  0 16:14 pts/3    00:00:00 grep --color=auto smb

```

If not send me the results.

---

### Post by rsnow on 2008-08-16
The results were nearly the same...

ron-ee@roneesdesktop:~$ps -ef | grep smb
root    8584     1  0 17:49 ?      00:00:00 /usr/sbin/smbd -D
root    8590  8584  0 17:49 ?      00:00:00 /usr/sbin/smbd -D
ron-ee  8763  8707  0 22:24 pts/0  00:00:00 grep smb


How do you get the info into a box so it doesn't lose the spacing?

---

### Post by bab1 on 2008-08-17
Good deal here.  I'll decipher for you.

```
root 8584 1 0 17:49 ? 00:00:00 /usr/sbin/smbd -D <-- Samba Server process 
root 8590 8584 0 17:49 ? 00:00:00 /usr/sbin/smbd -D<-- Samba Server process
```

The reason for 2 is that the process forks (spawns) a new process, responds to the request and when finished it dies.  The first one is the master for all new processes .  See the relationship between the 8584 process number in the 1st process and the 2nd?  If I kill the first process, then all will die.

In any event we have a server running on the host: roneesdesktop

To use the box to insert code:  After you click to reply, look for the button that says "go advanced" and click on it.  The icons at the top are for various HTML formating styles.  The hash mark one is for the box. It says "wrap in code" when you mouse over the icon.

It's late so I will continue tomorrow (Sunday).

---

### Post by rsnow on 2008-08-18
For the benefit of anyone who may be following this thread or is just checking it out, bab1 and myself are going to continue working on this via emails and IM. So, when we have completed our task - reached our goal - accomplished our mission - we will post the method/procedure we used and how it worked out. So, stay tuned and check in from time to time (hopefully not too long from now) and see the results.

---

### Post by rsnow on 2008-09-03
Maybe this will help someone.

I didn't think this first step was necessary either until I got involved actually trying to accomplish my goal of setting up a static IP LAN. But, to repeat the advice I was given..._Make a drawing_ of the network you plan to have. If possible, include the names of each computer and the IP address you will assign. 

The specifications for the router/switch and the modem were accessed via the appropriate web sites.

My LAN setup:
DSL connection-----Zyxel 660R modem-----LinkSys BEFSR41v4 DSL Router w/5 port switch-----computers.

My static ip configuration:
computer #1 - name: mylinux, ip address: 192.168.1.201
computer #2 - name: wife,    ip address: 192.168.1.202
computer #3 - name: myXP,    ip address: 192.168.1.203

default gateway: 192.168.1.1
DNS Servers: 192.168.2.1
             208.67.222.222

Windows XP machines procedure:
Start/control panel/network connections-right click on local area connection-click on properties-left
click on Internet Protocol[TCP/IP]-left click on Properties-left click on "Use the following IP address"-
enter the IP address. 
The subnet mask will be entered automatically when you left click on that window. 
Enter the Default gateway....

Now, left click on "Use the following DNS server addresses"-enter the Preferred and Alternate DNS server numbers *Note: Alternate DNS server is not required.
Left click OK- left click OK.

Use windows explorer to go to C:\Windows\system32\drivers\etc\hosts.
Right click on hosts folder and left click on Open and select either Notepad or Wordpad
On the lines under 127.0.0.1   localhost, type the IP address followed by the name of each computer on the LAN.
             i.e., 192.168.1.201 mylinux
                   192.168.1.202 wife
                   192.168.1.203 myXP

Save and close the file  -  reboot

Ubuntu machine procedure:
System/Administration/Network-enter password-click on 'Connections' tab-select 'Wired Connection'-
click on 'Properties'
Deselect (uncheck) "Enable roaming mode" (We do not want roaming)
In the Configuration dropdown choose "Static IP address".
In the IP address window enter the IP address you want assigned - i.e., 192.168.1.201.
The subnet mask number should come up automatically when you click on that window.
In the Gateway address window enter the default Gateway address - i.e., 192.168.1.1.
Click OK

Click the DNS tab.
If the correct DNS server number is not showing, click on the existing number and then click on "Delete"
Click "Add" and enter the correct DNS server number (numbers if you are using an alternate).

Click on the Hosts tab.
Under the 127.0.0.1 localhost entry there should be (or you can add) the computers that are on the LAN
Be sure these are located between the "localhost" and the "ip6-localhost ip6-loopback" entries.
click on "Close"
Reboot - (probably not necessary but a good precaution)

When completed on all computers that are on the LAN, each should have its own, assigned (by you), 
IP address and name.

Each computer should be reachable on the network by either its name or IP address.
This is assuming that Samba is installed on the Ubuntu machine(s).

Technical assistance was provided by Bruce Borah. A big THANKS to him!

To test LAN connections from Windows XP
start/run/cmd.exe-type in:"ping <computer name>" or "<ip address>"

To check ip configuration
start/run/cmd.exe-type in:"ipconfig /all"

To test LAN connections from Ubuntu
open a command line terminal and type "ping -c4 <name-of-computer>"

To check ip configuration
press Alt-F2 and type in "gksudo gedit /etc/hosts"

---

### Post by bab1 on 2008-09-05
Thank you Ron!

This is an example of how to properly setup a small network with static IP addressing and hosts files instead of a local DNS server. The Samba setup was also manually configured.  In this case we used security=share . This was due to the use of non-compatible login names.  This allows anyone to browse the shares, while the Linux permissions control the actual file access.

---

