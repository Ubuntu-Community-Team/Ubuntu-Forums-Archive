---
title: "Dumb-simple file sharing Win11 -&gt; Ubuntu?"
date: 2022-03-15
forum: Networking &amp; Wireless
---

### Post by sremick on 2022-03-15
Been a long time since I've set up something like this. Much has changed. It used to be trivial.

Situation: Want to share a folder on a Windows 11 computer with someone using Ubuntu (20.04 LTS). They're using GNOME-classic DE.

This is a tiny family network, so security isn't important for this share. Intuitive ease-of-use is paramount. What I'd *like *for him (Ubuntu) to be able to do is simply go to Places -> Browse Network, open up "Windows Network", see the Windows 11 computer, double-click on that to open it, see the one share, and be able to open the share without any friction, user/pass prompts, etc. 

Ideally I'd like this share to be password-less. I'll begrudgingly sway on that if we can make the user/pass a one-time thing that Ubuntu guy can save at his end to not be prompted again.

On the Windows 11 end I've enabled Network Discovery (and checked the box for "Turn on automatic setup of network connected devices". I've turned on file and printer sharing. I've turned on Public Folder Sharing, and turned off "Password Protected Sharing". This is all under "Private networks", which is the current profile for the network the Windows 11 computer is connected to. The share name is simply called "Shared" and the Permissions for Shared are "Everyone" granted both "change" and "read" permissions. 

Ubuntu can ping the Win11 system by IP. But name broadcast/resolution isn't working and Ubuntu can't ping the Win11 system by host name. DHCP is in use so I don't want to bake in any static host names anywhere... I want this to just work as designed.

Unsurprisingly, nothing else works on the Ubuntu end either. You can't "Connect to server:" using smb://win11hostname. You can swap in the IP but then you get prompted for a username and password. If you try to directly connect to the share via smb://xxx.xxx.xxx.xxx/shared you get a different password prompt that gives you the option to connect as "Anonymous" or "Registered user", but "Anonymous" doesn't work (not that I'd really want to be limited like that... I'd like the list of shares on win11host to be browseable). 

What else do I need to do in order to get the desired simple behavior?

---

### Post by #&amp;thj^% on 2022-03-15
Yep it has changed, see if this helps: [https://websiteforstudents.com/how-to-access-shares-on-windows-11-from-ubuntu/](https://websiteforstudents.com/how-to-access-shares-on-windows-11-from-ubuntu/)

---

### Post by sremick on 2022-03-15
> **1fallen said:**
> Yep it has changed, see if this helps: [https://websiteforstudents.com/how-to-access-shares-on-windows-11-from-ubuntu/](https://websiteforstudents.com/how-to-access-shares-on-windows-11-from-ubuntu/)

Hi, thanks for the quick response. I actually still had that tab open, as it was one of the many websites I found and read before posting here.

I tried to make it clear in my original post that I had done all the things outlined in that website.

It basically falls apart at *"If Network Discovery is enabled and file sharing enable, you should see  shared file and folders in the Windows Network folder above." *as you cannot. It then proceeds to instruct you to connect via the servername, which fails because there's no name resolution working (Discovery broken?). Etc.

Samba is installed on the Ubuntu computer.

---

### Post by TheFu on 2022-03-16
This is for the Ubuntu system to mount Windows CIFS shares, not the other way around.

I think the "Browse Network" was broken by MSFT in 2020.
You can still mount the storage using a CIFS mount via the fstab with user credentials.
I use something like this in my fstab:
```
//172.22.22.14/D   /misc/D   cifs noauto,user,iocharset=utf8,vers=2.1,uid=1000,gid=1000,file_mode=0664,dir_mode=0775,credentials=/etc/samba/D.credentials  0 0
```
**[COLOR="#FF0000"]all on 1 line.[/COLOR]**  Inside the  /etc/samba/D.credentials file is the username= and password= lines, as specified for the Windows system.
You might want to change/remove the vers= setting. Win10 and later will negotiate v3 which is bother faster and more secure.

There are 6 fields in that line above.  The options field cannot have **any** spaces.  The number of spaces between each field has to be at least 1, but more is fine.

With my example line, the remote CIFS storage will be mounted at /misc/D. You can mount it anywhere you like, but I'd strongly recommend NOT putting it under any user's HOME for a number of reasons.  While against Linux standards, lots of remote storage is being placed under /media/. 
Obviously, change the other settings as required for your needs/connection.

---

### Post by Morbius1 on 2022-03-16
> Ubuntu can ping the Win11 system by IP. But name broadcast/resolution isn't working and Ubuntu can't ping the Win11 system by host name.

NetBIOS broadcast / resolution is disabled in Win10/11. It's been replaced by WS-Discovery. KDE based systems have a WSD client which sorta kinda works but it comes with ... well ... the rest of KDE. 

As far as pinging is concerned ping by the Win11 mDNS ( avahi in Linux ) host name instead - host name with a .local attached at the end:

[HTML]ping -c3 win11-host-name.local[/HTML]

Connect to server becomes **smb://win11-host-name.local/Shared**:
[ATTACH=CONFIG]290153[/ATTACH]

The alternative is to enable "SMB 1.0/CIFS Server" on your WIn11 machine. Microsoft ( and even Linux ) cautions you against this but it will return you to the bygone NetBIOS era: Settings > APPS > Optional Features > More Optional Features > SMB 1.0/CIFS File Sharing Support. WIn11 doesn't tell you this but you need to reboot it for SMB1 to be enabled again.
[ATTACH=CONFIG]290154[/ATTACH]

I normally don't allow SMB guest access on Windows machines so I'm not sure how that would work. I achieve the same result by creating a user named smbuser on the Windows machine and I give it a password smbuserpw. I use that one to access shares. And Nautilus can "remember forever" the password so you only have to enter it once.

---

### Post by uninvolved on 2022-03-16
If security isn't a major concern, you could look into FTP. **This isn't what you expected **- but hear me out.

One is a client, one is a server. We'll say Win10/11 is the client where you install Filezilla. You install the FTP server on the Linux side of things.

When you set up the Filezilla account, you make it navigate/show a specific folder on the server's hardware.

Then, if they want to share a file with you, they just connect to FTP and drag/drop it - and it's there for your consumption.

If you want to give them a file, you put it into that directory and they'll see it when they connect to the server.

It's a horrible hodgepodge, but it'd work.

It'd take 10 minutes to set it up on both computers and another 10 minutes to show them how to login with Filezilla. Once logged in, it resembles most every other file manager out there.

This isn't even remotely secure. You could probably create an FTP user without any privileges outside their own directory, while assigning permissions that let anyone read/write/edit, but then you're looking at having to navigate to their folders. It'd be an extra couple of steps when you want to share files - when you navigate to their directories.

---

### Post by TheFu on 2022-03-16
sftp is easy to setup and use on Linux. There are good clients for every other OS.

```
$ sudo apt install ssh fail2ban
```
That's it. By default, every normal local user on the Ubuntu system will have sftp access using their Ubuntu login.

From Windows, use WinSCP. Connect to the Ubuntu system using sftp/scp and then drag-n-drop files.
From other Linux clients, use any linux file manager. In the URL field, put in the IP address (sftp://192.169.1.x) or DNS name (sftp://bobs-computer) or mDNS name (sftp://bobs-computer.local), make the connection, enter the userid/password and drag-n-drop files to from any other file-manager window onto the Linux server.

sftp is easy and secure enough if using ssh-keys, never passwords, for internet use.
Setting this up takes 30 seconds. The hardest part is hunting down the winscp for Windows setup.exe.

You can setup an account to be shared by everyone in the house, if you like. I wouldn't, but you could.
You can create ssh-keys and pre-install those on all the clients to connect to the server. This would make the access seamless. No prompts for users or passwords, but that setup takes a but more, especially on Windows.  On Linux/Unix systems, it is 2 commands - 30 seconds total.  For most Linux noobs, it will take longer to type the commands correctly because they won't use select/paste or don't know how.  I think I could setup password-less access for ssh, scp, sftp, rsync between a Linux client and ubuntu server in less than 30 seconds total time.  5 commands total.  2 on the server, 3 on the client - this assumes 100% default and working Ubuntu on both sides. It really is that simple. No need to have bad security.

Just running **sudo apt install ssh** on both the client and the server will make using ssh/scp/sftp between both systems with userids and passwords possible, though entering or having a file manager remember a password is poor security. Use ssh-keys, please.

But between Windows and Linux, CIFS is the expected answer and should perform a little better since it lacks the same level of authentication and encryption as sftp/ssh/scp use.

To share all the files in 1 directory for read-only access, there are plenty of 1-line webservers.  Python, Ruby, Perl all have 1.
Python 2.x
```
  $ python -m SimpleHTTPServer 8000
```

Python 3.x
```
  $ python -m http.server 8000
```

Ruby```

   $ ruby -rwebrick -e'WEBrick::HTTPServer.new(:Port => 8000,
                        :DocumentRoot => Dir.pwd).start'
```

Ruby 1.9.2+
```
   $ ruby -run -ehttpd . -p8000
```

Perl```

   $ cpan HTTP::Server::Brick   # install dependency
   $ perl -MHTTP::Server::Brick -e
           '$s=HTTP::Server::Brick->new(port=>8000);
            $s->mount("/"=>{path=>"."});
            $s->start'
```

http-server (Node.js)```

   $ npm install -g http-server   # install dependency
   $ http-server -p 8000
```

node-static (Node.js)```

   $ npm install -g node-static   # install dependency
   $ static -p 8000

```
PHP (>= 5.4)
```
   $ php -S 127.0.0.1:8000
```
    
busybox httpd
```
   $ busybox httpd -f -p 8000
```

These are are highly non-secure. Anyone with access to the webserver will have access. No login. No credentials.

sftp is better for many reasons, but if you have any of those languages already on a system (python3 should be on all Ubuntu 20.04+ already, and need read-only access to 1 directory structure for 30 seconds on a LAN, sure. Why not.

---

