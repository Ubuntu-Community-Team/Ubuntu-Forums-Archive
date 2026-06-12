---
title: "Setting up a home network for dummies"
date: 2014-12-16
forum: Networking &amp; Wireless
---

### Post by andyjohnson56003 on 2014-12-16
Hello everyone. I am new here and hoping I could possibly get some guidence. I want to set up a home network with Ubuntu. My main goals are:

Share files
Access a raspberry pi "headless"
Access both my machines and the raspberry pi from the internet. 

I am really hitting a road block as I know NOTHING about networking, and don't know where to start. 

I was wondering if someone knows of a good beginner tutorial with all the steps I will need to master, or if someone here would be willing to walk me though it. 

I am comfortable with the terminal provided I know what I need to be entering there. 

Any help or advice would be amazing. :)

-Andy

---

### Post by papibe on 2014-12-16
Hi andyjohnson56003. Welcome to the forum ):P

There are several steps to get access to your machines and files from the Internet:

If you're unfamiliar with that concepts mention below, take a look at this is a very helpul [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

This would be the main steps:
[LIST]
[*]Set your server with a LAN static IP.
[*]Install openssh-server on your server.
[*]Test LAN ssh access to your server.
[*]Optional: change the standar ssh port (22) to a different, preferable higher value.
[*]Subscribe to a Dynamic DNS service. There are free and pay options. For example: DynDNS, no-ip, zoneedit, etc (check [here]("http://dnslookup.me/dynamic-dns/") for a longer list).
[*]Either install and setup the package ddclient, or (better if available) set your DDNS client in your router.
[*]Forward the ssh port in your router to your server.
[/LIST]
Now you are ready to test accessing your server over the internet.

Important: do not try to access your server using its public IP, or dynamic name from inside your own LAN. The proper way to test access is from outside your network. For example, an internet café, public library, a friend house, or using your phone or tablet's 3G service (be sure to NOT being connected to your LAN's WiFi though).

I hope that points you in the right direction, and let us know how it goes.
Regards.

---

### Post by andyjohnson56003 on 2014-12-16
Thanks for the fast reply. I did check out the video you posted. Some of the basic concepts of IP addresses and name servers are somewhat familiar to me, but where I am really stuck is getting my machine set up. 

I have been studying this video

[https://www.youtube.com/watch?v=PEa1xopeufQ](https://www.youtube.com/watch?v=PEa1xopeufQ)

He uses sudo vim /etc/network/interfaces

vim doesn't work for me, but after some googling I saw it done as 

sudo vi /etc/network/interfaces and that does something, but instead of bringing up anything like the video, I get 

E325: ATTENTION
Found a swap file by the name "/etc/network/.interfaces.swp"
          owned by: root   dated: Tue Dec 16 21:49:12 2014
         file name: /etc/network/interfaces
          modified: YES
         user name: root   host name: andy-ThinkPad-X200
        process ID: 12265
While opening file "/etc/network/interfaces"
             dated: Tue Mar 19 18:59:28 2013

(1) Another program may be editing the same file.  If this is the case,
    be careful not to end up with two different instances of the same
    file when making changes.  Quit, or continue with caution.
(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/network/interfaces"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/network/.interfaces.swp"

    to avoid this message.
"/etc/network/interfaces" 3 lines, 82 characters
Press ENTER or type command to continue

and then

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
Type  :quit<Enter>  to exit Vim

Any thoughts?

-Andy

---

### Post by papibe on 2014-12-16
I would try first to set reservations on the router itself, and left the config files as they are.

See if you can set up an static IP from your router's admin pages.

Regards.

---

### Post by andyjohnson56003 on 2014-12-16
Ok. I will explore that tomorrow. Thanks!

---

### Post by spiffymoo on 2014-12-16
i found this page it talks about[h=4]Getting the IP address of the Raspberry Pi, Connecting over SSH, Configuring VNC[/h]  hope it helps
[http://mitchtech.net/vnc-setup-on-raspberry-pi-from-ubuntu/](http://mitchtech.net/vnc-setup-on-raspberry-pi-from-ubuntu/)

---

### Post by Bucky Ball on 2014-12-17
One thing that might help is to exit vim and use nano:

```
sudo nano /etc/network/interfaces
```

You can open the file to have a look, and safer, with:

```
nano /etc/network/interfaces
```

If you're going to make changes when using the first (sudo) command, good idea to make a backup of the file first.

You can also use vi, but it appears you might have opened the file in vim and also be opening it with vi. I've never used either so couldn't confirm and don't know if that's possible. ;) 

I use Putty to communicate SSH with the RPi (and the Odroid).

---

### Post by andyjohnson56003 on 2014-12-17
Just wanted to say thanks again. Tonight I was able to get into my desktop via my laptop and ssh and create a directory. As simple as that is to you all, it was a big moment for me. :D 

I know I will have more questions in the coming days, but just wanted to post an update!

spiffymoo - your link helped me a bunch!

---

