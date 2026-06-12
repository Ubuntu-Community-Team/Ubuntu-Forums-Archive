---
title: "SecureCRT for Ubuntu"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Caleb.Robertson on 2009-05-02
For work I use SecureCRT a lot, and I wanted to know if anyone knew of any program that would provide the same function?

---

### Post by nhasian on 2009-05-02
isnt that just like using ssh?  open a terminal and type:

```
ssh yourusername@yourserver
```

then enter your password and you should be in.

---

### Post by Caleb.Robertson on 2009-05-02
Well I use it to get in to routers and swtichs, so I don't think that will works. The nice thing about it is that it saves all my connections so I don't have to sit there and figure out which one is which.

---

### Post by Caleb.Robertson on 2009-05-03
I found this which is another one of the programs we use at work, I just prefer secureCRT but I ran the .deb installer from here [http://people.defora.org/~khorben/projects/gputty/]("http://people.defora.org/%7Ekhorben/projects/gputty/") 
Caleb

---

### Post by nhasian on 2009-05-03
correct me if i'm wrong but, routers and switches dont user secureshell, they use plain old telnet.  from a terminal you would just type telnet then the hostname.  it will prompt you for the userID and password to continue.  there are plenty of front end GUIs to help manage your list of ssh and telnet hosts :) try going to applications->add/remove programs.  Have it show All Available Applications and search for either telnet or ssh

---

### Post by nandemonai on 2009-05-03
You're talking about ssh access in essence. Shouldn't need an external program to do that. Provided the routers / switches support ssh then it will work fine, otherwise use telnet.

If you have issues remembering what is what then just make shortcuts to the ssh/telnet command.

Manually installing .deb files can be tricky sometimes as they wont necessarily add menu items etc. You should be able to invoke the program from terminal with its name.

---

### Post by ptviperz on 2009-05-03
> **Caleb.Robertson said:**
> For work I use SecureCRT a lot, and I wanted to know if anyone knew of any program that would provide the same function?

I'm the same way as you and I've found no better solution than Virtualbox and seamless windows. 

Nothing in linux comes close to SecureCRT

---

### Post by Caleb.Robertson on 2009-05-03
> **nhasian said:**
> correct me if i'm wrong but, routers and switches dont user secureshell, they use plain old telnet.  from a terminal you would just type telnet then the hostname.  it will prompt you for the userID and password to continue.  there are plenty of front end GUIs to help manage your list of ssh and telnet hosts :) try going to applications->add/remove programs.  Have it show All Available Applications and search for either telnet or ssh

Yes this is true most use telnet, but some use ssh 

> **nandemonai said:**
> You're talking about ssh access in essence. Shouldn't need an external program to do that. Provided the routers / switches support ssh then it will work fine, otherwise use telnet.

If you have issues remembering what is what then just make shortcuts to the ssh/telnet command.

Manually installing .deb files can be tricky sometimes as they wont necessarily add menu items etc. You should be able to invoke the program from terminal with its name.

Yeah how do I add the shortcuts... and no the .deb fine did not add it self to the menu items I had to add it in. 

> **ptviperz said:**
> I'm the same way as you and I've found no better solution than Virtualbox and seamless windows. 

Nothing in linux comes close to SecureCRT

I hear on that, but adapt and overcome...

---

### Post by gradysghost on 2009-05-03
> **Caleb.Robertson said:**
> 
Yeah how do I add the shortcuts... and no the .deb fine did not add it self to the menu items I had to add it in. 

Right-click on open desktop space or open panel space and click Create Launcher.  You can title them whatever you like (i.e. the names of the switches/hubs/whatever that you're connecting to), but set the command attribute to:

```
gnome-terminal -x <command>
```

Where <command> is something like

```
ssh hostname
```

All in all, it should read:

```
gnome-terminal -x ssh hostname
```

The -x flag is an abbreviation for eXecute, and will cause the terminal emulator to open and immediately execute whatever command follows it.

I assume that you have tons of these things to connect to.  The shortcuts can be easily organized with the use of panel drawers.

Right-click open space on a panel, click Add to Panel, and then choose the Drawer applet.  When you click and drag a launcher to the drawer, it will open for you to drop it inside in whatever order you like.  Nothing is preventing you from recursively planting drawers, or putting multiple drawers up all over the place.  This is a decent method of organizing them without having to get a separate piece of software involved.  It's all integrated into your desktop.

Hope this helps.

---

### Post by Parama on 2009-05-07
I stumbled upon Gnome-RDP which handles/remembers settings for all my SSH, RDP and VNC sessions. Very handy in the day to day work. Starting it minimized next next the date/time makes all my sessions just a right click away.

---

### Post by alphacrucis2 on 2009-05-07
> **nhasian said:**
> correct me if i'm wrong but, routers and switches dont user secureshell, they use plain old telnet.  from a terminal you would just type telnet then the hostname.  it will prompt you for the userID and password to continue.  there are plenty of front end GUIs to help manage your list of ssh and telnet hosts :) try going to applications->add/remove programs.  Have it show All Available Applications and search for either telnet or ssh

In the case of cisco routers they do support SSH provided they are running an IOS version that supports it. I think it is more or less standard with the newer models. As far as programs go for telnet, ssh or even serial I use putty on windows and gputty on Linux, as it is what I am used to. I like the fact that you highlight any text in the window and it is automatically copied. Then right click to paste. It also allows you to save a profile for each different host you connect to.

---

### Post by alphacrucis2 on 2009-05-07
I just looked at the secureCRt site. It appears they do have a version for Redhat so it shouldn't be hard to get it working on Ubuntu. It is commercial software BTW not open source.

---

### Post by glotz on 2009-05-07
SecureCRTs are so 1990s, the cool kids nowadays use SecureTFTs! ;)

---

### Post by alphacrucis2 on 2009-05-07
> **glotz said:**
> SecureCRTs are so 1990s, the cool kids nowadays use SecureTFTs! ;)

:lol::lol:

Actually I hadn't realised before that putty is in the repos. Just installed it. Better than using gputty which is based on an older version.

---

### Post by zivley on 2009-09-22
I have two answers for you
One is taking a look at [SecPanel]("http://secpanel.net/")

The other option is something I wrote, if you already have SecureCRT on a windoz box and you can copy your saved sessions files (.ini files) then you can use this script in order to quickly connect using your saved sessions, the only caveats are I don't kn ow how to use the saved passwords so you need to type them, which I think it's more secure anyway, or you could use rsa keys, which is even better.
Here's my script, to make it easier to use, you could just put it in your nautilus scripts folder and then you can just right click the .ini session file and run the script from there, in order to do this follow this steps:
Open a terminal and type
```
gedit ~/.gnome2/nautilus-scripts/SecureCRT-Connect
```
Paste this text:
```

#!/bin/bash

# Script to SSH/Telnet connect to devices using saved SecureCRT .ini session files
# Written by Ziv Leyes, aka "TuxSax"

file="$@"

# Function to use in error checking:
function die () {
  echo "$file"
  exit 1
  # it's better to exit with an error code other than zero,
  # this way, external programs can know whether this succeeded
  # or not :)
}

# Error checking, missing user input:
if [ $# = 0 ]; then 
	echo "You didn't specify any arguments."
	echo "Usage 'SecureCRT-Connect' '/path/to/filename.ini'"
	die 
fi

# Define the protocol (SSH1, SSH2, Telnet), host (IP), username and TCP Port:

proto=`grep -i protocol "$file" | grep -iv transfer | awk -F = '{print $2}' | tr '[A-Z]' '[a-z]' | tr -d '\r'`
host=`grep -i hostname "$file" | awk -F = '{print $2}' | tr '[A-Z]' '[a-z]' | tr -d '\r'`
user=`grep -i username "$file" | awk -F = '{print $2}' | tr '[A-Z]' '[a-z]' | tr -d '\r'`

# Declare strings for comparision:
S1="ssh1"
S2="ssh2"
S3="telnet"

# The port is in HEX so we convert the letters to uppercase and then convert it to decimal
if [ $proto = $S1 ]; then 
	port=`grep  "\[SSH1\]\ Port" "$file" | awk -F = '{print $2}' | tr -d '\r' | tr -s '[:lower:]' '[:upper:]'` 
elif [ $proto = $S2 ]; then
	port=`grep  "\[SSH2\]\ Port" "$file" | awk -F = '{print $2}' | tr -d '\r' | tr -s '[:lower:]' '[:upper:]'` 
elif [ $proto = $S3 ]; then
	port=`grep -i port "$file" | egrep -iv "server|printer|forward" | awk -F = '{print $2}' | tr -d '\r' | tr -s '[:lower:]' '[:upper:]'` 
fi
port=$(echo "obase=10;ibase=16;$port" | bc );

# Define the command to be used according to the protocol and port:
if [ $proto = $S1 ]; then 
	cmd="ssh -1 -p $port -l $user $host"
elif [ $proto = $S2 ]; then
	cmd="ssh -p $port -l $user $host"
elif [ $proto = $S3 ]; then
	cmd="telnet $host $port"
fi

# Execute the command itself on a terminal
gnome-terminal --tab --title="$user@$host" -e "$cmd"

```
Save and exit, then make it executable
```
chmod +x ~/.gnome2/nautilus-scripts/SecureCRT-Connect
```

That's it, now you can right-click any saved session .ini file and from the "scripts" menu chose the SecureCRT-Connect and it will launch a terminal that connects to the desired device.

---

### Post by boosis on 2009-10-23
Hiya,

Also I managed to run SecureCRT 6.2.3 on ubuntu 9.10 using wine.

---

### Post by yknivag on 2009-10-23
```
sudo apt-get install putty
```will give you the ability to save sessions and connect through a variety of different protocols. It also provides a useful graphical frontend for creating ssh tunnels too.

---

### Post by zivley on 2009-10-24
I've also managed to run SecureCRT on linux with wine but is not too seamless and it has some issues related to graphics, also if you, like me, use a lot the scripts inside SecureCRT then you'll find that you need a few tweaks on wine in order to support the Visual Basic Scripting language, I used the [winetricks]("http://wiki.winehq.org/winetricks") script to make it happen.

Last time I used PuTTY it didn't have that option.
Also, I did this for myself because I moved to linux after a while working with SecureCRT on windows, and I had a lot of sessions saved, starting to set all of them in PuTTY from scratch was something I didn't really want. Then I thought about sharing this with the community for all to use if needed.

BUT, guess what, as I type this lines an idea popped up, why not make a script that will "import" those SecureCRT .ini saved sessions files into PuTTY? All I need is to make sure the PuTTY "sessions" files are also text files that can be wrote with settings I need.
Anyone wants to help me out here?
I'll try to start working on it, but I'll appreciate any help!

---

### Post by kuthulu on 2010-02-23
try this.. [http://kuthulu.com/gcm](http://kuthulu.com/gcm)

it's a ssh/telnet session manager with autologin

it's like "putty connection manager" on windows

---

### Post by mattylee on 2013-02-05
I used to use SecureCRT, and missed it in linux, until I found the ssh config file.
I just added the following to my ~/.ssh/config 

Host serv1
 HostName 192.168.1.1
 User matty

Host serv2
 HostName 192.168.1.2
 User matty

etc...

Now I just type:

ssh serv1
ssh serv2 etc...

Much better and faster than SecureCRT. 
IMO

---

### Post by wildmanne39 on 2013-02-05
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

