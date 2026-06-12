---
title: "Connect two ubuntu PC's?"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by ian2112 on 2009-08-09
Hi

I'm looking for some general direction / thoughts towards methods access one ubuntu PC from another.

Here's the background: before switching to linux I loaded up linux on an old PC a friend had given me.  Because that was so much fun I loaded linux on my new PC. Now I would like to access the old via my home network (wired connection).

While the more immediate desire is to simply transfer some files I downloaded, in the future I'd like to use the older PC as sandbox, etc.  Ideally, I'd like to be able to connect to the old PC as though the keyboard and monitor were directly attached, and I was using old PC desktop (i.e., more than command line access).

I'm guessing I need to install and setup some sort of server on the old PC and then connect via a client from my new one.  Perhaps this is processing / bandwidth problem, not sure?

Last, any precautions regarding security / internet are welcome.  My intent is that this would only be a local (i.e., no internet) connnection between the two PCs.

I'm all ears!

Thanks,
Ian.

---

### Post by alphacrucis2 on 2009-08-09
> **ian2112 said:**
> Hi

I'm looking for some general direction / thoughts towards methods access one ubuntu PC from another.

Here's the background: before switching to linux I loaded up linux on an old PC a friend had given me.  Because that was so much fun I loaded linux on my new PC. Now I would like to access the old via my home network (wired connection).

While the more immediate desire is to simply transfer some files I downloaded, in the future I'd like to use the older PC as sandbox, etc.  Ideally, I'd like to be able to connect to the old PC as though the keyboard and monitor were directly attached, and I was using old PC desktop (i.e., more than command line access).

I'm guessing I need to install and setup some sort of server on the old PC and then connect via a client from my new one.  Perhaps this is processing / bandwidth problem, not sure?

Last, any precautions regarding security / internet are welcome.  My intent is that this would only be a local (i.e., no internet) connnection between the two PCs.

I'm all ears!

Thanks,
Ian.

Command line access use ssh or install an ssh gui client such as putty. 

Graphical access - VNC might suit your needs.

File access. Probably the easiest is to use samba as it caters for Windows file sharing as well.

---

### Post by dlmarti on 2009-08-09
Using nautilus through ssh, its simply a matter of dragging and dropping files.

Are you using KDE or Gnome?

---

### Post by lvleph on 2009-08-09
If you want to just copy some files every now and then, but not have a network share, use ssh and scp. If you want a network share use samba.

---

### Post by x33a on 2009-08-09
for file transfer:

first install ssh.

```
sudo aptitude install ssh
```then install filezilla
```
sudo aptitude install filezilla
```and use it to connect to the other pc.

note: you'll need to install these on both the computers.

---

### Post by mapes12 on 2009-08-10
Hi Ian

so, i guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved. I only state this because the solution that i am thinking of writing down here will NOT WORK to access windows machines.

I also do not know if there is a simpler way - this is the simplest way i know.

1.) Make sure the openssh-server is installed on both machines. You can check in Places>Connect to Server and make sure SSH is an option in the service type drop down box. If it isn't installed then type this command in both computers Terminal and let them run through. 

```
sudo apt-get install openssh-server
```

2.) find out the IP addresses of your computer this is important to address the computers. use the following command to obtain your computers IP-Address

```
ifconfig

```
this should give you an output just like this one

> eth0      Link encap:Ethernet  HWaddr 00:50:da:e0:67:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1732 (1.7 KB)  TX bytes:1732 (1.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:dd:a9:16  
          inet addr:**192.168.1.68**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fedd:a916/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1661090 (1.6 MB)  TX bytes:342426 (342.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-DD-A9-16-39-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

your output can differ quite a bit, but the imporant information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - there must always be a second).
so, in my case the address would be 192.168.1.68

3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server.
- Choose SSH as the at the service type
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Most imporant - click ok
you will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is **Secure** Shell which is designed to be just that i.e. secure.

The above will get your file sharing sorted quickly. For more advanced file sharing and taking remote control over the other machine then *"EDIT - reference to Remobo removed"* [Yuuguu]("http://www.yuuguu.com/home") have been suggested to me. I had a problem installing Remobo but I think that was my fault. I successfully installed Yuuguu yesterday but haven't had a chance to work with it yet

Hope this helps.

Mark

UPDATE - I've had it confirmed from another forum member (more experienced than me) that the problem I had with Remobo was not just me. scorp123 has had the same issue. Remobo uses an out of date protocol. scorp123 recommends leave it alone.

---

### Post by theozzlives on 2009-08-10
I've got 2 PCs connected to my router and transfer files over the network, I use 1 Monitor, Keyboard, Mouse via an A/B switch I picked up at Radio Shack.

---

### Post by gtr32 on 2009-08-10
> **alphacrucis2 said:**
> Graphical access - VNC might suit your needs.

Depends on the situation but in most cases X forwarding via SSH is IMO a much better option.

File copy, many ways to skin the cat but I would also recommend the methods lvleph already mentioned: Samba and scp. Easy to setup and use.

---

### Post by ian2112 on 2009-08-10
Everyone,

Thank-you for all the ideas!  I'll see what I can get working over the next day or so.  Very much appreciated.

Ian.

---

### Post by frncz on 2009-08-10
> **mapes12 said:**
> Hi Ian

so, i guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved. I only state this because the solution that i am thinking of writing down here will NOT WORK to access windows machines.

I also do not know if there is a simpler way - this is the simplest way i know.

1.) Make sure the openssh-server is installed on both machines. You can check in Places>Connect to Server and make sure SSH is an option in the service type drop down box. If it isn't installed then type this command in both computers Terminal and let them run through. 

```
sudo apt-get install openssh-server
```

2.) find out the IP addresses of your computer this is important to address the computers. use the following command to obtain your computers IP-Address

```
ifconfig

```
this should give you an output just like this one


your output can differ quite a bit, but the imporant information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - there must always be a second).
so, in my case the address would be 192.168.1.68

3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server.
- Choose SSH as the at the service type
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Most imporant - click ok
you will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is **Secure** Shell which is designed to be just that i.e. secure.

The above will get your file sharing sorted quickly. For more advanced file sharing and taking remote control over the other machine then both [Remobo]("http://www.remobo.com/") and [Yuuguu]("http://www.yuuguu.com/home") have been suggested to me. I had a problem installing Remobo but I think that was my fault. I successfully installed Yuuguu yesterday but haven't had a chance to work with it yet

Hope this helps.

Mark

This works great. Thanks

Mike

---

### Post by mapes12 on 2009-08-10
> This works great. Thanks

MikeYour welcome :lolflag:

---

### Post by ian2112 on 2009-08-12
This to let everyone know I've had success with ssh - thanks!  Files are copying as I type :)

If VNC is the same is Ubuntu's Remote Desktop then I was partially successful (please correct me here if I'm wrong here - I didn't spend much time reading and confirming).  I was able to login (I think) but got a black screen.  So, some more troubleshooting there.  I have yet to try the Remobo service, but that seems like a neat option too.  Ultimately this is the level of remote desktop administration I'd like to achieve.

As well, I plan to explore samba as I have some windows pc's and this seems the route to get them talking to one another.

Most important for me is to again express thanks and to let everyone know I'm having success based on your help, so thanks again!

Ian.

---

### Post by mapes12 on 2009-08-13
> **ian2112 said:**
> This to let everyone know I've had success with ssh - thanks!  Files are copying as I type :)

If VNC is the same is Ubuntu's Remote Desktop then I was partially successful (please correct me here if I'm wrong here - I didn't spend much time reading and confirming).  I was able to login (I think) but got a black screen.  So, some more troubleshooting there.  I have yet to try the Remobo service, but that seems like a neat option too.  Ultimately this is the level of remote desktop administration I'd like to achieve.

As well, I plan to explore samba as I have some windows pc's and this seems the route to get them talking to one another.

Most important for me is to again express thanks and to let everyone know I'm having success based on your help, so thanks again!

Ian.Hi Ian

Glad to hear of your success. Remobo is no longer recommended. See my edit to post #6. If you get windoze to share perhaps you could help me out. Here's my post: [http://ubuntuforums.org/showthread.php?t=1238509](http://ubuntuforums.org/showthread.php?t=1238509)

---

### Post by MrWES on 2009-08-13
> **ian2112 said:**
> This to let everyone know I've had success with ssh - thanks!  Files are copying as I type :)

If VNC is the same is Ubuntu's Remote Desktop then I was partially successful (please correct me here if I'm wrong here - I didn't spend much time reading and confirming).  I was able to login (I think) but got a black screen.  So, some more troubleshooting there.  I have yet to try the Remobo service, but that seems like a neat option too.  Ultimately this is the level of remote desktop administration I'd like to achieve.

As well, I plan to explore samba as I have some windows pc's and this seems the route to get them talking to one another.

Most important for me is to again express thanks and to let everyone know I'm having success based on your help, so thanks again!

Ian.

Here's a how to I used to setup Samba:
[Samba How To]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by 3rdalbum on 2009-08-13
For some things, X forwarding with SSH is great. If you need to adjust some settings in a GUI program running on your server, then it's fantastic. If you need to do file management in the GUI, then you can run a file manager over SSH.

If you want to tell the server to do something in a GUI program that will take a long time, and you won't be keeping the client computer on or you don't trust the reliability of your network, VNC works well there.

---

