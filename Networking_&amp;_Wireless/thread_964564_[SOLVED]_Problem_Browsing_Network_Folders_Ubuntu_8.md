---
title: "[SOLVED] Problem Browsing Network Folders Ubuntu 8.10"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by GoodPanos on 2008-10-31
Well, here we go again with another Samba problem.  First, Hardy Heron had a problem with browsing folders (could not copy network folders) and it got fixed in 8.04.1.  Now the problem is even worst in Ibex (8.10).

When I browse network shares on my NAS drive like so:
```
smb://192.168.1.2
```I get a list of my folder shares.  When I open any of them, they come out blank, empty.  With previous versions from 8.04.1 down, this was not an issue.

I like to point out that this is happening accross all new distros, like Fedora 9, Suse 11...  I have seen some posts to enable SMB browsing on the firewall but it never worked for me.

I beg somebody to have a solution for this. [-o< This is a total Linux show stopper for me and I can't even go to any other distro.

[COLOR="Red"]Edit: See post #81 for solution.[/COLOR]

---

### Post by Kobalt on 2008-10-31
What happens if you try to connect to your shares using the Places > Connect to a server menu ?

---

### Post by GoodPanos on 2008-10-31
Same exact thing, blank!

---

### Post by phil888 on 2008-10-31
> **GoodPanos said:**
> Well, here we go again with another Samba problem.  First, Hardy Heron had a problem with browsing folders (could not copy network folders) and it got fixed in 8.04.1.  Now the problem is even worst in Ibex (8.10).

When I browse network shares on my NAS drive like so:
```
smb://192.168.1.2
```I get a list of my folder shares.  When I open any of them, they come out blank, empty.  With previous versions from 8.04.1 down, this was not an issue.

I like to point out that this is happening accross all new distros, like Fedora 9, Suse 11...  I have seen some posts to enable SMB browsing on the firewall but it never worked for me.

I beg somebody to have a solution for this. [-o< This is a total Linux show stopper for me and I can't even go to any other distro.
I am having the same problem since upgrading to Intrepid, cannot get to windows network shares at my office from my laptop. This was working in Hardy. I can see the server in nautilus but the the display of contents is blank.
If i try to go directly to my share/directory I get 
"Error: Failed to mount Windows share
Please select another viewer and try again."

I am thinking of going back to Hardy.

---

### Post by mattray on 2008-10-31
Same problem here! This is not good for me and I may have to leave ubuntu and try another distro after 2+ years on ubuntu.

---

### Post by jaime256 on 2008-10-31
I'm having the same problem as well. I just did a clean install of the 8.10 desktop over the 8.04, not an upgrade and now I don't have access to my shares. I tried both browsing the network and connecting to the server...nothing...I also added the smbfs I think the system suggested, but still nothing...does anyone else have any ideas since I know there are a few new things on this version?

I just logged into the web administration page of my nas and I can get to it fine, so it's up and running, but I still can't access the shares from Ubuntu 8.10. My 8.04 version can still access the shares. I still have this installed on another machine.

---

### Post by tony2tone on 2008-10-31
same problem too performed an upgrade. I was easily abble to browse the shared folders on my windows computer but now it comes up blank and the windows machine can't see the shared folders from my ubuntu machine. performed a ping on both machines and both machines are able to talk to each other just not able to see the files on the network folder and network places.:(

---

### Post by RiffRaff06078 on 2008-10-31
Yep, same here.  Upgraded from 8.04 to 8.10 last night.  All shared Windows folders on my network worked fine yesterday; all showing up blank today.

I'm digging through the smb.conf file right now to look for changes, but a quick fix to this would be much appreciated.

Edit: I don't think this is a Samba issue.

Edit #2: Tried a suggestion from another forum and installed Gnome Commander.  I can mount and access SMB shares perfectly fine using this application.  That's a temporary workaround for anyone who needs it.  Looks like the problem lies in Nautilus.

---

### Post by rstewartmailacct on 2008-10-31
Yea I put post out about this 2 times over the past couple of weeks while testing.  I think this is the bug report.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

I tried SMB4K and it doesn't work anymore either so maybe I'll try Gnome commander tonight.
:-)

This works on my old Feisty machine.
:-)

Maybe they'll get it fixed if people keep this post going.:lolflag:

---

### Post by phil888 on 2008-10-31
I tried gnome commander, it also didn't work.

---

### Post by cariboo on 2008-10-31
Has anybody tried mounting a windows share manually?
I've been using Intrepid since before the Alphas and have never had the problem. To mount a share manually, make sure you have smbfs installed then in a terminal type:

```
sudo mount //server/share /media/mountpoint
```

where server= your server name or ip address share = sharename media/mountpoint = directory you have created in /media. You will have to enter your password in order to connect.

This doesn't fix the problem, but at least you can access your shares until the bug is fixed.

Jim

---

### Post by RiffRaff06078 on 2008-10-31
> **cariboo907 said:**
> Has anybody tried mounting a windows share manually?


Modifying the command you provided slightly to:

```
sudo mount //server/share /media/mountpoint/ -o user=username,pass=password
```

did the trick.  The share in question mounted and displayed properly.

Pain in the neck, but usable until a permanent solution is released.

Thanks!

---

### Post by jagercola on 2008-10-31
Yup, new 8.10 install on a thinkpad t41.  Can't browse my windows shares as they come up blank.

---

### Post by rrranch on 2008-11-01
Same here, can't connect to any other machine on my network since using 8.10.

---

### Post by S.O.P on 2008-11-02
Same again (this happened with 8.04 too - I didn't use it again).

Gnome Commander works, thanks for the suggestion.  Forgot to mention, last time Konqueror worked, Nautilus had the issues.

---

### Post by geokok1981 on 2008-11-02
The problem goes like this.

1. Windows can see shared files on ubuntu.

2. Nautilus can see shared folders at first. Everything works fine.
When I share a folder on ubuntu the sharing emblem appears on it.

3. At some random point Nautilus can no longer see the shares on the network. Also the sharing emblem disappears from ubuntu shared folders 
(although they do remain shared). 
*Note: the shares remain active and working. They can be accessed normally from and to windows using the following methods:
 3a. Use firefox to access shared folders
 3b. Use Gnome commander
 3c. Use Places-->Connect to server and add manually the path to the folder. 

So this does not seem like a samba issue but like a nautilus issue. Maybe
something gets screwed when changing the "workgroup" name in samba config, maybe its something with usershares, maybe.....

Do not really know, but it is really annoying having network problems from #1 networking operating system.

---

### Post by jonandrews on 2008-11-02
So many people have added to this post that there is obviously a real problem. All I can add to the debate is that is not present on ALL installations. I have done two clean installations of 8.10 on different machines in support of updating my networking guide:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

Both installations have worked fine, exactly as described in the guide for 8.10 / XP networking.

In the past, I have seen this 'blank' response to clicking on a shared XP folder as an intermittent problem, but not since 7.04, I think.

---

### Post by chipw on 2008-11-02
I too am having this problem and no solutions provided have fixed it. I keep getting session setup failed: NT_STATUS_LOGON_FAILURE

My XP box has no problem accessing my Ubuntu box, that direction works great. What's the point of even using Linux, or specifically Ubuntu, if networking doesn't work? Very disappointing.

---

### Post by funchords on 2008-11-02
I'm having multiple and competing problems involving Windows Networking.

The issue I was having that I don't think was involved in this is that my ISP is returning bogus IP addresses when lookups fail (Verizon and their "helpful" advertising).  I have worked around this by forcing my router and clients to use 4.2.2.1 and 4.2.2.2 for DNS.  The smbtree utility would find the server names but fail to resolve the IP addresses until I did this.  (I mention this because it's possible that failing to fix this would block making progress.)

The issue that I think may be involved in this is the wrong WORKGROUP being in Gnome configuration.  See [http://ubuntuforums.org/showthread.php?t=963152](http://ubuntuforums.org/showthread.php?t=963152) for the solution to this -- however, it only gets me one step further.  I still can't see beyond the machine names without a formal logon on Windows XP machines.  

This workaround command from a terminal window works .. 
**nautilus smb://TOPOLSKINET\;robb\@192.168.177.105/mybook/**

Where TOPOLSKINET is my workgroup and robb is my account name on 192.168.177.105 and mybook (actually MyBook) is the share name. 

This is MUCH harder than it should be.

---

### Post by Halbarad on 2008-11-02
Same prob here -- but this might be funny... I tested Intrepid alpha, told Launchpad there was a bug with browsing samba shares; several people did so, it's quite a well-known bug... But instead of fixing it before releasing Intrepid, they extended it to Hardy!!! ](*,)  After a recommended upgrade, both my Ubuntu machines stopped browsing the local network.

I have just installed Gnome Commander, which seems to WORK. However, since I have messed everything up so much by activating Wins and so on, I am afraid I shall have some hard time trying to set everything back...
I found a very interesting and competent post by Gregphil here: [http://ubuntuforums.org/showpost.php?p=5871299&postcount=663](http://ubuntuforums.org/showpost.php?p=5871299&postcount=663)
The bug seems tough, and it seems to have to do with Gnome itself. See also this post by SonicSteve: [http://ubuntuforums.org/showpost.php?p=6090260&postcount=72](http://ubuntuforums.org/showpost.php?p=6090260&postcount=72) 
Do you think the only really safe choice is to move to Kubuntu?
I'm ready to do anything (I mean, almost anything ;-) ) to get the basics of my system working... I don't care about the candy (compiz and the likez)

---

### Post by WrathofthePenguin on 2008-11-02
I was seeing this problem and have reported the following bug:

[https://bugs.launchpad.net/ubuntu/+bug/292836](https://bugs.launchpad.net/ubuntu/+bug/292836)

My thread is:

[http://ubuntuforums.org/showthread.php?t=968407](http://ubuntuforums.org/showthread.php?t=968407)

The problem is that (likely) samba is dropping the last character of the file/directory name in the packets being sent to the share server.

Gnome Commander does not really work (at least for me) - you will see more than with nautilus, but I find you cannot browse down to the file levels and access them.

---

### Post by WrathofthePenguin on 2008-11-02
Open the share up in firefox and add the last character of directories/files in the url bar.

Example:

If I open up my share using:

smb://192.168.5.103/

And click on the share name (for me it's Volume_1), I get this in the url bar:

smb://192.168.5.103/Volume_1

Look at the files and directories below, they will all have the last character dropped. Click on one anyway. I clicked on "DVDs" and the following shows up in the url bar:

smb://192.168.5.103/Volume_1/DVD

I can add the 's' on to the end, and access the directory. I can keep doing this until I get where I need - it is very tedious, but it works.

---

### Post by stageman on 2008-11-02
I was having the same problem until I entered my workgroup(domain) name into my router's  (dl-604) set up page. Bang, browsing and slow copying fixed!

I left ubuntu's network manager set to full dhcp.

---

### Post by bab1 on 2008-11-02
I feel that I should relate my experiences with Ubuntu and Samba.  I have successfully installed and maintained Samba on 7.04, 7.10 and 8.04 (Feisty, Gutsy and Hardy).  My clients have been XP Pro and Ubuntu.  I don't mount any drives via fstab.  I don't use winbind, I don't use NetBios.  I have never had a problem.  I feel this is due to my configuring samba manually.  I do not configure anything using Gnome (Nautilus) or any of it's tools.

IMHO the problems arise from the use of the GUI interface to try to  configure "shares".  Then when it fails, trying to solve the problem problem by manually modifying /etc/samba/smb.conf file.  Why does this fail?  Because Gnome (Nautilus) uses /var/lib/samba to configure the "shares".  These files are binary and can't be modified with a text editor.  As a side issue , the gvfs and the new GIO libraries are changing.  There are other concerns for the Gnome developers. 

I believe that the Samba daemon will always work when the /etc/samba/smb.conf file is used to configure the "shares".  it sure has for me.  I the upcoming future I will be upgrading to 8.10 (Intrepid).  I'm sure that it will work too.

---

### Post by devastian on 2008-11-03
I have the same issue when trying to access a samba share from Nautilus but I could make it work by manually mounting the samba share in my system.

> 
mount //192.168.2.120/Volume_1 /mnt/NASVOL1 -o password=""


Since I am using user "guest" with no password by default in my NAS I just provide the empty password and it worked. ;)

Seems that the issue is related to the **default authentication** when mounting the samba share with Nautilus from Gnome. From the console it works fine.

---

### Post by makmiler on 2008-11-03
It is I'm almost sure Nautilus problem.

Try this:

add your Username to the samba:

```
sudo smbpassd -a user
```


then try this:

```
smbclient --list=HOSTNAME
``` (under hostname write for example the hostname or the ip address of the host), and you will get a listing of all the shares on that host computer. So, if you get this, it means that samba is working all right, but nautilus is not interpreting the output as it should.


Best regards,
Robert.

---

### Post by WrathofthePenguin on 2008-11-03
> **makmiler said:**
> It is I'm almost sure Nautilus problem.

Try this:

add your Username to the samba:

```
sudo smbpassd -a user
```


then try this:

```
smbclient --list=HOSTNAME
``` (under hostname write for example the hostname or the ip address of the host), and you will get a listing of all the shares on that host computer. So, if you get this, it means that samba is working all right, but nautilus is not interpreting the output as it should.


Best regards,
Robert.

Given that the packet capture shows that the last character of the directory and/or file name is being dropped I am certain that it has nothing to do with a config problem. I do appreciate the suggestion, however.

---

### Post by jg1395 on 2008-11-03
i'm having problems with 8.04 talking through samba to my freenas server.  During write from ubuntu to freenas something goes wrong and freenas reboots.  

booted into xp on the same machine and performed numerous big copies with no problems.

i was about to lose it when i thought my freenas motherboard was going out.  so glad the problem is samba, gnome, or something...

---

### Post by dmizer on 2008-11-04
> **jg1395 said:**
> i'm having problems with 8.04 talking through samba to my freenas server.  During write from ubuntu to freenas something goes wrong and freenas reboots.  

booted into xp on the same machine and performed numerous big copies with no problems.

i was about to lose it when i thought my freenas motherboard was going out.  so glad the problem is samba, gnome, or something...

FreeNAS supports NFS, use it instead of samba, you'll get much better results.

---

### Post by renatoborges on 2008-11-05
I am having the same problem but reading this forum I figure out a possible solution. apparently the problem is with nautilus but I managed to resolve the situation as follows:

1 - open a nautilu's window
2 - change the location for the version in which you enter the path (see image1.png)
3 - enter the path to the computer you want to access starting with smb://
EX1: smb://computername/folder_name - where computername may be the computer name or IP address of the computer and folder_name is the name of the shared folder on your computer
EX2: smb://computername/hd_label (f) - where computername may be the computer name or IP address of the computer, hd_label is the label (name) of the shared disc followed by space and (f) is the unit of the disc between brackets and without a colon.
4 - after entering the path press enter
5 - if your share is not password-protected files and folders should appear immediately. if the share is password-protected login screen will appear asking the user, domain and password (see image2.png). just fill in and press OK. the folder will appear connected to your desktop.

if you do not want to perform this procedure every time you want to access your shared folders do one of the following:

Option 1
1 - open a nautilu's window and select the shared folder in the left sidebar (see image3.png).
2 - precione ctrl+D to save the folder in the list of favorites.

Option 2
1 - click the icon for the shared folder that appears in the locals menu, drag to the menu bar (where are the icons of evolution and firefox) and drop (see image4.png).

the next time you want to connect to the shared folder simply click on the corresponding icon.

this may not be the final solution but I think the best to we access our shared folders without need of additional software or complicated settings in command line.

---

### Post by makmiler on 2008-11-05
The solution that you are proposing here is not a solution, but a bypass, which doesn't work in every case-scenario, but only on a network with 2-3 computers. What will happen with your solution, if you don't know which folders are beeing shared on the network ?

What if you have a network with more then 100 computers, like we have? Are you going to make a Favorite for all the 100 * 8-9 = 800-900 shared folders on the network ? On every computer ?

Can you more so imagine the Places Menu with 900 favorites, or the Desktop with 900 icons on it ?



> **renatoborges said:**
> I am having the same problem but reading this forum I figure out a possible solution. apparently the problem is with nautilus but I managed to resolve the situation as follows:


---

### Post by renatoborges on 2008-11-05
> **makmiler said:**
> The solution that you are proposing here is not a solution, but a bypass, which doesn't work in every case-scenario, but only on a network with 2-3 computers. What will happen with your solution, if you don't know which folders are beeing shared on the network ?

What if you have a network with more then 100 computers, like we have? Are you going to make a Favorite for all the 100 * 8-9 = 800-900 shared folders on the network ? On every computer ?

Can you more so imagine the Places Menu with 900 favorites, or the Desktop with 900 icons on it ?

that is the reason i sad "possible solution". the bypass may not work in your case but, certainly, work's for a lot of people.

---

### Post by makmiler on 2008-11-05
Well I found one solution to the whole problem.

You have to install the smbnetfs package from the ubuntu repository

```
sudo apt-get smbnetfs
```

This package allows you to connect to the Workgroup and to browse the whole network without any problems through nautilus. You will be able to access all the computers, all the shares, and all the folders.

1. After installing the package, create a folder in your /home under the name .smb. 
2. Copy the smb.conf file from /etc/samba, and smbnetfs.conf from /etc into this folder.

```
cp /etc/samba/smb.conf /home/$user$/.smb
cp /etc/smbnetfs.conf /home/$user$/.smb

```

3. Configure the files as you like, and up you go.

Just type ```
smbnetfs [mountpoint]
```


Problem with Samba sharing gone.


Best regards,
Robert Mileski

---

### Post by yippiekiyay on 2008-11-05
I am having the same issues.  My shares are not browseable, can not browse vista shares.  What the heck is the issue?

---

### Post by dmizer on 2008-11-05
> **makmiler said:**
> Well I found one solution to the whole problem.

You have to install the smbnetfs package from the ubuntu repository

```
sudo apt-get smbnetfs
```

This package allows you to connect to the Workgroup and to browse the whole network without any problems through nautilus. You will be able to access all the computers, all the shares, and all the folders.

1. After installing the package, create a folder in your /home under the name .smb. 
2. Copy the smb.conf file from /etc/samba, and smbnetfs.conf from /etc into this folder.

```
cp /etc/samba/smb.conf /home/$user$/.smb
cp /etc/smbnetfs.conf /home/$user$/.smb

```

3. Configure the files as you like, and up you go.

Just type ```
smbnetfs [mountpoint]
```


Problem with Samba sharing gone.


Best regards,
Robert

This works, but it's still tricky. Better than most of the other options I've seen though.

---

### Post by makmiler on 2008-11-05
> **dmizer said:**
> This works, but it's still tricky. Better than most of the other options I've seen though.

Yes, it does works. I can mention some advice to those who are installing it about the package.

1. When you create your own .smb folder and copy the two needed files, the only thing to configure in the smb.conf file is the name of the WORKGROUP, nothing else needs to be changed.

2. The file smbnetfs.conf should be changed in this way:
   - Add the smb user and password to the file, you find that at the end of it
   - Change the context time to 100 sec, because 300 sec sounds too much for me, because I got drops from the timeout.

3. Make the smbnetfs.conf file chmod 600, because of security of the password.

4. Create a folder on the desktop named "Network"

5. Then you can put a startup module for the program, under System -> Preferences -> Sessions, in which you put: smbnetfs /home/$user$/Desktop/Network


This will enable you to see your samba network with every start automatically.



Best regards,
Robert Mileski

---

### Post by dmizer on 2008-11-05
> **makmiler said:**
> Yes, it does works. I can mention some advice to those who are installing it about the package.

1. When you create your own .smb folder and copy the two needed files, the only thing to configure in the smb.conf file is the name of the WORKGROUP, nothing else needs to be changed.

2. The file smbnetfs.conf should be changed in this way:
   - Add the smb user and password to the file, you find that at the end of it
   - Change the context time to 100 sec, because 300 sec sounds too much for me, because I got drops from the timeout.

3. Make the smbnetfs.conf file chmod 600, because of security of the password.

4. Create a folder on the desktop named "Network"

5. Then you can put a startup module for the program, under System -> Preferences -> Sessions, in which you put: smbnetfs /home/$user$/Desktop/Network


This will enable you to see your samba network with every start automatically.



Best regards,
Robert Mileski

You should write up a good howto for this.

A word of caution: This method breaks if you share a folder through Nautillus (right click > sharing options > share this folder)

---

### Post by WrathofthePenguin on 2008-11-05
> **dmizer said:**
> This works, but it's still tricky. Better than most of the other options I've seen though.

Well, that didn't change a thing for me. I checked and the last character is still being dropped in the packets.

---

### Post by makmiler on 2008-11-05
> **dmizer said:**
> You should write up a good howto for this.

A word of caution: This method breaks if you share a folder through Nautillus (right click > sharing options > share this folder)

I will write a Howto, good idea. :)

What do you mean by breaks the method? If you share the newely created Network folder on the desktop ?

I also think of changing the .deb package, so it'll be more suitable for normal users, so they don't need to go through all of these things, but rather a direct config of the program.

---

### Post by dmizer on 2008-11-05
> **makmiler said:**
> I will write a Howto, good idea. :)

What do you mean by breaks the method? If you share the newely created Network folder on the desktop ?

I also think of changing the .deb package, so it'll be more suitable for normal users, so they don't need to go through all of these things, but rather a direct config of the program.

If I share a folder through Nautilus, and then try to mount with smbnetfs, I get this error:

---

### Post by dmizer on 2008-11-05
Also, I still had to configure /etc/nsswitch.conf and install winbind.

---

### Post by bab1 on 2008-11-05
Indeed this is a hack.  A useful one in some instances.  Running Samba in userspace instead of under Nautilus is problematic as dimizer has found out.  It is no substitute for proper smb.conf configuration.  In fact it will be slower under high load.  Userspace has a lower I/O priority than the OS.

---

### Post by dmizer on 2008-11-05
> **bab1 said:**
> Indeed this is a hack.  A useful one in some instances.  Running Samba in userspace instead of under Nautilus is problematic as dimizer has found out.  It is no substitute for proper smb.conf configuration.  In fact it will be slower under high load.  Userspace has a lower I/O priority than the OS.

I found the speed to be much greater than mounting via Nautilus. Actually speeds very close (if not equal to) that which I get when mounting via cifs and fstab.

I have yet to duplicate your findings with configuring smb.conf however.

As an asside, a reboot corrected my problem. Other than that minor niggle, the method outlined above worked perfectly. Still requires a significant amount of cli editing though.

---

### Post by bab1 on 2008-11-05
Ah, but you are using netbios to resolve names.  I do not do that.  Do you have acces to DNS services?  Is this on you own private LAN?  I am posting a setup scheme to  [[COLOR="Red"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=784259&page=11") in a few minutes.  I'd welcome your thoughts.

---

### Post by GoodPanos on 2008-11-06
renatoborges, I don't know how you have your system configured, but your solution does not work for me.

Even when typing the address with the share name the folder still comes out blank.

---

### Post by phil888 on 2008-11-06
Same here, I believe I have tried almost every solution posted, though I work mostly graphically so I cannot be sure I did everything correctly but I cannot get beyond accessing the server on the network, the contents always come up blank. i am however surprised that a fix has not yet been released especially since it was working in Hardy. By the way does anyone know which file stores the search domains names that are entered in network manager settings?

---

### Post by Piupardo on 2008-11-06
Hi all!

I'm having this problem too, but with a little difference. Let me explain.

I have two Vista and one XP computers with shared folders.
They are all, as the one with ubuntu, in the same workgroup.

I can see them all when browsing in Nautilus.

I can access their shared folders with smb://x.x.x.x/[shared folder name] on the go to command line of nautilus. Just asks me the user and pass, and there we go.

If I want to access them in Nautilus browsing through the network, I only get blank pages from the ones with Vista, but I am ok with the one with XP, it shows me the folders and shares of it, and I can access them with no problems.

Tryed everything I found to make them appear when browsing...

Any thoughts, ideas?

Thanks in advance,
Piupardo

---

### Post by bab1 on 2008-11-06
@Piupardo,

I believe your problem is with the Vista encryption.  See [[COLOR="Red"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=954691") for the fix

---

### Post by Piupardo on 2008-11-06
> **bab1 said:**
> @Piupardo,

I believe your problem is with the Vista encryption.  See [[COLOR="Red"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=954691") for the fix

I also had the idea that the problem would be with Vista, once with XP everything is ok.

I tryed one of the options in that link, the other two links on the last post are broken, changed the [Send LM & NTLM - use NTLMv2 session security if negotiated] on local policies, but still with the same problem.

Can access and mount through smb://..../shared... but can't browse Vista computers/folders. I see the computers, but always open a blank page when opening them.

Well, thanks for the help anyway, I'm going to keep my searching and researching :)

Regards,

---

### Post by GoodPanos on 2008-11-06
Indeed!!!

I should have checked that too; browsing WinXP shared folders also works for me.

Browsing the shared folders on my NAS does not work.  Looks like it's probably using a different protocol?  I know it supports both Win and/or MAC.  This should not matter though, because it worked up until Hardy Heron.

Anyways, it's nice to know that it works with WinXP shares.  Thanks Piupardo for checking that.

---

### Post by dmizer on 2008-11-07
> **GoodPanos said:**
> Browsing the shared folders on my NAS does not work.  Looks like it's probably using a different protocol?  I know it supports both Win and/or MAC.  This should not matter though, because it worked up until Hardy Heron.

What NAS device do you have? (make and exact model number please)

---

### Post by Steve Ubu on 2008-11-07
I have a temporary solution: I do run the "old" Kernel 2.6.24-21-generic of Hardy and all works in Intrepid

Stefano

---

### Post by Piupardo on 2008-11-07
Anyway, just read somewhere on this forum that this is a reported bug that is being worke.
I guess we'll have to wait a little more.

Here it is, found it now on my history:

[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

I get this links from some thread in this forum as well.
Any thoughts?

Thanks,
Regards,

---

### Post by HarshReality on 2008-11-07
Im running a NASLite server with the same issue (I think) I can see the shares and even open them but the directories are empty.

Ironically in 8.04 when I 'browse the network' It would display Windows Network and I went in to see my other network computers. With 8.10 when I hit network it shows the shares AND Windows Network and if I go into windows network its just like it was with 8.04 (Workgroup > Systems > Shares).

So, I cant imagine why this one goes..

SharePC1 - Shares
SharePC2 - Shares
Windows Network - Workgroup - SharePC(s) - Shares

In either case I cant manipulate or even see the files on the linux shared NAS but I seem to be able to browse the windows directories fine.

Did the firefox thing and sure enough last character is dropped.. but only for my linux nas. Windows shares work fine.

---

### Post by GoodPanos on 2008-11-07
> What NAS device do you have? (make and exact model number please)
I have a Buffalo LinkStation 250GB (HD-H250LAN).

---

### Post by Eyebeear on 2008-11-09
> **GoodPanos said:**
> I have a Buffalo LinkStation 250GB (HD-H250LAN).

I seem to have the same problem.(empty shared folders on NAS)

Don't know if it's any help, but I can create a new folder using Nautilus in one of the apparently empty shared folders and it shows up when viewed from my Windows XP machine.

---

### Post by tehsnipes on 2008-11-09
okay, I installed smbntfs and all the above mentioned fixes. Now my workgroup and pcs show up on network. When I double click on my PC, nautilius just hangs for 5-10 minutes and gives this error 

> Sorry, could not display all the contents of "Windows shares on desktop": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


ANy ideas?

---

### Post by HarshReality on 2008-11-09
One of the earlier links in this thread pointed out a bug report and somehow clicked around and came a cross a positive post that mentioned sometime @ the 26th... thats a rediculously long time to wait for a fix to an issue that should have been resolved before including it in a release...

One of the great things I do like about webcode, if it doesnt work you just roll it back or undo a change, I have honestly no idea how I'd do that in this case short of complete format and install of 8.04. And from what I understand if I update 8.04 the same thing will happen since this 'issue' was sent to that release in the form of an update.

So, should anybody know how to roll back Samba to make this go away I'd be more than willing to hear it.

---

### Post by bab1 on 2008-11-09
@HarshReality,

I don't believe this is a Samba problem.  It is a Gnome (Nautilus) issue.  In all reality it can't be resolved by the folks at samba.org.  It appears that this problem is due to Nautilus incorrectly forming requests to the smbd daemon.

The problem is exacerbated further when the user relies on DHCP for IP addressing and does not implement either DNS or NetBIOS naming.

---

### Post by dmizer on 2008-11-09
> **GoodPanos said:**
> I have a Buffalo LinkStation 250GB (HD-H250LAN).

Yeesh. I've not been successful in getting anyone connected to that device. Sorry.

---

### Post by HarshReality on 2008-11-09
> **bab1 said:**
> @HarshReality,

I don't believe this is a Samba problem.  It is a Gnome (Nautilus) issue.  In all reality it can't be resolved by the folks at samba.org.  It appears that this problem is due to Nautilus incorrectly forming requests to the smbd daemon.

The problem is exacerbated further when the user relies on DHCP for IP addressing and does not implement either DNS or NetBIOS naming.

The result is the same, it shouldnt have made it to a release state. I dont see it asa nautilus issue at all considering the posts previously about the last character dropping off. This is apparent when viewing using firefox.

For a reminder to those just tuning in...
firefox.. smb://192.168.1.250/ Displays shares which is accessable but once in the shares all the links and filenames are missing the last character. So... seperate program.. same issue.. not a user interface issue.. more the program feeding it.

---

### Post by echovolutionx on 2008-11-09
:confused::confused::confused:

---

### Post by GoodPanos on 2008-11-10
As far as Hardy Heron, it does not have this issue.  I have a PC installed with it and I have run every update there is and there is no issue.  There was an issue (not the same as here) with 8.04 but it got fixed with 8.04.1.

To be honest I really don't know where the bug is.  The same thing also is happening with Fedora 9 and Suse 11.0 and I have tried numerous work-rounds with those distros to no avail.

I am not sure, though, but I don't think it's Nautilus.  The reason I say that is because Hardy Heron and Fedora 9 have the same version of Nautilus, 2.22.5.1.  Fedora has this problem but Hardy doesn't :-k

---

### Post by WrathofthePenguin on 2008-11-11
We may in fact be dealing with a couple of issues. However, I have reported a bug, and if you open firefox, type in:

smb://192.168.5.103/Volume_1

Replacing 192.168.5.103 with the IP address of your share and replacing Volume_1 with the share name (this is assuming you do not have a username/pw configured on the share) then you will be presented with a list of directories on your share.

If you see that the last character of your directories is missing, then PLEASE comment on this bug:

[https://bugs.launchpad.net/ubuntu/+bug/292836](https://bugs.launchpad.net/ubuntu/+bug/292836)

The more attention this gets the faster it will get fixed.

---

### Post by beetee2 on 2008-11-12
I cannot seem to get mine mounted properly either.

My Hardware:

Linksys WRT610N
SimpleDrive 500GB usb hdd that is plugged into my router

I type:

sudo mount //192.168.1.1/NetworkDrive/public /media/NetworkDrive -o user=admin,pass=*** in terminal and I get the following as an error:

mount: //192.168.1.1/NetworkDrive/public/ is not a valid block device

Additionally, when I navigate to my Network Folder in Firefox, I am able to see all my files just fine, no name mangling, etc.

Any advice?

NVM!  I fixed this by installing the proper smb4k package... /facepalm  =)

---

### Post by jwilentz on 2008-11-13
> **geokok1981 said:**
> The problem goes like this.

1. Windows can see shared files on ubuntu.

2. Nautilus can see shared folders at first. Everything works fine.
When I share a folder on ubuntu the sharing emblem appears on it.

3. At some random point Nautilus can no longer see the shares on the network. Also the sharing emblem disappears from ubuntu shared folders 
(although they do remain shared). 
*Note: the shares remain active and working. They can be accessed normally from and to windows using the following methods:
 3a. Use firefox to access shared folders
 3b. Use Gnome commander
 3c. Use Places-->Connect to server and add manually the path to the folder. 

So this does not seem like a samba issue but like a nautilus issue. Maybe
something gets screwed when changing the "workgroup" name in samba config, maybe its something with usershares, maybe.....

Do not really know, but it is really annoying having network problems from #1 networking operating system.

Same problem here.  Have tinkered with smb.conf to no avail.  "Upgrade" to 8.10 was a mistake for the networking bit.  REALLY disappointing.  I haven't tried gnome commander.  I'm running Xubuntu 8.10.  Should I try gnome commander?  Any tips or tricks.

---

### Post by notbitmonk on 2008-11-13
I have a NAS attached to the network.  My network consists of the following:
[LIST=1]
[*]Axesstel CDMA 1xEV-DO Wireless internet receiver
[*]Netgear Rangemax Wireless Router
[*]Mobile LanDisk (this is the NAS) from Premiertek [http://www.premiertek.net/products/enclosure35/ED-35-LANII.html]("http://www.premiertek.net/products/enclosure35/ED-35-LANII.html")
[/LIST]
My desktop is connected to the router and I haven't connected a second desktop and a network printer (HP Laserjet 4200n) yet (until I resolve this issue).  Also, since I do not have a wireless device yet (I'm getting my daughter a Wii for Christmas), the wireless is disabled.  My desktop dual-boots with WinXP which is able to see and access the drive without any problems.  The NAS drive is formatted as FAT because it won't recognize another filesystem (although I haven't tried to format the drive as another filesystem to see if the NAS is able to recognize it).  When I had 8.04, there was no trouble accessing the drive.  When I upgraded to 8.10 is when everything started going wrong.  So I do not think that it has anything to do with Samba but with whatever is done when there is an upgrade.  Intrepid was supposed to be about perfecting wireless networking capabilities so I believe that in that tweaking is where things went wrong.  If I access the drive through Connect to Server, it looks like is going to make the connection and then jumps to my home folder.  Accessing it through Firefox only shows me the Public folder (that the share folder accessible to anyone in the network) but not its contents.  I'm able to connect to the NAS configuration page without problems so I know there is no connection problems.  Gnome Commander is not able to see the share.

---

### Post by brycesteiner on 2008-11-13
I'm having similar problems now too.  I'm actually on a Windows XP host machine with VirtualBox and Ubuntu 8.10 guest. I could always connect to a network share just fine with 8.04, but not anymore, yet it can access the internet just fine. The XP box can access the drives just fine. If I manually type in the server and share under the "connect to server" menu item, it still cannot connect.

---

### Post by brycesteiner on 2008-11-13
Here is what I have seen at my location. This problem seems to happen only with new installs. Upgrades still connect fine. I also have the Buffalo linkstation 250.
*new* If I type in the IP address instead of the netbios name in the nautilus window, I can connect fine too. For some reason the new window manager or samba doesn't work with the netbios name. Though, I assume it's just a setting somewhere because the computers that kept their existing configurations files (upgraded) still connect fine.

---

### Post by jwilentz on 2008-11-13
> **brycesteiner said:**
> Here is what I have seen at my location. This problem seems to happen only with new installs. Upgrades still connect fine. I also have the Buffalo linkstation 250.
*new* If I type in the IP address instead of the netbios name in the nautilus window, I can connect fine too. For some reason the new window manager or samba doesn't work with the netbios name. Though, I assume it's just a setting somewhere because the computers that kept their existing configurations files (upgraded) still connect fine.


In my case the 8.10 was an "upgrade," from 8.04 LT, and SMB is definitely broken.  I'm considering uninstalling samba and trying to do a clean reinstall.  Has anyone tried that?

---

### Post by david@reid-iba.com on 2008-11-13
I have the same problem but with a small variation. I don't know if this will shed any light on the problem. 

When I browse shares on my Windows network, I can see the folders but only MOST of them are blank showing 0 items. A couple of them do display correctly. Those that do display correctly only have a few files in them. The ones that don't display correctly have a large number of files in them. This may only be coincidence but I thought I'd mention it in case it helps. 

Other note: I have servers on the network running Windows and 3 Linux servers running Samba. When browsing SMB the failures occur regardless of the base OS. 

My install was an automatic upgrade from Heron. 

David

---

### Post by kimda on 2008-11-13
I think its an issue with gvfs. This connects with the samba shares in nautilus and gnome. With me I can connect with the samba server. Omly sometimes either I get a blank screen,  then I have reload several times to get all the shares. Or when a share is finally mounted through gvfs I can also get blank screens. But my biggest gripe isn't with this, its the fact that theres no good support in openoffice for gvfs. It causes all kinds of problems. I used to enter my username/password every time I saved a file or opened a file. Now I use a hack which openes the files through .gvfs in my home dir. But I really hope these issues will be resolved soon.  ](*,)

---

### Post by david@reid-iba.com on 2008-11-13
> **david@reid-iba.com said:**
> I have the same problem but with a small variation. I don't know if this will shed any light on the problem. 

When I browse shares on my Windows network, I can see the folders but only MOST of them are blank showing 0 items. A couple of them do display correctly. Those that do display correctly only have a few files in them. The ones that don't display correctly have a large number of files in them. This may only be coincidence but I thought I'd mention it in case it helps. 

Other note: I have servers on the network running Windows and 3 Linux servers running Samba. When browsing SMB the failures occur regardless of the base OS. 

My install was an automatic upgrade from Heron. 

David

I forgot to mention that in Hardy Heron I had a similar problem but would get the error message indicating that there was no application associated with the file type when attempting to open the folders. After the upgrade I just see empty folders.

---

### Post by chiefchief on 2008-11-14
Hey all, I have this very frustrating problem on three boxes as well.  My workaround was just to mount via the FSTAB.  You do the work once, you never have to think about it again.  Still doesn't solve anything when it come to non-permanent shares, but it's a sigh of relief if you own a NAS.

Take a look at this guide:  [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

But remember to run the symbolic linking at the bottom of the guide FIRST.  It'll save you a headache, as I haven't found a single system yet that doesn't hang on shutdown after mounting via CFS in the FSTAB: [https://help.ubuntu.com/community/MountWindowsSharesPermanently#System%20Hangs%20on%20Shutdown](https://help.ubuntu.com/community/MountWindowsSharesPermanently#System%20Hangs%20on%20Shutdown)

Hope that helps some people.

---

### Post by wesswei on 2008-11-15
Similar but not exactly the same problem...

Places > Network > Windows Network > (Blank Page in Nautilus) "0 Items"

I can connect to shares manually or thru fstab. Previously I created a script for myself to automatically log me on to my permanent share upon loading (don't like my private share to automatically load with fstab at boot).

Browsing manually also works, ie smb://192.168.0.x brings up the share folders.

Recently upgraded from 8.04 also. Mainly a pretty smooth upgrade compared to recent upgrades. I only lost boot splash screens and this! ...that I know of. Everything else seems hunky dory. 

w

---

### Post by jwilentz on 2008-11-17
How are you manually connecting?  When I try that smb://192.168.0.x I get an error message saying that FF doesn't have an app to handle the smb call.

---

### Post by Loan_Refi on 2008-11-18
I'm having the same problem. I can no longer browse my by clicking network, computers ans see shared folders

Problem occurs when trying to connect to;

Windows Server 2003 SP2
Vista Enterprise SP1

XP Professional Version 2002 SP3 - This Works fine, I can brows my network by clicking on windows network, computer name and I can see and access the shared files.

I have no problem accessing the shared folders this way;
smb://<IP Address>/ShareName/

I get the authentication prompt with no problem.

I have read and searched for a solution for this issue with no success.  I'm starting to think MS Windows updates have something to do with it. I will test on a fresh new install Win Server 2003, Vista Enterprise and see if the problem is present.

Any suggestions?

---

### Post by jwilentz on 2008-11-18
where are you writing that smb command?  When I write it in the firefox box, it will not work at all.  Running Xubuntu 8.10 and firefox 3.03 for linux.

---

### Post by HarshReality on 2008-11-18
> **Loan_Refi said:**
> I'm having the same problem. I can no longer browse my by clicking network, computers ans see shared folders

Problem occurs when trying to connect to;

Windows Server 2003 SP2
Vista Enterprise SP1

XP Professional Version 2002 SP3 - This Works fine, I can brows my network by clicking on windows network, computer name and I can see and access the shared files.

I have no problem accessing the shared folders this way;
smb://<IP Address>/ShareName/

I get the authentication prompt with no problem.

I have read and searched for a solution for this issue with no success.  I'm starting to think MS Windows updates have something to do with it. I will test on a fresh new install Win Server 2003, Vista Enterprise and see if the problem is present.

Any suggestions?

I'll wager after that prompt you get to look at a clean white wall when using that lil smb:// link.

---

### Post by WrathofthePenguin on 2008-11-18
The bug I submitted:

[https://bugs.launchpad.net/bugs/292836](https://bugs.launchpad.net/bugs/292836)

 was marked as a duplicate of another:

[https://bugs.launchpad.net/bugs/282298](https://bugs.launchpad.net/bugs/282298)

The patch which fixes this bug is posted here:

[https://launchpad.net/~tcarrez/+archive](https://launchpad.net/~tcarrez/+archive)

And it resolved the problem completely for me.

---

### Post by HarshReality on 2008-11-18
Wonderful.. now if that included direction on how to apply the patch I'd be tickled pink.

---

### Post by WrathofthePenguin on 2008-11-18
Sorry - you are right, it's not very obvious.

In Synaptic Package Manager, go to Settings->Repositories

Under the Third-Party Software tab, click on Add.

Enter the following:

> deb [http://ppa.launchpad.net/tcarrez/ubuntu](http://ppa.launchpad.net/tcarrez/ubuntu) intrepid main

and Click on Add Source.

You can reload and the update shows up for samba (there will be a little star showing for Samba. You can click and upgrade. Do all the upgrades and make sure there aren't others for Samba afterward.

---

### Post by HarshReality on 2008-11-18
> **WrathofthePenguin said:**
> Sorry - you are right, it's not very obvious.

In Synaptic Package Manager, go to Settings->Repositories

Under the Third-Party Software tab, click on Add.

Enter the following:

deb [http://ppa.launchpad.net/tcarrez/ubuntu](http://ppa.launchpad.net/tcarrez/ubuntu) intrepid main

and Click on Add Source.

You can reload and the update shows up for samba (there will be a little star showing for Samba. You can click and upgrade. Do all the upgrades and make sure there aren't others for Samba afterward.

Confirmed.. using Synaptic I did search for Samba returned six packages. Marked all for upgrade and installed. Rebooted and now I can get to my NAS... thank you VERY much!

---

### Post by deepee_oz on 2008-11-18
Thanks very much for that! I spent hours trying to work through the issue before reading your post. 
Works a treat!

---

### Post by GoodPanos on 2008-11-19
:lolflag:

I am so happy!  Thank you WrathofthePenguin!

I'll mark the post as solved.

---

### Post by MockY on 2008-11-19
This solved some of the issues. Any XP machine can be accessed just fine now, but no Windows 2003 Server machines can. It's the same ol' issue with those (Pre Hardy can access them just fine). Either way, this fix is half the battle.

Thanks you for a great post.

---

### Post by WrathofthePenguin on 2008-11-19
I realized that I'd left something important out of my post. After you upgrade Samba with the patch you should go back in and remove this source from Synaptic. The reason is that any other patches that get posted there will be shown as updates on your system. Removing it as a source after updating Samba will not remove the update.

I'm going to test Mocky's problem against this - I suspect (as I've said before) that there could be a couple of problems.

Update: Ok, I tested a share to a 2003 Windows Server and had no problem - the inability to connect to a Windows 2003 share must be a separate problem.

---

### Post by geokok1981 on 2008-11-19
When will this patch be an official update?
I really do not want to start messing with patches 
in the wild...

---

### Post by WrathofthePenguin on 2008-11-19
> **geokok1981 said:**
> When will this patch be an official update?
I really do not want to start messing with patches 
in the wild...

That's a good question - I have no idea. I'm going to do a little more testing tonight and then post a comment to the bug with success/failure. If I hear something I will gladly post the information (for a nominal fee, of course).

---

### Post by ignacio69 on 2008-11-20
I believe that where you put intrepid, I should overwrite "hardy", because is for 8.04, L.T.S. am I right?

> **WrathofthePenguin said:**
> Sorry - you are right, it's not very obvious.

In Synaptic Package Manager, go to Settings->Repositories

Under the Third-Party Software tab, click on Add.

Enter the following:

deb [http://ppa.launchpad.net/tcarrez/ubuntu](http://ppa.launchpad.net/tcarrez/ubuntu) intrepid main

and Click on Add Source.

You can reload and the update shows up for samba (there will be a little star showing for Samba. You can click and upgrade. Do all the upgrades and make sure there aren't others for Samba afterward.

---

### Post by dmizer on 2008-11-20
> **ignacio69 said:**
> I believe that where you put intrepid, I should overwrite "hardy", because is for 8.04, L.T.S. am I right?

No, the title of the thread is, "Problem Browsing Network Folders Ubuntu [COLOR="Red"]8.10[/COLOR]"

---

### Post by HDTimeshifter on 2008-11-20
> **WrathofthePenguin said:**
> Sorry - you are right, it's not very obvious.

In Synaptic Package Manager, go to Settings->Repositories

Under the Third-Party Software tab, click on Add.

Enter the following:

deb [http://ppa.launchpad.net/tcarrez/ubuntu](http://ppa.launchpad.net/tcarrez/ubuntu) intrepid main

and Click on Add Source.

What if the Add Source button stays dimmed?  Do I have a permissions problem?  Is there a way to do this from the teminal (sudo)?

Edit:  never mind.  I got it to work by copying that entire line.  For some reason, copying the URL, then appending " intrepid main" would not activate the button.

---

### Post by WrathofthePenguin on 2008-11-20
> **HDTimeshifter said:**
> What if the Add Source button stays dimmed?  Do I have a permissions problem?  Is there a way to do this from the teminal (sudo)?

Edit:  never mind.  I got it to work by copying that entire line.  For some reason, copying the URL, then appending " intrepid main" would not activate the button.

Ah - I should change it to make it a little clearer - the url makes it look like that's what you should enter.

---

### Post by HDTimeshifter on 2008-11-21
> **Loan_Refi said:**
> I'm having the same problem. I can no longer browse my by clicking network, computers ans see shared folders

Problem occurs when trying to connect to;

Windows Server 2003 SP2
Vista Enterprise SP1

XP Professional Version 2002 SP3 - This Works fine, I can brows my network by clicking on windows network, computer name and I can see and access the shared files.

I have no problem accessing the shared folders this way;
smb://<IP Address>/ShareName/

I get the authentication prompt with no problem.

Did you get it to work with Vista?  How are you accessing the folders with the full IP address?  In the terminal window?  Internet browser?  I still get a blank window in Nautilus when I try to access Vista, but XP works.  I tried the fully qualified address with IP address in both a terminal and Firefox, but neither works either.  I got my Virtualbox XP set up so I can see all my Windows PCs (XP and Vista) from it.  However, I can't access my Ubuntu share from it, and I can't access my Virtualbox XP share from Ubuntu.  That makes it rather hard to copy files between Ubuntu and Virtualbox on the same hard disk!

---

### Post by framirez on 2008-11-21
The same thing here.  Everything was OK in 8.04, but after the upgrade, folders show blank

---

### Post by David Samuels on 2008-11-23
I am having a similar problem -- see [https://answers.launchpad.net/ubuntu/+source/samba/+question/50441](https://answers.launchpad.net/ubuntu/+source/samba/+question/50441) -- and had hopes that your solution would work for me. Sadly, that isn't the case.

---

### Post by jwilentz on 2008-11-24
OK,  this is a bug in the samba library for 8.10, and I have solved it by regressing to libsmbclient from 8.04 Hardy.  This is done by adding the Hardy repository to one's software sites in System > Software sources, then under Third Party Software add or enable the Canonical.com/ubuntu hardy partner.  Once that's done go to the Synaptic Package Manager and look for libsmbclient.  You will find (if you have 8.10) that the version is 2:3.2.3-1.  Click on the install box and then go up to Package (on the menu bar) and select force version and get version 3.0.28a-1ubuntu4.4.  Hit Apply (it will uninstall an unneeded file (I think) called gvfs-backends) and then you'll have a working version.  To make sure Update Manager doesn't keep trying to change you back to 8.10, go back in Synaptic Package Manager select the libsmbclient again, go to Package on the menu bar and select "Lock Version."  Now you're done and fusesmb and samba should work as desired to allow Thunar or other browsing of allowed Windows network shares.

Not my original idea.  Found it somewhere else in these fora, but it does work.  I wonder why the folks who created the new Samba package don't fix it?????????

JR
:guitar:

---

### Post by creynolds on 2008-11-25
Discovered by accident. Well not really since I'm a risk taker. Install the application Smb4k The SMB/CIFS Share Browser. It said it was for KDE but, I tried it anyway and it works flawlessly.

---

### Post by sinofemp on 2008-11-25
same problem here....
[http://ubuntuforums.org/showthread.php?t=991927]("http://ubuntuforums.org/showthread.php?t=991927")

somebody please help...

---

### Post by HDTimeshifter on 2008-11-25
> **jwilentz said:**
> OK,  this is a bug in the samba library for 8.10, and I have solved it by regressing to libsmbclient from 8.04 Hardy...

I've been unable to browse Vista shares in Nautilus since 8.04.  I was told they would fix the problem when 8.10 was released, but it is still a problem after upgrading to 8.10, so I don't see how regressing to 8.04 will fix it.

---

### Post by Samizdata on 2008-11-25
> **WrathofthePenguin said:**
> Sorry - you are right, it's not very obvious.

In Synaptic Package Manager, go to Settings->Repositories

Under the Third-Party Software tab, click on Add.

Enter the following:



and Click on Add Source.

You can reload and the update shows up for samba (there will be a little star showing for Samba. You can click and upgrade. Do all the upgrades and make sure there aren't others for Samba afterward.

I tried this and did not see any upgrades available.  Any suggestions?

---

### Post by arcibaldo on 2008-11-26
Hello

I myself to the list of users that Ubuntu 8.10 fails to manage its samba NAS iTek 3N1 (Max-Power Landisk clone) same problems with nautilus, while FTP does everything including other shares PC-M$.
Unfortunately, the problem lies in the Samba package and in particular in the library libsmbclient. The confirmation is on the Official List Bug.

Check that, for the most experienced, it may be forced to replace with the new version of this library in the official repository of distribution Ubuntu 8.04 Hardy.
I tried and I confirm that I managed to navigate to the folder, and upload files of various kinds!

Warning ... replacing the existing library involves the removal of several applications Dependencies and type Nautilus ... then the council not to those who must maintain a stable throughout the entire personal data ... To be Warned!

P.S. We hope that it will soon exit in a fix to the problem ... :guitar:

---

### Post by ahood on 2008-11-27
I too was having the problem of Nautilus failing to display files and folders of a Windows shared network folder after installing Intrepid. Note that it wasn't a problem in Hardy. 

The problem is fixed after I applied the latest updates (as of 3:04 AM US EST), which included an update to smbclient.

I hope others find the solution to be as simple as applying the latest Intrepid update.

Al

---

### Post by GoodPanos on 2008-11-27
For those of you who have not applied the patches yet, I believe it might be included in the latest official updates that were just released.  Today I got some upgrades and it included some (I'm not sure if all of them) of the samba files I had patched.  Still works.

So, try those updates before doing anything.

Edit: Indeed that is the case.  I posted this message literally while ahood posted his.

---

### Post by dmizer on 2008-11-27
> **HDTimeshifter said:**
> I've been unable to browse Vista shares in Nautilus since 8.04.

Heh, I've been using Ubuntu since Warty, and I've never been able to get reliable network browsing through nautilus.

WrathofthePenguin, would you mind writing up a formal howto for your fix and submitting it to the forum Tutorials & Tips: [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

Thanks.

---

### Post by ahood on 2008-11-27
> **GoodPanos said:**
> Edit: Indeed that is the case.  I posted this message literally while ahood posted his.

Too funny!

:)

---

### Post by notbitmonk on 2008-11-27
Well, the updates didn't work for me.  I'm still unable to access the NAS through Samba.  The manufacturer sent me a firmware update for the NAS but it didn't work.  I am able to access the NAS through ftp so the problem still lies with Samba.  I asked the manufacturer what version of Samba they use.  See if that info can shed some light.

---

### Post by arcibaldo on 2008-11-27
Hi

Also for me ... Today with the last update "Samba 2:3.2.3.-1ubuntu3.3" (intrepid-security) ....

Nothing solved ... My problem persist :confused:

NAS FTP Storage is OK ...
Other Local and Network PC Shared Folder with M$ (Vista & XP) is OK
NAS SMB Storage is NOT (with M$ O.S. is OK)

Network-Workgroup-Landisk (see inside Folders but when open browser some of them return to see a Folder-Home of my system) ... :mad:



Cheers :guitar:

---

### Post by caribconsult on 2008-11-27
Same problem here...I've tried every suggestion in this thread and I still cannot see my WinNet shared resources from the net file mgr of Ubuntu UNLESS I am logged in as 'root'.  What gives here?  I was pretty impressed with this OS until I ran into this issue, which is a slam dunk in other systems, but here I have already downloaded more patches than I can count, issued many commands from the terminal window and still, the file sharing does not work correctly.  Doesn't anyone at Ubuntu prowl these forums and pay attention to this stuff?  Some readers report that this feature worked correctly on earlier versions of Ubuntu, so what happened here?

---

### Post by WrathofthePenguin on 2008-11-27
> **dmizer said:**
> Heh, I've been using Ubuntu since Warty, and I've never been able to get reliable network browsing through nautilus.

WrathofthePenguin, would you mind writing up a formal howto for your fix and submitting it to the forum Tutorials & Tips: [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

Thanks.

I would be happy to.

---

### Post by Flos Headford on 2008-11-28
I, too, have been unable to see Windows Shares using nautilus, even with the latest updates.
Phil Headford

---

### Post by ecarter on 2008-11-28
Similar problem although confined to NAS Landisk access over Samba. 
No joy with Ibex - Dolphin, Konqueror at least report that the "SMB protocol has unexpectedly died" - Nautilus just drops back to the local home directory. Funny because access to other Linux machines and Vista is OK 
No problems on Heron on Konquerer and I will stick with that until this one gets resolved. However, Nautilus on Heron does seem to loose access after a few minutes of no use and directory has to be remounted to gain access. Leaves me wondering about the Samba protocol on the NAS Landisk.

---

### Post by ecarter on 2008-11-28
removed

---

### Post by geekyhawkes on 2008-11-28
Im pretty sure this issue isnt solved.  I have all of the latest updates and still have the issues described above.  I can see the smb shares in both Nautilus and the terminal but cannot get any closer to my files.

The NAS remains available at all times via FTP or its web interface.  Anyone got any good ideas on how we can get this issue solved?

---

### Post by geekyhawkes on 2008-11-29
Is anyone else still having these issues or is it just me left? Im sure ive installed all of the updates in this thread, but am still having smb issues with my freecom nas

---

### Post by geekyhawkes on 2008-11-29
Double post sorry

---

### Post by geekyhawkes on 2008-11-29
Edit: Right ive downloaded the Smb user guide and I have found the following activity in 8.10 that doesnt happen in 8.4;

If you connect to your NAS from a terminal via smbclient //FND/Public (//servername or ip/share) then all goes well in both 8.4 and 8.10 at the smb: \> prompt in 8.4 if type dir then you get a full dir list as you would expect. In 8.10 dir at the smb prompt returns the following "Segmentation fault" and then closes your smbclient connection. Hopefully someone with more knowledge than me will find this useful and move us on.

---

### Post by geekyhawkes on 2008-11-30
Am i the only person that this issue is still effecting?

---

### Post by alicemoon on 2008-11-30
> **geekyhawkes said:**
> Am i the only person that this issue is still effecting?

no you are not I cannot see any of my windows network - I have 2 PC's and a laptop - all viewable when booted int XP but not visible in Ibex - do we need to start a new thread if this is marked as solved?

---

### Post by geekyhawkes on 2008-11-30
Maybe.  Il stay watching this thread tonight, if nothing much turns up then i will repost a new thread with as many details as i can. Its reasuring im not the only one having issues, although that clearly doesnt help you out bud!

---

### Post by arcibaldo on 2008-11-30
Hello

Since none of the maintenance group, gave an answer to this! :(

I think it is necessary to include the specific problem to the list of Bugs in "Samba" through the official channel ... [**[COLOR="Gray"]launch[/COLOR][COLOR="Orange"]pad[/COLOR]**]("https://bugs.launchpad.net/ubuntu/+source/samba/") 

Cheers :guitar:

---

### Post by matthewboh on 2008-11-30
I don't know if this is related but I'm having terrible problems using OpenOffice 3.0 and my files on a Samba share.  Right now, I have to open the files through Nautilus - but then OO 3.0 just kind of crashes.

I'm running Ubuntu 8.10 on my laptop, with Samba Version 3.23 on a server running Ubuntu 8.04

---

### Post by jocatoth on 2008-11-30
i just upgraded ubuntu 7.10 to ubuntu 8.04. i have noticed that a network drive appears twice on my desktop, once in a folder which was created to mount a network drive into and once in a drive icon. both work fine to access the network drive. the duplication is unnecessary. i would like to clear up my misunderstanding of the fstab way of mounting a network shared drive.

the relavant entry in the fstab appears in the following format:

//Whitebox/Black /home/john/Desktop/White_Black cifs exec,uid=john,gid=users,ip=192.168.1.125 0 0

it would seem that network drives are handled differently in 8.04. so i am not sure how to mount and use network drives properly. perhaps someone could point me in the right direction. thanks 

i just saw your entry in this forum while i had this placed in installation and upgrade. hope this helps if you are still working on this networking problem.

---

### Post by HDTimeshifter on 2008-11-30
> **arcibaldo said:**
> Hello

Since none of the maintenance group, gave an answer to this! :(

I think it is necessary to include the specific problem to the list of Bugs in "Samba" through the official channel ... [**[COLOR="Gray"]launch[/COLOR][COLOR="Orange"]pad[/COLOR]**]("https://bugs.launchpad.net/ubuntu/+source/samba/") 

Cheers :guitar:

I already submitted the Nautilus browsing Vista shares problem as a bug:  [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/303299]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/303299").  They already replied, but since I have very limited knowledge of Samba, need to research Samba some before I can reply.  All I know is Nautilus doesn't work, irrespective of anything I've tried to do in Samba.  As far as I know, smbclient isn't a GUI, and I'm trying to figure out the command line options and can't figure out the non-IP naming some of the command line options need.

---

### Post by arcibaldo on 2008-12-01
Hi

I think that the problem is not linked only to Nautilus! 

To me the only browser NAS (see dir tree but not on subdir) does not work with any program file manager, connection to the server and including the display smb: //xxx.xxx.xxx.xxx on firefox .... 

However, I can just send details on the log daemon smbclient (-L-B) ... 

Regards

---

### Post by matthewboh on 2008-12-01
Just a follow-up to my issue - having problems with OpenOffice and Samba drives and my files getting corrupted and OO crashing - 

Someone suggested I mount the Samba shares as filetype cifs - which seems to fix it, but there seems to be another problem.  I had wanted the system to just pick up the userid but I wanted to use guest so the password wouldn't have to be entered - but I kept getting a security violation.  Here's my command 

```
sudo mount.cifs //ubuntu/Business /media/samba -o sec=none
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

and I tried

```
sudo mount.cifs //ubuntu/Business /media/samba -o guest
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

So, I added in the username and password information and it seems to work with OpenOffice fine now.

---

### Post by arcibaldo on 2008-12-01
Example of my smbclient DEBUG:

First - Label Usage:
```
arci@arci-laptop:~$ smbclient --usage
Usage: smbclient [-?EgBVNkPe] [-?|--help] [--usage] [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST] [-t|--terminal=CODE] [-m|--max-protocol=LEVEL]
        [-T|--tar=<c|x>IXFqgbNan] [-D|--directory=DIR] [-c|--command=STRING] [-b|--send-buffer=BYTES] [-p|--port=PORT]
        [-g|--grepable] [-B|--browse] [-d|--debuglevel=DEBUGLEVEL] [-s|--configfile=CONFIGFILE]
        [-l|--log-basename=LOGFILEBASE] [-V|--version] [-O|--socket-options=SOCKETOPTIONS] [-n|--netbiosname=NETBIOSNAME]
        [-W|--workgroup=WORKGROUP] [-i|--scope=SCOPE] [-U|--user=USERNAME] [-N|--no-pass] [-k|--kerberos]
        [-A|--authentication-file=FILE] [-S|--signing=on|off|required] [-P|--machine-pass] [-e|--encrypt] service <password>
arci@arci-laptop:~$ 

```

Test 1 on my NAS (Landisk IP 192.168.1.13)

```
arci@arci-laptop:~$ smbclient --list=192.168.1.13
Enter arci's password: 
Domain=[&#519;] OS=[] Server=[&#65533;&#65533;&#65533;]

	Sharename       Type      Comment
	---------       ----      -------
	Film            Disk      
	Musica          Disk      
	Foto            Disk      
	Documenti       Disk      
	XBOX            Disk      
	WD              Disk      
	Backup          Disk      
	Elettronica     Disk      
	PUBLIC          Disk      
	HDD-D           Disk      
	PSP             Disk      
	IPC$            IPC       
Domain=[&#519;] OS=[] Server=[&#65533;&#65533;&#65533;]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

```

Test 2 on my NAS (test resolve Landisk name)

```
arci@arci-laptop:~$ smbclient -L \\Landisk
Enter arci's password: 
Domain=[&#519;] OS=[] Server=[&#65533;&#65533;&#65533;]

	Sharename       Type      Comment
	---------       ----      -------
	Film            Disk      
	Musica          Disk      
	Foto            Disk      
	Documenti       Disk      
	XBOX            Disk      
	WD              Disk      
	Backup          Disk      
	Elettronica     Disk      
	PUBLIC          Disk      
	HDD-D           Disk      
	PSP             Disk      
	IPC$            IPC       
Domain=[&#519;] OS=[] Server=[&#65533;&#65533;&#65533;]

	Server               Comment
	---------            -------

	Workgroup            Master

	---------            -------

```

Test 3 - Try to brows a sub dir (/Landisk/Film)

```
arci@arci-laptop:~$  smbclient //Landisk/Film/ -N -U
Domain=[&#519;] OS=[] Server=[&#65533;&#65533;&#65533;]

smb: \> help
?              allinfo        altname        archive        blocksize      
cancel         case_sensitive cd             chmod          chown          
close          del            dir            du             echo           
exit           get            getfacl        hardlink       help           
history        iosize         lcd            link           lock           
lowercase      ls             l              mask           md             
mget           mkdir          more           mput           newer          
open           posix          posix_encrypt  posix_open     posix_mkdir    
posix_rmdir    posix_unlink   print          prompt         put            
pwd            q              queue          quit           rd             
recurse        reget          rename         reput          rm             
rmdir          showacls       setmode        stat           symlink        
tar            tarmode        translate      unlock         volume         
vuid           wdel           logon          listconnect    showconnect    
..             !              

smb: \> listconnect
0:	server=Landisk, share=Film

smb: \> showconnect
//Landisk/Film

smb: \> logon
logon <username> [<password>]

smb: \> logon xxxxxx xxxxxxx
Current VUID is 0

smb: \> ls
cli_list_new: Error: unable to parse name from info level 1
Segmentation fault

or 

smb: \> dir
cli_list_new: Error: unable to parse name from info level 1
Segmentation fault
arci@arci-laptop:~$
```

Another Test Landisk (default port map 137 to 139):

```
arci@arci-laptop:~$ smbclient //Landisk/Film/ -N -d3

lp_load_ex: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=fe80::20e:35ff:fe49:db52%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.3 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 3.2.3).
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permesso negato
resolve_lmhosts: Attempting lmhosts lookup for name Landisk<0x20>
resolve_wins: Attempting wins lookup for name Landisk<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name Landisk<0x20>
resolve_hosts: getaddrinfo failed for name Landisk [Nessun indirizzio associato con l'hostname]
name_resolve_bcast: Attempting broadcast lookup for name Landisk<0x20>
Got a positive name query response from 192.168.1.13 ( 192.168.1.13 )
Connecting to 192.168.1.13 at port 445
error connecting to 192.168.1.13:445 (Connessione rifiutata)
Connecting to 192.168.1.13 at port 139
Domain=[&#519;] OS=[] Server=[&#65533;&#65533;&#65533;]
dos_clean_name [(null)]
smb: \> dir
cli_list_new: Error: unable to parse name from info level 1
Segmentation fault
arci@arci-laptop:~$ 


```

Good Test with another client of My-Net workgroup-share (My daughter Claudia with M$-XP)::)
```
arci@arci-laptop:~$ smbclient //pc-claudia-xp/Video/ -N -d3
lp_load_ex: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=fe80::20e:35ff:fe49:db52%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.3 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 3.2.3).
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permesso negato
resolve_lmhosts: Attempting lmhosts lookup for name pc-claudia-xp<0x20>
resolve_wins: Attempting wins lookup for name pc-claudia-xp<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name pc-claudia-xp<0x20>
resolve_hosts: getaddrinfo failed for name pc-claudia-xp [Nessun indirizzio associato con l'hostname]
name_resolve_bcast: Attempting broadcast lookup for name pc-claudia-xp<0x20>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: Nessun file o directory
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: Nessun file o directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: Nessun file o directory
Connecting to 192.168.1.2 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[PC-CLAUDIA-XP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
dos_clean_name [(null)]
smb: \> dir
received 8 entries (eos=1)
  .                                  DR        0  Mon Sep  8 13:52:28 2008
  ..                                 DR        0  Mon Sep  8 13:52:28 2008
  careless_cartoon.mp4                A  9151530  Sat Aug 30 22:03:24 2008
  ddfashionrocks512.mp4               A 21503105  Sat Aug 30 22:22:29 2008
  Desktop.ini                       AHS      180  Thu May 22 01:16:21 2008
  Desperate housewives.mp4            A 21911204  Sun Aug 31 16:13:28 2008
  DivX Movies                         D        0  Thu May 22 01:16:21 2008
  Roger DJ's pt 1 (Cut to Klaus' audio).mp4      A  4934922  Mon Sep  8 13:56:48 2008

		33751 blocks of size 4194304. 12582 blocks available
Total bytes listed: 57500941
smb: \> 


```


Cheers :guitar:

---

### Post by coskierken on 2008-12-01
Hi All!  I was having the same problem and probably lost a little hair over it.  I can see my Window shares, but they won't load immediately into Nautilus.  I tried all the updates and apparently have them all, but still no go.  To see them, I put the path in the Nautilus text bar as smb://192.168.1.xx (whatever your IP is).  I then bookmarked it.  The thing I learned was the WINS in windows has to be set up manually with the ip of the Intrepid box.  I then can browse the drive I share through XP.  I only have smbclient loaded and not server.  It is all I really need just to share files on the XP machine.  

Just my personal experience through research, trial, error, frustration and then alcohol!:)  Hope this helps a little.

---

### Post by arcibaldo on 2008-12-01
> **coskierken said:**
> 

Just my personal experience through research, trial, error, frustration and then alcohol!:)  Hope this helps a little.

Hi 

Alcohol !!! :(   No ... is better a cup of good coffee or tea :)

	
**Thanks to** **[COLOR="Red"]dmizer[/COLOR]**

... I temporarily resolve with [**[COLOR="RoyalBlue"]Mount samba shares with utf8 encoding using cifs[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=288534") ... and **[COLOR="Red"]nounix[/COLOR]** option ... :)

Regards

---

### Post by Flos Headford on 2008-12-19
Sorry, could not display all the contents of "WindowsShareName on ComputerID": Connection timed out.

I'm still getting the above message. I can transfer files between machines if I sit a Windows machine, but not if I'm using the Linux machine. Bloody exasperating, innit?

It's now 19 Dec '08. Anyone heard of any movement to correct the problem?

Phil.

---

### Post by matthewboh on 2008-12-19
You might want to start a new thread - this one is marked solved - and it seems like there's about three different problems running through here.  I was having an OpenOffice issue, sounds like you're having a Samba issue.

---

### Post by wincen on 2008-12-28
I installed the update from Post 81 which were supposed to solve the problem with browsing.  It did not work for me though smbclient still works.  How do I remove these updates?

---

### Post by HeinzVoerbakje on 2009-01-07
I'm having the same problem, though it only showed up after a certain upgrade of Samba. I cannot access any Samba shares, neither from the server itself when browsing the network, neither from an other (windows) client. It's strange as it did work until that fateful update.

The error I get is 'Failed to mount windows share'.

Samba's log (var/log/samba/log.heinzvoerbakje) says:

[2009/01/07 23:39:00,  0] smbd/service.c:make_connection_snum(1156)
  '/home/myname/share' does not exist or permission denied when connecting to [share] Error was Permission denied

The usershares in /var/lib/samba/usershares says for this folder:

#VERSION 2
path=/home/myname/share
comment=
usershare_acl=S-1-1-0:R
guest_ok=y

Who has any clue?

Thanks, HeinzVoerbakje

---

### Post by WIVO_Riley on 2009-01-07
C'mon any help here yet?

Can see my network, but then upon getting to my shares, nothing is shown and I get the same error as above.

Even tried Nautilus to smb://192.16x.x.x over to it, but get the same result.

I've never had this problem before- I had my ubuntu machine using network (windows) attached printers, etc.  

Anyone have an idea here?

Thanks in advance.

---

### Post by dmizer on 2009-01-07
> **WIVO_Riley said:**
> C'mon any help here yet?

This thread is marked solved. People browsing through the forum assume that the problem is fixed and that a reply is not necessary.

Since the thread is marked solved, you may be able to search through this thread to find a solution for your problem. If you cannot, then you're probably better off starting a new thread.

---

### Post by mecca_spy on 2009-01-20
thx, man for solution!
i am so happy,:D

---

### Post by arcibaldo on 2009-01-27
Hello :D

I'm sorry for thread reopen ... but it should be noted that ...

With the Samba 2:3.2.3.-1ubuntu3.5  intrepid-update

the problem of the NAS browsering was resolved ... :popcorn:

Thank's to development team ...

cheers

---

### Post by wincen on 2009-02-01
> 
With the Samba 2:3.2.3.-1ubuntu3.5 intrepid-update

the problem of the NAS browsering was resolved ... 

Great, I still have hope.  I'm running intrepid; when I look in synaptic I see I have samba-common 2:3.2.3-1ubuntu3.4 installed.

This may be a silly question, but how so I have it install 2:3.2.3.-1ubuntu3.5 intrepid-update?

From the CLI I generally just do the usual:
apt-get update
apt-get install

What am I missing?

---

### Post by ahood on 2009-02-03
After installing Intrepid about a month ago, I initially had the problem of viewing my network shares (SMB) using Nautilus. The original problem was that Nautilus in Intrepid could display the workgroup, it did not display the shared content (white space with no shared folders).

After a few updates via update manager, the problem seemed to get better. When the above problem would occur (shared content being absent in Nautilus), the shared folders would appear after pressing the 'Refresh' button in Nautilus several times.

With the latest updates from the past week or so, the problem has gone away and seems resolved on my Intrepid box. Today, Intrepid has no problem displaying shared content of the SMB network shares.

I did not apply the fix described in post #81. I simply waited and installed the updates.

Still have to give it more time and see if this remains. So far so good.

Cheers.

DrH

---

### Post by ecarter on 2009-02-08
Thanks for that reminder arcibaldo. I tracked down the update and now, at long last, the Landisk works under Samba with Ubuntu Intrepid. I'm overjoyed.
To Wincen - I found this by including "intrepid-proposed" and "intrepid-backports" in the software

---

### Post by BLTicklemonster on 2009-03-04
Wow, this thread has my name written all over it. And I keep being told no one has problems with networking in ubuntu, it's something I'm doing wrong...

Subscribing to this thread for sure.

---

### Post by BLTicklemonster on 2009-03-04
I KNEW IT! God all mighty. I was doing fine, then last night I saw an update and clicked on it, and there was one for network manager, so I stupidded out and let it upgrade, and voila, my network will not work at all. I click network, and it shows Windows Network, but when I click on it, I see:

> Unable to mount location

Failed to retrieve share list from server

I knew better than to upgrade!!!!

There were other things in the upgrade, too, not sure if they were network related also. 

Is there any way to undo the changes made by updating?

---

### Post by BLTicklemonster on 2009-03-04
> **WrathofthePenguin said:**
> Sorry - you are right, it's not very obvious.

In Synaptic Package Manager, go to Settings->Repositories

Under the Third-Party Software tab, click on Add.

Enter the following:



and Click on Add Source.

You can reload and the update shows up for samba (there will be a little star showing for Samba. You can click and upgrade. Do all the upgrades and make sure there aren't others for Samba afterward.

I update, and get this:

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E82979A648A08ED
W: You may want to run apt-get update to correct these problems

```

And there's no useful information that I can find that tells me where to get the key.

---

### Post by dmizer on 2009-03-04
> **BLTicklemonster said:**
> And there's no useful information that I can find that tells me where to get the key.

It's on launchpad in the FAQ: [https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system) ;)

---

### Post by BLTicklemonster on 2009-03-04
That's exactly gibberish by my reckonin', and was what I was talking about.

---

### Post by dmizer on 2009-03-04
> **BLTicklemonster said:**
> That's exactly gibberish by my reckonin', and was what I was talking about.

Perhaps you'd be more interested in this: [http://ubuntuforums.org/showthread.php?t=1086208](http://ubuntuforums.org/showthread.php?t=1086208)

---

### Post by chelrob on 2009-03-04
Hey dmizer.
Did that work for you?  It solved my problem.

---

### Post by BLTicklemonster on 2009-03-04
Oh, well, it's all good now. Adding that to the sources list did it, I guess. I had to go through and redo all my shares again, but it's all fine now. Well, except, and this is the oddest thing, I can share off a partition, but not from the partition that / is on. Dangdest thing. Probly something in smb.conf I can change, but what the heck, I'll just put stuff on other partitions to share if I have to, no problem.

---

### Post by skiwithpete on 2009-03-05
I'm also getting the error message that I need a key to access this repository, and I can't find the project page that has the key on it.  
I understand how to add a key, I just cant find the right one!

---

### Post by chelrob on 2009-03-05
> **skiwithpete said:**
> I'm also getting the error message that I need a key to access this repository, and I can't find the project page that has the key on it.  
I understand how to add a key, I just cant find the right one!

Try this:
[http://wiki.ubuntuforums.org/showthread.php?t=1056099](http://wiki.ubuntuforums.org/showthread.php?t=1056099)

---

### Post by Skatespeare on 2009-03-09
> **WrathofthePenguin said:**
> Sorry - you are right, it's not very obvious.

In Synaptic Package Manager, go to Settings->Repositories

Under the Third-Party Software tab, click on Add.

Enter the following:



and Click on Add Source.

You can reload and the update shows up for samba (there will be a little star showing for Samba. You can click and upgrade. Do all the upgrades and make sure there aren't others for Samba afterward.

thanks a lot mate! that did the trick :)

---

### Post by HDTimeshifter on 2009-04-01
Well, tonight I turned on my Vista laptop for the first time in months to make sure the virus files were up to date, and I was able to access it from the file browser (just had to enter username and password twice), so I guess one of the Ubuntu updates fixed the problem.

---

### Post by sbrandon on 2009-04-09
I guess to echo an earlier inquiry - why are we having to go thru all of these gyrations? Granted, we learn more about the system, but shouldn't this be as easy as joining the Domain/Workgroup function in XP? Being able to do what should be a standard network function off the bat should be a built in client function. The first time I installed 8.04 on a test box and plugged into our network jack I was able to install the network printer I use with XP, did not need to log into the Windows network, did not need to plug in a printer IP - CUPS just searched and came back with a list of network printers with their IPs.

I can now find my share server and see my hidden share$ but I cannot mount it using my network user name and password which is frustrating. If I were using this for the first time, I would think that I should be able to join the Domain, find my hidden share$ and operate as an XP box can.  Everything else about Ubuntu I love - especially that it is not MS.

---

### Post by bristolbadger23 on 2009-04-27
I have **wireshark** reports showing this in the only 2 states i see it...

Not ideal, but working in Nautilus by typing smb://ip.ad.re.ss of remote host...

and failing when trying to open a network place from the places menu...

[http://tinyurl.com/d26nal]("http://tinyurl.com/d26nal")

For the record, my Ubuntu host is 172.16.0.2 and my XP host is 172.16.0.1, directly connected via crossover...

ssh etc all works, cable etc are all sound.

Both computers are also connected via a couple of switches to a router...

All that is sound, and if I run Win7 on my Ubuntu machine that works peachy too...

---

### Post by Dr_Willis on 2009-05-05
Been reading this tread trying to solve some other problems.. But i think somthing is getting over looked here..


I to have issues 'browsing' the various servers and samba shares.. but what ive noticed is that i can simply enter the whole server/share name manually and i get to them every time. I then bookmark that :)


ie: I go to Places -> netsork, it shows all my servers  I click on one, for example the 'homes' share i have on   smb://black/ It refuses to mount it.. I know its shared as 'willis' so i just enter  smb://black/willis - it then asks for the user/password  

Seeing this work i tried it on my other nonhome shares. and it also worked.

I know its not good for when you dont rember the server/share names. But at least I can get to the ones I do know. 

There is also some console command to list all the shares/servers on the network. I learned it from the irc channel last week.. and of course now i cant rember it. :( 

Well hope this helps a little.

---

### Post by mgmiller on 2009-05-12
I maintain 2 networks with mixed ubuntu / Windows XP SP2 machines and this problem has not been resolved for me. All of my Ubuntu machines whether they are clean installs of 8.04 or 8.10 or 9.04, 32 or 64 bit or upgrades from earlier versions all exhibit the failure to display or browse smb shares.   DHCP or staic IP makes no difference.

The only fix is to edit etc/samba/smb.conf:
# What naming service and in what order should we use to resolve host names
# to IP addresses
 ; name resolve order = lmhosts host wins bcast
 remove the leading ; from the name resolve order line and change the order of the entries to read:
   name resolve order = lmhosts wins bcast host
 Save the file, log off and back on.
 

This change fixes the problem for all my machine in both networks.
The problem remains unresolved in clean installs of Jaunty unless I do this. This problem appeared suddenly in September of 2008 on 8.04 machines that had been working normally and has persisted through 8.10 and now 9.04.

---

### Post by blusa on 2009-05-24
> **mgmiller said:**
> I maintain 2 networks with mixed ubuntu / Windows XP SP2 machines and this problem has not been resolved for me. All of my Ubuntu machines whether they are clean installs of 8.04 or 8.10 or 9.04, 32 or 64 bit or upgrades from earlier versions all exhibit the failure to display or browse smb shares.   DHCP or staic IP makes no difference.

The only fix is to edit etc/samba/smb.conf:
# What naming service and in what order should we use to resolve host names
# to IP addresses
 ; name resolve order = lmhosts host wins bcast
 remove the leading ; from the name resolve order line and change the order of the entries to read:
   name resolve order = lmhosts wins bcast host
 Save the file, log off and back on.
 

This change fixes the problem for all my machine in both networks.
The problem remains unresolved in clean installs of Jaunty unless I do this. This problem appeared suddenly in September of 2008 on 8.04 machines that had been working normally and has persisted through 8.10 and now 9.04.

that's wonderful!!!
it works, after so many tries... thanks a lot \\:D/

---

### Post by armagedonc on 2009-07-18
> **mgmiller said:**
> I maintain 2 networks with mixed ubuntu / Windows XP SP2 machines and this problem has not been resolved for me. All of my Ubuntu machines whether they are clean installs of 8.04 or 8.10 or 9.04, 32 or 64 bit or upgrades from earlier versions all exhibit the failure to display or browse smb shares.   DHCP or staic IP makes no difference.

The only fix is to edit etc/samba/smb.conf:
# What naming service and in what order should we use to resolve host names
# to IP addresses
 ; name resolve order = lmhosts host wins bcast
 remove the leading ; from the name resolve order line and change the order of the entries to read:
   name resolve order = lmhosts wins bcast host
 Save the file, log off and back on.
 

This change fixes the problem for all my machine in both networks.
The problem remains unresolved in clean installs of Jaunty unless I do this. This problem appeared suddenly in September of 2008 on 8.04 machines that had been working normally and has persisted through 8.10 and now 9.04.



"Failed to mount windows share"
I already done that,it didn't solve my problem between
Jaunty an windows vista.

---

### Post by mgmiller on 2009-07-18
> "Failed to mount windows share"
I already done that,it didn't solve my problem between
Jaunty an windows vista.

Unfortunately, I have only ever gotten networking to function between Ubuntu and Windows XP.   I have never been able to get it to work with Vista or 7. 

I find Windows Vista/7 networking completely incomprehensible.  As near as I can tell, it will only easily network with itself, not other OS's.

I did mange to get an XP box to talk to a Vista box once, but there were a lot of hoops to jump through in both systems and I don't remember what they were.

This is one of the prime reasons why I continue to use only XP on the only machine at my business that has to run Windows.  All my other workstations are Ubuntu.

You could check this forum posting:
[http://ubuntuforums.org/showthread.php?t=1216169&highlight=file+sharing+vista](http://ubuntuforums.org/showthread.php?t=1216169&highlight=file+sharing+vista)

Or this posting:
[http://ubuntuforums.org/showthread.php?t=1172310&highlight=file+sharing+vista](http://ubuntuforums.org/showthread.php?t=1172310&highlight=file+sharing+vista)

Finally, have you tried by clicking on Places > Connect To Server and choosing Service Type: Windows Share?

Enter the IP address of the windows machine, rather than the name.

Good Luck.

---

### Post by jwilentz on 2009-08-08
> **mgmiller said:**
> I maintain 2 networks with mixed ubuntu / Windows XP SP2 machines and this problem has not been resolved for me. All of my Ubuntu machines whether they are clean installs of 8.04 or 8.10 or 9.04, 32 or 64 bit or upgrades from earlier versions all exhibit the failure to display or browse smb shares.   DHCP or staic IP makes no difference.

The only fix is to edit etc/samba/smb.conf:
# What naming service and in what order should we use to resolve host names
# to IP addresses
 ; name resolve order = lmhosts host wins bcast
 remove the leading ; from the name resolve order line and change the order of the entries to read:
   name resolve order = lmhosts wins bcast host
 Save the file, log off and back on.
 

This change fixes the problem for all my machine in both networks.
The problem remains unresolved in clean installs of Jaunty unless I do this. This problem appeared suddenly in September of 2008 on 8.04 machines that had been working normally and has persisted through 8.10 and now 9.04.

Unfortunately not for me, and I have duplicated this many times.  Whenever I don't pin libsmbclient to the 3.0.28a-1ubuntu4.8 version the fusesmb fails.  When  *go back to the earlier version it works fine. *This is *not* an smb.conf issue! :confused:

---

### Post by mgmiller on 2009-08-08
> Unfortunately not for me, and I have duplicated this many times. Whenever I don't pin libsmbclient to the 3.0.28a-1ubuntu4.8 version the fusesmb fails. When *go back to the earlier version it works fine. *This is *not* an smb.conf issue! :confused:

Have you checked to see if your ISP is using DNS redirection?  I discovered that that was the root of this whole problem, for me at least, and have filed a bug report about it.
[https://bugs.launchpad.net/bugs/389909](https://bugs.launchpad.net/bugs/389909)

---

### Post by jwilentz on 2009-08-08
I don't quite understand that.  This is within my personal WLAN and should never make it outside of my router???

---

### Post by jwilentz on 2009-08-08
Still doesn't explain why with the earlier version of libsmbclient it works perfectly!!!!!!

---

### Post by mgmiller on 2009-08-08
You could try submitting a bug report against the version that does not work for you.

---

### Post by jwilentz on 2009-08-08
> **mgmiller said:**
> You could try submitting a bug report against the version that does not work for you.
And while we're at it, I reverted the smb.conf file to the original commented out line with the preceding semicolon --
*;     name resolve order = lmhosts host wins bcast*

Now the system seems to work much faster and still flawlessly with the old version of libsmbclient.

How do I report this bug?  Also I think it has been reported and no one seems to care!! Boo hoo!!  Anyway my machine "works" this way, but it's no way to run a railroad.  Perhaps a Lionel or HO train as a hobby, but nothing that people depend on!!  For that I'll stick with my WinXP box and my son's MacOSX.

---

### Post by dmizer on 2009-08-08
> **jwilentz said:**
> Anyway my machine "works" this way, but it's no way to run a railroad.  Perhaps a Lionel or HO train as a hobby, but nothing that people depend on!!  For that I'll stick with my WinXP box and my son's MacOSX.

A real rail road that a company depends on would have a local DNS server where this would not be a problem. The fix is needed because your home network is a Lionel or HO hobby, so samba needs to be configured to handle name resolution on its own.

---

### Post by jwilentz on 2009-08-09
> **dmizer said:**
> A real rail road that a company depends on would have a local DNS server where this would not be a problem. The fix is needed because your home network is a Lionel or HO hobby, so samba needs to be configured to handle name resolution on its own.

Oohh, burn!  That was a little harsh.  :P

But getting back to the facts, with the same Linksys router and the WinXP server having a static IP with the rest on DHCP, and everything working great prior to Hardy update, I changed nothing except going to 8.10 and trying 9.04.  But I have isolated the problem to the libsmbclient version.  With what you call my Lionel or HO networking and the libsmbclient from the earlier version pinned and everything else 8.10, samba works wonderfully *without* "The fix" suggested to overcome the DNS redirection problem.  It's only when I "upgrade" libsmbclient to the current version that the system will not mount the WinXP shares.  So I respectfully suggest that this is a bug in libsmbclient from 8.10 on.  And it would be a great boon to fix it.

---

### Post by mgmiller on 2009-08-09
> So I respectfully suggest that this is a bug in libsmbclient from 8.10 on.  And it would be a great boon to fix it.[https://bugs.launchpad.net/bugs/+filebug](https://bugs.launchpad.net/bugs/+filebug)

I checked with:
Distribution: Ubuntu
Package:  libsmbclient
subject: "network browsing fails with libsmbclient 3.3.2"  
I also tried subject: "fusesmb fails with libsmbclient 3.3.2"

There are no reported bugs like yours.  You should report this. 

If you never did a bug report before, you will have to create an account, but there should be a walk through as you submit the bug.

---

### Post by HDTimeshifter on 2009-08-22
I installed Ubuntu 9.04 desktop on my file server, wiping out Windows XP Pro a month or so ago and it's been working fine.  However, occasionally I can't browse that computer through Nautilus.  A few minutes ago I went to Network Places and drilled down to my server, but couldn't see any shared folders.  I even tried to refresh this window and go back out and in.  However, in the Places menu, some of the shared folders showed up, so I clicked on one and it opened.  So there appears to be some sort of bug in Nautilus.

---

