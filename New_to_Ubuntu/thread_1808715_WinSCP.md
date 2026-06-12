---
title: "WinSCP ?"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by Dead root on 2011-07-20
Hello,

Is there a problem like WinSCP for Ububtu? where I can FTP my server and SSH into it? WinSCP is really easy to use (SFTP and FTP client) but it's for Windows only. Is there a similar program for ubuntu?

Thanks !

---

### Post by skatinjj on 2011-07-20
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html")

Any questions just ask, I'll be around.

Also, google works magic ;)

---

### Post by schnelle02 on 2011-07-20
Filezilla is a good FTP client for ubuntu.  'sudo apt-get install filezilla'

---

### Post by skatinjj on 2011-07-20
> **schnelle02 said:**
> Filezilla is a good FTP client for ubuntu.  'sudo apt-get install filezilla'

I did forget ftp didn't I? XD

---

### Post by Dead root on 2011-07-20
Thanks.

What I mean is that I have a VPS. I want to FTP and SSH into it. WinSCP was a great tool but now I don't want to use Filezilla it's not that great tbh.

Is there a software Where I can log in..and use it as FTP..and when I need I can click on the SSH button? because it'll be easier to see the folders in the FTP..and copy the directories to the SSH..

---

### Post by skatinjj on 2011-07-20
Have you tried winscp under wine?  Suppose to work.

---

### Post by kaldor on 2011-07-20
Maybe Putty?

---

### Post by Dead root on 2011-07-20
Thanks I found SecPanel the best Alternative to WinSCP.

[http://ubuntuguide.net/secpanel-gui-tool-to-manage-ssh-connections](http://ubuntuguide.net/secpanel-gui-tool-to-manage-ssh-connections)

---

### Post by alphacrucis2 on 2011-07-20
> **Dead root said:**
> Thanks.

What I mean is that I have a VPS. I want to FTP and SSH into it. WinSCP was a great tool but now I don't want to use Filezilla it's not that great tbh.

Is there a software Where I can log in..and use it as FTP..and when I need I can click on the SSH button? because it'll be easier to see the folders in the FTP..and copy the directories to the SSH..

Filezilla does sftp. Just tested it myself.

---

### Post by skatinjj on 2011-07-20
But can it also switch to ssh as needed like asked?

---

### Post by alphacrucis2 on 2011-07-20
> **skatinjj said:**
> But can it also switch to ssh as needed like asked?

Yes.

---

### Post by Dead root on 2011-07-20
> **skatinjj said:**
> But can it also switch to ssh as needed like asked?
Yeah that's what I need really.

SecPanel Unfortunately can't edit/rename the files at all :( I just could see the directions and files. I couldn't rename them. This is not fun :P

---

### Post by Dead root on 2011-07-20
> **alphacrucis2 said:**
> Yes.
OK Great thanks. Downloading it now.

Thanks guys for your help. I can't believe I Joined Ubuntu today...I wasted a lot of my time with that Windows thing :P

---

### Post by skatinjj on 2011-07-20
Glad we could help.  I prefer a nice CLI though =)

---

### Post by Dead root on 2011-07-20
> **skatinjj said:**
> Glad we could help.  I prefer a nice CLI though =)
What is a CLI? 

I just tried Filezilla I can't seem to find that SSH in it..Where's that option? :(

---

### Post by skatinjj on 2011-07-20
CLI = command line interface.  No gui required to do ftp, sftp(I believe), or ssh.

---

### Post by alphacrucis2 on 2011-07-20
> **Dead root said:**
> OK Great thanks. Downloading it now.

Thanks guys for your help. I can't believe I Joined Ubuntu today...I wasted a lot of my time with that Windows thing :P


Well I just checked out WinSCP and it is a little more convenient for selecting the protocol. In Filezilla if you use the quick connect method you type 22 in the port field for sftp rather than select from a drop down. The Filezilla site manager does use a dropdown protocol selector though

---

### Post by Dead root on 2011-07-20
> **skatinjj said:**
> CLI = command line interface.  No gui required to do ftp, sftp(I believe), or ssh.
Oh no Please stay away from me :P I am afraid of command line because I always break something unless I copy/paste them from a reliable source.

> **alphacrucis2 said:**
> Well I just checked out WinSCP and it is a little more convenient for selecting the protocol. In Filezilla if you use the quick connect method you type 22 in the port field for sftp rather than select from a drop down. The Filezilla site manager does use a dropdown protocol selector though
Yeah WinSCP is so good. I tried Filezilla and put 22 and I was connected as SFTP but I couldn't find that SSH button where I can SSH into my VPS. :confused:

---

### Post by skatinjj on 2011-07-20
I can't find anything on filezilla using ssh.  

I would just use putty, easy and convenient.

Or, google using winscp under wine so you can use your windows program.

---

### Post by Dead root on 2011-07-20
> **skatinjj said:**
> I can't find anything on filezilla using ssh.  

I would just use putty, easy and convenient.

Or, google using winscp under wine so you can use your windows program.
What is a Wine? I don't want to break my Ubuntu...It's new :P

OK I'll use SSH from my terminal now I need to login twice (waste of time) :P 

In WinSCP you can just login and open the SSH and you are ready. but the terminal in ubuntu is great compared to the windows (from dinosaurs days).

---

### Post by Primefalcon on 2011-07-20
> **skatinjj said:**
> But can it also switch to ssh as needed like asked?
what?? open terminal

ssh -X user@ip

then lauch nautilus via nautilus &

---

### Post by alphacrucis2 on 2011-07-20
> **Dead root said:**
> Oh no Please stay away from me :P I am afraid of command line because I always break something unless I copy/paste them from a reliable source.


Yeah WinSCP is so good. I tried Filezilla and put 22 and I was connected as SFTP but I couldn't find that SSH button where I can SSH into my VPS. :confused:

You mean the button in winscp that opens putty and connects it to the same host that winscp is connected to? If so, then no, filezilla wont do that. You can install putty but you would have to manually connect it. Actually that is a quite convenient feature of winscp.

---

### Post by skatinjj on 2011-07-20
Wine creates an environment in which windows apps can run.

To install wine:

Go to the software center and search wine then click install.

Then get the .exe to install WinSCP and run it.  If all goes well then it will install and be used.

Not all programs work.

---

### Post by schnelle02 on 2011-07-21
A couple more details on wine.  It stands for "Wine Is Not an Emulator", but it provides a file structure similar to windows and allows programs to access extensions as if it were running on windows.  Once wine is installed you can check out your home directory, make hidden files visible in the menu.  Then open the file ".wine" and you will start to recognize things if your a windows user such as program files.  It is great for programs without a ton of overhead.  Go to [www.winehq.org]("http://www.winehq.org") and check out the App database, you will find excellent support and fixes for any errors you might come across.  I didn't check personally, but I believe WinSCP will run just fine on it.

Follow an installation tutorial for it if you think you might break your OS.  But once it is installed and configured, you can download and install windows programs through your browser.  It will simply ask "Install using wine" and you select yes or ok.

---

