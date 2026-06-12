---
title: "Startup Questions"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Brad_J on 2011-06-16
Hi. I'm currently running ubuntu 10.04 on my Laptop and I have a couple questions that may or may not have simple answers, but that's what the beginner forum is for right? I would like to make it so that a couple things (Dropbox permissions, Path variables, wifi) are changed or enabled at boot. The problem is that whenever I search the solution I just find people saying that I need to change my .bash_profile in the home directory to initialize these things, but the only file with that name I can find upon running ls -al is full of garbage and doesn't execute anything that I put in it. I guess my question would be how do I run Dropbox as a super user, enable wifi, and add ~/../bin (I think) to my Path variables on boot?
 
-Brad

---

### Post by sanderd17 on 2011-06-16
there are two files (if they don't exist, you need to create them). The .bashrc file in your home directory and the .profile file. The .bashrc file is executed when you start a terminal (so not when you log in) and the .profile file is executed when you log in.

You must be sure to make the files executable (right click -> properties -> rights -> allow execution).

I hope this helps.

---

### Post by Brad_J on 2011-06-16
Cool, I did see a couple sites mention .profile rather than .bash_profile but the vast majority of them mentioned .bash_profile, so I assumed that was the default for ubuntu as well. Do all versions of ubuntu use .profile instead? Just curious.
 
Also, I didn't really ask, but is there a script that will automatically connect to a specified network if it's available? When I start ubuntu it enables wifi automatically but I have to go click on the network I want to join in order to join it. I want to automate it purely out of laziness. Thanks.

---

### Post by yetiman64 on 2011-06-16
You can also look into using /etc/rc.local to run commands or apps at start, but be aware it runs with root privileges (be very careful as to what you launch as root).

In the code box below is an example of how I bring up multiple ethernet cards (bridge them). I then have the bridge brought online with dhcp in /etc/network/interfaces. rc.local also runs a script in my home folder to do bind mounting in a 32 bit chroot (system folders required by my chroot setup).

Just note all my examples need to be run with root privileges so are ok to do from rc.local. Your path variables would likely best be done in .profile.

**Dropbox is a network program and is probably not advisable to run as root**. I have it here and it puts its entry in startup applications (System > Preferences > Startup Applications). See screenshot.

```
# By default this script does nothing.

## Start of networking.
# Bring the network interfaces down.
ifconfig eth0 down
ifconfig eth1 down
ifconfig eth2 down

# Add a network bridge & add the interfaces to it.
brctl addbr br0
brctl addif br0 eth0 eth1 eth2

# Configure the network interfaces.
ifconfig br0 up
ifconfig eth0 up
ifconfig eth1 up
ifconfig eth2 up

# Bridge is defined and brought online with dhcp in /etc/network/interfaces.
## End of networking

# Chroot "special" folder binding.
/home/*****/bin/chroot/Various-fixes-Sup &

exit 0
```**Edit**: This is not for your wifi network question OP just an example of rc.local in use. And a note to any one else reading this with multiple ethernet cards, I don't think this will work with network manager, I use wicd for network connections and can connect my install to the bridge directly.

---

### Post by Brad_J on 2011-06-16
Thanks for your help yetiman. Is the only difference between ~/.profile and /etc/rc.local that one of them runs as root and one doesn't? Out of curiosity is it possible to run commands in .profile with sudo?
> **yetiman64 said:**
> **Dropbox is a network program and is probably not advisable to run as root**.
 I realize that it might not seem like a good idea, but, I have had problems with dropbox not having the correct permissions to copy some things over and I've been missing files from other locations because of it. I looked this up and it is apparently a common problem on ubuntu, I just want to skip the hassle of stopping dropbox and restarting it as root.

---

### Post by yetiman64 on 2011-06-16
> **Brad_J said:**
> Thanks for your help yetiman. Is the only difference between ~/.profile and /etc/rc.local that one of them runs as root and one doesn't? Out of curiosity is it possible to run commands in .profile with sudo?

.profile is used to issue system related commands that are to be applied to your user profile each time it is used. An example of that is the export command. I use that here to add _sub-folders_ of ~/bin (~ = my home folder) to the system path. I use sub-folders in ~/bin as my collection of scripts is quite large. 
eg. The top part of this will be similar in your .profile (I have switched the order of $PATH and $HOME/bin), while the bottom 2 lines are my additions (I have 5 sub-folders all up but only show 2 here as an example)

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$PATH:$HOME/bin"          
fi

export PATH=$PATH:$HOME/bin/chroot
export PATH=$PATH:$HOME/bin/MyScripts              

```Any other non-system related command or program I need to run as user has an entry inserted into System > Preferences > Startup Applications. Screenshot of 2 examples.

Yes, anything needing root privileges to be run automatically can be done from /etc/rc.local. I can't see sudo with a command working from .profile as your password needs to put in for the command to work.


 > **Brad_J said:**
> I realize that it might not seem like a good idea,** but, I have had problems with dropbox not having the correct permissions to copy some things over and I've been missing files from other locations because of it.** I looked this up and it is apparently a common problem on ubuntu, I just want to skip the hassle of stopping dropbox and restarting it as root. 

The bolded part I don't understand, can you explain in more detail as to the problem you're having there please. I am not at all comfortable in advising anyone to run a port opening network related program as root. If a security issue were to occur with dropbox your whole install would be opened up to attack with dropbox run as root, unnecessary escalation of privileges is not a good idea (there may be a better way to fix dropbox than just running it as root).
Could you include some links to information you have found with regard to your problem so we can see the situation more fully? Thanks.

Dropbox copies files to the storage server and synchronizes the folders across all 6 of my linux installs here  (see the -heavily censored- :smile: screenshot) without the need for me to run it as root. A fuller explanation of your problem with dropbox is needed for us to help.

Regards, 
yetiman64

---

### Post by Brad_J on 2011-06-17
**[This]("http://forums.dropbox.com/topic.php?id=22343")** is explaining the exact problem that I've had with dropbox, if there is some other way that you can suggest to fix this I would be grateful. Thanks for the other info too, I've still got a lot to learn about linux.

---

### Post by yetiman64 on 2011-06-17
From the first reply in the link,

> However, it also seems like you've added a symlink inside your Dropbox folder, which is pointing to a folder owned by root.Are you trying to share files of folders owned by root or linking to files or folders owned by root in your dropbox folder? Check the ownership and permissions (mainly ownership) of what you are trying to share.

If you need to do so, then make a copy of the content into a folder you own (can be the dropbox folder) and change ownership/permissions of the file/folder to yourself (if needed) with either the chown (change ownership) or chmod (change mode ie. permissions) commands. Just making a copy of a root owned file into your dropbox folder should change ownership to you (pays to check that, I'm not entirely sure it always works). Then ensure permissions are not too tight (755 and in your ownership should cause no problems for dropbox)

Mainly check the ownership issue and remember anything outside of your home folder is owned by root. Examine carefully what you are trying to share rather than running a network accessing program as root (my current avatar adequately displays how I react to that idea :lol:)

Use,
```
man chown
```and
```
man chmod
```to find usage examples of the 2 commands, feel free to ask further questions about permissions and ownership. Once you come to terms with them you will become aware that they play a large part of the security offered by Linux (think of effectively no viruses and malware on Linux when everything is run with correct privileges). 

The "sudo dropbox" idea suggested in your link may be convenient for some, but it is ultimately very dangerous to your installation and data should a vulnerability in the dropbox software become known to anyone with malicious intent (I'm not actually aware of any vulnerabilities specific to dropbox but the network daemon is closed source - something for you to think about).

---

### Post by Brad_J on 2011-06-18
> **yetiman64 said:**
> 
Mainly check the ownership issue and remember anything outside of your home folder is owned by root.

Does this mean that using chmod 000 for anything outside of the home folder will restrict even root from accessing it? Also, could you explain symlinking? I don't really understand how I could've done that as the things that are having restricted access came from windows in the first place.

---

### Post by nitstorm on 2011-06-18
Symlinks are short for Symbolic Links (Shortcuts ideally speaking).

And chmod 000 means restrict read, write and execute access to the owner of the file, the group and other users.

For more on chmod permissions, look at [this link here]("http://catcode.com/teachmod/index.html") and [this link here]("http://linuxcommand.org/lts0070.php") ( i like this one better )

---

### Post by Brad_J on 2011-06-18
> **nitstorm said:**
> Symlinks are short for Symbolic Links (Shortcuts ideally speaking).
But shortcuts (At least in windows) are separated from the file and just created to give access to a location, correct? Nothing would have any problem copying a .lnk because without any context it wouldn't have any use. Would an accurate description of symlinks be similar to pointers or references in programming, where the address of memory is given and the original file can be modified through it? Or am I way off? How would this have happened with my windows files, did ubuntu do something behind the scenes that I am unaware of?

---

### Post by nitstorm on 2011-06-18
> But shortcuts (At least in windows) are separated from the file and just  created to give access to a location, correct? Nothing would have any  problem copying a .lnk because without any context it wouldn't have any  use. Would an accurate description of symlinks be similar to pointers or  references in programming, where the address of memory is given and the  original file can be modified through it? Or am I way off?
Symbolic links contain pointers to the file location just like in programming, as you said. For a nice explanation on symlinks see - [http://www.nixtutor.com/freebsd/understanding-symbolic-links/](http://www.nixtutor.com/freebsd/understanding-symbolic-links/)

---

### Post by yetiman64 on 2011-06-18
> **Brad_J said:**
> Does this mean that using chmod 000 for anything outside of the home folder will restrict even root from accessing it?....

No, root "owns" everything including the /home folder in which your user folder and all your files are located. Even if you went and put 000 permissions on some file anyone gaining root access to your install from a network accessing process running as root would have the ability to change the permissions as they would be "root". Note the owner of a file has the ability to change permissions of that file. I suggest you never alter the permissions of a file outside your folder without a very good understanding of what can happen, permissions changes to system files/folders are regular source for new starters having to reinstall a system here (I have shot myself in the feet a few times while operating as root, requiring re-installs on a couple of occasions).

Some files like /boot/grub/grub.cfg are set as read only for root, yet the system can still change it to writable when alterations are needed, then set it back afterwards, this is one file the system doesn't like a user to be able to change even with sudo-ing, (it can be done with a couple of steps as root, but the system will ultimately overwrite any changes a user does make to it.)

The links for chmod, chown and the symlinking info from nitstorm is worth a good read for you, imo.

---

### Post by gordintoronto on 2011-06-18
> **Brad_J said:**
> Also, I didn't really ask, but is there a script that will automatically connect to a specified network if it's available? When I start ubuntu it enables wifi automatically but I have to go click on the network I want to join in order to join it.

Not a script, a GUI setting. Right click on your networking icon and select "edit connections." Click on the Wireless tab, then select your network. Click on "edit." Click on the "connect automatically" box. Then Close.

---

### Post by Brad_J on 2011-06-19
Thank you all for your responses, all of my questions were answered. Dropbox permission problems haven't come up again in a couple days while copying something over, but I'm sure they will and I know how to deal with them now. I'm gonna mark this thread as solved as I don't have any further issues, thanks again.

-Brad

---

