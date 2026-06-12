---
title: "Connect Ubuntu to WinXp"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by countrylane on 2008-04-10
I am trying to get my Ubuntu box to talk to my WinXp box. My Ubuntu box can see my WinXp box, including shared files and folders. I can view graphics files on my WinXp box from a graphics file viewer on my Ubuntu box.  I did this by modifying the smb.conf file that came with Ubuntu using the gsambad configuration tool. Nothing I did would allow me to view my Ubuntu PC in the WinXP Network Neighborhood

I finally gave up and went to samba.org. They had a bare bones smb.conf file that they said:
"will allow connections by anyone with an account on the server, using either their login name or homes as the service name"

Here is the file:
[global]
workgroup = MIDEARTH
[homes]
guest ok = no
read only = no

I changed MIDEARTH to the workgroup name that I am using. I can now get my Ubuntu to be seen in the WinXP Network Neighborhood, but when I click on the link, I get a user name/password box that I cannot get past. I have tried every combination of username/passwords that I have ever used with no luck. I also cant get past the login screen by just submitting blank entries.

What now? I am at a loss as to what to do next.

---

### Post by superprash2003 on 2008-04-10
have you added a samba user?
sudo smbpasswd -a system_username

[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by countrylane on 2008-04-10
Followup:
I reinstalled my original smb.conf file. When I am on my WinXP machine and look for computers in my Workgroup, the Ubuntu PC is listed, but when I click on the link I get the follwing error message:

\\Samba24 is no longer available. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.  The specified network name is no longer available.

I can see all of the shared files on my WinXP machine from my Ubuntu machine when the above error occurs.

---

### Post by countrylane on 2008-04-10
> **superprash2003 said:**
> have you added a samba user?
sudo smbpasswd -a system_username

Yes. I get this error:
Failed to modify password entry for user [username]

---

### Post by superprash2003 on 2008-04-10
you need to add a username who is a system user.. say you want to create a samba user called test , that user should be present as a ubuntu system user

---

### Post by countrylane on 2008-04-10
> **superprash2003 said:**
> you need to add a username who is a system user.. say you want to create a samba user called test , that user should be present as a ubuntu system user

OK, I added an administrator account to Ubuntu......then did....

sudo smbpasswd -a system_username

I then went into the smb.conf file using gsambad (I could just edit the file manually I guess, but I am more comfortable with the graphical front end).  I verified the new admin user was in the USERS section. For good measure I stopped and restarted Samba.  I went to my WinXp box, opened the "View workgroup computers" link, clicked on the Ubuntu link and got the same .....\\Samba24 is not accessable..... error message.

---

### Post by Eiríkr on 2008-04-10
Ditto to what superprash2003 said.  Have a look at **man smbpasswd** in a terminal for details.  This quote is from the man page:
> **OPTIONS**
**-a**
This option specifies that the username following should be added  to  the  local  smbpasswd  file,  with  the  new  password typed (type <Enter> for the old password). This option is ignored if the username following already exists in the smbpasswd file and it is  treated  like a regular change password command. **Note that the default passdb backends  require  the  user  to  already  exist  in  the  system  password  file  (usually /etc/passwd), else the request to add the user will fail.**
That last sentence means, as superprash2003 pointed out, that the username you feed into the Samba password program ***must*** exist as a regular username on your server's OS.  

Cheers,

Eiríkr

---

### Post by Eiríkr on 2008-04-10
> **countrylane said:**
> OK, I added an administrator account to Ubuntu......then did....

sudo smbpasswd -a system_username

**I then went into the smb.conf file using gsambad** (I could just edit the file manually I guess, but I am more comfortable with the graphical front end).  I verified the new admin user was in the USERS section. For good measure I stopped and restarted Samba.  I went to my WinXp box, opened the "View workgroup computers" link, clicked on the Ubuntu link and got the same .....\\Samba24 is not accessable..... error message.

PLEASE post your smb.conf file here for a sanity check once you're done -- I've seen some truly horrendous results from the gsambad tool, and I very much expect that whatever it outputs will be barely usable and possibly bork up your server (the software, not the hardware ;)).  

Cheers,

Eiríkr

---

### Post by countrylane on 2008-04-10
Here is my smb.conf generated by gsambd.  I modified the workgroup name, chnaged the IPs to match my network, and then later on edited/added the administrator user per an earlier suggestion.

[global]
netbios name = Samba24
server string = Carl
workgroup = WORKGROUP
security = user
hosts allow = 192.168.1.0
interfaces = 127.0.0.1/8 192.168.1.0/24 
remote announce = 192.168.1.255
remote browse sync = 192.168.1.255
printcap name = /etc/printcap
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = yes
username level = 8
password level = 8
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins server = 
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gsambadpdf %s %u
lpq command =
lprm command =

---

### Post by Eiríkr on 2008-04-10
Oh good CHRISTMAS this is fugly.  I'm really hating gsambad, as it *pretends* to offer users a GUI config tool, but the garbage it spews out is truly unconscionable.  There's *tons* of stuff in here that you don't need, and quite a few options that have bogus values, and some options that themselves are bogus.  

If you're interested in how messed up gsambad is, have a look at [post=4577292]this post[/post] and [post=4654123]this post[/post].  In both of these, I go over the options, link to [the online smb.conf man page]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html"), and note what options are redundant, irrelevant, and bogus.   

As it is, there are just so bleeping many bad options here, I'm just going to prune them out.  After doing so, your conf file looks like this.  Notice that it's a **heck** of a lot smaller.  

```
[global]
# NetBIOS name resolution options
   netbios name = Samba24
   server string = Carl
   workgroup = WORKGROUP
   wins support = yes     # Changed from "no"
# Master browser options (related to name resolution)
   local master = yes     # Changed from "no"
   domain master = yes    # Changed from "no"
   preferred master = yes # Changed from "no"
# Network security options
   hosts allow = 192.168.1.0/24 # Added /24 subnet mask (required)
   interfaces = 127.0.0.1/8 192.168.1.0/24
# User security options
   security = user
   encrypt passwords = yes
   obey pam restrictions = yes
   username map = /etc/samba/smbusers  # Only useful if mapping usernames
   passwd program = /usr/bin/passwd '%u'
   passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
   
[homes]
   comment = Home Directories
   read only = no
```

Note that the "username map" option may be deleted if you're not using the indicated /etc/samba/smbusers file to map usernames.  If you don't know what username mapping is but might be interested, look at [post=4496702]this post[/post] and scroll down to the "In the [global] section" portion, where I describe how username mapping works.  

I hope this helps.  And ***please***, for the love of sanity, remove the **gsambad** package.  The accent here is really on the **bad** -- just look at how much cruft was removable from your conf file.  

Cheers,

Eiríkr

---

### Post by countrylane on 2008-04-10
Thank you, Thank you, Thank you.

I copied/pasted your file....commented out the "username map" line.....saved it as smb.conf...restarted Samba......and like magic, my linux box was viisble on my WinXP box and I was able to log in and browse around inside my linux box.

Now that it works I have several questions:
When I clicked on the link to access my Ubuntu files, a username/password box popped up. I tried using my regular username and password, which didn't work. I got in with my newly-created administrator level username/password (from a suggestion earlier in this thread). Why can't I use my regular name/password?  Or no username/password at all? Or a non-administrator level user name/password?

Sorry if those questions seem elementary, but right now I am not sure I have the stamina to look through any more help files to find the answer or the courage to change anything now that it works.

Again, thank you.

---

### Post by Eiríkr on 2008-04-10
You're welcome.  :)  I like it when folks get Samba working, as that's one less reason to pay the Microsoft tax.  :mrgreen:

When accessing a Samba share from Windows, you will always be prompted for a username and password at least once (possibly more often, depending on how you set things up on the Windows side -- if you map a network drive to the share and check the "Reconnect on logon" box in the dialog, you only need to enter the username and password that once, as the drive (i.e. share) is mounted automatically thereafter).  

No username or password means guest access, in Samba terms.  This is possible to set up, but can also be complicated, and so is generally not recommended unless needed.  

You *should* be able to use your normal Ubuntu username, *unless* you haven't yet added it to the Samba password file using the **smbpasswd** command:
```
sudo smbpasswd -a REGULARUSERNAME
```
Enter whatever password you want at the prompt.  Note that the password you use in Samba doesn't have to be the same as your Ubuntu login password; it's easier to remember if they're the same, but more secure if they're different.  

Does that help?

Cheers,

Eiríkr

---

### Post by countrylane on 2008-04-11
I created the regular username/password in Samba. That worked. I can now log in as a regular user.  I also mapped a network drive to try and stop having to log in every time.  The mapping worked (including checking the box to reconnect at login), but I still need to log in every time.  I was not able to map the share until after I logged in. Then I was abl to map a user folder as the Z drive. Windows wouldnt let me map the actual share that appears in the Windows Workgroup computer list.

---

### Post by Eiríkr on 2008-04-11
Ah, yes -- in Explorer with the Folder pane open on the left, the drill-down order is: **My Network Places -> Entire Network -> Microsoft Windows Network -> WORKGROUP -> SERVER -> SHARE**.  You can only map a network drive (i.e. mount) at the SHARE level or below (i.e. a subdirectory within the SHARE).  The SERVER level is not mountable.  

Does that make sense?

Plus, after mapping the network drive, do you get Samba username and password prompts after you log in to Windows but before the network drive (share) automatically mounts?

Cheers,

Eiríkr

---

### Post by countrylane on 2008-04-11
> **Eiríkr said:**
> Plus, after mapping the network drive, do you get Samba username and password prompts after you log in to Windows but before the network drive (share) automatically mounts?

I'm not sure I understand your question. Here is what happens, step by step. Hopefully this will answer your question.
1. Power up the Windows PC.
2. Windows log-in screen appears with all the users of the computer displayed.
3. Login to my Windows user account.
4. Open My Network Places. (There are several network connections shwon on the right side of the pane, but I will ignore those for the moment).
5. Click on "View Workgroup Computers". Two computers appear in the right pane....my WinXP box and the Samba share.
6. I click on the Samba share.
7. A username/password box appears.
8. I enter my Samba name/pass and can now view my Ubuntu/Samba shares/files.
9. I select my home folder and map it as a network drive.

If I then log off and power up the PC again, I either need to go through all 9 steps again to re-access my Ubuntu files ----or---- repeat steps 1 through 3 then click on My Computer.  The network drive is there. Click on it, then get the user/pass box where I then enter my Samba username/pass to gain access.

Basically, not matter what sequence I go through, I always need to enter my Samba username and password.

---

### Post by Eiríkr on 2008-04-11
Iiiinteresting.  What version of Windows are you using?  I've got XP Pro on my end, and things definitely sound different.  For one, in My Network Places, there is no "View Workgroup Computers" icon.  For another, once I map a drive, I no longer need to enter anything to access the mapped drive.  Nor, in fact, do I need to provide any info at all to access any of the server shares, as presumably once my info has been entered (by the automatic network drive mounter in Windows), the Samba server is happy to consider me as already authenticated.  

Might you perchance be running XP Home?  I am slowly learning (mainly through folks here on the boards) about the oddball ways in which Home has been deliberately crippled (not that Pro doesn't have its faults), and I'm wondering if what you describe might be part of that.  

Cheers,

Eiríkr

---

### Post by countrylane on 2008-04-11
I am running WinXP Pro Service Pack 2. with all of the latest updates.  Here is what is in the "My Network Places" left-hand pane:
There is a block titled "NETWORK TASKS" with these items in the block:
Add a Network Place
View Network Connections
Set Up A Home or Small Office Network
Set Up A Wireless Network for a Home or Small Office
View Workgroup Computers
Show Icons for Networked Upnp Devices

Then there is a block titled "OTHER PLACES" with these items in the block:
Desktop
My Computer
My Documents
Shared Documents
Printers and Faxes

Then there is a block titled "DETAILS" with these items in the block:
My Network Places (not clickable)
System Folder (not clickable)

---

### Post by Iowan on 2008-04-11
Probably off-base (as usual)...
Did you check the "Reconnect at logon" box?

---

### Post by countrylane on 2008-04-11
> **Iowan said:**
> Probably off-base (as usual)...
Did you check the "Reconnect at logon" box?

Any help or suggestion is welcome. Yes, I did that. Doesn't seem to matter. Originally, I thought I may have forgotten to do that, so I deleted the mapped drive and re-attached it, verifying that it was checked. I got the same result.

One thought that just hit me though, is when I boot my Windows box, I am presented with a screen that has several user icons. When I click mine, WinXP continues to start up normally. I don't need to enter a password to log into my account.  I don't remember now if I configured Windows to automatically enter my password, or if I set it to log into my account without a password. I am also not sure if one or the other scenario is even possible.  Both of the other users have passwords for their accounts.  I will have to see if, when I boot the PC and they login, if the shares just automatically work or not. I will also try to change my account to require a manually entered password and see if that fixes things.

---

### Post by Eiríkr on 2008-04-11
@Iowan --

Glad to have another pair of knowledgable eyes looking things over.  :)  From the description above, it sounds like the network drive is appearing on logon, which would suggest that countrylane had checked the "Reconnect" button.  

@countrylane, can you confirm this?

----------

@countrylane --

Oho!  :idea: :o  Yep, what you're looking at is *not* the same as what I'm looking at, but I think we can get these two thingies to agree -- what you're looking at is the generic left-hand pane that shows up in Explorer under XP.  What I'm looking at is the Explorer left-hand pane that shows up when you click the Folders toolbar button at the top of the Explorer window.  So if you click the same Folders button, your left-hand Explorer pane should change to look like a tree view with Desktop at the top, followed (probably) by My Documents, then My Computer, then My Network Places.  

ANYway, that aside, your question / concern about what is mountable equates to #5 in your list of what you do to access your shares:
> 5. Click on "View Workgroup Computers". Two computers appear in the right pane....my WinXP box and the **Samba share**.
What you call your "Samba share" here is actually your Samba **server**, which is not mountable; the shares themselves are *on* the server, and show up after you open the server icon.  These *are* mountable (and thus mappable as network drives).  

But this still doesn't answer the question of why you're still being prompted for login info after mapping the drive.  As a shot in the dark here, I'm guessing that your Windows and Samba / Ubuntu usernames are different, and that perhaps the automagic info caching that Windows does only works if they're the same, or if the Windows username is mapped to the Samba / Ubuntu username by a username map file, pointed to by the **username map** [global] option in your smb.conf file.  

If you don't mind experimenting for a moment, open your smb.conf file for editing:
```
sudo gedit /etc/samba/smb.conf
```

In the [global] section, add the following line:
```
username map = /etc/samba/users.map
```

Save and close the smb.conf file, but keep gedit open.  If you accidentally close gedit (or if it closes itself if there's no docs open), reopen it in sudo mode:
```
sudo gedit
```

Start a new empty document and type in the following:
```
UBUNTUUSERNAME=WINDOWSUSERNAME
```
Replace the caps as appropriate.  Enter the Ubuntu username you'd like to use for Samba access.  Save the file as **/etc/samba/users.map**, and close out gedit.  

Restart your Samba server:
```
sudo /etc/init.d/samba restart
```

Just for good measure, you might want to reboot your WinXP machine.  Then log in, disconnect the old networked drive to the share, map a new network drive, and in the username and password prompt, enter your Windows login username but your Samba password.  Again, click the "Reconnect on logon" button.  Then try rebooting and see if the share mounts on logon and if you can get into it without needing to enter anything this time.  

HTH,

Eiríkr

---

### Post by countrylane on 2008-04-11
I changed my WinXP account login to require a password.  That didn't change anything. I still got a login request when I tried to access the Ubuntu PC.

I followed your suggestions Eiríkr and created the users.map file and added the GLOBAL line of text to the smb.conf file.  Restarted Samba. Powered down/up the WinXP box and am still getting the login request. I deleted the existing network drives, remapped them, then powered down and back up again. Same result.  When I click on the My Computer icon, the mapped drive is there, but it has a status of Disconnected.  When I click on the mapped drive, I am asked for a username and password, same as always.  Probably a stupid question, but does the username as I entered it into the users.map file need to be any special case (ie all upper, all lower, etc....). Windows doesn't pay attention to case in a variety of situations. I am wondering if the username as I entered it in the users.map file (Xxxxx) is being sent by Windows when I log in as XXXX or xxxx. Just a thought.

This is getting a little frustrating.  On the positive side, I added this to my smb.conf file and am now able to print from my WinXP machine to the printer connected to the parallel port on my Ubuntu machine (after logging into the networked drive):

[printers]
comment = All Printers
browseable = yes
path = /var/spool/samba
printable = yes
public = no
writable = no
create mode = 0700

---

### Post by Eiríkr on 2008-04-11
Glad to hear that printing is working.  :)  But I'm baffled as to why Windows isn't keeping the login information; in a few other threads, we were dealing with the opposite situation, where Windows was keeping old (and now incorrect) login information that we couldn't get it to *forget*.  In fact, one user even wrote [thread=720889]this HOWTO[/thread] about altering the Registry to keep Windows from storing the info; maybe the HOWTO might be useful to you in reverse?

Cheers,

Eiríkr

---

### Post by countrylane on 2008-04-11
Thanks for the Howto. I looked at it briefly but it is now about 10:30PM and I started the day at about 6AM, so I am fading fast.  I'll try to figure this out over the weekend and post my results.  Thanks again for sticking with this and providing all of the good suggestions and tips. It is appreciated.

---

### Post by gsiliceo on 2008-04-13
You can vote to change this in ubuntu using the brainstorm page, theres already an idea voting to make samba easier. Please vote here.
[Improve file/folder sharing experience (Samba)]("http://brainstorm.ubuntu.com/idea/403/")

---

