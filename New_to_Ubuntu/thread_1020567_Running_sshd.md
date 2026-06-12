---
title: "Running sshd"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by JFASI on 2008-12-24
My situation is as follows: My primary operating system is Mac OS X, but I write applications that are meant to be totally cross platform (read: include nothing but stdio.h and stdlib.h) I typically run my applications through Valgrind to clean them up a bit before I public them, but Valgrind is not available on Mac OS X. 

So here is my solution. I have installed Ubuntu 8.04 LTS Server on an old machine I had lying around, and I am running it headless from some dark corner, with its only connection to the real world being an ethernet cable strung between it and my main Mac. I want to SSH into it, but there is a slight hitch. 

For starters, I need to install sshd, but that's not so bad. My real issue is with getting the networking down. I don't want to have to fish for the IP address of the machine to log into it. How do I give it a static hostname that will be visible across the entire network?

---

### Post by Pobega on 2008-12-24
You can simply give your machine a static IP address. Just add the following to /etc/network/interfaces (If your interface isn't eth0 then change eth0 to whatever applies in this snippet)

**/etc/network/interfaces**
[i]auto eth0

iface eth0 inet static
       address 192.168.1.10
       netmask 255.255.255.0
       network 192.168.1.0
       broadcast 192.168.1.255
       gateway 192.168.1.1[/i]

---

### Post by JFASI on 2008-12-24
That's great. I can totally use that. Is there no easy way to give it a pretty name like "work" or something?

---

### Post by The Cog on 2008-12-24
You can change the hostname by editing the two files /etc/hostname and /etc/hosts. But you have to edit these at the same time (open two editing sessions before saving any changes) because while they disagree sudo won't work, and then you won't be able to edit the second one.

---

### Post by bodhi.zazen on 2008-12-24
And then you need to tell OSX about the host. In Ubuntu this is in /etc/hosts as well.

I am not sure of the location or layout of the hosts file on OSX.

Once you do this you can ssh user@work

---

### Post by JFASI on 2008-12-24
A little snag: I put in the values exactly as suggested above in my /etc/network/interfaces, but when I try to connect to the machine, nothing happens, and when I try to ssh into my Mac, which I know is configured for ssh, it informs me that there is no route to the network. I'm assuming one of those addresses wants to be a router or something?

---

### Post by bodhi.zazen on 2008-12-24
You will need to modify your settings to fit your network.

What is the ip address of your router ?

---

### Post by JFASI on 2008-12-24
The thing is that my setup is very simple. For completely idiotic reasons, I do not have internet access on my development machines. The link I am working under is (my main Mac) <-Ethernet-> (Ubuntu development machine). That's my entire network, so I do not have a router, and the connection between the two machines is direct. How should I set /etc/network/interfaces up to reflect that? 

Note: For the time being, I am "assuming" that the IP address taken by DHCP by the machine is constant, so I just let DHCP handle the setup of the network, and set my Mac's /etc/hosts file accordingly. I obviously want a more foolproof method, which is my I want some help with the static IP.

---

### Post by albinootje on 2008-12-24
> **JFASI said:**
> For starters, I need to install sshd, but that's not so bad. My real issue is with getting the networking down. I don't want to have to fish for the IP address of the machine to log into it.

The following will install the openssh-server for you :
```

sudo apt-get install ssh

```
Did you do that already ?
And did you do a /etc/init.d/networking restart on that machine itself already ?

---

### Post by albinootje on 2008-12-24
> **JFASI said:**
> The thing is that my setup is very simple. For completely idiotic reasons, I do not have internet access on my development machines. The link I am working under is (my main Mac) <-Ethernet-> (Ubuntu development machine). That's my entire network, so I do not have a router, and the connection between the two machines is direct. How should I set /etc/network/interfaces up to reflect that? 


Without internet-access, and with only access to the Apple machine, you don't need the gateway line, this should be enough on the Ubuntu machine :

# example /etc/network/interfaces
auto eth0

iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

And afaik you should use a cross-link cable however, you have that ?

---

### Post by JFASI on 2008-12-26
I think I've cornered another interesting problem. I've gotten the internet connection to work, but sshd is acting weirdly. When I start the machine, I usually start it headless, and then try to log in. That invariably fails. But when I start the machine with a monitor attached and run 

ssh 127.0.0.1 exit

And switch my monitor back to my mac, I can login as normal. Why would it be doing this?

---

### Post by albinootje on 2008-12-26
> **JFASI said:**
> I think I've cornered another interesting problem. I've gotten the internet connection to work, but sshd is acting weirdly. When I start the machine, I usually start it headless, and then try to log in. That invariably fails. But when I start the machine with a monitor attached and run 

ssh 127.0.0.1 exit

And switch my monitor back to my mac, I can login as normal. Why would it be doing this?

Did you install the desktop or server Ubuntu release ?
In another posting a user described that without a monitor attached gdm would not start, and then sshd also didn't want to start.

If I do a : 
```

ls -la /etc/rc2.d/

```
Then I see that ssh is pretty early in the boot-sequence, before gdm.

---

### Post by JFASI on 2008-12-26
I've installed Ubuntu 8.04 server LTS. Whenever I start the machine, I see a message informing me that it is starting sshd. When I look at rc#.d's three through five, and I see a symlink called S16ssh, so ssh is clearly being called. 

In fact, I find that I need just plug in the monitor to get ssh to work, meanwhile, when it runs headless, nothing happens. Perhaps I should try appending /path/to/ssh/sshd to rc.local?

---

### Post by albinootje on 2008-12-26
> **JFASI said:**
> I've installed Ubuntu 8.04 server LTS. Whenever I start the machine, I see a message informing me that it is starting sshd. When I look at rc#.d's three through five, and I see a symlink called S16ssh, so ssh is clearly being called. 

In fact, I find that I need just plug in the monitor to get ssh to work, meanwhile, when it runs headless, nothing happens. Perhaps I should try appending /path/to/ssh/sshd to rc.local?

You can try the following in /etc/rc.local :
```

/etc/init.d/ssh restart

```

If you prefer to start sshd manually, take a look at the content of /etc/init.d/ssh how that is done.

---

### Post by JFASI on 2008-12-26
I've tried adding that to rc.local, and while it does restart it, I still get nothing. Should I start a new thread with this issue?

---

### Post by bodhi.zazen on 2008-12-26
> **JFASI said:**
> I've tried adding that to rc.local, and while it does restart it, I still get nothing. Should I start a new thread with this issue?

NO

multiple threads will not solve your problem any faster and lead to duplication of effort and confusion.

---

### Post by albinootje on 2008-12-26
> **JFASI said:**
> I've tried adding that to rc.local, and while it does restart it, I still get nothing.
Did you remove or disable Network Manager by the way ?
I've seen Firefox and some other apps go "offline" when NM claimed that there was no internet connection.

---

### Post by JFASI on 2008-12-27
I would be surprised to find a service like network manager running on server install. I do not have anything relating to X installed, so at this point it's just me and a terminal. 

The issue at hand seems to be this: I've decided that assuming dhco will settle on the same address is not *so* bad an assumption, so I've gotten the basic networking down. When I go ahead and ping the machine, it is returning packets, so networking is working well. 

It seems the issue is with SSH refusing to start when there is not monitor attached (and technically no keyboard as well, since it uses a typical Apple setup with the keyboard going through the monitor's usb). Is there any way I can notify myself when the machine is fully booted where I could see running processes? Something like 

top > top.txt && scp top.txt me@mymac

maybe?

---

### Post by bodhi.zazen on 2008-12-28
That is exactly the issue.

Computers are not designed to run "headless" meaning no terminal and no keyboard. Some can boot this way, and some can not (but I am afraid I can not give you the technical details ... ).

I am guilty of not reading the entire thread, see if this thread gives you any hints.

[http://ubuntuforums.org/showthread.php?t=774739](http://ubuntuforums.org/showthread.php?t=774739)

---

### Post by juanoleso on 2008-12-28
if you do:
```

ps -A | grep ssh

```

it should come up with something similar to this:

```

 5336 ?        00:00:00 sshd

```

if the ssh daemon is running.  The ps command lists running processes and grep just picks out any lines with ssh in them.  if you need to install without internet type:
```

sudo vi /etc/apt/sources.list

```

when the file comes up delete the "# " in the first line:

```

# deb cdrom:[Ubuntu 8...

```

so it should say

```

deb cdrom:[Ubuntu 8...

```

by pressing the delete button 2 times and then press ESC and then ZZ.  What this does is allow the cdrom as a source for apt to get software.  Then pop in the ubuntu cd and do:

```

sudo aptitude install openssh-server

```

Also, I saw it once in the thread, but to run CAT5 from computer to computer you need to either get or make a [[COLOR="Blue"]Ethernet crossover cable[/COLOR]]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable") and plug it in.  But, if your MAC doesn't have two network cards, it won't be able to access the internet.  You should really invest in a router if you can.  They are not very expensive and will make your job a lot easier and will protect you with a hardware firewall.

The ssh daemon should work without a monitor.  It seems strange that it wouldn't.  That just doesn't make sense.  Anyway, after you have got the cross-over going from computer to computer use the address that you gave the computer from the /etc/network/interfaces file to ssh from the MAC box.

I wasn't sure how far that you had gotten so I just put down everything that I thought would help.

---

### Post by JFASI on 2008-12-28
I'm sorry, I find that last post kind of useless. I already have openssh-server installed. It only fails when there is no monitor, so I can't run "ps -A | grep ssh" when the machine is headless, because (1) I don't have a monitor installed, and (2) I can't ssh into the machine. Did you even read the rest of this thread? 

Is there a log of the messages output by init and all its children? If so, I can probably try adding "scp /path/to/log.txt [email]me@mymac:~/log.txt[/email]" to rc.local.

---

### Post by juanoleso on 2008-12-29
ok, plug in the monitor and get it running and then unplug the monitor and don't turn off the computer...

---

### Post by bodhi.zazen on 2008-12-30
> **JFASI said:**
> Did you even read the rest of this thread? 

Just a reminder to be courteous on these forums. Keep in mind this thread is fairly long and that we are all volunteers trying to help.

Simply restating the problem can be quite helpful to new people looking through the thread and if your posts are viewed as hostile you are less likely to get the assistance you seek.

---

### Post by JFASI on 2009-01-02
Sorry about that...

At any rate, it looks like not turning off the computer is going to have to be my solution. I'll try reinstalling Ubuntu. I was considering FreeBSD or Gentoo, but they are a whole lot more work than a nice friendly Ubuntu setup. Anyway, thanks for the help.

---

