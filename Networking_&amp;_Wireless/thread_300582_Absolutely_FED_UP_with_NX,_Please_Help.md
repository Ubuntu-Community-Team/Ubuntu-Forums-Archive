---
title: "Absolutely FED UP with NX, Please Help"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by craz on 2006-11-15
Well recently I have just gotten ssh to work.  It works fine on my own machine (localhost), but on my networked windows machine with Putty, the ssh connection keeps timing out and I do not know why.  Since I cannot use NX from that machine because of that, I have been testing it on this machine.  I first started with freenx and it wasnt working.  So I switched to regular NX.  My problem is this: 
```
NX> 203 NXSSH running with pid: 20864
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.46 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
```
I have (I believe) everything set up correctly including keys, usernames and such.  I have researched the problem heavily for at least 6 hours, and, though it seems a common problem, have not had any luck.  Can anyone help me get my NX working and then my ssh connection from the other machine?  I hope its not too much to ask..any help is appreciated like you wouldn't believe.  Thanks.

---

### Post by craz on 2006-11-16
~*bump*~

---

### Post by craz on 2006-11-16
Has anybody been able to fix this problem?

---

### Post by jlintz on 2006-11-21
Same problem here.  Anyone?

---

### Post by trubblemaker on 2006-11-21
check dmesg on the linux side for tips of ware it went wrong,  don't use NX but does it have an error log? posting that would help others help you more.  As for checking from the windows side, there are system logs that you can check in Start>Programs>System tools? I can't remember, but this might help you track it down.  

Just to clarify your issue is that you can use NX on linux. (on the same computer that hosts NX) but you can't ssh/NX into it for any reasonable amount of time before it dies.  Is that sound like your issue?

---

### Post by craz on 2006-11-21
No, I dont think it is.  It will not work at all.  Ok I ran dmesg and i do not think there was anything wrong, however I dont really know what to look for.  I do have the NX error logs, however, they are here.  This is the run log.
> [Thu Nov 16 14:44:11 2006]: Setting environment variable 'NX_SYSTEM' to '/usr/NX'
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'NX_ROOT' to '/home/chrisberube/.nx'
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'NX_HOME' to '/home/chrisberube'
[Thu Nov 16 14:44:11 2006]: Starting font debug
Fixed font was set to: 'Courier' size: '8'
And the result is: 'Courier'
Setting font from nxclient.conf: 'Bitstream Vera Sans,9,-1,5,50,0,0,0,0,0'
Font was set to: 'Bitstream Vera Sans'
And the result is: 'Bitstream Vera Sans'
End of font debug


[Thu Nov 16 14:44:11 2006]: Starting NX Client version 2.1.0-9
[Thu Nov 16 14:44:11 2006]: qtrc: useXft read=1 value=1
qtrc: useXft is set to true
qtrc: enableXft read=1 value=1
qtrc: enableXft is set to true

[Thu Nov 16 14:44:11 2006]: Initializing the login dialog.
[Thu Nov 16 14:44:11 2006]: Config File Name set to: '/home/chrisberube/.nx/config/nxclient.cfg'.
[Thu Nov 16 14:44:11 2006]: System NX dir set to: '/usr/NX'.
[Thu Nov 16 14:44:11 2006]: Personal NX dir set to: '/home/chrisberube/.nx'.
[Thu Nov 16 14:44:11 2006]: creating SessionSettings=''
[Thu Nov 16 14:44:11 2006]: LoginDialog::loadConfigFiles - number of entires in config dir: 5
[Thu Nov 16 14:44:11 2006]: ComboSession::insertSession: 'Home' -> '/home/chrisberube/.nx/config/Home.nxs'
[Thu Nov 16 14:44:11 2006]: ComboSession::setCurrentSession: 'Home'
[Thu Nov 16 14:44:11 2006]: SessionSettings::loadFromFile('/home/chrisberube/.nx/config/Home.nxs')
[Thu Nov 16 14:44:11 2006]: Utility::getPreferencesFile: 'nxclient' -> '/home/chrisberube/.nx/config/nxclient.cfg'
[Thu Nov 16 14:44:11 2006]: ComboSession::setCurrentSession: 'Home'
[Thu Nov 16 14:44:11 2006]: SessionSettings::loadFromFile('/home/chrisberube/.nx/config/Home.nxs')
[Thu Nov 16 14:44:11 2006]: LoginDialog: slotChangeSession [Home]
[Thu Nov 16 14:44:11 2006]: LoginDialog: loadUserAndPassword
[Thu Nov 16 14:44:11 2006]: LoginDialog: loadUserAndPassword
[Thu Nov 16 14:44:11 2006]: Settings::flush
[Thu Nov 16 14:44:11 2006]: Settings::flush
[Thu Nov 16 14:44:11 2006]: LoginDialog: loadUserAndPassword
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'NX_HOME' to '/home/chrisberube'
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'NX_ROOT' to '/home/chrisberube/.nx'
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'NX_SYSTEM' to '/usr/NX'
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'NX_CLIENT' to '/usr/NX/bin/nxclient'
[Thu Nov 16 14:44:11 2006]: Trying the XAUTHORITY environment variable with value [/home/chrisberube/.Xauthority].
[Thu Nov 16 14:44:11 2006]: Utility::getXAuthorityFilePath: /home/chrisberube/.Xauthority
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'XAUTHORITY' to '/home/chrisberube/.Xauthority'
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'LD_LIBRARY_PATH' to '/usr/NX/lib'
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'HOME' to '/home/chrisberube'
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'PATH' to '/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/NX/bin:/usr/X/bin'
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'NX_TEMP' to '/tmp'
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'TEMP' to '/tmp'
[Thu Nov 16 14:44:11 2006]: Setting environment variable 'NX_VERSION' to '2.1.0'
[Thu Nov 16 14:44:11 2006]: NXService::run command=--cleanup
[Thu Nov 16 14:44:11 2006]: path=/home/chrisberube/.nx/temp/5166/servicelog
[Thu Nov 16 14:44:15 2006]: LoginDialog: login setupGui 1
[Thu Nov 16 14:44:15 2006]: Setting environment variable 'NX_HOME' to '/home/chrisberube'
[Thu Nov 16 14:44:15 2006]: Setting environment variable 'NX_ROOT' to '/home/chrisberube/.nx'
[Thu Nov 16 14:44:15 2006]: Setting environment variable 'NX_SYSTEM' to '/usr/NX'
[Thu Nov 16 14:44:15 2006]: Setting environment variable 'NX_CLIENT' to '/usr/NX/bin/nxclient'
[Thu Nov 16 14:44:15 2006]: Trying the XAUTHORITY environment variable with value [/home/chrisberube/.Xauthority].
[Thu Nov 16 14:44:15 2006]: Utility::getXAuthorityFilePath: /home/chrisberube/.Xauthority
[Thu Nov 16 14:44:15 2006]: Setting environment variable 'XAUTHORITY' to '/home/chrisberube/.Xauthority'
[Thu Nov 16 14:44:15 2006]: Setting environment variable 'LD_LIBRARY_PATH' to '/usr/NX/lib:/usr/NX/lib'
[Thu Nov 16 14:44:15 2006]: Setting environment variable 'HOME' to '/home/chrisberube'
[Thu Nov 16 14:44:15 2006]: Setting environment variable 'PATH' to '/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/NX/bin:/usr/X/bin:/usr/NX/bin:/usr/X/bin'
[Thu Nov 16 14:44:15 2006]: Setting environment variable 'NX_TEMP' to '/tmp'
[Thu Nov 16 14:44:15 2006]: Setting environment variable 'TEMP' to '/tmp'
[Thu Nov 16 14:44:15 2006]: Setting environment variable 'NX_VERSION' to '2.1.0'
[Thu Nov 16 14:44:15 2006]: Trying to write the ssh key into [/home/chrisberube/.nx/temp/5166/keylog]
[Thu Nov 16 14:44:15 2006]: SSH key file path [/home/chrisberube/.nx/temp/5166/keylog]
[Thu Nov 16 14:44:15 2006]: LoginDialog: startProgressTimer
[Thu Nov 16 14:44:15 2006]: LoginDialog::ShowConnectionStatus code=[240] str=[Setting up the environment] error=[0]
[Thu Nov 16 14:44:15 2006]: ProgressDialog::printNxStatus: [Setting up the environment]
[Thu Nov 16 14:44:15 2006]: LoginDialog: startProgressTimer
[Thu Nov 16 14:44:15 2006]: Showing progress dialog: Setting up the environment
[Thu Nov 16 14:44:15 2006]: Going to get the X authorization cookie on display.
[Thu Nov 16 14:44:15 2006]: Trying the XAUTHORITY environment variable with value [/home/chrisberube/.Xauthority].
[Thu Nov 16 14:44:15 2006]: Running command [xauth -f /home/chrisberube/.Xauthority nextract - :0.0 | cut -f 9 -d ' ' 1>/home/chrisberube/.nx/temp/5166/authlog 2>/dev/null].
[Thu Nov 16 14:44:15 2006]: Command run.
[Thu Nov 16 14:44:15 2006]: Got or created the X authorization cookie.
[Thu Nov 16 14:44:15 2006]: LoginDialog::ShowConnectionStatus code=[241] str=[Connecting to 192.168.1.46] error=[0]
[Thu Nov 16 14:44:15 2006]: ProgressDialog::printNxStatus: [Connecting to 192.168.1.46]
[Thu Nov 16 14:44:15 2006]: LoginDialog::connectHost() nxsshline=/usr/NX/bin/nxssh -nx -p 22 -i /home/chrisberube/.nx/temp/5166/keylog nx@192.168.1.46 -x -2 -o RhostsAuthentication no -o PasswordAuthentication no -o RSAAuthentication no -o RhostsRSAAuthentication no -o PubkeyAuthentication yes -B -E
[Thu Nov 16 14:44:15 2006]: Using NX_STDIN flag redirection for [nxssh] process
[Thu Nov 16 14:44:15 2006]: Using NX_STDOUT flag redirection for [nxssh] process
[Thu Nov 16 14:44:15 2006]: Using NX_STDERR flag redirection for [nxssh] process
[Thu Nov 16 14:44:15 2006]: SpawnProcess method has returned [1]
[Thu Nov 16 14:44:15 2006]: Process [nxssh] running with pid [5183]
[Thu Nov 16 14:44:16 2006]: Received line from nxssh process [NX> 203 NXSSH running with pid: 5183

] with code [203]
[Thu Nov 16 14:44:16 2006]: Received code[203]
[Thu Nov 16 14:44:16 2006]: NXProtocol: trying to read ssh pid from ' 5183

' - read '5183'
[Thu Nov 16 14:44:16 2006]: Received line from nxssh process [NX> 285 Enabling check on switch command

] with code [285]
[Thu Nov 16 14:44:16 2006]: Received code[285]
[Thu Nov 16 14:44:16 2006]: Received line from nxssh process [NX> 285 Enabling skip of SSH config files

] with code [285]
[Thu Nov 16 14:44:16 2006]: Received code[285]
[Thu Nov 16 14:44:16 2006]: Received line from nxssh process [NX> 285 Setting the preferred NX options

] with code [285]
[Thu Nov 16 14:44:16 2006]: Received code[285]
[Thu Nov 16 14:44:16 2006]: Received line from nxssh process [NX> 200 Connected to address: 192.168.1.46 on port: 22

] with code [200]
[Thu Nov 16 14:44:16 2006]: Received code[200]
[Thu Nov 16 14:44:16 2006]: Received line from nxssh process [NX> 202 Authenticating user: nx

] with code [202]
[Thu Nov 16 14:44:16 2006]: Received code[202]
[Thu Nov 16 14:44:16 2006]: LoginDialog::ShowConnectionStatus code=[242] str=[Connected to 192.168.1.46] error=[0]
[Thu Nov 16 14:44:16 2006]: ProgressDialog::printNxStatus: [Connected to 192.168.1.46]
[Thu Nov 16 14:44:16 2006]: Received line from nxssh process [NX> 208 Using auth method: publickey
] with code [208]
[Thu Nov 16 14:44:16 2006]: Received code[208]
[Thu Nov 16 14:44:17 2006]: Received line from nxssh process [NX> 204 Authentication failed.
] with code [201]
[Thu Nov 16 14:44:17 2006]: Received code[201]
[Thu Nov 16 14:44:17 2006]: KillAllComponents 0x86ad088
[Thu Nov 16 14:44:17 2006]: LoginDialog: stopAllTimers
[Thu Nov 16 14:44:17 2006]: LoginDialog: stopProgressTimer
[Thu Nov 16 14:44:17 2006]: LoginDialog::killAllComponents() stopping NXProtoSSH
[Thu Nov 16 14:44:17 2006]: NXProcessUnix::StopProcess process [nxssh] with pid [5183]
[Thu Nov 16 14:44:17 2006]: end of killAllComponents
[Thu Nov 16 14:44:17 2006]: Error is [Server not installed or NX access disabled]
[Thu Nov 16 14:44:17 2006]: messageError: [Server not installed or NX access disabled]
[Thu Nov 16 14:44:17 2006]: printFatalError [Server not installed or NX access disabled]
[Thu Nov 16 14:44:17 2006]: KillAllComponents 0x86ad088
[Thu Nov 16 14:44:17 2006]: LoginDialog: stopAllTimers
[Thu Nov 16 14:44:17 2006]: LoginDialog: stopProgressTimer
[Thu Nov 16 14:44:17 2006]: LoginDialog::killAllComponents() stopping NXProtoSSH
[Thu Nov 16 14:44:17 2006]: NXProcessUnix::StopProcess process [nxssh] with pid [5183]
[Thu Nov 16 14:44:17 2006]: end of killAllComponents
[Thu Nov 16 14:44:17 2006]: LoginDialog::ShowConnectionStatus code=[268] str=[Server not installed or NX access disabled] error=[1]
[Thu Nov 16 14:44:17 2006]: ProgressDialog::printNxStatus: [Server not installed or NX access disabled]
[Thu Nov 16 14:44:17 2006]: LoginDialog: isReconnecting() [0]
[Thu Nov 16 14:44:17 2006]: Logfile path [/home/chrisberube/.nx/temp/5166/sshlog] exists.
[Thu Nov 16 14:44:20 2006]: LoginDialog::ShowConnectionStatus code=[251] str=[Disconnecting...] error=[0]
[Thu Nov 16 14:44:20 2006]: ProgressDialog::printNxStatus: [Disconnecting...]
[Thu Nov 16 14:44:20 2006]: KillAllComponents 0x86ad088
[Thu Nov 16 14:44:20 2006]: LoginDialog: stopAllTimers
[Thu Nov 16 14:44:20 2006]: LoginDialog: stopProgressTimer
[Thu Nov 16 14:44:20 2006]: LoginDialog::killAllComponents() stopping NXProtoSSH
[Thu Nov 16 14:44:20 2006]: NXProcessUnix::StopProcess process [nxssh] with pid [5183]
[Thu Nov 16 14:44:20 2006]: end of killAllComponents
[Thu Nov 16 14:44:21 2006]: LoginDialog: closeEvent received!
[Thu Nov 16 14:44:21 2006]: LoginDialog::destructor called begin
[Thu Nov 16 14:44:21 2006]: LoginDialog: stopAllTimers
[Thu Nov 16 14:44:21 2006]: LoginDialog: stopProgressTimer
[Thu Nov 16 14:44:21 2006]: Utility::getPreferencesFile: 'nxclient' -> '/home/chrisberube/.nx/config/nxclient.cfg'
[Thu Nov 16 14:44:21 2006]: Settings::flush
[Thu Nov 16 14:44:21 2006]: LoginDialog::destructor called end

This is the ssh log.
> NX> 203 NXSSH running with pid: 5183

NX> 285 Enabling check on switch command

NX> 285 Enabling skip of SSH config files

NX> 285 Setting the preferred NX options

NX> 200 Connected to address: 192.168.1.46 on port: 22

NX> 202 Authenticating user: nx

NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

Thanks for any help.

---

### Post by craz on 2006-11-22
Well its still no go.  I really dont know what to do.

---

### Post by trubblemaker on 2006-11-22
Yeah I don't even have NX but found some linx for you 

check setup with 
[http://ubuntuguide.org/wiki/Dapper#Remote_Desktop_Access_via_NX](http://ubuntuguide.org/wiki/Dapper#Remote_Desktop_Access_via_NX)

Post to this forum to get help
[http://www.ubuntuforums.org/archive/index.php/t-97277.html](http://www.ubuntuforums.org/archive/index.php/t-97277.html)

Try posting againg with a better description of the issue.  I know it's not suggest that you post mutliple times, but you description really doesn't say anything about your issue.  All anyone knows is you don't like NX, but if you posted with "NX and dropped sessions from windows" you'd get a better response. 

"Absolutely FED UP with @@@@@@@, Please Help" is pretty generic.  

Your posting on a help form no need to say 'PLease help', 
People rarely post if there not irritated  with something so 'Absolutely FED UP with' is also redundant and lends no information to the issue.

leaving "NX" or something about NX as all the information about your issue.


The more specific the easier for everyone to help.  Only people with a love of punishment or experts will view your post if it's generic.

I hope you understand I'm not trying to rip you down, I'm trying to help you get more responses for your problem.

---

