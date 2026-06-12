---
title: "PPTP in 8.10 (I'm a nube) need help!"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by Irysche on 2008-11-06
Hello,

I really new at this. I like Ibex, but need help to get this going and I have not found the answer in searching the net. Anything you guys can give me would be great.

I am trying to setup a VPN to a Microsoft network via PPTP. I found in Network Configuration where you can add a VPN. I have done that, in fact I found in another forum what I needed to install to get that to allow me to add anything. Problem is, I see that I have added it and it lists that I have never connected. That's fine because I don't know how to start the dern thing up!!!:(

Double Clicking just brings up the editor or properties of the connection. Right clicking (yes, I am a windows user big time) does not seem to do anything. I have seen in other forums where there should be a start button, I don't see that either.

What am I missing? I would only be making a connection occasionally to RDP to my Vista Desktop at work.

Help me!

---

### Post by kdcoetzee on 2008-11-07
So far I understand. 
just left click on the network manager icon.
go to "VPN Connections" then click on your VPN you configured.

you don't connect within the setup window.


And just to make shore you installed.
```

sudo apt-get install network-manager-pptp

```

---

### Post by and.duncan on 2008-11-07
The above is how I have connected to a few different VPN's now. 

As for the next question: It's given me some grief at times, for my particular case it seems to prefer that I enter the password manually rather than have it in the config settings and then it will connect fine.

---

### Post by kdcoetzee on 2008-11-07
Yes I have the same problem.
Don't enter the password in the configuration field. 
enter it when the VPN connection is trying to connect.

a bug or something.

---

### Post by Irysche on 2008-11-08
Hey thanks for all the tips, I was able to at least get this thing started :D

However, it fails, but I don't know why that is. So, how do I create or find the Log file that the VPN Connection creates so I can see why it failed?

---

### Post by kdcoetzee on 2008-11-09
Try messages in terminal.

```

tail -f /var/log/messages

```

---

### Post by Irysche on 2008-11-09
Okay, I tried the command as suggested. Not quite what I was hoping to see. Here's what I got:

[I]Nov  9 20:46:50 ubuntu pppd[5599]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Nov  9 20:46:50 ubuntu kernel: [  237.910554] PPP generic driver version 2.4.2
Nov  9 20:46:50 ubuntu pppd[5599]: pppd 2.4.4 started by root, uid 0
Nov  9 20:46:50 ubuntu pppd[5599]: Using interface ppp0
Nov  9 20:46:50 ubuntu pppd[5599]: Connect: ppp0 <--> /dev/pts/1
Nov  9 20:46:55 ubuntu pppd[5599]: Connection terminated.
Nov  9 20:46:55 ubuntu pppd[5599]: Exit.[/I]

Not much in the way of any kind of error. Is there another log that I can look at to see what is going on? I hate asking these questions, but I really don't know where to look. :confused:

Like I said, I'm a nube!! :(

---

### Post by kdcoetzee on 2008-11-10
Well I don't have a Ubuntu Machine, close to me at this moment. 

But go to the /var/log folder and look for a pppd file or folder.

```

cd /var/log

```

to display files 

```

ls

```

---

### Post by Irysche on 2008-11-10
The fact that you can remember this stuff from the top of your head is impressive:)

I went to the /var/log directory and listed the contents, but no pppd directory. Nothing even close.

I've installed all of the stuff that I think I need to, based on the articles that I have found. Do you think there is something else I might have missed?

One other thing, do you know how to get bash type files to run? I have an install that is compatible with Suse and I have seen it run on Ubuntu also, but it appears that you need to have the bash shell installed. I instlled it, but does not seem to work. I can post this one somewhere else if you're not sure.

---

### Post by kdcoetzee on 2008-11-11
> **Irysche said:**
> 
The fact that you can remember this stuff from the top of your head is impressive:)

Constantly working with it and I enjoy it may be the reason.

> **Irysche said:**
> 
I went to the /var/log directory and listed the contents, but no pppd directory. Nothing even close.

I've installed all of the stuff that I think I need to, based on the articles that I have found. Do you think there is something else I might have missed?


I think you installed all there is to install.
I mean I only installed network-manager-pptp and connected.
My only snag was the password.
try leaving out the username and password.
And then you can play around with the compression and encryption ticks.

I think there is our problem.

On the VPN configure window. click on the Advanced button. then under "Authentication", check everything, and then enable the MPPE under "Security And Compression"

Then give it another shot.


> **Irysche said:**
> 
One other thing, do you know how to get bash type files to run? I have an install that is compatible with Suse and I have seen it run on Ubuntu also, but it appears that you need to have the bash shell installed. I instlled it, but does not seem to work. I can post this one somewhere else if you're not sure.

what is the extension of the file, an ".sh".  what is the program name ?
in Ubuntu it is always best to look for a ".deb" file  that is meant for Ubuntu or Debian. that is when the package is not in the repository. 

try searching for your package in "Sympatic Package Manager", 
you can get the Package Manager from the System Menu,
or with APT

```

apt-cache search <package_name>

```
and to get more detail on a package
```

apt-cache show <package_name>

```


But.
you can run it with. 

```

./filename

```

---

### Post by Irysche on 2008-11-11
> On the VPN configure window. click on the Advanced button. then under "Authentication", check everything, and then enable the MPPE under "Security And Compression"

I went into advanced options and checked everything as you suggested. Still no luck. I'm really bummed because Ubuntu is so much faster than windows and I can't get it to work! Do you think there is any chance that removing the packages and then adding back just the one PPTP-manager would work?

As for the package that I am trying to install, it is something known as Bomgar. It is a remote support package. The command the package I downloaded is trying to run is as follows

```
bash "-f" "-c" "exec echo bash \'"%k"\' | sed -e 's!file://!!' | sh"
```

---

### Post by kdcoetzee on 2008-11-12
> **Irysche said:**
> 
I went into advanced options and checked everything as you suggested. Still no luck. I'm really bummed because Ubuntu is so much faster than windows and I can't get it to work! Do you think there is any chance that removing the packages and then adding back just the one PPTP-manager would work?

I think just ask the guy how he did the setup on the VPN, which compression  n and encryption he used.

I am stumped, All I can say more is, play abit this those settings in Advanced if you do not get any info from the setup guy.

I will keep a eye out for any extra info on the web. 


> **Irysche said:**
> 
As for the package that I am trying to install, it is something known as Bomgar. It is a remote support package. The command the package I downloaded is trying to run is as follows

```
bash "-f" "-c" "exec echo bash \'"%k"\' | sed -e 's!file://!!' | sh"
```

try these links:


[http://ubuntuforums.org/archive/index.php/t-902774.html](http://ubuntuforums.org/archive/index.php/t-902774.html)
[http://www.dbjohn.com/2008/10/20/installing-the-bomgar-representative-client-on-ubuntu-804](http://www.dbjohn.com/2008/10/20/installing-the-bomgar-representative-client-on-ubuntu-804)
[http://jeffrasmussen.wordpress.com/2008/10/29/bomgar-remote-assistance-tool/](http://jeffrasmussen.wordpress.com/2008/10/29/bomgar-remote-assistance-tool/)

---

### Post by gabor111 on 2008-11-12
Hello,

I have similar problem.
I'm trying on EeePC 901 with arrays.org UBUNTU 8.10 kernel, in Hungarian version.
My wired and wireless networks are working fine.
I installed network-manager-pptp and tried with all settings one by one, but I had an error message like this: there is no VPN service.

After that, I installed openvpn, and I received this error message when I tryto connect (I hope my translation back to english is correct): There are no valid secret VPN informations. ](*,)

Can anyone help? :confused:

Thx in advance.

---

### Post by gabor111 on 2008-11-18
The solution is described in this post:
[URL="http://ubuntuforums.org/showthread.php?t=964255"]
http://ubuntuforums.org/showthread.php?t=964255[/URL]

I think, this post cn be closed....

---

