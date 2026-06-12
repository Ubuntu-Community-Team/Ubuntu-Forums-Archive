---
title: "Proftpd help"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by dinonet on 2007-12-03
Hi,

I'm having trouble configuring proftpd to work. Can some please take a look and see if you can find anything I could have done wrong? I followed these instructions from this old thread [http://ubuntuforums.org/showthread.php?t=51611](http://ubuntuforums.org/showthread.php?t=51611)

I followed it exactly and added the user in the conf file. When I try to connect with fireftp I keep getting "Unable to make a connection. Please try again."

Any help would be greatly appreciated. Here's my conf file. Thanks!

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias pooftp userftp

ServerName			"poo"
ServerType 			inetd
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nouser
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>
    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

---

### Post by Jose Catre-Vandis on 2007-12-03
Only thing I can see is you have opted for inetd instead of standalone under Servertype.

Also where is your proftpd.conf file. It should be in>  /etc/proftpd/ and not>  /etc as indicated in the howto you linked. If you created it in the latter then the daemon might not be picking it up?

I run proftpd with standalone no problems.

---

### Post by dinonet on 2007-12-03
Hi Jose,

Thanks for your response. I used inetd only because I read it's preferred if I am only planning on using ftp very little. Is that not true? The proftpd.conf file is in /etc/proftpd. Think I should reinstall but the standalone?

---

### Post by Jose Catre-Vandis on 2007-12-03
Well, as standalone is recommended to start off with ([http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6)), it's worth a try to get the thing up and running. I wouldn't worry about aliases either. Get the default to work (uses server box login), then tweak to how you want it, you'll always know how to get back to a working config that way.

I installed proftpd from the repos, so got the GUI question about standalone on install, that was all it took to be up and running (of course port forwarding on the router was important too)

---

### Post by dinonet on 2007-12-03
> **Jose Catre-Vandis said:**
> Well, as standalone is recommended to start off with ([http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6)), it's worth a try to get the thing up and running. I wouldn't worry about aliases either. Get the default to work (uses server box login), then tweak to how you want it, you'll always know how to get back to a working config that way.

I installed proftpd from the repos, so got the GUI question about standalone on install, that was all it took to be up and running (of course port forwarding on the router was important too)

Thanks! I'll try it

---

### Post by dinonet on 2007-12-04
Hi Jose, do you have any idea what I might be doing wrong? I tried to use a different port and it only works when I set it to port 21. When I try a different port I add it to the conf file and then in the router settings to forward that port but no go.

---

### Post by dinonet on 2007-12-04
Also one more question sorry! How can I add a new user so they can log in with their own user/pwd to the same directories?

---

### Post by Jose Catre-Vandis on 2007-12-05
You are restarting proftpd each time you make a change, yes?```
sudo /etc/init.d/proftpd restart
```

OK I think I have figured out your problems by testing on my own system (LAN)

There is a password step missing in the howto you followed. On your ftp server machine type the following:```
sudo password userftp
``` and follow the prompts to add your password.

You should now be able to login as your alias. Not sure how to add further users

Didn't have any real problems in changing the port number. Make sure you have the port forwarding setup properly on your router, and the settings are applied and the new service added (if that's how it works - I have a default FTP service in place, and had to create a new one for a different port, and then enable and apply it)

Have a look here for detailed instructions about multiple users
[http://www.ubuntuforums.org/showthread.php?p=429783#post429783](http://www.ubuntuforums.org/showthread.php?p=429783#post429783)

---

