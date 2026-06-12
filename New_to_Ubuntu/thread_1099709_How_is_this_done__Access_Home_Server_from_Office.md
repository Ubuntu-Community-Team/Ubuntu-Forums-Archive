---
title: "How is this done?  Access Home Server from Office?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Kellemora on 2009-03-18
Hi Gang

Actually, don't need to know HOW to do it, just WHAT it's called so I can look it up and study it myself.

I had asked a friend to bring some paperwork to a meeting for me, naturally they forgot it, said it's at home.  But Wait a second!

She asked another person if they could borrow their computer for a second, it was a laptop with a cellphone link stuck in the side.

They connected to their Home Computer (on a strangers computer) downloaded the file I had requested to the SD card from my Palm.

I asked how they did that and she said, don't know, my hubby set it up for me since I always forget things.  
She connects to her ISP using a normal www URL on Firefox and a home page pops up and on that home page was a link (password protected) that took her to her home computers shared folders, they WERE NOT on the physical ISP's web site.

She said she keeps ALL of her data in various shared folders at Home and can get to ALL of them just by going through her web page.

If I KNEW what search criteria or name to use for this, I wouldn't be bothering you guys about it.  But I'm 2 hours into doing searches and producing NOTHING at all similar.  LOTS of ways to connect to my home computer IF it was set up for outside access, but none through my URL.

Thanks

TTUL
Gary

---

### Post by gn2 on 2009-03-18
Firstly, my knowledge of this is limited, so apologies in advance for any errors/omissions.

Your router at home will have an IP address assigned to it by your ISP.
On a computer elsewhere, entering this address into Firefox's address bar will connect you to the router.

You need to configure the router and it's firewall to allow access through to your computers and network devices, which must be left switched on.

Some ISP's do not allocate static IPs which means that the address for your network keeps changing.
This can be got around by using [DynDns.org]("http://www.dyndns.com/services/dns/dyndns/"), you configure a named url and DynDns tracks changes to your IP and updates as required so that the DynDns named url keeps pointing at your home network.

Some routers have the ability to be set up to update the IP directly to DynDns.org in their configuration pages.
If your router does not have this facility it is possible to configure a computer to do it.

As for how to set up computers to be accessible, I don't have a clue, I've only done this for security webcams....

An interesting little device is the [Linksys NSLU2]("http://en.wikipedia.org/wiki/NSLU2") which is a Network Attached Storage device and can be easily configured to allow access from the internet.
I have one and can recommend it, but mine is not configured to be accessible from the www.

---

### Post by thomps on 2009-03-18
Hey Kellemora,

I'm not sure if this is what you are looking for or not, but I know of a company that allows this type of connection for Windows and Macs.  The company is logmein.com.  You create an account and add the computers at home.  Then, wherever you are you access your account from logmein.com and you have "Remote Control" of your computer.  No firewall config, etc. required.

thomps

---

### Post by mlentink on 2009-03-18
I agree. LogMeIN most likely

Another possibility is That they use a NAS (Synology?) which allows remote access, provided they use a fixed IP or DynDNS.

---

### Post by achase79 on 2009-03-18
You want to look up OpenSSH.  SSH is cross platform and can download, upload or control your remote system.

---

### Post by OffAxis on 2009-03-18
install apache2

```
sudo apt-get install apache2
```

forward port 80 on your home router to your machine's IP.

The settings file for apache is here:
**/etc/apache2/sites-available/default**

This is where you can control the website visitor's ability to follow symlinks or even access the given directory (you can specify a username or IP address of legitimate users)

The default folder for apache is here:
**/var/www/**

so any files or folders in that directory are served up to the website visitor. You can add a symlink in there to a different directory (like /home/sharedFiles/ or some such thing) if you like. And then, in that previously mentioned settings file, you grant access for the user to follow this link.

You can read up on it here:
[http://httpd.apache.org/docs/2.0/howto/htaccess.html](http://httpd.apache.org/docs/2.0/howto/htaccess.html)

paying particular attention to the 3rd section, "When not to use a .htaccess file"

The 5th section is also very pertinent to you, as well.

---

### Post by OffAxis on 2009-03-18
Openssh is probably not the answer.
 On a Windows machine you'd have to download a client (putty) to browse your files and then copy them across with another utility (pscp). And if you're in a corporate environment or an a handheld computer forget about it.

apache is about as easy to set up as an openssh server, and if whatever system you're on has a web browser, you're in.

---

### Post by Helios1276 on 2009-03-18
An FTP server you mean? I use dyndns.com and a nas setup up as an FTP server for similar results.

---

### Post by MrWES on 2009-03-18
FWIW, I just setup a DynDNS free account and configured my router to use DynDNS and it updates my IP automatically for me. Took all of ten minutes to setup the account and configure the router. Now, where ever I am I can ssh or ftp to xxxx.homedns.org -- very nice.

Bill

---

### Post by billgoldberg on 2009-03-18
For most users this is sort of a problem because most people have dynamic IP adresses.

Luckily there are free services like [DynDNS]("http://www.dyndns.com/") that you can use to get around that.

Then it's a simple matter of running some sort of server on that machine and have a client to connect to it on your office pc.

---

### Post by Sam the Wizer on 2009-03-18
Sounds like FTP to me.  Best to use FTP in conjunction with SSH (FTPS) or else your data (including your password) is being transmitted completely unencrypted.

---

### Post by MrWES on 2009-03-19
Quick question; I setup my router to use dyndns, are the updates on a certain frequency, or just if or when my IP changes?

Bill

---

### Post by MrWES on 2009-03-19
He could use WinSCP on his Windows box - that would be a secure SFTP.

[http://winscp.net/eng/index.php]("http://winscp.net/eng/index.php")

---

### Post by Kellemora on 2009-03-19
WOW, Thanks Gang

You've given me enough things to study to keep me out of everyone's hair for a full year, hi hi..........

Those of you who mentioned DynDNS might be how she's doing it?
I THINK I saw that in the URL bar when she typed in her web page and hit the link on it.

So apparently, rather than having to remember places, she only needs to remember her own home web page.  Once there, she has links to all the places one would normally find in your own bookmarks.

Her hubby is not approachable by outsiders, so I couldn't ask him, and she never questions how he makes things happen for her on her computer.

Again, thanks for the WEALTH of Info you guys all gave to me on this!

TTUL
Gary

---

### Post by amadeus266 on 2009-03-19
I knuckled under and purchased Windows Home Server. I can access all my files plus stream music and video to wherever I am.

EDIT: Waiting PATIENTLY for Ubuntu Home Server

---

### Post by bodhi.zazen on 2009-03-19
Hard to know what was used exactly.

IMO I suggest ssh. You can access your server from windows with winscp.

Other options include http, ftp, and samba. I advise strongly against samba over the internet and if you ftp do so with caution.

---

### Post by ugm6hr on 2009-04-10
http / https access is possible using any php file manager software.  I think that is perhaps the easiest, and would require nothing but a standard web browser to download files from your server (and a dyndns account and appropriate port forwarding on router).

Your router can probably auto-update a dyndns dynamic ip (I was surprised to find that mine has a drop-down for dyndns updates!), although if it can't, I'm sure that your server can fulfil that function too.  Just be aware that it is not possible to access your router's setup page from outside your LAN (i.e. from the web); my router certainly doesn't by default.

FreeNAS uses QuixPlorer (pre-configured), but it does not sound too difficult to install manually on a web server: [http://quixplorer.wiki.sourceforge.net/Installation+Instructions](http://quixplorer.wiki.sourceforge.net/Installation+Instructions)

Google offers lots more PHP File Manager options: [http://www.google.co.uk/search?q=php+file+manager&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox](http://www.google.co.uk/search?q=php+file+manager&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox)

Not wanting to detract from Ubuntu (obviously I'm a big desktop fan), but I can't help but sing praises for FreeNAS as a home server (unless you need a print server).  It allows me to all this with a few clicks (still experimenting though).

---

### Post by rdisanza on 2009-05-02
I have been using LogMeIn probably since it 1st came out way back when on all my windows based pc's and lappys. And since I run a private game server from home, I am on LMI from my office computer numerious times per day without any problems at all. LogMeIn does have a FREE version that works extremely well as long as you don't need remote file transfers or remote print capabilities. Those only come with the Pro Edition which is a paid program. Keep in mind that LMI doesn't yet offer a Linux to Linux version of their software. See below from [www.LogMeIn.com]("http://www.LogMeIn.com")
 
[quote="the LogMeIn WebSite"] 
 
***[COLOR=red]Can I install LogMeIn on a Linux computer?[/COLOR] ***
 
Currently, we do not have any LogMeIn software products that allow you to login to Linux operating systems. We do plan to offer Linux compatibility in the future, but we cannot release or discuss any timelines as to when that will happen.
 
You can, however, use Linux to connect to a Windows or Mac OSX host via the use of our legacy Java interface. To use this, you will need the Java Runtime Environment, and Firefox installed on the computer. Most Linux distributions can install this from their Package Managers (RPM for Redhat based, Synaptic for Debian based, etc.). [/quote] 
 
As soon as I am alerted that LMI has a version for Linux to Linux remotes, I will let you all know. 
 
Regards,

---

### Post by Alterax on 2009-05-02
> **Helios1276 said:**
> An FTP server you mean? I use dyndns.com and a nas setup up as an FTP server for similar results.

I advise against standard FTP because it doesn't encrypt the username or password used to authenticate.  That means that any joker on your outside network with a dime-a-dozen packet sniffer will know your credentials.

A better option is to use SSH (TCP 22).  You can pipe X programs across it, access things via the terminal, set up a VPN tunnel, or use sftp which is simply FTP used through an encrypted SSH tunnel.

Much more secure, especially if you use private/public keys rather than passwords.

Now, as for the original post, it's not the greatest, but you may want to look up a nice web app called SSL-Explorer.  You'll need to set up your router to allow incoming ports 443 and 80 (for web traffic) and set up a DynDNS service so you can get a simple URL to connect to.  DynDNS will monitor your external IP and update the URL pointer if it changes.

When that's set up, install SSL explorer and you can set up access to documents, terminal applications, and VNC sessions.

---

### Post by yangt299 on 2009-05-02
I have done something similar to this before. I set up a computer server (if that's what its called) on my Ubuntu computer, and then through my router connected to my other computer, so then both computers could view what i put on my Ubuntu server. The server's home was located at var/www.

If this is what you are looking for, feel free to ask for instructions. I'm too lazy to type them out right now :P

---

