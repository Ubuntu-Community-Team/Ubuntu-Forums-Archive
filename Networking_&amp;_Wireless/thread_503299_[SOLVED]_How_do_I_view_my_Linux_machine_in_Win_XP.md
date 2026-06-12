---
title: "[SOLVED] How do I view my Linux machine in Win XP?"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by geotev on 2007-07-16
Hello,

I understand to use Samba on my Linux machine to view the rest of my network which are Win XP computers, but how do I view my Linux computer on a Win XP network?

Thank You for the help!

---

### Post by geotev on 2007-07-17
Hello,

I activated Samba and can view all the Windows machines on my network from my Linux computer. In addition to viewing the computers, I can actually go into the Windows file systems and view the files. Installing the Canon Pixma 4000 printer that is attached to one of my XP machines was no problem. I can print documents from my Linux computer on the printer. I am left with the question, how do I view my Linux computer on a XP computer? 

I would appreciate the help. Thank You!

---

### Post by ugm6hr on 2007-07-17
Hopefully this should work:

(Cut from a previous post: [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734))

I then added a shared folder on my laptop:
Applications->System->Shared folders
Shared folders tab:
Added a folder (I trialled my /home/user)
General tab:
Tick the This computer is a WINS server box

I then edited /etc/samba/smb.conf (as root) (in Terminal: gksudo nautilus and browse and double-click file), and added just [COLOR="Red"]one line[/COLOR] immediately below the [global] entry, so this part looked like:
```

#======================= Global Settings =======================

[global]
[COLOR="Red"]security=share[/COLOR]
## Browsing/Identification ###
```

Then make sure you run the home network wizard on the XP box.

---

### Post by geotev on 2007-07-17
Thank You!

---

### Post by jcoles on 2007-07-17
Any tricks for Windows 2000? I tried the configuration you describe, except that I don't know what the "home networking wizard" equivalent is in Win2000.

I can access Windows from Linux with no problem. 

My Linux home shows up in My Network Places, but when I try to open it, I get a message that it is not accessible. Looks like a permissions problem. What permissions do I need? 

As an alternative, I tried security=user. I am prompted for user name and password. Valid credentials are rejected.

Any ideas?

---

### Post by ugm6hr on 2007-07-18
> **jcoles said:**
> Any tricks for Windows 2000? I tried the configuration you describe, except that I don't know what the "home networking wizard" equivalent is in Win2000.

I can access Windows from Linux with no problem. 

My Linux home shows up in My Network Places, but when I try to open it, I get a message that it is not accessible. Looks like a permissions problem. What permissions do I need? 

As an alternative, I tried security=user. I am prompted for user name and password. Valid credentials are rejected.

Any ideas?

If you can see the linux box in my network places from Win2000 - you have already run the wizard (I think).

Did you try restarting after *security=share* edit?

---

### Post by geotev on 2007-08-02
Hello,

I have Samba installed. I can view and access the two XP Home and the one XP Prof machines from my Linux computer. I can view my Linux computer from the XP machine. The problem is that I cannot access it.

When I right-click on My Computer and "Map Network Drive", it lets me select a drive letter, I type in the following information of the Linux computer as: 
\\(the IP address)\MyFiles
Then a dialog box pops up with the title displaying as "Connect to Home.hsd1.va.comcast.net". Also, in the the box it displays "Connecting to (IP address) of the Linux computer and I enter my Linux computer log-on name, which is the same user name on every computer in my network, and password. Then enter.
The same kind of box appears with the same info except a different User name "(Computer Name)\(my network name)". I enter the same password, since I use the same password when logging in to every computer on my network. Then enter.
This dialog box reappears with the same info over and over.

I am almost in, I just need some help to get over this hurdle.

Thank You!!

---

### Post by McTek on 2007-08-02
I  have the same problem, with the exception that windows xp see's my linux mach and then asks for user name and password.  How do i set these up?
BTW I can access the xp mach from linux just fine.

---

### Post by geotev on 2007-08-03
Hello,

I want the Samba server's username and password to be the same as my Linux username and password. How do you do this? I know I need to enter something like:
smbpasswd -a [username]. I went in through the terminal with no success. Obviously, I am doing something wrong.

Samba is installed. I can access the three WinXP machines from my Linux computer, but I cannot access the Linux computer from my XP machines. When I go to Map Network Drive from My Computer, I see an icon for the Samba server and try to select it, then, I keep getting dialog boxes that ask me for my username and password into the Samba server. My Linux username and password, is not getting me in.

Thank You!

---

### Post by geotev on 2007-08-03
Hello,

I think my main problem is the "How To?" part:

Specifically, how do I enter the necessary changes on my Linux computer. Samba was automatically installed and configured by the Ubuntu version. I did not perform a manual install of Samba. Being new to the Linux OS, I need to know how to access and make changes to the Samba server.

The following shows the problem I am having from a previous post with only one response. I am trying to use the suggestion and need help.

I can view and access the two XP Home and the one XP Prof machines from my Linux computer. I can view my Linux computer from the XP machine. The problem is that I cannot access it.

When I right-click on My Computer and "Map Network Drive", it lets me select a drive letter, I type in the following information of the Linux computer as: 
\\(the IP address)\MyFiles
Then a dialog box pops up with the title displaying as "Connect to Home.hsd1.va.comcast.net". Also, in the the box it displays "Connecting to (IP address) of the Linux computer and I enter my Linux computer log-on name, which is the same user name on every computer in my network, and password. Then enter.
The same kind of box appears with the same info except a different User name "(Computer Name)\(my network name)". I enter the same password, since I use the same password when logging in to every computer on my network. Then enter.
This dialog box reappears with the same info over and over.

The assistance is greatly appreciated.
Thank You!

---

### Post by geotev on 2007-08-03
Hello,

What GUI Apps are availble to access the Samba Server?

This may be a tool for me to access the Samba server and make suggested changes.

Thank You!

---

### Post by geotev on 2007-08-06
Hello,

I am struggling with making changes to the Samba config file. 

1) When I open it with the editor, it shows "Read Only". From the feedback I have received showing what changes to make my Samba server username and password the same as my Log-in username and password, you have to change the SMB.CONF file. 

2) I cannot locate where to make the changes in the SMB.CONF file.

3) Of all the Samba GUI programs available, which ones actually help newbies like me?

Some background info, Samba is installed. I can access the three WinXP machines from my Linux computer, but I cannot access the Linux computer from my XP machines. In XP, when I go to Map Network Drive from My Computer, I see an icon for the Samba server and try to select it, then, I keep getting dialog boxes that ask me for my username and password into the Samba server. My Linux username and password, is not getting me in. 

Somehow I think having root privileges and accessing the root is key, but I do not know how to do this. 

Thoroughly confused and frustrated, please help.

Thank You!

---

### Post by geotev on 2007-08-06
Hello,

I am struggling with making changes to the Samba config file. 

1) When I open it with the editor, it shows "Read Only". From the feedback I have received showing what changes to make my Samba server username and password the same as my Log-in username and password, you have to change the SMB.CONF file. 

2) I cannot locate where to make the changes in the SMB.CONF file.

3) Of all the Samba GUI programs available, which ones actually help newbies like me?

Some background info, Samba is installed. I can access the three WinXP machines from my Linux computer, but I cannot access the Linux computer from my XP machines. In XP, when I go to Map Network Drive from My Computer, I see an icon for the Samba server and try to select it, then, I keep getting dialog boxes that ask me for my username and password into the Samba server. My Linux username and password, is not getting me in. 

Somehow I think having root privileges and accessing the root is key, but I do not know how to do this. 

Thoroughly confused and frustrated, please help.

Thank You!

---

### Post by fpurdue on 2007-08-06
1)  preface any command that you want to run as 'root' with 'sudo'.  For example to edit your smb.conf file you would use "sudo gedit smb.conf" (or whatever editor you prefer)

2) Look towards the bottom of the file - that's where most of the good stuff is

3) Are you looking for a gui to browse & mount samba shares or a gui to let you edit the configuration?

As far as the issue you are having - you need to a) make sure you are sharing out the directory you are looking to access and b) make sure you are providing a username and password that samba recognizes (look at "man smbpasswd")

---

### Post by geotev on 2007-08-06
Hello,

Some additional info, Samba was installed through the Ubuntu install. I have printer support, which is located on one of the XP computers. I can access the files on the XP machines. I do not use WINS, therefore, I have no need for Netbios. On every XP computer, I can see my Linux computer. 

It seems that the majority of suggestions and "How-to's" give examples of using WINS. Since I am not having trouble viewing computers, I just want to know how to access my Linux computer from these XP computers.

Thank You!
geotev

---

### Post by geotev on 2007-08-06
Hello,

Some additional info, Samba was installed through the Ubuntu install. I have printer support, which is located on one of the XP computers. I can access the files on the XP machines. I do not use WINS, therefore, I have no need for Netbios. On every XP computer, I can see my Linux computer. 

It seems that the majority of suggestions and "How-to's" give examples of using WINS. Since I am not having trouble viewing computers, I just want to know how to access my Linux computer from these XP computers.

Thank You!
geotev

---

### Post by jnorthr on 2007-08-06
Use the command line to edit your file. To make changes to some files you need to be 'root' AKA God. You can pretend to be god by using the 'sudo' command for any other command. So to edit your xxx.conf file (once you find it) you can CD into the directory containing the file then : sudo gedit xxx.conf    (for ubuntu) or sudo kate xxx.conf for kubuntu. That should then allow your edit session to avoid the 'read-only' feature. Then when you make changes you can save succesfully. Suggest making  a backup copy of any .conf file BEFORE you change it - just in case. Sorry i'm no samba expert yet so cannot help you there. Good luck. :cool:

---

### Post by Nekiruhs on 2007-08-06
> **jnorthr said:**
> UTo make changes to some files you need to be 'root' AKA God. You can pretend to be god by using the 'sudo' command for any other command.
XD, I never thought of it that way! What does that make sudo -i then? Logging in as god?

---

### Post by bmeyer on 2007-08-06
To open smb.conf with root permissions, use:
```
sudo gedit [path]/smb.conf
```
It will prompt for your password.

In smb.conf, look for the following lines:
```
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
security = user
```

Change "security = user" to "security = share".  I had the same issues as you a few weeks ago and that completely solved the problem.

Good luck!

---

### Post by aysiu on 2007-08-06
Text editor: ```
sudo nano -B /etc/samba/smb.conf
``` Ubuntu graphical: ```
gksudo gedit /etc/samba/smb.conf
``` Kubuntu graphical: ```
kdesu kate /etc/samba/smb.conf
``` Xubuntu graphical: ```
gksudo mousepad /etc/samba/smb.conf
``` Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by aysiu on 2007-08-06
Watch this video:
[How-to: File sharing with Ubuntu using Samba](http://www.youtube.com/watch?v=Ad17kma8rNM)

It shows you every step.

**P.S.** You had about six threads all on the same topic: how to set up Samba so that Windows can see Linux. I've merged them all to one thread to allow people to more  efficiently help you, and for you to better keep track of the help you're getting.

---

### Post by geotev on 2007-08-06
Hello,

1) I am interested  to know if there is a GUI program that will let me access and configure the server and the client.

2) I went into the Terminal and entered sudo gedit smb.conf and it opened up the editor withe the filename with no information. Then I opened up the file fin the etc folder and for the first time, I did not see the read-only  before the filename.

I hope I entered the sudo ... in the right place. AS you can see, I am new, but eager to learn.

Thank You!
geotev

---

### Post by geotev on 2007-08-06
Hello,

Thanks to all for the feedback as I learn. I will put it to use.

geotev

---

### Post by aysiu on 2007-08-06
Please watch that video I linked to earlier. It will help you.

---

### Post by geotev on 2007-08-06
To all who replied,

The "You Tube" video link that Aysiu provided us, is very good, and it is easy to understand. Now , the code info I have been reading thoughout the replies to this thread and the other threads  makes sense.

I appreciate the replies.

Again, thanks to all for the feedback,
Geotev

---

### Post by aysiu on 2007-08-06
> **geotev said:**
> To all who replied,

The "You Tube" video link that Aysiu provided us, is very good, and it is easy to understand. Now , the code info I have been reading thoughout the replies to this thread and the other threads  makes sense.

I appreciate the replies.

Again, thanks to all for the feedback,
Geotev
Please let us know if you still run into problems after following the video instructions.

If you get any error messages, for example, post them back here.

If it all went without a hitch, post that as well.

---

### Post by geotev on 2007-08-06
To all,

I can finally see and access my Linux computer on my XP computer.  

I am a happy camper. I could not have done it without the expert help that, finally, put all the pieces together for me.

I think my comfort zone with Microsoft's obsession with windows and reliance on GUI apps,  clouded my understanding of the assistance that was initially, being provided to me. As you already know, MS does not encourage command-line usage and use of the text editor.

I know that those of you who are comfortable with Linux know what I learned throughout this process. I am amazed at how the Terminal editor and the system editor are linked together. I am even more eager to learn the Linux OS and make my contributions to its further development.

I know I can be of assistance to others when faced with the same problem.

Again, many thanks,
Geotev

---

### Post by aysiu on 2007-08-06
Actually, the fact that you have to resort to a tutorial on sharing folders indicates a deficiency in the interface, but it's a good thing you got it sorted and that great video tutorials exist.

---

