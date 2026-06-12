---
title: "Re: Did Local Network Share ever work?"
date: 2019-04-29
forum: Networking &amp; Wireless
---

### Post by DAVID_LECKIE on 2019-04-29
Computer is a Ryzen 1 1700 with 16GB memory running Ubuntu V19.04

I have a strange sharing/networking issue which I cannot resolve.

I am in the process of making a media server.

I bought an 4TB WD hard drive and added it to my system.

Gparted found it OK 
I created a 2TB partition called Media_Server it mounts fine and and I can access it OK.

I created a folder called Shows and put some media .mp4 files into it.

These files I can access OK from the local machine.

As I want to share this folder I did the following

Nautilus
Other Locations
Media_Server was there OK
Opened up and 
Shows was there OK
Right Click
Properties
Permissions I gave myself full access.
So far all OK

First Issue
Now the problems start.
Right Click on Shows
Properties
Local Network Share
Share this folder
Share Name "Media_Shows"
Create Share
Close the window
The icon now has the green shared icon.

Close down Nautilus
Re-open Nautilus
Still shared OK

Re-start Ibuntu
Go to Nautilus
Go to Media Server
And Shows folder no longer has a shared icon
Right click 
Properties
Go to Local Network Share
and it is no longer shared.

Surely shares should not be lost when I re-boot?

Second Issue
I re-create the share as describe above but give it a new name to avoid confusion
It has the green shared icon OK.
Now I go to 
Other locations
Networks
"Computer Name"(File Sharing)
Double click
All the shares that were lost above appear.
I go to the new share I have just created
Double click
Password required box appears
User name and Domain are already there and correct
I put in my password (the one I use to log into the machine at the start of a session.
And the log on box re-appears
I cannot log on.

Now I boot up an old laptop runing 16.04 LTS on my network
On the laptop I select Network
My new Main machine's name appears 
Double click it
It opens up
The share I just created above appaers (along with the shares that I cannot get rid off.)
Double click this new share
Log on box appears
I enter my log on details
They are not accepted.
Note log on details for both machines are the same.

I cannot log on across the network.

Am I doing something wrong?

---

### Post by Morbius1 on 2019-04-29
Need more information but first:
>  I put in my password (the one I use to log into the machine at the start of a session.
There are two passwords when using Samba. The one you use to log into the machine and the one you use for samba file sharing. They can be the same if you want but you need to add your login user name to the samba password database:
```
sudo smbpasswd -a your-user-name
```

As for the shares disappearing after a reboot I have no idea. Never happened to me. Since you are sharing them with Nautilus post the output of the following command to get a list of those shares and how they are set up:
```
net usershare info --long
```
You might want to post the output of this command as well so the folks here can see how samba itself is set up:
```
testparm -s
```

---

