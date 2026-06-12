---
title: "Securely sharing files across internet."
date: 2010-04-08
forum: New to Ubuntu
---

### Post by karthick87 on 2010-04-08
I am using [COLOR=Red]ubuntu 9.04[/COLOR] and my friend is using [COLOR=Red]Windows[/COLOR] and we both are connected through internet..And both of our connection uses [COLOR=Red]Dynamic IP[/COLOR]..I would like to access his system and i wanted to copy some files from his system.Is it possible?If possible how to do this.?

---

### Post by Elaztic on 2010-04-08
well...depending on the size and amount of files you can either use:
- instant messaging (eg. Pidgin)
- ftp (setup a FTP server on both machines)
- online drive (megaupload or whatever they are called)
- SSH/Telnet?

---

### Post by VeeDubb on 2010-04-08
All good advice there, but fails to deal with that whole "dynamic IP" issue, which is a big one if you're dealing with large enough files that you have to use ftp or sftp.

The easiest way to get around dynamic IP is using a service like dyndns.com

Once you register with the site and make up a domain name, you set up scripting on your computer that updates the site with your IP address every time it changes.

Some routers, like my netgear, have built in support for dyndns.com, so I actually have my router updating instead of my desktop, and then only have my router forward specific ports to my dekstop.

Once you have your dynamic IP issue taken care of, you can use whatever protocal you want for file transfers.  I prefer sftp because it's highly secure.  Also, filezilla can access it from windows VERY easily, which is a plus if your buddy is on a windows box.

---

### Post by aeiah on 2010-04-08
what veedubb said. id also like to point out that if you want things secure, you should probably stay away from FTP and use sFTP (which runs through ssh, as mentioned). 

if you're regularly sharing stuff and want to share everything within a specific folder with eachother, you could consider using rsync (once you've set up the dyndns stuff). rsync can work with ssh to sync data across the internet, and only copies the bits that change. you'd just issue the same command each time and get new stuff that your friend has put in a specific folder and vice versa. might get messy due to him using windows though, but is still do-able.

---

### Post by mastablasta on 2010-04-08
you could use one of cloud services that offer space on th einternet. there are quite a few out there that are free and require password & user login. sort of safe....
 
edit you could also encripty file in this case if it is necessary.

---

### Post by VeeDubb on 2010-04-09
> **aeiah said:**
> what veedubb said. id also like to point out that if you want things secure, you should probably stay away from FTP and use sFTP (which runs through ssh, as mentioned).

The choice of which protocol to use is always up to the user, but I agree that sFTP is a much better option.  There is absolutely no difference in speed or reliability that I have ever seen, but sFTP is infinitely more secure.

---

### Post by CharlesA on 2010-04-09
> **VeeDubb said:**
> The choice of which protocol to use is always up to the user, but I agree that sFTP is a much better option.  There is absolutely no difference in speed or reliability that I have ever seen, but sFTP is infinitely more secure.

This. sftp would definitely be better, since it encrypts the  file transfer.

Could try scp, but I use sftp more often then scp.

---

### Post by lespaul_rentals on 2010-04-09
Dynamic IP?  No problem.  Sign up at DynDNS.com for a free dynamic hostname.

Use ddclient (available from the repositories) to keep the IP address current in case of a power outage, router reset, etc.  After installation, you MUST make a change in the config file!  Edit **/etc/ddclient/ddclient.conf** as root, and change *use=if, if=[interface_name]* to read *use=web, if=[interface_name]*

As for secure file transfers, I would suggest SFTP.  It's built into SSH.  Read up on it; the security is fantastic with protocol 2.0.

Once you set up the OpenSSH daemon (there are a plethora of tutorials online, just Google it), you can connect to it using an SSH client, or for file transfers, an SFTP client.  My personal favorite SFTP client for Windows is WinSCP (free).  FileZilla is my favorite for Linux (free, OS).

Not only does SSH allow you to securely transfer files using SFTP, it also allows for remote administration.  In addition, you can use it to tunnel otherwise insecure traffic to make it secure.  Anytime I'm on a network that might not be trustworthy, I can tunnel my Firefox traffic through an encrypted tunnel to my home server.  If anyone wants to sniff my email passwords or IM conversations, they'll have to crack my connection first. :)

---

### Post by fremantle on 2010-04-09
just get deluge, create a torrent of your file, send it to your friend.

---

### Post by VeeDubb on 2010-04-10
> **fremantle said:**
> just get deluge, create a torrent of your file, send it to your friend.

That's kind of a kludge, and only works for transferring predetermined sets of files in one direction.

If you want to be able to browse files, and move/copy/delete/etc remotely, then it's of no value what so ever.

Not to mention, all the joy of fast transfer rates you get with a torrent depend on there being multiple users.

In other words, that's the worst suggestion I've seen today.

---

### Post by lespaul_rentals on 2010-04-10
> **fremantle said:**
> just get deluge, create a torrent of your file, send it to your friend.

What about the word "secure" do you not understand?

Also, he's trying to share files with one other host, not the whole world.  The entire point of BitTorrent is *de-centralized* file sharing.

> **VeeDubb said:**
> In other words, that's the worst suggestion I've seen today.

Yup. :popcorn:

---

### Post by asharpham on 2010-04-11
I also want to enable file transfer from Ubuntu 9.10 to WinXP remotely. I set up SSH according to some instructions I found but I can't work out the method of implementing a transfer using sftp.

I entered sftp into Terminal and got a list of options I just don't understand. For example, it mentions username@host and [file [file]]. What on earth does this mean?

Currently I can access the machine remotely through Remote Desktop Viewer as I have its IP address and port number. How can I access using ssh? Or can someone point me to a tutorial that's written for newbies?

---

### Post by KIAaze on 2010-04-11
[edit]Note: I wrote this without paying attention to the fact you are using a Windows machine as client or server. Things might be slightly different in that case.[/edit]

_General vocabulary:_
username : The name of your account on the remote PC

host : The "hostname" of the remote PC. You can find it by running the command "hostname" on the machine. It can also be replaced by the IP address of the machine. You should be able to ping the host for things to work.

file: Well, the path of the file you want to copy/get/download/write to...

USER : Same as "username"
IP : same as "host"

_ftp/sftp:_
In the case of ftp/sftp, you can normally enter the URL as follows in a browser or file manager (Firefox, Konqueror or Nautilus should work):
```
ftp://USER@IP
sftp://USER@IP
ftp://IP
sftp://IP

```
It should normally ask you for a username and password in the case of sftp.

sftp command-line tutorial:
[http://www.cae.wisc.edu/linux-sftp](http://www.cae.wisc.edu/linux-sftp)

(ftp is similar, except that it's not secure)

sftp can be used interactively (cf tutorial) or directly.
ex:
In the manual it states:
```
sftp [[user@]host[:file [file]]]
```
Arguments within "[]" are optional.
This is what it means:
```
#copy ~/.bashrc from remote to local
sftp kiaaze@192.168.1.1:.bashrc
#copy ~/.bashrc from remote to local and name it "toto"
sftp kiaaze@192.168.1.1:.bashrc toto
#"kiaaze" can be left out if my account name on the local machine is the same as on the remote machine
sftp 192.168.1.1:.bashrc toto

```

_ssh usage:_
To get command-line access to a remote PC, use ssh:
```
ssh USER@IP
```
(IP can be replaced by a hostname if you have one)
It will ask you for the password of USER on the remote PC.

If you also want to run graphical programs on the remote PC:
```
ssh -X USER@IP
```

Note: To use ssh from Windows, you can use putty: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

_scp usage:_
If you want to copy one file securely from one PC to another:
```
scp USER@IP:REMOTE_SOURCE_PATH LOCAL_DESTINATION_PATH
scp -r USER@IP:REMOTE_SOURCE_PATH LOCAL_DESTINATION_PATH
scp LOCAL_SOURCE_PATH USER@IP:REMOTE_DESTINATION_PATH
scp -r LOCAL_SOURCE_PATH USER@IP:REMOTE_DESTINATION_PATH

```
"-r" means copy recursively, just like for the normal "cp" command.

ex:
```
scp ~/foo kiaaze@192.168.1.1:/home/kiaaze
```
This will copy my local ~/foo file to my home directory on the remote PC with IP address 192.168.1.1.
It is equivalent to:
```
scp ~/foo kiaaze@192.168.1.1:
```
because if there is no path given after ":", it takes the home directory of the user by default.

---

### Post by The Cog on 2010-04-11
The easiest way to do SFTP file browsing is to use nautilus. You can enter an address into the location bar at the top like this:
> sftp://asharpham@1.2.3.4
or from the nautilus menus, choose **File / Connect to server...**, choose service type SSH and fill in the address and username.

---

