---
title: "ubuntu and windows"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by ubdai on 2007-06-10
Presently running ubuntu on my laptop and desktop. My son runs microsoft w2k.
Is there a way i can see all the directories on his machine just to check he is not visiting sites not appropriate for his age. (Pls don't give me any stuff on privacy and civil liberties, when he's 18 he can do what he wants).

He likes watching Divx online and also chatting. Used to run a net nanny, but it was more hassle than it was worth.

Anyways thanks for any advice.

ubdai.

---

### Post by lavinog on 2007-06-10
is your son using a separate computer or are we talking about a dual boot machine?
if it is dual boot you can just mount the win partion in linux and have full access.
if it is a separate computer then you have a couple of options.

do you have a computer that you leave on at all times? if so you can have your sons computer send the info you want to it (chat logs, file listings...etc) then you can check the files without him even knowing.
the simplest way of doing this is write a command shell script for his machine to do a dir listing to a text file, compress it (you can use 7zip for command line compression), then you can have it map the network drive and copy the file (although robocopy can transfer without mapping.)
the trick is to get the script to execute when the computer started...there are abunch of ways to do this. generally you want have it do this when he starts his computer because he would not notice any extra activity at this point, but if you want you could set the script to run every hour or so with task scheduler...another sneeky way would be to attach the script to the shortcuts for his games or whatever program he uses so that when he launches his game he would just think the hard drive activity is just his game loading.



another option is to share his entire drive, but he could notice that and disable it.

the script method worked for my mom to catch my little brother up to no good.

something else you should look into: many routers have the ability to log what websites he goes to and how frequently. They also give you the ability to block those websites or any sites containing certain keywords.

---

### Post by ubdai on 2007-06-11
He's got a single boot to w2k machine. I think the easiest would be to enable to entire drive to be shared.
He's not quite that au fait with the inner workings of the pc.

I know how to share a drive on windows, but no too sure how to get it visable on my ubuntu pc.

So thats the info I require.

Thanks
ubdai

---

### Post by ohbeehaaaave on 2007-06-13
I've got shared folders on an XP that I have no problem seeing on my ubuntu 7.04 machine.  It just worked without doing anything special.

In a related vein, this suddenly stopped working a couple days ago and I traced it to Samba update I'd downloaded.

---

### Post by lavinog on 2007-07-04
> **ubdai said:**
> He's got a single boot to w2k machine. I think the easiest would be to enable to entire drive to be shared.
He's not quite that au fait with the inner workings of the pc.

I know how to share a drive on windows, but no too sure how to get it visable on my ubuntu pc.

So thats the info I require.

Thanks
ubdai

Sorry my reply is so late...been busy with alot of stuff.

edit the file: /etc/samba/smb.conf
and check what your workgroup is set to.
it should be the same as the workgroup for your sons computer

if everything is good you should be able to connect to your sons computer with the nautilus by typing smb://[your sons computer name]

if that doesn't work go to the terminal and type:
```
smbclient \\\\[your sons computers name]
```
it will ask for a password
if the shared folder is not password protected just press enter.
if it connects then you should be able access his drive like a ftp server.

---

