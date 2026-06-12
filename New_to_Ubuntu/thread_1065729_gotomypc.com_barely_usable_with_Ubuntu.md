---
title: "gotomypc.com barely usable with Ubuntu"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by occams_beard on 2009-02-10
I have to use gotomypc for work. Sadly however, when logging in under Linux the service is barely usable. I have to connect via the "Univeral Viewer" Java applet which is sorely lacking compared to the default Windows client. It doesn't let you drag and drop files, copy/paste text, etc.  It's just not viable solution for the work I have to do.

Just wondering if anyone might have any ideas, or tips for using gotomypc under Linux.

---

### Post by Hospadar on 2009-02-10
You should really install and use ssh or vnc.
ssh is a command-line remote client that allows you to very securely connect to your home machine and run whatever applications you wish.
vnc is a remote desktop client that works nice, but I've always found ssh to be faster, besides being more secure.
So long as you are ok with running programs from a command line (can you type "firefox" or "nautilus") you should be fine.  ssh also gives you great file transfer capabilities, and you can use an nice ftp client (like filezilla or others) to access your machine.
You should google or check the "community docs" in my sig for more full info, but basically this is going to entail:

1) install the ssh server: just install the "ssh" package from synaptic or a terminal "sudo apt-get install ssh"

2) You need to forward port 22 on your home router to your home machine: this is assuming your home machine is behind a router, port 22 (the port ssh uses) needs to be forwarded to your machine.  consult your router manual on how to do this if you are unsure.  Generally it will involve pointing your web browser at your router and clicking some buttons.

3) learn your external ip address: while you can usually find this out from your router, I think it's easier to go to a site like [http://www.whatismyip.com/](http://www.whatismyip.com/) you will need this address to connect from outside your house (though you can test from inside the house with this address)

4)learn how to use ssh: there are a ton of clients that can connect to ssh.  On linux and  osx, the ssh client is almost always installed by default, on windows you can get a tiny little program called putty (it doesn't even need to be installed).  Putty has a graphical interface to set up connections which is pretty straightforward.  you put in your ip, port 22, it will prompt for your username and password.
on linux or osx, open a terminal, use a command like "ssh [email]my_server_username@my.server.ip.addres[/email]s" and it will ask you to accept a key and then for a password.

5) learn to X11 forward: X11 forwarding is how graphical interfaces go through ssh.  on linux or osx, all you need to do is add a -X or -Y to the ssh command "ssh -Y username@ip", on windows, you'll need to go to connection->ssh->X11 in putty and "enable forwarding.  also you'll need to install and run a windows x server like "xming" (google it)

If anything is unclear, ask more here, or google around, there are a ton of guides to do this.  it is a very simple, secure, and fast way to remotely connect to a linux machine.  And if you get comfortable on a command line, you can get stuff done even faster.

---

### Post by adam_kimber on 2009-02-10
Occams beard, the wiry protrusion that obscures those multiple hypotheses. :D

Anyway onto your question. GotomyPC is a Windows only program unfortunately.  Both Windows and Linux have remote desktop viewing capabilties but unfortunately its not that secure to use these across the internet. Windows uses RDP and Linux VNC. You can get VNC software for Windows. 

Have a look at this [guide]("http://www.linuxplanet.com/linuxplanet/tutorials/6641/1/") and [this]("http://www.linuxplanet.com/linuxplanet/tutorials/6648/1/") for a way of setting out Remote Desktop from Linux to Windows across the Internet.

Question is are you using Linux to access a Windows PC? Not quite sure what the reasons for using the gotomypc service are?

Linux has many options (bascially the method of transferring the data from one machine to the other) for Remote Desktop. If you are not wanting to "play" around much try this [guide]("http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html"). 

Taken from the above link > GoToMyPC.com is a company as with LogMeIn. It provides a third party to your remote connection.

Basically &#8212; It gets around the NAT problems by being a man-in-the-middle as most firewalls will allow outgoing connections on HTTPS. It takes two outgoing connections to its own servers to create a tunnel to see the other PC.

A stand alone tool such as VNC (above) or RDP in the windows world or any such remote protocol (SSH, Citrix) cannot do this as its a point to point connection.

You cant configure such point-to-point remote controlling protocols without revealing it to the internet for people to connect to. thus port forwarding.. There has been moves to make it easier via UPnP but this hasnt really worked well.

I have not found a true equivalent alternative to LogMeIn for Linux (but I understand a LogMeIn client is in the works) but I would be great if such a service could be offered by Canonical or other company. It is possible to setup a service yourself through using SSH tunneling. although you will need another server out there on the internet to act as a man-in-the-middle. Unfortunately this server will require port forwarding.

But if you are more interested in other options. The above method uses VNC, there is also SSH, FreeNX and RDP as far as I know, there are probably more. Have a look at [this]("http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/") as it might be of interest.

---

### Post by adam_kimber on 2009-02-10
> **Hospadar said:**
> You should really install and use ssh or vnc.

5) learn to X11 forward: X11 forwarding is how graphical interfaces go through ssh.  

I think VNC is a better way to go. x11 over ssh is sometimes slow and is tricky to setup. VNC is preferable as Ubuntu has a pretty GUI to help people do the majority of the configuring. :D

---

### Post by occams_beard on 2009-02-10
> 
Not quite sure what the reasons for using the gotomypc service are?


Thanks for the replies but unfortunately that's the only option my employer provides. VNC would be great, but I don't see how it'd be possible to use in conjunction with the gotomypc service.

---

### Post by adam_kimber on 2009-02-10
Can you confirm which way round you are using the service? If you are using Linux to access the work computer (running XP/vista) you could try [this]("http://ubuntuforums.org/showthread.php?t=753437") or you could try using wine......... (I can help this option if you wish).

---

### Post by occams_beard on 2009-02-10
I'm logging into XP boxes from Ubuntu via gotomypc.  I can use their Java applet, aka "Universal Viewer", but it's severely limited. It doesn't allow me to copy/paste text or transfer files, so it's basically unusable for me.

I considered using wine, but it seems doubtful it'll work since I'd need 3 Windows apps to work correctly simultaneously.  A browser, the gotomypc client, and a Windows JRE.  (The gotomypc client requires Java)

The only other option I can think of is running Win2k from VirtualBox. But there again, it'll be a pain to copy/paste and transfer files. Ack, what a complicated mess!

---

### Post by adam_kimber on 2009-02-10
Well I just installed Firefox and JRE on wine and no problems. Get FF from [here]("http://download.mozilla.org/?product=firefox-3.0.6&os=win&lang=en-GB") and JRE from [here]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=27983"). That should download a couple of exes. Just double click them! 

PS You need to install wine first :D

PPS I have not tried using gotomypc as I have no account and am not a big fan of buying it as I have no use for it at the moment :(

---

### Post by yther on 2009-02-10
> **occams_beard said:**
> The only other option I can think of is running Win2k from VirtualBox. But there again, it'll be a pain to copy/paste and transfer files. Ack, what a complicated mess!

Well, you actually *can* copy & paste, at least text, between a VM and the host OS.  For file transfer, I think the easiest way would be to share a folder from inside the Windows VM and connect to it using Samba from the Linux side.  That is easy and fairly transparent; you can even mount the Windows share so that it behaves like a normal folder, very much like "Map Network Drive" works in the Windows world.

I think I might actually prefer that approach to using WINE, and in fact I may soon need to do essentially the same thing because of the extreme crappiness of LogMeIn when trying to use it from a non-Windows machine.  (Again, I need it for work sometimes, just like you.)

---

### Post by occams_beard on 2009-02-10
> **adam_kimber said:**
> Well I just installed Firefox and JRE on wine and no problems. Get FF from [here]("http://download.mozilla.org/?product=firefox-3.0.6&os=win&lang=en-GB") and JRE from [here]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=27983"). That should download a couple of exes. Just double click them! 

PS You need to install wine first :D

PPS I have not tried using gotomypc as I have no account and am not a big fan of buying it as I have no use for it at the moment :(


Woah, I'm impressed! I just tried it and it actually worked!!  Well sort of... Firefox worked, Java worked, but the gotomypc client is kind of flakey.  I can transfer files, but I STILL can't copy/paste text. Also, the window doesn't resize properly, although I could live with that if I could just copy and paste :(

Ah well, guess I'll have to experiment with running Windows in a virtual machine.

---

### Post by niteshifter on 2009-02-10
Hi,

> The only other option I can think of is running Win2k from VirtualBox. But there again, it'll be a pain to copy/paste and transfer files. Ack, what a complicated mess!

Not really, this response comes to you via Word in an XP Guest, running in seamless mode. Your text above copied (Ctrl+C) and pasted (Ctrl+V) into Word, this part filled out and all selected (Ctrl+A) and pasted back (Ctrl+V) into the forum replay page (FF in Ubuntu). Along with a screenshot ;)

---

### Post by occams_beard on 2009-02-10
Absolutely brilliant! This works perfectly :)

---

### Post by kiwiboyus on 2010-07-14
Hi,

I work for Citrix and have another solution for using GoToMyPC on Ubuntu (and Linux in general). If you have a Windows PC or Mac running the GoToMyPC Host software and you want to connect to it from Ubuntu, you can actually use the Windows version of the GoToMyPC Viewer in Wine. All you need to do is install Wine if you don't have it already, and then install the User Agent Switcher extension in Firefox. Set the User Agent Switcher to Windows XP and then when you login to your GoToMyPC account and click Connect you will get the Windows Viewer instead of the Universal Viewer. Download the .exe and then open it with Wine and you're all set. You can transfer files and even stream audio from your Windows PC Host (Mac Host don't have this yet).

I've blogged this [here]("http://glenndcitrix.wordpress.com/2010/07/07/gotomypc-and-linux/") 

Thanks,

---

