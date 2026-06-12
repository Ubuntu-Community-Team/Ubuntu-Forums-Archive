---
title: "How to remote desktop from Windows to XUbuntu?"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by krijg87 on 2010-04-27
I'm running XUbuntu 9.10 on my laptop and Windows XP Pro on my desktop. I'd like to be able to connect to my Windows PC from anywhere, but I'm not sure what the best solution is.

Since XUbuntu is running on Xfce and I'd like to keep memory usage low, I'd rather not install a Gnome based remote desktop application. The tutorials I found so far either used a Gnome based app or were very outdated posts. Can anyone give me some hints which applications would be best to use?

---

### Post by cuberts on 2010-04-27
> **krijg87 said:**
> I'm running XUbuntu 9.10 on my laptop and Windows XP Pro on my desktop. I'd like to be able to connect to my Windows PC from anywhere, but I'm not sure what the best solution is.

Since XUbuntu is running on Xfce and I'd like to keep memory usage low, I'd rather not install a Gnome based remote desktop application. The tutorials I found so far either used a Gnome based app or were very outdated posts. Can anyone give me some hints which applications would be best to use?gnome (ubuntu) comes with an inbuilt vnc server called vino. I'm assuming that xcfe (xubnutu) doesn't come with anything similar.

Install vnc4server from the repositories and search for a how to to set it up.

Then install a vnc client in windows (I can recommend "xming" - google it) and configure it to connect to vnc4server (really easy).

If you're connecting via a router, remember to forward port 5900 to your xubuntu PC.

---

### Post by bodhi.zazen on 2010-04-27
Just keep in mind VNC is very insecure and is one of the most commonly cracked servers on these forums.

I would advise you use FreeNX , it works with both Linux and Windows, is faster, and more secure.

Better would be ssh. You can forward X applications with -X

ssh -X user@server

You can tunnel VNC over ssh.

Windows ssh client = Putty
Windows X server = Xming

If you use ssh, use ssh keys and install denyhosts or fail2ban.

---

### Post by krijg87 on 2010-04-27
> **bodhi.zazen said:**
> Just keep in mind VNC is very insecure and is one of the most commonly cracked servers on these forums.

I would advise you use FreeNX , it works with both Linux and Windows, is faster, and more secure.

Better would be ssh. You can forward X applications with -X

ssh -X user@server

You can tunnel VNC over ssh.

Windows ssh client = Putty
Windows X server = Xming

If you use ssh, use ssh keys and install denyhosts or fail2ban.
Ew, I just did an apt-get install vnc4server. Do I safely remove it with 'apt-get remove vnc4server'? 

My remote desktop connection would only go one way; from XUbuntu to Windows, so I thought security wouldn't be an issue? I have no anti virus or firewall installed atm and I'm not too advanced in Linux so I'm unsure what the security implications are. 

I noticed I have ssh pre-installed on XUbuntu, but I thought that was only shell based without a GUI. What is meant by tunneling over ssh and forwarding X applications?

---

### Post by arrrghhh on 2010-04-27
It's best to use aptitude to install programs.  This ensures clean removals.

Tunneling over ssh is a way to run applications remotely using SSH.  So you can run the application on a remote machine on your local computer using the -X switch with SSH.  It's a little slow unless you're on a LAN.

FreeNX is very nice, but a PITA to setup.  If you can get it configured, it's probably the best, full remote desktop solution I've seen/used for Linux.

---

### Post by 2hot6ft2 on 2010-04-27
> **arrrghhh said:**
> It's best to use aptitude to install programs.  This ensures clean removals.

Tunneling over ssh is a way to run applications remotely using SSH.  So you can run the application on a remote machine on your local computer using the -X switch with SSH.  It's a little slow unless you're on a LAN.

FreeNX is very nice, but a PITA to setup.  If you can get it configured, it's probably the best, full remote desktop solution I've seen/used for Linux.
I like aptitude for a few reasons but there is a bug I read about that comes into play if the terminal window size is an odd number. Beats me, but I read it here in the forum from someone with a very good reputation so I took it to be good info.

The ssh client is installed by default but not the server.
FreeNX is not that hard to install and with ssh and FreeNX you get speed, flexibility and security.
There is a guide in my signature which is how I set it up between 2 ubuntu machines. But it should be the same for the xubuntu part.
The windows part of your setup is just going to be the client so it shouldn't be too hard to set up. there is a lot of documentation on the nomachine website that should be helpful for that part.

I have flashed my router with DD-WRT firmware so I included that in the guide but you should be able to do the same with yours by adjusting the instructions to fit your routers menus and settings.

It's the best way I've found to remote desktop.

---

### Post by bodhi.zazen on 2010-04-27
> **krijg87 said:**
> Ew, I just did an apt-get install vnc4server. Do I safely remove it with 'apt-get remove vnc4server'? 

My remote desktop connection would only go one way; from XUbuntu to Windows, so I thought security wouldn't be an issue? I have no anti virus or firewall installed atm and I'm not too advanced in Linux so I'm unsure what the security implications are. 

I noticed I have ssh pre-installed on XUbuntu, but I thought that was only shell based without a GUI. What is meant by tunneling over ssh and forwarding X applications?


If you want to connect to your windows box, you need a VNC server on Windows and a VNC client on Xubuntu.

The VNC server is a potential security risk on any OS, Windows or Linux.

Yes you may remove the vnc4sever from Xubuntu, it does not sound as if you will be using it.

---

### Post by 2hot6ft2 on 2010-04-27
How to remote desktop from Windows to XUbuntu?
> **krijg87 said:**
> I'm running XUbuntu 9.10 on my laptop and Windows XP Pro on my desktop. I'd like to be able to connect to my Windows PC from anywhere, but I'm not sure what the best solution is.

That's just the opposite of the title of the thread.
Title = windows (client) > Xubuntu (server)
Your post = Xubuntu (client) > Windows (server)
:confused:

---

### Post by krijg87 on 2010-04-28
> **2hot6ft2 said:**
> How to remote desktop from Windows to XUbuntu?

That's just the opposite of the title of the thread.
Title = windows (client) > Xubuntu (server)
Your post = Xubuntu (client) > Windows (server)
:confused:
You are right, my bad - it was late yesterday. :) I can't edit the thread title anymore though but I meant connecting from XUbuntu to a Windows PC. 

Anyway, while Googling some I found out XUbuntu had its own remote desktop application pre-installed; Vinagre. I installed TightVNC on my XP Pro, allowed TightVNC in my firewall and was able to connect without a problem using interal IP's. I found that both TightVNC and Vinagre use port 5900, so I forwarded this port to the desktop PC I want to connect with. I'm however unable to connect using my external IP, even if I disable the firewall on my XP PC.

Furthermore, when I choose to remote desktop in full screen, I'm unable to close the full screen - I have to kill the client from my XP PC.

Thanks for all the replies!

---

### Post by Steven_S on 2010-04-28
A configuration-free solution is Teamviewer ([http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)) - free for non-commercial use. I have tried it a few days ago, and it works great.

---

