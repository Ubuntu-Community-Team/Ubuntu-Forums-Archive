---
title: "Samba - multiple users, different shares"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by IainPurdie on 2008-02-28
I've checked the alternative threads mentioned but not quite found the info I'm looking for...

I've got Samba up and going (on Ubuntu 6.06) fairly well. The aim is to have two shares - one publicly accessible without requiring a password/username and one secure, requiring a username password stored on the Ubuntu box.

My smb.conf is as follows:

[global]
workgroup = WORKGROUP
interfaces = lo eth0
bind interfaces only = true
local master = yes
guest account = nobody
map to guest = bad user
security = user

[accounts]
path = /home/AccountsShare
guest ok = no
user = accounts
public = no
browseable = no
read only = no

[Documents]
browseable = yes
browsable = yes
path = /home/shared
public = yes
writeable = yes
guest ok = yes

No need to hide anything to protect the innocent! The "accounts" one is to require password authentication, Documents for any and all to access.

AccountsShare is owned by accounts:account (chmod 755)
shared is owned by nobody:nogroup (chmod 777)

The problem I have is that if someone logs in as "accounts" to access the protected share, and then navigates over to the shared folder, they cannot create new files, change existing ones etc etc. They "carry" the login information over. This is the same if they connect as accounts and then close the window and later connect to the shared folder. The system "remembers", I assume, the PC they logged in from as last being logged in as "accounts".

Is there a way to keep these both separate so that one user on one PC (all clients are Windows XP or Vista *spit*) can access both, if required?

I also seem to have another problem. In getting the non-passworded share working I can no longer connect as the "accounts" login. The only PC which will connect is the one which was logged on before I made changes... and it's stuck as "accounts" so can't do much in the "shared" folder!

I've restarted Samba a couple of times, and also entered a new password for "accounts" just to make sure I've got that right. No joy.

Argh. Any help appreciated!

---

### Post by akudewan on 2008-02-28
I don't know much about networking and samba, but you could try the *user@domain* thing while accessing the shares...

For instance, smb://username@hostname works with Nautilus. For windows I'm guessing it would be something like \\username@hostname

---

### Post by IainPurdie on 2008-02-28
The issue is to avoid doing this as the users are used to connecting to a Windows share, and they navigate to the Samba one in a variety of ways - desktop shortcut, start/run, My Network Places... The connection to the share has to be as transparent as possible with no logins required (except for the accounts one which now seems to be refusing the password provided... *sigh*)

---

### Post by jhetrick62 on 2008-02-28
My guess is that you haven't set any login credentialing for this share, so it isn't following this properly.

You need to have at the least, some sort of credentialing such as:
username map = /etc/samba/smbusers

This may help with that.  I force everyone to log into my server but then I use PAM for credentialing.

Try adding these lines to the documents share:
force user = nobody 
force group = nogroup

Again, my solution would be to use a group name like "shared" on this and assign all valid users to belong to that group, but I know you don't want to have to do that.

See if this helps,
Jeff

---

### Post by Eiríkr on 2008-02-28
> **IainPurdie said:**
> I've checked the alternative threads mentioned but not quite found the info I'm looking for...

I've got Samba up and going (on Ubuntu 6.06) fairly well. The aim is to have two shares - one publicly accessible without requiring a password/username and one secure, requiring a username password stored on the Ubuntu box...

<... snip ...>

AccountsShare is owned by accounts:account (chmod 755)
shared is owned by nobody:nogroup (chmod 777)

The problem I have is that if someone logs in as "accounts" to access the protected share, and then navigates over to the shared folder, they cannot create new files, change existing ones etc etc. They "carry" the login information over. This is the same if they connect as accounts and then close the window and later connect to the shared folder. The system "remembers", I assume, the PC they logged in from as last being logged in as "accounts".


[[color=gray]NB: I've got Samba v3.026 on Xubuntu Gutsy 7.10.  The examples here assume that [font=courier]smb.conf[/font] default values are the same as for v3.026.[/color]]

From what you describe, it sounds like you need to set up a couple different things on the server for this to work properly.  You need to make sure Samba knows who is logging in, so you can control access, but you also need to be able to simply control permissions.  

Now you have to ask yourself, do you care if you can tell later who did what in either the shared or account folders, in terms of the specific Windows (or other client) usernames?  If you *do*, then things get a bit more complicated, but are definitely do-able.  I can describe that for you later if you decide it's what you want.  If that level of finely-grained security doesn't matter to you, things are simpler.  Here's the simple setup.  It's long, but bear with me.  :)

---------------
**Simple Setup (username mapping)**

Jeff's suggestion of using the global option [font=courier]username map = /etc/samba/smbusers[/font] is an excellent one.  I don't know if you're at all familiar with username mapping in Samba, but it can be very useful.  Let's assume you've got two small groups of users like below:
```

Group A                 Group B
(Shared)                (Accounts + Shared)
User1                   User2
User2                   User5
User3
User4
User5

```

You would then set up your [font=courier]/etc/samba/smbusers[/font] file as follows.  Note the first column holds the Ubuntu usernames, the second column the client usernames (Windows users in your case, but could just as well be Mac or Linux clients too).  

```

User1=shared
User2=accounts
User3=shared
User4=shared
User5=accounts

```

So any time User1 logs in, Samba logs them in as the "shared" user, whereas User5 would become the "accounts" user.  Great!  

*** *Filesystem Permissions*

The big thing I'll look at here is permissions on the Ubuntu Samba server side.  Setting up proper filesystem permissions on the server itself can lead to much more secure and manageable shares, and a much simpler [font=courier]smb.conf[/font] file.  

User groups can be a powerful means of controlling access, and I think they provide just the solution you need here.  However, I don't think [font=courier]nobody:nogroup[/font] is quite what you need.  Set up a different, new user:group combo, named simply [font=courier]shared:shared[/font].  This user:group combo doesn't exist on a fresh Ubuntu install, so it shouldn't collide with any other extant settings.  We can create it simply enough by doing this:
```
sudo adduser shared --no-create-home
```

Now change ownership of [font=courier]/home/shared[/font] and everything in it by running:
```
sudo chown -R shared:shared /home/shared
```

However, you'll still run into the problem you had before: user "accounts" still has no permissions to do anything to the [font=courier]/home/shared[/font] folder.  That's easy enough to fix, though -- we just add user "accounts" to the "shared" group, using the [font=courier]usermod[/font] command (see [font=courier]man usermod[/font] for details):
```
sudo usermod -aG shared accounts
```

User "accounts" should now be able to do anything to the [font=courier]/home/shared[/font] directory that is allowed by the group permissions (set via [font=courier]chmod[/font], in your case "7" or read/write/execute).  Meanwhile, user "shared" can still only do anything to the [font=courier]/home/AccountsShare[/font] folder that is allowed by the "other" permissions (in your case "5" or read/execute).  From the use case you describe, you should change this now to prevent "shared" users from being able to read "accounts" files and directories:
```
sudo chmod -R 700 /home/AccountsShare
```

This sets it so user "accounts" can read/write/execute, and no one else can do anything (except for root, of course).  

You've already got group read/write/execute permissions set on your [font=courier]/home/shared[/font] directory.  This is great -- user "accounts" is part of group "shared", and so will be able to do whatever is needed in that directory.  There's one rub, though!  Any files or directories created by "accounts", even within [font=courier]/home/shared[/font], will still belong *just* to the "accounts:accounts" user:group combo, meaning that no one else will be able to access them.  The trick here is to set what's known as the [font=courier]setgid[/font] bit on the directory and all subdirectories.  This is a Unixy filesystem setting that means that any files or directories created within such a directory will have the group ID (GID) set to be the same as the directory owner.  So in this case anything user "accounts" creates within [font=courier]/home/shared[/font] will have the owner groupname set to "shared", giving user "shared" access (since user "shared" is part of the "shared" group).  We assign the [font=courier]setgid[/font] bit like this.  The "2" in front is the key.  
```
sudo chmod 2777 /home/shared
```
If instead you wanted to use the [font=courier]setuid[/font] bit, which sets any new file/directory owner username to the the owner of the folder, you'd change that "2" into a "4".  

If there are any subdirectories within [font=courier]/home/shared[/font], we also need to assign [font=courier]setgid[/font] for them as well.  Rather than manually going through and typing [font=courier]chmod ...[/font] for each one, type in the following command.  It looks ugly, but basically it goes through [font=courier]/home/shared[/font] and sets the permissions just for directories, and *not* for files.  (Any executables with the [font=courier]setgid[/font] bit run with the owning group's permissions, which can in some cases pose a security risk -- so we just use [font=courier]setgid[/font] on *directories* to manage file and directory creation permissions.)  (Below code courtesy [Geek Pit](http://blog.unixlore.net/2007/11/excursions-with-find-xargs-and-perl.html).  Good explanation there if you're interested.)
```
find /home/shared/. -type d -print0 | sudo xargs -0 chmod 2777
```

[[color=gray]NB: At this point, I'd also recommend changing the "other" permissions for the [font=courier]/home/shared[/font] directory, as you no longer need it to be accessible to just anybody:
```
find /home/shared/. -type d -print0 | sudo xargs -0 chmod 2770
```
This way only folks logging in with the user or group name "shared" can access the directory.[/color]]

Excellent!  Your server-side file permissions should be all set up.  Anytime user "shared" logs in (either via Samba or directly via ssh or at the server itself), they'll only be able to access [font=courier]/home/shared[/font], having full read/write/execute permissions.  They **won't** be able to access [font=courier]/home/AccountsShare[/font].  However, any time user "accounts" logs in, they **will** be able to access **both** [font=courier]/home/AccountsShare[/font] and [font=courier]/home/shared[/font], and anything they create in [font=courier]/home/shared[/font] will *also* be readable/writable/executable by user "shared".  

*** *Samba Passwords*

Once all the server-side file permissions are set up, you need to make sure that Samba passwords are properly configured.  You'll need to add the following to the [global] section of your [font=courier]/etc/samba/smb.conf[/font] file, ideally right under [font=courier]security = user[/font].  This will give you a null password setup, meaning that anyone with the right username can log in via Samba without supplying a password.
```
   null passwords = yes
```

And since we've set up file permissions as we want, we no longer need any "guest" access specifications, so remove the following lines:
```
[global]
   guest account = nobody
   map to guest = bad user

[accounts]
   guest ok = no
   public = no

[Documents]
   guest ok = yes
   public = yes
```

Restart Samba:
```
sudo /etc/init.d/samba restart
```

Now make sure Samba passwords are properly entered for your two Samba user accounts.  Note that things work out a bit differently for users that have blank Windows passwords (a terrible idea, but some folks still seem to do this).  From [hardfolding.com](http://www.hardfolding.com/index.php?go=3&gtype=1&id=11&show=1):
> If you want a blank password, use the n (as in null) argument like this:
```
sudo smbpasswd -an USERNAME
```

Note that if you use null passwords, your smb.conf should have the following under the [global] section:
null passwords = yes

Many people have blank Windows passwords, so they don't have to type them when they log on. This tends to cause trouble with Samba, as a Windows 'blank' password is NOT equal to a Samba null password. If you must use a blank password, set the Samba password like this:
```
sudo smbpasswd -a USERNAME
```

Samba will ask you for the password twice, just press enter each time.

At the end of all this, your smb.conf file should look something like this:
```
[global]
workgroup = WORKGROUP
interfaces = lo eth0
bind interfaces only = true
# local master = yes      <-- defaults to "yes"
# guest account = nobody  <-- not needed anymore with proper filesystem perms in place
# map to guest = bad user <-- not needed anymore with proper filesystem perms in place
security = user
username map = /etc/samba/smbusers # <-- newly added
null passwords = yes # <-- newly added

[accounts]
path = /home/AccountsShare
# guest ok = no   <-- defaults to "no"
# user = accounts <-- not needed anymore with proper filesystem perms in place
# public = no     <-- same as saying "guest = no", defaults to "no"
browseable = no
# read only = no  <-- same as saying "writeable = yes"
writeable = yes   # Let's use this for sake of consistency

[Documents]
# browseable = yes <--
# browsable = yes  <-- These both do the same thing.  Default is "yes"
path = /home/shared
# public = yes     <-- not needed anymore, same as saying "guest = ok"
writeable = yes
# guest ok = yes   <-- not needed anymore with proper filesystem perms in place
```

Restart Samba:
```
sudo /etc/init.d/samba restart
```


Now try logging in from Windows as a couple different users and make sure logins and permissions all work as expected.  Create a few files and directories from each account and check to make sure that access from the other account meets your requirements.  Feel free to delete the commented lines from your [font=courier]smb.conf[/font] file (lines beginning with "#") once you've confirmed that all is working.  

---------------

The only thing I'm fuzzy on here is the smbpasswd configuration, as I've never tried to set up a no-password login scenario.  Try this out and let us know if it's working for you.  

Happy sharing,

Eirikr

---

### Post by IainPurdie on 2008-02-29
Guys - wow! Thanks to you both!

Before I wade in (had a good read, but want to clarify a detail or two):

The username mapping sounds good, but I think has a small problem. Currently no login details need to be requested/sent for anyone to get into the "shared" share. As far as anyone's concerned, it's wide open. I doesn't care what their Windows usernames are. Thing is, I don't know them all either which makes it difficult to build up the mapping table! The additional problem is that I'm setting this system up and then leaving in a couple of months. Should any of the staff (and therefore usernames) change once I'm gone, I can't expect anyone to know to update the mapping table.

At present it seems that people connect as "nobody" - would it work to map "nobody" to the new "shared" user? Or is that using two solutions to solve one problem?

The ones I'd like to log in as "accounts" should all be asked for a login each time they create a fresh connection (i.e. after local machine reboot). Ideally, SAMBA should just ask for login credentials to which they respond with the username "accounts" and the password set in  smbpasswd (or configured to the user within Ubuntu? I'm not 100% certain how these map). Again, this covers any issues with people coming and going and me not being here to update the mapping table.

So essentially, two generic logins:

"shared" for everyone who connects - which does not ask for a username or password. If you try to connect to the "shared" share it just lets you on. Completely insecure but easy for the users.

"accounts" for which a password is required and asked for at each new connection. Only user allowed to access the "AccountsShare" share. Also needs to access "shared" with full rights (but the latter half of the solution above should resolve this - thank you!)

Before I go all "bull in a china shop" will the above achieve this?

Again, thanks to you both for the replies - Eirikr in particular!

---

### Post by Eiríkr on 2008-02-29
Should be possible to have folks logging in w/o any credentials (username / password) mapped to "guest" (i.e. nobody, or whatever else you set up smb.conf to map such users to), but to still have the option to provide the accounts username and password if you have them.  I'll look at that later and see what I can find (gotta run now to teach a class :)).

Cheers,

Eiríkr

---

### Post by IainPurdie on 2008-02-29
No worries, Eirikr - I'm off home for the night. Another 13+hour shift is one more than my body can take! I've got the "shared" working very well now - I just don't want to change too much in the .conf that I screw *that* one up trying to fix the "accounts" one :)

---

### Post by Eiríkr on 2008-03-03
Iain --

One possible problem has occurred to me for this no-mapping setup -- there's no secure way to demote an "accounts" user to a "guest" user.  If this would never be needed, then fine; otherwise, you might be in a bit of a pickle when it comes to passing on the reins to the next person to take your post.  

I'm afraid I'm still up to my eyeballs in work, so I can't take the time just yet to set up a similar config on my SMB server.  That said, the smb.conf man page (also available as a somewhat-more-readable html page [here]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")) does suggest that what you describe should be possible.  Have a look at the [section about validation]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#VALIDATIONSECT") for what appear to be some promising hints.

Cheers,

Eiríkr

---

### Post by IainPurdie on 2008-03-03
Once again, Eirikr - thank you! I'll check out the man pages a little more thoroughly. Got the "unprotected" share working a treat now. The staff are over the moon at the lack of "too many users are connected to this resource - please try again later" messages that the old XP "server" used to pop up.

For some reason I can't get onto the Accounts share at all right now, even though I know the password. Strange. Ah well, nothing I can't completely strip and work more on! *FIXED*

OK, seem to be getting *somewhere*...

I've run the "find ... | xargs ..." command to sort out the group permissions. Whenever I create a file anywhere within Shared and it's subdirs, I now have the group set to "nogroup", which is great. It'd be nice if the user could also be set to "nobody" but I don't think this is possible. Anyway, not an issue as the group permissions take precedence, giving the effect desired. Only...

Problem. When creating anything new (as the anonymous user or as "accounts" via Windows Explorer through Samba), the file is created with 744 permissions i.e. owner has full privileges while group and other have read-only. Unless I create the file while logged onto the terminal as "admin" in which case it's creating them with 644 privileges. Hum. I'd assume there's a setting somewhere for default file creation settings? Maybe in one of the .rc files? I've not manually set the "umask" anywhere and my vague memory of UNIX classes at uni tell me this may be related?

---

### Post by Iowan on 2008-03-03
I'm afraid I don't have the details, but one option for your **accounts** share is to build a group which has read/writes to the share, then include the "accountants" in that group.  I don't remember whether you've had any luck logging on as a user yet.

---

### Post by IainPurdie on 2008-03-05
I think I cracked it, potentially using something akin to a sledgehammer to do it...

There are a few commands that can be put into the smb.conf file which pretty much solved things. As I said elsewhere, security on the "shared" share is completely irrelevant so I've left the thing basically wide open. If you want to use this solution for your own ends, adapt as needed.

The lines I added to the [Documents] (i.e. the wide open share) section of the smb.conf file are as follows:

create mask = 2777
directory mask = 2777
force user = nobody
force group = nogroup

Essentially, it means that *any* files or folders created by *any* user within the share will have permissions set to 2777 and be assigned to nobody:nogroup.

Overkill, perhaps, but it does give the results required. If I do get the time, I would prefer to operate things a little more "correctly" with users logging in on their PCs to a server environment with proper security and groups. But for the meantime, this certainly seems to be doing the job.

Again, thanks to all the respondants for your time and help! I've picked up some useful hints from this which I will try to keep tucked away for future use!

---

### Post by Eiríkr on 2008-03-05
Do let us know if you ever figure out a good way of controlling access to the Accounts section without keeping any track of users.  I'm still baffled as to whether there's any way of doing it that would allow for the removal of anyone from the group; the one possible way I can think of for setting it up without any user tracking would mean that *anyone* who knows the password would be able to access it, and (in my limited experience with corporate IT) that information usually leaks out after a while, at least a little bit.  I've looked through the smb.conf man page for hints, and the best I could find was in [the bit about variable substitutions]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#id2479780"), where there's mention of group names.  However, I've never been able to get the variables to work as expected when I've tried to double-check their values, and besides, I strongly suspect they indicate the Linux side of things anyway, and would likely not be useful for trying to control access by means of Windows group membership...

Anyway, good luck, and let us know what you find.  :)

Cheers,

Eiríkr

---

### Post by IainPurdie on 2008-03-05
See above - it seems to work. I know what you mean about passwords "leaking". I've had a nightmare with the handful of people I reluctantly gave Windows admin passwords to (old Win2000 machines - they couldn't put USB sticks in without installing them via Admin!). The last PC I remotely checked had Google Earth and a pornographic desktop... GRR.

I'm about to add an FTP server to the machine which will require adding about 30 users. They need to access only their own directories remotely to transfer a couple of files each week, while a couple of people here need to be able to access *all* the directories to put the files there in the first place.

So I'm off to mess with proftpd.conf and start this mess all over again ;)

---

### Post by sam0t on 2008-03-07
This thread fits my problem quite well so I add my questions here.

I have used basicly the same smb.conf as Eiríkr posted last and made changes to folders as he suggested, but I have a login trouble. Basicly whenever I try to log on to my samba file server, it does not prompt the login screen where you type your user name and password.

I can access Samba share folder if I use a Windows machine with a username and password same as in smbpasswd file, the windows machine logs into samba share folder automaticly. If I disable the user name, which is the same as Windows machines U/P, I get an error :(

The problem short, I would like Samba to prompt user/password everytime a user tries to access the server. All the help is much appriciated.

My smb.conf:

> [global]

netbios name = sambaserver
workgroup = WORKGROUP
interfaces = lo eth1
bind interfaces only = true
security = user
username map = /etc/samba/smbusers 


[share]

path = /home/share
writable = yes
browseable = no

---

### Post by Iowan on 2008-03-07
My Samba server requires login information the first time I try to access it, but remembers for the duration of the session.  You want a login prompt each time you access a share?
The [section on verification]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#VALIDATIONSECT") link in Eiríkr's post (#9) has some useful information about how Samba "verifies".
#4 *If the client has previously validated a username/password pair with the server and the client has passed the validation token, that username is used.*

---

### Post by Eiríkr on 2008-03-07
> **sam0t said:**
> ... but I have a login trouble. Basicly whenever I try to log on to my samba file server, it does not prompt the login screen where you type your user name and password.

Do you mean you *never* see the login prompt?  Or did you see it once, then never again?  

On my setup, I've got the Windows username mapped in my mapping file.  It's been so long since I mapped my drives in Windows (to Samba shares), that I cannot remember if I initially had to plug in my username and password, but after mapping, as Iowan notes, Windows has recorded the authentication info and does not prompt me anymore (the drives just show up automatically on login into my Windows machine).  

> **sam0t said:**
> I can access Samba share folder if I use a Windows machine with a username and password same as in smbpasswd file, the windows machine logs into samba share folder automaticly. If I disable the user name, which is the same as Windows machines U/P, I get an error :(

How do you mean "disable the user name"?  If it's disabled (on either the Windows or Ubuntu side), it would seem pretty obvious that trying to use it would produce an error...?  Which makes me think perhaps I'm not fully understanding you here.

> **sam0t said:**
> The problem short, I would like Samba to prompt user/password everytime a user tries to access the server. All the help is much appriciated.

This is something on the Windows side, in terms of how it stores authentication information.  I don't think there are any Samba settings that could change how this happens, and unfortunately I'm not familiar enough with the finer points of Windows configuration to help on that end.  Anyone else have any ideas?

Cheers,

Eiríkr

---

### Post by sam0t on 2008-03-08
> **Eiríkr said:**
> Do you mean you *never* see the login prompt?  Or did you see it once, then never again?  

Yes I have gotten the prompt once or twice, I entered a correct login information and everything worked smoothly. Problem being that I have not seen that login screen since. I have the system set up at my work, I shall try to change my Windows computers username and see if it changes anything.

> How do you mean "disable the user name"?  If it's disabled (on either the Windows or Ubuntu side), it would seem pretty obvious that trying to use it would produce an error...?  Which makes me think perhaps I'm not fully understanding you here.

I have disabled my user by doing a following command: sudo smbpasswd -d <username>

Sorry for my bad description, I´ll try to explain it better. I have few different users on my Ubuntu, I have created a user accounts for them with adduser command and added them to Samba with smbpasswd -a command. Also I have added all the users to the share group, share is the name of the user/group that has its directory shared with smb.

Now lets say I have 3 users in my system: test1 , test2 , test3 and all of em have a password "password".  

Now I have a Windows machine with U:P test1 : password. With this I can log in to my Samba file server automaticly, it does not prompt any login screen. This is fine and dandy since I read Windows tries to access Samba server with its default user/password combination. 

What Iam after is that, when I disable that test1 account with smbpasswd -d test1, I would still like to access Samba server with the remaining test2 and test3 accounts, but cannot, because the login screen never pops up when I try to access Samba, just an error. So it seems that Samba only lets Windows machines access which have username/password that match an entry in the the smbpasswd file. I would like a login prompt window everytime that a Windows machine tries to access Samba.

> This is something on the Windows side, in terms of how it stores authentication information.  I don't think there are any Samba settings that could change how this happens, and unfortunately I'm not familiar enough with the finer points of Windows configuration to help on that end.  Anyone else have any ideas?
Cheers,
Eiríkr


Hopefully somebody can shed some ligh on to this issue, thank you for your effort, this post has been very helpfull in many ways :)

ps. Could all of this be due to the fact that I have only one directory shared? If I would have couple directories, then the Samba would be forced to ask "who" is trying to login, because it needs to know which directory it gives access? .. Bear with me Iam a total Ubuntu newbie :)

---

### Post by Iowan on 2008-03-08
Your explanation sheds much light... Besides Samba accounts - the users (test2, test3...) also have accounts on the Ubuntu box? (Perhaps they must to make smbpasswd work??)

I'll just edit this in - instead of adding another post... Yes, I forgot about sam0t mentioning he had created all the users with adduser - I presume they got password set, too...

---

### Post by Eiríkr on 2008-03-08
Excellent point to bring up.  From the smbpasswd man page:
> **OPTIONS**
**-a**
This option specifies that the username following should be added  to  the  local  smbpasswd  file,  with  the  new  password typed (type <Enter> for the old password). This option is ignored if the username following already exists in the smbpasswd file and it is  treated  like a regular change password command. **Note that the default passdb backends  require  the  user  to  already  exist  in  the  system  password  file  (usually /etc/passwd), else the request to add the user will fail.**

However, sam0t notes:
> Sorry for my bad description, I´ll try to explain it better. I have few different users on my Ubuntu, I have created a user accounts for them with adduser command and added them to Samba with smbpasswd -a command. Also I have added all the users to the share group, share is the name of the user/group that has its directory shared with smb.

Now lets say I have 3 users in my system: test1 , test2 , test3 and all of em have a password "password". 

sam0t, are we correct in thinking the "adduser" usernames are indeed these "test1" - "test3" usernames?

Cheers,

Eiríkr

---

### Post by sam0t on 2008-03-09
I shall double check the /etc/passwd file to make sure I have created the users. I´ll report back tomorrow when I got the chance to mess around with my Ubuntu system. Iam 99% certain that they excist because otherwise smbpasswd -a command returns an error.

I shall also change my Windows machines default U:P to something else than the test1 : password. I have a slight feeling this causes confusion to the login somehow, as Windows tries to log on to Samba first with its default U:P combination. Thanks again from your help!

ps. I found out the hard way, that the below quote is true. I followed a Samba guide in which there was only one user account and a single shared directory in Ubuntu. First couple hours went into googleing why the smbpasswd -a command did not work, reasong being that I had not added the users needed with adduser command. Also if you guys have any good Samba tutorials/guides in your bookmarks feel free to share, this topic has been most helpfull but no harm in more info. Ofcourse the MAN command with Ubuntu is very powerfull, just that sometimes it seems bit overwhelming to a n00bie :) 

> OPTIONS
-a
This option specifies that the username following should be added to the local smbpasswd file, with the new password typed (type <Enter> for the old password). This option is ignored if the username following already exists in the smbpasswd file and it is treated like a regular change password command. Note that the default passdb backends require the user to already exist in the system password file (usually /etc/passwd), else the request to add the user will fail.

---

### Post by Eiríkr on 2008-03-09
> Ofcourse the MAN command with Ubuntu is very powerfull, just that sometimes it seems bit overwhelming to a n00bie :)

Boy howdy.  There's just **so much** info to absorb when you're first testing the waters, it can be quite overwhelming.  I still remember my first experiences with RedHat 7 (I think), and wondering where the heck the C: drive had gotten to.  :shock: :D

Good luck, have fun, and welcome to the other side of the fence!  \\:D/

---

### Post by sam0t on 2008-03-10
Ok , I think I got the things under "control" :D 

Where to start. The Samba file server seems to work just fine, the problem seems to be the Windows side and its weird login procedure. I'll tell step by step what I did.

Double checked that the users are present in Ubuntu, both in /etc/passwd and in /etc/samba/smbpasswd. After this I disabled the test1 user in Ubuntu with passwd -d command, tried to log into samba with test1 account under Windows and naturally I got an error that the user account is disabled. This is correct, but weird, why does the Windows prompt the logon window :/ ?

After that I created a random user account in Windows and tried to access Samba, I get a login prompt. 

To sum it up, as I understand it:

1. Windows always tries to access Samba with its own U:P combination automaticly.. If that exact U:P combination does exist in Samba smbpasswd file, it connects automaticly to the share folder. No login prompts, just automatic connection.

2. If the account is disabled in Samba smbpasswd (smbpasswd -d user), the Windows just pops up an error "user account disabled". 

3. Thirdly, when you connect Samba with an Windows account that does not excist in smbpasswd it prompts an login screen.

4. All this brain work because Windows tries automaticly access file server with its logged U:P and does not act logically when that login fails :p

So indeed the problem seems to be on Windows side, must start searching the net for clues on how to change Windows login procedure. Crude tactic is just to force Windows to log on to the network drive with another user name. Not as neat, but guess I can live with it :) 

edit: 

Not so fast it seems. Somehing is still fishy with one of the users, this time the share folders owner. This is is set up as share folders owner and everything set up as with other accounts. Even if I enable this account with smbpasswd -e , Windows insists that the share account is disabled, giving error "user account is disabled". Is there something Iam not seeing :/

---

### Post by Eiríkr on 2008-03-10
I think you've stumbled across the same problem being discussed over in [thread=719541]Thread 719541[/thread] -- basically, it seems that once you log onto a Samba share in Windows, that Windows user account saves the Samba login information, and automatically uses that, and *WILL NOT* let you change it.  Or at least we haven't been able to figure out how.  So once you logged onto the Samba "test1" account from the Windows "test1" account, the Windows "test1" account is stuck.  However, it doesn't matter *what* the Windows username is; once you use it to log into any Samba username, that Samba username gets stuck on the Windows side.  You could have Windows username "rutabaga" and Samba username "yorkshirepudding", and once you log into "yorkshirepudding" from "rutabaga", "rutabaga" will be stuck on "yorkshirepudding".  The end.  At least, until someone can discover how to force Windows to allow the user to input a different Samba username.  :-(

Do you think this might be what's happening with your share folder?

Eiríkr

---

### Post by IainPurdie on 2008-03-11
Sounds like the problem I was having. Fortunately I've been testing with the actual usernames I intended to use so my PC is "stuck" as "accounts" which suits me.

I can think of two possible solutions: 

1) connecting using the "username : password@\\share" form

2) search the Windows registry for the username you picked and see where it stores it (assuming it's stored in the registry). You can then delete the entry which should force it to ask you for a password the next time.

Both untested theories!

---

### Post by Eiríkr on 2008-03-11
KennedyM hunted down how Windows stores these settings.  Have a look at his new HOWTO over at [thread=720889]this thread[/thread], where he describes how to remove the relevant data and *force* Windows to prompt for authentication, and see if that helps you at all.  

Cheers,

Eiríkr

---

### Post by sam0t on 2008-03-12
Thanks for all the good links, really sheds light upon the issue! 

My only problem left is that my main account named share, which is according to Windows, disabled. This is the account I used to share the samba share folder, below the some facts from CLI:

drwxrwx---  2 share share

Everytime I try to connect samba server with username share, Windows informs that the account is disabled.

I have checked multiple times that the account share is indeed enabled and I have deleted/recreated that particular account in smbpasswd, still no go. Iam pretty clueless about the situation, I have no idea why Samba marks my account share as disabled even if I have enabled it :/

Is there some thing that must be taken account? This is not the end of the world since other accounts work just fine, even with Windows logon oddities, just curious what could be causing the problem.

---

### Post by Eiríkr on 2008-03-12
Could it be that you tried accessing "share" once from Windows when "share" *was* disabled?  Then maybe Windows (in it's never-ending quest to completely second-guess the user) promptly stored the information that the account was disabled, and now won't even check?  It might be worth it to follow KennedyM's HOWTO to wipe out the Windows connection cache information; either that, or set up a different Samba username...?

Cheers,

Eiríkr

---

### Post by sam0t on 2008-03-13
Most excelent suggestion Enkir, I shall try that! Now that I recall it, the account name share was the first one that I started messing around with, only later came the test1 etc, so this could be it. I shall report you back later.

Another question while we are at it. Is it possible just to connect Samba server IP , get the login prompt and then Samba directs the user to the right share folder according to smbuser files list/chart ? 

In example: Currently I directly connect the share folders like \\192.168.1.154\share and so on. What Iam after is like connect \\192.168.1.154 , get the login prompt, login and then be in the correct share folder? Or is the point just to connect some shared folder and Samba then checks the smbusers file and directs the login to the right folder ? Dunno if this is more Windows guestion than Samba, bear with me :)

Just tried to connect share folder with guest account and ended up in share folder, not in share1 as I would have liked :/

smbusers:
```

share=share
test=share
test1=share
guest=share1

```

smb.conf
```

[global]
netbios name = sambaserver
workgroup = WORKGROUP
interfaces = lo eth1
bind interfaces only = true
security = user
username map = /etc/samba/smbusers


[share]
path = /home/share
writable = yes
browseable = yes

[share1]
path = /home/share1
writable = yes
browseable = yes

```

---

### Post by Eiríkr on 2008-03-13
Judging from the relevant entries in the man page, I think the guest user definition should actually be a setting in the [global] section, as described [here](http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT).  As such, I'm not sure if using a "guest" username might conflict with whatever defaults these settings might go to, and produce weird behavior.  But hey, if you're not running into trouble with that, then I guess you're good to go.  :)

As far as how to define automagically connecting home shares, there is indeed a Samba mechanism for that.  Have a look [here](http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#HOMESECT) at the description of the [homes] section, as that sounds like exactly what you're looking for.  

Cheers,

Eiríkr

---

### Post by sam0t on 2008-03-13
I decided to disable/remove the Guest account as Iam not looking for trouble. Guest shall now be known as visitor :D 

I shall check out the link you provided, many thanks again Eirikr!

edit:

I feel somewhat stupid now, just googled some samba stuff and it seems that XP and Vista do not handle shared folders quite the same way. Anyways my main problem remains, when Windows machine (be it XP or Vista) tries to connect Samba server with username "share", I always get "account disabled" message. No biggie its not the end of the world as all the other user accounts work.

---

### Post by IainPurdie on 2008-03-15
As an aside, I came across an issue that may cause some of the problems we've encountered above but that is nothing to do with Samba as such.

My office PC died 2 nights ago so I rebuilt it, installing all the usual apps...then found that I couldn't connect to the "guest" share - the one that's wide open for all users without requiring a login. It was asking me for a login. Same when I tried to access the share *with* security on - the password wasn't accepted.

Solution - ZoneAlarm had my local area interface configured as "Internet", not "Trusted". A quick change and it all went back to normal. A very bizarre symptom!

---

### Post by sam0t on 2008-03-17
It seems there is rather old version ( 3.0.26a ) available in synaptics for ubuntu. I checked out Sambas home page and they have released 3.0.28a which has some Vista related fixes. 

Iam keen on upgrading samba but wanted to ask for the smartest way of doing this :/ ?

edit: 

I realize that this is probably right topic for all this, and been considering to drop the whole issue. Clearly its a Vista thing as all the XP clients can connect my Samba shares and it works out smoothly. Does anybody got a clue when new Samba updates will be available through synaptics ? 

I googled abit and I guess it could be possible to compile the Samba source code and make an install through that way, but I think my skills do not stretch that far, especially if it needs messing with dependencies and so on :/

---

### Post by sam0t on 2008-03-26
Just wanted everybody, who has been helping me, to know that it was indeed the Vista at fault. I did not need to install latest version of Samba to get things working, I just reinstalled Vista on my test machine and everything works fine and dandy now :)

---

### Post by Eiríkr on 2008-03-26
Yay, sam0t!  :D  

Thanks too for letting us know what you did to fix the problem.  Hopefully that might come in handy for someone else stuck in the same situation.  :-o

Cheers,

Eiríkr

---

### Post by IainPurdie on 2008-03-26
Hehe - should have known it would be Vista's fault! Vista = evil ;)

---

### Post by sam0t on 2008-03-28
Indeed Vista is evil :D 

In fact there seems to be some Windows update that messes up the system. After reinstall I could see Samba server just fine in my little test workgroup, but after some updates to Vista, the Samba server vanished from Vistas network :/

I read that Vista and Sambas earlier versions had some incompatibility issue regarding the Vista NTLMv2 authentication, but that is supposed to be fixed in Samba 3, so thats not the case. Anyways Iam too frustrated to battle with Vista, Iam just glad my XP machines can see/access Samba shares ok :)

---

### Post by IainPurdie on 2008-03-28
Add another reason to the long list of why you should never install Vista *sigh*. I'm not going to "bash" MS. Frankly, I think XP is a great OS. A little buggy - it's bound to be. It's huge. Somewhat insecure - it's bound to be. It's got a huge user base so it's a target.

But it works, it's flexible, it's got a massive amount of software available for it. On the whole it's pretty stable. It's fairly fast if you take care of it.

And then there's Vista. Oh dear me. It even makes Windows ME look like a worthwhile release.

Anyway, back on topic. I'm making use of the link elsewhere on the page to "force" Windows to forget login parameters for Samba shares. I need it to do this for security on one of them and it seems to be working a treat. User logs onto public share - no password required. User logs onto secure share with Account data on and it requests a password.

---

