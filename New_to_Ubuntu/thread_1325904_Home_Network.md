---
title: "Home Network"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by maxximilian on 2009-11-13
Hiya,

I'm new to anything Linux based. We are talking peach fuzz new here. But have a pretty good handle on Windoze. Just installed Ubuntu 9.10 and making headway trying to understand things. So far....pleasantly surprised and have been able to solve my problems with searches.....until now.

Home Network with a Win7 machine and XP machine and this Ubuntu machine. The Win7 and XP are getting along fine. However, here is what I got when I try to get this Ubuntu machine involved.

1. The Ubuntu machine can see the windows group (using something called Nautilas which was already installed). It sees the group name and the group machines (win7 and XP). However, when I try to get to the shared folders on those....I get a message about failed "mount" and failure to retrieve shared list....or something to that effect.

2. The windows machines don't even see the Ubuntu machine in the network

3. All machines can ping each other successfully

4. All firewalls are down as I try to get this network configured.

Any help is appreciated. Not only am I new to Ubuntu or anything Linux....the Win7 machine is brand new and MS did some freaky stuff there too. Uncle Bill even took away my Outlook Express!:o:D

---

### Post by The Funkbomb on 2009-11-13
Did you install and configure Samba?

---

### Post by maxximilian on 2009-11-13
No...I have not installed Samba, although it is a name I came across in my searches. Is that a Ubuntu requirement for interfacing with Windows machines? This Nautilas thingy doesn't do that?

Thanks

---

### Post by The Funkbomb on 2009-11-13
> **maxximilian said:**
> No...I have not installed Samba, although it is a name I came across in my searches. Is that a Ubuntu requirement for interfacing with Windows machines? This Nautilas thingy doesn't do that?

Thanks

Nautilus is a file browser, sort of like Windows Explorer but better.  Samba is the sharing tool.  You need to install that to view Windows shares.

I can't tell you exactly how it works.  It's pretty well documented though.

---

### Post by maxximilian on 2009-11-13
Ahhh.........OK.....I was missing a part then. I will go install this samba critter and see what happens.....;)

---

### Post by Malac on 2009-11-13
Also make sure you have an account with the same name and password on the Ubuntu machine as the Windows machines, this makes sharing alot easier.
 
Hope this helps.

---

### Post by maxximilian on 2009-11-13
I installed Samba....and found instructions for configuring the smb.conf file. But it won't let me save any changes. Says I don't have permission.....

There are no other users on this machine.....one account....just me.

---

### Post by The Funkbomb on 2009-11-14
You have to use sudo in front of the command.

So it would look like this:

```
sudo gedit /etc/smb.conf
```

That will allow you to edit the file.

---

### Post by cariboo on 2009-11-14
The reason you can't connect to the shares on the Windows computers, is because the workgroup names are not the same, Ubuntu has a default ability to connect to windows shares, the only time you need to install samba is so that the Windows computers can connect to the Ubuntu computer.

When setting up Samba, make sure it is in the same workgroup as the rest of the computers.

---

### Post by maxximilian on 2009-11-14
I knew about the having the same group name....and have entered that in the smb.conf file....

We made some progress....I was able to edit the file and here's what I have.

1. Ubuntu can still see the group and windows machine....but still unable to access folders with a "mount" error.

2. The Win7 machine can now see the Ubuntu machine on the network (couldn't before), but askis for a username and password? None of my machines are set up to use passwords....they are open to each other without them. I'm the only user....so I skip using passwords.

One thing I notice. When I try to access the win7 machine from Ubuntu....I am using Places>Network....and the nautilus critter runs. Should this samba be running somewhere? I can't find it in my programs list to run....

---

### Post by maxximilian on 2009-11-14
Update.....

Been playing around with some things....I really mean playing, because I don't have a clue what I am doing...

Anyway....I have the Ubuntu machine showing up on the windows machine and files will transfer over to Win7. Now....the windows machine shows on the Ubuntu box, but I still cannot access the Win7 machine's shared folders. That "mount" thingy again....

However....since I have set permissions to allow transfers and edits via that single "MyFiles" folder, anything I want on the Ubuntu box, I can just drop in that one folder which goes both ways. Not exactly what I wanted....but it will get the job done for now.

Wow.....I had a terminal, a text editor, Firefox (4 tabs) and a file manager all open to accomplish this partial victory. I have to say....coming from the hand-holding world of Windows....learning this thing aint gonna be easy. And command lines don't necessarily frighten me....I've hacked a few windows registries in my day and use the MS command prompt often, but this stuff is freaking me out. Samba really needs a GUI to configure properly for new people. Just about everyone jumping to Linux has a windows machine elsewhere in the house. Just a thought....

Thanks for the assist....I will be back with more, I am sure..... ;)

---

### Post by WitchCraft on 2009-11-14
Have you installed ntfs-3g ?


How did you connect to your drive?
Use Places->Connect to server

service type: windows share
server: internal IP
share: whatever you called your windows share
username: the username you shared
domain name: LEAVE THAT EMPTY

---

### Post by Malac on 2009-11-14
Windows won't allow password-less network access without doing some tweaks to the registry and the security policy.
 
This is why I suggested setting up accounts with the same name and password on both machines. You can set Ubuntu to automatically login without entering the password each boot and do the same on Windows.
 
Hope this helps.

---

### Post by maxximilian on 2009-11-15
Sorry I am late getting back....

Had other issues. Firefox was giving me fits....so installed opera and things are much better. Also having audio issues which I am still working on. Win7 has some new things too. Trying to learn both Ubuntu and Win7 (skipped vista).

The networking thing is just plain freaky. First....I can't get Samba to load up at start. Tried adding the command to Start-up Applications, but it won't take. Still have to run it via terminal. Then...even after I get it going, connectivity with the Win7 machine is sporadic at best. Sometimes the Win7 machine can get to the shared files on Ubuntu....but mostly cannot. The Ubuntu machine can never get to Win7 via Places > Network, but can get there via Places > Connect to server.

Possible this could be a win7 issue since win7 has a new way to construct a network. Even my XP machine had trouble at first. I had to take the XP machine off the network to run through the hub isolated on a seperate IP....so can't test against XP just yet. Hope to evetually get the XP back in the network to see if Win7 is causing the problem or not.

I should note....that many times after starting Samba...I don't see any changes in System Monitor>Processes. What processes should be there after I start Samba in a terminal? I wonder sometimes if it is even running...

Thanks for the help.:)

---

### Post by sandyd on 2009-11-15
> **maxximilian said:**
> Hiya,

I'm new to anything Linux based. We are talking peach fuzz new here. But have a pretty good handle on Windoze. Just installed Ubuntu 9.10 and making headway trying to understand things. So far....pleasantly surprised and have been able to solve my problems with searches.....until now.

Home Network with a Win7 machine and XP machine and this Ubuntu machine. The Win7 and XP are getting along fine. However, here is what I got when I try to get this Ubuntu machine involved.

1. The Ubuntu machine can see the windows group (using something called Nautilas which was already installed). It sees the group name and the group machines (win7 and XP). However, when I try to get to the shared folders on those....I get a message about failed "mount" and failure to retrieve shared list....or something to that effect.

2. The windows machines don't even see the Ubuntu machine in the network

3. All machines can ping each other successfully

4. All firewalls are down as I try to get this network configured.

Any help is appreciated. Not only am I new to Ubuntu or anything Linux....the Win7 machine is brand new and MS did some freaky stuff there too. Uncle Bill even took away my Outlook Express!:o:D
```

sudo apt-get install system-config-samba samba

```
```

gksudo system-config-samba

```
go into Prefrences -> Server Settings, change the workgroup to the same one that your windows computer have. 
Security tab -> Authentication mode = share
Guest Account = your_username
add shares using the "+" button
when your finished, run
```

/etc/init.d/samba restart

```

---

### Post by maxximilian on 2009-11-15
Thanks carlee....but sort of past that now. Samba has been uninstalled and re-installed several times now. The other settings you mentioned are also already in place....and I do a restart all the time in hopes I can get some connectivity. Just did all that today again. This time using the GUI instead of manually editing the smb file....which I did before and failed.

---

### Post by maxximilian on 2009-11-15
BTW....here is something I can't figure....

The name of this machine is ABCD (fake)

Yet when it shows on the win7 machine....it appears as "ABCD-DESKTOP". Why is that? Does it factor into my troubles?

---

### Post by ArinSky on 2009-11-15
> **Malac said:**
> Windows won't allow password-less network access without doing some tweaks to the registry and the security policy.
 
This is why I suggested setting up accounts with the same name and password on both machines. You can set Ubuntu to automatically login without entering the password each boot and do the same on Windows.
 
Hope this helps.

yup, make sure that's fixed first...

---

### Post by theozzlives on 2009-11-15
One of my problems that sent me back to 9.04 was Samba. I couldn't get it to start at boot-up, and couldn't access Windows 7 shares without typing them in manually. You'd be best starting with 9.04 (if you can find it) or 8.04 LTS.

---

### Post by maxximilian on 2009-11-15
Are you guys talking inbound or outbound for Win7?

I have set win7 to disable password protection....and as I said....sometimes Win7 *can see* Ubuntu shares. Also...Ubuntu can access win7 shares via "connect to server" and accepts a blank area for password.

As I mentioned....I am also still learning win7....so anything there is helpful too.

---

### Post by sandyd on 2009-11-15
> **maxximilian said:**
> Sorry I am late getting back....

Had other issues. Firefox was giving me fits....so installed opera and things are much better. Also having audio issues which I am still working on. Win7 has some new things too. Trying to learn both Ubuntu and Win7 (skipped vista).

The networking thing is just plain freaky. First....I can't get Samba to load up at start. Tried adding the command to Start-up Applications, but it won't take. Still have to run it via terminal. Then...even after I get it going, connectivity with the Win7 machine is sporadic at best. Sometimes the Win7 machine can get to the shared files on Ubuntu....but mostly cannot. The Ubuntu machine can never get to Win7 via Places > Network, but can get there via Places > Connect to server.

Possible this could be a win7 issue since win7 has a new way to construct a network. Even my XP machine had trouble at first. I had to take the XP machine off the network to run through the hub isolated on a seperate IP....so can't test against XP just yet. Hope to evetually get the XP back in the network to see if Win7 is causing the problem or not.

I should note....that many times after starting Samba...I don't see any changes in System Monitor>Processes. What processes should be there after I start Samba in a terminal? I wonder sometimes if it is even running...

Thanks for the help.:)
if thats the problem, the simple workaround to fix this is to assign a static ip for each of the computers, then map the ip addresses to hostnames in /etc/hosts

---

### Post by maxximilian on 2009-11-15
> **theozzlives said:**
> One of my problems that sent me back to 9.04 was Samba. I couldn't get it to start at boot-up, and couldn't access Windows 7 shares without typing them in manually. You'd be best starting with 9.04 (if you can find it) or 8.04 LTS.

I don't want to do that. I am already peach fuzz new...and ahte to start over. :D

However...I ran into a website where the person had instructions for Windows share with an older Ubuntu, and said 9.10 won't take the instructions....but they would be back with a work-around. Watching that page for something new....

I guess I really need to get that XP machine back on the network to see if it has the same trouble as Win7....to eliminate that as a potential.

---

### Post by maxximilian on 2009-11-15
Update....

After doing battle with a spider I found amongst the CAT5 cables under the table (I squished it)...I have put the XP machine back on the network...

Here is the story....with Samba (supposedly running) on the Ubuntu machine...

1. XP machine can see and access the Win7 machine. All shared files and folders....no password prompt. XP can see the ubuntu machine and lists it as "*machine_name*-desktop server(Samba,Ubuntu)(*machine_name*-desktop)....but cannot access any shares, "network path not found" is the Windows error.

2. Win7 machine can see and access all shares on the XP machine. No password prompt. Can see the Ubuntu machine, with name "machine_name-desktop", but cannot access. Tells me I should check my spelling....yeah right.

3. Ubuntu machine, via Places>network>Windows Network>"Network_name", can see both the Win7 and XP machine. It can access shares on the XP machine, no password prompt. Cannot access win7 machine with mount error.

In short....everyone is seeing each other (even if with different names). Win7 is being the real PITA by not accessing Ubuntu or allowing Ubuntu access. However...Ubuntu will take XP shares, but won't give up any.

I need a drink.....:D

---

### Post by maxximilian on 2009-11-16
Going to mark this one solved. It's not 100%.....but between the "connect to server" function and using the XP machine as a go-between for the Ubuntu and Win7 machines....I can get along. As mentioned by others, it might be a Win7 issue anyway. Don't want to get too bogged down trying to make everything perfect this early in the learning process. Thanks for the help. :)

---

