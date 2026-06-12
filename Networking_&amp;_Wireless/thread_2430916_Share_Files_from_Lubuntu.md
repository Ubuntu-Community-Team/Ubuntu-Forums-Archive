---
title: "Share Files from Lubuntu?"
date: 2019-11-09
forum: Networking &amp; Wireless
---

### Post by 2CV67 on 2019-11-09
Hi!

I just installed Lubuntu 18.04.3 (so LXDE) on my little old Asus EeePC Netbook, replacing Ubuntu which had been getting too troublesome.

Most things are working very well, but I am unable to share files from Lubuntu on my local WiFi network.
*(Note: - I have another thread open on non-admin file sharing in Ubuntu, but I think this is really a separate subject)*

From the Lubuntu Netbook, I can easily see & manipulate shareable files on my main Ubuntu 19.04 PC.
From the PC, I see the Netbook but only the folder "print$".
(Printing over the network from the Netbook works fine, by the way.)

When I tried to make files shareable in Lubuntu, I started in the pcmanfm file manager by right-clicking the file & selecting "Properties" but there is nothing there concerning sharing.

I saw somewhere that I should be able to Go: Preferences > Samba and see a Samba Configuration GUI to make files shareable, but I don't find Samba anywhere in my menus, Preferences, System tools, Accessories etc...
Samba IS installed & I can open the smb.conf file OK, but I don't want to start messing with that file.

Is there a GUI method I have missed?

Thanks!

---

### Post by 2CV67 on 2019-11-09
OK - it seems to be working now...

I saw I should be able to launch Samba GUI from Terminal with:
```
sudo system-config-samba
```
But that brought:
```
sudo: system-config-samba: command not found
```

SynApt showed me system-config-samba was not installed.
So I installed it.

sudo system-config-samba then brought a long error message including:
```
could not open configuration file '/etc/libuser.conf': No such file or directory
```

I found an answer to that in Ask Ubuntu:
- Create the file with:
```
sudo touch /etc/libuser.conf
```

I was then able to launch Samba GUI from terminal with:
```
sudo system-config-samba
```
and set up my share OK.
It can be seen from my other PC.
Nothing changed in File Manager to indicate file is now shared.

Menu > System Tools now includes a launcher for Samba but it does not work (yet?).
It brings up an error message about invalid file 'usr/share/applications/system-config-samba.desktop'
There is no such file in File Manager...

---

### Post by Morbius1 on 2019-11-09
> Menu > System Tools now includes a launcher for Samba but it does not work (yet?).
You are fighting a battle with system-config-samba that you will eventually not win.

Samba in the menu will not run because it's designed to run [highlight]gksu system-config-samba[/highlight]

There is no gksu. It should be pkexec system-config-samba but you can't just edit the file and replace it. You have to build a pkexec just for that application. It's all very complicated and at the end of the day it's not worth fixing for two reasons:

[1] It hasn't been updated in 11 years and one of it's options will actually stop samba from running.

[B] THe system-config-samba package was removed from the repositories beginning with Ubuntu 19.04

If you must use it in your current version there's nothing wrong with invoking it in a terminal with sudo - but for the grace of <fill in the name of your personal deity > do it wth the -H option:
```
sudo -H system-config-samba
```

---

### Post by 2CV67 on 2019-11-10
Thanks for your dire warning, Morbius!

I have no desire to continue bashing my head against a brick wall.

I now know what not to do.

So:  How should I share files from Lubuntu?

---

### Post by TheFu on 2019-11-10
> **2CV67 said:**
>  
So:  How should I share files from Lubuntu?

You can use any number of protocols, not just SMB or CIFS to share files. There are at least these:  NFS, SFTP, SCP, rsync, HTTP.

On the "server", getting the sftp/scp working is the easiest.  
```
sudo apt install openssh-server fail2ban
```
That command will install and setup the ssh server and a brute-force prevention tool.  With that 1 command, we get support for encrypted ssh, sftp, scp, transfers.\

On the client, you can use any sftp client.  WinSCP on Windows.  Any file browser on Linux using sftp:// URLs after the "ssh" package is installed on the client. sftp is secure enough for use over the internet.

On the same LAN, if there is MS-Windows, samba is the most convenient choice to use. The best settings depends on the clients that will be connecting. Win10 needs different settings than other versions of Windows.
If there isn't any Windows clients, just Unix/Linux clients, then I'd go with NFS.  We can help set that up, if you are interested, but there will be text config files that need to be edited on both the client-side and the server-side.  For the best security, both clients and servers should have static IPs. Ain't no GUI for NFS.

---

### Post by Morbius1 on 2019-11-10
>  So:  How should I share files from Lubuntu?         
Samba is the default file sharing mechanism for the Ubuntu family since basic components of it are already present in a default install and are part of the Linux kernel. So if you want to continue to use it and want to create shares do it by editing the /etc/samba/smb.conf file directly.

For example, to create a share of your public folder accessible to everyone on your lan at the bottom of the file add the following - I will use my own user name in the example:
```
[Public]
path = /home/morbius/Public
read only = No
guest ok = yes
force user = morbius
```
To create a share that requires credentials to access just change [highlight]guest ok[/highlight] from [COLOR=#0000cd]**yes**[/COLOR] to [COLOR=#0000cd]**No**[/COLOR]:
```
[Public]
path = /home/morbius/Public
read only = No
guest ok = no
force user = morbius
```
If credentials are required remember that unlike Windows there are two  passwords for every user. One is used to log into the machine itself and  the other is to log into the samba server. You create that "samba  password" with this command:
```
sudo smbpasswd -a morbius
```

In either case after adding the share definition and saving smb.conf remember to restart the smbd service:
```
sudo service smbd restart
```

The way Samba has evolved it will automatically be visible to all other Linux clients and all other MacOS clients present on your network.

---

### Post by Morbius1 on 2019-11-11
To go back to the original issue:
> When I tried to make files shareable in Lubuntu, I started in the  pcmanfm file manager by right-clicking the file & selecting  "Properties" but there is nothing there concerning sharing.
I installed Lubuntu 19.04 and started poking around PCManFM the last few days to see if something can be modified to allow creating a share of a folder through the file manager and I have come up with something that can work if you are interested.

---

### Post by 2CV67 on 2019-11-11
Yes, Morbius1, I am interested in what you found.

But please see also the following which I was just preparing when I saw your new post>>>>>>
.......................................

Thanks, TheFu & Morbius1, for your helpful contributions.

Let me just comment that I am amazed & appalled that there is not a simple GUI method to set up simple file sharing.

As there will occasionally be Windows clients on my network, I accept to go with samba.
I looked at the smb.config file & left with my head spinning...
I read all the tutorials I could find on samba & thought it was way beyond me.

So I blindly copied the code from Morbius1
```
[Public]
path = /home/morbius/Public
read only = No
guest ok = yes
force user = morbius
```
at the end of /etc/samba/smb.conf file
Changing the name, obviously.
And it works! (Thank you!)

In the process, I had to learn/remember to:
- create a backup with
```
cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```
- Open file in text editor as admin with
```
sudo leafpad /etc/samba/smb.conf
```
(no gedit installed in Lubuntu)

Out of curiosity, I looked in the smb.config file on my Ubuntu PC, where I had added file-sharing with a couple of GUI clicks, and found there was a similar, but different, entry for my share:
```
[Desktop]
	path = /home/xxxx/Desktop
	writeable = yes
;	browseable = yes
	guest ok = yes
```

I experimented with that entry on the Lubuntu Netbook & that worked fine too.

Please tell me if there is any significant difference/preference between the 2 entries (unless that involves pages & pages of samba documentation, in which case I am too old!)

I further experimented to see if I could use that latest entry to create a share for another user on the Netbook & that worked fine too!
That was the subject & answer to my other open thread mentioned above.

So, thank you again TheFu & Morbius1 and I will happily mark both threads SOLVED.
...................................

But I would be even happier if the skeleton could be published as "Ubuntu/Lubuntu File-sharing for Dummies" somewhere.

I suppose it would go something like:

1. Install samba (but not system-config-samba ?).

2. From Terminal, make a backup of /etc/samba/smb.conf with:
```
cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

3. From Terminal, open /etc/samba/smb.conf in text-editor as admin with:
```
sudo leafpad /etc/samba/smb.conf
```
or
```
sudo gedit /etc/samba/smb.conf
```
or whichever text editor is installed.

4. Copy in at the very end:
```
[AAAA]
	path = BBBB
	writeable = yes
;	browseable = yes
	guest ok = yes
```

5. Replace AAAA by whatever name you want your new shared file to show to others
Replace BBBB by path to file you want to share (your own or other user) e.g. /home/me/Desktop
*(Is there any point leaving the commented-out browseable line? What does it mean?)*
*(Or should we prefer Morbius1's version?)*

6. Save smb.conf file

7. From Terminal, enter:
```
testparm
```
to check for errors *(but I don't know how to interpret the output)*

8. From Terminal, enter:
```
sudo service smbd restart
```

That should be about all, shouldn't it?

IMPORTANT: Nobody should rely on what I have written above - I am not competent to advise on this stuff!!!

---

### Post by Morbius1 on 2019-11-11
> Please tell me if there is any significant difference/preference between  the 2 entries (unless that involves pages & pages of samba  documentation, in which case I am too old!)
What you did is fine:
 [highlight]read only = No[/highlight] and [highlight]writeable = yes[/highlight] mean the same thing to samba.

The only other difference is the use of [highlight]force user = morbius[/highlight]. I do that so that the file added by the guest user is editable to - in this case - morbius on the server. Otherwise it saves with owner = nobody ( which is an actual user ) and writeable only to that user.

As far as the [highlight];browseable[/highlight] entry that's the implied default for all share definitions so it's really not needed. 

[COLOR=#0000cd]* Please add a -H when you do this kind of thing:*[/COLOR]
> sudo leafpad /etc/samba/smb.conf
```
sudo -H leafpad /etc/samba/smb.conf
```
[COLOR=#0000cd]* Sooner or later using sudo by itself to invoke a gui application will get you in trouble.*[/COLOR]

In the long run my personal opinion is editing smb.conf directly as you have done is the better way to go. 

The method to use PCManFM will create a samba share as well but not in smb.conf. It's called a usershare and is what things like Nautilus does in Gnome. IT's best not to use both methods at the same time on the same folder. I will post that method in my next post as soon as I make it more comprehensible ;)

---

### Post by Morbius1 on 2019-11-11
OK, here goes: Creating Samba Shares from PCManFM-QT

[1] Create a subfolder in your home directory:
```
mkdir -p ~/.local/share/file-manager/actions 
```
[2] Open PCManFM and create 3 files under the actions folder:

*** [highlight]SMBGuestShare.desktop[/highlight] with this content:
```
[Desktop Entry]
Type=Action
Name=Create Public Share
Icon=gtk-connect

Profiles=create_share;

[X-Action-Profile create_share]
MimeTypes=inode/directory;
Exec=net usershare add %w %f "" Everyone:F guest_ok=y
```

*** [highlight]SMBPrivateShare.desktop[/highlight] with this content:
```
[Desktop Entry]
Type=Action
Name=Create Private Share
Icon=gtk-connect

Profiles=create_share;

[X-Action-Profile create_share]
MimeTypes=inode/directory;
Exec=net usershare add %w %f "" Everyone:F guest_ok=n

```
*** [highlight]RemoveSMBShare.desktop[/highlight] with this content:
```
[Desktop Entry]
Type=Action
Name=Remove SMB Share
Icon=gtk-disconnect

Profiles=remove_share;

[X-Action-Profile remove_share]
MimeTypes=inode/directory;
Exec=net usershare delete %w
```

In each case after you save the file right click it and enable the "[highlight]Trust this executable[/highlight]" option.

[3] Now here's where it gets tricky. I've done this multiple times now to get rid of the kinks in the process and you will have to logoff and logon again for the options to appear. You might have to reboot but ...

When you go to a folder you own right click and you will see 3 new options in your context menu:
[ATTACH=CONFIG]284393[/ATTACH]

The share definitions you create in this method are under /var/lib/samba/usershares. You can get a list of how all these types of shares are configured with this command:
```
net usershare info --long
```

[COLOR=#0000ff]**Note**: It's best not to use both methods at the same time - on the same folder. Since they are defined in two different location you risk them not being defined the same way resulting in Samba getting confused.

[/COLOR][COLOR=#000000]On the whole I'd rather just edit smb.conf directly as you have done since you have more control over how the share is defined - but it can be done this way.[/COLOR]

---

### Post by 2CV67 on 2019-11-12
Morbius1, I want to thank you very much for the trouble you have taken over this and for the clear detailing you have used!

I will go with your recommendation to stick with the smb.config route.

And I will try hard to remember sudo -H !

I will mark the thread SOLVED.

---

