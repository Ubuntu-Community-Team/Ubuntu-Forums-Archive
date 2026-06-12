---
title: "How do you network 2 Linux computers locally?"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-04-26
I guess I never really thought about it before, but how do you actually set up networking for 2 side-by-side computers with Ubuntu 10.x?

Like 2 computers side by side connected to the same router and local IP addresses (like 192.168.x.x)

Do you have to enable networking somehow?  Do you just share folders or is there more to it?

---

### Post by pricetech on 2011-04-26
If it's two Ubuntu boxen on the same subnet, it's a piece of cake.  Look for Places - Connect to Server.  Choose SSH as the Service Type, fill in the blanks, and you're good.

---

### Post by donkyhotay on 2011-04-26
Technically they are networked since they both have valid IP addresses, however if you want to share files between them you'll need something else. How to share files can be a big question and depends on the type of network and sharing you need. If you're going to do anything with a windows comp you will want samba. Personally I just keep everything I want on a "file server" running apache and have each computer download what they need from it. Lots of people use FTP, there are probably more newbie friendly ways too.

---

### Post by Learning Linux 2011 on 2011-04-26
>  If it's two Ubuntu boxen on the same subnet, it's a piece of cake.  Look  for Places - Connect to Server.  Choose SSH as the Service Type, fill  in the blanks, and you're good. 

So what is the "server" then?  Assuming they are both desktop installs of Linux.

---

### Post by donkyhotay on 2011-04-26
> **Learning Linux 2011 said:**
> So what is the "server" then?  Assuming they are both desktop installs of Linux.

Technically both computers are "servers", remember that lots of linux usage is on the server scene so some of the phrasing in the software reflects that. The only difference between a "server" and a "desktop" is how you use it. As I mentioned I have a fileserver set up but thats basically a broken down old desktop that I've repurposed into sharing files onto my other computers. Basically if you consider each computer as a server they will be able to host and share files to each other equally. From a computer perspective thats what windows file sharing does but they call it "hosting" or something silly like that to make people feel more confident about what they are doing. It's the same thing though.

---

### Post by Learning Linux 2011 on 2011-04-26
> **donkyhotay said:**
> Technically they are networked since they both have valid IP addresses, however if you want to share files between them you'll need something else. How to share files can be a big question and depends on the type of network and sharing you need. If you're going to do anything with a windows comp you will want samba. Personally I just keep everything I want on a "file server" running apache and have each computer download what they need from it. Lots of people use FTP, there are probably more newbie friendly ways too.

Yeah, I guess I mean like sharing folders and files, so that one computer could "browse" another computer and transfer files, etc.

I understand that technically they are already "networked" since they are plugged into the same router and have the same subnet (I think one is 192.168.1.10 and the other is 192.168.1.11)

I always thought Apache was just WWW, does it also double as an FTP server?

---

### Post by Learning Linux 2011 on 2011-04-26
> **donkyhotay said:**
> Technically both computers are "servers", remember that lots of linux usage is on the server scene so some of the phrasing in the software reflects that. The only difference between a "server" and a "desktop" is how you use it. As I mentioned I have a fileserver set up but thats basically a broken down old desktop that I've repurposed into sharing files onto my other computers. Basically if you consider each computer as a server they will be able to host and share files to each other equally.

Ok, that makes sense.  Can you explain how it actually works in your case?  Like does one computer connect to the other and uses FTP to transfer files?  Do you use command line, or a web browser (or does it matter)?

Are both computers FTP servers? So you can transfer files between both?

Can/do you do it by IP address or server name?  How do you know what the server name is?

---

### Post by hodge3153 on 2011-04-26
> **Learning Linux 2011 said:**
> I guess I never really thought about it before, but how do you actually set up networking for 2 side-by-side computers with Ubuntu 10.x?

Like 2 computers side by side connected to the same router and local IP addresses (like 192.168.x.x)

Do you have to enable networking somehow?  Do you just share folders or is there more to it?

As stated earlier there are lots of ways to accomplish this, but it sounds as though what your are probably looking for is called a samba share.  Take a look at this posting: 

[http://ubuntuforums.org/showthread.php?t=1468498](http://ubuntuforums.org/showthread.php?t=1468498)

---

### Post by Learning Linux 2011 on 2011-04-26
> **hodge3153 said:**
> As stated earlier there are lots of ways to accomplish this, but it sounds as though what your are probably looking for is called a samba share.  Take a look at this posting: 

[http://ubuntuforums.org/showthread.php?t=1468498](http://ubuntuforums.org/showthread.php?t=1468498)

I thought Samba was for Linux and Windows, is it also for 2 Linux installations?

---

### Post by donkyhotay on 2011-04-26
I probably shouldn't have mentioned anything, the system I use works for me but I wouldn't recommend for a beginning user but here goes:

So I have an old headless desktop running apache that I connect to via SSH (CLI, no GUI). I use that to download various files from the internet that I want to store and easily transfer to my desktops and make accessible to friends easily when they visit (main reason I do it this way). To download the file they just type the local IP address of the server into their browser, click on the file, and it's downloaded. No muss, no fuss. Course it's not the best for sharing random stuff on my computer as I need to specifically get it onto the server first for others but that is how I do filesharing on my own personal network. If you want to try it do a google search for "beginning apache tutorial" and go for it. Otherwise I'd do something else for more simple filesharing.

---

### Post by earthpigg on 2011-04-26
The easiest way to shoot files/folders across a LAN and have it go faster than your _inter_net connection would allow is via '[giver]("http://tombuntu.com/index.php/2008/12/19/simple-desktop-file-sharing-with-giver/")'. It's in the repos, and what my roomate and I use.

[IMG]http://tombuntu.com/wp-content/uploads/2008/12/giver1.jpg[/IMG]
[IMG]http://tombuntu.com/wp-content/uploads/2008/12/giver2.jpg[/IMG]

'tom' is the username he uses on all his computers on his LAN in that example, and 'eeetom'/'quadtom' is what he named those computers when he installed ubuntu.

---

### Post by hodge3153 on 2011-04-26
> **Learning Linux 2011 said:**
> I thought Samba was for Linux and Windows, is it also for 2 Linux installations?

Samba can be used between 2 or more Linux boxes, it is not just for Windows to Linux. Another method is to use sshfs.  sshfs is not installed by default but apt-get install sshfs will do the it.

---

### Post by linuxyogi on 2011-04-26
I use NFS. Its really simple to setup & a lot faster than samba.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Simple copy & paste.

---

### Post by oldfred on 2011-04-26
My portable was XP and desktop Ubuntu. But everytime windows, firewall or other software updated in windows my Samba had to be reset. I just decided it was time to convert portable and was using NFS for the last couple years. Someone suggested SSH and that seems even easier.

[https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html)
In the menu go accessories > terminal and copy and paste
sudo apt-get install openssh-server openssh-client
Do this on both machines.
That`s it for commands.

On the machine you want to share files from, right click on the network icon and choose "conection information". This will tell you the ip address.
On the other machine, go places > connect to server
In the top box (service type) choose ssh
in the server box type username@ipaddress substituting your real username and real ip address

Don`t worry about the next 2 boxes unless you only want to share specific folders.
Tick (check) the add bookmark box
In the bottom box give your other computer a name.

After you click connect you will be able to access all files and folders on the other machine from your places menu using the bookmark name you just gave it.

You can also connect to an ssh server from the command line, eg:
ssh charlie@192.168.1.2

---

### Post by Miljet on 2011-04-26
As you have seen from the replies, there are multiple ways to accomplish what you want. And believe me, I have tried most of them at one time or another. I finally settled on NFS. This is the absolutely best tutorial on connecting two machines using NFS that I have found.
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

---

### Post by Dude-PWB- on 2011-04-26
Aside from using ssh in the command line for doing work on the other PC's, I used the commands from post #6 in this link [http://ubuntuforums.org/showthread.php?t=1543087&highlight=share+folder+local+machine ]("http://ubuntuforums.org/showthread.php?t=1543087&highlight=share+folder+local+machine")to allow me to transfer files between the PC's. Since it is ssh/ftp (sftp) it is a little slower than it would normally be since everything is encrypted but it is simple and easy to set up.

---

### Post by Buntumatic on 2011-04-26
> **linuxyogi said:**
> I use NFS. Its really simple to setup & a lot faster than samba.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Simple copy & paste.
That's your answer, NFS.

---

