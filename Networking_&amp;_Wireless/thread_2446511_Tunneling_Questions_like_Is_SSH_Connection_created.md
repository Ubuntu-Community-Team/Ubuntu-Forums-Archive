---
title: "Tunneling Questions like Is SSH Connection created before the &quot;Tunnel&quot; is created?"
date: 2020-07-01
forum: Networking &amp; Wireless
---

### Post by fran_3 on 2020-07-01
(Note: This is a follow up to my SSH thread but this is about Tunneling and SSH and so I thought it merited it's own Thread.)

From the Windows Command line...
WinPCpro-L-1 at Location 1 connects over the internet to a Ubuntu Server at Location 2
with...
Putty.exe [email]username@xxx.xx.xx.xxx[/email] -P aaaaa -i .\username.ppk
And after entering the password...
WinPCpro-L-1 is connected to the Ubuntu Server and can remotely enter commands.

(I've actually got this working but I want to know what is going on under the hood.)

Question 1:
After the connection is established the commends entered on the PC's keyboard will ultimately be sent to... the Ubuntu Server at xxx.xx.xx.xxx:aaaaa -- that is Public IP Address xxx.xx.xx.xxx Port aaaaa
So this means the Linux Server is "listening" for SSH traffic on Port aaaaa
Right?

Question 2:
Does the Windows Command Line entry
Putty.exe [email]username@xxx.xx.xx.xxx[/email] -P aaaaa -i .\username.ppk
also setup a "tunnel" ?

Question 3:
The term "Tunnel" confuses me as it makes me think of some kind of magic hardwired permanent connection... which of course is impossible over a packet switching network like the internet...
So the "tunnel" is virtual... as seen between the TCP/IP Model's "Application" Layers...
Right so for?

Question 4:
And before "Tunneling" can begin the two computers must communicate with each other and setup/agree to things... like maybe what "Tunneling" protocol is going to be used, etc...
Right so for?

Question 5:
So now the SSH "connection" has been established between the 2 computers
And the "Tunneling" protocol has been agreed to by the 2 computers...
Or does this happen differently?

Question 6:
So after the two computers agree to talk and "how" they are going to talk...
- the raw data from the PC Application gets processed by the "tunneling" software...
- and then sent to the SSH client for further processing and forwarding down to...
- the TCP/IP Model and then to the
- Transport/TCP Layer and then to the
- Internet/IP Layer and then to the Data Link Layer and then
- out the NIC door to the network...
Or does this happen differently?

Sorry for all the confusion but I've dived in to learning this stuff now and really appreciate anyone helping me find my way.

Thanks for any help.

PS-1 Hopefully I'm in the right font size so I don't get in trouble again :-)
PS-2 , I've Googled and watched YouTube videos on all this but I'm trying to dig a little deeper into the events and actual sequence of events.

---

### Post by TheFu on 2020-07-01
2.  No.
i have no idea how putty sets up ssh tunnels.  You'll need to read the manual page for that program.  Putty makes things harder than necessary.

Also, we don't use passwords for ssh connections.  We use either ssh-key or ssh-certs.  Passwords are a security failure.

```
   ssh -f -C -D $PORT  gw.example.com -NT &
```
is how i setup a tcp tunnel from the local machine to a remote machine.  UDP traffic cannot be tunnelled over ssh.  You can look up what each option means.  i don't remember anymore.  i put it into a script so i don't need to know anymore.  i use the ~/.ssh/config file to fill in userid, port and other settings for the gw.example.com connection so i don't need to remember those things, ever, for any connection to that same name.

Don't know about any of the other questions. Sorry.

---

### Post by wildmanne39 on 2020-07-02
Hello fran6, I restored your post please do not delete your posts if you think something needs our attention please report it and a staff member will take a look and consider what you are asking.

Thanks

---

### Post by fran_3 on 2020-07-02
Wildman39, thanks, I guess. 
After consideration I decided I wanted to approach this from a different direction and that, due to my poor network knowledge, the post may have been way off the mark.
Thanks for everyone's patience and kind assistance as I try to fill in the gaps in my knowledge.

---

### Post by fran_3 on 2020-07-02
Hello TheFu, thanks for your response.

FYI, in my case...
- I have a Windows 10 Pro PC at one location and a Ubuntu Server at another location.
- There are a couple of PC's in the same location as the server
- We log into the Server in order to control a couple of PC's with TightVNC and, for now, it works :-)
- Our "expert" is now mostly unavailable so I'm learning how it all works.
- Because one of the two PC's crashed and I'm configuring its replacement

My questions:
1 - Are you running the command line you put up on a Windows machine or what?
2 - I don't see a reference to your private key name and location... does your system just know where it is?

When I login from the Windows 10 machine command line using Putty here is the line I use...

```
putty.exe  username@xxx.xx.xx.xx  -P 13116 -i .\username.ppk 
```

When I login from the Win10 command line using the built in SSH client here is the line I use...

```
ssh -p 13116 username@xxx.xx.xx.xx  
```

Note that I'm still researching how to tell Windows SSH client where to find the private key username.ppk file

Thank to everyone for any help.

---

