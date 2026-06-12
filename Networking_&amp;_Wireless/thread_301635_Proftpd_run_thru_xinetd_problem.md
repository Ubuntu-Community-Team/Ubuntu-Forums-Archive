---
title: "Proftpd run thru xinetd problem"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2006-11-17
Ok, well the subject line says it all. I can get my ftp server working when it's standalone but I want to use xinetd so that proftpd daemon doesn't tie up any system resources and the xinetd daemon will be running and listening on port 21, then when some1 tries to connec the connection is then passed on to proftpd. at least that's my understanding. ok here are the applicable config files and output of common commands that 1 might ask me for. oh, i compiled version 1.3 myself, i run dapper and wanted the latest version but version 1.3 in the backport repo doesn't have mod_tls compiled in so I had to do it myself.
**/etc/proftpd.conf**
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on
# Choose here the user alias you want !!!!
UserAlias ftpuser ftp
ServerName "UBUNTU FTP Server"
ServerType                      inetd
DeferWelcome                    on
MultilineRFC2228 on
DefaultServer                   on
ShowSymlinks                    off
TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 600
DisplayFirstChdir               .message
ListOptions                     "-l"
RequireValidShell               off
TimeoutLogin 20
RootLogin                       off
# It's better for debug to create log files ;-)
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog               /var/log/syslog.log
#DenyFilter                     \*.*/
# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off
# Allow to restart a download
AllowStoreRestart on
Port                            21
# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8
# Set the user and group that the server normally runs at.
User nobody
Group nogroup
# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022
PersistentPasswd                off
MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8
# Display a message after a successful login
AccessGrantMsg "YOU MADE IT!"
# This message is displayed for each access good or not
ServerIdent on "you're at home"
# Set /home/ftp directory as home directory
DefaultRoot /home/ftp
# Lock all the users in home directory, ***** really important *****
#DefaultRoot ~
MaxLoginAttempts 5
UseReverseDNS                   off
IdentLookups                    off
AllowForeignAddress on
#VALID LOGINS
<Limit LOGIN>
AllowUser ftp
DenyALL
</Limit>
<Directory /home/ftp>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>
<Directory /home/ftp/download/*>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>
<Directory> /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
        <Limit READ DELE>
        DenyAll
        </Limit>
        <Limit STOR RMD RNFR RNTO CWD MKD>
        AllowAll
        </Limit>
</Directory>

**/etc/xinetd.conf**
# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/

defaults
{
}
includedir /etc/xinetd.d

**/etc/xinetd.d/ftp**
service ftp
{
disable = no
flags = REUSE
socket_type = stream
instances = 5
port = 21
wait = no
user = root
server = /usr/sbin/proftpd
#bind = 192.168.0.1
log_type = FILE /var/log/xinetd.log
log_on_success = HOST EXIT DURATION
log_on_failure = HOST ATTEMPT
#Allow access from the local network (ie, 192.168.0.0/24)
#only_from   = 192.168.0.0/24
#And from two remote locations
#only_from   = 10.1.1.2 sampleconfig.com
#allow from anywhere
only_from   = 0.0.0.0
}

when I do **ftp localhost** in a terminal, I get this: Connected to localhost.
421 Service not available, remote server has closed connection

**netstat -pat**
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:43816         *:*                     LISTEN     -
tcp        0      0 *:mysql                 *:*                     LISTEN     -
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     -
tcp        0      0 localhost:57419         *:*                     LISTEN     -
**tcp        0      0 *:ftp                   *:*                     LISTEN     -**
tcp        0      0 localhost:ipp           *:*                     LISTEN     -
tcp        0      0 UBUNTU:42367            205.188.8.252:5190      ESTABLISHED6145/gaim
tcp        0      0 localhost:57419         localhost:40441         ESTABLISHED-
tcp        0      0 localhost:40441         localhost:57419         ESTABLISHED-
tcp6       0      0 *:www                   *:*                     LISTEN     -
tcp6       0      0 *:ssh                   *:*                     LISTEN     -
tcp6       0    356 UBUNTU:ssh              blah blah blah ESTABLISHED-

**netstat -pant**

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:43816         0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     -
tcp        0      0 127.0.0.1:57419         0.0.0.0:*               LISTEN     -
**tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     -**tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -
tcp        0      0 192.168.0.3:42367       205.188.8.252:5190      ESTABLISHED6145/gaim
tcp        0      0 127.0.0.1:57419         127.0.0.1:40441         ESTABLISHED-
tcp        0      0 127.0.0.1:40441         127.0.0.1:57419         ESTABLISHED-
tcp6       0      0 :::80                   :::*                    LISTEN     -
tcp6       0      0 :::22                   :::*                    LISTEN     -
tcp6       0  1812 ::ffff:192.168.0.3:22 ::ffff:63.161.86.254:25854 ESTABLISHED-

I view syslog and it states that xinetd started 1 service, so I don't think's xinetd. It may be user auth but how do I check this? I have followed frodon's guide ([http://www.ubuntuforums.org/showthread.php?t=79588&highlight=proftpd](http://www.ubuntuforums.org/showthread.php?t=79588&highlight=proftpd)) to the tee just that I want to run it through xinetd and he does it standalone. So why can I not connect????

edited: i ran proftpd -d 10 which runs it in the highest debugging setting it can can this is what it states for errors: Fatal: SystemLog: unable to redirect logging to '/var/log/syslog.log': Permission denied on line 23 of '/etc/proftpd.conf'
Does this matter? At one point I thought that it couldn't write to syslog because I had syslog open within Ubuntu's log viewer, well I am ssh'd into the machine and when I did a ps aux | grep log, I found the gnome-log-viewer and I killed it. so i reran the debug and it still says it can't redirect logging to '/var/log/syslog.log'????

---

### Post by dannyboy79 on 2006-11-17
MY GOSH, I troubleshoot this for about 10 hrs, read every log file I could, read every forum thread at proftpd forums, and I think every thread I found in gogle relating to proftpd and xinetd not working. It turned out that since I compiled it myself, a dir wasn't created due to, well I am not sure why it wasn't created after I ran checkinstall??? **1.** so I did mkdir /var/proftpd and this allowed for proftpd.scoreboard to be created, it also solved this error: mod_delay/0.5: error opening DelayTable '/var/proftpd/proftpd.delay':, cause now since the dir was there it was able to create the proftpd.delay file. Low and behold, I can login!!! yeah!!!!! also, to mention some other things that I messed with that might have had an effect. **2.** there was no /etc/pam.d/ftp file installed either after compiling it myself, they luckily provided 1 with the source files within proftpd-1.3.0/contrib/dist/rpm/, it was called ftp.pamd originally but Ubuntu Dapper required it to just be ftp, so i copied that file from there and renamed it to ftp and put it in /etc/pam.d/. **3. possibly optional** within that file, I also uncommented this: 
auth       required     /lib/security/pam_shells.so
so that anonymous logins will fail because the 'ftp' user does
not have a "valid" shell, as listed in /etc/shells. (i don't want anyone to be able to login anon!) I am trying to think what else I played with besides. **4.** ah ah, i changed my /etc/xinetd.d/ftp file, it now looks like this:
service ftp
{
disable = no
socket_type = stream
wait = no
user = root
server = /usr/sbin/proftpd
log_on_success += DURATION USERID
log_on_failure += USERID
nice = 10
}
as a side note, since I am using xinetd and not inetd I thought I would document my current /etc/inetd.conf file to show you that this has nothing to do with getting proftpd working thru xinetd:
netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd
#<off># ftp     stream  tcp     nowait  root    /usr/sbin/tcpd /usr/sbin/proftpd

other than all this, i followed frondons guide ([http://www.ubuntuforums.org/showthre...hlight=proftpd](http://www.ubuntuforums.org/showthre...hlight=proftpd)) and instead of doing sudo aptitude install proftpd, I just downloaded proftpd version 1.3 from the official website and compiled it myself. i did use a --prefix=/usr as well as these 2 things when configuring:  --sysconfdir=/etc --localstatedir=/var along with all the modules I listed above. Boy was this a learning experience!!! if I note anything else I'll keep people informed.

---

### Post by dannyboy79 on 2006-11-21
new finding! I have a netgear router that I have port forwarded port 21 to my local server. i know that when I connect to it from outside the lan, my client, Filezilla is using passive ftp, which, what happens is that port 21 is used for the control connection which is what sends the username and the password. then it opens up a random port to use for the data connection. what I don't uhderstand is that If I have a router and have not forwarded ports for the passive connection or have openened ports in my iptables firewall, how in the hell is this working???? I am assuming that my netgear router is a nat router??
Here is a log of a successful login from outside the lan with no other ports forwarded except 21, 22 and the ones I use for bittorrent which are really high.

Status:	Connecting to blah blah...
Status:	Connected with blah blah. Waiting for welcome message...
Response:	220 you're at home
Command:	USER xxxxxx
Response:	331 Password required for xxxxxx.
Command:	PASS ***************
Response:	230 YOU MADE IT!
Command:	FEAT
Response:	211-Features:
Response:	 MDTM
Response:	 REST STREAM
Response:	 SIZE
Response:	211 End
Command:	SYST
Response:	215 UNIX Type: L8
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is current directory.
Command:	TYPE A
Response:	200 Type set to A
Command:	PASV
Response:	227 Entring Passive Mode (xx,xx,xxx,xxx,233,238
Command:	PORT 10,90,118,166,19,76
Response:	200 PORT command successful
Command:	LIST
Response:	150 Opening ASCII mode data connection for file list
Response:	226 Transfer complete.
Status:	Directory listing successful

then the other issue, is that I can't get mod_tls to work even locally?? I use frodons guide for creating the cert's and i get errors in syslog.log that state that Nov 20 15:17:53 UBUNTU proftpd[22968] localhost: mod_tls/2.1.1: unable to use RSA certificate key in '/etc/ftpcert/server.key', exiting
Nov 20 15:17:53 UBUNTU proftpd[22968] localhost: FTP session closed??? Can anyone help me with this???? Shouldn't I at least be able to log into the ftp localhost? I know that I have tried using Fireftp as well as Filezilla both trying to do it securely only on the ctrl channel as well as both and the above error is what I was getting.

---

### Post by dannyboy79 on 2007-01-05
hello, I can't believe no one else runs their ftp server thru xinetd and uses ssl?

---

### Post by dannyboy79 on 2007-01-16
bump, please

---

