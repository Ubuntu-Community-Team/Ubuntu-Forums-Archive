---
title: "Network sharing files between Ubuntu, W11, and W8.1. How do I set this up?"
date: 2022-01-27
forum: Networking &amp; Wireless
---

### Post by dokimira on 2022-01-27
Hello!

Im looking to network share files between three different systems.

- A Dell laptop running Ubuntu 20.04.3 LTS
- An HP laptop running Windows 8.1
- An HP laptop running Windows 11

However, i'm not entirely sure how to set this up between a Linux system and two windows systems. Additionally, to complicate this further, Windows 8.1 uses Homegroup but W11 and Ubuntu do not.

How would I set something like this up?

---

### Post by TheFu on 2022-01-27
Use sftp to xfer files.  Every platform supports it. It is already included when you install ssh on every Unix-like OS in the world. With key-based authentication, it is secure enough to use over the internet AND very convenient. Almost every Linux file manager supports sftp:// URLs.  sftp uses the same port that ssh uses, so only that port (use a non-standard port on the internet) 

On the LAN, you can use samba/cifs, but it isn't secure enough for internet use.  You can ignore the homegroup, IME.

Basically, I'd pick 1 system to the be "storage server" and setup connectivity to it for the other 2 systems. In my world, that would be Ubuntu. I have a bias.  If you do setup CIFS/Samba, there is a help.ubuntu.com page about doing that. Google finds it easy.  Also, don't use any GUI to setup sharing from the Ubuntu side. Do the text config files.

---

### Post by dokimira on 2022-01-28
I feel like I need to clarify here. I don't know if this is what's being explained, but I was looking for just something where I can get a document on one system and move it to another, not anything involving a dedicated storage system as all laptops have their own uses. Essentially a basic move "grab photo/document from one system and copy it to the other" one. As far as im aware, this would be LAN. Not experienced with Linux at all, so sorry if this is what's been said.

---

### Post by Morbius1 on 2022-01-28
Note: I have no experience with Win8 or homegroups so I don't know how much help I will be there.

What is not clear from your post is if you installed samba on the Ubuntu machine. You will need that first:
```
sudo apt install samba
```
You can create a share in Ubuntu from Nautilus ( File Manager ) if you want by right clicking a folder you own and selecting Local Network Share. Or you can create a more traditional share in /etc/samba/smb.conf. If you need help with this just ask.

After you do that run this command to find the hostname of the Ubuntu server:
```
hostname
```

Now go to your Win11 machine and in explorer enter the network address with that hostname and a **[COLOR="#0000CD"].local [/COLOR]**attached at the end, like this example:
```
\\vubsrv2004.local
```
Which resolves to:
[ATTACH=CONFIG]289908[/ATTACH]
In this case I created two shares on the ubuntu server so that is what shows up.

Because of a bug in Ubuntu you can't do the same from Nautilus ( file manager ) so you have to specify the same hostname.local address but also specify the share name like this:
[ATTACH=CONFIG]289909[/ATTACH]
Which resolves to:
[ATTACH=CONFIG]289910[/ATTACH]
In this case I created a "shared" share on win11.

Discovery of shares on both systems is really not possible on either system since SMB1 has been disabled on both. You can enable WS-Discovery on your Ubuntu system ( with a little work ) so Win11 ( and possibly Win8 - not sure ) can discover it under Network. But from a Win11 perspective you can create a bookmark ( Pin to Quick Access ) to the ubuntu hostname.local machine and access things that way.

---

### Post by TheFu on 2022-01-28
> **dokimira said:**
> I feel like I need to clarify here. I don't know if this is what's being explained, but I was looking for just something where I can get a document on one system and move it to another, not anything involving a dedicated storage system as all laptops have their own uses. Essentially a basic move "grab photo/document from one system and copy it to the other" one. As far as im aware, this would be LAN. Not experienced with Linux at all, so sorry if this is what's been said.

File transfers are a client-server operation.  The client is the machine you are working on and the server is the other machine.  If you want to be able to sit at any machine and transfer files, then all of those machines have to be setup as both the client AND the server.  That applies to Samba/CIFS and to sftp.  

It is ok to use both protocols.  Win10 and later support ssh/sftp - finally - after the rest of the world supported it the last 20+ yrs.

**Servers**
Windows has an sftp server now: [https://winscp.net/eng/docs/guide_windows_openssh_server](https://winscp.net/eng/docs/guide_windows_openssh_server)
Unix-like systems have has an sftp server since the beginning: [https://www.ssh.com/academy/ssh/sftp](https://www.ssh.com/academy/ssh/sftp) It is included with openssh package. The install on Linux is **sudo apt install ssh fail2ban**. That's it. Nothing more. It will work from that point on. If you enable a firewall, then be sure to open 22/tcp from the LAN for access. A firewall isn't normally enabled on Ubuntu like it is on many other distros. Fail2ban is just to block brute force attacks. By default, it protects the ssh server with reasonable defaults.

**Clients**
Windows has FileZilla and WinSCP. I use WinSCP. This is the drag-n-drop stuff.
Linux file managers all support sftp (after openssh is installed). This is the drag-n-drop stuff.
There is always the CLI version, which even I haven't used in years and years. It is exactly the same CLI that plain FTP has provided for 40 yrs. That is by design.

Having name resolution work seems connected, but it is separate. That's the reason that we can say 
```
ping myhost
```
or
```
ping myhost.local
```
instead of 
```
ping 192.168.1.100
```
There are different protocols for the name resolution and there's the old /etc/hosts method.
* DNS, which is what the internet uses and has been around since the late 1980s (I'm guessing).
* mDNS, which is what avahi provides on Linux systems. I don't know if Windows supports it or not. This is also called ZeroConf. All the IoS devices use it. It broadcasts "I'm here and these are the services I offer."  mDNS is part of Ubuntu desktop installs, but not Ubuntu Server. I mainly see it used with media center software.

But dont forget that you can edit the /etc/hosts file on each system to tell it about the other systems on your LAN. With just 3 computers, I'd use this. I did for over a decade.  Windows has a "hosts" file ... buried under the system32/drivers/ directory.

For name resolution to work, all the systems that will run a "server" like samba or sftp should have a static IP on the LAN. This is something that must be manually setup. A mistake is NOT to do this.  Eventually, the computers and router will be off long enough for all the IPs to change if static IPs are not setup.  It is just accounting - keeping the IP and name consistent and known by all systems. If you want a cell phone on wifi to find your computers, then DNS is the only real answer. I've not seen any of my phone/tablet devices with with mDNS, but I have a small DNS server on the network here.

---

### Post by him610 on 2022-01-28
> Windows has a "hosts" file ... buried under the system32/drivers/ directory.

It is actually buried a little further down in 'C:\windows\system32\drivers\etc\hosts'

---

### Post by him610 on 2022-01-28
If the suggested methods in #2, #4, & #5 are too much for you, there are alternatives,...

A) Sneakernet, also called sneaker net, is an informal term for the transfer of electronic information by physically moving media such as magnetic tape, floppy disks, optical discs, USB flash drives or external hard drives between computers, rather than transmitting it over a computer network.

B) email, email yourself the file_2b_xferred from one pc and read it on the other pc.

C) Cloud service, you could upload your file to say, Google Documents from the source pc then download the file to the target pc

---

### Post by TheFu on 2022-01-28
him610 brings up some excellent options.  I'd completely forgotten that there are lots and lots of other methods.
I use a nextcloud server here to get small files and notes between systems like Android. I don't use NC on Windows.

Another option are point-to-point file transfer tools like "**wormhole**" (aka magic wormhole).  This is available on every platform I've looked at, android, Windows, and Linux. There is a server on the internet that negotiates connectivity between the sender and receiver, but the actual transfers are direct and well encrypted. Safe from anywhere.

There is a snap version of wormhole, but it is python, so you don't HAVE to use the snap package. I don't.
The app-stores for phones/tablets have wormhole in them.

But honestly, just learn to use ssh, scp, sftp, and rsync.  Those basic tools are amazing^2 9squared).  Whenever 2 different systems need to communicate, ssh or an ssh-based tool should be the first thought.

---

