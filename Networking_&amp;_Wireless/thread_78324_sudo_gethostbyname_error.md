---
title: "sudo gethostbyname error"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by MoshNet on 2005-10-18
Ok, whenever I try to complete a command, like sudo, I get this error..

```

ssga@:~$ sudo chmod 666 /dev/dsp
sudo: unable to lookup  via gethostbyname()

```

Why does it try to get my reverse DNS? I do not have it enabled...

Also when I try to open up networking, it says its opening, and opens in the "taskbar" (IM used to windows sorry) then it just closes...

Im so depressed like.. :-(

---

### Post by nocturn on 2005-10-18
[QUOTE=MoshNet]Ok, whenever I try to complete a command, like sudo, I get this error..

```

ssga@:~$ sudo chmod 666 /dev/dsp
sudo: unable to lookup  via gethostbyname()

```

Why does it try to get my reverse DNS? I do not have it enabled...

Also when I try to open up networking, it says its opening, and opens in the "taskbar" (IM used to windows sorry) then it just closes...

Im so depressed like.. :-([/QUOTE]

Can you post your /etc/hosts file please?

---

### Post by MoshNet on 2005-10-18
```

order hosts,bind
multi on

```

Thats it. I'm pretty sure the error is its trying to reverse my IP to a name, and it won't work since my ip has no reverse DNS. I just don't know how to correct this being so new to LInux. Also, From System > Administration >Networking.. When I try to open networking, it says starting, but then closes before it can open? What the heck?

---

### Post by tvandenbos on 2005-10-18
i have the same problem with edubuntu

---

### Post by nocturn on 2005-10-19
[QUOTE=MoshNet]```

order hosts,bind
multi on

```
[/QUOTE]


Is this in your /etc/hosts file?  Then it is wrong.
It should read something like this: 
```

127.0.0.1       localhost

```

---

### Post by nocturn on 2005-10-19
The code you posted should be in /etc/host.conf file.

---

### Post by MoshNet on 2005-10-19
I'm sorry , you are right noc.. I did read from the wrong file.

HERE IS THE RIGHT FILE...

```

127.0.0.1 localhost.localdomain localhost ubuntu 
209.82.191.113 ubuntu

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by luke.stanbra on 2005-10-19
I have exactly the same problem....well, the same symptoms anyway

My /etc/hosts file is:
```
127.0.0.1 localhost.localdomain localhost skywalker

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by nocturn on 2005-10-24
Strange

Can you also post the contents of your /etc/nsswitch.conf file?

And the output of 
```

ifconfig

```

and

```

ping localhost

```

---

### Post by heimo on 2005-10-24
Also make sure that *hostname *(run this on terminal without parematers) returns same name as you have in */etc/hosts *file. If not, you can set it using *hostname [newhostname]. *Check that your username is included in /etc/sudoers (use sudoedit to edit this file).

---

### Post by stevea1210 on 2005-10-25
[QUOTE=nocturn]Strange

Can you also post the contents of your /etc/nsswitch.conf file?

And the output of 
```

ifconfig

```

and

```

ping localhost

```[/QUOTE]


Thank you so much nocturn.  I've been battling this one for days.  Everything in the forums say it is your /etc/hosts file.  I knew that wasn't the case in my situation.  For me, It was my nsswitch.conf.   I had joined all of ubuntu boxes to my win 2k3 AD domain, and screwed up the nsswitch.conf on this one.  I owe you one.:)

---

### Post by Topsiho on 2005-10-27
Hello, my name ( :) ) is Topsiho,

I have a problem much like this one, I know the cause but cannot correct it, as sudo does not work and gives:

sudo: unable to lookup Bromo via gethostbyname()

My computername is Bromo.Brantas with alias Bromo

but in my /etc/host file I entered

<home network Ip- address> Bromo.Brantas Brantas

instead of

<home network ip-address> Bromo.Brantas Bromo

This I want to correct of course but can not because I need sudo, but can't !!!

Who has got a solution to this?

I would be very grateful to her/him :)

Greetz,

Topsiho

---

### Post by Topsiho on 2005-10-27
A follow-up to my previous post:

Rebooting into recoverymode gives root privileges, just what is necessary.
Mended /etc/hosts deleting the offending line as it is not necessary: this computer is the localhost.

However: the problem persists after reboot into normal mode.
The error line is exactly the same so the cause is still there.

What should be in the hostname file, as that is as far as I know the only one left with the name Bromo in it that is mentioned in that line....

Greetz,

Topsiho

---

### Post by mxyzptlk on 2005-10-27
restart your system, in the session screen type alt+ctrl+f1
 now you are as root

find your ect/host file and at the top of if write this

127.0.0.1 localhost.localdomain localhost <yourhostname> 
reboot and thats it

---

### Post by Topsiho on 2005-10-28
Thanks very much!

Problem is solved.
This is what I did:

rebooted in recovery mode. Then you are root.
replaced erroneous line in /etc/hosts with

<home network ip-number> Bromo.Brantas **Bromo**

rebooted computer in the normal mode

et voila: sudo works again

Of course I'll replay your answer too, but it is not necessary (for me) now :)

Thanks,

Topsiho

---

### Post by luke.stanbra on 2005-11-03
nsswitch.conf
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:C0:49:55:6A:13
          inet addr:129.234.121.110  Bcast:129.234.121.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:372 txqueuelen:1000
          RX bytes:1019457 (995.5 KiB)  TX bytes:192380 (187.8 KiB)
          Interrupt:16 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:333582 (325.7 KiB)  TX bytes:333582 (325.7 KiB)

```
ping localhost
```

64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=1 ttl=64 time=0.027 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=2 ttl=64 time=0.019 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=3 ttl=64 time=0.015 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=4 ttl=64 time=0.019 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=5 ttl=64 time=0.021 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=6 ttl=64 time=0.017 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=7 ttl=64 time=0.023 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=8 ttl=64 time=0.023 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=9 ttl=64 time=0.019 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=10 ttl=64 time=0.023 ms
...

```
This then continues...and doesn't stop...(I let it go to ~250 before I manually closed the terminal)

---

### Post by naught101 on 2006-07-20
got the same problem here, except my /etc/hosts appears all correct:
```
127.0.0.1 localhost.localdomain localhost np

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
and my nsswitch.conf:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
and the eth0 entry from ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:12:3F:21:23:9E
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe21:239e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5327544 (5.0 MiB)  TX bytes:426476 (416.4 KiB)
          Interrupt:169


```
ping localhost works fine.

when I run hostname as root, it looks like this:
```
root@naughttop:/home/naught101# hostname

root@naughttop:/home/naught101# 
```ie. ther is no hostname, which makes me think, I deleted my host name from kcontrol>>network settings>>hostnames (can't remember, I can't open it right now). and that was probably the point where it all went sideways.
if I run "hostname np" as root, it fixes it, so that sudo works, and the response to "hostname" is "np", but then I get "KLauncher could not be reached via DCOP" errors when ever I try to open something from a KDE icon. I've tried searching the forums for ways to fix the DCOP errors, but I haven't found anything to help.

the host name resets everytime I reboot, to ""
[QUOTE=stevea1210]Thank you so much nocturn. I've been battling this one for days. Everything in the forums say it is your /etc/hosts file. I knew that wasn't the case in my situation. For me, It was my nsswitch.conf. I had joined all of ubuntu boxes to my win 2k3 AD domain, and screwed up the nsswitch.conf on this one. I owe you one.[/QUOTE]that looks promising, but I don't know what I should be fixing in my nsswitch.conf if that is the problem. I tried putting "np" in the "hosts:" field after the others, but it didn't work.

when you change the hostname in the network setting through kcontrol, what files does it change? perhaps if I know that I can change it back. I figure changing it back through kcontrol would fix it, but either sudo doesn't work, or if sudo does work, DCOP stuffs up (I don't understand it), and I can't open kcontrol anyway. I tried opening kcontrol from a root terminal, but I get error messages saying that, among other x errors, "kcontrol: cannot connect to X server :0.0"

PLEASE, any help with this would be greatly appreciated.

oh, and I'm actually using dapper 6.06, but the problem seems exactly the same.
-------
edit: reposted the problem [here at in the dapper forum]("http://ubuntuforums.org/showthread.php?p=1278563"), as that's where it should be for my case

---

### Post by naught101 on 2006-07-20
HAHA!! got it!

need to edit **/etc/hostname** and add <hostname> to read simply:
```
np
```
simple. won't do that again.

thanks to **aleoje** in [this thread]("http://http://ubuntuforums.org/showthread.php?t=188337")

----
_Suggestion to Ubuntu maintainers:_
NEVER let anyone put a zero-sized entry into the Kcontrol>>Network Settings>>Domain Name System>>Hostname field. this will kill all newbies on the spot.

---

### Post by shongzah on 2006-08-09
I've been having the same problem.  In the GUI my sudoers file has a red X through it.  When I pull up the properties it tells me that it is unreadable. WTF! Help!!

---

### Post by dokumentamarble on 2006-08-12
ive tried the ctrl+alt+f1 and it doesnt log me in as anything, and i do not know how to log in as root, i can only log in as my regular account. any help is appreciated.

---

### Post by unloadlocal on 2006-09-02
I had the same problem and followed the steps in the thread to fix it but a little differantly. Here's what I did:

1)Restart ubuntu and hit esc in Grub

2)Choose recovery mode

3)At command line do a "vi /etc/hosts"

4)hit insert and add your hostname at the end of the line with 127.0.0.1

5)hit esc to exit the insert mode and press shift x. then press enter to confirm save

6)now back at the command line enter "hostname (your hostname)"

7)now type exit and login as usual at the login screen

---

### Post by don_m on 2006-09-06
I added a bit of detail:

1. Choose recovery mode when booting.
2. At command line, type "vi /etc/hosts"
3. Press Insert on keyboard, and enter "127.0.0.1 IBMT23" (substitute your hostname for IBMT23)
4. Press escape.
5. Vi editor works with a ":" command, so type ":wq".
6. File should be saved and type exit to login.
7. You should now be able to access "Network Adminstration" as well as the avoiding the posted error.:-D 

[http://www.eng.hawaii.edu/Tutor/vi.html](http://www.eng.hawaii.edu/Tutor/vi.html)

---

### Post by eschreib on 2006-09-08
I'm having the same issue, and even if I go into the recovery consul as 'su' I can not copy into the etc/ directory.
vi will not let me save there either.
Any ideas?

---

### Post by don_m on 2006-09-09
I had the same problem to and it seemed to work after a couple of tries.

I did try the installation CD, but I could not access the Ubuntu partition.

At that point, I was speculating whether I could download a copy of perhaps Knoppix and mount the partition, and then overwrite the file. 

But I do not know enough about Linux partitions as to whether I am restricted if I were to mount an Ubuntu partition. I would have to try it.

---

### Post by goathunter on 2007-01-16
> I added a bit of detail:

1. Choose recovery mode when booting.
2. At command line, type "vi /etc/hosts"
3. Press Insert on keyboard, and enter "127.0.0.1 IBMT23" (substitute your hostname for IBMT23)
4. Press escape.
5. Vi editor works with a ":" command, so type ":wq".
6. File should be saved and type exit to login.
7. You should now be able to access "Network Adminstration" as well as the avoiding the posted error. 

i had the same problem with the network admin not working. Also synaptic, updatenotifier and automatic 2 fail to start. I did your solution but nothing seem to have changed. Is there anything else i can short of a reformat and reinstall?
cheers

---

### Post by perc76 on 2007-03-02
Hello! I was playing with my network-admin settings, when I deleted (on purpose) the Hosts entry there that says "127.0.0.1    localhost edubuntu".

result... next boot, I can no longer run "sudo" and it gives the message title above. and I don't know "root" password. my previous attempt to run sudo yielded "root@edubuntu"... now , I'm being told I entered the wrong password. Okay...

Solution: Somebody in the "irc.freenode.net #ubuntu channel" advised me to login as single to grab control. How?
1. boot like you used to.
2. when you see the prompt asking you to press "ESC"... do so.
3. modify the kernel command and add "single" to the line. just read the commands given you and you will be fine. You will be taken into editing several lines of command that will boot your OS... take the line that's the longest... and add "single" at it's end.
4. (I forgot what command was next... it's on screen anyway, but the general idea is to boot using the edited routine.
5. now, you are logged in as root@edubuntu... change it's password by the command passwd.
6. reboot your system.
7. after logging in to your account, run a terminal and type "su", you will be asked to enter the password you typed for root.
8. enter this command: "network-admin" or "gksu network-admin", whichever works for you.
9. go to the "Hosts" tab. and click "add button".
10. type "127.0.0.1" to the IP Address field and "localhost" to the Aliases field.
11. click OK until you are out of the network-admin.
12. now, open a new terminal (you may also use the previously opened terminal, but you must "exit" from root.
13. try "sudo", your system should be functioning like mine, now :D

--disclaimer--
I'm only a newbie in ubuntu... don't know much commands, but I refuse to give up. sorry for the missing commands above... will try to do better next time. :)

---together, we can make things work---

---

