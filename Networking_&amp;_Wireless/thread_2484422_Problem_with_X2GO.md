---
title: "Problem with X2GO"
date: 2023-02-25
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2023-02-25
I have two ubuntu (20.04 and 22.04) Desktop machines A and B on a local lan. I can successfully ssh from A to B using the terminal without being asked for machine B's password. I have installed x2go server on B and the client on A.  The settings for the x2go session appear straight forward but I'm stuck at the attached screens.  Interesting x2go is asking me the password.

---

### Post by Quarkrad on 2023-02-25
The order of the screens are the reverse of the above attachments

---

### Post by Quarkrad on 2023-02-27
bump

---

### Post by Quarkrad on 2023-03-02
bump

---

### Post by Quarkrad on 2023-03-03
bump

---

### Post by him610 on 2023-03-04
You need assistance from TheFu who is the resident evangalist for x2go. 
Sometimes I use x2go, but I am not an expert on it so I might wind up telling you the wrong thing. 
One other thing: do not be concerned with x2go asking for a password; it is builtin security that you do not want to circumvent.

Do you happen to have pre-defined sessions? Refer to attached screenshot that show session widgets for four local devices on my LAN [https://imgur.com/6pcv24n.png]("https://imgur.com/6pcv24n.png")

---

### Post by Quarkrad on 2023-03-05
I've re-installed everything and it is the same.  I did have this working originally but something has happened to stop it.  Next move; clear the log file and start with a fresh log output.

---

### Post by Quarkrad on 2023-03-05
I'm still having problems and there is an error message that comes up - but the screen is only visible for a very short while and moves onto the picture I post above.  The screen with the error message looks like the attached.  There must be a way of freezing the screen but I cannot find it. Or the text is outputted somewhere(?).

---

### Post by #&amp;thj^% on 2023-03-05
assuming your using ssh, check to see what port is used in "~/.ssh/config" and try to remove port 22
Provisional fix - The offending
line is "Port 22" in the localhost section of the ~/.ssh/config file on the
client side.  Commenting out the line solves the problem in most cases.
if not run it in debug:
```
x2goclient --debug

```

---

### Post by Quarkrad on 2023-03-05
I haven't got a ~/.ssh/config file.  But I have change the port number on both machines in /etc/ssh/sshd_config.  I first established a ssh connection.

```
dad@dadubuntu:~$ ssh liz@192.168.1.165 -p 46182
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 5.15.0-67-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

 * Introducing Expanded Security Maintenance for Applications.
   Receive updates to over 25,000 software packages with your
   Ubuntu Pro subscription. Free for personal use.

     https://ubuntu.com/pro

Expanded Security Maintenance for Applications is not enabled.

6 updates can be applied immediately.
To see these additional updates run: apt list --upgradable

41 additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm

Your Hardware Enablement Stack (HWE) is supported until April 2025.
Last login: Sun Mar  5 16:47:45 2023 from 192.168.1.145
liz@lizubuntu:~$ 
```

I then closed the connection and the terminal and run your de-bug command:

```
x2go-DEBUG-../src/sshprocess.cpp:213> this=SshProcess(0x55f77f380290) Running masterCon->addChannelConnection(this, '"226cd449-d3fc-4131-9141-13d02d2006d4"', '"bash -l -c 'echo \"X2GODATABEGIN:226cd449-d3fc-4131-9141-13d02d2006d4\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2golistsessions; echo \"X2GODATAEND:226cd449-d3fc-4131-9141-13d02d"');
x2go-DEBUG-../src/sshmasterconnection.cpp:1810> Locking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1812> Passing new channel connection object to channelConnections.
x2go-DEBUG-../src/sshmasterconnection.cpp:1814> Unlocking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1977> Creating new channel.

x2go-DEBUG-../src/sshmasterconnection.cpp:1990> New channel:0x7f77dc0bb380

x2go-DEBUG-../src/sshmasterconnection.cpp:2065> Executing remote: "bash -l -c 'echo \"X2GODATABEGIN:226cd449-d3fc-4131-9141-13d02d2006d4\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2golistsessions; echo \"X2GODATAEND:226cd449-d3fc-4131-9141-13d02d2006d4\";'"

x2go-DEBUG-../src/sshmasterconnection.cpp:2082> New exec channel created.

x2go-DEBUG-../src/sshmasterconnection.cpp:2121> EOF on channel 0x7f77dc0bb380; SshProcess object: 0
x2go-DEBUG-../src/sshmasterconnection.cpp:2222> EOF sent.
x2go-DEBUG-../src/sshmasterconnection.cpp:2224> Channel closed.
x2go-DEBUG-../src/sshprocess.cpp:532> SSH finished: raw output (stdout): "X2GODATABEGIN:226cd449-d3fc-4131-9141-13d02d2006d4\nX2GODATAEND:226cd449-d3fc-4131-9141-13d02d2006d4\n"
x2go-DEBUG-../src/sshprocess.cpp:543> SSH finished: true - "" (0).
x2go-DEBUG-../src/onmainwindow.cpp:3861> ""
x2go-DEBUG-../src/onmainwindow.cpp:4521> Executing remote command: "X2GO_XINERAMA=no x2gostartagent 800x600 lan 16m-jpeg-9 unix-kde-depth_24 us auto 1 D MATE both"
x2go-DEBUG-../src/sshprocess.cpp:199> Executing remote command via SshProcess object 1: "X2GO_XINERAMA=no x2gostartagent 800x600 lan 16m-jpeg-9 unix-kde-depth_24 us auto 1 D MATE both"
x2go-DEBUG-../src/sshprocess.cpp:213> this=SshProcess(0x55f77f36e2e0) Running masterCon->addChannelConnection(this, '"8a43cdb2-6f3b-4f04-9c08-2c0fbe668a46"', '"bash -l -c 'echo \"X2GODATABEGIN:8a43cdb2-6f3b-4f04-9c08-2c0fbe668a46\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; X2GO_XINERAMA=no x2gostartagent 800x600 lan 16m-jpeg-9 unix-kde-de"');
x2go-DEBUG-../src/sshmasterconnection.cpp:1810> Locking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1812> Passing new channel connection object to channelConnections.
x2go-DEBUG-../src/sshmasterconnection.cpp:1814> Unlocking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1977> Creating new channel.

x2go-DEBUG-../src/sshmasterconnection.cpp:1990> New channel:0x7f77dc0bbf90

x2go-DEBUG-../src/sshmasterconnection.cpp:2065> Executing remote: "bash -l -c 'echo \"X2GODATABEGIN:8a43cdb2-6f3b-4f04-9c08-2c0fbe668a46\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; X2GO_XINERAMA=no x2gostartagent 800x600 lan 16m-jpeg-9 unix-kde-depth_24 us auto 1 D MATE both; echo \"X2GODATAEND:8a43cdb2-6f3b-4f04-9c08-2c0fbe668a46\";'"

x2go-DEBUG-../src/sshmasterconnection.cpp:2082> New exec channel created.

x2go-DEBUG-../src/sshmasterconnection.cpp:2121> EOF on channel 0x7f77dc0bbf90; SshProcess object: 1
x2go-DEBUG-../src/sshmasterconnection.cpp:2222> EOF sent.
x2go-DEBUG-../src/sshmasterconnection.cpp:2224> Channel closed.
x2go-DEBUG-../src/sshprocess.cpp:532> SSH finished: raw output (stdout): "X2GODATABEGIN:8a43cdb2-6f3b-4f04-9c08-2c0fbe668a46\n50\nced8b6f8ed8c995fb03b3c020ddb78ef\n2923\nliz-50-1678038712_stDMATE_dp24\n62084\n62085\n62086\nX2GODATAEND:8a43cdb2-6f3b-4f04-9c08-2c0fbe668a46\n"
x2go-DEBUG-../src/sshprocess.cpp:543> SSH finished: true - "50\nced8b6f8ed8c995fb03b3c020ddb78ef\n2923\nliz-50-1678038712_stDMATE_dp24\n62084\n62085\n62086\n" (1).
x2go-DEBUG-../src/onmainwindow.cpp:5425> Agent output: "50\nced8b6f8ed8c995fb03b3c020ddb78ef\n2923\nliz-50-1678038712_stDMATE_dp24\n62084\n62085\n62086\n"
x2go-DEBUG-../src/sshprocess.cpp:387> Starting tunnel via SshProcess object 2: "localhost":62084 -> "localhost":63084

RESUMING SESSION is KDRIVE:  false
x2go-DEBUG-../src/onmainwindow.cpp:6142> "Starting NX proxy, command: nxproxy -S nx/nx,options=/home/dad/.x2go/S-liz-50-1678038712_stDMATE_dp24/options:50"
x2go-DEBUG-../src/sshprocess.cpp:157> Direct tunnel: waiting for connections on "localhost":63084
x2go-DEBUG-../src/onmainwindow.cpp:6618> Proxy wrote on stderr: "\nNXPROXY - Version 3.5.99.26\n\nCopyright (c) 2001, 2011 NoMachine (http://www.nomachine.com)\nCopyright (c) 2008-2014 Oleksandr Shneyder <o.shneyder@phoca-gmbh.de>\nCopyright (c) 2014-2016 Ulrich Sibiller <uli42@gmx.de>\nCopyright (c) 2014-2016 Mihai Moldovan <ionic@ionic.de>\nCopyright (c) 2011-2016 Mike Gabriel <mike.gabriel@das-netzwerkteam.de>\nCopyright (c) 2015-2016 Qindel Group (http://www.qindel.com)\n\nNXCOMP, NX protocol compression and NX extensions to this software\nare copyright of the aforementioned persons and companies.\n\nRedistribution and use of the present software is allowed according\nto terms specified in the file LICENSE.nxcomp which comes in the\nsource distribution.\n\nAll rights reserved.\n\nNOTE: This software has received contributions from various other\ncontributors, only the core maintainers and supporters are listed as\ncopyright holders. Please contact us, if you feel you should be listed\nas copyright holder, as well.\n\nNX protocol compression is derived from DXPC project.\n\nCopyright (c) 1995,1996 Brian Pane\nCopyright (c) 1996,1997 Zachary Vonler and Brian Pane\nCopyright (c) 1999 Kevin Vigor and Brian Pane\nCopyright (c) 2000,2003 Gian Filippo Pinzari and Brian Pane\n\nAll rights reserved.\n\nSee https://github.com/ArcticaProject/nx-libs for more information.\n\nInfo: Proxy running in server mode with pid '6000'.\nSession: Starting session at 'Sun Mar  5 17:51:54 2023'.\nInfo: Using errors file '/home/dad/.x2go/S-liz-50-1678038712_stDMATE_dp24/sessions'.\nInfo: Using stats file '/home/dad/.x2go/S-50/stats'.\nLoop: WARNING! Overriding auxiliary X11 port with new value '1'.\nWarning: Overriding auxiliary X11 port with new value '1'.\nInfo: Using abstract X11 socket in kernel namespace for accessing DISPLAY=:0.\nInfo: Connecting to remote host 'localhost:63084'.\nInfo: Connected to remote proxy on FD#5.\n"
x2go-DEBUG-../src/sshprocess.cpp:109> New TCP connection.
x2go-DEBUG-../src/sshprocess.cpp:114> New socket: 25
x2go-DEBUG-../src/sshmasterconnection.cpp:1977> Creating new channel.

x2go-DEBUG-../src/sshmasterconnection.cpp:1990> New channel:0x7f77dc0bbf90

x2go-DEBUG-../src/sshmasterconnection.cpp:1994> Forwarding parameters: from remote ("localhost":62084) to local ("localhost":50534)
x2go-DEBUG-../src/sshmasterconnection.cpp:2028> Temporary session port after config file parse: 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:2032> Temporary session host after config file parse: localhost
x2go-DEBUG-../src/sshmasterconnection.cpp:2059> New channel forwarded.

x2go-DEBUG-../src/onmainwindow.cpp:6618> Proxy wrote on stderr: "Loop: PANIC! Parse error in remote options string 'SSH-2.0-OpenSSH_8.2p1 '.\nError: Parse error in remote options string 'SSH-2.0-OpenSSH_8.2p1 '.\nLoop: PANIC! Failure negotiating the session in stage '7'.\nError: Failure negotiating the session in stage '7'.\nLoop: PANIC! Wrong version or invalid session authentication cookie.\nError: Wrong version or invalid session authentication cookie.\nSession: Terminating session at 'Sun Mar  5 17:51:54 2023'.\nSession: Session terminated at 'Sun Mar  5 17:51:54 2023'.\n"
x2go-DEBUG-../src/sshmasterconnection.cpp:2199> "Error reading from TCP socket." - ""

x2go-DEBUG-../src/sshmasterconnection.cpp:2222> EOF sent.
x2go-DEBUG-../src/sshmasterconnection.cpp:2224> Channel closed.
x2go-DEBUG-../src/sshprocess.cpp:478> I/O error: "Error reading from TCP socket.""" (2).
x2go-DEBUG-../src/onmainwindow.cpp:6475> Deleting Proxy.
x2go-DEBUG-../src/onmainwindow.cpp:6520> Waiting for proxy to exit.
x2go-DEBUG-../src/onmainwindow.cpp:6544> Checking exit status.
x2go-DEBUG-../src/sshprocess.cpp:199> Executing remote command via SshProcess object 3: "x2gocmdexitmessage liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/sshprocess.cpp:213> this=SshProcess(0x55f77f46d3b0) Running masterCon->addChannelConnection(this, '"2d2bbe56-ab43-47b6-9289-bcf04a0253dc"', '"bash -l -c 'echo \"X2GODATABEGIN:2d2bbe56-ab43-47b6-9289-bcf04a0253dc\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2gocmdexitmessage liz-50-1678038712_stDMATE_dp24; echo \"X2GODATAE"');
x2go-DEBUG-../src/sshmasterconnection.cpp:1810> Locking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1812> Passing new channel connection object to channelConnections.
x2go-DEBUG-../src/sshmasterconnection.cpp:1814> Unlocking SSH channel connection MUTEX.
x2go-DEBUG-../src/onmainwindow.cpp:6601> Finished proxy.
x2go-DEBUG-../src/sshmasterconnection.cpp:1977> Creating new channel.

x2go-DEBUG-../src/sshmasterconnection.cpp:1990> New channel:0x7f77dc0bbf90

x2go-DEBUG-../src/sshmasterconnection.cpp:2065> Executing remote: "bash -l -c 'echo \"X2GODATABEGIN:2d2bbe56-ab43-47b6-9289-bcf04a0253dc\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2gocmdexitmessage liz-50-1678038712_stDMATE_dp24; echo \"X2GODATAEND:2d2bbe56-ab43-47b6-9289-bcf04a0253dc\";'"

x2go-DEBUG-../src/sshmasterconnection.cpp:2082> New exec channel created.

x2go-DEBUG-../src/sshmasterconnection.cpp:2121> EOF on channel 0x7f77dc0bbf90; SshProcess object: 3
x2go-DEBUG-../src/sshmasterconnection.cpp:2222> EOF sent.
x2go-DEBUG-../src/sshmasterconnection.cpp:2224> Channel closed.
x2go-DEBUG-../src/sshprocess.cpp:532> SSH finished: raw output (stdout): "X2GODATABEGIN:2d2bbe56-ab43-47b6-9289-bcf04a0253dc\nX2GODATAEND:2d2bbe56-ab43-47b6-9289-bcf04a0253dc\n"
x2go-DEBUG-../src/sshprocess.cpp:543> SSH finished: true - "" (3).
x2go-DEBUG-../src/onmainwindow.cpp:9933> "Command message: "
x2go-DEBUG-../src/sshmasterconnection.cpp:764> SshMasterConnection, instance SshMasterConnection(0x55f77f1aace0) waiting for thread to finish.
x2go-DEBUG-../src/sshmasterconnection.cpp:1908> Disconnecting ...

x2go-DEBUG-../src/sshmasterconnection.cpp:1917> Deleting channel connections.

x2go-DEBUG-../src/sshmasterconnection.cpp:1923> Disconnecting session.

x2go-DEBUG-../src/sshmasterconnection.cpp:1927> Deleting sockets.

x2go-DEBUG-../src/sshmasterconnection.cpp:1932> All channels closed and session disconnected. Quitting session loop.

x2go-DEBUG-../src/sshmasterconnection.cpp:766> SshMasterConnection, instance SshMasterConnection(0x55f77f1aace0) thread finished.
x2go-DEBUG-../src/sshprocess.cpp:52> SshProcess destructor called.
x2go-DEBUG-../src/sshprocess.cpp:52> SshProcess destructor called.
x2go-DEBUG-../src/sshprocess.cpp:52> SshProcess destructor called.
x2go-DEBUG-../src/sshprocess.cpp:52> SshProcess destructor called.
x2go-DEBUG-../src/sshmasterconnection.cpp:771> SshMasterConnection, instance SshMasterConnection(0x55f77f1aace0) finished destructor.
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678038712_stDMATE_dp24"
x2go-INFO-8> "Starting connection to server: 192.168.1.165:46182"
x2go-DEBUG-../src/onmainwindow.cpp:2853> Starting new ssh connection to server:"192.168.1.165":"46182" krbLogin: false
x2go-DEBUG-../src/sshmasterconnection.cpp:168> SshMasterConnection, host "192.168.1.165"; port 46182; user "liz"; useproxy false; proxyserver ""; proxyport 22
x2go-DEBUG-../src/sshmasterconnection.cpp:248> Starting SSH connection without Kerberos authentication.
x2go-DEBUG-../src/sshmasterconnection.cpp:250> SshMasterConnection, instance SshMasterConnection(0x7f7824008b70) created.
x2go-DEBUG-../src/sshmasterconnection.cpp:495> SshMasterConnection, instance SshMasterConnection(0x7f7824008b70) entering thread.
x2go-DEBUG-../src/sshmasterconnection.cpp:797> Session port before config file parse: 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:807> Session port after config file parse: 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:870> Session port before config file parse (part 2): 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:880> Session port after config file parse (part 2): 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:904> cserverAuth
x2go-DEBUG-../src/sshmasterconnection.cpp:943> state: 1

x2go-DEBUG-../src/sshmasterconnection.cpp:687> User authentication OK.
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/sshmasterconnection.cpp:1708> LOGIN CHECK:"LOGIN OK\r\n"
x2go-DEBUG-../src/sshmasterconnection.cpp:1711> don't have interaction
x2go-DEBUG-../src/sshmasterconnection.cpp:1744> LOOP FINISHED
x2go-DEBUG-../src/sshmasterconnection.cpp:1748> No interaction needed, continue session
x2go-DEBUG-../src/sshmasterconnection.cpp:702> Login Check - OK
x2go-DEBUG-../src/onmainwindow.cpp:2947> SSH connection established.
x2go-DEBUG-../src/onmainwindow.cpp:3374> Continue normal X2Go session
x2go-DEBUG-../src/sshprocess.cpp:199> Executing remote command via SshProcess object 0: "x2golistsessions"
x2go-DEBUG-../src/sshprocess.cpp:213> this=SshProcess(0x55f77f2fc380) Running masterCon->addChannelConnection(this, '"66042ce2-4763-49fd-9277-862b3f1a8bd6"', '"bash -l -c 'echo \"X2GODATABEGIN:66042ce2-4763-49fd-9277-862b3f1a8bd6\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2golistsessions; echo \"X2GODATAEND:66042ce2-4763-49fd-9277-862b3f"');
x2go-DEBUG-../src/sshmasterconnection.cpp:1810> Locking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1812> Passing new channel connection object to channelConnections.
x2go-DEBUG-../src/sshmasterconnection.cpp:1814> Unlocking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1977> Creating new channel.

x2go-DEBUG-../src/sshmasterconnection.cpp:1990> New channel:0x7f77dc0bb110

x2go-DEBUG-../src/sshmasterconnection.cpp:2065> Executing remote: "bash -l -c 'echo \"X2GODATABEGIN:66042ce2-4763-49fd-9277-862b3f1a8bd6\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2golistsessions; echo \"X2GODATAEND:66042ce2-4763-49fd-9277-862b3f1a8bd6\";'"

x2go-DEBUG-../src/sshmasterconnection.cpp:2082> New exec channel created.

x2go-DEBUG-../src/sshmasterconnection.cpp:2121> EOF on channel 0x7f77dc0bb110; SshProcess object: 0
x2go-DEBUG-../src/sshmasterconnection.cpp:2222> EOF sent.
x2go-DEBUG-../src/sshmasterconnection.cpp:2224> Channel closed.
x2go-DEBUG-../src/sshprocess.cpp:532> SSH finished: raw output (stdout): "X2GODATABEGIN:66042ce2-4763-49fd-9277-862b3f1a8bd6\n2923|liz-50-1678038712_stDMATE_dp24|50|lizubuntu|R|2023-03-05T17:51:52|ced8b6f8ed8c995fb03b3c020ddb78ef|192.168.1.145|62084|62085|2023-03-05T17:51:53|liz|12|62086|-1|-1\nX2GODATAEND:66042ce2-4763-49fd-9277-862b3f1a8bd6\n"
x2go-DEBUG-../src/sshprocess.cpp:543> SSH finished: true - "2923|liz-50-1678038712_stDMATE_dp24|50|lizubuntu|R|2023-03-05T17:51:52|ced8b6f8ed8c995fb03b3c020ddb78ef|192.168.1.145|62084|62085|2023-03-05T17:51:53|liz|12|62086|-1|-1\n" (0).
x2go-DEBUG-../src/onmainwindow.cpp:3861> "2923|liz-50-1678038712_stDMATE_dp24|50|lizubuntu|R|2023-03-05T17:51:52|ced8b6f8ed8c995fb03b3c020ddb78ef|192.168.1.145|62084|62085|2023-03-05T17:51:53|liz|12|62086|-1|-1\n"
x2go-DEBUG-../src/onmainwindow.cpp:4864> No shadow session.
x2go-DEBUG-../src/onmainwindow.cpp:4887> "Decoding session string:2923|liz-50-1678038712_stDMATE_dp24|50|lizubuntu|R|2023-03-05T17:51:52|ced8b6f8ed8c995fb03b3c020ddb78ef|192.168.1.145|62084|62085|2023-03-05T17:51:53|liz|12|62086|-1|-1"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
```

---

### Post by Quarkrad on 2023-03-05
Some of the text did not come out - where the PANIC starts

```
dad@dadubuntu:~$ x2goclient --debug
x2go-INFO-1> "Starting X2Go Client 4.1.2.2..."
x2go-WARNING-1> English language requested, not loading translator.
x2go-WARNING-1> English language requested, not loading translator.
x2go-INFO-3> "Started X2Go Client."
x2go-DEBUG-../src/onmainwindow.cpp:575> "$HOME=/home/dad"
x2go-DEBUG-../src/onmainwindow.cpp:2266> Reading 1 sessions from config file.
x2go-DEBUG-../src/sessionbutton.cpp:361> Creating QPixmap with session icon: ":/img/icons/128x128/x2gosession.png".
x2go-DEBUG-../src/onmainwindow.cpp:13290> libssh not initialized yet. Initializing.
x2go-DEBUG-../src/onmainwindow.cpp:2752> Creating QPixmap with session icon: '":/img/icons/128x128/x2gosession.png"'.
x2go-DEBUG-../src/onmainwindow.cpp:2819> Starting session via Smart Card, SSH Agent or Kerberos token.
x2go-INFO-8> "Starting connection to server: 192.168.1.165:46182"
x2go-DEBUG-../src/onmainwindow.cpp:2853> Starting new ssh connection to server:"192.168.1.165":"46182" krbLogin: false
x2go-DEBUG-../src/sshmasterconnection.cpp:168> SshMasterConnection, host "192.168.1.165"; port 46182; user "liz"; useproxy false; proxyserver ""; proxyport 22
x2go-DEBUG-../src/sshmasterconnection.cpp:248> Starting SSH connection without Kerberos authentication.
x2go-DEBUG-../src/sshmasterconnection.cpp:250> SshMasterConnection, instance SshMasterConnection(0x5638f0a448e0) created.
x2go-DEBUG-../src/sshmasterconnection.cpp:495> SshMasterConnection, instance SshMasterConnection(0x5638f0a448e0) entering thread.
x2go-DEBUG-../src/sshmasterconnection.cpp:797> Session port before config file parse: 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:807> Session port after config file parse: 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:870> Session port before config file parse (part 2): 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:880> Session port after config file parse (part 2): 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:904> cserverAuth
x2go-DEBUG-../src/sshmasterconnection.cpp:943> state: 1

x2go-DEBUG-../src/sshmasterconnection.cpp:687> User authentication OK.
x2go-DEBUG-../src/sshmasterconnection.cpp:1708> LOGIN CHECK:"LOGIN OK\r\n"
x2go-DEBUG-../src/sshmasterconnection.cpp:1711> don't have interaction
x2go-DEBUG-../src/sshmasterconnection.cpp:1744> LOOP FINISHED
x2go-DEBUG-../src/sshmasterconnection.cpp:1748> No interaction needed, continue session
x2go-DEBUG-../src/sshmasterconnection.cpp:702> Login Check - OK
x2go-DEBUG-../src/onmainwindow.cpp:2947> SSH connection established.
x2go-DEBUG-../src/onmainwindow.cpp:3374> Continue normal X2Go session
x2go-DEBUG-../src/sshprocess.cpp:199> Executing remote command via SshProcess object 0: "x2golistsessions"
x2go-DEBUG-../src/sshprocess.cpp:213> this=SshProcess(0x5638f0c3a900) Running masterCon->addChannelConnection(this, '"b126a319-9279-48c5-a9ce-44e6a0817a4b"', '"bash -l -c 'echo \"X2GODATABEGIN:b126a319-9279-48c5-a9ce-44e6a0817a4b\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2golistsessions; echo \"X2GODATAEND:b126a319-9279-48c5-a9ce-44e6a0"');
x2go-DEBUG-../src/sshmasterconnection.cpp:1810> Locking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1812> Passing new channel connection object to channelConnections.
x2go-DEBUG-../src/sshmasterconnection.cpp:1814> Unlocking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1977> Creating new channel.

x2go-DEBUG-../src/sshmasterconnection.cpp:1990> New channel:0x7fcc680bb380

x2go-DEBUG-../src/sshmasterconnection.cpp:2065> Executing remote: "bash -l -c 'echo \"X2GODATABEGIN:b126a319-9279-48c5-a9ce-44e6a0817a4b\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2golistsessions; echo \"X2GODATAEND:b126a319-9279-48c5-a9ce-44e6a0817a4b\";'"

x2go-DEBUG-../src/sshmasterconnection.cpp:2082> New exec channel created.

x2go-DEBUG-../src/sshmasterconnection.cpp:2121> EOF on channel 0x7fcc680bb380; SshProcess object: 0
x2go-DEBUG-../src/sshmasterconnection.cpp:2222> EOF sent.
x2go-DEBUG-../src/sshmasterconnection.cpp:2224> Channel closed.
x2go-DEBUG-../src/sshprocess.cpp:532> SSH finished: raw output (stdout): "X2GODATABEGIN:b126a319-9279-48c5-a9ce-44e6a0817a4b\nX2GODATAEND:b126a319-9279-48c5-a9ce-44e6a0817a4b\n"
x2go-DEBUG-../src/sshprocess.cpp:543> SSH finished: true - "" (0).
x2go-DEBUG-../src/onmainwindow.cpp:3861> ""
x2go-DEBUG-../src/onmainwindow.cpp:4521> Executing remote command: "X2GO_XINERAMA=no x2gostartagent 800x600 lan 16m-jpeg-9 unix-kde-depth_24 us auto 1 D MATE both"
x2go-DEBUG-../src/sshprocess.cpp:199> Executing remote command via SshProcess object 1: "X2GO_XINERAMA=no x2gostartagent 800x600 lan 16m-jpeg-9 unix-kde-depth_24 us auto 1 D MATE both"
x2go-DEBUG-../src/sshprocess.cpp:213> this=SshProcess(0x5638f0c2d920) Running masterCon->addChannelConnection(this, '"775cddd2-038d-4afa-89ed-8f07f05459cd"', '"bash -l -c 'echo \"X2GODATABEGIN:775cddd2-038d-4afa-89ed-8f07f05459cd\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; X2GO_XINERAMA=no x2gostartagent 800x600 lan 16m-jpeg-9 unix-kde-de"');
x2go-DEBUG-../src/sshmasterconnection.cpp:1810> Locking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1812> Passing new channel connection object to channelConnections.
x2go-DEBUG-../src/sshmasterconnection.cpp:1814> Unlocking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1977> Creating new channel.

x2go-DEBUG-../src/sshmasterconnection.cpp:1990> New channel:0x7fcc680bbf90

x2go-DEBUG-../src/sshmasterconnection.cpp:2065> Executing remote: "bash -l -c 'echo \"X2GODATABEGIN:775cddd2-038d-4afa-89ed-8f07f05459cd\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; X2GO_XINERAMA=no x2gostartagent 800x600 lan 16m-jpeg-9 unix-kde-depth_24 us auto 1 D MATE both; echo \"X2GODATAEND:775cddd2-038d-4afa-89ed-8f07f05459cd\";'"

x2go-DEBUG-../src/sshmasterconnection.cpp:2082> New exec channel created.

x2go-DEBUG-../src/sshmasterconnection.cpp:2121> EOF on channel 0x7fcc680bbf90; SshProcess object: 1
x2go-DEBUG-../src/sshmasterconnection.cpp:2222> EOF sent.
x2go-DEBUG-../src/sshmasterconnection.cpp:2224> Channel closed.
x2go-DEBUG-../src/sshprocess.cpp:532> SSH finished: raw output (stdout): "X2GODATABEGIN:775cddd2-038d-4afa-89ed-8f07f05459cd\n50\nf1d5132a7bd2046b38baed9026c13fd7\n2459\nliz-50-1678042953_stDMATE_dp24\n53364\n53365\n53366\nX2GODATAEND:775cddd2-038d-4afa-89ed-8f07f05459cd\n"
x2go-DEBUG-../src/sshprocess.cpp:543> SSH finished: true - "50\nf1d5132a7bd2046b38baed9026c13fd7\n2459\nliz-50-1678042953_stDMATE_dp24\n53364\n53365\n53366\n" (1).
x2go-DEBUG-../src/onmainwindow.cpp:5425> Agent output: "50\nf1d5132a7bd2046b38baed9026c13fd7\n2459\nliz-50-1678042953_stDMATE_dp24\n53364\n53365\n53366\n"
x2go-DEBUG-../src/sshprocess.cpp:387> Starting tunnel via SshProcess object 2: "localhost":53364 -> "localhost":54364

RESUMING SESSION is KDRIVE:  false
x2go-DEBUG-../src/onmainwindow.cpp:6142> "Starting NX proxy, command: nxproxy -S nx/nx,options=/home/dad/.x2go/S-liz-50-1678042953_stDMATE_dp24/options:50"
x2go-DEBUG-../src/sshprocess.cpp:157> Direct tunnel: waiting for connections on "localhost":54364
x2go-DEBUG-../src/onmainwindow.cpp:6618> Proxy wrote on stderr: "\nNXPROXY - Version 3.5.99.26\n\nCopyright (c) 2001, 2011 NoMachine (http://www.nomachine.com)\nCopyright (c) 2008-2014 Oleksandr Shneyder <o.shneyder@phoca-gmbh.de>\nCopyright (c) 2014-2016 Ulrich Sibiller <uli42@gmx.de>\nCopyright (c) 2014-2016 Mihai Moldovan <ionic@ionic.de>\nCopyright (c) 2011-2016 Mike Gabriel <mike.gabriel@das-netzwerkteam.de>\nCopyright (c) 2015-2016 Qindel Group (http://www.qindel.com)\n\nNXCOMP, NX protocol compression and NX extensions to this software\nare copyright of the aforementioned persons and companies.\n\nRedistribution and use of the present software is allowed according\nto terms specified in the file LICENSE.nxcomp which comes in the\nsource distribution.\n\nAll rights reserved.\n\nNOTE: This software has received contributions from various other\ncontributors, only the core maintainers and supporters are listed as\ncopyright holders. Please contact us, if you feel you should be listed\nas copyright holder, as well.\n\nNX protocol compression is derived from DXPC project.\n\nCopyright (c) 1995,1996 Brian Pane\nCopyright (c) 1996,1997 Zachary Vonler and Brian Pane\nCopyright (c) 1999 Kevin Vigor and Brian Pane\nCopyright (c) 2000,2003 Gian Filippo Pinzari and Brian Pane\n\nAll rights reserved.\n\nSee https://github.com/ArcticaProject/nx-libs for more information.\n\nInfo: Proxy running in server mode with pid '5386'.\nSession: Starting session at 'Sun Mar  5 19:02:34 2023'.\nInfo: Using errors file '/home/dad/.x2go/S-liz-50-1678042953_stDMATE_dp24/sessions'.\nInfo: Using stats file '/home/dad/.x2go/S-50/stats'.\nLoop: WARNING! Overriding auxiliary X11 port with new value '1'.\nWarning: Overriding auxiliary X11 port with new value '1'.\nInfo: Using abstract X11 socket in kernel namespace for accessing DISPLAY=:0.\nInfo: Connecting to remote host 'localhost:54364'.\nInfo: Connected to remote proxy on FD#5.\n"
x2go-DEBUG-../src/sshprocess.cpp:109> New TCP connection.
x2go-DEBUG-../src/sshprocess.cpp:114> New socket: 25
x2go-DEBUG-../src/sshmasterconnection.cpp:1977> Creating new channel.

x2go-DEBUG-../src/sshmasterconnection.cpp:1990> New channel:0x7fcc680bbf90

x2go-DEBUG-../src/sshmasterconnection.cpp:1994> Forwarding parameters: from remote ("localhost":53364) to local ("localhost":48188)
x2go-DEBUG-../src/sshmasterconnection.cpp:2028> Temporary session port after config file parse: 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:2032> Temporary session host after config file parse: localhost
x2go-DEBUG-../src/sshmasterconnection.cpp:2059> New channel forwarded.

x2go-DEBUG-../src/onmainwindow.cpp:6618> Proxy wrote on stderr: "Loop: PANIC! Parse error in remote options string 'SSH-2.0-OpenSSH_8.2p1 '.\nError: Parse error in remote options string 'SSH-2.0-OpenSSH_8.2p1 '.\nLoop: PANIC! Failure negotiating the session in stage '7'.\nError: Failure negotiating the session in stage '7'.\nLoop: PANIC! Wrong version or invalid session authentication cookie.\nError: Wrong version or invalid session authentication cookie.\nSession: Terminating session at 'Sun Mar  5 19:02:34 2023'.\nSession: Session terminated at 'Sun Mar  5 19:02:34 2023'.\n"
x2go-DEBUG-../src/sshmasterconnection.cpp:2199> "Error reading from TCP socket." - ""

x2go-DEBUG-../src/sshmasterconnection.cpp:2222> EOF sent.
x2go-DEBUG-../src/sshmasterconnection.cpp:2224> Channel closed.
x2go-DEBUG-../src/sshprocess.cpp:478> I/O error: "Error reading from TCP socket.""" (2).
x2go-DEBUG-../src/onmainwindow.cpp:6475> Deleting Proxy.
x2go-DEBUG-../src/onmainwindow.cpp:6520> Waiting for proxy to exit.
x2go-DEBUG-../src/onmainwindow.cpp:6544> Checking exit status.
x2go-DEBUG-../src/sshprocess.cpp:199> Executing remote command via SshProcess object 3: "x2gocmdexitmessage liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/sshprocess.cpp:213> this=SshProcess(0x5638f0d1b300) Running masterCon->addChannelConnection(this, '"3de2e793-9bd6-4909-a3ff-740ad09be997"', '"bash -l -c 'echo \"X2GODATABEGIN:3de2e793-9bd6-4909-a3ff-740ad09be997\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2gocmdexitmessage liz-50-1678042953_stDMATE_dp24; echo \"X2GODATAE"');
x2go-DEBUG-../src/sshmasterconnection.cpp:1810> Locking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1812> Passing new channel connection object to channelConnections.
x2go-DEBUG-../src/sshmasterconnection.cpp:1814> Unlocking SSH channel connection MUTEX.
x2go-DEBUG-../src/onmainwindow.cpp:6601> Finished proxy.
x2go-DEBUG-../src/sshmasterconnection.cpp:1977> Creating new channel.

x2go-DEBUG-../src/sshmasterconnection.cpp:1990> New channel:0x7fcc680bbf90

x2go-DEBUG-../src/sshmasterconnection.cpp:2065> Executing remote: "bash -l -c 'echo \"X2GODATABEGIN:3de2e793-9bd6-4909-a3ff-740ad09be997\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2gocmdexitmessage liz-50-1678042953_stDMATE_dp24; echo \"X2GODATAEND:3de2e793-9bd6-4909-a3ff-740ad09be997\";'"

x2go-DEBUG-../src/sshmasterconnection.cpp:2082> New exec channel created.

x2go-DEBUG-../src/sshmasterconnection.cpp:2121> EOF on channel 0x7fcc680bbf90; SshProcess object: 3
x2go-DEBUG-../src/sshmasterconnection.cpp:2222> EOF sent.
x2go-DEBUG-../src/sshmasterconnection.cpp:2224> Channel closed.
x2go-DEBUG-../src/sshprocess.cpp:532> SSH finished: raw output (stdout): "X2GODATABEGIN:3de2e793-9bd6-4909-a3ff-740ad09be997\nX2GODATAEND:3de2e793-9bd6-4909-a3ff-740ad09be997\n"
x2go-DEBUG-../src/sshprocess.cpp:543> SSH finished: true - "" (3).
x2go-DEBUG-../src/onmainwindow.cpp:9933> "Command message: "
x2go-DEBUG-../src/sshmasterconnection.cpp:764> SshMasterConnection, instance SshMasterConnection(0x5638f0a448e0) waiting for thread to finish.
x2go-DEBUG-../src/sshmasterconnection.cpp:1908> Disconnecting ...

x2go-DEBUG-../src/sshmasterconnection.cpp:1917> Deleting channel connections.

x2go-DEBUG-../src/sshmasterconnection.cpp:1923> Disconnecting session.

x2go-DEBUG-../src/sshmasterconnection.cpp:1927> Deleting sockets.

x2go-DEBUG-../src/sshmasterconnection.cpp:1932> All channels closed and session disconnected. Quitting session loop.

x2go-DEBUG-../src/sshmasterconnection.cpp:766> SshMasterConnection, instance SshMasterConnection(0x5638f0a448e0) thread finished.
x2go-DEBUG-../src/sshprocess.cpp:52> SshProcess destructor called.
x2go-DEBUG-../src/sshprocess.cpp:52> SshProcess destructor called.
x2go-DEBUG-../src/sshprocess.cpp:52> SshProcess destructor called.
x2go-DEBUG-../src/sshprocess.cpp:52> SshProcess destructor called.
x2go-DEBUG-../src/sshmasterconnection.cpp:771> SshMasterConnection, instance SshMasterConnection(0x5638f0a448e0) finished destructor.
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-liz-50-1678042953_stDMATE_dp24"
x2go-INFO-8> "Starting connection to server: 192.168.1.165:46182"
x2go-DEBUG-../src/onmainwindow.cpp:2853> Starting new ssh connection to server:"192.168.1.165":"46182" krbLogin: false
x2go-DEBUG-../src/sshmasterconnection.cpp:168> SshMasterConnection, host "192.168.1.165"; port 46182; user "liz"; useproxy false; proxyserver ""; proxyport 22
x2go-DEBUG-../src/sshmasterconnection.cpp:248> Starting SSH connection without Kerberos authentication.
x2go-DEBUG-../src/sshmasterconnection.cpp:250> SshMasterConnection, instance SshMasterConnection(0x7fccb4008d10) created.
x2go-DEBUG-../src/sshmasterconnection.cpp:495> SshMasterConnection, instance SshMasterConnection(0x7fccb4008d10) entering thread.
x2go-DEBUG-../src/sshmasterconnection.cpp:797> Session port before config file parse: 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:807> Session port after config file parse: 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:870> Session port before config file parse (part 2): 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:880> Session port after config file parse (part 2): 46182
x2go-DEBUG-../src/sshmasterconnection.cpp:904> cserverAuth
x2go-DEBUG-../src/sshmasterconnection.cpp:943> state: 1

x2go-DEBUG-../src/sshmasterconnection.cpp:687> User authentication OK.
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/sshmasterconnection.cpp:1708> LOGIN CHECK:"LOGIN OK\r\n"
x2go-DEBUG-../src/sshmasterconnection.cpp:1711> don't have interaction
x2go-DEBUG-../src/sshmasterconnection.cpp:1744> LOOP FINISHED
x2go-DEBUG-../src/sshmasterconnection.cpp:1748> No interaction needed, continue session
x2go-DEBUG-../src/sshmasterconnection.cpp:702> Login Check - OK
x2go-DEBUG-../src/onmainwindow.cpp:2947> SSH connection established.
x2go-DEBUG-../src/onmainwindow.cpp:3374> Continue normal X2Go session
x2go-DEBUG-../src/sshprocess.cpp:199> Executing remote command via SshProcess object 0: "x2golistsessions"
x2go-DEBUG-../src/sshprocess.cpp:213> this=SshProcess(0x5638f0d1b300) Running masterCon->addChannelConnection(this, '"412051e5-6c90-4083-afc7-70e6dcc10d72"', '"bash -l -c 'echo \"X2GODATABEGIN:412051e5-6c90-4083-afc7-70e6dcc10d72\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2golistsessions; echo \"X2GODATAEND:412051e5-6c90-4083-afc7-70e6dc"');
x2go-DEBUG-../src/sshmasterconnection.cpp:1810> Locking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1812> Passing new channel connection object to channelConnections.
x2go-DEBUG-../src/sshmasterconnection.cpp:1814> Unlocking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1977> Creating new channel.

x2go-DEBUG-../src/sshmasterconnection.cpp:1990> New channel:0x7fcc68000f80

x2go-DEBUG-../src/sshmasterconnection.cpp:2065> Executing remote: "bash -l -c 'echo \"X2GODATABEGIN:412051e5-6c90-4083-afc7-70e6dcc10d72\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2golistsessions; echo \"X2GODATAEND:412051e5-6c90-4083-afc7-70e6dcc10d72\";'"

x2go-DEBUG-../src/sshmasterconnection.cpp:2082> New exec channel created.

x2go-DEBUG-../src/sshmasterconnection.cpp:2121> EOF on channel 0x7fcc68000f80; SshProcess object: 0
x2go-DEBUG-../src/sshmasterconnection.cpp:2222> EOF sent.
x2go-DEBUG-../src/sshmasterconnection.cpp:2224> Channel closed.
x2go-DEBUG-../src/sshprocess.cpp:532> SSH finished: raw output (stdout): "X2GODATABEGIN:412051e5-6c90-4083-afc7-70e6dcc10d72\n2459|liz-50-1678042953_stDMATE_dp24|50|lizubuntu|R|2023-03-05T19:02:33|f1d5132a7bd2046b38baed9026c13fd7|192.168.1.145|53364|53365|2023-03-05T19:02:34|liz|8|53366|-1|-1\nX2GODATAEND:412051e5-6c90-4083-afc7-70e6dcc10d72\n"
x2go-DEBUG-../src/sshprocess.cpp:543> SSH finished: true - "2459|liz-50-1678042953_stDMATE_dp24|50|lizubuntu|R|2023-03-05T19:02:33|f1d5132a7bd2046b38baed9026c13fd7|192.168.1.145|53364|53365|2023-03-05T19:02:34|liz|8|53366|-1|-1\n" (0).
x2go-DEBUG-../src/onmainwindow.cpp:3861> "2459|liz-50-1678042953_stDMATE_dp24|50|lizubuntu|R|2023-03-05T19:02:33|f1d5132a7bd2046b38baed9026c13fd7|192.168.1.145|53364|53365|2023-03-05T19:02:34|liz|8|53366|-1|-1\n"
x2go-DEBUG-../src/onmainwindow.cpp:4864> No shadow session.
x2go-DEBUG-../src/onmainwindow.cpp:4887> "Decoding session string:2459|liz-50-1678042953_stDMATE_dp24|50|lizubuntu|R|2023-03-05T19:02:33|f1d5132a7bd2046b38baed9026c13fd7|192.168.1.145|53364|53365|2023-03-05T19:02:34|liz|8|53366|-1|-1"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:11659> "Searching proxy window: X2GO-"
x2go-DEBUG-../src/onmainwindow.cpp:13278> "Searching window with title: X2GO-"

```

---

### Post by Quarkrad on 2023-03-05
```
x2go-DEBUG-../src/onmainwindow.cpp:6618> Proxy wrote on stderr: "Loop: PANIC! Parse error in remote options string 'SSH-2.0-OpenSSH_8.2p1 '.\nError: Parse error in remote options string 'SSH-2.0-OpenSSH_8.2p1 '.\nLoop: PANIC! Failure negotiating the session in stage '7'.\nError: Failure negotiating the session in stage '7'.\nLoop: PANIC! Wrong version or invalid session authentication cookie.\nError: Wrong version or invalid session authentication cookie.\nSession: Terminating session at 'Sun Mar  5 19:02:34 2023'.\nSession: Session terminated at 'Sun Mar  5 19:02:34 2023'.\n"
x2go-DEBUG-../src/sshmasterconnection.cpp:2199> "Error reading from TCP socket." - ""
```

---

### Post by Quarkrad on 2023-03-05
For some reason text is being deleted.

x2go-DEBUG-../src/onmainwindow.cpp:6618> Proxy wrote on stderr: "Loop: PANIC! Parse error in remote options string 'SSH-2.0-OpenSSH_8.2p1 '.\nError: Parse error in remote options string 'SSH-2.0-OpenSSH_8.2p1 '.\nLoop: PANIC! Failure negotiating the session in stage '7'.\nError: Failure negotiating the session in stage '7'.\nLoop: PANIC! Wrong version or invalid session authentication cookie.\nError: Wrong version or invalid session authentication cookie.\nSession: Terminating session at 'Sun Mar  5 19:02:34 2023'.\nSession: Session terminated at 'Sun Mar  5 19:02:34 2023'.\n"
x2go-DEBUG-../src/sshmasterconnection.cpp:2199> "Error reading from TCP socket." - ""

---

### Post by #&amp;thj^% on 2023-03-05
> **Quarkrad said:**
> ```
x2go-DEBUG-../src/onmainwindow.cpp:6618> Proxy wrote on stderr: "Loop: PANIC! Parse error in remote options string 'SSH-2.0-OpenSSH_8.2p1 '.\nError: Parse error in remote options string 'SSH-2.0-OpenSSH_8.2p1 '.\nLoop: PANIC! Failure negotiating the session in stage '7'.\nError: Failure negotiating the session in stage '7'.\nLoop: PANIC! Wrong version or invalid session authentication cookie.\nError: Wrong version or invalid session authentication cookie.\nSession: Terminating session at 'Sun Mar  5 19:02:34 2023'.\nSession: Session terminated at 'Sun Mar  5 19:02:34 2023'.\n"
x2go-DEBUG-../src/sshmasterconnection.cpp:2199> "Error reading from TCP socket." - ""
```

Yes Sir, this is the one needed..
just for testing only, will you cp your .Xauthority in the home directory and move it out of home, and try again.
These errors are the first I've seen on x2go

---

### Post by Quarkrad on 2023-03-06
Seem to have another problem now - hard to describe so I've given link of my Desktop (screen recorder).  The commands in the terminal start to disappear - so it is difficult to copy and paste what is happening. 

[https://www.dropbox.com/s/qufms2e3jmakwfi/x2go.mkv?dl=0](https://www.dropbox.com/s/qufms2e3jmakwfi/x2go.mkv?dl=0)

Is there a some way of printing the terminal output to a text file as they are appearing in real time?  At the x2go window asking for the password - it doesn't matter whether I put in the password or not, the terminal text starts to disappear.

---

### Post by #&amp;thj^% on 2023-03-06
> **Quarkrad said:**
> 
Is there a some way of printing the terminal output to a text file as they are appearing in real time?  At the x2go window asking for the password - it doesn't matter whether I put in the password or not, the terminal text starts to disappear.
I've seen the disappearing text before, as for printing in real time try this:
```
x2goclient && tail -f /var/log/syslog

```

---

### Post by Quarkrad on 2023-03-06
Thank you for your help.  This is the output in syslog.

```
Mar  6 20:19:16 dadubuntu pulseaudio[1878]: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Mar  6 20:19:18 dadubuntu systemd-timesyncd[964]: Initial synchronization to time server [2620:2d:4000:1::40]:123 (ntp.ubuntu.com).
Mar  6 20:19:19 dadubuntu systemd[1]: blueman-mechanism.service: Deactivated successfully.
Mar  6 20:19:19 dadubuntu systemd[1]: systemd-fsckd.service: Deactivated successfully.
Mar  6 20:19:20 dadubuntu brisk-menu[2616]: gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed
Mar  6 20:19:20 dadubuntu brisk-menu[2616]: gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed
Mar  6 20:19:21 dadubuntu systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Mar  6 20:19:22 dadubuntu systemd[1]: systemd-timedated.service: Deactivated successfully.
Mar  6 20:19:46 dadubuntu dbus-daemon[1311]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.91' (uid=1000 pid=3580 comm="pluma /var/log/syslog " label="unconfined")
Mar  6 20:19:46 dadubuntu systemd[1]: Starting Hostname Service...
Mar  6 20:19:46 dadubuntu dbus-daemon[1311]: [system] Successfully activated service 'org.freedesktop.hostname1'
Mar  6 20:19:46 dadubuntu systemd[1]: Started Hostname Service.
Mar  6 20:20:05 dadubuntu wnck-applet[2612]: Negative content width -1 (allocation 1, extents 1x1) while allocating gadget (node button, owner WnckButton)
Mar  6 20:20:05 dadubuntu systemd[1854]: Started snap.firefox.firefox.17bad7b7-b3c1-4c0f-a268-eb371f118d7e.scope.
Mar  6 20:20:05 dadubuntu kernel: [   80.616336] kauditd_printk_skb: 3 callbacks suppressed
Mar  6 20:20:05 dadubuntu kernel: [   80.616337] audit: type=1400 audit(1678134005.694:109): apparmor="DENIED" operation="capable" profile="/snap/snapd/18357/usr/lib/snapd/snap-confine" pid=3820 comm="snap-confine" capability=12  capname="net_admin"
Mar  6 20:20:05 dadubuntu kernel: [   80.616340] audit: type=1400 audit(1678134005.694:110): apparmor="DENIED" operation="capable" profile="/snap/snapd/18357/usr/lib/snapd/snap-confine" pid=3820 comm="snap-confine" capability=38  capname="perfmon"
Mar  6 20:20:05 dadubuntu wnck-applet[2612]: Negative content width -1 (allocation 1, extents 1x1) while allocating gadget (node button, owner WnckButton)
Mar  6 20:20:05 dadubuntu systemd[1]: tmp-snap.rootfs_aaeZvY.mount: Deactivated successfully.
Mar  6 20:20:05 dadubuntu kernel: [   80.653131] audit: type=1400 audit(1678134005.730:111): apparmor="DENIED" operation="open" profile="snap-update-ns.firefox" name="/var/lib/" pid=3846 comm="5" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Mar  6 20:20:05 dadubuntu kernel: [   80.654246] audit: type=1400 audit(1678134005.734:112): apparmor="DENIED" operation="open" profile="snap-update-ns.firefox" name="/var/lib/" pid=3846 comm="5" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Mar  6 20:20:06 dadubuntu kernel: [   80.980370] audit: type=1326 audit(1678134006.058:113): auid=4294967295 uid=1000 gid=1000 ses=4294967295 subj=snap.firefox.firefox pid=3820 comm="firefox" exe="/snap/firefox/2391/usr/lib/firefox/firefox" sig=0 arch=c000003e syscall=314 compat=0 ip=0x7f3d57d3873d code=0x50000
Mar  6 20:20:06 dadubuntu rtkit-daemon[1899]: Supervising 7 threads of 3 processes of 1 users.
Mar  6 20:20:06 dadubuntu rtkit-daemon[1899]: message repeated 5 times: [ Supervising 7 threads of 3 processes of 1 users.]
Mar  6 20:20:06 dadubuntu rtkit-daemon[1899]: Successfully made thread 4047 of process 3820 owned by '1000' RT at priority 10.
Mar  6 20:20:06 dadubuntu rtkit-daemon[1899]: Supervising 8 threads of 4 processes of 1 users.
Mar  6 20:20:06 dadubuntu dbus-daemon[1913]: [session uid=1000 pid=1913] Activating service name='io.snapcraft.Settings' requested by ':1.98' (uid=1000 pid=4054 comm="dbus-send --print-reply=literal --session --dest=i" label="snap.firefox.firefox (enforce)")
Mar  6 20:20:06 dadubuntu dbus-daemon[1913]: [session uid=1000 pid=1913] Successfully activated service 'io.snapcraft.Settings'
Mar  6 20:20:06 dadubuntu io.snapcraft.Settings[4057]: userd.go:93: Starting snap userd
Mar  6 20:20:06 dadubuntu rtkit-daemon[1899]: Supervising 8 threads of 4 processes of 1 users.
Mar  6 20:20:10 dadubuntu rtkit-daemon[1899]: message repeated 11 times: [ Supervising 8 threads of 4 processes of 1 users.]
Mar  6 20:20:17 dadubuntu systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Mar  6 20:20:18 dadubuntu rtkit-daemon[1899]: Supervising 8 threads of 4 processes of 1 users.
Mar  6 20:20:18 dadubuntu rtkit-daemon[1899]: Supervising 8 threads of 4 processes of 1 users.
Mar  6 20:20:26 dadubuntu systemd[1854]: snap.firefox.firefox.17bad7b7-b3c1-4c0f-a268-eb371f118d7e.scope: Consumed 11.448s CPU time.
Mar  6 20:20:27 dadubuntu wnck-applet[2612]: Negative content width -1 (allocation 1, extents 1x1) while allocating gadget (node button, owner WnckButton)
```

---

### Post by Quarkrad on 2023-03-06
I re-booted pc.  The  syslog file went to line 2488.  Then I ran your command - the above is from line 2489 to the bottom.

---

### Post by #&amp;thj^% on 2023-03-06
My friend I'm not going to able to help you, snaps are involved and i don't use a snap system.
My best advice in to head over to x2go support and open a support request there, I'm truly sorry.

---

### Post by Quarkrad on 2023-03-06
OK again , thank you for your time.  This was working OK - perhaps something re a snap update has caused the problem.  If I get a solution I will post it here for others to reference.

---

### Post by #&amp;thj^% on 2023-03-06
This is the part that troubles me:
```
DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Mar  6 20:19:18 dadubuntu systemd-timesyncd[964]: Initial synchronization to time server [2620:2d:4000:1::40]:123 (ntp.ubuntu.com).
Mar  6 20:19:19 dadubuntu systemd[1]: blueman-mechanism.service: Deactivated successfully.
```

---

### Post by Quarkrad on 2023-03-09
I found one other ref on the web to a similar problem and the same output error text - but that was never answered so I'm thinking perhaps this is one of those one off's that is not worth the effort to fix (if it can).  I built a vm with a similar snap build and everything looked to be ok.  So ... as I have done a recent re-build and still not finished I started all over again (actually, just re installing* /*).  This time x2goclient is working fine even with the horrid snap!  Thank you again for your time.

---

### Post by TheFu on 2023-03-09
> **Quarkrad said:**
> Seem to have another problem now - hard to describe so I've given link of my Desktop (screen recorder).  The commands in the terminal start to disappear - so it is difficult to copy and paste what is happening. 

[https://www.dropbox.com/s/qufms2e3jmakwfi/x2go.mkv?dl=0](https://www.dropbox.com/s/qufms2e3jmakwfi/x2go.mkv?dl=0)

Is there a some way of printing the terminal output to a text file as they are appearing in real time?  At the x2go window asking for the password - it doesn't matter whether I put in the password or not, the terminal text starts to disappear.

The video seems like a slow refresh issue only. Nothing nefarious.
BTW, when you didn't enter the password, I was screaming at the computer for you to do that. ;)  Like many GUI programs, x2go spews lots of information messages in --debug mode.

If you aren't using the standard ssh port, please setup a ~/.ssh/config file on the client-side so you don't have to enter the non-standard port ever again ... and if the userid is different, I'd put that in there too. All ssh-based tools will pick up those things. It is handy to have them documented in a text file too. ;)  If you don't have DNS setup, you can even use the ~/.ssh/config file to provide something like that for all ssh-based connections too.
```
host xubu-2204
  user backup32149
  port 62022
  hostname 172.22.22.246

```
So anywhere I'd enter the port, IP and/or different username I don't need to anymore.  
```
ssh xubu-2204
```
is sufficient.  x2go using that same **xubu-2204** will do the same.  The entries for that file are documented in the ssh_config manpage.

I haven't read most of the other parts to this thread yet.  I don't have 22.04 Mate.

---

### Post by TheFu on 2023-03-09
I see you have a session running for liz still.  Double click on that line - does that not open the session?
BTW, I unusually tweak the x2go session parameters a bit to get better performance.
[LIST]
[*]Set the network bandwidth level to be 1 less than you actually have
[*]Set the image transfers to be 4K-png
[*]Disable printer sharing
[*]Disable audio
[*]Disable file sharing.
[/LIST]

My desktop seems to be too old for x2goclient now.  I'm getting errors trying to run it and trying to --reinstall the client.  Yet another reason why I need to move to a newer release on that system. Sigh.

Tried running x2go over remote X11 ... and that didn't work. I remember doing it years ago without problems.  I use x2go mostly for remote connections over the internet. Locally, I use **ssh -X** or spice to get a full desktop on a running VM.

---

### Post by #&amp;thj^% on 2023-03-09
> **Quarkrad said:**
> I found one other ref on the web to a similar problem and the same output error text - but that was never answered so I'm thinking perhaps this is one of those one off's that is not worth the effort to fix (if it can).  I built a vm with a similar snap build and everything looked to be ok.  So ... as I have done a recent re-build and still not finished I started all over again (actually, just re installing* /*).  This time x2goclient is working fine even with the horrid snap!  Thank you again for your time.

Interesting, thanks for posting back, with how you solved this.

---

