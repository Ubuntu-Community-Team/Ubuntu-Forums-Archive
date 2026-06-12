---
title: "7 curious questions"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Qualia on 2010-01-06
I haven't instlled Ubuntu 9.10 yet, I'm still running it off the Live CD, but I have a few questions:

1. I have a programming class using a program called "QBasic", which is Window only, and is a variant of the BASIC programming language. I need to be able to code and run my qbasic programs from my computer, which will soon be using Ubuntu. Is there any program that can replace "qbasic" in the task of programing in BASIC?

2. Can DOSbox run in Ubuntu?

3. What type of file in Ubuntu is an executable (like how in Windose, .exe is an excutable. What kind of file extenstion is used for a executable in Ubuntu?)

4. Can AIM work? If not, an appplication that I can talk to my AIM Buddies?

5. DVD player? I haven't seen one anywhere on the live CD...

6. can i open zip files?

7. Anyway that I can talk to others on my own home network? Is there an application for this? (kinda like the net send command in Windows!)

That's all, I especialy want to know 1, 4, and 7 :)

---

### Post by lisati on 2010-01-06
> **Qualia said:**
> I haven't instlled Ubuntu 9.10 yet, I'm still running it off the Live CD, but I have a few questions:

1. I have a programming class using a program called "QBasic", which is Window only, and is a variant of the BASIC programming language. I need to be able to code and run my qbasic programs from my computer, which will soon be using Ubuntu. Is there any program that can replace "qbasic" in the task of programing in BASIC?
There's "Freebasic". It's a different dialect of BASIC that comes in DOS, Windows and Linux versions. See [http://www.freebasic.net/](http://www.freebasic.net/)

> 
2. Can DOSbox run in Ubuntu?

Short answer: yes
> 
3. What type of file in Ubuntu is an executable (like how in Windose, .exe is an excutable. What kind of file extenstion is used for a executable in Ubuntu?)

Ubuntu doesn't use the extension to indicate the file type, it uses file attributes.
> 
4. Can AIM work? If not, an appplication that I can talk to my AIM Buddies?

Yes. Check out the program "Pidgin"
> 
5. DVD player? I haven't seen one anywhere on the live CD...

Have a look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
> 
6. can i open zip files?

Short answer: yes. 
Longer answer: from the desktop or file browser, double-click on the file. From the commandline, use the "unzip" command.
> 
7. Anyway that I can talk to others on my own home network? Is there an application for this? (kinda like the net send command in Windows!)

Hmmmm.... are you thinking file sharing or are you thinking in terms of a chat program?
> 
That's all, I especialy want to know 1, 4, and 7 :)

Good luck!

---

### Post by juancarlospaco on 2010-01-06
1-Gambas2
2-Yes
3-Any, Executable is a property of the file on Ubuntu, file extension doest care at all
4-Empathy, Emesene, aMSN, Pidgin
5-VLC, SMPlayer
6-Yes, Right click
7-Empathy, enable "People Nearby" account, and you can talk to other Ubuntu, to File Sharing, install Giver

---

### Post by Sef on 2010-01-07
> 4-Empathy, Emesene, aMSN, Pidgin

Only Empathy and Pidgin are correct.  The other two are just msn clones.  The OP asked about AIM.

---

### Post by juancarlospaco on 2010-01-07
*oh, you are correct, sorry Sef* :)

Empathy, Pidgin--->Multi-Protocol
Emesene, aMSN--->MSN speciallyzed

---

### Post by marshmallow1304 on 2010-01-07
> **Qualia said:**
> 7. Anyway that I can talk to others on my own home network? Is there an application for this? (kinda like the net send command in Windows!)

smbclient
[QUOTE=man smbclient]       -M NetBIOS name
           This options allows you to send messages, using the "WinPopup"
           protocol, to another computer. Once a connection is established you
           then type your message, pressing ^D (control-D) to end.

           If the receiving computer is running WinPopup the user will receive
           the message and probably a beep. If they are not running WinPopup
           the message will be lost, and no error message will occur.

           The message is also automatically truncated if the message is over
           1600 bytes, as this is the limit of the protocol.

           One useful trick is to pipe the message through smbclient. For
           example: smbclient -M FRED < mymessage.txt will send the message in
           the file mymessage.txt to the machine FRED.

           You may also find the -U and -I options useful, as they allow you
           to control the FROM and TO parts of the message.

           See the message command parameter in the smb.conf(5) for a
           description of how to handle incoming WinPopup messages in Samba.

           Note: Copy WinPopup into the startup group on your WfWg PCs if you
           want them to always be able to receive messages.[/QUOTE]

For sending files over the LAN, see [Giver]("apt://giver").

---

### Post by rCXer on 2010-01-07
1. Qbasic can run in dosbox as described [here](http://ubuntuforums.org/showpost.php?p=5340752&postcount=3).  If you want FreeBASIC you can get it from [here](http://old.getdeb.net/app/FreeBASIC+Compiler).

---

### Post by Qualia on 2010-01-17
Cool! Thanks! :)

---

