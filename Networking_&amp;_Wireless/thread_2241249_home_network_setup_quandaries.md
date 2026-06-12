---
title: "home network setup quandaries"
date: 2014-08-25
forum: Networking &amp; Wireless
---

### Post by cecilieaux on 2014-08-25
I'm completely new to Linux networks, although I have seen one in operation. I'm aiming to connect 3 computers, one running Ubuntu 14.04 LTS, another running Linux Mint Qiana and a third running Windows 7. Initial quandaries:

1) The Ubuntu machine is a dual-boot with Windows XP, which I only use unconnected and vary sparingly and ultimately intend to discard, but it reports a "Windows network" even in Linux, which I suspect is what connects it to the wireless rooter. I'm not sure whether this will conflict with the wireless LAN I want to set up.

2) This setup grew like Topsy, without thought and I have two machines (Ubuntu and Linux Mint that have the same main admin user, but different passwords). When I read about setting up Samba, one of the first things they say is to add users and I wonder whether ther will be a user conflict and if so, how do I change a main user without losing access to all the data in /home.

3) I don't want to start a war between software theologies, but I would like to hear some pros and cons of Giver, SSH and Samba, or if there is something simpler for someone who is not much beyond a non-technical user.

Thanks in advance for your pearls of wisdom,
C

---

### Post by The Cog on 2014-08-25
I think the "Windows network" is the root under which any windows domains are listed. The linux computer listens for adverts from windows machines and lists the domains (e.g. WORKGROUP) that they say they belong to. Clicking a domain will list the PCs that belong to that domain. So it won't conflict with a wireless LAN, it will list the domains/PCs that it discovers on that LAN.

Samba is a file server using the windows smb protocol. You can use it to get the linux boxes to share their files with windows boxes. I'm really not sure about how samba ties in its own user database with the linux file permissions.  You don't need samba for linux boxes to access file shares on windows boxes - the windows network thingy above can handle that for you.

As I said above, samba turns a linux box into a windows protocol file server. Handy if you want to acess it from lots of linux boxes frequently. It is getting linux to do file sharing the windows way. SFTP (the file sharing aspect of SSH) is will implemented by linux boxes, but of course microsoft don't want to play. You can use an sftp client like filezilla on the windows boxes but it is far from being integrated into the OS. Which you choose to use will depend on which OS you use most often, I guess. I've never heard of giver but a quick look at their web page suggests there's no windows version, and no security.

---

### Post by Morbius1 on 2014-08-25
"Windows Network" is a rather unfortunate name but it's really just a shortcut to:
```
nautilus smb://
```
It's probably called "Windows Network" because some folks think Samba / SMB is just for Windows.

In a mixed OS environment Samba / SMB is the one file sharing protocol that all of the them have in common since Windows ( SMB ) , Linux ( Samba ), and now Apple ( with their own interoperabile version of SMB which has become the default for OSX ) can all use.

---

### Post by ian-weisser on 2014-08-25
> **cecilieaux said:**
> 2) This setup grew like Topsy, without thought and I have two machines (Ubuntu and Linux Mint that have the same main admin user, but different passwords). When I read about setting up Samba, one of the first things they say is to add users and I wonder whether ther will be a user conflict and if so, how do I change a main user without losing access to all the data in /home.

This assumes you want to use Samba.
It also assumes that moving all the data from one /home to another is difficult (it's not).


> **cecilieaux said:**
>  3) I don't want to start a war between software theologies, but I would like to hear some pros and cons of Giver, SSH and Samba, or if there is something simpler for someone who is not much beyond a non-technical user.

Well, you are asking to do something complex, but you want it simple.
You can chase complexity around, but you can never get rid of it. You can have a setup that's dead-easy to set up, but operationally it will be limited and frustrating (that's how phone/tablet apps work). Or you can have an operation that does everything you want and practically reads your mind...but first you must set it up.

There are lots of pros and cons.
What kind of networking are you trying to do? Exchange files? Backup from one machine to another? Media server? Shared printing?

One really nice element of free software for networking is that you can erase your setup and try something different. Try stuff and see what you like to use. We can't predict what you will like.

Personally, I use SSH and SSHFS for most LAN networking needs. I find it easiest to set up and troubleshoot. Your experience may differ - your needs and wants are likely quite different from mine.

---

### Post by Morbius1 on 2014-08-25
>  2) This setup grew like Topsy, without thought and I have two machines  (Ubuntu and Linux Mint that have the same main admin user, but different  passwords). When I read about setting up Samba, one of the first things  they say is to add users and I wonder whether ther will be a user  conflict and if so, how do I change a main user without losing access to  all the data in /home.
a) You don't have to add users if you don't want to. You can create guest accessible shares if that's what you want to do.
b) A samba client user either guest or a named user doesn't have access to your entire box just the parts that you want to share.
c) There's two different users in Linux - Samba. The login user with his user name and password and the samba user which has the same user name but can have a different password.
d) There is no need to move around any /home directories.

So if agnes wants access to your share you can set up a user "agness" on your box, give her a local login password that matches your own not hers ( that way she can't logon to your physical box ), and then set a samba password for her that matches hers or something totally different.

---

### Post by kurt18947 on 2014-08-25
As others have said, it depends on what capabilities you require and how sophisticated you want to be.  I wanted simple file sharing and really preferred to not enable file & printer sharing.  I bought a second router that has a USB port.  I plugged a flash drive into it and installed filezilla on each machine.  Nautilus would see the drive and would show file names but wouldn't upload or download content.  Windows 7 explorer would upload and download so I may have been able to get Nautilus to work.  Filezilla is easier.  I doubt my solution would work for someone wanting to steam HD media or other demanding application but it does what I need it to do.

---

### Post by cecilieaux on 2014-08-26
OK, let's see if I understand. First of all, I should accept a little complexity. Check! Then the "Windows" network does not refer to that infamous OS that I have fled (am fleeing). Check! The usernames in one thing (logi make

My purpose is to enable occasional filesharing. Every now and then I miss a picture or a song I have in another computer. Or I was writing the Great American Novel on the desktop, but I am in bed with the laptop and want to edit, or write more. Etc. I've been sneaker-netting with a USB, using Dropbox and so forth (desktop to huge external drive, HED to laptop), etc. At the office I have a peer-to-peer network with shared material. That's all in the other OS. At home I wanna do the same but including Linux.

Is Samba too much of an elephant gun to kill a mosquito?

Would SSH or Filezilla do? I can see any other computer opening the Windows network.

---

### Post by cecilieaux on 2014-08-26
OK, I tried clicking on the Windows network icon in the Ubuntu 14.04 LTS desktop and the Linux Mint 17 Cinnamon 64-bit laptop. Here are my results:

network:///

3 icons: SMB-SERVER and THELINUXLAPTOP look like a cabled computer box, WINDOWS NETWORK looks like three monitors

1. clicking on SMB-SERVER

smb:///

in the desktop, clicking properties just closes the box and wipes the icons off my desktop or give me an error that the software has crashed

in the laptop, I just cycle to WORKGROUP, the the other icons then back again 

2. clicking on THELINUXLAPTOP

smb://thelinuxlaptop/

folders: Documents print$

Then a dialog pops up

username cecilieaux
workgroup WORKGROUP

password ... I try everything I can think of, nothing works

3. smb:///

new icon WORKGROUP

click on that, get to smb://workgroup/

in the desktop crrr ... ash, the window is gone and Ubuntu has experienced an internal error

in the laptop, just cycle through the icons, occasionally get the dialog, no password works

So... what have I done wrong?

---

### Post by kurt18947 on 2014-08-26
> **cecilieaux said:**
> Sorry, don't know how to delete the duplicate.

You can click the "report this post" icon in the lower left corner and ask a mod to delete the duplicate.  I haven't really messed with Samba but what I have read convinced me I didn't want to if I didn't have to.  So far I don't have to. Enabling file & print sharing in Windows has been opening yet another door to security issues.  I don't know if linux has the same weakness but right now I don't have to wonder because it isn't enabled.  The only thing I'd like to change on my current setup would be to change the default port on the router's FTP server and/or enable SFTP.  So far I don't see a way to do that.

---

### Post by Morbius1 on 2014-08-27
> My purpose is to enable occasional filesharing. Every now and then I miss a picture or a song I have in another computer.

A Samba Approach: Note: you need to share something first so in this example we will share your "Public" folder:

***On the Mint machine:***

*** Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
*** Add the following line [COLOR=#0000cd]with your real Mint login user name[/COLOR] - right under the workgroup line towards the top of the file:
```
force user = your-mint-login-user-name
```
*** Save the file then restart samba:
```
sudo service smbd restart
```
*** Now, Open Nemo
Go to your home folder
Right click the Public folder > Sharing Options > Select all the boxes
You just created a samba share of your Public folder and made it guest accessible.

***On the Ubuntu machine:***

Open a terminal and type:
```
nautilus smb://thelinuxlaptop
```
** [COLOR=#0000cd] Or better yet:[/COLOR]**
```
nautilus smb://thelinuxlaptop.local
```
[COLOR=#0000cd]*The ".local" is an mDNS qualifier which all Linux machines can use by default as long as avahi-daemon is running and it's port is open.*[/COLOR]

You should see the "Public" folder in there somewhere.

Get this working then explore all the other options mentioned here like ftp, ssh, whatever then decide for yourself what best fit's your requirements.

---

### Post by Morbius1 on 2014-08-27
> My purpose is to enable occasional filesharing. Every now and then I miss a picture or a song I have in another computer.

An ssh approach:

_***On the Mint machine***_

Install ssh:
```
sudo apt-get install ssh
```

_***On the Ubuntu machine:***_

Run this command from the terminal:
```
nautilus ssh://thelinuxlaptop
```
**[COLOR=#0000cd] Or better yet:[/COLOR]**
```
nautilus ssh://thelinuxlaptop.local
```

You will get a rather nasty looking thing that looks a lot like this:
> This happens when you log in to a computer the first time.

The identity sent by the remote computer is
 &#8220;f7:ef:47:a5:15:72:76:02:41:12:5c:b0:57:7b:9c:03&#8221;. 
If you want to be absolutely sure it is safe to continue, contact the system administrator.
Well, you are the system administrator so just select "Log In Anyway"

Supply the user name and password of the Mint box user and you pretty much have access to the whole damn box.

Get this working then explore all the other options mentioned here like  ftp, samba, whatever then decide for yourself what best fit's your  requirements.[COLOR=#0000cd][/COLOR]

---

### Post by cecilieaux on 2014-08-29
> **Morbius1 said:**
> A Samba Approach: Note: you need to share something first so in this example we will share your "Public" folder  ...
Get this working then explore all the other options mentioned here like ftp, ssh, whatever then decide for yourself what best fit's your requirements.

This sounds very clever, Morbius, and I will try it this evening when I get home. Question: Can I reverse this, since I really will most need to get files from the Ubu box to the Mint laptop?

The guys who sold me the laptop ([http://www.thelinuxlaptop.com/products_new.php](http://www.thelinuxlaptop.com/products_new.php) ... I love my laptop) are telling me they recommend ssh, so that will be next. But if this can work, do I have to?

Thanks muchly,
C

---

### Post by Morbius1 on 2014-08-30
Everything I posted works in Ubuntu just as it does on Mint.

---

### Post by cecilieaux on 2014-08-30
OK, both already had ssh installed. So I tried, from the Linux Mint 17 Cinnamon 64-bit laptop

> nemo ssh://precision-workStation-390

Nautilus was not installed on LM so I tried Nemo. I got the error message 

> Could not display "sftp://precision-workstation-390/", because the host could not be found.

From the Ubuntu 14.04 LTS desktop I tried the same thing (actually, both nemo and nautilus) and got essentially the same error. 

The machines don't know the other exists?

---

### Post by Morbius1 on 2014-08-30
You forgot the ".local":
```
nemo ssh://precision-workStation-390.local
```

In order for the ".local" to work - and it should work by default in Ubuntu / Mint you need to have avahi running:
```
sudo service avahi-daemon start
```
And your firewall should allow ports 5353 ( avahi ) and 22 ( ssh ) - assuming you are using a firewall.

Worst case access the machine by ip address:
```
nemo ssh://192.168.0.100
```

But you really should try to get mDNS / Avahi to work - it's the one thing Linux ( and OSX ) can do that Windows cannot.

---

### Post by cecilieaux on 2014-09-02
Tried in the Mint laptop

> nemo ssh://precision-workStation-390.local

Avahi was running, but still got

> sudo service avahi-daemon start

Then I tried

> nemo ssh://precision-workStation-390.local

and received no complaint, but I'm at prompt.

I try the Network, Windows, get the smb:/// window and after much trying, the error

> Could not display "sftp://192.168.0.100/".

Error: SSH program unexpectedly exited
Please select another viewer and try again.


---

### Post by Morbius1 on 2014-09-03
If you are going through [COLOR=#0000cd]**smb:///**[/COLOR] and got this error message:
> I try the Network, Windows, get the smb:/// window and after much trying, the error
  [COLOR=#000000]**Could not display**[/COLOR][COLOR=#0000cd]** "sftp://**[/COLOR][COLOR=#000000]**192.168.0.100**[/COLOR][COLOR=#000000]**/**[/COLOR]".
Your problem is outside the scope of this topic - even in the unlikely event that your ubuntu machine really did have the ip address of 192.168.0.100.

---

### Post by cecilieaux on 2014-09-05
I cannot believe this answer!

---

### Post by Morbius1 on 2014-09-05
I can't believe the symptom.

You go through smb in the file manager and you get an sftp error? Not gonna happen. If it does you need to seriously consider reinstalling the operating system.

---

### Post by christopher9 on 2014-09-05
If I read all this correctly, you really don't need file sharing as in collaborative access to data but simply data retrieval as in 'oh,  myfile.x is on the other machine' ?  If so, then wouldn't a NAS or external HDD for copying your important music, photos, and documents on your home network accomplish your purpose ?  Your home router may even support USB storage which can be seen as a network shared folder...if I'm not seeing the whole picture, I apologize....

---

### Post by cecilieaux on 2014-09-07
> **christopher9 said:**
> If I read all this correctly, you really don't need file sharing as in collaborative access to data but simply data retrieval as in 'oh,  myfile.x is on the other machine' ?  If so, then wouldn't a NAS or external HDD for copying your important music, photos, and documents on your home network accomplish your purpose ?  Your home router may even support USB storage which can be seen as a network shared folder...if I'm not seeing the whole picture, I apologize....

Very well described:  'oh,  myfile.x is on the other machine' That's pretty much it.

I have thought of an NAS. I'm concerned about hardware compatibility with Linux, tho. If I can't communicate with another computer on the same network, how will I communicate with the NAS?

I have an external HDD and a USB stick, I just thought that was inelegant and sneaker-net-ish, but yeah, that's what I'm doing while I figure out this networking stuff. I guess I need some tutorials to get me up to speed. (Suggestions accepted.)

Thanks!

---

### Post by cecilieaux on 2014-09-07
> **Morbius1 said:**
> I can't believe the symptom.

You go through smb in the file manager and you get an sftp error? Not gonna happen. If it does you need to seriously consider reinstalling the operating system.

I just tried it again in the terminal nemo > ssh://precision-workStation-390.local



and I got

> ** (nemo:21425): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

and a popup message > Could not display "sftp://precision-workstation-390.local/". outside the terminal.

I am not making this up.

---

### Post by cecilieaux on 2014-09-07
Kudos to [Nerdtron]("http://ubuntuforums.org/member.php?u=895543") who solved my problem in [another subforum]("http://ubuntuforums.org/showthread.php?t=2243293") after I gave up all hope here.

---

### Post by Morbius1 on 2014-09-08
OK, I'll play along.

This is what I wrote after suggesting you install the ssh package:
> **Morbius1 said:**
> Worst case access the machine by ip address:
```
nemo ssh://192.168.0.100
```
.
This is how you responded:
> **cecilieaux said:**
> 
I try the Network, Windows, get the smb:/// window and after much trying, the error
 > Could not display "sftp://192.168.0.100/.
Two things:

*** You couldn&#8217;t possibly have gotten a cannot display "sftp://..." error by using the "smb://" protocol.
*** Even if I assume you just made up the "I try the Network, Windows, get the smb:/// window" part your ip address was not 192.168.0.100.

It was 192.168.1.104:
> **cecilieaux said:**
> OK, you mean this, right?

> ping 192.168.1.104
PING 192.168.1.104 (192.168.1.104) 56(84) bytes of data.
64 bytes from 192.168.1.104: icmp_seq=1 ttl=64 time=102 ms
64 bytes from 192.168.1.104: icmp_seq=2 ttl=64 time=133 ms
64 bytes from 192.168.1.104: icmp_seq=3 ttl=64 time=2.62 ms

....
So I assume they can ping. or "see" each other.

In retrospect what I should have written was this:
> **Morbius1 said:**
> Worst case access the machine by ip address [COLOR=#0000cd]*by running this command in a terminal*[/COLOR] :
```
nemo ssh://192.168.0.100
```
[COLOR=#0000cd]*Change 192.168.0.100 to the ip address of the machine you are trying to connect to.*[/COLOR]
.

My bad.

---

### Post by cecilieaux on 2014-09-14
Look, Morbius, thank you but I'm done.

---

