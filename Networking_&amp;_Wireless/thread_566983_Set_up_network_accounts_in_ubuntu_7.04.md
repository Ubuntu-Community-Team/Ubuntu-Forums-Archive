---
title: "Set up network accounts in ubuntu 7.04"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by paulie69 on 2007-10-04
Ok, i have been using Ubuntu for around a yr now but have never got really technical in using it or networking with it. What i would like to do is setup some form of network user accounts like they use at schools and businesses, u know where u have to press Ctrl, Alt, Del on the windows box's to get to a login page then you login through a main server ( ubuntu in my case) which stores all your files.

Also i would like a guide or something to setting up a shared printer on Ubuntu which would connect through usb to the Ubuntu box then shared throughout the network.

and, last but not least, what sort of tweaks or adjustments can i make to improve the speed of my network?

Any help will be appreciated greatly.

Thanks heaps, Paul

---

### Post by renzokuken on 2007-10-04
you want a primary domain controller.......i just set one up for aour group at uni.....very easy

have alook here

[http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10](http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10)

---

### Post by paulie69 on 2007-10-04
hey do you know if i must use the server edition? and does the server edition just have a command line or does it have a user interface?

---

### Post by renzokuken on 2007-10-05
you can use desktop or server....desktop you would have to install samba but thats only one command

server comes as command line only but you can install the UI with one command

i personally installed the server so i had samba and lamp and everything else already installed.....then ran 

```
sudo apt-get install ubuntu-desktop
```

to install gnome and give me a GUI (i.e. the Gnome Desktop)

---

### Post by paulie69 on 2007-10-05
Ok thanks for all your help so far!

I am getting very annoyed at the command line and have tried "sudo apt-get install Ubuntu-desktop" and well lets just say with my net i might as well install samba and lamp after lol.

With that guide you referred me to it is really starting to confuse me, since I'm a noob at networking except for simple samba file sharing, do you know of a more broken down guide?

And as for assigning a static ip, instead of a static ip what if i used DHCP and just used the host name ( example: Ubuntu)  to connect to it instead?

Thanks, Paul

Edit: Also do you have any idea how to get it all working on the windows side?  i am using win xp.

Thanks again.

---

### Post by renzokuken on 2007-10-05
that guide over complicates it alot, i ignored the majority........

all your really need to do is install samba and edit the smb.conf file a bit, which i can show you how to do if you like.

adding users to the domain is a case of a couple of commands. and them entering their own passwords.

---

### Post by paulie69 on 2007-10-05
Yeah that would be excellent if you can show me.

When i try to edit the smb.conf file it says Permission denied, see below.

root@ubuntu:~# /etc/samba/smb.conf              
-bash: /etc/samba/smb.conf: Permission denied 

Am i doing it correct?                                            

EDIT: Ok never mind about that above i figured out if i log into root and then browse to the file manually i can happily edit it.

EDIT: Ok i know how to set it up in windows just have to finish off the work in Ubuntu and it should be all up and running, hopefully :)

EDIT: So what are these edits i need to do, and how do i add users?

---

### Post by paulie69 on 2007-10-11
Ok, so i finally figured out how to get windows to connect to the domain and it logs in ok with the user names i setup, now i have a few q's

1. when it logs in it says "windows cannot locate the servers copy of your roaming profile" & "windows cannot locate your local profile and logging you on with a temporary profile" well something like that anyway, how can i fox this?

2. It also promts me to tick some tick boxes that it wnats me to do and i don't know what it is 
- tick box 1 "migrate windows 3.x win.ini and control.ini
- tick box 2 "migrate windows 3.x programe manager group files.

What would be best to tick for me?

Thanks, Paul

---

### Post by renzokuken on 2007-10-11
lol, roaming profiles, i had all that crap trying to set my domain up.......anyways, you need to disable roaming profiles, there are two ways (or use both) to do it.....

firstly edit your smb.conf so that your logon path and logon home are unassigned...

i.e.

logon path = 
logon home = 

(blank after = sign)

then restart samba

```
sudo /etc/init.d/samba restart
```

try that, if it doesnt work i'll show you the other way

no idea for question 2 though.....but solving 1 may automatically solve 2.

to add users, add them to the server first

```
sudo useradd *name* -m -G users
```

replacing *name* with their desired username

then give them a sambapassword using

```
sudo smbpasswd -a *name*
```

enter their password twice

restart samba again

then to logon on their windows machine just use whatever *name* was for username and whatever smbpasswd you/they entered for a passwd.

the new users will each now have a home folder on the server only they cann access. they can logon onto the domain from any win pc connected to it using that same u/n and p/w

enjoy

---

### Post by paulie69 on 2007-10-11
LoL dam roaming profiles, it still does the same thing.
Is there anyway i can actually make a roaming profile for each user?

Thanks, Paul

---

### Post by renzokuken on 2007-10-12
on the windows computers, log in and right click on My Computer and select Properties

Advanced Tab - User Profiles - Settings and use Change Type to change accounts from Remote to Local

---

### Post by paulie69 on 2007-10-13
Hey thx heaps that worked great, thx for all your help with this cus i know i don't understand much about it but it helps heaps when i got someone that knows what there talking about like you. :)

You rock dude! :guitar:

Thanks. Paul

---

### Post by worksofcraft on 2007-10-26
Thanks for this thread :-)
I couldn't understand why my Ubuntu pc can access my Windows pc shared folder but vice-versa needed a user+password, but my normal sign in didn't work :-(
Just to recap: after the following commands it did.

sudo useradd name -m -G users
sudo smbpasswd -a name

---

### Post by ginge6000 on 2007-10-26
Sorry to highjack another thread but I'm trying to do a similar thing.  Thanks to your info I've managed to get a Windows machine to log onto the Samba domain but how do I get an Ubuntu desktop to do the same?  I used 

```
[global]
    security = domain
    workgroup = myworkgroup
    password server = server
```

as my smb.conf on the Desktop and then did

```
net rpc join -S server -UAdministrator%password
```

which told me that I had successfully joined the domain but when I go to log in I can still only log in as a local user, not one of the domain users?

---

