---
title: "NX Server problems"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by nukie77 on 2008-07-02
I had NX server running on my 8.04 box so that I could control it as a headless server from my Vista box.  I installed it and had no problems connecting with the windows client.  But all of the sudden last week I started to get a server configuration error when trying to connect.  Below are the details:


NX> 203 NXSSH running with pid: 3872
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.138 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-13 - LFE
NX> 105 Hello NXCLIENT - Version 3.1.0
NX> 134 Accepted protocol: 3.1.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: george
NX> 102 Password: *********
NX> 103 Welcome to: batlin user: george
NX> 105 Listsession --user="george" --status="suspended\054running" --geometry="1680x1050x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: george
NX> 105 Start session with: --link="lan" --backingstore="1" --encryption="1" --cache="64M" --images="256M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Batlin" --type="unix-gnome" --geometry="1680x1020" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="1680x1020x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: B0C0FD66. To get detailed information about
NX> 595 ERROR: the error search for the string B0C0FD66 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15



Here is the output of the log:

george@batlin:~$ grep B0C0FD66 /var/log/messages
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NX> 596 ERROR: NXNODE Ver. 3.2.0-11  (Error id eE1F7B5)
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NX> 596 ERROR: create session: run commands
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NX> 596 ERROR: execution of last command failed
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/george/.nx/C-batlin-1040-AC5298E197CADA414056104F96B85410/scripts/authority'
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NX> 596 exit value: 1
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NX> 596 stdout: 
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NX> 596 stderr: xauth:  /home/george/.Xauthority not writable, changes will be ignored
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NX> 596 init: stdin arguments: user=george,userip=192%2e168%2e1%2e125,uniqueid=AC5298E197CADA414056104F96B85410,display=1040,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e1%2e138,encryption_mode=3,connection=local,images=256M,cache=64M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=Batlin,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1680x1020x32%2brender,keyboard=pc102%2fen_US,geometry=1680x1020,link=lan
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NXNodeExec::exec('startsession', 'user=george&userip=192%2e168%2e1%2e125&uniqueid=AC5298E197CADA41...', 'localhost', 22) called at handlers/nxserver.pl line 3398
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NXShell::handler_session_start('--link="lan" --backingstore="1" --encryption="1" --cache="64M" -...') called at NXShell.pm line 373
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NXShell::handle_command('startsession', '--link="lan" --backingstore="1" --encryption="1" --cache="64M" -...') called at NXShell.pm line 145
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) NXShell::run() called at nxserver.pl line 4461
Jul  2 18:28:52 batlin NXSERVER-3.2.0-13[31801]: ERROR: (exception id B0C0FD66) eval {...} called at nxserver.pl line 4420


It does not appear to be an authentication problem, but maybe a graphics driver problem?  Any Ideas?

---

### Post by nukie77 on 2008-07-04
well, it looks like the problems was indeed the fact that the /home/george/.Xauthority directory had somehow been taken over by root.  When I "sudo chown george:george /home/george/.Xauthority" the directory, that at least allowed the session to start.  I did generate a few gnome errors one the session started, but that is a problem for another day.

---

