---
title: "setting up a server"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by opentarget on 2011-04-12
im trying to set up a server to link a few workstations in my house. the workstations are windows based, im a freelance artist and i use once machine for my 3d work and the other for flash and after effects. normally im back and fort all day between projects.

im follwing this tutorial:
[http://www.intac.net/build-your-own-server/](http://www.intac.net/build-your-own-server/)
got xubuntu 10.10 installed.
but when i hit the command line i hit problems.

i get to the point where i try to run "nano smb.conf" and that throws up "Error opening terminal: unknown"

i have it open in gedit and it allows me to make changes.
so in the guide linked above it asks me to replace workgroup = "Name"  so what is the "Name"? and netbios name = "Server name"
so what should that corespond to? 

is this guide for a much older version of ubuntu? im stumped here.

im sorry for the stupid questions.

---

### Post by f1tz on 2011-04-12
Not so sure on this, but I think your TERM environment variable isnt getting set.

try this: check the output of echo $TERM, it should probably be xterm. If not:

*export TERM=xterm*

if that works, you can probably put it in your .bashrc file, so it does it automatically.

---

### Post by spillin_dylan on 2011-04-12
Workgroup name refers to whatever your Windows machines are set up as with their workgroup (typically *workgroup* or *mshome*.  You can find this in Windows by right clicking My Computer, selecting Properties, and there should be some info about machine name, workgroup, and maybe domain?

Server name I believe refers to the hostname of your server.  In Linux try *uname -n* to find out what it is.

---

### Post by earthpigg on 2011-04-12
> **opentarget said:**
> 
is this guide for a much older version of ubuntu? im stumped here.


yes, but it shouldn't make that big of a difference. nothing wrong with using gedit instead of nano. i prefer leafpad, but to each his own.

spillin_dylan's guidance looks correct to me.

---

### Post by crispy_420 on 2011-04-12
> **spillin_dylan said:**
> try *uname -n* to find out what it is.

That returns kernel version. Try just simply 'hostname' to get machine name. 

But that is not 100% necessary for a samba server. There is a gui for samba configuration in the repos (system-config-samba?) where you can prep the server with shares, permissions, users, etc. Then find your local IP address on the server via 'ifconfig'. Remember or write down that address and head over to you Windows machine and from the run command type '\\ADDRESS' (ADDRESS = the IP you wrote down) it will then ask for username/password if you set one up. If you are able to try to reserve the address in your router, many have this feature. Also for convenience try mapping the drive in windows to save time.

---

### Post by earthpigg on 2011-04-12
> [QUOTE]try uname -n to find out what it is.
That returns kernel version.[/QUOTE]

surely, sir, you jest :)

```
[chris: ~]$ uname -n
chris-desktop
[chris: ~]$ hostname
chris-desktop
[chris: ~]$ 
```

---

### Post by crispy_420 on 2011-04-12
My bad thought it said uname -r.

---

### Post by opentarget on 2011-04-13
thanks for the help so far people!

i have sorted out the smb.conf and set it the WORKGROUP and the server name. i then save the file and close it.

then in terminal i try to restart the server by:
/etc/init.d/samba restart

i get this error:

bash: /etc/init.d/samba: No such file or directory

any thoughts?
thanks again for all the help.

---

### Post by f1tz on 2011-04-13
Hmm, cd to */etc/init.d*, do you see samba in there? Perhaps you see *smbd* instead? If thats the case try:
*sudo /etc/init.d/smbd restart*

Otherwise, it might be that you don't have samba installed?

---

### Post by opentarget on 2011-04-13
im quite sure samba is installed....in fact 100% sure.

ill try what you sujested when im at soon to be server later this evening.
ill report back when i try.

thanks for the reply.

---

### Post by opentarget on 2011-04-15
so i run this command: restart smbd
and get this:
smbd start/running, process 1956

im guessing this is confirmation of a restart?

so i run:    smbpasswd -a kevin
and get:

New SMB password:
Retype new SMB password:
then this happens:
Failed to add entry for user kevin.

so im totally lost here.
i defiantly have samba installed from the package manager. unless somthing mad happened in the install.
is there a command that will confirm samba install?

---

### Post by opentarget on 2011-04-15
just thought id bump this up, the forum gets tons of traffic.

dose anyone know of a better solution for server than what im trying now?

---

### Post by Hack.The.Pow. on 2011-04-15
check the /etc/init.d folder with a ls -a command.  Is there a entry for samba in there?

If so you might not just be working as root.  Try running sudo su and then try all commands again

---

### Post by gobbledigook on 2011-04-15
> **opentarget said:**
> so i run this command: restart smbd
and get this:
smbd start/running, process 1956

im guessing this is confirmation of a restart?

yes :)

> **opentarget said:**
> so i run:    smbpasswd -a kevin
and get:

New SMB password:
Retype new SMB password:
then this happens:
Failed to add entry for user kevin.

so im totally lost here.

try ```
sudo smbpasswd -a kevin
```

> **opentarget said:**
> i defiantly have samba installed from the package manager. unless somthing mad happened in the install.
is there a command that will confirm samba install?

```
sudo dpkg --get-selections | grep samba
```

will list the status of your samba installation... i would suggest reading the documentatio [here about samba]("https://help.ubuntu.com/community/Samba") and [here about ubuntu server]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

i started with a headless (no GUI... just terminal) server a few years ago and i have had great enjoyment out of setting it up just how i want ;) so don't be afraid of the Command line Interface, for future reference there is also a specific "server" forum which you would get a better response from :)

---

