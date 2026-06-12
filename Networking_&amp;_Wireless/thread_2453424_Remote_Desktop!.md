---
title: "Remote Desktop!"
date: 2020-11-10
forum: Networking &amp; Wireless
---

### Post by hornetster on 2020-11-10
Sorry, time for a rant....
Why is it SO difficult to securely (or even insecurely!) remote desktop in Ubuntu/Linux? (Check out the number of basically unsolved forum posts.)
There is NO WAY to simply connect to a desktop (I am talking local network here, same subnet - won't even venture onto anything more widespread.)
Sure, can jump through heaps of hoops, and get some form of VNC connected, Remmina, etc, but don't venture into the security side of things - have to have a degree to get anywhere.
Have used TeamViewer for a while, but it even has issues in the linux world - works fine if you have a logged on machine on the other end, but if it is slightly "remote", and difficult to access, there is no way to remote a "logged off" PC. (and from what I can see at the moment, this is also an issue for VNC, and maybe Remmina.)
Please..... Can anyone give me a SIMPLE method of remoting to another desktop? Preferably to it's Plasma/Gnome/etc desktop, not a cutdown XFCE or similar version.
Yes, I do ssh into these machines and do admin from there, but there are times when it would be SO GOOD (and even essential...) to be able to connect to the GUI.
Wish I was a developer, and had a clue.... :p

Thanks.

---

### Post by Holger_Gehrke on 2020-11-10
If you can ssh into the remote machine then you can run graphical applications from the command line. You just need to start the ssh client with the option for X11-forwarding ('ssh -X user@remotemachine'), then ssh will set up a way for the program running on the server to display on the client. No need to send the whole desktop over the network, just the window(s) for the remote application(s).
And as a bonus you can configure the ssh server to offer sftp, then you can connect to the remote file system from your file manager by giving it an URL of the form 'ssh://user@remotemachine/path' as a location. This basically turns your ssh into a network 'share'.

Holger

---

### Post by hornetster on 2020-11-10
> **Holger_Gehrke said:**
> lient with the option for X11-forwarding ('ssh -X user@remotemachine'), then ssh will set up a way for the program running on the server to display on the client. No need to send the whole desktop over the network, just the window(s) for the remote application(s).
And as a bonus you can configure the ssh server to offer sftp, then you can connect to the remote file system from your file manager by giving it an URL of the form 'ssh://user@remotemachine/path' as a location. This basically turns your ssh into a network 'share'.

Holger

Hey, great tip. Thanks. Have tried that before, but never really worked it out.... Will have a play with that!
Not a real solution to the full desktop, though.....

---

### Post by cmcanulty on 2020-11-10
I agree. I support 12 computers as our local library. After the upgrade to 20.04 I can't make vnc,, rdp, or anydesk  work. All setups are the same as what worked in 18.04. I have wasted days of work trying to fix this. I wish Ubuntu would stop always adding new features yet basic features don't work.

---

### Post by joeschu2 on 2020-12-02
Here's my experience. I installed a fresh 20.04LTS onto a 128g SSD from a USB stick. After it was completed, I went to the sharing section to turn on Screen Sharing. It was greyed out. I found out that you need Vino installed. I install Vino only to be told a more current version is already installed and so the install does not take place. I used sudo apt get install vino using terminal. Now I am on the forums trying to find a solution. That is why I am here agreeing with the above posts.

---

### Post by cmcanulty on 2020-12-02
how would I login to use graphical apps when I need to get to a certain port behind a router? I support 12 xubuntu machines at a library and have spent the last several weeks trying to get back access via vnc and rdp since upgrade to xubuntu 20.04 fried all my remmina remote access?

---

### Post by TheFu on 2020-12-02
On the LAN, I use remote X11
```
ssh -X remote-user@remote-server  command
```
I do this daily, for many applications.  Why be limited to a laptop power when I have a desktop faster than a Cray supercomputer in another room?

For connections outside the LAN, I use **x2go**, which implements the NX protocol.  NX uses ssh, which makes it pretty convenient, until 20.04 when something about x2go got broken and it is requiring a password be used rather than my ed25519 ssh-keys.  x2go performance feels 2-3x faster than any VNC I've used. Use the PPA.

As you can see, all roads lead through ssh and for good reason.

I've been doing remote X11 through ssh for about 25 yrs.  It is how I work and built into my workflow.
Coming from Windows and expecting non-secure connections like RDP or VNC to be possible doesn't make sense to me. I've heard that in the last year, MSFT finally tried to get RDP working in a secure way, but that broke compatibility with non-MSFT systems.

Now, if you run desktop inside KVM virtual machines, then we can talk about nearly native graphics performance over secure channels, but most people don't do that.   Think I saw around 65 fps using the glxgears tests from a remote machine to a VM using the SPICE protocol.  On the same hardware, again using SPICE, I just saw 745 fps. Seems fast enough and I know it is fast enough for video.  SPICE isn't new, BTW. It has been used over a decade now. Spice supports both remote desktops and remote applications.  Too bad they don't have any advertising for their awesome work or the Gnome project pushing it by name.  Gnome is off adding bloat to their projects and dumbing down all the GUIs.

Many complaints are simply due to uninformed people.  Sometimes that's me.

---

### Post by hornetster on 2020-12-08
Well, have sort of got it working, in an insecure way!! (Only ever use it on the local LAN...)
Installed/configured x11vnc on the machines I want to connect to, and use TigerVNC viewer on my client machine. Seems to be working OK.
Will see if I can work out how to run over ssh....
Thanks.

---

### Post by hornetster on 2020-12-08
Update from my last post....
x11vnc is started as a service on my server machine using:  ExecStart=/usr/bin/x11vnc -auth guess -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.pwd -rfbport 5900 -shared -o /var/log/x11vnc.log

Connect to this machine, using: ssh -L 5900:localhost:5900 media

Run tigervnc on this machine, and connect to: localhost:5900

It works!
So, I am assuming that this is now running securely over ssh...? Am I correct?
Can I monitor the data being transferred?
Thanks.

---

### Post by TheFu on 2020-12-08
Doesn't the **-localhost yes** option ensure it can't be contacted except on 127.x.x.x/8?
Check it by running an nmap scan from another system on the LAN.

---

### Post by illmortal on 2021-01-17
Have to agree with OP. I remember VNC working flawlessly last time I used Ubuntu (version 16.04). Now I've come back to Ubuntu, this time with a fresh install of 20.04.1 LTS, VNC comes to a black screen, spent 2 almost 3 days on trying to find a solution to it, but no dice. Now I'm going the RDP route, which I'm not too happy about since this is going to be a headless media/fileserver and prefer to screen share than RDP since I'm forced to log out of my session in order to RDP in. This will ultimately have to change, can't be logging out of this system, ever. 

I just wish there was an official SOP/Knowledge Base for any of these changes and how to properly setup these services instead of going through pages upon pages of tutorials, all of which failed to solve the VNC issue that I, amongst many others are facing.

---

### Post by TheFu on 2021-01-17
Nobody here works for Canonical.

The official guides are at help.ubuntu.com. Everywhere else is unofficial to my knowledge. Random google answers often are bad, out of date, written by someone who knows less than you or me.  They think they know how something works, but it turns out not all the steps are really connected. The fact that there are all 50-500 possible answers for each desired result doesn't help either. There isn't just 1 right answer.

---

### Post by hornetster on 2021-01-27
> **hornetster said:**
> 
It works!
So, I am assuming that this is now running securely over ssh...? Am I correct?
Can I monitor the data being transferred?
Thanks.

Another update:
No, this wasn't working, well, not securely, anyway.
Have since played with again, and have it "sort of" working, securely...
x11vnc installed on server machine - no automatic startup.
When I want to connect, I run: ```
ssh -L 5900:localhost:5900 <HOSTNAME> 'x11vnc -localhost -display :1 -rfbauth /<HOMEDIRECTORY>/.vnc/passwd'
```
Password has previously been saved, using : x11vnc -storepasswd
Then connect to ```
localhost
``` using, I assume, almost any vncviewer (I am using Tigervnc)

Issues:
Apparently a user has to be logged in for it to be able to find the "display" component, and then sometimes doesn't appear to work either. I am a little bit perplexed by the whole user/logon/reboot process. What use is a remote app, if you have to logon physically to the remote machine before you can logon remotely??
This is also the case when trying to connect to a linux box using teamviewer...
Can anyone explain/give a solution?
Thanks.

---

### Post by TheFu on 2021-01-27
> Can anyone explain/give a solution?
Post #7 above provides 2 solutions.

---

### Post by hornetster on 2021-02-01
> **TheFu said:**
> Post #7 above provides 2 solutions.

Thanks for the reply, but, I don't believe it answers my original question. Yes, gives ways and means to do various things, but I am just trying to do a full remote session to another machine (not necessarily logged on), internally.

The initial command mentioned in Post#7 is for running a specific application/command? Don't believe this will work for a full session?
x2go apparently is for external to the network? I am after internal...
So... don't beleive that Post#7 actually provides 2 solutions to my original post?
Thanks.

---

### Post by TheFu on 2021-02-01
You are incorrect.  It provides 2 solutions.  Neither require a local login on the "console" first.

---

### Post by cmcanulty on 2021-02-01
x2go works perfectly over LAN either as the actual desktop as sharing or as xfce, or just about any desktop available in llinux. I can advise how if you need more help. I tried to use it for years without success just because I didn't realize a few easy tricks t o it.

[https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04]("https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04")

[https://www.cs.mtsu.edu/~steven/x2go_tutorial/]("https://www.cs.mtsu.edu/~steven/x2go_tutorial/")

[https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/]("https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/")

[https://draculaservers.com/tutorials/install-x2go-ubuntu-remote-desktop/]("https://draculaservers.com/tutorials/install-x2go-ubuntu-remote-desktop/")

---

### Post by thebigk on 2021-02-05
I Use nomachine which is fine to me. Is even better than rdp I would say. Disadvantage is that is not open source. But since I connect over a SSH-Tunnel its secure enough to me.

[https://www.nomachine.com/](https://www.nomachine.com/)

---

### Post by TheFu on 2021-02-05
NoMachine is similar to x2go. Both use the NX protocol, just in proprietary ways.  NX uses ssh, so getting ssh working is the first step.

I'm always amazed at people still using RDP or VNC when x2go is so much faster and just a few minutes to install and configure.  The main problem with x2go is the limitation that only 1 client can run at a time, but if the remote systems are on the same LAN, then using 1 as a desktop and accessing the others using **ssh -X** works perfectly.

NoMachine also limits the number of client connections into a server.  Product-based companies tend to do that, unlike service-based companies.

---

### Post by cmcanulty on 2021-02-05
Actually you can use x2go on several machines at once by opening another instance of x2go for every computer you need to access. Not as easy as tabs in x2go but workable. Works over LAN or WAN

---

### Post by hornetster on 2021-02-07
> **cmcanulty said:**
>  can advise how if you need more help. I tried to use it for years without success just because I didn't realize a few easy tricks t o it.


Hey, have installed x2go, and working fine as far as connecting to a logged in session. Still unable to access pre-login though(gdm3, I beleive).
Have searched high and low, but unable to find solutions without installing full, separate desktops etc.
IS there actually any way to connect pre-login?
Thanks.

---

### Post by TheFu on 2021-02-07
You pick which type of session you want in the x2goclient.

If you want a dumb client, use XDMCP. I haven't used XDMCP in about 25 yrs. It is what dumb x/terminals used when we'd have 30+ people connect to one workstation in the olden days. This was always pre-login.  [https://wiki.ubuntu.com/xdmcp](https://wiki.ubuntu.com/xdmcp)  It worked over UDP. Meh. No security.

The other option is to use SPICE, but I've never gotten SPICE working unless the machine was a KVM virtual machine. There was a project to make it a normal remote desktop, but there wasn't too much interest. Someone with an itch probably kept working on it and SPICE over a LAN is probably the fastest remote desktop available today.  [https://www.spice-space.org/](https://www.spice-space.org/)  I'm 100% positive this is pre-login. It always works that way, which I find maddening.

---

