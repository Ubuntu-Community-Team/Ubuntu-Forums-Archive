---
title: "smb.conf is blank"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by txwooley on 2008-12-05
Well, now I've gone and done it!  I pushed that little red button next to the sign that says, "[B]DO NOT PUSH[B]"!  My Ubuntu laptop won't recognize my Vista desktop and visa-versa.  I have been playing around with all sorts of settings that I know nothing about and got the results one usually does in such a situation - major snafu's.  Someone suggested the problem (with networking) could lie in the smb.conf file.  I opened said file and now believe that is very much the problem.  The page is completely BLANK!  I've toyed around enough to know how to edit it using gksudo gedit, but I have no idea what information to put in there.  I've looked it up on google, but the explanations seem very complex.  Can anyone dummy this down a little for me?  Please?

---

### Post by handydan918 on 2008-12-05
Here is a copy of a smb.conf from Debian. Well commented. 

```
;
; /etc/smb.conf
;
; Sample configuration file for the Samba suite for Debian GNU/Linux
;
; Please see the manual page for smb.conf for detailed description of
;	every parameter.
;

[global]
   printing = bsd
   printcap name = /etc/printcap
   load printers = yes
   guest account = nobody
   invalid users = root


; "security = user" is always a good idea. This will require a Unix account
;	in this server for every user accessing the server.
   security = user
;   security = share

; Change this for the workgroup your Samba server will part of
   workgroup = HOME

; private settings
   server string = Samba %v at %h
   hosts allow = 192.168.1. 127.  
   interfaces = 192.168.1.1

; If you want Samba to log though syslog only then set the following
;	parameter to 'yes'. Please note that logging through syslog in
;	Samba is still experimental.
   syslog only = no

; We want Samba to log a minimum amount of information to syslog. Everything
;	should go to /var/log/{smb,nmb} instead. If you want to log through
;	syslog you should set the following parameter to something higher.
   syslog = 0;

; This socket options really speed up Samba under Linux, according to my
;	own tests.
   socket options = IPTOS_LOWDELAY TCP_NODELAY SO_SNDBUF=4096 SO_RCVBUF=4096

; Passwords are encrypted by default. This way the latest Windows 95 and NT
;	clients can connect to the Samba server with no problems.
   encrypt passwords = yes

; It's always a good idea to use a WINS server. If you want this server
;	to be the WINS server for your network change the following parameter
;	to "yes". Otherwise leave it as "no" and specify your WINS server
; 	below (note: only one Samba server can be the WINS server).
;	Read BROWSING.txt for more details.
   wins support = yes

; If this server is not the WINS server then specify who is it and uncomment
;	next line.
;   wins server = 172.16.0.10

; Please read BROWSING.txt and set the next four parameters according
;	to your network setup. There is no valid default so they are commented
;	out.
   os level = 34
   domain master = yes
   local master = yes
   preferred master = yes

; What naming service and in what order should we use to resolve host names
;	to IP addresses
   name resolve order = lmhosts host wins bcast

; This will prevent nmbd to search for NetBIOS names through DNS.
;   dns proxy = no
   dns proxy = yes

; Name mangling options

   preserve case = yes
   short preserve case = yes

; This boolean parameter controlls whether Samba attempts to sync. the Unix
;	password with the SMB password when the encrypted SMB password in the
;	/etc/samba/smbpasswd file is changed.
   unix password sync = yes

; For Unix password sync. to work on a Debian GNU/Linux system, the following
;	parameters must be set (thanks to Augustin Luton
;	<aluton@hybrigenics.fr> for sending the correct chat script for
;	the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

; The following parameter is useful only if you have the linpopup package
;	installed. The samba maintainer and the linpopup maintainer are
;	working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

; The default maximum log file size is 5 MBytes. That's too big so this
;	next parameter sets it to 1 MByte. Currently, Samba rotates log
;	files (/var/log/{smb,nmb} in Debian) when these files reach 1000 KBytes.
;	A better solution would be to have Samba rotate the log file upon
;	reception of a signal, but for now on, we have to live with this.
   max log size = 1000


[homes]
   comment = Home Directories
   browseable = no

; By default, the home directories are exported read only. Change next
;	parameter to "no" if you want to be able to write to them.
   read only = no

; File creation mask is set to 0700 for security reasons. If you want to
;	create files with group=rw permissions, set next parameter to 0775.
   create mask = 0755

; Directory creation mask is set to 0700 for security reasons. If you want to
;	create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0755

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700

; pub
[pub]
; sticky: no delete file by others 
; SGID: can share within group for read
   comment = share directory 3775 root:src
   browseable = yes
   create mode = 0640
   directory mask = 0750
   writable = yes
   locking = yes
   path = /home/ftp/share
   public = yes

; A sample share for sharing your CD-ROM with others.
[cdrom]
   comment = Samba server's CD-ROM
   writable = no
   locking = no
   path = /cdrom
   public = yes
;
; The next two parameters show how to auto-mount a CD-ROM when the
;	cdrom share is accessed. For this to work /etc/fstab must contain
;	an entry like this:
;
;       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
;
; The CD-ROM gets unmounted automatically after the connection to the
;
; If you don't want to use auto-mounting/unmounting make sure the CD
;	is mounted on /cdrom
;
   preexec = /bin/mount /cdrom
   postexec = /bin/umount /cdrom


```

---

### Post by txwooley on 2008-12-05
Thanks for the help.  I'm not sure if it worked or not though.  As I said- my original problem was not networking with Vista desktop.  That hasn't changed, but at least my smb.conf isn't blank anymore.  However while I was checking to make sure all my info was properly saved, I opened the dhcp.conf and found it blank as well.  At least I'm good at what I do!  Know anyone needs their OS screwed up?  Anyway, I don't know anything about dhcp, but it sounds important.  Could that be my prob?  Do you know what goes in dhcp.conf?  I think it's time to buy a book instead of "tinkering" to see what makes it tick!

Again, thanks for the help so far.

---

### Post by handydan918 on 2008-12-05
This is a test. Please give the full path to both of the .conf files you have mentioned.

---

### Post by txwooley on 2008-12-05
Good news on the networking front!  I found my Vista shares by manually entering it's IP address with smb://

Both of those files are in /etc/samba/smb.conf and /etc/samba/dhcp.conf

Also in the /etc/samba/ is gdbcommands, smb.conf7364gksudo, smb.template, smbpasswd, and smbusers.

I'm pretty sure dhcp.conf isn't supposed to be a blank page, and I have no idea how I deleted it.

Thanks

---

### Post by pdtpatrick on 2008-12-05
Are you using dhcp or static? is your dhcp server running?

---

### Post by pdtpatrick on 2008-12-05
can you do cat /etc/network/interfaces and post what you have there pls

---

### Post by Zorael on 2008-12-05
Per default Ubuntu doesn't heed requests towards "computer names" like Windows does (\\COMPUTER and smb://COMPUTER). So you'll want to enable WINS (Windows Internet Name Service) host resolution. You need to install **winbind** with your package manager of choice, and modify **/etc/nsswitch.conf** slightly.
```
$ sudo aptitude install winbind
```
Pop up that nsswitch.conf in a text editor with superuser permissions and find the 'hosts:' line. Mine looked like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
Now just add **wins** after files (order matters) and save the file.
```
hosts:          files **[COLOR="DeepSkyBlue"]wins[/COLOR]** mdns4_minimal [NOTFOUND=return] dns mdns4
```
Then restart samba for good measure. I think that ought to do it.
```
$ sudo service samba restart
```

On a sidenote, use **smbtree** to discover other computers in your network. Just hit enter when it asks for a password unless you need to authenticate towards the other computers to access their shares.
```
$ smbtree
Password: 
LAPPNET
	\\TLEILAX        		Linux Mint
		\\TLEILAX\Print_to_PDF   	Print to a PDF File
		\\TLEILAX\IPC$           	IPC Service (Linux Mint)
		\\TLEILAX\video          	
		\\TLEILAX\audio          	
		\\TLEILAX\downloads      	
		\\TLEILAX\print$         	Printer Drivers
	\\SUNSPIRE       		
		\\SUNSPIRE\video
		\\SUNSPIRE\downloads
		\\SUNSPIRE\pleiades
...
```

---

### Post by txwooley on 2008-12-06
/etc/network/interfaces  only has 2 lines

auto lo
iface lo inet loopback

I think I am using a static IP. I'm connecting to my home network via a Dlink wireless router with satelite internet plugged directly into the router.  The satelite modem has claimed 192.168.0.1 as its own and no-one else can use it, so I think I set up static IP's for all the comps assigning progressive numbers.  The delinquent laptop we're speaking of uses 192.168.0.5

---

### Post by txwooley on 2008-12-06
I ran smbtree and got this:

WARNING: no network interfaces found


so I ran ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:1f:3a:a4:23:cc  
          inet addr:192.168.0.5  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fea4:23cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:130272 (127.2 KB)  TX bytes:15051 (14.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:46:1a:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6668 (6.5 KB)  TX bytes:6668 (6.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-A4-23-CC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2053 errors:0 dropped:0 overruns:0 frame:7
          TX packets:287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:219942 (214.7 KB)  TX bytes:25465 (24.8 KB)
          Interrupt:19 



I have to have somekind of network interface - I'm (wirelessly) on the internet right now!

---

### Post by txwooley on 2008-12-06
bump

---

