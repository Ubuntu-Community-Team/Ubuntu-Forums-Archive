---
title: "Repair Installation ??"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-10-11
Today I decided to do a reinstall of 9.04 because of some problems I was having, and when choosing the partition I put it back on the same partition, I left the format box unchecked because it was already formatted as EXT3.

Well, I was surprised when I saw the desktop after it installed, all the changes I had made were still there, except for a couple small apps I had installed.

I was even more surprised to see my home folder intact with all my stuff, seems like all I needed was updates and restricted codecs. Even Google Chrome was still on the desktop.

I searched this forum and Google and could come up with only one thread about this on a Launchpad forum.

[https://answers.launchpad.net/ubuntu/+question/61011](https://answers.launchpad.net/ubuntu/+question/61011)

The post that interested me:

Tom said on 2009-02-14:
```

Firstly and most easily available is the "Recovery Mode" one of the options given during normal bootup. It does have some useful features and unlike the Windows equivalent it doesn't just hose your system.

During install there is the option of "Manual Partitioning" rather than "Guided" and this can be used to to UNticked the "format partition?" option for each partition. This often allows data and settings to remain intact. However, it often suffers from 'user-error' so i'd always back-up the data before using this.

Keeping your data on a different partition is quite a smart move - so it doesn't always get wiped during an install

Good luck and regards from
Tom :)

```

I was wondering why this option is not ever mentioned, it seems like it would save time if you just wanted to repair your install.

Mine got fixed, Synaptic works right now, it was installing programs and Ubuntu could not find them.

---

### Post by rb0171610 on 2009-10-11
> **barnaclebill18 said:**
> 
I was wondering why this option is not ever mentioned, it seems like it would save time if you just wanted to repair your install.

Mine got fixed, Synaptic works right now, it was installing programs and Ubuntu could not find them.

I am sure you are not the first person to naturally figure it out. ;)
Repair your install and don't format your partition.  Backups, Backups, Backups.  Do you keep your /home directory on a separate partition? Just curious.

---

### Post by barnaclebill18 on 2009-10-11
> **rb0171610 said:**
> I am sure you are not the first person to naturally figure it out. ;)
Repair your install and don't format your partition.  Backups, Backups, Backups.  Do you keep your /home directory on a separate partition? Just curious.

That is how I got everything messed up in the first place, trying to put my /home on a separate partition.

I have decided to wait until I have more experience before I try it again.

I have backups, when you are as bad at this stuff as I am, they are a necessity.

---

### Post by rb0171610 on 2009-10-11
> **barnaclebill18 said:**
> That is how I got everything messed up in the first place, trying to put my /home on a separate partition.

I have decided to wait until I have more experience before I try it again.

I have backups, when you are as bad at this stuff as I am, they are a necessity.

I have moved the /home directory to a separate partition before.  It was like performing surgery but I managed to get it all copied over with some obscure command I found on a forum somewhere.  I am sure you are NOT that bad at it.  After all, you are still here. Did you find a good tutorial for moving your /home directory to it's own partition btw?

---

### Post by barnaclebill18 on 2009-10-11
> **rb0171610 said:**
> I have moved the /home directory to a separate partition before.  It was like performing surgery but I managed to get it all copied over with some obscure command I found on a forum somewhere.  I am sure you are NOT that bad at it.  After all, you are still here. Did you find a good tutorial for moving your /home directory to it's own partition btw?

I used this one

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I have a real problem figuring out what to put in the terminal, if I can't copy and paste I usually mess it up. Sometimes I spend 5 or 10 minutes trying to get a command in, I just can't see how these guys can say it is a faster way to do things, give me a mouse.

---

### Post by rb0171610 on 2009-10-11
> **barnaclebill18 said:**
> I used this one

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I have a real problem figuring out what to put in the terminal, if I can't copy and paste I usually mess it up. Sometimes I spend 5 or 10 minutes trying to get a command in, I just can't see how these guys can say it is a faster way to do things, give me a mouse.

Cool I will give this a look over for you.  
I would say print out the instructions first so you have a copy in your hands.  Read them thoroughly from beginning to end so there are no suprises like "Oh, I guess this really doesn't work, sorry" at the end of the tutorial. Believe it or not, I have seen that.  Look for a second tutorial and maybe a third. If not to find a better one, to at least verify that the information is good.
Also, take a deep breath and relax. Take your time and try to learn from the experience.
 If you have a mouse and a good tutorial, you CAN just copy and paste the right commands into the command line and do it that way.  You don't have to type unless you cannot see the tutorial and are working from a TTY (blank terminal.) In that case, I can see that you might have to type from your printed tutorial.

Just some thoughts . . . 
Anyway let me look at this and see what it says, I will get back to you.

---

### Post by rb0171610 on 2009-10-11
> **barnaclebill18 said:**
> I used this one

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I have a real problem figuring out what to put in the terminal, if I can't copy and paste I usually mess it up. Sometimes I spend 5 or 10 minutes trying to get a command in, I just can't see how these guys can say it is a faster way to do things, give me a mouse.

sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

yes i believe this was the obscure copy command I was talking about  
This tutorial would be ok at first glance provide that your partitions are labeled the same (sda1, sda3, etc.) and you were indeed using ext3 file system rather than reiserfs, for example. 
It is a hefty undertaking if you don't know all of this for sure.

I am sure this was similar to the tutorial I used and the obscure command above seems to be the same.

Hopefully you will try again in the future and have better luck.  Or on your next install, I'd definitely recommend having /home on a its own partition.

---

### Post by barnaclebill18 on 2009-10-11
I see you are in Orlando, I am in the Keys, Marathon.

I have 2 computers side by side and will put the instructions on one while I work on the other, sometimes I will put a command on a USB stick to be able to copy it to the other computer, I could probably hook them up on a network, but I don't know how and it is not important enough to me to figure that out right now.

If I have to change something in the command, I will put it in the text editor and work on it and then paste it in the terminal.

I am really a computer dummy, only been using one a few years and never typed in my life and I am 67.

---

### Post by rb0171610 on 2009-10-11
> **barnaclebill18 said:**
> I see you are in Orlando, I am in the Keys, Marathon.

I have 2 computers side by side and will put the instructions on one while I work on the other, sometimes I will put a command on a USB stick to be able to copy it to the other computer, I could probably hook them up on a network, but I don't know how and it is not important enough to me to figure that out right now.

If I have to change something in the command, I will put it in the text editor and work on it and then paste it in the terminal.

I am really a computer dummy, only been using one a few years and never typed in my life and I am 67.

Hey that is COOL.  I love Florida.  
I have a degree in networking so if you have any questions, and I have time I'd be happy to help.
You should consider taking a typing class. It would help you tremendously I think.  It takes about four weeks to learn to type efficiently and correctly.  
You are not a dummy.  No one knows everything, people are unaware of everything they do not know, and age is irrelevant. 
;)
Do you use ssh to log into the other computer from the one your are typing on?  Are they both hooked up to the internet?

---

### Post by barnaclebill18 on 2009-10-12
;)
Do you use ssh to log into the other computer from the one your are typing on?  Are they both hooked up to the internet?[/QUOTE]

I don't know what ssh is, I will look it up.

I have both of them set up so I do not have to log in, I just start them up and start using them, on this one I have Ubuntu, Mint and XP. 

On the other one I just have Xp.

They are both on the internet, I use a Sprint Air card in a Kyocerra router, I live on a boat at anchor.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> ;)
Do you use ssh to log into the other computer from the one your are typing on?  Are they both hooked up to the internet?

I don't know what ssh is, I will look it up.

I have both of them set up so I do not have to log in, I just start them up and start using them, on this one I have Ubuntu, Mint and XP. 

On the other one I just have Xp.

They are both on the internet, I use a Sprint Air card in a Kyocerra router, I live on a boat at anchor.[/QUOTE]
**Install ssh on both computers and be sure to restart ssh as well.**
ssh, you can install ssh at the command line:

*sudo apt-get update & sudo apt-get install ssh*
 Now that ssh is installed, you need to restart ssh:

*sudo /etc/init.d/ssh restart* 
If the command was successful you will see output like this:
** Restarting OpenBSD Secure Shell server sshd *

 
Then you just need to know the ip address of the other computer. After it is installed, if you know the IP address of the other computer, type ssh ip-address-of-the-other-computer at the command prompt and you will see something like this:
[I]ssh 192.168.1.103
rob@192.168.1.103's password:
[/I]
Now you can log into the other computer from the computer you are working on.  Look at the command prompt and you will see it now says username@nameofothercomputer.
Of course you are only at the command line, but you can always open and browse directories to start.
try typing this to get started:
*ls*
will list the contents of your home directory on the computer.
If you want to close the remote connection, just type:
*exit*


 Let me know if you get this far or have more questions, I'd be happy to help.

---

### Post by barnaclebill18 on 2009-10-12
Well, I put it on this computer
```

Setting up ssh (1:5.1p1-5ubuntu1) ...

bill@bill-laptop:~$ 
bill@bill-laptop:~$ sudo /etc/init.d/ssh restart 
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 
bill@bill-laptop:~$ 

```

How do I get it on the XP machine?

BTW Thanks

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> Well, I put it on this computer
```

Setting up ssh (1:5.1p1-5ubuntu1) ...

bill@bill-laptop:~$ 
bill@bill-laptop:~$ sudo /etc/init.d/ssh restart 
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 
bill@bill-laptop:~$ 

```

How do I get it on the XP machine?

BTW Thanks
In windows, you can use a free utility called putty:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")
You can use it as an ssh client to login to another computer.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> Well, I put it on this computer
```

Setting up ssh (1:5.1p1-5ubuntu1) ...

bill@bill-laptop:~$ 
bill@bill-laptop:~$ sudo /etc/init.d/ssh restart 
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 
bill@bill-laptop:~$ 

```

How do I get it on the XP machine?

BTW Thanks
Go to the download page or this is the direct link:

[http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)

It is just a utility that you run by clicking on it, no need to install.

---

### Post by barnaclebill18 on 2009-10-12
Hello Rob,

I have it on the XP now, when I opened it, there is a box with stuff to fill in.

I don't know what to do next, how do I find the IP address?

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> Hello Rob,

I have it on the XP now, when I opened it, there is a box with stuff to fill in.

I don't know what to do next, how do I find the IP address?

you select ssh in putty, this will automatically select port 22; and then click open at the bottom. Of course u need the IP address where it says host name. Do you mean how do you find the IP address of the other (linux) machine?
[IMG]http://www.wifi.com.ar/english/doc/network/putty/putty-session.gif[/IMG]

---

### Post by barnaclebill18 on 2009-10-12
I guess I need the IP address of this one(Ubuntu) to put in PuTTY and the XP one to put in this machine.

I don't know how to find either one.

---

### Post by barnaclebill18 on 2009-10-12
I did a Google search and both computers have the same IP address.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> I did a Google search and both computers have the same IP address.

If both computers are hooked up to a router, and that router is hooked up to the internet, that is the routers ip address.

In windows XP, to find your IP address open up CMD, or the command box in accessories of the start menu.  Type ipconfig
[IMG]http://www.cites.illinois.edu/wireless/graphics/win2k-ipconfig.gif[/IMG]

You can see the IP address in the above image. On your Linux machine, open a terminal, at the command prompt you would type: 

*ssh 130.126.112.49*

---

### Post by barnaclebill18 on 2009-10-12
This is strange, when I type ipconfig in the run box, that black screen you posted flashes on for a second, then disappears.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> This is strange, when I type ipconfig in the run box, that black screen you posted flashes on for a second, then disappears.

You can also go to the control panel, click on networking, icon and . . . 
[IMG]http://img199.imageshack.us/img199/5286/repairipaddress.jpg[/IMG]

Sorry I am not sure exactly how at the moment but this is a screenshot!
The networking icon in control panel.  Make sure you switch to classic view on the left side of the control panel first.

---

### Post by barnaclebill18 on 2009-10-12
It has been awhile since I played around in XP, I think I forgot most of what I knew.

I looked at all the connection status boxes and none of them are showing the IP addresses. 

I tried it with the ethernet cable unplugged also.

---

### Post by barnaclebill18 on 2009-10-12
Hey Rob,

I have to hit the sack, I will play with it in the morning.

Thank you for the help.

BarnacleBill

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> Hey Rob,

I have to hit the sack, I will play with it in the morning.

Thank you for the help.

BarnacleBill

Certainly. Good night Bill.

---

### Post by barnaclebill18 on 2009-10-12
```
what is output on the Linux terminal of ping -4 IP-of-XP-machine?

so:

ping -4 192.168.0.101

This is like playing catch. It tells the Linux machine to send four small packets across the network to the XP machine. The XP machine should receive them, and send them back to the Linux machine. The Linux machine will dump the output to the terminal. If it is unsuccessful in connecting to the XP machine, it may time out or you may get an error.
Let me know either way.
Past
__________________
```
Hello Rob,

Here is the output```

bill@bill-laptop:~$ 
bill@bill-laptop:~$ ping -4 192.168.0.101
ping: invalid option -- '4'
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
bill@bill-laptop:~$ 

```

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> ```
what is output on the Linux terminal of ping -4 IP-of-XP-machine?

so:

ping -4 192.168.0.101

This is like playing catch. It tells the Linux machine to send four small packets across the network to the XP machine. The XP machine should receive them, and send them back to the Linux machine. The Linux machine will dump the output to the terminal. If it is unsuccessful in connecting to the XP machine, it may time out or you may get an error.
Let me know either way.
Past
__________________
```
Hello Rob,

Here is the output```

bill@bill-laptop:~$ 
bill@bill-laptop:~$ ping -4 192.168.0.101
ping: invalid option -- '4'
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
bill@bill-laptop:~$ 

```

Yes it should be:
ping -c 4 192.168.0.101
 
the c switch is for count as you can read above in your output.
My apologies, I was still asleep.

---

### Post by barnaclebill18 on 2009-10-12
Here is that one
```

bill@bill-laptop:~$ ping -c 4 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
64 bytes from 192.168.0.101: icmp_seq=1 ttl=128 time=1.35 ms
64 bytes from 192.168.0.101: icmp_seq=1 ttl=128 time=1.96 ms (DUP!)
64 bytes from 192.168.0.101: icmp_seq=2 ttl=128 time=0.213 ms
64 bytes from 192.168.0.101: icmp_seq=3 ttl=128 time=0.213 ms
64 bytes from 192.168.0.101: icmp_seq=4 ttl=128 time=0.214 ms

--- 192.168.0.101 ping statistics ---
4 packets transmitted, 4 received, +1 duplicates, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 0.213/0.790/1.961/0.733 ms
bill@bill-laptop:~$ 
```

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> Here is that one
```

bill@bill-laptop:~$ ping -c 4 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
64 bytes from 192.168.0.101: icmp_seq=1 ttl=128 time=1.35 ms
64 bytes from 192.168.0.101: icmp_seq=1 ttl=128 time=1.96 ms (DUP!)
64 bytes from 192.168.0.101: icmp_seq=2 ttl=128 time=0.213 ms
64 bytes from 192.168.0.101: icmp_seq=3 ttl=128 time=0.213 ms
64 bytes from 192.168.0.101: icmp_seq=4 ttl=128 time=0.214 ms

--- 192.168.0.101 ping statistics ---
4 packets transmitted, 4 received, +1 duplicates, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 0.213/0.790/1.961/0.733 ms
bill@bill-laptop:~$ 
```
Good what this tells you is that the XP machine and the Linux machine are talking to each other.  It says that Linux sent 64 byte packets four times,  and they were returned.  You got a duplicate return packet but that should not be anything to worry about at this point.
Now, try to make sure the ssh service is started on your linux box and that you know its correct IP address.  Try opening putty again and using it again.  You may have used the wrong IP address or the ssh service was not running.  To make sure the ssh service is started on your Linux machine, type the following:

*sudo service ssh start*

you should see output similar to the following:

[I]rob@tux:~$ sudo service ssh start
[sudo] password for rob:
 * Starting OpenBSD Secure Shell server sshd                                                                                                            [ OK ]
rob@tux:~$[/I]

---

### Post by barnaclebill18 on 2009-10-12
> **rb0171610 said:**
> Good what this tells you is that the XP machine and the Linux machine are talking to each other.  It says that Linux sent 64 byte packets four times,  and they were returned.  You got a duplicate return packet but that should not be anything to worry about at this point.
Now, try to make sure the ssh service is started on your linux box and that you know its correct IP address.  Try opening putty again and using it again.  You may have used the wrong IP address or the ssh service was not running.  To make sure the ssh service is started on your Linux machine, type the following:

*sudo service ssh start*

you should see output similar to the following:

[I]rob@tux:~$ sudo service ssh start
[sudo] password for rob:
 * Starting OpenBSD Secure Shell server sshd                                                                                                            [ OK ]
rob@tux:~$[/I]

I started it in Ubuntu
```

bill@bill-laptop:~$ sudo service ssh start
[sudo] password for bill: 
 * Starting OpenBSD Secure Shell server sshd                             [ OK ] 
bill@bill-laptop:~$ 
```

Then I put the 192.168.0.100 in PuTTY and it asked for 192.168.0.100's password, I used the one for Ubuntu and it said 'Access denied'.

Could it be Firestarter, I think I have it on the Ubuntu and I have Comodo on the XP.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> I started it in Ubuntu
```

bill@bill-laptop:~$ sudo service ssh start
[sudo] password for bill: 
 * Starting OpenBSD Secure Shell server sshd                             [ OK ] 
bill@bill-laptop:~$ 
```

Then I put the 192.168.0.100 in PuTTY and it asked for 192.168.0.100's password, I used the one for Ubuntu and it said 'Access denied'.

Could it be Firestarter, I think I have it on the Ubuntu and I have Comodo on the XP.
Good thinking Bill.  Yes, it may be.  Since you have a router between you and the Internet, you may consider disabling Firestarter for now.  A router is a physical firewall.  I think it will be enough protection for you for the moment.  If it is indeed causing the problem, you can always try to figure out how to let it accept ssh (port 22) traffic later.

So for now, disable it and then try again.  I don't think your XP firewall has anything to do with it, but you may have to try disabling that as well. 
If you still get the error with one or both firewalls turned off let me know.

So to reiterate, disable the Linux firewall.  Try again. If you get an error, temporarily disable the Windows firewall.  Try again.
Good Luck.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> I started it in Ubuntu
```

bill@bill-laptop:~$ sudo service ssh start
[sudo] password for bill: 
 * Starting OpenBSD Secure Shell server sshd                             [ OK ] 
bill@bill-laptop:~$ 
```

Then I put the 192.168.0.100 in PuTTY and it asked for 192.168.0.100's password, I used the one for Ubuntu and it said 'Access denied'.

Could it be Firestarter, I think I have it on the Ubuntu and I have Comodo on the XP.

If disabling the firewall does not fix the problem, then we can try to look at this (older) post and see if it will help:

[http://ubuntuforums.org/showthread.php?t=7842]("http://ubuntuforums.org/showthread.php?t=7842")

---

### Post by barnaclebill18 on 2009-10-12
I just checked and I guess Firestarter did not get reinstalled because it is not checked in Synaptic, I turned off Comodo Firewall on the XP and tried it again it said 'Access denied'

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> I just checked and I guess Firestarter did not get reinstalled because it is not checked in Synaptic, I turned off Comodo Firewall on the XP and tried it again it said 'Access denied'

[http://ubuntuforums.org/showthread.php?t=7842]("http://ubuntuforums.org/showthread.php?t=7842")

Ok, read this post. It describes the problem you are having.

---

### Post by rb0171610 on 2009-10-12
> **rb0171610 said:**
> [http://ubuntuforums.org/showthread.php?t=7842]("http://ubuntuforums.org/showthread.php?t=7842")

Ok, read this post. It describes the problem you are having.

If you want to try this, open a terminal and type:

[I]sudo nano /etc/ssh/sshd_config
[/I]

scroll down using the arrow key to find the line that says:

*#PasswordAuthentication yes*

Remove the # sign in front of it.

so that it now says this:

*PasswordAuthentication yes*

Hit CTRL+X to save the file in nano. 

Now restart your ssh server on the Linux machine using their command or the one I taught you:

*sudo /etc/init.d/ssh restart*

OR
 
*sudo service ssh restart* 


Good Luck.

---

### Post by barnaclebill18 on 2009-10-12
```
I had this same problem. My XP machine at work running PuTTY could not connect to my server at home. I modified the /etc/ssh/sshd_config file on the server and changed the 'PasswordAuthentication' variable from 'no' to 'yes'. I then ran '/etc/init.d/ssh restart' to restart the sshd server and I could then connect using PuTTY. I found a good explanation for the various authentication mechanisms on the debian forums here:

http://lists.debian.org/debian-secur.../msg00343.html
```

I think this is the post with the answer to my problem, I do not know how to do this and the post on the debian forum might as well been written in Greek, as far as I am concerned.

---

### Post by rb0171610 on 2009-10-12
> **rb0171610 said:**
> If you want to try this, open a terminal and type:

[I]sudo nano /etc/ssh/sshd_config
[/I]

scroll down using the arrow key to find the line that says:

*#PasswordAuthentication yes*

Remove the # sign in front of it.

so that it now says this:

*PasswordAuthentication yes*

Hit CTRL+X to save the file in nano. 

Now restart your ssh server on the Linux machine using their command or the one I taught you:

*sudo /etc/init.d/ssh restart*

OR
 
*sudo service ssh restart* 


Good Luck.

> **barnaclebill18 said:**
> ```
I had this same problem. My XP machine at work running PuTTY could not connect to my server at home. I modified the /etc/ssh/sshd_config file on the server and changed the 'PasswordAuthentication' variable from 'no' to 'yes'. I then ran '/etc/init.d/ssh restart' to restart the sshd server and I could then connect using PuTTY. I found a good explanation for the various authentication mechanisms on the debian forums here:

http://lists.debian.org/debian-secur.../msg00343.html
```I think this is the post with the answer to my problem, I do not know how to do this and the post on the debian forum might as well been written in Greek, as far as I am concerned.

Did you read the simplified instructions in my previous post? I was just wanting you to read it so you know where are next step would lie.  While you were reading the background information, I posted a tutorial (quoted above).
Try my instructions, they are easy. If you need help, let me know.

---

### Post by barnaclebill18 on 2009-10-12
Hello Rob,

Thanks again for helping me get this done.

I hate proving how dumb I am, but how do you remove the #, I tried backspace, but that just moved the line up.

I am still looking for the Dummy Guide to Using the Terminal.

Bill

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> Hello Rob,

Thanks again for helping me get this done.

I hate proving how dumb I am, but how do you remove the #, I tried backspace, but that just moved the line up.

I am still looking for the Dummy Guide to Using the Terminal.

Bill
When you are using nano, use the arrow key to move your cursor so that it is in front of the # sign.  You can try hitting delete on your keyboard.  
If you were to use the arrow key to move the cursor in nano so that it ends up after the # sign, you could hit backspace.  Hang in there.  We learn by doing and being patient. 
Hit CTRL+X to save. The shortcuts for nano are at the bottom.  Use CTRL key plus the first letter.  SO for example, if you were searching for text in a document you opened, you would type CTRL+W (for Where is). Give it a try.  Let me know if you are successful.

---

### Post by barnaclebill18 on 2009-10-12
I know you will find this hard to believe, but I think I messed it up. I don't know for sure, also it asked for a Y or N, does that have to be a capitol letter?
 
I did the CTRL+X, something happened, but I am not sure what.

It did some more stuff then it thought it asked for my password, but when I put it in, it was visible in the terminal and said command not found. I just closed the darn thing.

Should I start this all over again, or just try it? I don't think I was built for command line work.

I am going to have to learn more about 'nano', I really don't know what that is.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> I know you will find this hard to believe, but I think I messed it up. I don't know for sure, also it asked for a Y or N, does that have to be a capitol letter?
 
I did the CTRL+X, something happened, but I am not sure what.

It did some more stuff then it thought it asked for my password, but when I put it in, it was visible in the terminal and said command not found. I just closed the darn thing.

Should I start this all over again, or just try it? I don't think I was built for command line work.

I am going to have to learn more about 'nano', I really don't know what that is.
Take a deep breath and start over.  I doubt you messed anything up that can't be fixed.

Before you edit a file in nano, make a backup copy of that file
so you can use the (copy)  cp command to do that:
sudo cp */etc/ssh/sshd_config *[I]/etc/ssh/sshd_config.bak

[/I]basically I just added .bak extension to the file so you will have a backup copy.

I would try again bill.  And yes, if you manage to remove the pound sign from the file using the directions i gave you (*use the arrow keys to move the cursor in front of the # sign, hit delete on your keyboard, hit CTRL+X  to save the file, type Y for yes to confirm that you do indeed wish to save the changes you made.*) 
Relax and take your time, this one is not difficult.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> I know you will find this hard to believe, but I think I messed it up. I don't know for sure, also it asked for a Y or N, does that have to be a capitol letter?
 
I did the CTRL+X, something happened, but I am not sure what.

It did some more stuff then it thought it asked for my password, but when I put it in, it was visible in the terminal and said command not found. I just closed the darn thing.

Should I start this all over again, or just try it? I don't think I was built for command line work.

I am going to have to learn more about 'nano', I really don't know what that is.
If you cannot figure it out easily, I have attached a copy of the file with the #sign removed for you.  You can put it in your home directory.  Open a terminal and type the following to copy it over to where it needs to be:

[I]sudo cp ~/sshd_config /etc/ssh/ 

[/I]restart your ssh server following the instructions in the previous post and continue from there.  
Good Luck.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> I know you will find this hard to believe, but I think I messed it up. I don't know for sure, also it asked for a Y or N, does that have to be a capitol letter?
 
I did the CTRL+X, something happened, but I am not sure what.

It did some more stuff then it thought it asked for my password, but when I put it in, it was visible in the terminal and said command not found. I just closed the darn thing.

Should I start this all over again, or just try it? I don't think I was built for command line work.

I am going to have to learn more about 'nano', I really don't know what that is.
nano is just a simple command line text editor like notepad in windows or microsoft word.
You can use it to create a simple document.  If someone gives you a phone number and you want to save it to a text file, open a terminal and type nano plus the name you want to give to the file:
nano phone_number.txt

type the phone number in nano: 555-5555 and then hit CTRL+X to save
nano will ask you to hit y or n to save as in the attached picture.  You will see that Y and N are highlighted at the bottom.  So if you hit Y or y followed by enter it will save the document and close the program.
If you want to read your file to see how it worked type:
nano phone_number.txt
nano will open the file and you should see 555-5555 just like you typed it. If you open this same file with open office or some other text program you will see it too.

---

### Post by rb0171610 on 2009-10-12
> **rb0171610 said:**
> nano is just a simple command line text editor like notepad in windows or microsoft word.
You can use it to create a simple document.  If someone gives you a phone number and you want to save it to a text file, open a terminal and type nano plus the name you want to give to the file:
nano phone_number.txt

type the phone number in nano: 555-5555 and then hit CTRL+X to save
nano will ask you to hit y or n to save as in the attached picture.  You will see that Y and N are highlighted at the bottom.  So if you hit Y or y followed by enter it will save the document and close the program.
If you want to read your file to see how it worked type:
nano phone_number.txt
nano will open the file and you should see 555-5555 just like you typed it. If you open this same file with open office or some other text program you will see it too.

Also, I forgot to post the pic!

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> 
I am going to have to learn more about 'nano', I really don't know what that is.
Here are a few quick references on nano. 
Background info on the program itself:

[http://en.wikipedia.org/wiki/Nano_%28text_editor%29]("http://en.wikipedia.org/wiki/Nano_%28text_editor%29")

and a simple tutorial to get you started:

[http://www.debianadmin.com/nano-editor-tutorials.html](http://www.debianadmin.com/nano-editor-tutorials.html)

and yet more reading, with a quiz to follow:

[http://beginlinux.com/desktop_training/comm/shells/1377-nano-introduction](http://beginlinux.com/desktop_training/comm/shells/1377-nano-introduction)

---

### Post by barnaclebill18 on 2009-10-12
I put this command in again sudo nano /etc/ssh/sshd_config, and saw that the # was gone from PasswordAuthentication yes, I closed that terminal, then opened a new one and did sudo service ssh restart.

I started PuttY and when I put 192.168.0.100 in, it now says Network error: Connection refused.

I don't know how to save that picture you put in the last post, it is a thumb nail and the file does not look like it is as long as the one in my terminal and how will the terminal find it,  doesn't it have to have a name.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> I put this command in again sudo nano /etc/ssh/sshd_config, and saw that the # was gone from PasswordAuthentication yes, I closed that terminal, then opened a new one and did sudo service ssh restart.

I started PuttY and when I put 192.168.0.100 in, it now says Network error: Connection refused.

I don't know how to save that picture you put in the last post, it is a thumb nail and the file does not look like it is as long as the one in my terminal and how will the terminal find it,  doesn't it have to have a name.
What is happening is that the XP box is being denied access by the Linux Machine.  
Try one more thing:

[I]sudo apt-get install openssh-server openssh-client 

[/I]restart your ssh server (i am sure you are an expert on this by now) and try connecting from your XP machine again.
Installing openssh has fixed this problem for some people.
Good Luck.

---

### Post by barnaclebill18 on 2009-10-12
I put in that last command
```

bill@bill-laptop:~$ sudo apt-get install openssh-server openssh-client 
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version.
openssh-server set to manually installed.
openssh-client is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bill@bill-laptop:~$ sudo service ssh restart
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 
bill@bill-laptop:~$ 


```
I restarted ssh and tried again from XP and it did the same as soon as I hit enter: Network error: Connection refused.

---

### Post by barnaclebill18 on 2009-10-12
Hello Rob,

I think I probably ruined the file when I used the backspace and might have took something off the line above PasswordAuthentication, maybe I should remove ssh and start all over, that seems to be the way with my computer tries.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> Hello Rob,

I think I probably ruined the file when I used the backspace and might have took something off the line above PasswordAuthentication, maybe I should remove ssh and start all over, that seems to be the way with my computer tries.
it couldn't hurt

---

### Post by barnaclebill18 on 2009-10-12
The more I think about it, I think that is what I did.

If I am not being too big of a pain in the butt, could you give me the code to remove it and I will start over from the beginning.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> The more I think about it, I think that is what I did.

If I am not being too big of a pain in the butt, could you give me the code to remove it and I will start over from the beginning.
A note to you: This file is read by the SSH service when it starts.  That is why if you edit it, you need to restart the SSH service.  The SSH service rereads this file with the changes you just made.  Anything with a # sign in front of the line is ignored (meaning only lines that do not begin with a # will be read).  If you remove the # sign below that begins the line PasswordAuthentication yes you are telling the SSH service to read this instruction.  I have removed the # sign for you below.  You will just need to copy this file to your /etc/ssh directory using the command below. Do not forget to restart your ssh service.  If this does not fix your problem, do not give up.  You will eventually be able to use SSH to log into your Linux machine.  


Copy and paste the following into a text document named sshd_config in your home directory.   Then to move the file to where it needs to be type at the terminal:

*sudo cp -r  sshd_config /etc/ssh/ *

Then restart your ssh service.  The text is as follows:

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> The more I think about it, I think that is what I did.

If I am not being too big of a pain in the butt, could you give me the code to remove it and I will start over from the beginning.

try again
I attached the file as a text document, you will need to remove the .txt extension from the file name so it is sshd_config not sshd_config.txt. 
Save it to your home directory and use the commands I gave you in the previous post. I have removed the # sign for you.

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> The more I think about it, I think that is what I did.

If I am not being too big of a pain in the butt, could you give me the code to remove it and I will start over from the beginning.
Some people said they had to change a setting in Putty.  I attached a thumbnail for you. 

" I am beginning to suspect the putty client may be the problem. If there is an option in putty, make sure it is set to use ssh protocol 2."

"I tried it from another linux box and it worked just fine, suggesting that the problem is indeed putty. Putty is configured for v2 as preferred. Setting it to v2 only fixes the issue."

You can see in the pic you can click the plus sign next to ssh on the left and click on ssh 2only.  In this pic you can see the default is 2.  Some people report success with this setting. Then go back to to top where it says connection on the left and type in your IP address you want to connect to, make sure you click ssh, and hit open at the bottom.

Good Luck.

---

### Post by barnaclebill18 on 2009-10-12
Hi Rob,

I had to make a run to town, just got back and read your posts, I will go back and reread the posts you and try to figure this out.

I will post back and let you know how I am doing and maybe ask a question or two.

Thanks again.

Bill

---

### Post by barnaclebill18 on 2009-10-12
I followed your instructions, I downloaded the text file to the desktop, took off the .txt and saved it to /home.

Then I ran the commands:
```

bill@bill-laptop:~$ 
bill@bill-laptop:~$ sudo cp -r sshd_config /etc/ssh/ 
[sudo] password for bill: 
bill@bill-laptop:~$ 
bill@bill-laptop:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 
bill@bill-laptop:~$ 



```

I started PuTTY, looked at the page you posted the screen shot of, and it was exactly the same, so I did not have to change anything, then tried to log on and I got the 'Access denied'

I am pretty sure I did everything properly so I don't know where to go from here.

I did get a good lesson and learned more about using the terminal and you gave me some great links to learn more, I was wondering why the terminal changed sometimes with those letter boxes at the bottom, nano.

I am willing to try something else or just think about it some more.

Whatever you care to do, thanks Rob, if you get down this way I will take you out fishing if you want,

Bill

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> I followed your instructions, I downloaded the text file to the desktop, took off the .txt and saved it to /home.

Then I ran the commands:
```

bill@bill-laptop:~$ 
bill@bill-laptop:~$ sudo cp -r sshd_config /etc/ssh/ 
[sudo] password for bill: 
bill@bill-laptop:~$ 
bill@bill-laptop:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 
bill@bill-laptop:~$ 



```I started PuTTY, looked at the page you posted the screen shot of, and it was exactly the same, so I did not have to change anything, then tried to log on and I got the 'Access denied'

I am pretty sure I did everything properly so I don't know where to go from here.

I did get a good lesson and learned more about using the terminal and you gave me some great links to learn more, I was wondering why the terminal changed sometimes with those letter boxes at the bottom, nano.

I am willing to try something else or just think about it some more.

Whatever you care to do, thanks Rob, if you get down this way I will take you out fishing if you want,

Bill
Awesome.  The reason that those boxes pop up with the menus at the bottom is that you have opened a program called nano.  Instead of a program that starts in front of you, with its own Gui, such as Firefox, nano runs in the terminal.  When you are finished using nano, you hit CTRL+X (x for eXit) and you are returned to your normal terminal.  Just think of it as a typing program that allows you to edit documents.
Very simple. 

Now, this is the next step to get ssh working.  You can edit your sshd_conf file on your Linux machine to have it log error messages to a text file (log.)   You will restart your SSH service.  Then you will try to connect again from your XP machine a few times and, as expected, you will get the error "access denied" a few times.
You can then post the ssh log files from your Linux machine so we can see what they say.  It may give us a clue as to why you are denied access when trying to log in from your XP machine.
If and when you are ready to try this, let me know and I will gladly help you along.

---

### Post by barnaclebill18 on 2009-10-12
Like I said, I enjoy doing these things and learning, I just don't know how to do it yet, seems like whenever I find a guide or information I want to know more about, I start reading it they say something about something I have not much knowledge about and I start Googling, I get lost often, this is all pretty new to me and I am trying to learn by doing.

I got to be fairly good with XP, I did not really want to learn Vista and then I heard about Ubuntu, after checking it out for awhile, I could see that it is the way of the future and I would like to get good enough to use it properly.

Anyway I am ready for anything you might suggest.

Bill

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> Like I said, I enjoy doing these things and learning, I just don't know how to do it yet, seems like whenever I find a guide or information I want to know more about, I start reading it they say something about something I have not much knowledge about and I start Googling, I get lost often, this is all pretty new to me and I am trying to learn by doing.

I got to be fairly good with XP, I did not really want to learn Vista and then I heard about Ubuntu, after checking it out for awhile, I could see that it is the way of the future and I would like to get good enough to use it properly.

Anyway I am ready for anything you might suggest.

Bill

can you post the output of the following commands for me:

[I]cat /etc/hosts.allow
[/I]

and 

[I]cat /etc/hosts.deny
[/I]
I just want to double check that there is nothing in these two files that may be causing a problem.

---

### Post by barnaclebill18 on 2009-10-12
Here is the first one```
[CODE]

bill@bill-laptop:~$ cat /etc/hosts.allow
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
bill@bill-laptop:~$ 

Here is the second
[CODE]
bill@bill-laptop:~$ cat /etc/hosts.deny
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
bill@bill-laptop:~$ 

```



[/CODE][/CODE]

---

### Post by barnaclebill18 on 2009-10-12
```
bill@bill-laptop:~$ cat /etc/hosts.deny
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
bill@bill-laptop:~$ 

```

---

### Post by rb0171610 on 2009-10-12
Perfect there is nothing there that would keep hosts from connecting.  Sometimes old firewall installs will leave things in the hosts.deny file and can cause a problem.

Type:

*sudo nano /etc/ssh/sshd_config*

and using the arrow keys on your keyboard, scroll down and find the section that says:

[I]# Logging
SyslogFacility AUTH
LogLevel INFO
[/I]
In the third line, delete the word INFO and change it to DEBUG3 as follows:

[I]LogLevel DEBUG3
[/I]
After you edit it correctly, hit CTRL+X on your keyboard, y to confirm that you want to save the changes followed by the enter key. Nano should cleanly exit, leaving you back at your command prompt.

Restart your ssh server:

*sudo service ssh restart*

Now try go to Putty and try to connect a few times.
You will get the expected access denied error.

Now go back to your Linux machine and type:

*sudo cat /var/log/auth.log | grep sshd*

post the output and we will see if it gives us any clues as to what the Linux machine is doing when you try to connect with PuTTy.

---

### Post by barnaclebill18 on 2009-10-12
Here it is```


bill@bill-laptop:~$ sudo nano /etc/ssh/sshd_config
[sudo] password for bill: 
bill@bill-laptop:~$ sudo nano /etc/ssh/sshd_config
bill@bill-laptop:~$ sudo service ssh restart
/etc/ssh/sshd_config line 22: unsupported log level 'DEBUGS3'
bill@bill-laptop:~$ sudo cat /var/log/auth.log | grep sshd
Oct 12 00:54:08 bill-laptop useradd[11671]: new user: name=sshd, UID=112, GID=65534, home=/var/run/sshd, shell=/usr/sbin/nologin
Oct 12 00:54:08 bill-laptop usermod[11676]: change user `sshd' password
Oct 12 00:54:08 bill-laptop chage[11681]: changed password expiry for sshd
Oct 12 00:54:08 bill-laptop sshd[11721]: Server listening on 0.0.0.0 port 22.
Oct 12 00:54:08 bill-laptop sshd[11721]: Server listening on :: port 22.
Oct 12 00:55:04 bill-laptop sshd[11721]: Received signal 15; terminating.
Oct 12 00:55:04 bill-laptop sshd[11748]: Server listening on 0.0.0.0 port 22.
Oct 12 00:55:04 bill-laptop sshd[11748]: Server listening on :: port 22.
Oct 12 07:45:49 bill-laptop sshd[2380]: Server listening on 0.0.0.0 port 22.
Oct 12 07:45:49 bill-laptop sshd[2380]: Server listening on :: port 22.
Oct 12 07:51:08 bill-laptop sshd[2373]: Server listening on 0.0.0.0 port 22.
Oct 12 07:51:08 bill-laptop sshd[2373]: Server listening on :: port 22.
Oct 12 09:05:41 bill-laptop sshd[4854]: Invalid user bb from 192.168.0.101
Oct 12 09:05:42 bill-laptop sshd[4854]: Failed none for invalid user bb from 192.168.0.101 port 1154 ssh2
Oct 12 09:06:12 bill-laptop sshd[4854]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 09:06:12 bill-laptop sshd[4854]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 09:06:14 bill-laptop sshd[4854]: Failed password for invalid user bb from 192.168.0.101 port 1154 ssh2
Oct 12 09:09:35 bill-laptop sshd[2373]: Received signal 15; terminating.
Oct 12 09:09:35 bill-laptop sshd[4873]: Server listening on 0.0.0.0 port 22.
Oct 12 09:09:35 bill-laptop sshd[4873]: Server listening on :: port 22.
Oct 12 09:14:01 bill-laptop sshd[5022]: Invalid user bb from 192.168.0.101
Oct 12 09:14:01 bill-laptop sshd[5022]: Failed none for invalid user bb from 192.168.0.101 port 1160 ssh2
Oct 12 09:14:08 bill-laptop sshd[5022]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 09:14:08 bill-laptop sshd[5022]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 09:14:10 bill-laptop sshd[5022]: Failed password for invalid user bb from 192.168.0.101 port 1160 ssh2
Oct 12 09:14:32 bill-laptop sshd[5022]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 09:14:34 bill-laptop sshd[5022]: Failed password for invalid user bb from 192.168.0.101 port 1160 ssh2
Oct 12 09:24:45 bill-laptop sshd[5217]: Invalid user bb from 192.168.0.101
Oct 12 09:24:45 bill-laptop sshd[5217]: Failed none for invalid user bb from 192.168.0.101 port 1167 ssh2
Oct 12 09:24:51 bill-laptop sshd[5217]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 09:24:51 bill-laptop sshd[5217]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 09:24:53 bill-laptop sshd[5217]: Failed password for invalid user bb from 192.168.0.101 port 1167 ssh2
Oct 12 09:25:07 bill-laptop sshd[5217]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 09:25:09 bill-laptop sshd[5217]: Failed password for invalid user bb from 192.168.0.101 port 1167 ssh2
Oct 12 13:56:57 bill-laptop sshd[9387]: Invalid user bb from 192.168.0.101
Oct 12 13:56:57 bill-laptop sshd[9387]: Failed none for invalid user bb from 192.168.0.101 port 1263 ssh2
Oct 12 13:57:04 bill-laptop sshd[9387]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 13:57:04 bill-laptop sshd[9387]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 13:57:06 bill-laptop sshd[9387]: Failed password for invalid user bb from 192.168.0.101 port 1263 ssh2
Oct 12 13:57:25 bill-laptop sshd[9387]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 13:57:27 bill-laptop sshd[9387]: Failed password for invalid user bb from 192.168.0.101 port 1263 ssh2
Oct 12 14:03:30 bill-laptop sshd[9472]: Invalid user bb from 192.168.0.101
Oct 12 14:03:30 bill-laptop sshd[9472]: Failed none for invalid user bb from 192.168.0.101 port 1269 ssh2
Oct 12 14:03:43 bill-laptop sshd[9472]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 14:03:43 bill-laptop sshd[9472]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 14:03:45 bill-laptop sshd[9472]: Failed password for invalid user bb from 192.168.0.101 port 1269 ssh2
Oct 12 14:19:25 bill-laptop sshd[9675]: Invalid user bb from 192.168.0.101
Oct 12 14:19:25 bill-laptop sshd[9675]: Failed none for invalid user bb from 192.168.0.101 port 1275 ssh2
Oct 12 14:19:37 bill-laptop sshd[9675]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 14:19:37 bill-laptop sshd[9675]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 14:19:40 bill-laptop sshd[9675]: Failed password for invalid user bb from 192.168.0.101 port 1275 ssh2
Oct 12 15:31:13 bill-laptop sudo:     bill : TTY=pts/0 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 16:27:21 bill-laptop sshd[4873]: Received signal 15; terminating.
Oct 12 16:27:21 bill-laptop sshd[11771]: Server listening on 0.0.0.0 port 22.
Oct 12 16:27:21 bill-laptop sshd[11771]: Server listening on :: port 22.
Oct 12 16:28:26 bill-laptop sshd[11775]: Invalid user bb from 192.168.0.101
Oct 12 16:28:26 bill-laptop sshd[11775]: Failed none for invalid user bb from 192.168.0.101 port 1365 ssh2
Oct 12 16:28:36 bill-laptop sshd[11775]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 16:28:36 bill-laptop sshd[11775]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 16:28:38 bill-laptop sshd[11775]: Failed password for invalid user bb from 192.168.0.101 port 1365 ssh2
Oct 12 16:29:06 bill-laptop sshd[11775]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 16:29:07 bill-laptop sshd[11775]: Failed password for invalid user bb from 192.168.0.101 port 1365 ssh2
Oct 12 16:52:38 bill-laptop sudo:     bill : TTY=pts/0 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 16:56:19 bill-laptop sudo:     bill : TTY=pts/0 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 16:56:59 bill-laptop sshd[11771]: Received signal 15; terminating.
Oct 12 16:56:59 bill-laptop sshd[12281]: Server listening on 0.0.0.0 port 22.
Oct 12 16:56:59 bill-laptop sshd[12281]: Server listening on :: port 22.
Oct 12 17:46:08 bill-laptop sshd[12281]: Received signal 15; terminating.
Oct 12 17:46:08 bill-laptop sshd[13076]: Server listening on 0.0.0.0 port 22.
Oct 12 17:46:08 bill-laptop sshd[13076]: Server listening on :: port 22.
Oct 12 19:46:35 bill-laptop sudo:     bill : TTY=pts/0 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 20:09:08 bill-laptop sudo:     bill : TTY=pts/1 ; PWD=/home/bill ; USER=root ; COMMAND=/bin/cp -r sshd_config /etc/ssh/
Oct 12 20:19:30 bill-laptop sshd[13076]: Received signal 15; terminating.
Oct 12 20:19:30 bill-laptop sshd[15652]: Server listening on 0.0.0.0 port 22.
Oct 12 20:19:30 bill-laptop sshd[15652]: Server listening on :: port 22.
Oct 12 20:20:40 bill-laptop sshd[15795]: Invalid user bb from 192.168.0.101
Oct 12 20:20:40 bill-laptop sshd[15795]: Failed none for invalid user bb from 192.168.0.101 port 1475 ssh2
Oct 12 20:20:51 bill-laptop sshd[15795]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 20:20:51 bill-laptop sshd[15795]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 20:20:53 bill-laptop sshd[15795]: Failed password for invalid user bb from 192.168.0.101 port 1475 ssh2
Oct 12 20:31:45 bill-laptop sshd[15941]: Invalid user bb from 192.168.0.101
Oct 12 20:31:45 bill-laptop sshd[15941]: Failed none for invalid user bb from 192.168.0.101 port 1478 ssh2
Oct 12 20:31:57 bill-laptop sshd[15941]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 20:31:57 bill-laptop sshd[15941]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 20:31:59 bill-laptop sshd[15941]: Failed password for invalid user bb from 192.168.0.101 port 1478 ssh2
Oct 12 22:19:25 bill-laptop sudo:     bill : TTY=pts/1 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 22:24:33 bill-laptop sudo:     bill : TTY=pts/1 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 22:28:42 bill-laptop sshd[17617]: Invalid user bb from 192.168.0.101
Oct 12 22:28:42 bill-laptop sshd[17617]: Failed none for invalid user bb from 192.168.0.101 port 1954 ssh2
Oct 12 22:28:52 bill-laptop sshd[17617]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 22:28:52 bill-laptop sshd[17617]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 22:28:55 bill-laptop sshd[17617]: Failed password for invalid user bb from 192.168.0.101 port 1954 ssh2
Oct 12 22:29:07 bill-laptop sshd[17617]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 22:29:08 bill-laptop sshd[17617]: Failed password for invalid user bb from 192.168.0.101 port 1954 ssh2
Oct 12 22:29:22 bill-laptop sshd[17617]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 22:29:24 bill-laptop sshd[17617]: Failed password for invalid user bb from 192.168.0.101 port 1954 ssh2
bill@bill-laptop:~$ 

```

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> Here it is```


bill@bill-laptop:~$ sudo nano /etc/ssh/sshd_config
[sudo] password for bill: 
bill@bill-laptop:~$ sudo nano /etc/ssh/sshd_config
bill@bill-laptop:~$ sudo service ssh restart
/etc/ssh/sshd_config line 22: unsupported log level 'DEBUGS3'
bill@bill-laptop:~$ sudo cat /var/log/auth.log | grep sshd
Oct 12 00:54:08 bill-laptop useradd[11671]: new user: name=sshd, UID=112, GID=65534, home=/var/run/sshd, shell=/usr/sbin/nologin
Oct 12 00:54:08 bill-laptop usermod[11676]: change user `sshd' password
Oct 12 00:54:08 bill-laptop chage[11681]: changed password expiry for sshd
Oct 12 00:54:08 bill-laptop sshd[11721]: Server listening on 0.0.0.0 port 22.
Oct 12 00:54:08 bill-laptop sshd[11721]: Server listening on :: port 22.
Oct 12 00:55:04 bill-laptop sshd[11721]: Received signal 15; terminating.
Oct 12 00:55:04 bill-laptop sshd[11748]: Server listening on 0.0.0.0 port 22.
Oct 12 00:55:04 bill-laptop sshd[11748]: Server listening on :: port 22.
Oct 12 07:45:49 bill-laptop sshd[2380]: Server listening on 0.0.0.0 port 22.
Oct 12 07:45:49 bill-laptop sshd[2380]: Server listening on :: port 22.
Oct 12 07:51:08 bill-laptop sshd[2373]: Server listening on 0.0.0.0 port 22.
Oct 12 07:51:08 bill-laptop sshd[2373]: Server listening on :: port 22.
Oct 12 09:05:41 bill-laptop sshd[4854]: Invalid user bb from 192.168.0.101
Oct 12 09:05:42 bill-laptop sshd[4854]: Failed none for invalid user bb from 192.168.0.101 port 1154 ssh2
Oct 12 09:06:12 bill-laptop sshd[4854]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 09:06:12 bill-laptop sshd[4854]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 09:06:14 bill-laptop sshd[4854]: Failed password for invalid user bb from 192.168.0.101 port 1154 ssh2
Oct 12 09:09:35 bill-laptop sshd[2373]: Received signal 15; terminating.
Oct 12 09:09:35 bill-laptop sshd[4873]: Server listening on 0.0.0.0 port 22.
Oct 12 09:09:35 bill-laptop sshd[4873]: Server listening on :: port 22.
Oct 12 09:14:01 bill-laptop sshd[5022]: Invalid user bb from 192.168.0.101
Oct 12 09:14:01 bill-laptop sshd[5022]: Failed none for invalid user bb from 192.168.0.101 port 1160 ssh2
Oct 12 09:14:08 bill-laptop sshd[5022]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 09:14:08 bill-laptop sshd[5022]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 09:14:10 bill-laptop sshd[5022]: Failed password for invalid user bb from 192.168.0.101 port 1160 ssh2
Oct 12 09:14:32 bill-laptop sshd[5022]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 09:14:34 bill-laptop sshd[5022]: Failed password for invalid user bb from 192.168.0.101 port 1160 ssh2
Oct 12 09:24:45 bill-laptop sshd[5217]: Invalid user bb from 192.168.0.101
Oct 12 09:24:45 bill-laptop sshd[5217]: Failed none for invalid user bb from 192.168.0.101 port 1167 ssh2
Oct 12 09:24:51 bill-laptop sshd[5217]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 09:24:51 bill-laptop sshd[5217]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 09:24:53 bill-laptop sshd[5217]: Failed password for invalid user bb from 192.168.0.101 port 1167 ssh2
Oct 12 09:25:07 bill-laptop sshd[5217]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 09:25:09 bill-laptop sshd[5217]: Failed password for invalid user bb from 192.168.0.101 port 1167 ssh2
Oct 12 13:56:57 bill-laptop sshd[9387]: Invalid user bb from 192.168.0.101
Oct 12 13:56:57 bill-laptop sshd[9387]: Failed none for invalid user bb from 192.168.0.101 port 1263 ssh2
Oct 12 13:57:04 bill-laptop sshd[9387]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 13:57:04 bill-laptop sshd[9387]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 13:57:06 bill-laptop sshd[9387]: Failed password for invalid user bb from 192.168.0.101 port 1263 ssh2
Oct 12 13:57:25 bill-laptop sshd[9387]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 13:57:27 bill-laptop sshd[9387]: Failed password for invalid user bb from 192.168.0.101 port 1263 ssh2
Oct 12 14:03:30 bill-laptop sshd[9472]: Invalid user bb from 192.168.0.101
Oct 12 14:03:30 bill-laptop sshd[9472]: Failed none for invalid user bb from 192.168.0.101 port 1269 ssh2
Oct 12 14:03:43 bill-laptop sshd[9472]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 14:03:43 bill-laptop sshd[9472]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 14:03:45 bill-laptop sshd[9472]: Failed password for invalid user bb from 192.168.0.101 port 1269 ssh2
Oct 12 14:19:25 bill-laptop sshd[9675]: Invalid user bb from 192.168.0.101
Oct 12 14:19:25 bill-laptop sshd[9675]: Failed none for invalid user bb from 192.168.0.101 port 1275 ssh2
Oct 12 14:19:37 bill-laptop sshd[9675]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 14:19:37 bill-laptop sshd[9675]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 14:19:40 bill-laptop sshd[9675]: Failed password for invalid user bb from 192.168.0.101 port 1275 ssh2
Oct 12 15:31:13 bill-laptop sudo:     bill : TTY=pts/0 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 16:27:21 bill-laptop sshd[4873]: Received signal 15; terminating.
Oct 12 16:27:21 bill-laptop sshd[11771]: Server listening on 0.0.0.0 port 22.
Oct 12 16:27:21 bill-laptop sshd[11771]: Server listening on :: port 22.
Oct 12 16:28:26 bill-laptop sshd[11775]: Invalid user bb from 192.168.0.101
Oct 12 16:28:26 bill-laptop sshd[11775]: Failed none for invalid user bb from 192.168.0.101 port 1365 ssh2
Oct 12 16:28:36 bill-laptop sshd[11775]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 16:28:36 bill-laptop sshd[11775]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 16:28:38 bill-laptop sshd[11775]: Failed password for invalid user bb from 192.168.0.101 port 1365 ssh2
Oct 12 16:29:06 bill-laptop sshd[11775]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 16:29:07 bill-laptop sshd[11775]: Failed password for invalid user bb from 192.168.0.101 port 1365 ssh2
Oct 12 16:52:38 bill-laptop sudo:     bill : TTY=pts/0 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 16:56:19 bill-laptop sudo:     bill : TTY=pts/0 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 16:56:59 bill-laptop sshd[11771]: Received signal 15; terminating.
Oct 12 16:56:59 bill-laptop sshd[12281]: Server listening on 0.0.0.0 port 22.
Oct 12 16:56:59 bill-laptop sshd[12281]: Server listening on :: port 22.
Oct 12 17:46:08 bill-laptop sshd[12281]: Received signal 15; terminating.
Oct 12 17:46:08 bill-laptop sshd[13076]: Server listening on 0.0.0.0 port 22.
Oct 12 17:46:08 bill-laptop sshd[13076]: Server listening on :: port 22.
Oct 12 19:46:35 bill-laptop sudo:     bill : TTY=pts/0 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 20:09:08 bill-laptop sudo:     bill : TTY=pts/1 ; PWD=/home/bill ; USER=root ; COMMAND=/bin/cp -r sshd_config /etc/ssh/
Oct 12 20:19:30 bill-laptop sshd[13076]: Received signal 15; terminating.
Oct 12 20:19:30 bill-laptop sshd[15652]: Server listening on 0.0.0.0 port 22.
Oct 12 20:19:30 bill-laptop sshd[15652]: Server listening on :: port 22.
Oct 12 20:20:40 bill-laptop sshd[15795]: Invalid user bb from 192.168.0.101
Oct 12 20:20:40 bill-laptop sshd[15795]: Failed none for invalid user bb from 192.168.0.101 port 1475 ssh2
Oct 12 20:20:51 bill-laptop sshd[15795]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 20:20:51 bill-laptop sshd[15795]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 20:20:53 bill-laptop sshd[15795]: Failed password for invalid user bb from 192.168.0.101 port 1475 ssh2
Oct 12 20:31:45 bill-laptop sshd[15941]: Invalid user bb from 192.168.0.101
Oct 12 20:31:45 bill-laptop sshd[15941]: Failed none for invalid user bb from 192.168.0.101 port 1478 ssh2
Oct 12 20:31:57 bill-laptop sshd[15941]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 20:31:57 bill-laptop sshd[15941]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 20:31:59 bill-laptop sshd[15941]: Failed password for invalid user bb from 192.168.0.101 port 1478 ssh2
Oct 12 22:19:25 bill-laptop sudo:     bill : TTY=pts/1 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 22:24:33 bill-laptop sudo:     bill : TTY=pts/1 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Oct 12 22:28:42 bill-laptop sshd[17617]: Invalid user bb from 192.168.0.101
Oct 12 22:28:42 bill-laptop sshd[17617]: Failed none for invalid user bb from 192.168.0.101 port 1954 ssh2
Oct 12 22:28:52 bill-laptop sshd[17617]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 22:28:52 bill-laptop sshd[17617]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.101 
Oct 12 22:28:55 bill-laptop sshd[17617]: Failed password for invalid user bb from 192.168.0.101 port 1954 ssh2
Oct 12 22:29:07 bill-laptop sshd[17617]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 22:29:08 bill-laptop sshd[17617]: Failed password for invalid user bb from 192.168.0.101 port 1954 ssh2
Oct 12 22:29:22 bill-laptop sshd[17617]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 22:29:24 bill-laptop sshd[17617]: Failed password for invalid user bb from 192.168.0.101 port 1954 ssh2
bill@bill-laptop:~$ 

```Oct 12 22:29:22 bill-laptop sshd[17617]: pam_unix(sshd:auth): check pass; user unknown
Oct 12 22:29:24 bill-laptop sshd[17617]: Failed password for invalid user bb from 192.168.0.101 port 1954 ssh2
this is the error that your machine is giving, let me look at something real fast, in the meantime just to give you something to do until i can post back and partly to entertain me, would you please type on the Linux machine:
[I]
ssh localhost[/I]

If ssh is working properly, you will see some output similar to this:
[I]
rob@localhost's password:
Linux vostro 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.


[/I]I suspect this is the case but it is good to check just to be sure.  For clarification, instead of trying to use SSH to login to the Linux machine from another computer, you are basically just trying to use ssh to login to the Linux machine from . . . You guessed it . . . the Linux machine.
If that is successful, we can eliminate the SSH service having any problems working. It just isn't allowing you to connect from the other computer. 
[I]
To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

Last login: Mon Oct 12 22:23:14 2009 from localhost[/I]

---

### Post by barnaclebill18 on 2009-10-12
I did that, but might have done something you did not want, it asked for yes or no and I said yes and hit enter, after I did it, I wondered if that was a mistake.
```

bill@bill-laptop:~$ ssh localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is ff:6f:3d:e6:62:dd:25:ad:01:98:ea:21:55:8a:8c:71.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
bill@localhost's password: 
Linux bill-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

bill@bill-laptop:~$ 

```

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> I did that, but might have done something you did not want, it asked for yes or no and I said yes and hit enter, after I did it, I wondered if that was a mistake.
```

bill@bill-laptop:~$ ssh localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is ff:6f:3d:e6:62:dd:25:ad:01:98:ea:21:55:8a:8c:71.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
bill@localhost's password: 
Linux bill-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

bill@bill-laptop:~$ 

```
no bill that was perfect, each computer has a fingerprint, and you just accepted the finger print.  This means you logged into the Linux machine successfully.  This doesn't do you any good because you are using it to do that, but it tells us that if we could successfully connect from the other machine, everything on the Linux machine (ssh server) is working correctly.
Now, the error messages that we logged earlier indicate that the problem is with the user name you are using on your XP machine being denied access. We can fix this.  We are very close.  
So bear with me and let me continue reading, and I will reply as quickly as possible.

In the meantime, can you try logging in using PuTTy again using your username on the Linux machine with the @ symbol followed by the IP address and try again? make sure ssh is selected.

SO if your user name on the linux machine is bill, and the IP of the linux machine is 192.168.xxx.xxx, put this in the IP box of putty
[EMAIL="bill@192.168.xxx.xxx"]bill@192.168.xxx.xxx[/EMAIL]
If you were to use capital letters in your login name, make sure you type it that way. Linux is case sensitive. 

Let me know if you get an error.  If so, post what you typed into the IP box of the PuTTY program.  
Good Luck.

---

### Post by 3rdalbum on 2009-10-12
> **barnaclebill18 said:**
> Today I decided to do a reinstall of 9.04 because of some problems I was having, and when choosing the partition I put it back on the same partition, I left the format box unchecked because it was already formatted as EXT3.

Well, I was surprised when I saw the desktop after it installed, all the changes I had made were still there, except for a couple small apps I had installed.

I was even more surprised to see my home folder intact with all my stuff, seems like all I needed was updates and restricted codecs. Even Google Chrome was still on the desktop.

I was wondering why this option is not ever mentioned, it seems like it would save time if you just wanted to repair your install.

Mine got fixed, Synaptic works right now, it was installing programs and Ubuntu could not find them.

I always mention the "you can reinstall onto a single-partition setup without losing the contents of /home" feature since I found it a couple of months ago :-)   But yes, I had heard a while back that it was going to be implemented, but I had heard nothing since so it was mildly surprising to see the contents of /home retained.

---

### Post by barnaclebill18 on 2009-10-12
I put bill@196.168.0.100 

I hit open and this time it did not ask me to log in,it said 'using username "bill", then it asked for the password for bill@196.168.0,100.

After I put in the PW, 'Access denied'

---

### Post by rb0171610 on 2009-10-12
> **barnaclebill18 said:**
> I put bill@196.168.0.100 

I hit open and this time it did not ask me to log in,it said 'using username "bill", then it asked for the password for bill@196.168.0,100.

After I put in the PW, 'Access denied'
bill@196.168.0,100  or bill@196.168.0.100?


Please try again a couple of times, making sure you type it in correctly and put in the right password of the Linux machine.  If you still get access denied, then post the output of the following command :

*ifconfig -a *

as well as:

[I]sudo cat /var/log/auth.log | grep sshd 

[/I]Good Luck.

---

### Post by barnaclebill18 on 2009-10-12
This time I think it worked.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
along with some other stuff, was there.

---

### Post by rb0171610 on 2009-10-13
> **barnaclebill18 said:**
> This time I think it worked.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
along with some other stuff, was there.
As long as you got a command prompt, a # sign or a $ you are set.  It certainly would appear that way.
Awesome Bill.  I am sorry that we had to go through all that trouble to figure out how to log in correctly.  I have the same user name on all of my computers for years so I never had to worry about it. It was a learning experience for me.  

Now, here is a tutorial about the command line in Linux.  Read it at your leisure.  You will learn a lot about the different things you can do from a command prompt. You can learn at your own pace.  It is very important to know how to use the command line or CLi to navigate your filesystem, reboot your computer, copy files, edit files, etc.
Sometimes you will need to do this if you are working at your Linux machine. You may find it much faster to open a terminal and type ifconfig -a to find your IP address than click through menus or open the right program to find the right menu to scroll down  the right tab to see the IP address, if you catch my drift. 

Also, if you want help setting up a ssh server on your XP machine, so you can login to it from Linux, Id be happy to show you how.

A beginner's tutorial to start learning the CLi:
[http://www.tuxfiles.org/linuxhelp/shell.html](http://www.tuxfiles.org/linuxhelp/shell.html)

this is a webpage that shows how to install the ssh server for XP:

[http://www.rasyid.net/2007/05/18/install-ssh-server-in-windows-xp/](http://www.rasyid.net/2007/05/18/install-ssh-server-in-windows-xp/)

Hopefully you learned something useful today. I know I did. Add me as a friend on here.  If you ever need help, let me know.

---

### Post by barnaclebill18 on 2009-10-13
Thank you for everything.

The thing now is, how do I use this, can I access files on the other computer now?

---

### Post by rb0171610 on 2009-10-13
> **barnaclebill18 said:**
> Thank you for everything.

The thing now is, how do I use this, can I access files on the other computer now?
Well for now it is only one way since you do not have an SSH client setup on the XP box yet.
The tutorial link I sent you is very thorough and will walk you through step by step all the things you can do at the command line.  
When you use Putty and open a command prompt and Login to your Linux machine, you have complete control of your Linux machine.

For example, try rebooting your Linux machine from the XP machine:

Use PuTTy to login, and type:

*sudo reboot*

Sit back and watch your laptop reboot.

---

### Post by barnaclebill18 on 2009-10-13
OK, I got it now.

I will have to get it set up so I can get stuff from the XP machine, because that is the way I would use it most.

I have been using the Linux for just about everything lately, there is only a few things I use XP for, like the PayPal plug-in when I need to buy something.

---

### Post by rb0171610 on 2009-10-13
> **barnaclebill18 said:**
> OK, I got it now.

I will have to get it set up so I can get stuff from the XP machine, because that is the way I would use it most.

I have been using the Linux for just about everything lately, there is only a few things I use XP for, like the PayPal plug-in when I need to buy something.
Cool.  Yes there is always that one thing lol.  Maybe they will make the plugin for Firefox 3 and you won't even need it for that.
There are a few added steps to go through if you want to transfer files remotely.  But for now  you could at least access your linux machine remotely and perform commands as if  you were sitting right in front of it.
It could prove useful to you someday.

---

### Post by barnaclebill18 on 2009-10-13
I doubt that PayPal would ever be an open source type of Plug-in, but it is listed in my Firefox add-ons.

It is real neat the way it works, if the place you are buying something from does not take PP, you can generate a one-time use Master Card to pay for it. You can also do that if they take PP, and you don't have to access PP through the vendors site. I like it.

I invited you to be a friend, I am headed to bed, big day tomorrow.

Thanks for all the help.

---

### Post by rb0171610 on 2009-10-13
> **barnaclebill18 said:**
> I doubt that PayPal would ever be an open source type of Plug-in, but it is listed in my Firefox add-ons.

It is real neat the way it works, if the place you are buying something from does not take PP, you can generate a one-time use Master Card to pay for it. You can also do that if they take PP, and you don't have to access PP through the vendors site. I like it.

I invited you to be a friend, I am headed to bed, big day tomorrow.

Thanks for all the help.
I accepted you as a friend.  
I will help you set up file sharing from your XP box next time.
Good Night Bill.

---

