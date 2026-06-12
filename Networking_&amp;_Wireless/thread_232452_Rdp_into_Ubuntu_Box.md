---
title: "Rdp into Ubuntu Box"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by turath on 2006-08-08
Greets

Just setup a fresh ubuntu box for testing in my office.

Trying to rdp into the box via network.

Box has ip..can connect to the windows server from it.

What am I missing that will allow me to 

use Remote desktop from my windows machine and log into the server.

Any help is appreciated.

Ubuntu 6.06
p4

---

### Post by harisund on 2006-08-08
What does 'can connect to the Windows server from it' mean? Are you able to connect using SSH/VNC?

Anyway, you can't use 'Remote Desktop' from Windows to Linux. Remote Desktop is a Windows only protocol.

---

### Post by turath on 2006-08-08
Awesome

You just gave me info I did not know.

Thanks.


Nwo how do I log into the Linux box from Windows?

Is there an easy way to do this .


-Thanks

> **harisund said:**
> What does 'can connect to the Windows server from it' mean? Are you able to connect using SSH/VNC?

Anyway, you can't use 'Remote Desktop' from Windows to Linux. Remote Desktop is a Windows only protocol.

---

### Post by harisund on 2006-08-09
Windows to Linux --

SSH - On linux install the package openssh-server. 
Then on your Windows machine get yourself a 'ssh client' like putty (search on the net for puty download) and if you want to login to your Linux box you can open putty and connect to 'username@ip_of_linux_box' and you are in the terminal of the Linux machine. 
The advantage is once ssh server is installed, you can even copy files to and fro. Install winscp3 and use it like a graphical file copy program. 

VNC-
In the settings menu of Ubuntu, you will find something called 'remote desktop'. This basically enables a VNC server. Search online for something called VNC client and logon to ip_address_of_ubuntu_box. You wlil see a graphical screen. The only problem with that is the fact that you will have to be logged in already with your machine. There are other work arounds as well. 

NX: For this search around the forums, even by posts made by myself on 'FreeNX.' 

Linux to Windows: 
perhaps the easiest (and as far as I know, only) way to access Windows machine from Linux is to enable Remote login on Windows and use 'tsclient' software on Linux to access Windows.
 
Is your Linux box behind a hardware/software firewall? If so you will have to open port 22 for SSH access and 5900 for VNC access.

---

### Post by turath on 2006-08-09
Hey

Thanks so far for the responses.

The box is inside my office...Tech support guys want to learn linux, and I am showing them the ropes from an Ubuntu Standpoint.

no firewall. ( its all internal testing )

The only thing that we want to really accomplish is loggin in from windows clients remotely.

ssh is already running on the box

Remote Desktop: already discovered that if you don't have a session logged in , you can't use TightVnc .....

They don't want to linux to windows, the only want to 
Windows to linux.

Linux to Windows works like a charm when we log into the 2k Servers.

Tired the putty thing...not sure how to get it to work 
but from the windows side I have x tunneling in the putty options set up.


FreeNx seemed a bit too much to teach these guys to use.

-Thanks

---

### Post by harisund on 2006-08-09
First, I am not sure why FreeNX is hard to use. I could walk you through if you want. It's practically as convenient as you can get.

What tunnel are you creating? You don't need any tunnel at all. could you perhaps the tunnel you are having in mind?

---

### Post by turath on 2006-08-13
Greets

Hey not I could use the walkthrough.

I tried installing it and somehow it failed.

Perhaps I missed something...then again when we have issues
isn't it always something missing.

-Thanks



> **harisund said:**
> First, I am not sure why FreeNX is hard to use. I could walk you through if you want. It's practically as convenient as you can get.

What tunnel are you creating? You don't need any tunnel at all. could you perhaps the tunnel you are having in mind?

---

### Post by turath on 2006-08-19
Howdy

Freenx ...

Free Nx only allows 2 users to log on with the no machine client.

I am trying to set up an office box where all the users can log into X and test and play .

---

### Post by 1oki on 2006-08-22
> **harisund said:**
> Anyway, you can't use 'Remote Desktop' from Windows to Linux. Remote Desktop is a Windows only protocol.

thats true, but there are still ways of using it for remote desktop perposes... As we know you can rdp from linux to windows, but you can also do it from windows to linux... I have done it before (about 8 months ago) but forgot how the heck i did it. You can also look at it like this: If they have the know-how and ability to do it one way that means they have the protcol down and are able to do it the other way. Its all about manipulation. ;) 

I will figure it out, and repost how I got it to work.

---

### Post by 1oki on 2006-08-22
I wanted to delete this message, but I couldnt... So i replaced it with this one...](*,) ](*,) ](*,)

---

### Post by 1oki on 2006-08-22
> **turath said:**
> Greets

Hey not I could use the walkthrough.

I tried installing it and somehow it failed.

Perhaps I missed something...then again when we have issues
isn't it always something missing.

-Thanks

hey turath, try this thread... It looks like a howto for installing FreeNX on Ubuntu. It says its for (k)Ubuntu breezy, but it should be ok. They are all pretty much the same! It is Ubuntu after all! :D 

[http://www.ubuntuforums.org/showthread.php?t=241651&highlight=freeNX+howto](http://www.ubuntuforums.org/showthread.php?t=241651&highlight=freeNX+howto)

L

---

