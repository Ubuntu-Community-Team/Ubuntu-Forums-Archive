---
title: "how to start telnet - frustrated please help"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by samssf on 2006-09-21
Ok, this has to be the 5th problem Ive had with Ubuntu and not been able to find any solution whatsoever by reading the boards.

I want to run telnet on my machine and connect to it. Yes I know it isn't secure. I don't want to run SSH right now.

I ran sudo apt-get install telnetd

Installed fine.

using nmap  or sudo netstat -plantu  I can see that I am not listening on port 23.

How do I start telnet daemon? I tried everything. I also searched every damn folder on my filesystem and couldn't find anything called telnet or telnetd. Of course the search feature didnt seem to do anything either when I click the search button.... but I tried searching on my own and could not find it.

Please tell me how to start telnet, and where it is located.

Thanks

---

### Post by kidders on 2006-09-21
This is just a guess, but is there an **/etc/init.d/telnetd** or similar?

If this was the first thing you tried (which it probably is!), I'm sorry.

---

### Post by Captain-Fungi on 2006-09-22
I would also like to know the answer to this as I am currently having the same problem.

I am aware of the risks of using telnet as opposed to SSH but need to use telnet.

Any help is appreciated.

---

### Post by kidders on 2006-09-22
Hi again,

Without knowing which telnet server you guys have installed, it's hard to know how it works. One thing you could do is take a look at the application's homepage and see if you start it up using its own daemon, or whether it prefers to have a thing called xinetd manage it.

By the way, how come you both *have* to use telnet? I'm curious!

---

### Post by spd106 on 2006-09-22
You can start telnetd in debug mode (man in.telnetd), but this won't run as a daemon. 

I think you need to install an inetd super server to allow telnetd to work as expected. Inetd is not usually installed by default, since it's not good security to have open ports by default and many modern daemons don't need inetd to run.

---

### Post by Captain-Fungi on 2006-09-22
I will try installing this tomorrow, see if I can get it to work.

---

### Post by A. J. Rimmer on 2006-09-24
Hope this helps ...

I wanted to run a Telnet session so did some googling and found an application to download in .deb format.  Tried to install it and Ubuntu told me that it was already installed.  

OK, says me, let's do some experimenting.

First thing I tried, I opened a terminal window, typed telnet ###.###.###.### and it connected.

It's been working ever since.  All I'm using is the stock Dapper 6.06 installation from the DVD (the one that comes with "The Official Ubuntu Book.")

---

### Post by GaryH on 2006-09-28
I can't figure out how to start the telnet daemon either. If anybody out there knows please let us all know. Thanks.

---

### Post by Captain-Fungi on 2006-09-29
Right, here is how I managed to get my telnet server to work.

First you need to install the inetd super server.

[COLOR="Red"]sudo apt-get install netkit-inetd[/COLOR]

Then install telnetd

[COLOR="Red"]sudo apt-get install telnetd[/COLOR]

Now restart inetd
[COLOR="Red"]
sudo /etc/init.d/inetd restart[/COLOR]

Check telnet is running 

[COLOR="Red"]netstat -a | grep telnet[/COLOR]

Telnet to you loopback address just to make sure

[COLOR="Red"]telnet 127.0.0.1[/COLOR]

Enjoy Telnet :cool:

---

### Post by GaryH on 2006-09-29
All,
After much Googling I figured out that telnetd doesn't run independently, it requires the help of the inetd daemon. So I installed inetd and still couldn't get telnet to startup. Not in all my Googling and Ubuntuing did I run accross a mention of installing netkit-inet. Is there a site that gives package dependencies or tips? How does one know that netkit-inet is required to make telnet work? Is there a book I should buy? It took me a whole day to get vsftpd working as I didn't know to load the compatibility module. What am I doing wrong?

Anyway I'm happy now. I can telnet to my Linux box thanks to the good Capt'n-Fungi.

GaryH

---

### Post by dorhelp on 2006-10-16
I am also trying to get the telnet dameon working on a ubuntu machine. I have an old rh network that is not connected to the internet. I replaced one of the machines and installed ubuntu on it. Everyone needs to be able to telnet on to the machine to run some text based programs that are on that machine.
I have tried following the steps above and everything is great through netstat. It shows tcp 0   0 *:telnet   *:*    LISTEN
so telnet dameon should be working but I can not telnet to loopback I get connection closed by foreign host. Same error message I get if trying to telnet in from another machine. The hosts files are all the same as they were when it was a red hat 7.2 machine. Any ideas what I am doing wrong.

---

### Post by kidders on 2006-10-18
Hi there,

> The hosts files are all the same as they were when it was a red hat 7.2 machine.Which files are you referring to?

"Connection closed by foreign host" usually means your telnet daemon *is* listening, so your problem must be something else. I wonder if it's authentication-related. Any clues in your system logs?

---

### Post by dorhelp on 2006-10-18
I am not finding anything in the logs and all the host files are set right. I wonder if there is a configuration file somewhere that I need to play with to get it working.
 On the lucky side all but one of the computers that need to login can use ssh or putty to connect. I have one very old machine that works as a dumb terminal and needs to telnet on to this machine. It has slackware 3.3 on it only two floppy drives and almost no hard drive like 40 meg. Oh well if I can not figure out a solution it will have to be retired.
                           Linda

---

### Post by pavel_kbc on 2006-11-26
oot@r00t-server:/home/r00t# sudo apt-get install netkit-inetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
netkit-inetd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up runit (1.6.0-1) ...
Adding SV inittab entry...
cp: omitting directory `/etc/inittab'
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ssh-krb5 (3.8.1p1-10build1) ...
/etc/ssh/sshd_config: line 73: Bad configuration option: AcceptEnv
/etc/ssh/sshd_config: terminating, 1 bad configuration options
invoke-rc.d: initscript ssh-krb5, action "restart" failed.
dpkg: error processing ssh-krb5 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 runit
 ssh-krb5
E: Sub-process /usr/bin/dpkg returned an error code (1)


please tell me what is the problem?

---

### Post by bhishma on 2006-12-20
Excellent HOWTO.  I followed your instructions and finally have a telnet server up and running.

It is amazing how many "how do i run a telnet server" questions here are answered by "run ssh instead".  There are times when telnet is really the only solution.

---

### Post by koenn on 2006-12-20
> **bhishma said:**
> 
It is amazing how many "how do i run a telnet server" questions here are answered by "run ssh instead".  There are times when telnet is really the only solution.

Like when ?
seriously, I really don't see how or when you'd prefer telnet over ssh.

---

### Post by bhishma on 2007-05-27
I have a Ubuntu machine at work.  When I need to do something on this computer from home, my only chance is to telnet into an old UNIX server at the workplace and then to telnet into my computer, as this server is the only computer accessible directly from outside the network.

The UNIX(AIX to be accurate) server is old, it doesn't have ssh client software, and I'm not its administrator.  Asking the administrator to add ssh function is out of question.

How's that for a "telnet-beats-ssh" situation?

---

### Post by kidders on 2007-05-27
Hehe...

I'd say the main point to me made about telnet vs ssh in your case goes a bit like this...

If you have a car without airbags or seatbelts, do you:

(a) Decide that airbagless, seatbeltless vehicles are superior because, after all, lots of old ones don't have either, or
(b) Not drive?

Stupid analogies aside, you'd have to admit that it is no longer considered sane to use unencrypted communications protocols over publicly accessible networks, where the information being exchanged is in any way sensitive.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by BlitheB on 2007-07-02
[QUOTE=Captain-Fungi;1558629]Right, here is how I managed to get my telnet server to work.

First you need to install the inetd super server.
[COLOR="Red"]sudo apt-get install netkit-inetd[/COLOR]
Then install telnetd
[COLOR="Red"]sudo apt-get install telnetd[/COLOR]
Now restart inetd
[COLOR="Red"]
sudo /etc/init.d/inetd restart[/COLOR]
Check telnet is running 
[COLOR="Red"]netstat -a | grep telnet[/COLOR]

===============================

I followed the above steps on my fiesty ubuntu 7.04
netkit-inetd installed
telnetd installed and says it removed netkit-inetd
which doesn't sound right to me, since step one said to install it.

inetd doesn't exist in init.d, I'm assuming because telnetd removed it, so I cannot restart it.
went ahead and looked for telnet running, using netstat  there's no entry for telnet or tel or inet for that matter.  All of the text from both installs looked great (except the above mention of removal of netkit-inetd)

Terminal server runs from Ubuntu into XP, just want the opposite, telnet at a minimum, or SSH or any other open source app. for that matter that will let me manipulate Ubuntu locally (not over internet) from XP.

any assistance would be greatly appreciated, I've searched the lists and this sounded like the easiest to get running.  I've also read the comments regarding SSH over Telnet...  SSH would be fine with me.  My preference is for terminal server type access, but would settle for easy to configure and command line only.

Thanks!

---

### Post by PhrankDaChickenGeek on 2007-07-04
Like BlitheB said, this method dosn't work in 7.04

My reason for running telnet is so I can control the server through a java web app over https. This gets around any firewalls/proxies and still lets me remotly control the machine (since port 443 is usually open, and 22 is not). I haven't been able to get the java app (JTA) to work with SSH, and https is still secure.

---

### Post by fcp on 2007-07-04
I am having the same problem but the instructions provide no joy.  The netkit-inetd installs fine but the telnetd package is not found and therefore not installed.

I tried ssh as well and got the same error: connection refused.

Thanks for any help!  Transcript of commands and results below.

fcp@fcp-desktop:~$ sudo apt-get install netkit-inetd
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  netkit-inetd
0 upgraded, 1 newly installed, 0 to remove and 170 not upgraded.
Need to get 32.6kB of archives.
After unpacking 156kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main netkit-inetd 0.10-10.3ubuntu4 [32.6kB]
Fetched 32.6kB in 1s (23.5kB/s)      
Preconfiguring packages ...
Selecting previously deselected package netkit-inetd.
(Reading database ... 89534 files and directories currently installed.)
Unpacking netkit-inetd (from .../netkit-inetd_0.10-10.3ubuntu4_i386.deb) ...
Setting up netkit-inetd (0.10-10.3ubuntu4) ...
 * Starting internet superserver...                                      [ ok ] 

fcp@fcp-desktop:~$ sudo apt-get install telnetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package telnetd
fcp@fcp-desktop:~$ sudo /etc/init.d/inetd restart
 * Restarting internet superserver...                                    [ ok ] 
fcp@fcp-desktop:~$ telnet 127.0.0.1
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
fcp@fcp-desktop:~$ ssh 127.0.0.1
ssh: connect to host 127.0.0.1 port 22: Connection refused
fcp@fcp-desktop:~$

---

### Post by PhrankDaChickenGeek on 2007-07-04
Installing SSH should be as easy as
```

sudo apt-get install openssh-server

```

Telnet is still giving me fits, however.

---

### Post by PhrankDaChickenGeek on 2007-07-04
I Have finally figured it out!!

HOW TO INSTALL TELNET ON UBUNTU FEISTY FAWN 7.04:

NOTE! SSH is secure. Telnet is NOT! Use SSH if at all possible:
```

sudo apt-get install openssh-server

```

Ok, to setup telnet, we'll start from scratch:
```

sudo apt-get remove --purge openbsd-inetd telnetd

```

Then edit the inetd.conf file
```

sudo nano /etc/inetd.conf

```

If there is already a telnet line in this file, remove the "#off#" from the beginning of the line. If not, add the following line:
```

telnet          stream  tcp     nowait  telnetd /usr/sbin/tcpd  /usr/sbin/in.telnetd

```
(The inetd service won't start if there is not already a line in the inetd.conf file)

Ctrl-X, 'Y' to save

Then we can install openbsd-inetd:
```

sudo apt-get install openbsd-inetd

```

Then install telnetd:
```

sudo apt-get install telnetd

```

And test!
```

telnet localhost

```

---

### Post by ashishmourya21 on 2007-07-24
it worked for me the solution

---

### Post by JohnsonUT on 2007-07-25
I cannot install openbsd-inetd.  I get this same error when I try to uninstall netkit-inetd.


/etc/init.d> sudo apt-get install openbsd-inetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  netkit-inetd
The following NEW packages will be installed:
  openbsd-inetd
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/34.7kB of archives.
After unpacking 20.5kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 105886 files and directories currently installed.)
Removing netkit-inetd ...
/var/lib/dpkg/info/netkit-inetd.prerm: 5: /etc/init.d/inetd: not found
dpkg: error processing netkit-inetd (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 netkit-inetd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by xtrumanx on 2007-08-04
> **PhrankDaChickenGeek said:**
> I Have finally figured it out!!

HOW TO INSTALL TELNET ON UBUNTU FEISTY FAWN 7.04:

NOTE! SSH is secure. Telnet is NOT! Use SSH if at all possible:
```

sudo apt-get install openssh-server

```

Ok, to setup telnet, we'll start from scratch:
```

sudo apt-get remove --purge openbsd-inetd telnetd

```

Then edit the inetd.conf file
```

sudo nano /etc/inetd.conf

```

If there is already a telnet line in this file, remove the "#off#" from the beginning of the line. If not, add the following line:
```

telnet          stream  tcp     nowait  telnetd /usr/sbin/tcpd  /usr/sbin/in.telnetd

```
(The inetd service won't start if there is not already a line in the inetd.conf file)

Ctrl-X, 'Y' to save

Then we can install openbsd-inetd:
```

sudo apt-get install openbsd-inetd

```

Then install telnetd:
```

sudo apt-get install telnetd

```

And test!
```

telnet localhost

```

Well, this was the closest i got to getting telnet to work. This is what happens when I try to test it:
```
telnet localhost
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```

Any other ideas anyone? Installing telnetd and netkit-inetd isn't possible i think since the one which is installed second will remove the first. Suggestions to use ssh would not be helpful. This is for an assignment. Telnet is required.

EDIT: Well, I tried using ssh and it works fine using the above given directions. I think I'll just used this, close enough to what I need.

---

### Post by PhrankDaChickenGeek on 2007-08-09
> **JohnsonUT said:**
> I cannot install openbsd-inetd.  I get this same error when I try to uninstall netkit-inetd.


/etc/init.d> sudo apt-get install openbsd-inetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  netkit-inetd
The following NEW packages will be installed:
  openbsd-inetd
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/34.7kB of archives.
After unpacking 20.5kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 105886 files and directories currently installed.)
Removing netkit-inetd ...
/var/lib/dpkg/info/netkit-inetd.prerm: 5: /etc/init.d/inetd: not found
dpkg: error processing netkit-inetd (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 netkit-inetd
E: Sub-process /usr/bin/dpkg returned an error code (1)



This might work, I'll have to test later:

```

sudo touch /etc/init.d/inetd
sudo chmod u=rwx,g=rx,o=rx /etc/init.d/inetd
sudo apt-get remove -f --purge netkit-inetd

```

And then proceed with installation...

---

### Post by climbjm on 2007-08-16
Worked great for me, thx!

---

### Post by Quar on 2007-10-08
Nope...

It's installed and listening, obviously, but not authenticating.

```
root@Quarputar:/etc# telnet localhost
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.

```

Inetd.conf contains:
```

ftp     stream  tcp     nowait  root    /usr/sbin/tcpd /usr/sbin/proftpd
telnet  stream  tcp     nowait  root    /usr/sbin/tcpd /usr/sbin/in.telnetd

```

Any ideas on how to get it to give an authentication prompt?

---

### Post by ableape on 2007-10-09
I got openbsd-inetd to work for dapper following this thread. explative deleted...

---

### Post by feefs on 2007-11-27
this worked for me on LTS6.06 - thanks!!

First you need to install the inetd super server.
sudo apt-get install netkit-inetd
Then install telnetd
sudo apt-get install telnetd
Now restart inetd

sudo /etc/init.d/inetd restart
Check telnet is running
netstat -a | grep telnet


And as for all those pedants who keep bleating on about "telnets not secure use ssh".

* I DONT CARE !!!! *

Please answer questions, not pontificate your religeous beliefs. thankyou.
I'm using telnet on a closed network and ALL the o/s's I have can use it. It's easy. It's simple. There's lots of clients. everyone knows it. face it, it's like ftp. universal. If somebody wants to break in my network and sniff my packets to find the password then good luck. I'll just restore the image and turn it off. Although if anyone can do that on a network not on the internet and with no user access (vlanned out) i'd like to see it tbh.

---

### Post by ChrisRob on 2008-06-28
Many thanks I got telet working.  It was harder than instaliing unbuntu.  I am on 8.04 server.  I need telnet because with this I can use cut and paste.

I use SSH for secure working.

Chris

---

### Post by ChrisRob on 2008-07-03
Many thanks worked great.  Took ages to get telnet going.

Chris

---

