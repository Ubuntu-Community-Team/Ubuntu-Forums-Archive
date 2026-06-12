---
title: "Samba, Unison, SSH, and More"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-03-09
This is a single thread for multiple topics. I've been using Linux for a couple of years but have only started using it exclusively (almost) for a few months. I'm getting a new hard drive for my laptop, which means that I'll be using two different computers regularly. This thread is mainly about networking and synchronizing the two computers, but I have a couple of questions on other topics as well.

**How I organize my files now**:
I dual boot between Windows XP and Ubuntu. I keep many of my files on my Windows partition and load the Windows filesystem when I'm on ubuntu. Instead of synchronizing between my windows home directory and my Ubuntu home directory, I just read/write everything to my Windows home directory.

**How I plan to organize my files when my laptop is fixed**:
I plan to dual boot Windows XP and Ubuntu on my laptop and follow a similar structure, but now I'd like to synchronize my the home folder of my Windows partition of my desktop to the Windows partition of my laptop.

Is there another method of organizing files that you use or recommend?
As it is now, my Windows partition is filling up pretty fast. Should I make my Windows partitions bigger because I'll be storing most of my files on them (i.e. music, programming, ebooks)?
If so, what's a good ratio?

**Samba**:
When I'm at home, I'd like to be able to transfer files from my desktop to my laptop and listen to music that's stored on my desktop. Is this easy to do with Samba?

Are there any downsides to this tool?
Is there a more popular networking tool?
If I'm using Windows for one reason or another can I send/receive files using Samba?
Is there a quickstart guide or can someone explain it in simple terms? (I've never set up a network before)
Is Samba (on both Windows and Linux) secure from hackers?

**Unison**:
Since I'll be networking my two computers, I'd like to synchronize my programming projects and possibly some other files/folders. **I've always had trouble with outdated copies of files on different computers and/or partitions. Getting this to work right is important to me.**

Are there any downsides to this tool?
Is there a more popular synchronizing tool?
How can I automate it?
Is there a quickstart guide or can someone explain it in simple terms?
In other words, what's the typical usage of Unison?

**SSH**:
A while back my friend set up SSH on my computer, but I've reformatted since then. I've been trying to set it up myself, but since I won't have the hard drive to my laptop until tomorrow, I haven't been able to tinker with it very much. I'd like to be able to access my desktop when I'm not at my house.

Is there an easy way to set it up?
How about with putty on Windows?

**Evolution Mail**:
I've set up Evolution Mail for my gmail account.

Is there a way to use my hotmail account(s) with my gmail account simultaneously?

**Additional Questions**:
The main applications I use are: PenguinTV (rss reader), Pidgin (IM Client), Subversion (source control), Netbeans (C/C++ IDE), irssi (IRC chat), Chrome (Browser), FogBugz (issue tracking), Evolution (email), Lynx (When I need to browse the net from a terminal).

Are there any other programs that you'd recommend?

If there are any other tips you have for a still beginning Linux user, let me know! And thank you!

---

### Post by EnigmaticCoder on 2010-03-10
Bump.

I know I could probably answer some of these questions if I did more research, but it'd be better to get answers from you all.

---

### Post by undecim on 2010-03-10
About organizing your files:
You can use symlinks to make (for example) your Downloads folder on Ubuntu point to your downloads folder in Windows.

Run "ln -s /media/Windows/Users/username/Downloads ~/Downloads"[/s] where /media/Windows/Users/username/Downloads is the location on Ubuntu for your Windows downloads folder. You can do this with any other folder in your home directory, too.

About Samba:

You will probably have to edit /etc/samba/smb.conf

There are settings there already that will allow you to share your home directory, but they are commented out (i.e. have # in front of each line). Find those lines and uncomment them to access your files over the network. After that, run the command "sudo service samba restart" from a terminal.

Samba is designed to work with windows. You can map a network drive from windows to point to your Samba share.

Samba is probably less secure than other filesharing solutions (sftp, for example), because it is designed to be compatable with Windows' file sharing protocol, which isn't ver secure.

About SSH:
setting up SSH is fairly simple. Just run "sudo aptitude install openssh-server" from a terminal. Then you will be able to connect from another computer on your network either with putty (Windows) or with the ssh command (Linux, and probably Mac)

If you want to be able to access SSH outside of your network, you need to set up port forwarding on your router for port 22. However, having port 22 on your router will end up with a lot of hacking attempts, so it's recommended that you use a different port. If you are lucky, your router will support different incoming and outgoing ports. If you are unlucky, you will have to change the port number in /etc/ssh/sshd_config and the run "sudo service sshd restart"


If you need me to be more specific with anything here, let me know by posting here.

---

### Post by Morbius1 on 2010-03-10
> **Samba**:
When I'm at home, I'd like to be able to transfer files from my desktop to my laptop and listen to music that's stored on my desktop. Is this easy to do with Samba?If you're using gnome on the desktop then it couldn't be easier:

Open Nautilus
Right click on say... /home/your_username/Music
Select "Sharing Options"
Mark one or all of three boxes
Select "Create Share"

You just created a share.

---

### Post by EnigmaticCoder on 2010-03-10
"If you are lucky, your router will support different incoming and outgoing ports."
Yes it supports different incoming and outgoing ports. For incoming I put any, for outgoing I put 2222. Is that right?

"setting up SSH is fairly simple. Just run 'sudo aptitude install openssh-server' from a terminal."
It was already installed. Does it automatically start when ubuntu boots up?

You said I could use SFTP. Is there a quickstart guide for that?

Great information overall guys. Thank you!

---

### Post by undecim on 2010-03-10
> **EnigmaticCoder said:**
> "If you are lucky, your router will support different incoming and outgoing ports."
Yes it supports different incoming and outgoing ports. For incoming I put any, for outgoing I put 2222. Is that right?

My router (a linksys) calls it internal and external ports. The external port being the one you would connect to from the internet. You want to set it up so that you can connect to a port other than 22 from the internet to reach port 22 on your server.

Also, in addition to port forwarding, you may need to set up either DHCP reservation (available on some routers) or a static IP for your server (done from the server, as described [here]("http://codesnippets.joyent.com/posts/show/319")), if your router doesn't allow you to forward ports based on MAC address or host name.

If you aren't quite sure what to do with your router, post the model number of your router and I can look up specific instructions on port forward, etc.

> **EnigmaticCoder said:**
> "setting up SSH is fairly simple. Just run 'sudo aptitude install openssh-server' from a terminal."
It was already installed. Does it automatically start when ubuntu boots up?

You said I could use SFTP. Is there a quickstart guide for that?

The SSH daemon will start when Ubuntu does, unless it was configure not to. SFTP is FTP over SSH. If you have SSH set up, you can use it.

From Ubuntu (or any other distro with gnome) you can just go to sftp://[user@]server[:port] in a file manager. Leaving out the brackets. The parts inside the brackets are optional. If you use the same username, you don't need to user part, and if you are using the default port, you don't need the port part.

From windows, you can access those files with an SFTP client such as FileZilla.

---

### Post by EnigmaticCoder on 2010-03-10
"If you aren't quite sure what to do with your router, post the model number of your router and I can look up specific instructions on port forward, etc."
*snip* (I think that is an 'I' and not a '1')

"Also, in addition to port forwarding, you may need to set up either DHCP reservation (available on some routers)"
I don't have a static IP, so I think this is the way to go.

---

### Post by undecim on 2010-03-10
> **EnigmaticCoder said:**
> I don't have a static IP, so I think this is the way to go.

I was referring to a static IP on your network, not the internet. All of you computers are behind your router, and share the router's IP address, so setting up static IPs inside your network is fine.

Although you can also use a dynamic DNS service if you don't want to keep checking your IP address.

I use a subdomain from freedns.afraid.org, but there are many other dynamic dns services out there.

I found a PDF manual for your router, but it's got ~20 minutes left to download (it's only going 3kbps!). Once it's done, I'll take a look at it and see what exactly you need to do.

---

### Post by undecim on 2010-03-10
Looking at the manual, this appears to be what you need to do:


From your router's security page, click "Add Port Forwarding Rule" from the port forwarding page.

For "Networked Computer / Device", you should be able to enter the hostname of your computer (the part that shows up between @ and : from the command line).

The manual isn't quite clear on "Protocol". I think this is for the external port, since there is no other option for this. If there is an option in the drop-down box for selecting a port, choose a number from 1024 to 65535

"Wan Connection Type" shoud be "All Broadband Devices".

"Forward to Port" needs to 22.

"When this rule should occur" is up to you. It will dictate what time of day you will be able to connect to your server from the internet.


Since we can use a host name here instead of an IP, we don't need to worry about DHCP reservation or static IPs. To test it, go to [www.whatismyip.com](www.whatismyip.com) to get your internet IP address, and then try to ssh to that IP address and the port number you chose. From a Linux command line this will do just that```
ssh -p XXXX Y.Y.Y.Y
```where XXXX is the port you used in the "Protocol" option, and Y.Y.Y.Y is your IP address.

---

### Post by EnigmaticCoder on 2010-03-10
Hmmm, I see this when I "Edit Service" and click "Add Server Ports"

[IMG]http://img535.imageshack.us/img535/4370/screenshotbbf.png[/IMG]

---

### Post by undecim on 2010-03-10
Guess I had the wrong manual...

Source port should be a number from 1024 to 65535

Destination port should be 22

---

### Post by EnigmaticCoder on 2010-03-10
Thank you!

I'll be able to try out ssh after I install my new hard drive :)

---

### Post by EnigmaticCoder on 2010-03-22
I finally got my laptop hard drive installed, but I'm having problems with SSH. SSH works fine over the local network, but I fear I'd have problems if I was away from home. I went to canyouseeme.org, and tried it out with port 22, 80, and 8080. Every time I try it, it replies with: connection timed out. Is port forwarding not set up correctly?

Also, how can I force ssh to use a password AND a key?

---

### Post by undecim on 2010-03-22
From outside your network, you should see open whatever source port you chose when setting up port forwarding, and when connecting you will need to use the "-p port" option.

As for SSH requiring a password and a key, I don't know how to do that, but you can put a password on your key which is better, because if someone steals your laptop, they still have to use your password to get the key.

---

### Post by EnigmaticCoder on 2010-03-22
Putting a password on the key -- ingenious! (How do I do this btw)

About the port forwarding, I get the same message with the source port I chose.

---

### Post by undecim on 2010-03-22
When creating your key, you should be prompted to enter a passphrase. This will encrypt your private key, so your private key becomes worthless without the password.

Sounds like a port forwarding problem. Did you make sure your destination port is 22, and protocol is TCP?

It may also be that your ISP is blocking that port (for example, maybe you chose a port related to some filesharing protocol)

See if the command "ssh -p [port] [your IP]" connects from your local network, where [port] is your WAN port (the source port) and [your IP] is your WAN IP (as you see from canyouseeme.org)

---

### Post by EnigmaticCoder on 2010-03-22
> **undecim said:**
> Sounds like a port forwarding problem. Did you make sure your destination port is 22, and protocol is TCP?
Yes

> **undecim said:**
> It may also be that your ISP is blocking that port (for example, maybe you chose a port related to some filesharing protocol)
I still need to look into this.

> **undecim said:**
> See if the command "ssh -p [port] [your IP]" connects from your local network, where [port] is your WAN port (the source port) and [your IP] is your WAN IP (as you see from canyouseeme.org)
I tried this, but the terminal responded with connection refused.

---

### Post by undecim on 2010-03-22
> **EnigmaticCoder said:**
> I tried this, but the terminal responded with connection refused.

In that case, you do not have the port correctly forwarded, or are using the wrong port/IP.

Look around in your router's HTTP interface and make sure that your WAN IP address corresponds with what you see at canyouseeme.org

---

### Post by EnigmaticCoder on 2010-03-22
"Look around in your router's HTTP interface and make sure that your WAN IP address corresponds with what you see at canyouseeme.org"

It's definitely the same IP

"In that case, you do not have the port correctly forwarded, or are using the wrong port/IP."

This is what I see. Is there something incorrect?

[IMG]http://img203.imageshack.us/img203/713/screenshotverizongoogle.png[/IMG]

As an added note, I tried canyouseeme.org from the Desktop and the laptop.

---

### Post by undecim on 2010-03-22
I assume that EnigmaticLinux is the name of your server? that is the only thing I can think of that could be wrong with this.

---

### Post by EnigmaticCoder on 2010-03-22
> **undecim said:**
> I assume that EnigmaticLinux is the name of your server? that is the only thing I can think of that could be wrong with this.

Yep, that's the name of the server.

Is it odd that I can't see port 80 open on canyouseeme.org?

---

### Post by undecim on 2010-03-22
> **EnigmaticCoder said:**
> Yep, that's the name of the server.

Is it odd that I can't see port 80 open on canyouseeme.org?

Unless you have it forwarded, no.

If you are referring to your router's http interface, that is only available from inside the network for security reasons, unless you configure it otherwise

---

### Post by EnigmaticCoder on 2010-03-22
"If you are referring to your router's http interface, that is only available from inside the network for security reasons, unless you configure it otherwise"

I'm not sure what you mean by this.

---

### Post by undecim on 2010-03-22
> **EnigmaticCoder said:**
> "If you are referring to your router's http interface, that is only available from inside the network for security reasons, unless you configure it otherwise"

I'm not sure what you mean by this.

port 80 is the http port. You can't connect to your router's settings from outside your network, so port 80 should not be open unless you have that port forwarded to your server running a web server.

---

### Post by EnigmaticCoder on 2010-03-22
Ok, I get it now, although I'm still stuck.

---

### Post by EnigmaticCoder on 2010-03-22
I tried using tcp->any->22, and canyouseeme.org replied with success when I did it, but I don't want the insecurities of leaving port 22 open. I'm going to try a port other than 2222, do you have any suggestions?

---

### Post by EnigmaticCoder on 2010-03-22
Is it very dangerous to have the source port as any and the destination port as 22?

EDIT: I tried a few different permutations and got a different error message: Connection refused (opposed to timed out).

---

### Post by undecim on 2010-03-22
> **EnigmaticCoder said:**
> Is it very dangerous to have the source port as any and the destination port as 22?

EDIT: I tried a few different permutations and got a different error message: Connection refused (opposed to timed out).

Having port 22 open means that your SSH server will get attacked more.

Attackers looking to get access to an SSH system will try common usernames and passwords to try to gain access to an SSH system that has port 22 open. That means if you have port 22 open and one of your users has a weak password, an attacker will likely gain access to your computer and use it for evil purposes unless you have it very well locked-down.

I would try a different source port first. something in the 1000's maybe.

---

### Post by EnigmaticCoder on 2010-03-22
"I would try a different source port first. something in the 1000's maybe."
I tried several combinations: 2000, 1025, and something in the 100s, but none of them worked.

"Attackers looking to get access to an SSH system will try common usernames and passwords to try to gain access to an SSH system that has port 22 open. That means if you have port 22 open and one of your users has a weak password, an attacker will likely gain access to your computer and use it for evil purposes unless you have it very well locked-down."
That sounds intimidating. Is there a way to setup ssh to only allow keys and not take any passwords?

---

### Post by EnigmaticCoder on 2010-03-22
I got a success with it set up like this. Will this work, and is it secure?

[IMG]http://img405.imageshack.us/img405/6697/screenshotig.png[/IMG]

---

### Post by undecim on 2010-03-22
That setup connects to SSH or just shows the port open?

Because from what I'm looking at, it shouldn't be doing either, unless you changed /etc/ssh/sshd_config to use port 2222.

---

### Post by EnigmaticCoder on 2010-03-22
Yes, the setup connects to port 2222 and to ssh. Port in the config is 22.

---

### Post by undecim on 2010-03-23
I guess I misunderstood the image. Looks like you've got it figured out.

Also, if you want to secure your server a litte more, start by setting up public key encryption, and the change the line in /etc/ssh/sshd_config from
```
#PasswordAuthentication yes
```

to become
```
PasswordAuthentication no
```

This will make it impossible to log into the server without your private key.

---

### Post by EnigmaticCoder on 2010-03-23
Thank you for all your help. I'm going to mark this thread as solved.

---

