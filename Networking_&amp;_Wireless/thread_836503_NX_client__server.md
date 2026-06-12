---
title: "NX client / server"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by chris.tkd on 2008-06-21
Hello, 

Im trying to set up the nx client and server so im able to remote desktop from an ubuntu machine to another ubuntu machine.

Ive set up the server, and the client. When i try to connect it gives me an error.

NX> 203 NXSSH running with pid: 9961
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.6 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-13 - LFE
NX> 105 Hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: chris
NX> 102 Password: ********
NX> 103 Welcome to: chris-linux user: chris
NX> 105 Listsession --user="chris" --status="suspended\054running" --geometry="1280x1024x24+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: chris
NX> 105 Start session with: --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="vnc" --type="unix-gnome" --geometry="1024x768+128+103" --client="linux" --keyboard="pc105\057gb" --screeninfo="1024x768x24+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 7401ECBC. To get detailed information about
NX> 595 ERROR: the error search for the string 7401ECBC in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15

When i check the log file for the number it isnt in there, the only NX logs are

Jun 21 19:00:05 chris-linux-desktop NXSERVER-3.2.0-13[6378]: User 'chris' logged in from '192.168.1.6'. 'NXLogin::set'
Jun 21 19:00:08 chris-linux-desktop NXSERVER-3.2.0-13[6378]: Selected node host:localhost with port:22 'main::selectNode'
Jun 21 19:00:08 chris-linux-desktop NXSERVER-3.2.0-13[6378]: Current selected node: localhost is in status: running  'main::selectNode'
Jun 21 19:00:08 chris-linux-desktop NXSERVER-3.2.0-13[6378]: Selected session type: unix-gnome allowed in the profile of user: chris 'NXShell::Static'
Jun 21 19:00:11 chris-linux-desktop NXSERVER-3.2.0-13[6378]: Session '3DFEA14409311307DBB053BC534707EE' started by user 'chris'. 'NXShell::handler_session_start'
Jun 21 19:00:11 chris-linux-desktop NXSERVER-3.2.0-13[6378]: User 'chris' from '192.168.1.6' logged out. 'NXLogin::reset'
Jun 21 19:00:12 chris-linux-desktop NXNODE-3.2.0-10[6393]: Using port '1002' on node 'chris-linux-desktop' for session 'unix-gnome'. Logger::log nxnode 6035
Jun 21 19:00:12 chris-linux-desktop NXNODE-3.2.0-10[6393]: Using host from available host list: '192.168.1.2'. Logger::log nxnode 6036
Jun 21 19:01:25 chris-linux-desktop NXNODE-3.2.0-10[6393]: Session 'unix-gnome' on port '1002' closed. Logger::log nxnode 6313
Jun 21 19:01:27 chris-linux-desktop NXSERVER-3.2.0-13[6420]: session sessionId:3DFEA14409311307DBB053BC534707EE finished 'NXShell::handler_session_start'
Jun 21 19:01:27 chris-linux-desktop NXSERVER-3.2.0-13[6420]: Session '3DFEA14409311307DBB053BC534707EE' closed by user 'chris'. 'NXShell::Static'
Jun 21 19:05:16 chris-linux-desktop NXSERVER-3.2.0-13[7178]: Cannot read from stdin: NX client disconnected before the 'bye' message: exiting cleanly 'NXShell::handleExitRequests'

Has anyone any idea whats causing this error?

Thanks,
Chris.

---

### Post by chris.tkd on 2008-06-21
bump

---

