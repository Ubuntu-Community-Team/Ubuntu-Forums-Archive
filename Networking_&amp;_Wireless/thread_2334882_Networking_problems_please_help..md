---
title: "Networking problems please help."
date: 2016-08-23
forum: Networking &amp; Wireless
---

### Post by blumbly on 2016-08-23
One of the last things I need to do before I run all my computers on ubuntu is networking/file sharing.Now I've had a go at trying to do this all to no avail.
I install something called samba (I think that's what it was called).That didn't work,I then installed gnome3 and about all that did was made a lot of files and folders look different.
Can somebody please tell me what I'm doing wrong?
I mean going from ubuntu and getting files from a windows system is so so very easy,but doing it from ubuntu to ubuntu systems it's just not working.
What am I doing wrong? 
Please help me.
Thanks.

---

### Post by Fire_Chief on 2016-08-23
Hi blumbly,

If you're going to a pure Ubuntu network, I'd suggest using NFS for file sharing instead of Samba (which is for Windows file share internetworking).
There is a guide found here [URL="https://help.ubuntu.com/community/SettingUpNFSHowTo"]https://help.ubuntu.com/community/SettingUpNFSHowTo
[/URL]
Cheers!

---

### Post by blumbly on 2016-08-24
Thanks Fire_Chief I've tried that and it just doesn't do (I guess) what is suppose to do.When I put in, 
apt-get install nfs-kernel-server 
It comes up with, 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
Then nothing else goes any good from there.
I just don't understand why it needs to be this difficult.
One of my Ubuntu systems can get files from the other Ubuntu system but they don't work the other way round.
Yet when I go from ubuntu back to windows it works faultless,and I never even had to try and do that,just a password.
As much as I'm loving this ubuntu if I can't get them to network then I can't use it.I need them to share files.
I just don't know what to do.I just don't want to use that silly Microsoft windows anymore,but I'm running out of time and options.
If that's the only to network then I guess that's it for me.

---

### Post by speed... on 2016-08-24
you have to run the installation with root rights. Try this:
[COLOR=#000000]```
sudo apt-get install nfs-kernel-server
```[/COLOR]

---

### Post by blumbly on 2016-08-24
Thanks speed.I don't know what exactly what that command does but it has made it worse.Now from being able to see the other ubuntu computers,I now can't see them at all.Also this computer has 7 hard-drives on it and now I can only see one.The main drive all the rest have disappeared. The only network I can see is a windows network of which I don't have a computer that runs on windows except this one which runs as a due boot system,of Windows 7 and ubuntu of which I'm currently using ubuntu.
I just don't get why it's so hard to run a network through ubuntu I don't believe I've ever had this much trouble setting up a network before.
Surely someone out there knowns how to fix this.
I'm just wondering if there any other os's I can use other than this that isn't windows,to be able to share files over a home network.I'm getting the feeling that ubuntu isn't setup to be able to share files over a network.
If this is the case can someone let me know please.That way I can find an os that does.As I've been trying for weeks to get this to work and I'm just getting further and further away from what I'm trying to achieve.
Thanks guys.

---

### Post by speed... on 2016-08-25
Did you read the manual about NFS that posted Fire_Chief? [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
You can also check out the [New to Ubuntu]("https://ubuntuforums.org/forumdisplay.php?f=326") Section and the [Ubuntu Documentation]("https://help.ubuntu.com/"). There you can learn at least the basics to work with Ubuntu.

---

### Post by blumbly on 2016-08-28
Yes i did read it,but I think the biggest thing that stands out for me is this one line here,(Providing you understand what you are doing). Well that's not me,I'm only new to this and I have no idea what I'm doing.Am I suppose to change things like (users) the the actual names of the computers?
I guess that's why I'm asking is this the only way to achieve what I'm trying to achieve? Or is there something easier? I just don't understand why it needs to be so difficult to network systems with Ubuntu.They can't even see each other.
Why is it when you want to access a file or folder from Ubuntu to windows it just does it straight out of the box?
Even when I first used it from the disc before installing it could access files over the network (into a windows system),but from one Ubuntu system to another forget it.They can't even see each other let alone share files.
I guess this must be for advanced users of which it turns out I'm not.
I don't know what to do.I really don't want to go back to that crappy Windows,but I guess at least I can use it.

---

### Post by sudodus on 2016-08-29
You can also use ***ssh***, (***sftp*** and other tools, for example ***filezilla***, or maybe easier via the file browser).

If you install **openssh-server** in one of your computers, you can log in remotely with *ssh* and with graphics with 

```

ssh <username>@<IP address>     # general syntax
ssh -X <username>@<IP address>  # general syntax with graphics
ssh -X blumbly@192.168.0.2      # example, use the correct username and IP address in your case

```

and run programs remotely in the server from any of the other computers.

You can  access files remotely and transfer files via the file browsers (***nautilus***, ***thunar*** or ***pcmanfm***) as illustrated with the attached screenshots.

-o-

If you intend to connect to the server from outside your router and firewall, you should increase the security. See the following links,

[SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

[SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by blumbly on 2016-08-29
OK thanks sudodus I will certainly have a look at that. Unfortunately I run my main computer as a due boot and typical the windows side went down big time.Try to recover it but lost it.It never rains just poors.

---

### Post by sudodus on 2016-08-29
I wish you good luck :-)

---

### Post by blumbly on 2016-08-31
OH wow what a pain in the bum that was.I'm not sure what happen but windows went down and wouldn't and couldn't restart and the only way to get it going was to diskpart the drive and reinstall everything.After doing that ubuntu wouldn't and couldn't setup as a due boot system.As windows was under the UEFI file system.Then I had to make partitions and make ubuntu run under the UEFI system.What a pain that was,but all done and now back to this networking problem.I was reading somewhere about ubuntu file server.
Is that what I need to do? 
Or do I just go ahead and try other options like above?

---

### Post by sudodus on 2016-09-01
There are several solutions for your networking, and if you tell us more about what you want, we can suggest what would be the best.

So please tell us:

- Is it 'enough' with a common file server, where you want to keep your files?
- Or do you want to log in remotely via the network to your computer?
- Where do you want the file server (in Ubuntu desktop system or Windows or in a separate network server, or simply where it is easiest)?
- Do you want access via the internet (through your router's firewall)? This makes it more complicated for security reasons.

-o-

My contribution is ssh, to let your Ubuntu system be an ssh server, as described in post #8. I know how to install and use it, becuase I use it. *ssh* can give you both remote access to files and remote login to run programs in the server.

I know that there are other good solutions (with other tools), but I don't know the details very well. I'm sure the people who know those tools will help you with them.

---

