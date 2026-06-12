---
title: "Trying to get SSH and VNC to work"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by M4573R on 2011-03-18
I'm trying to follow this guide: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
While seemingly very straight forward, I am completely lost. I am not a adept at the command-line.
I'm trying to connect to my ubuntu machine from my windows machine.

I downloaded the applications, everything seems fine on the windows end, but I cannot for the life of me setup my ubuntu box. It alludes to using SSH, but doesn't give sufficient instructions to set it up with x11vnc.

So far I have the programs installed, and this added to my  /etc/gdm/Init/Default:
/usr/bin/x11vnc -safer -localhost -shared -forever -usepw -auth /var/lib/gdm/:0.Xauth -display :0

I do not know if the -auth is correct for what I'm doing. I'd like anyone I give the IP / pw to to be able to connect to my machine (friends).
I set the password using:
x11vnc -storepasswd

I also have my router forwarding port 22 to my ubuntu machine.

That's basically where I'm at. I don't think VNC is successfully running startup, as I did not see it listed in the running applications list, however after using the example command line after login, it did work and show up.

I assume there is more SSH stuff to setup, but I can't figure it out... There are public and private keys I have to manually handle I guess? I'm finding instructions for getting a public key (I used the ssh key generator), but do I put one of them on EVERY machine I want to connect to unbuntu box? Seems ridiculous.

Anyways, I'm confused and frustrated for something I wanted to be a fun project. Some help would be GREATLY appreciated. :C

So I was able to SSH into my ubuntu box using putty, but the tutorial says to run the x11vnc command line, but should it already be running on the machine? I can't get TightVNC to connect to it now. I cant even connect to Vino anymore.

---

### Post by dfreer on 2011-03-19
I can help with this, but not so much tonight. I'll try to give you a quick overview of how I set my machine up for my parents:
[LIST]
[*]My ubuntu machine is set up to accept only SSH connections from the internet.
[*]TightVNC server is installed to only accept connections from the ubuntu machine **itself**, the localhost. It will not accept connections from the internet. 
[*]Ubuntu is running DynDNS so I can access it remotely using a friendly name like mymachine.dyndns.com instead of an IP address (which is subject to change periodically).
[*]I use a private/public key pair with SSH so that I don't have to enter a password, it just connects automatically and I lock out password use altogether so anyone wanting to connect needs my key. It's a bit more secure this way.
[*]From there, I SSH into mymachine.dyndns.com. I then use SSH port tunneling to tunnel to VNC port to my local machine.
[*]I then connect my VNC client on my local machine to the port I just forwarded. I now have a SSH encrypted VNC session.
[*]I wrote a windows *.bat script, created two windows registry keyfiles, and put all of this along with my SSH key into a folder.
[*]Now, all I have to do to connect to my machine is doubleclick my *.bat file from **any machine anywhere**. If I want others to connect, I simply pass them the whole folder and they can now doubleclick and connect. 
[/LIST]

Does this sound like what you would like to do? I can provide detailed discussions on each step later, or if you would like to change anything (like just use a password with SSH instead of the key pair) I can help with that too. Tonight I'm off to bed.

---

### Post by krunge on 2011-03-19
Yes, the "-auth" option should not be used for /etc/gdm/Init/Default startup.  Neither should the "-display ..." option be used in /etc/gdm/Init/Default. Note that the values you set for these options may "just happen" to be correct.

I think the problem you may be having is that all commands run in
/etc/gdm/Init/Default must be put into the background.  Are you doing this? It doesn't look like it from your command line.   To put x11vnc into the background either put a "&" at the end of the cmdline (i.e. standard unix shell backgrounding) or use the x11vnc "-bg" option.

---

### Post by M4573R on 2011-03-19
So I was able to get it working. Because I am a noob, I wasn't familiar with the login@computerName syntax, so I hadn't set up SSH correctly. So I can now SSH into the box and use TightVNC. I'm not sure if the command line on startup is correct though. I just used the one from here: [https://help.ubuntu.com/community/VNC/Servers#x11vnc-before-login](https://help.ubuntu.com/community/VNC/Servers#x11vnc-before-login)

So now that it seems to be working fine, how can I make it more secure? Seems like anyone could sniff my IP on port 22 and start brute-forcing my login. How do I use the public key I generated?

---

### Post by dfreer on 2011-03-20
You add the public key to your ~/.ssh/authorized_keys file. The SSH server is configured by default to check that folder for keys, and from there you can login with both key and password.

Once you got the key working, then you want to edit your /etc/ssh/sshd_config file to change the PasswordAuthentication from Yes to No. Now only public/private key logins are accepted.

---

### Post by asmoore82 on 2011-03-20
You might like the howto in my signature, it's getting some age on it but
the machine I worked out the procedure on has been smooth sailing ever since,
with multiple hits from all around my workplace on SSH, VNC and RDP.

---

