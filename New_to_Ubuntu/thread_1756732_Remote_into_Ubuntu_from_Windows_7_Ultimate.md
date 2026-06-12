---
title: "Remote into Ubuntu from Windows 7 Ultimate"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by rollin77 on 2011-05-12
Hi all,

I'd like to setup an old PC running Ubuntu 11.04 that will be in my garage running 24/7 and can be remoted into from inside the house.  It's on my local network and I have no interest in remoting from outside my network, but it doesn't seem to work with Windows 7 Ultimate's built in remote desktop client.  From what I know I have everything setup so it should work on both PC's, but because it isn't working I'm wondering if Windows remote desktop is only compatible with other Windows OS's.

Is this possible, and if so what do I need to do on both PC's to make it work?  If it is not possible what would be a good, simple solution?  I have read about TightVNC but would prefer to just use the built in client I already have if possible.  Also, preferably something easy as I'm still very inexperienced with Ubuntu :)

---

### Post by cavh on 2011-05-12
You could try Teamviewer: [http://www.teamviewer.com]("http://www.teamviewer.com")

---

### Post by rollin77 on 2011-05-12
Problem with teamviewer is then my home PC can be remoted into, which I don't want.  

So this is not possible with the windows 7 RDP client?

---

### Post by eentonig on 2011-05-12
No, RDP is Ms proprietary. There are Linux clients to connect to Ms devices, but no server side component to allow à Windows client to connect to à Linux device. 
However, you could look at VNC, which Does the same thing for both Ms and Linux.

---

### Post by rollin77 on 2011-05-12
Any particular products you would recommend?  I just tried TightVNC but Ubuntu has to be logged in and I'd have to allow the connection from that PC....meaning I'd have to be physically in front of the Ubuntu PC which makes the whole process pointless as that's what I want to avoid.

---

### Post by doas777 on 2011-05-12
the "Remote Desktop" in ubuntu uses teh VNC protocol, not the RDP5 protocol that windows uses.

to access ubuntu from windows, download and run TightVNC or RealVNC or any of the numerous other VNC clients.

from ubuntu to windows, instead of using the "remote desktop viewer" use the "Terminal Services Client" (rdesktop) to connect via RDP5

hope that helps clear it up.

---

### Post by YesWeCan on 2011-05-12
Yes, Tight VNC Viewer is what you want. Just install it on your W7 PC and use it to get a remote desktop of your Ubuntu machine. I use this all the time. [http://www.tightvnc.com/](http://www.tightvnc.com/)

I think the download will also give you the server by default (which you do not need) so deselect it when it asks.

---

### Post by rollin77 on 2011-05-12
> **doas777 said:**
> from ubuntu to windows, instead of using the "remote desktop viewer" use the "Terminal Services Client" (rdesktop) to connect via RDP5
I don't understand, TightVNC doesn't have anything called either of those.  You either install TightVNC Server or TightVNC Viewer, or were you not referring to TightVNC in particular?

I got TightVNC to work, but like I said above I have to still be physically in front of the Ubuntu box to allow the connection or it won't work.

---

### Post by compmodder26 on 2011-05-12
This post describes a method for what you want.  It is rather old, so there may be a new (better) way to accomplish it, but afaik it should work for you:

[http://ubuntuforums.org/showthread.php?t=265983](http://ubuntuforums.org/showthread.php?t=265983)

Note:  If you are planning to remote over the internet, then I highly recommend you follow the advice in the post #6 about forwarding over SSH.

---

### Post by doas777 on 2011-05-12
> **rollin77 said:**
> I don't understand, TightVNC doesn't have anything called either of those.  You either install TightVNC Server or TightVNC Viewer, or were you not referring to TightVNC in particular?

I got TightVNC to work, but like I said above I have to still be physically in front of the Ubuntu box to allow the connection or it won't work.
sorry for the confusion. those are both programs in the ubuntu application menus. 

on Windows, use TightVNCViewer to connect to ubuntu.

on ubuntu, use "Terminal Server Client" to connect to windows. you do not need to install any additional software for ubuntu to do this.

---

### Post by compmodder26 on 2011-05-12
Some quick browsing on the net pointed me to another possible solution:

[http://www.nomachine.com/products.php](http://www.nomachine.com/products.php)

Might be worth investigating.

---

### Post by doas777 on 2011-05-12
> **compmodder26 said:**
> Some quick browsing on the net pointed me to another possible solution:

[http://www.nomachine.com/products.php](http://www.nomachine.com/products.php)

Might be worth investigating.


FreeNX/NeatX is my choice remote desktop protocol, and i highly recommend it. fast, responsive and ssh-based so nicely secure too. its just a little more work than the built in options. 
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by eentonig on 2011-05-12
> **compmodder26 said:**
> Some quick browsing on the net pointed me to another possible solution:

[http://www.nomachine.com/products.php](http://www.nomachine.com/products.php)

Might be worth investigating.

I stand correcter and ashamed for forgetting nomachine. That's actually what I use myself for using a virtual Ubuntu at work. Very stable and responsive. Even over the WAN

---

### Post by Purplerob on 2011-05-12
If you have to allow the VNC access, you can turn that off in remote desktop settings. ( in ubuntu) If the problem is that you have to login on the phyical computer you can get the computer to login automatically in login screen.

---

### Post by rollin77 on 2011-05-12
> **Purplerob said:**
> If you have to allow the VNC access, you can  turn that off in remote desktop settings. ( in ubuntu) If the problem is  that you have to login on the phyical computer you can get the computer  to login automatically in login screen.
I want the machine to be locked out from physical access so this would not work.

> **compmodder26 said:**
> Some quick browsing on the net pointed me to another possible solution:

[http://www.nomachine.com/products.php](http://www.nomachine.com/products.php)

Might be worth investigating.

Would this allow me to log into the Ubuntu machine that is locked out?  If it is no different than TightVNC I'm not interested.  The machine needs to be locked out from physical access with its system password.

---

### Post by YesWeCan on 2011-05-12
> **rollin77 said:**
> Is this possible, and if so what do I need to do on both PC's to make it work?  If it is not possible what would be a good, simple solution?  I have read about TightVNC but would prefer to just use the built in client I already have if possible.  Also, preferably something easy as I'm still very inexperienced with Ubuntu :)
There are two approaches here.

One is to view the local desktop that is displayed at the monitor of the Ubuntu PC. The other is to have Ubuntu spawn any number of independent desktops that can only be viewed remotely. So this means the remote desktop you get served can be independent of whatever desktop is being displayed on the machine's monitor. This is very handy because you don't even need to log in to the Ubuntu PC locally. So you don't need the Ubuntu machine to be accessible in the garage at all.

Ubuntu allows you to do either. The 'Applications/Preferrences/Remote Desktop' app, (aka vino) does the Windows thing to allow the locally displayed desktop to be accessed remotely, on port 5900.

If you install 'tightvncserver' from the Software Centre, you can use this to spawn remotely accessible desktops which are independent of the local desktop. They start at port 5901, then 5902 and so on.

Using Tight VNC Viewer on your Windows PC you can dial in to whichever desktop ports you have enabled.


As has been mentioned, for security reasons VNC remote access requires that you are logged in to the Ubuntu machine. There are 3 ways to do this:
1) Log in at the Ubuntu PC. Then you can lock the display for security.
2) Log in to the Ubuntu machine remotely, using SSH, from another PC such as your Windows PC. To do this you can run putty.exe ([http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)and](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)and) log in to the Ubuntu PC. This gives you a remote Ubuntu console and you can do whatever console stuff you like. So you can administer the Ubuntu PC entirely using a putty console and never have to step foot in the garage.
3) And, as has been mentioned, have the Ubuntu auto-login. But you may not want this for security reasons.

To be able to log in using SSH the Ubuntu PC needs to run an SSH server application. Just go to the Software Centre and install 'ssh'.

A word about security.
As you are doing all you remote access within your LAN and not via the internet, you don't need to worry too much about unwanted access. Just make sure your router is set up properly. SSH is encrypted but VNC is not. Both VNC and SSH require a login password but VNCs password is sniffable.

If you did want to do remote from somewhere else across the public internet then you certainly can, and do so securely. You might choose to create an SSH tunnel for the VNC port you want to use or you could set up a VPN connection.

---

### Post by YesWeCan on 2011-05-12
I should confess that I only use TightVNC so I am not familiar with alternatives. It works fine for me. There may well be better alternatives. :)

---

### Post by rollin77 on 2011-05-12
> **YesWeCan said:**
> There are two approaches here.

Windows is not a proper multi-tasking OS and so it can only ever serve one desktop view. [COLOR=Red]I only have one machine I want to remote into, so this is fine.[/COLOR]

As has been mentioned, for security reasons VNC remote access requires that you are logged in to the Ubuntu machine. There are 3 ways to do this:
1) Log in at the Ubuntu PC. Then you can lock the display for security.  [COLOR=Red]This does not work, once Ubuntu is locked out YOU CANNOT use TightVNC  to remote in, (unless you know of a way in which I can).[/COLOR]
2) Log in to the Ubuntu machine remotely, using SSH, from another PC such as your Windows PC. To do this you can run putty.exe ([http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)and]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html%29and") log in to the Ubuntu PC. This gives you a remote Ubuntu console and you can do whatever console stuff you like. So you can administer the Ubuntu PC entirely using a putty console and never have to step foot in the garage.  [COLOR=Red]I use SecureCRT but that isn't working either, but even if it did I haven't used Ubuntu enough to know how to do what I want to do through terminal commands.[/COLOR]
3) And, as has been mentioned, have the Ubuntu auto-login. But you may not want this for security reasons.  [COLOR=Red]Yes I have already mentioned I am not interested in this.[/COLOR]

My responses are [COLOR=Red]in red[/COLOR]

---

### Post by alphacrucis2 on 2011-05-12
> **YesWeCan said:**
> There are two approaches here.

Windows is not a proper multi-tasking OS and so it can only ever serve one desktop view. So when you do a remote view of a Windows PC you see a mimic of the actual desktop that appears on the monitor of the Windows PC (or may not appear at both places depending upon your settings).

That hasn't been true for a long time. Windows can have many RDP clients connecting to it and all see their own individual desktop. This functionality was originally developed by Citrix and MS bought it off them and it has been incorporated into Windows for many years. IIRC by default you only get allowance for two concurrent rdp connections. If you want more then you have to pay licence fees

---

### Post by YesWeCan on 2011-05-12
So what I do is open a remote console, using putty.exe, and then log in. Minimize the console and then run TightVNC Viewer.

You could also go into the garage and log in and then lock the screen for security. You can then turn the monitor off and just leave it like that indefinitely or until you need to reboot it.


Putty is very easy. You don't even install it. You just download it and run it. It looks complicated because it is very versatile, but on the window you see just put in the IP address of the Ubuntu PC and hit "open" and you should get a terminal prompting you to enter your Ubuntu PC username and password.

---

### Post by YesWeCan on 2011-05-12
> **alphacrucis2 said:**
> That hasn't been true for a long time. Windows can have many RDP clients connecting to it and all see their own individual desktop. This functionality was originally developed by Citrix and MS bought it off them and it has been incorporated into Windows for many years. IIRC by default you only get allowance for two concurrent rdp connections. If you want more then you have to pay licence fees
OK thanks. That is progress. I withdraw my cynical and erroneous claim. ;)

---

### Post by rollin77 on 2011-05-12
I know what putty is, I already said I have SecureCRT which is no different.  Neither will log into the Ubuntu machine, the connection is being refused.

---

### Post by YesWeCan on 2011-05-12
I don't know SecureCRT.
Check that:
1. You have installed 'ssh' on the Ubuntu PC. This adds the sshd server. Make sure it is running: 'sudo service ssh start'
2. You don't have any firewall on the Ubuntu PC blocking incoming connections
3. You can ping the Ubuntu PC from a Windows console.

---

### Post by rollin77 on 2011-05-12
Wouldn't simply telnetting into it be easier than SSH?  This is only over a local connection and at this point I'm just trying to make a connection so I know it is even possible.

Yes I can ping it, but as far as configurations on the Ubuntu PC I have no clue what would need changed as in my original post I mentioned I'm not experienced with Ubuntu/Linux.  So if anything needs changed I'll need to know what is needed to be done on Ubuntu's side.

By the way, I can easily remote into Windows from Ubuntu as right now I am posting this from the Ubuntu PC.  So the connection is working, but just in the wrong direction!:mad:

---

### Post by alphacrucis2 on 2011-05-12
> **rollin77 said:**
> Wouldn't simply telnetting into it be easier than SSH?  This is only over a local connection and at this point I'm just trying to make a connection so I know it is even possible.

Yes I can ping it, but as far as configurations on the Ubuntu PC I have no clue what would need changed as in my original post I mentioned I'm not experienced with Ubuntu/Linux.  So if anything needs changed I'll need to know what is needed to be done on Ubuntu's side.

By the way, I can easily remote into Windows from Ubuntu as right now I am posting this from the Ubuntu PC.  So the connection is working, but just in the wrong direction!:mad:

Telnetting is not any easier than ssh and is also not recommended as telnet sends passwords in clear text which is horribly unsecure.

---

### Post by YesWeCan on 2011-05-12
Sure, just open a Ubuntu command terminal and type 'sudo apt-get install ssh'
Put in your password and say yes to any questions.

Then type 'ssh localhost'
If the ssh server is running you will be asked to verify the "authenticity of the host". Say "yes" and then you can log in. Type "exit" to log out.

If this works then try again from Windows.

---

### Post by rollin77 on 2011-05-12
> **alphacrucis2 said:**
> Telnetting is not any easier than ssh and is also not recommended as telnet sends passwords in clear text which is horribly unsecure.
Well I don't think my mom is going to be sniffing the network lol

Anyway, I finally was able to connect via SecureCRT (putty kept giving me an error saying the password wasn't correct), but now what?  Logging in via SSH doesn't unlock the PC so how do I do that so that TightVNC will work?

---

### Post by YesWeCan on 2011-05-12
Perhaps start by doing it the easy way, using Ubuntu's Remote Desktop app. Read this:
[http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/](http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/)

(I am not sure what you mean by "unlocking the PC". Locking is a usually a monitor display thing. One doesn't have to unlock anything on the monitor for network access)

---

### Post by rollin77 on 2011-05-12
Connecting via TightVNC is not the problem, I can already do so.  The  problem is I can't do it if the Ubuntu PC is locked or logged out.  It  has to be logged in for TightVNC to work.

I need to be able to remote into the Ubuntu PC that is locked out.

---

### Post by YesWeCan on 2011-05-12
If you are not using "remote desktop" service on Ubuntu then you have to use a different service; one that does not involve the local desktop.

There are several apps for this. Here's one:

From your terminal type 'sudo get-install tightvncserver'
To run a new remote desktop type 'vncserver'

The first time you do this it will ask you to choose a password. It will also ask you whether you want a read-only desktop too (probably not).
Then it tells you the number of the desktop that it has created. The first will be "1".

In TightVNC viewer enter the Ubuntu IP address and :1.

More instructions here: [http://www.tightvnc.com/vncserver.1.php](http://www.tightvnc.com/vncserver.1.php)

---

### Post by rollin77 on 2011-05-13
> **YesWeCan said:**
> There are several apps for this. Here's one:

From your terminal type 'sudo get-install tightvncserver'
To run a new remote desktop type 'vncserver'

You don't seem to be paying attention to what I am writing.  I have already very clearly stated that I can access via TightVNC.  That is not the problem.

The problem is TightVNC can't remote into the Ubuntu machine when that machine is logged out.

On the reverse side, I can log into my Windows PC via Ubuntu regardless if the Windows PC is logged out or not.  This is how I want to be accessing the Ubuntu machine because I don't want it constantly logged in.

Anyone else know how I can do this?

---

### Post by doas777 on 2011-05-13
> **rollin77 said:**
> You don't seem to be paying attention to what I am writing.  I have already very clearly stated that I can access via TightVNC.  That is not the problem.

The problem is TightVNC can't remote into the Ubuntu machine when that machine is logged out.

On the reverse side, I can log into my Windows PC via Ubuntu regardless if the Windows PC is logged out or not.  This is how I want to be accessing the Ubuntu machine because I don't want it constantly logged in.

Anyone else know how I can do this?
freenx will allow you to log into sessions even if the server is booted but not logged in.

FreeNX is not overly hard to install (far easier than[ resumable vnc via XDMCP]("http://ubuntuforums.org/showthread.php?t=122402"), your other major option):
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

and install a client from Nomachine.org on your windows machine. 

freeNX is far supperior to VNC. I think you'll like it.

---

### Post by rollin77 on 2011-05-13
That looks promising, but I'm running into some Ubuntu noob issues with installing FreeNX.

At step 4 it says it is "unable to locate package freenx"

It then explains to "cd to the directory to where the script was downloaded and unpack it" - I don't really understand what it is saying to do here.

> (note, as of Aug. 16 2010 the above command doesn't  install a particular script which appears to be missing from the  package. So after performing the above, [download it from here]("https://bugs.launchpad.net/freenx-server/+bug/576359/+attachment/1378450/+files/nxsetup.tar.gz"). Next, cd to the directory to where the script was downloaded (probably your downloads folder) and unpack it: 
**tar -xvf nxsetup.tar.gz**

Then, copy the script to the proper directory: /usr/lib/nx/ with: 
**sudo cp nxsetup /usr/lib/nx/nxsetup**I tried the following commands it gave but neither works.  I'm really noobish with installing anything on Ubuntu, I'm still coming from the Windows mindset of simply double clicking on an icon and I know it's different with Linux so I'm sure this isn't a complex issue I'm having, probably really simple!

---

### Post by YesWeCan on 2011-05-13
> **rollin77 said:**
> You don't seem to be paying attention to what I am writing.  I have already very clearly stated that I can access via TightVNC.  That is not the problem.

The problem is TightVNC can't remote into the Ubuntu machine when that machine is logged out.

On the reverse side, I can log into my Windows PC via Ubuntu regardless if the Windows PC is logged out or not.  This is how I want to be accessing the Ubuntu machine because I don't want it constantly logged in.

Anyone else know how I can do this?
I am trying to help you. What you claim contradicts my experience.
When you log in to Ubuntu from Windows...that is being logged in. VNC is happy with that.

---

### Post by rollin77 on 2011-05-13
> **YesWeCan said:**
> I am trying to help you. What you claim contradicts my experience.
When you log in to Ubuntu from Windows...that is being logged in. VNC is happy with that.
I'm not trying to offend you but telling me how to install TightVNC  right after I made a post about how I already have it running does not  help me at all.  I also have no idea what you mean when you say "VNC is happy with that".  VNC is not a particular program which is what I am asking for.  I need a specific program that can remote into a locked Ubuntu machine.  
And by remote I mean access it completely from a remote PC on my local network so any instructions that include "walk over to it and unlock it" are not helpful.

I think I may have better luck with Freenx but so far I can't get it installed.  I would like to try this if anyone can help with the installation details.

Thanks

---

### Post by doas777 on 2011-05-13
> **YesWeCan said:**
> I am trying to help you. What you claim contradicts my experience.
When you log in to Ubuntu from Windows...that is being logged in. VNC is happy with that.

the way cannonical configured vino (the "Ubuntu Remote Desktop" VNC server), it will only allow connection when the user is logged in, because vino is enabled/disabled per user based on their preferences. so if one user allows vino access, and another disallows it, there is no way to tell which is which when no one is interactively logged in.  one solution to this is to set the ubuntu box to autologin to a desktop that has vino enabled. 

the other approach is to install another VNC server variant and enable XDMCP login, per the link I posted above (resumable VNC via XDMCP).


On to FreeNX:

@Op: when you download a file from the link in the documentation ([https://bugs.launchpad.net/freenx-server/+bug/576359/+attachment/1378450/+files/nxsetup.tar.gz](https://bugs.launchpad.net/freenx-server/+bug/576359/+attachment/1378450/+files/nxsetup.tar.gz)), you download it to a specific directory, like '~/Downloads'.  if I download the script into ~/Downloads, I woudl issue these commands:

```
 cd ~/Downloads
tar -xvf nxsetup.tar.gz
sudo cp nxsetup /usr/lib/nx/nxsetup

```so "cd to the directory to where the script was downloaded and unpack it", means to use the CD command to change directories to the one where the .tar.gz was downloaded to. then you use tar -xvg to unpack/decompress the file. the last line copies the extracted file to /usr/lib/nx/

does that make sense?

alternately you could just specify the full path to the file:
```
 tar -xvf ~/Downloads/nxsetup.tar.gz
 sudo cp ~/Downloads/nxsetup /usr/lib/nx/nxsetup

```

---

### Post by compmodder26 on 2011-05-13
> **rollin77 said:**
> I'm not trying to offend you but telling me how to install TightVNC  right after I made a post about how I already have it running does not  help me at all.  I also have no idea what you mean when you say "VNC is happy with that".  VNC is not a particular program which is what I am asking for.  I need a specific program that can remote into a locked Ubuntu machine.  
And by remote I mean access it completely from a remote PC on my local network so any instructions that include "walk over to it and unlock it" are not helpful.

I think I may have better luck with Freenx but so far I can't get it installed.  I would like to try this if anyone can help with the installation details.

Thanks

tightvncserver is what you install on the ubuntu box.  It is most certainly capable of allowing you to log in to your ubuntu box even if you aren't logged in locally.  I think you are misunderstanding what we are telling you.  When we mention tightvncserver, we are not talking about the client you are using on the windows PC.  We are talking about a server that is run under Ubuntu.

---

### Post by rollin77 on 2011-05-14
> **doas777 said:**
> 
On to FreeNX:

```
 cd ~/Downloads
tar -xvf nxsetup.tar.gz
sudo cp nxsetup /usr/lib/nx/nxsetup

```
When I go to copy I get an error saying no such file or directory   exists.  Using the graphical view I can see that I need the /nx/   directory in the /usr/lib/ directory but I don't know how to do this.    Just tried navigating to /usr/lib/ and issuing mkdir nx but I just got   an error saying permission denied.

> **compmodder26 said:**
> tightvncserver is what you install on the ubuntu box. 
It is most certainly capable of allowing you to log in to your ubuntu box even if you aren't logged in locally. 

[COLOR=black]I have TightVNC server running on the Ubuntu machine.[/COLOR][COLOR=black]  However, nobody has explained exactly how I can log into the locked Ubuntu machine and in my own trial and error I can only log in when the machine is unlocked.  This makes sense to me because if the PC is locked wouldn't TightVNC server not be running?[/COLOR][COLOR=Red]

[COLOR=Black]So if this is possible I need to know how exactly this is done because currently nothing I have tried is working.[/COLOR]
[/COLOR]

---

### Post by doas777 on 2011-05-14
try again, and please post back the terminal output (showing your commands.)

if it fails could you please post 
```
ls -al <dir path>
```
on the directory that contains your .tar.gz file?
the extraction may have created a sub directory with the nxsetup script in it, but that would be abnormal.

---

### Post by coccu on 2011-05-14
> **alphacrucis2 said:**
> That hasn't been true for a long time. Windows can have many RDP clients connecting to it and all see their own individual desktop. This functionality was originally developed by Citrix and MS bought it off them and it has been incorporated into Windows for many years. IIRC by default you only get allowance for two concurrent rdp connections. If you want more then you have to pay licence fees

> **YesWeCan said:**
> OK thanks. That is progress. I withdraw my cynical and erroneous claim. ;)

From what I understand, you'd need to a windows server (Win 2k/2k3/2k8) to have multiple RDP sessions.  But here, we're talking about Win7 which only allow 1 active console at anytime.  

I've running Ubuntu on my laptop for years and am still a newbie.   Coming to the forum for help with RDP topic. Kudos to all your suggestions and advices.  !](*,):confused::(

---

### Post by YesWeCan on 2011-05-14
> **coccu said:**
> From what I understand, you'd need to a windows server (Win 2k/2k3/2k8) to have multiple RDP sessions.  But here, we're talking about Win7 which only allow 1 active console at anytime.
Thanks. Corroboration here: [http://social.technet.microsoft.com/Forums/en-US/w7itpronetworking/thread/d8728606-9d2d-40aa-b028-007a14a5c7be/](http://social.technet.microsoft.com/Forums/en-US/w7itpronetworking/thread/d8728606-9d2d-40aa-b028-007a14a5c7be/)

I now withdraw my withdrawal and **** a snoot at Windows 7. :P
All hail linux!

---

### Post by two4two on 2012-03-01
I realize this is a really old thread thread, but I thought I'd add:  I don't understand all the reason for all the posts.  The native Win7 Remote Desktop Connection client works out of the box with Ubuntu 11.04 (Natty) Studio the way it comes with xRDC installed.  I do it between machines here on our home network.  The only thing is it only works for me within our home network and not from without.  (I guess that's a good thing if I don't want strangers getting in.)  But I WOULD like to connect to my home computer from work.  So can anyone suggest how to do that?  Is this where Teamviewer comes in?

---

