---
title: "New VPN Client GUI for GNOME"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by SuperMike on 2007-01-27
I have built a new VPN Client GUI for Gnome and I use this on Ubuntu. Of course you'll have to do a couple minor things (explained in the README.txt), but then it should work for your VPN connections to your office.

The project is called gvpnc and uses the vpnc tool, which you download separately.

Feel free to customize, extend, and do this code better than I have, or port it to an XUL application (the new thing to do on Linux these days).

[COLOR="DarkOrange"]_**[http://code.google.com/p/gvpnc/]("http://code.google.com/p/gvpnc/")**_[/COLOR]

[IMG]http://gvpnc.googlecode.com/files/Screenshot.jpg[/IMG]

---

### Post by malpan on 2007-02-12
Thank you so much! This GUI is very much appreciated.

---

### Post by SuperMike on 2007-02-13
Thank you so much. I hope the Ubuntu or GNOME Team gets a look at this someday and considers including it in with their products. I don't mind if they revamp it entirely -- perhaps they could use it as a starting point. After all, it's written in Python and both the GNOME and Ubuntu teams currently have a sick lovefest with that language. (Me, I pulled my hair out with Python.)

Oh, and by the way, to install vpnc in order to use gvpnc, just do:

# temporarily enable Universe, Backports, and Multiverse option in /etc/apt/sources.list
$ sudo nano /etc/apt/sources.list
$ sudo apt-get update
$ sudo apt-get install vpnc
# disable Universe, Backports, and Multiverse option
$ sudo nano /etc/apt/sources.list
$ sudo apt-get update

---

### Post by colonelk on 2007-02-13
How would you go about connecting to a Microsoft PPTP server which uses RSA SecurID?

---

### Post by SuperMike on 2007-02-13
> **colonelk said:**
> How would you go about connecting to a Microsoft PPTP server which uses RSA SecurID?

Hmmm. Try my tool out and see if it works for you. I have a Cisco VPN router that I connect to and it uses an RSA SecurID as well. Since Microsoft has proven to be nothing more than a glorified copycat with cash reserves, or snatch up the really smart innovators through business acquisitions, perhaps Microsoft based their PPTP on Cisco's technology? 

The real magic, however, is in the 'vpnc' command -- all I did was write the front-end. However, you can see if perhaps there's a switch or something on the vpnc command that might need to be added in order for your connection to work. (For that, you might want to call Ubuntu Support if you don't get an answer here in the forums.) Anyway, if you find you need this extra --switch option, then you could edit my python file for the application in a text editor to add it.

---

### Post by SuperMike on 2007-02-16
> **colonelk said:**
> How would you go about connecting to a Microsoft PPTP server which uses RSA SecurID?

BTW, a devious little patent troll just went after M$ on their VPN product:

[http://news.yahoo.com/s/cmp/20070216/tc_cmp/197006578](http://news.yahoo.com/s/cmp/20070216/tc_cmp/197006578)

As much as I hate M$, I hate patent trolls worse, actually. Praising a patent troll for going after M$ is absolutely the WRONG thing that any of us should do. We should be fighting on both fronts.

Okay, off the soapbox now.

---

### Post by colonelk on 2007-02-16
Thanks for this.  I'll have a play early next week and see if I can get it to work.

---

### Post by SuperMike on 2007-02-18
Note you may encounter a problem when you try to launch the gvpnc tool as a non-root user. This is because it needs to edit a file in the /etc/vpnc folder. To overcome that, I created a Bash script in the gvpnc project that utilizes gksudo so that it runs under the root account through sudo.

If anyone can devise a system to work around that, please let me know and I'll utilize that instead.

---

### Post by hacabrera on 2007-02-21
SuperMike:

May I know under which Ubuntu version did you run it? I have Edgy and It keeps giving me some errors stating that theres is something wrong in /etc/vpnc/gvpnc.conf


vpnc: warning: unknown configuration directive in /etc/vpnc/gvpnc.conf at line 1
VPNC started in background (pid: 18899)...


Thank You!!!!

HACabrera

---

### Post by SuperMike on 2007-02-21
I have it running at home under Breezy, but I don't think that's it. Did you read the readme.txt? Did you load the script with gksudo so it runs under root (unless you can think of a better way)? Do you think perhaps I may have chmodded my /etc/vpnc dir differently than you?

Taking out your user/pass and group/pass info, and any IP addresses and so on, can you reply with your gvpnc.conf for us so that we can see what it looks like and why it might be failing?

Do you have vpnc still running in the background multiple times? If so, you'll want to use 'killall vpnc' to kill it, and run it a few times under root or sudo.

---

### Post by SuperMike on 2007-02-22
Ah, I think I know what the problem is. My gvpnc starts with:

AUTOGENERATED BY gvpnc

instead of:

# AUTOGENERATED BY gvpnc

and that's probably your problem. I bet my version of vpnc accepts this, while yours does not. Here's the fix, for now:

Look for the file in the gvpnc directory called buildrunconf.sh. Edit it and change the line that has AUTOGENERATED BY to look like:

echo -e "# AUTOGENERATED BY gvpnc" >> "/etc/vpnc/gvpnc.conf"

(Note the # symbol was added.)

Then, reboot or use killall to eliminate any chance of a hung vpnc in memory.

Then, reconnect and see if it works. Please reply back so that I can then release a bug fix on code.google.com.

Thanks!

---

### Post by SuperMike on 2007-02-23
> **hacabrera said:**
> vpnc: warning: unknown configuration directive in /etc/vpnc/gvpnc.conf at line 1
VPNC started in background (pid: 18899)...


I released version 1.01 on the code.google.com site with the line 1 bug fix. I think that should handle you okay now.

---

### Post by colonelk on 2007-02-27
Still not getting anywhere with PPTP.  Seems like the config files talk about IPSEC only.

---

### Post by SuperMike on 2007-02-27
> **colonelk said:**
> Still not getting anywhere with PPTP.  Seems like the config files talk about IPSEC only.

Ah, that's unfortunate. Have you tried a 'man vpnc' to see if it offers any features for PPTP instead of IPSEC? If it does, then perhaps you could work those small changes into the Bash and Python scripts with minimal effort.

---

### Post by Mr Potter on 2007-11-06
Hey man, I think your front end looks great :popcorn:, but I'm having some trouble understanding the install notes in the read me.  I've been able to get it extracted to /etc/gvpnc, open the gvpnc Bash script for editing, and honestly that's where I get lost.  Any chance you could post an example of what that file would look like when finished under Ubuntu?  Sorry if you've already posted that somewhere in the thread...it's late, and I'm super tired.  

  I've already got my .conf set up for vpnc (been using vpnc for a bit now and it works great.Would love to use your front end for my standard users, who don't understand the command line).  

Thanks for any help you can give.  

Oh, and have you thought at all about using a custom launcher and adding gvpnc to the /etc/sudoers list?  I played around with kvpnc trying to accomplish this but their directions went off the road about half way through.  Maybe you can make sence of it, take a look at the "Howto setup KVpnc for use without root password" half way down this page [http://home.gna.org/kvpnc/en/documentation.html](http://home.gna.org/kvpnc/en/documentation.html)

Again thanks

---

### Post by SuperMike on 2007-11-09
> **Mr Potter said:**
> Hey man, I think your front end looks great, but I'm having some trouble understanding the install notes in the read me.  I've been able to get it extracted to /etc/gvpnc, open the gvpnc Bash script for editing, and honestly that's where I get lost.  Any chance you could post an example of what that file would look like when finished under Ubuntu? 

I'm at work, but I want to help you. I don't have the gvpnc here right now, so I'll have to look at it from home and tell you what to do. I'll try to contact you here within 24 hours.

---

### Post by SuperMike on 2007-11-09
1. Create a file in /etc/vpnc named gvpnc.conf that looks like:

# AUTOGENERATED BY gvpnc
IPSec gateway [gateway address]
IPSec ID [group id]
IPSec secret [group password]
Xauth username [user id]
Xauth password [leave blank]

Where everything in [] should be provided by your company's VPN administrator. Do not include the brackets, of course.

2. When you run gvpnc, you must set up your launcher icon to run under root. The way I do that is to make it say something like...

/usr/bin/gksudo /home/supermike/apps/gvpnc/gvpnc

...where you use gksudo to point to the path of where you installed the app, and to the executable script name of gvpnc.

3. When you launch the app, it asks for your password and then becomes root. It then runs the app under root credentials.

4. Choose File, Connect to VPN.

5. Because of step # 1, everything should be filled out except your user password. For that, this is usually a company-provided PIN code (or one you setup), and then you follow this with the number on your RSA SecureID. (At least, that's what I do on my office VPN. Your mileage may vary depending on how your VPN Admin has setup your VPN settings.)

6. When you type in the PIN code followed by the password on the "user password" line, and click Connect, it will connect and give you the result back in a white window if it was able to connect properly.

7. Once connected, you can then minimize gvpnc and start your work over VPN like you normally would, such as browse the company websites, or point your mail client at your mail server, or open a Terminal Service connection to a Windows workstation or Server, or whatever you used to do with vpnc.

8. When done, unminimize gvpnc and click the File, Disconnect from VPN menu item. It will disconnect you. If you don't believe it did, try the option again and it will tell you if VPNC is even loaded at this point.

That's it.

---

### Post by marfal on 2008-02-13
Help needed please,

I've been looking for a vpn client to allow me access to my work vpn which uses the RSA SecurID token. Found gvpnc on a google search and it looked very promising from the screen shots. Down loaded the tar.gz file and extracted the file to my desktop (vpnc already installed)
cd'd to that file and tried to install using ./configure but it returned no such file.

I'm affraid my installation skills are very limited outside the package manager.
I did manage to create and edit the gvpnc.conf in /etc/vpnc as instructed on the "READ ME" file but I'm completely lost from there, I don't now how to install the rest of the files.

Help please

Mark

---

### Post by SuperMike on 2008-02-13
Okay, let me take a moment to remember this, and I'll get back to you shortly.

---

### Post by SuperMike on 2008-02-13
About the only thing you're missing now is to create a launcher for this. So let's say your home directory is ~. That's a shortcut way at the Linux command line to get to your home directory. So, without switching to root with sudo or su, you could do this:

$ cd ~

...and you'd be at your home directory's root.

So, in there, I created an apps folder and a gvpnc subfolder. You can do it in Nautilus, or at command line:

$ mkdir apps
$ cd apps
$ mkdir gvpnc

And then you can copy the gvpnc files into there.

Okay, if that's your path for the gvpnc files, then you can right-click your desktop and choose Create Launcher...

Give it a name like VPN2Office or whatever and then make the command set to:

~/apps/gvpnc/gvpnc

...and then an icon and then click OK.

Okay, but you're not finished yet. Now go find ~/apps/gvpnc, and look for a script in there called gvpnc. Edit it with a text editor and make it say:

#!/bin/bash
cd ~/apps/gvpnc
gksudo "/usr/bin/python ~/apps/gvpnc/gvpnc.py"

...save it and then double-click the icon on your desktop. The interface should come up. If it does not, I'll be surprised. If it fails to come up, it's because GTK and Python dependencies are probably not installed on your system, but most Ubuntu systems come with GTK and Python installed properly. However, I use GNOME all the time instead of KDE or other desktop interfaces, so perhaps your desktop is different and I wasn't testing for that.

---

### Post by marfal on 2008-02-13
Many thanks for replying so quickly.

Ok I followed the instruction carefully to create the directories apps then gvpnc and put all the extracted files into it ie the gvpnc.py + various png files.

I can search to the file path ~/apps/gvpnc/gvpnc and it opens the executable file gvpnc in gedit
and contains this entry:
#!/bin/bash
#
#
cd ~/apps/gvpnc
#
gksudo "/usr/bin/python ~/apps/gvpnc/gvpnc.py"

gvpnc.conf is in place ( /etc/vpnc ) and has my details set

I created the launcher with the command ~/apps/gvpnc/gvpnc

but when I double click the launcher icon I get this error message:

Details: Failed to execute child process "~/apps/gvpnc/gvpnc" (No such file or directory)

I'm running stock ubuntu gutsy with gnome, so as you say everything should be loaded by default.

Thank again

Mark





> **SuperMike said:**
> About the only thing you're missing now is to create a launcher for this. So let's say your home directory is ~. That's a shortcut way at the Linux command line to get to your home directory. So, without switching to root with sudo or su, you could do this:

$ cd ~

...and you'd be at your home directory's root.

So, in there, I created an apps folder and a gvpnc subfolder. You can do it in Nautilus, or at command line:

$ mkdir apps
$ cd apps
$ mkdir gvpnc

And then you can copy the gvpnc files into there.

Okay, if that's your path for the gvpnc files, then you can right-click your desktop and choose Create Launcher...

Give it a name like VPN2Office or whatever and then make the command set to:

~/apps/gvpnc/gvpnc

...and then an icon and then click OK.

Okay, but you're not finished yet. Now go find ~/apps/gvpnc, and look for a script in there called gvpnc. Edit it with a text editor and make it say:

#!/bin/bash
cd ~/apps/gvpnc
gksudo "/usr/bin/python ~/apps/gvpnc/gvpnc.py"

...save it and then double-click the icon on your desktop. The interface should come up. If it does not, I'll be surprised. If it fails to come up, it's because GTK and Python dependencies are probably not installed on your system, but most Ubuntu systems come with GTK and Python installed properly. However, I use GNOME all the time instead of KDE or other desktop interfaces, so perhaps your desktop is different and I wasn't testing for that.

---

### Post by SuperMike on 2008-02-14
Try this:

1. Open a terminal prompt.
2. Type:

echo $PWD

3. Write down the result of that and then type 'exit'.
4. Now, everywhere I have told you to use ~, I want you to replace that with the result of what you saw in step # 2. So, if your name is Jack, and your directory is /home/jack, then replace ~ with /home/jack and then follow that with whatever is the rest of the path.
5. Ensure that everything is pathed properly. Don't just give up -- try to get inside the "mind" of the program on what it needs and how it calls stuff. Think it through. And did you know you can launch your program from command line as well and see what the errors are?

---

### Post by marfal on 2008-02-14
Ok I did that and as you suggested put the command into the terminal, getting these results:

mark@joey:~$ /home/mark/apps/gvpnc/gvpnc
/home/mark/apps/gvpnc/gvpnc.py", line 5
SyntaxError: Non-ASCII character '\xc2' in file /home/mark/apps/gvpnc/gvpnc.py on line 5, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details

the gvpnc.py looks like this:

#!/usr/bin/python2.2
#

# gvpnc v. 1.01
# Copyright © 2007, Super Mike  (This is line 5 with the offending character)




Once again thanks for the speedy reply.

Cheers, Mark

---

### Post by marfal on 2008-02-14
Got it, it didn't like the copywrite symbol ©

Deleted it from script at line 5 and 55 then the app poped up! excellent many thanks for your help and patience.

Cheers

Mark

---

### Post by SuperMike on 2008-02-14
Oh Yeah! I forgot!!! I forgot that after a certain version of the app I had to remove that dumb thing because the code would break if I didn't. I'm so glad you reminded me because I couldn't recall.

---

