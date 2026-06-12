---
title: "Help: How to make an FTP drone"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by custommadename on 2007-06-26
Hey, everybody.  I'd like to make my Ubuntu Server Edition 6.06 an FTP server.  I need to make just a username and password to access a directory.  I'm used to using a GUI, but I can't get mine to install.  In case I can use only the Terminal for now, how do I set up FTP access to a main directory?

Thanks!

---

### Post by Maxtorm on 2007-06-26
You can install vsftp (available in the repos via apt-get install) and then consult this page [http://articles.techrepublic.com.com/5100-1035_11-5034763.html](http://articles.techrepublic.com.com/5100-1035_11-5034763.html) for a good run down on setting it up.

---

### Post by custommadename on 2007-06-26
Thanks for that great post.  I'm just wondering, though, how to put it on the drive without a GUI.  There's a server set of File & Domain on Windows Server 2003.  Can I download VSFTP to a directory and navigate to it via 192.168.../directory?

---

### Post by Maxtorm on 2007-06-26
If I understand the question, in the terminal session on the Ubuntu 6.06 Server, type the following:
```
sudo apt-get install vsftp
```

---

### Post by custommadename on 2007-06-27
I tried this, and I just got this message:
E: Cannot find package gnome

A lot of the stuff I'd like to install I just can't because I keep getting that message.  Is there a greater problem?

---

### Post by Maxtorm on 2007-06-27
I don't get it.  VSFTP does not depend on gnome.  It *might* indicate a problem with your sources.list file.  Can you post it here?  To do so:
```
cat /etc/apt/sources.list
```

---

### Post by custommadename on 2007-06-27
I'm sorry.  I meant to type "can't find vsftp."  Gnome is just another message I get.  Basically, I can only install ssh-server, and that's fine.  However, everything else I try to install comes back as "Cannot... (program)."

---

### Post by Maxtorm on 2007-06-27
That would indicate a problem with the repositories.  Either you don't have the repository enabled that vsftp is in or apt can't establish a connection with the Internet.  Is the server connected to the Internet directly or is it going through a proxy server (or some other manner of connection)?

---

### Post by custommadename on 2007-06-27
The PC is connected to wall plug 8, which goes from a patch panel port 8 to port 3 on a 24-port Netgear gigabit switch.  That switch is connected to a pfSense firewall, a Windows Server 2003 domain controller, and a Windows Server 2003 file server.

So...  When I connected a Windows 2000 PC to this very ethernet cable yesterday, it went right through to DHCP and such.  It really had no problem connecting with everything set to Automatic.

---

### Post by custommadename on 2007-06-27
I typed sudo apt-get install ubuntu-desktop, and now I'm installing a GUI.  From there, I'll download VSFTP with a web browser.

---

### Post by custommadename on 2007-06-27
The GUI installed, but nothing happened, and ls won't show me any trace of new files.

---

### Post by Maxtorm on 2007-06-28
I'm not sure having the GUI is going to be of any assistance if you don't have access to the repos.  However, if you installed ubuntu-desktop successfully, the following command should invoke it:
```
sudo /etc/init.d/gdm start
```
I'd also be interested to know what the following command returns:
```
sudo apt-get update
```
That should confirm or deny the existence of a connection to the repositories.

---

### Post by custommadename on 2007-06-28
sudo apt-get update actually works!  I left the PC on all night, and now I'm in a GUI.  I'm chatting through Gnome!

---

### Post by Maxtorm on 2007-06-28
Excellent!  So, now, how have you made out with the FTP server?

---

### Post by custommadename on 2007-06-28
Hey, thing seem to be going well.  I'm now on the forum with just Ubuntu Server.

I unzipped VSFTP, but I still can't find it.  The folder's on the Desktop, so I'm at /Desktop/vsftpd-1.2.2/

Not much is running, though.  Here's what I type in:
sudo apt-get install vsftp

Here's what I get:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vsftp

I'm going to look into this with the Readme and such, but I'm wondering if you could provide more in-depth help?  That would be great.

Thanks!

---

### Post by Maxtorm on 2007-06-28
Oh geez... I feel like a complete knob here.  Please append a "d" to the end of that line:
```
sudo apt-get install vsftp**d**
```
REALLY sorry I didn't see that long ago!

---

### Post by custommadename on 2007-06-28
Yes!  It works!  This is awesome!
Actually, I'm just installing.  Regardless, IT'S AWESOME!

---

### Post by custommadename on 2007-06-28
Also, no problem about that letter.  Don't worry about it at all.

---

### Post by custommadename on 2007-06-29
Well, it seems I have the FTP running.  VSFTP is up, and the only problem is that Tech Republic's tutorial leaves me at mkdir/var/ftp because that never gets the proper result.  Aside from me not being able to get VSFTP to work properly because it keeps telling me the directories that I try to create don't exist yet, I think I've done this pretty well.  However, would you mind helping me rule out these recurring issues?  On the link you gave me, I'm stuck on the step right after creating the "nobody" user name.

---

### Post by Maxtorm on 2007-07-02
Sorry, I was AFK for a few days.  Did any of the commands that followed the "nobody" section give you issues?  See below as excerpted from the article:
```
mkdir/var/ftp/
``` 	Creates a directory named /var/ftp.
```
/usr/sbin/useradd -d /var/ftp ftp
``` 	Creates a user named "ftp" with the home directory /var/ftp. On many systems, this user will already exist.
```
chownroot.root /var/ftp
``` 	Changes ownership of the /var/ftp directory to the root user.
```
chmodog-w /var/ftp
``` 	Removes the write permission from others and groups.

---

### Post by custommadename on 2007-07-02
Starting at the first line of the codes you typed out, the server responded negatively.  I can't really tell you the error message exactly because the power supply exploded, and the hard drive had a head crash.

I'm going to install this on the following PC:
Asus A8R32-MVP
AMD Athlon64 3800
1.75GB of DDR333 memory
2x250GB IDE hard drives

That should hold up without a head crash for quite a while.  The drives will be mirrored, so everything should be all right.  I'll let you know when I have the PC formatted & ready to go so I can retry the FTP lines.

Thanks!

---

### Post by Maxtorm on 2007-07-02
Heh... yeah... those specs should be adequate for a server!  Are you going to make another attempt without the gui?

---

### Post by custommadename on 2007-07-03
Yeah, I think the GUI really wasn't necessary.  However, I also want to get the PC to play on-hold music for my phone system.  Could I do that without a GUI?

---

### Post by Maxtorm on 2007-07-03
In general (very general) I would think you can do anything without a gui that doesn't require user interaction.  What are you thinking about using for your audio source?  Are you thinking about setting up a full-blown phone system like Trixbox ([http://www.trixbox.org/](http://www.trixbox.org/))?

---

### Post by custommadename on 2007-07-10
Hello.  I was just running Winamp on the Server 2003 machine, but the board has onboard HD audio, and I need a separate driver for that all of a sudden.  I was told this wouldn't work initially, but I installed Winamp & the audio driver without Microsoft's HD suppor thing I couldn't find.  It worked, and then it stopped working.  Regardless, it was just a test.

We actually have a phone service hosted by a couple of rackmount devices, and we'll switch that over to something like what you've mentioned.  Until the switch, there needs to be something playing audio into the phones.

By the way, we got all our parts in, but we just can't get the PC to boot.  The board was working, and then the CPU went bad.  When the new processor came in, the entire thing just died.  It's a very awkward situation, and I'll keep trying to get this thing up and running.  Hopefully, we should soon have dual 500GB SATA drives for a RAID 1.  It'll be awesome.

---

