---
title: "Unable to see network folders"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-05-23
I have a clean install of Lucid 10.04 on two machines (call them Computer A and Computer B) connected to the same local network.

On each machine...

[LIST]
[*]I created a folder.
[*]Right-click > Sharing options > Share this folder.
[*]The machine prompted me to install some package, which I allowed it to do.
[*]I clicked "Allow others to create and delete files in this folder" and "Guest access", and restarted the computer.
[/LIST]
 But, when I go to Places > Network, I have problems.

**Computer A:**

I see both my machine and the other machine (and a "Windows Network", even though I don't have Windows). But when I click on the other machine, after a minute or so it says, "Unable to mount location. Failed to retrieve share list from server."

**Computer B:**

I see only the "Windows Network" and nothing else. Opening that leads to WORKGROUP, which in turn leads to the same error message as the Computer A.

Before I installed Lucid, one was Hardy and the other Jaunty, and both could see each other without any problem.

What can I do to fix this?

---

### Post by new_tolinux on 2010-05-23
The most easy way to do that is using samba.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by CharlesA on 2010-05-23
It would help to know what package was installed. I believe that the "Windows Network" icon is always where, weather you have a Windows network in place or not.

---

### Post by Paddy Landau on 2010-05-24
> **new_tolinux said:**
> The most easy way to do that is using samba.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
My goodness, that is so complex! I will attempt that later.

I don't need a Windows share, though. I use only Ubuntu.

---

### Post by new_tolinux on 2010-05-24
> **Paddy Landau said:**
> My goodness, that is so complex! I will attempt that later.

I don't need a Windows share, though. I use only Ubuntu.
You'll probably do want a Windows share. Not because it's a Windows share, but it's a lot easier to work with Samba (and Windows-type shares).

---

### Post by Paddy Landau on 2010-05-24
> **CharlesA said:**
> It would help to know what package was installed. I believe that the "Windows Network" icon is always where, weather you have a Windows network in place or not.
I've just tried on Computer C, and you're right, the Windows Network icon already is there.

On Computer C:

[LIST]
[*]I did right-click > Sharing Options > Share this folder.
[*]The message said, "Sharing service is not installed. You need to install the Windows networks sharing service in order to share your folders."
[*]I pressed the "Install Service" button.
[/LIST]
I have no clue what it installed. While installing, I pressed the "Details" button, but things went by fast. I did see the word "Samba", but looking on Ubuntu Software Centre, I notice that Samba is not installed.

I'm also finding on the three computers that when I try to access the network, about half the time it gives an error message:
> Could not display "network:///".
Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.If I restart the machine, then it works again. Not always, but mostly.

But, I still cannot connect to the other machines. Do I need to install Samba?

This is really a shame, as I would have expected better from Ubuntu.

---

### Post by Paddy Landau on 2010-05-24
> **new_tolinux said:**
> You'll probably do want a Windows share. Not because it's a Windows share, but it's a lot easier to work with Samba (and Windows-type shares).
Thanks, I'll take a look at Samba now.

---

### Post by Paddy Landau on 2010-05-24
So far...

I installed Samba on both Computer A and Computer B.

On each computer, I used System > Administration > Samba to change the Workgroup name (both computers the same), to add the folder to be shared and to make it both visible and writeable, and to allow access to everyone.

I've fiddled with the file smb.conf as described in the Samba link given previously.

All to no avail.

I find it hard to credit that Canonical should have made it so incredibly hard to share folders on the same network, even between two Ubuntu Lucid machines!

How on earth is a beginner supposed to get his head around this, if I can't?

Anyway, rant over. I'd really appreciate some help, please.

---

### Post by new_tolinux on 2010-05-24
I prefer to do it only partly through terminal and partly with the graphical configuration.
I haven't got Lucid installed and my Linux-machine isn't in English, so things can differ a bit.

First the "server" (the machine which is supposed to share folders):
Start with installing samba and system-config-samba from terminal:
```
sudo apt-get install samba system-config-samba
```After that go to user/group-management (Tools-menu) and make sure the user you need to connect to the samba is a member of the Samba-group.
Then open the samba-settings (can be done from the menu, also from terminal: [FONT=Courier New]gksudo system-config-samba[/FONT] ). Create a samba username and password for that user.
Go back to the main samba settings page. Create a share and assign the share at least to the user you just set up.
After that, you'll probably need to grant sufficient rights for the linux-user to the shared folder. It can be done by chmod/chown (from terminal) or from Nautilus ( [FONT=Courier New]gksudo nautilus[/FONT] from terminal).

After that, go to the "client" machine (the one which should be able to access the "server"). You should be able to connect to the previous made share from the menu.

---

### Post by fatality_uk on 2010-05-24
Hi Paddy, are you wanting a server client model, both PC's to act as "servers" if you like providing access to all other PC's on the network or just a peer to peer connection between these two machines?

---

### Post by Paddy Landau on 2010-05-24
> **fatality_uk said:**
> Hi Paddy, are you wanting a server client model, both PC's to act as "servers" if you like providing access to all other PC's on the network or just a peer to peer connection between these two machines?
I want **any user** on **any machine** (within the network) to be able to access the shared folders. The intention is to make it easy to transfer files between any two machines.

So, all machines will be "servers".

Perhaps I should have said that in my first post.

---

### Post by Paddy Landau on 2010-05-24
> **new_tolinux said:**
> Start with installing samba and system-config-samba from terminal
OK, they were already installed (probably from what I did earlier).

> **new_tolinux said:**
> After that go to user/group-management (Tools-menu) and make sure the user you need to connect to the samba is a member of the Samba-group.
I imagine that you meant System > Administration > Users and Groups. All users on the machines (including *nobody*) already belong to the *sambashare* user (there is no *samba* user).

> **new_tolinux said:**
> Then open the samba-settings (can be done from the menu, also from terminal: [FONT=Courier New]gksudo system-config-samba[/FONT] ). Create a samba username and password for that user.
Here I'm confused. I don't see an option to create a Samba username.

> **new_tolinux said:**
> Go back to the main samba settings page. Create a share and assign the share at least to the user you just set up.
I had marked the share as "Writable", "Visible", with "Allow access to everyone".

> **new_tolinux said:**
> After that, you'll probably need to grant sufficient rights for the linux-user to the shared folder.
I've already made it read-write access to everyone ([FONT=Courier New]chmod a+rwx[/FONT]).

So, thanks for the ideas, but sadly I'm no further forward.

---

### Post by new_tolinux on 2010-05-24
> **Paddy Landau said:**
> OK, they were already installed (probably from what I did earlier).Ok. Yet I've got gnome back up on my server, so at least I'm not doing everything just by memory. However it's Dutch and 9.10, so like I said names can slightly differ although I tried to translate them properly.
> **Paddy Landau said:**
>  I imagine that you meant System > Administration > Users and Groups. All users on the machines (including *nobody*) already belong to the *sambashare* user (there is no *samba* user).
I do. The only user that has to be assigned there is the one you'll want to have access to the shares. If more than one user needs access, you can assign as many users as is useful to that group.
> **Paddy Landau said:**
> Here I'm confused. I don't see an option to create a Samba username.
I guess the menu you're looking for is called "Preferences" and the option "Samba-users". There you'll see a button with some text like "Add user".
You have to assign a password and username to an existing linux-user. That has be (one of) the user(s) that you assigned to the group "sambashare" before.
Username and password can be completely different from the linux-credentials, so a linux user "account" with password "password" can be given "username" as username and "mysecret" as a password.
After that close the samba-users window and click the + button at the top-left of the window where the shares are listed.
There are 2 tabs there, the first is to configure the share (name/location/settings) and the second tab displays the samba-user(s) you made before. Assign the ones that need access to that particular share.
> **Paddy Landau said:**
> I had marked the share as "Writable", "Visible", with "Allow access to everyone".

I've already made it read-write access to everyone ([FONT=Courier New]chmod a+rwx[/FONT]).
You shouldn't allow "everyone" full access, unless you really need to have everyone full access. It's a way, but the better way is to assign the users to a (new) group and then grant the necessary rights to that group (e.g. chmod -R 770 /path/to/folder will give the user+group you made owner of those files with chown full access but blocks "the rest of the world").

---

### Post by Paddy Landau on 2010-05-24
Thank you for taking such time with this.

> **new_tolinux said:**
> I do. The only user that has to be assigned there is the one you'll want to have access to the shares. If more than one user needs access, you can assign as many users as is useful to that group.
To simplify things at this stage, Computer A and Computer C both have (among others) myself as a Linux user, with the same account name and the same password. So, I'm only logging in to my account on both computers.

I've already done all the things that you suggested, except...

In the Samba users, Samba had automatically added every user on the machine. The Windows Username was the same as the Unix Username (which is fine by me). Do I have to assign a password there? I see only asterisks.

 > **new_tolinux said:**
> You shouldn't allow "everyone" full access, unless you really need to have everyone full access. It's a way, but the better way is to assign the users to a (new) group and then grant the necessary rights to that group (e.g. chmod -R 770 /path/to/folder will give the user+group you made owner of those files with chown full access but blocks "the rest of the world").
Once I have this working, I'll experiment with this. It already seems crazily complicated.

Thanks again for your time; I still don't know how to get it working.

---

### Post by new_tolinux on 2010-05-24
> **Paddy Landau said:**
> Thank you for taking such time with this.
No problem.
> **Paddy Landau said:**
>  To simplify things at this stage, Computer A and Computer C both have (among others) myself as a Linux user, with the same account name and the same password. So, I'm only logging in to my account on both computers.

I've already done all the things that you suggested, except...

In the Samba users, Samba had automatically added every user on the machine. The Windows Username was the same as the Unix Username (which is fine by me). Do I have to assign a password there? I see only asterisks.
That's a new one to me which I've never seen before.
I really don't have any clue which password is assigned, as I did look in /etc/samba/smbusers I do see the accountnames and their "samba" equivalents, but nowhere in /etc/samba/smbusers or /etc/samba/smb.conf I do see any evidence of where the passwords are stored.

> **Paddy Landau said:**
>  Once I have this working, I'll experiment with this. It already seems crazily complicated.

Thanks again for your time; I still don't know how to get it working.
Does it produce error-messages along the line?
Can you ping to the other machine?

A little bit info on that matter from your side should be more than welcome.
"Not working" is at least a bit vague.

---

### Post by Paddy Landau on 2010-05-25
> **new_tolinux said:**
> That's a new one to me which I've never seen before.
Maybe it's new to Lucid?

> **new_tolinux said:**
> I really don't have any clue which password is assigned...
I manually assigned the passwords, making them the same on both machines. Still it made no difference.

> **new_tolinux said:**
> Does it produce error-messages along the line?
No, no messages along the line. It all appears to work fine. Only when I try to connect do I get the messages that I [already posted]("http://ubuntuforums.org/showthread.php?p=9346255#post9346255").

> **new_tolinux said:**
> Can you ping to the other machine?
Good question! I hadn't thought of that.

I've just tested, and both machines successfully ping each other.

> **new_tolinux said:**
> A little bit info on that matter from your side should be more than welcome.
I wish I knew what else to tell you.

> **new_tolinux said:**
> "Not working" is at least a bit vague.
I feel that's not fair. I think I told you a lot. :(

I'm really frustrated, because this should be a simple thing. I don't recall doing any of this with Jaunty; Hardy was so long ago that I don't recall what I did. I will keep looking around, but it's crazy that I'm spending hours doing what should be a five-minute job.

Oh well. C'est la vie.

---

### Post by 3rdalbum on 2010-05-25
1. Remove all firewalls in between the computers.
2. Try accessing the machine  by IP address (in Nautilus, access smb://ip-address-goes-here)
3. Log out of Gnome on the client, and log back in, after each change on the server.

---

### Post by Paddy Landau on 2010-05-25
I've had two further thoughts.

On the network, each machine can connect to itself and see its own folder without any problem. The problem is with accessing the other machine.

I booted one of the machines into Windows. (After all, Samba is supposed to work with Windows, isn't it?)

[LIST]
[*]The Windows machine and the Ubuntu machine ping each other successfully.
[*]From Windows, I successfully connect to the Ubuntu machine, and I can create, modify and delete files on the Ubuntu machine.
[*]From Ubuntu, I can see the Windows machine, but I can't connect to it.
[/LIST]
One more thing. When I go to Places > Network, it takes nearly a minute before it displays. That isn't right, is it?

Do you suppose it could be a permissions problem?

---

### Post by michaelA1330 on 2010-05-25
dont install a package with out knowing what it is first and set your updated to security only , just a tip :p

---

### Post by Paddy Landau on 2010-05-25
> **3rdalbum said:**
> 1. Remove all firewalls in between the computers.
I wouldn't have the faintest idea how to do that, sorry. But that's probably not the problem, because (a) Windows can access the Ubuntu machine, and (b) your next point...

> **3rdalbum said:**
> 2. Try accessing the machine  by IP address (in Nautilus, access smb://ip-address-goes-here)
Gasp! Yes, it works!

So why, then, is there a such a mismatch between doing it the user-friendly way (through the named network on Nautilus) and the user-unfriendly way (finding out the IP address and typing it manually)?

Also, when I create a file, it's not created with full read-write access, so the file is not truly shared. I read somewhere (where?) about changing the default umask (I think it's called a umask) to set all new files and folders in the shared folder with full read-write access to everybody.

> **3rdalbum said:**
> 3. Log out of Gnome on the client, and log back in, after each change on the server.
Thanks for the advice; yes, I have been rebooting after each change. Fortunately Lucid takes only two minutes to reboot, unlike Windows.

---

### Post by new_tolinux on 2010-05-25
> **Paddy Landau said:**
> I feel that's not fair. I think I told you a lot. :(
It wasn't meant unfair. As I read your last post before my reply it only states "but sadly I'm no further forward."
That (to me) meant the same as "still not working". 

The part below was meant as a complete part, because you did not specify any new/other error-message in your post:
> Does it produce error-messages along the line?

A little bit info on that matter from your side should be more than  welcome.
"Not working" is at least a bit vague.
Only later I thought of ping, so I added that question. Maybe the place where I put that question was an unlucky choice.

---

### Post by Paddy Landau on 2010-05-25
> **new_tolinux said:**
> It wasn't meant unfair...
OK. I thank you and the others who have spent time on this.

We've established that [I can get it working]("http://ubuntuforums.org/showthread.php?p=9356583#post9356583"), but only if the user knows the IP address. That's not terribly user-friendly, so I wonder what I need to do to make it take that final step.

I'm wondering whether to take up [Canonical's paid-for service]("http://www.ubuntu.com/support/services/starter"), because I'm wasting far too much time on this nonsense.

---

### Post by new_tolinux on 2010-05-25
> **Paddy Landau said:**
> We've established that [I can get it working]("http://ubuntuforums.org/showthread.php?p=9356583#post9356583"), but only if the user knows the IP address. That's not terribly user-friendly, so I wonder what I need to do to make it take that final step.
That's a relatively easy step.

Although it should be possible to use the format computername.workgroup it just don't work most times (at least for me).
1 way to solve that is to edit /etc/hosts
Add a line on both computers:
```
123.456.789.012 computername
```
replace 123.456.789.012 with the IP-adress of the _other_ computer and replace computername with the name you want to assign to the other computer.

Example:
192.168.0.1 server
192.168.0.2 workstation

The name you specify doesn't need to be the same as the original computername.

To edit the specified file you can enter one of the 2 lines below in terminal:
```
gksudo gedit /etc/hosts
```
or
```
sudo nano /etc/hosts
```
Gedit is the X text-editor, where nano is the terminal text editor.

---

### Post by Paddy Landau on 2010-05-25
> **new_tolinux said:**
> Example:
192.168.0.1 server
192.168.0.2 workstation
Thanks for the idea. The problem is that the computers aren't guaranteed to keep the same IP address. The router allocates them and changes them occasionally.

I know that there must be another way, because, as I said, it used to work when I had a mix of Jaunty and Hardy.

---

### Post by new_tolinux on 2010-05-25
> **Paddy Landau said:**
> Thanks for the idea. The problem is that the computers aren't guaranteed to keep the same IP address. The router allocates them and changes them occasionally.

I know that there must be another way, because, as I said, it used to work when I had a mix of Jaunty and Hardy.
I know that it's possible with most routers to assign an IP to a specific MAC-address. That should guarantee that each computer is given it's own IP-address. The only thing to keep in mind is that (for example) your router has a DHCP-range of 192.168.0.2-192.168.0.100 that the "fixed" address should be best outside that range (for example 192.168.0.101 and .102).

I really don't know any other (working) way of using hostnames instead of IP-adresses to connect other machines.

---

### Post by Paddy Landau on 2010-05-25
> **new_tolinux said:**
> I know that it's possible with most routers to assign an IP to a specific MAC-address...
Thanks for the reply. Even so, it's not a great solution, as I have to go to each computer (I have several) and make the changes; and maintain the settings in the router; and remember to do this any time a computer is replaced or added.

I know it's possible, and by rights it should be easy.

I have contacted Canonical to find out whether a paid contract will support this question, and emails are going back-and-forth because they don't seem to know! :confused:

I'll keep this thread updated with any progress, if indeed I have any.

---

### Post by ubername on 2010-05-25
Hi Paddy

You have my sympathy. I have struggled a lot with samba, to no avail
[http://ubuntuforums.org/showthread.php?t=1341141](http://ubuntuforums.org/showthread.php?t=1341141)

During the Lucid dev cycle I had solutions which came and went and I have more or less given up for now.

I completely agree with you that all this capering about setting up samba is ridiculous if you only want to share between ubuntu computers, and fwiw it also takes my computer a long tome to open 'network'. 

Sharing your pain.

---

### Post by scrapmetal on 2010-05-25
You have my sympathy to.:(
I gave up with samba, discovered a lot of posts, but could not get it working. :confused:
Purchased a 500 Gb USB passport drive to transfer large files,
Until I have time to set up a server to do what you are trying to do.
You would think it should be simple once MAC addressees where input.
Will be watching this post, with the hope you succeed.
**All updates appreciated.**

---

### Post by sonu 1807 on 2010-05-25
May sound foolish...but there is an alternative........install iptux on both the machines..you can send messages and files to the the other machine. Don't know why the samba thing has been made so complicated :confused:.

---

### Post by cgb on 2010-05-25
Definitely sounds like a DNS issue..  Possibly a bug between Lucid and your Router talking correctly.  Unfortunately the only solution I have in mind would be basically the same as others have suggested and set a static IP and manually label the DNS..  Unless these PC's on your network are Laptops that get moved around to other networks, setting up as static IP's should be pretty straight forward and help prevent future issues..

---

### Post by Paddy Landau on 2010-05-26
> **ubername said:**
> You have my sympathy...
> **scrapmetal said:**
> You have my sympathy to.
Hmm, interesting. I think that I'll raise a bug report.

> **scrapmetal said:**
> All updates appreciated.
I most certainly will post any updates here. This is a sharing forum.

> **sonu 1807 said:**
> May sound foolish...but there is an alternative........install iptux on both the machines...
Yes, that's an idea; or Skype or any other similar package. But it really avoids the issue, doesn't it?

> **cgb said:**
> Possibly a bug between Lucid and your Router talking correctly.
You may be right. I spent even more time yesterday with Google and trying this and that, still to no avail.

I have been in touch with Canonical about the paid-for service, and I think that I'm going to go for it. A bit of a risk considering that Canonical doesn't know whether it supports this :confused:, but I can only try.

---

### Post by Paddy Landau on 2010-05-28
> **sonu 1807 said:**
> but there is an alternative........install iptux...
> **cgb said:**
> ... setting up as static IP's...
I've just realised why it's so important to get this right. My networked scanner scans directly into the shared folder. Naturally, it can't use iptux or static IP's, because it uses the Windows method.

So, now I can't scan!

I will be purchasing support from Canonical today, and I'll let you know what happens.

---

### Post by cgb on 2010-05-28
Not sure what type of Network Scanner you are using but it really shouldn't be an issue with Static IP's..  I've dealt with many different MFP's with Network Scanning and all of them worked fine in a static network, actually typically better.  Again not sure what brand of scanner but if it scans to a windows file share (SMB) you really shouldn't have any issues if setup correctly..  From what you have been saying the existing problems appear to be DNS related from the Linux PC's and your Router, this would not effect the scanner.  Although if their is a DNS issue on the scanner as well you could always setup the scan file location with the IP address instead of computer name (ex: \\IP_address\share_name)..

---

### Post by Paddy Landau on 2010-05-28
@cgb: Thanks for the comments.

I've signed up for a year's support from Canonical, because this is supposed to be a simple and basic thing. I don't have any more time to fiddle and play. I don't mind paying a little money to support the free stuff that I've had from them over the years.

This really should have "just worked". After all, before Lucid, it did work, without static IPs and all this mucking around.

I'll let you know what happens.

---

### Post by Paddy Landau on 2010-05-31
Well, I still haven't received a reply from Canonical, maybe because I signed up over the weekend and today is a public holiday in the UK.

I did find two new things, thanks to another thread.


[LIST=1]
[*]Typing [FONT=Courier New]testparm[/FONT] returns one error that I don't understand and haven't found anything meaningful (to me) when searching:
[FONT=Courier New]rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
[/FONT]Any idea whether this is something to worry about, and if so, what to do about it?
[*]Typing [FONT=Courier New]smbtree[/FONT] returns the following error when attempting to connect to the other computer:
[FONT=Courier New]cli_start_connection: failed to connect to SHARED<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
[/FONT]Again, this means nothing to me.
[/LIST]

---

### Post by Imatech64 on 2010-05-31
Hello ,
 
After many many days of searching through the different threads, I too have the same question to find an user friendly and easy graphical solution in creating a simple home network with a corresponding file sharing based on ubuntu distribution on all the PCs/laptops (no windows).
 
I do not know if this is of any help but that is how I partly have sold it at home.
 
My Desktop is with Lucid 10.04 directly connected with LAN cable to the router and my laptop is with Karmic 9.10 with wireless connection to the same router of course.
 
I edited the connections (right click on top left connection icon and edit) inserting an IP, Gateway etc...in order to avoid the router to assign IPs automatically.
 
In "places" , I type in "locations" the following : "smb://IPadressOFthe_other_PC" and bookmarked it.
 
Acivated the file sharing for each of the folders I wanted to share in each PC and laptop . And it works.  
 
It is not friendly user at all but it has been a solution for me.

---

### Post by Paddy Landau on 2010-05-31
> **Imatech64 said:**
> I edited the connections (right click on top left connection icon and edit) inserting an IP, Gateway etc...in order to avoid the router to assign IPs automatically.
Well, I can get my router to assign a permanent IP address using the MAC address. But, that's a really silly thing to have to do; if I change or add a new computer, or if a friend visits and needs to connect, or if the router dies and I have to replace it, then it means I have to fiddle at that level. Again.
 
> **Imatech64 said:**
>  In "places" , I type in "locations" the following : "smb://IPadressOFthe_other_PC" and bookmarked it.
Yes [post 17]("http://ubuntuforums.org/showthread.php?p=9356526#post9356526") also mentioned that. But that's not possible with my scanner.
 
> **Imatech64 said:**
> It is not friendly user at all but it has been a solution for me.
Agreed, not a user-friendly solution -- especially as it used to work before 10.04! "Computers for humans" ideally should not have to fiddle with IP addresses when the computers have names.

I'm awaiting a response from Canonical, and I'll let you know what happens.

Incidentally, do you know how to change the name of the computer? I  don't see that setting anywhere.

---

### Post by Morbius1 on 2010-05-31
>  Incidentally, do you know how to change the name of the computer? I   don't see that setting anywhere.The easiest way without mucking about in linux internals is to use smb.conf itself:

Add the following line to the [global] sections of smb.conf:
```
netbios name = something
```"Something" can be anything you want as long as it is less than or equal to 15 characters long and doesn't have spaces or weird symbols in it.

Don't forget to restart samba.

NOTE: This will change how your machine is seem on the network only. If you open up a terminal it will still show the old name.

---

### Post by Paddy Landau on 2010-05-31
Thanks for letting me know. I actually was wondering about the computer's name irrespective of Samba. Anyway, it's not important.
> **Morbius1 said:**
> Don't forget to restart samba.
How do I restart Samba without rebooting? I've been Googling but not found the answer.

---

### Post by Morbius1 on 2010-05-31
Depends on what version of Ubuntu you are using:

Prior to 10.04:
```
sudo service samba restart
```In 10.04 we're going back to the good old days:
```
sudo restart smbd
sudo restart nmbd
```

---

### Post by Garthhh on 2010-05-31
> **Morbius1 said:**
> Depends on what version of Ubuntu you are using:

Prior to 10.04:
```
sudo service samba restart
```In 10.04 we're going back to the good old days:
```
sudo restart smbd
sudo restart nmbd
```

I had started a thread a few days ago & gave up when it got to the level of static IP's & mucking about in the terminal

When I try to do a GUI right click share I get 
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.

There are some old bugs from a couple of years ago

I have what should be easy questions
how can I tell when samba & or Gshare [anything for that matter]  is running, using GUI?

I'm running 10.04 on an old PC, wired
& mint9 on a couple of laptops, [though both also have 10.04 installed] wireless

I'll just continue emailing stuff around to my self until there is a reasonably easy solution...

not being able to do the easy stuff like this is one of the things that keeps Unbuntu from going prime time
on a happy note the wireless never worked on this notebook when it was an XP machine

---

### Post by BandD on 2010-05-31
I had a very similar problem.  Same error message from Nautilus when trying to access the "Windows Network".  I did a lot of research on the smb.conf file and came across this excellent guide [http://ubuntu.swerdna.org/ubulanprimer.html]("http://ubuntu.swerdna.org/ubulanprimer.html").  What ended up working for me was opening up the smb.conf file and insterting/overwritting a few lines in the global section.  Here's how:

First we'll back up the current smb.conf file.  In a terminal:```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
```

Then we'll make the changes to the new one.  Again in a terminal: ```
sudo gedit /etc/samba/smb.conf
```

Scroll down a little and you should see a section marked [GLOBAL]  it should look something like this ```
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
```

Replace that entire section with the following:```
workgroup = WORKGROUP
netbios name = NETBIOS_NAME
name resolve order = bcast host lmhosts wins
map to guest = Bad User
local master = yes
os level = 33
```

Replace NETBIOS_NAME with the name you wnat your computers to be called across the network (it should be different on each computer).  Click Save.

Make these changes to EVERY computer on your network.  Restart them all.

It worked for me.  Hopefully you'll have some luck with it too!

---

### Post by new_tolinux on 2010-05-31
> **BandD said:**
> Replace NETBIOS_NAME with the name you wnat your computers to be called across the network (it should be different on each computer).

I did not try this, but I'll have to say that it really makes sense to set the NETBIOS-name. Although to keep things simple I think that the netbios-name should be set the same value as the hostname.

---

### Post by Morbius1 on 2010-05-31
> Although to keep things simple I think that the netbios-name should be  set the same value as the hostname.     By default Samba uses the hostname. Using smb.conf is just a simple way to change it.

---

### Post by Paddy Landau on 2010-05-31
> **BandD said:**
> Replace that entire section with the following...

 BandD... thank you! :)

Oh well, I guess that my money spent on Canonical was wasted. Never mind, I don't mind contributing after all that Canonical has given me free, and it was certainly cheaper than buying the competition.

[FONT=Courier New] testparm -v[/FONT] showed me that the only options needed were [FONT=Courier New]name resolve order[/FONT] and [FONT=Courier New]os level[/FONT]. I experimented a little to confirm this.

The [FONT=Courier New]netbios name[/FONT] is not necessary, provided that you've already set your computer name differently from the other computers; otherwise, you do need it.

I read on another site that you make [FONT=Courier New]smb.conf[/FONT] more efficient as follows:

[LIST]
[*]Back up your [FONT=Courier New]smb.conf[/FONT] as BandD already said.
[*]Copy your [FONT=Courier New]smb.conf[/FONT] into [FONT=Courier New]smb.conf.master[/FONT]. In future, change only [FONT=Courier New]smb.conf.master[/FONT].
[*]After you've changed [FONT=Courier New]smb.conf.master[/FONT], run the following command:
**[FONT=Courier New]sudo testparm -s /etc/samba/smb.conf.backup >smb.conf[/FONT]**
[FONT=Courier New] testparm[/FONT] will check your [FONT=Courier New]smb.conf.master[/FONT] and display any errors in the terminal, then output a cleaned-up version to [FONT=Courier New]smb.conf[/FONT].
[/LIST]

---

### Post by BandD on 2010-05-31
Glad it worked for you Paddy!

I don't mean to be a nag, but would you mind marking this thread as solved if everything is indeed working?  I'm a little OCD.  ;)  Thanks!

You'll just have to find more problems for Canonical to help you with...

---

### Post by Paddy Landau on 2010-06-01
> **BandD said:**
> ... would you mind marking this thread as solved...
Thanks for the reminder. In my relief, I quite forgot.

Oh, and Canonical got back to me. Said I'd purchased the wrong package, even though I confirmed previously that it was the right package. Hmm.

---

### Post by WolfRage on 2010-06-05
Don't ,mean to bring this back up but I believe I found a simpler way for you Paddy.
Please see here: [http://ubuntuforums.org/showthread.php?t=1502265](http://ubuntuforums.org/showthread.php?t=1502265)

---

### Post by Paddy Landau on 2010-06-05
Hello WolfRage, thanks for pointing that out.

That is precisely what I ended up doing, but it still didn't work!

The key was to add what [BandD explained]("http://ubuntuforums.org/showthread.php?p=9389067#post9389067"), to add [FONT=Courier New]name resolve order[/FONT] and [FONT=Courier New]os level[/FONT] to the Samba file's [global] section.

---

### Post by WolfRage on 2010-06-05
Thanks for the update paddy. I am not sure why different things work for different setups. Either way i hope that Ubuntu can make this a lot easier in the future so any one can do it with out trouble. File sharing is big and users want it and Windoz does it quick and easy but Ubuntu is still a fight....

---

### Post by dgaud on 2010-06-09
Thanks everyone for the info. I finally got this working at home. However my **name resolve order** is different (it didn't work the other way)?:

name resolve order = hosts lmhosts wins bcast

I can now see my share folder from another ubuntu pc in PLACES/NETWORK and even from my Windows Mobile phone!

---

### Post by Paddy Landau on 2010-06-09
> **dgaud said:**
> .. my **name resolve order** is different...
How curious.

So many people seem to be affected by this. Do you all agree that I should file it as a bug?

---

### Post by scrapmetal on 2010-06-10
I think reporting as a bug would be a good idea.
I would if I new how to file the steps taken, a b c etc. = outcome.
Think you would be doing a great service to us all.
Thanks Paddy.
Will keep following this thread with the greatest of interest.
Network - Share folders etc should not be Brain Surgery,
when all else works together so well.):P

---

### Post by Garthhh on 2010-06-11
> **Paddy Landau said:**
> How curious.

So many people seem to be affected by this. Do you all agree that I should file it as a bug?

I've been doing a bit of corresopndence w/launch pad & referring to this thread, I haven't been able to determine if there is a formal bug as yet.

I'm a bit swamped & haven't tried the workaround from the other thread as yet

simple sharing should work, being one of those basic things.

Yes please on a bug report

---

### Post by Paddy Landau on 2010-06-11
I found a couple of bugs that looked similar, but not quite the same.

I've logged a new bug for this.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610)

Feel free to vote for it.

---

### Post by Garthhh on 2010-06-15
There are also some other related threads:
Paddy Landau's thread
[http://ubuntuforums.org/showthread.php?t=1491092](http://ubuntuforums.org/showthread.php?t=1491092)
with a work around

Wolfrage's better solution:
[http://ubuntuforums.org/showthread.php?t=1502265](http://ubuntuforums.org/showthread.php?t=1502265)

A bug [please subscribe]:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610)

My thread from a couple of weeks ago:
[http://ubuntuforums.org/showthread.php?t=1491180](http://ubuntuforums.org/showthread.php?t=1491180)

The community of developers has spent many hours developing this  capability, too bad it doesn't work, without a bunch of fiddling around  on the command line:confused:
If you are reading this & would like to be able to share files with a  couple of mouse clicks, post a comment on the threads & especially  the bug

---

