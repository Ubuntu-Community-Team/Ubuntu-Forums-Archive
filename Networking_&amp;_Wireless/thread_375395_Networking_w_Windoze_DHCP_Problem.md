---
title: "Networking w/ Windoze DHCP Problem"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by hppyfngy on 2007-03-03
New Edgy install and wired connection enabled, dhcp connects me to WRT54G and internet, no problem, but I don't show up in router clients list.  

Network settings untouched except changing Domain name to mshome in "general" tab.  Can't determine my network address.  DNS servers listed are of my ISP.  

Samba running.  Home folder shared and it shows up in my XP machine's workgroup, but I can't access it.  I can cruise the mshome network from Edgy fine.  

How do I access Edgy from Windows machines and where is my ip address?  :confused:

---

### Post by Mr. C. on 2007-03-03
First, your IP address:

ifconfig -a

You'll find it there.

Something seems off if your WRT54G is not show the IP address in its DHCP table, AND it gave you the IP address via DHCP.  Be sure that the IP addr of your system is within the IP address of the DHCP server (just as a double check).

Second,  for your Samba config, is your home folder shared to Everyone, or just your own UID?  Check the permissions set for your shared folder.  Windows will attempt to acess as Guest if no credentials are not specified.

MrC

---

### Post by hppyfngy on 2007-03-03
Thx, was able to find my ip at least, now I can assign a port forward to it for azureus.  Still don't know why it doesn't show up in my clients table, but the port forward worked.

Still having trouble with permissions...


It looks like I have somehow set my group to my username..  ](*,) 

How do I change my group name for the folder I want to share??

---

### Post by Mr. C. on 2007-03-03
Good.  Was the IP in your DHCP range assigned on your router?

I'm not sure I'm following you on "group name for the folder" and "set my group to my username".  You mean your directories UID/GID ?  What "group" and "username" are we referring to?

---

### Post by hppyfngy on 2007-03-03
Yes, my IP addy was in the range.  

Username is randy, (that's me,) and I get this in terminal

randy@randy-desktop:~$ ls -l /home
total 4
drwxrwxrwx 30 randy randy 4096 2007-03-03 18:29 randy


I'm new to this but doesn't that indicate that for that folder the owner is randy (not root) and the group is also randy.  

Don't wonder how I got here, just followed some bad advice I guess...:(

---

### Post by hppyfngy on 2007-03-03
Well, I figured out how to change the hdd permissions back to root, but still can't  open server from windows network.

I get a login screen but username and pw don't work.  :popcorn:

---

### Post by Mr. C. on 2007-03-03
Sorry, I got a bit busy for a bit there. 

No problems, just trying to make sure I understand what you were saying.

Part of the confusion is the terminology (folders vs. directories), the former being Windows/Mac'ish, the later being Unix/Linux.

Ubuntu sets a user into his/her own group (eg. user: randy, group: randy), so that's fine.  Your home folder should be owned by you, and grouped as desired for various forms of security.  Its clear with your permissions being 777, your directory is wide open anyway.

You wouldn't want your home directory owned by root - its yours, and you get to set the permission on it to allow group members, and others read, write, or examine access.  If it was owned by root, you could not make those changes.  Here's mine:

drwxr-xr-x 19 cappella cappella 4096 2007-03-03 16:42 /home/cappella


I'll respond to your second part about not gaining access in a few minutes...

MrC

---

### Post by Mr. C. on 2007-03-03
Now, back to the problem at hand.

You need to enable a few settings in Samba to allow shares to work correctly.  How you do that depends somewhat on what you want to accomplish, and how concerned you are about security, already have a Windows password, etc.  Rather than us go back and forth, here is a good getting started guide.  You likely only need to configure a few settings, as you should already have some files in place.

First, shutdown samba:

/etc/init.d/samba stop

Next, copy the samba config file so you can revert if necessary:

cd /etc/samba
cp smb.conf smb.conf.save

Now, review the settings in the first post, inside the scrolling text box here:

[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto)

You need to change the settings in smb.conf, but don't just copy that file.  Instead review the settings line by line, and try to understand the instructions there.  Any line that starts with a semicolon or blanks and a semicolon can be ignore - they are comments.

There are serveral things you have to configure correctly, so be sure to review each setting as described in the HowTo.  I'll help if you don't understand some things.  Set your workgroup to be the same as that of your Windows system (eg. WORKGROUP, or MSHOME, if that's what it is).

You can ignore the stuff about creating home directories, etc.  You already have one.  Use this instead, replacing with your home directory (i used hppyfngy for you).

[hppyfngy]
 path = /home/hppyfngy
 available = yes
 browsable = yes
 public = yes
 writable = yes

These are not necessarily secure, but you can worry about that later.

Once you've made those changes, you can start samba again (/etc/init.d/samba start)
and then you need to setup your passwords.  Follow the directions for adding the user to hte samba password file and enabling that user (the smbpasswd -L -a your_username and smbpasswd -L -e your_username commands).  Ignore any useradd commands - you already are a user.

Now, see if you can browse via your PC to your samba shares; your login should be work, and will be the username you configured with the password you entered.  You'll not the first time it will fail, and then add your systemname\username - this is correct, and how you actually are named as a user.  This time, it should succeed.

Once that all works, you can concern yourself with security, and any other shares.

Hope this helps,
MrC

---

### Post by hppyfngy on 2007-03-04
Thanks for your time and expertise Mr C

I'll give it a try and post again later.  Have little time today.  

As I live in the middle of nowhere, I have no security on my network, so this should be pretty simple.  

BTW, did a firmware upgrade to the router and now Edgy shows up in my clients table...

Thx again  :guitar:

---

