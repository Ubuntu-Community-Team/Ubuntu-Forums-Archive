---
title: "Ubuntu x64 - LTSP - pam_mount and auto start local apps &quot;issues&quot;"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by rcocchiararo on 2014-04-03
Hi there!

I had to look into installing ubuntu with LTSP. Right now 12.04 ships awesomly easy to work with this, it works right out of the box if you install it on a machine with 2 Ethernet cards.

A friend did some stuff with likewise-open and joined the ubuntu machine to a windows domain.

After i got it working, i installed skype/google chrome as local apps (dunno if this is cleaver for chrome? i was told to do that :P)

All is fine, i just had to add an iptables rule and it worked.

Only 2 things i am missing are:

1) Mounting windows shares automatically
2) Having the local apps autostart when users login.

*****************************
Now, for point 1, i followed this:
[https://help.ubuntu.com/community/UbuntuLTSP/ActiveDirectoryIntegration](https://help.ubuntu.com/community/UbuntuLTSP/ActiveDirectoryIntegration)

I just had to install what is listed there, all the other changes (besides the .xml modifications for what i wanted to mount) were ok from the get go.

Example of what i mounted:

```
<volume
fstype="cifs"
user="*"
server="serverName"
path="Users"
mountpoint="/home/likewise-open/DOMINIO/%(DOMAIN_USER)/Escritorio/User-Share"
options="user=%(DOMAIN_USER),domain=DOMINIO"
/>


<volume
fstype="cifs"
user="*"
server="serverName"
path="folder"
mountpoint="/home/likewise-open/DOMINIO/%(DOMAIN_USER)/Escritorio/folder"
options="user=%(DOMAIN_USER),domain=DOMINIO"
/>

```

This works perfectly if i log in to the computer directly. 
But if i log from a thin terminal (normal old pcs really :P), nothing gets mounted. 
Then again, if i first log in locally, and then from the thin teminal, the mounts REMAIN.

Using pam_mounts, you don't seem to need to create the folders where you are going to mount stuff, if they don't exist, they "appear". But if you had created them, a small icon (similar to a hard disk?) is added to them when the mount works.
But if you create the folders, and log in from a thing terminal without loging in locally first, the folders get DELETED.

I don't know where to look for this, enabling debuging does not help me, so i am at a loss here. For now i added those locations as "bookmarks" in nautilus (they are mounted by smb://server/folder), but this is not ideal because google chrome does not use nautilus for browsing files, so users have no direct access to those bookmarks and this turns out very cumbersome.

***************************
For point 2:

**Autostart software on all fat clients.**


[LIST]
[*]To autostart a program for all fat client users is fairly easy, simply copy the .desktop shortcut of the application to the/etc/xdg/autostart folder.
[*]If you want to start google-chrome for all fat client users open the Terminal Window and enter :
[/LIST]
sudo cp /opt/ltsp/amd64/usr/share/applications/google-chrome.desktop /opt/ltsp/amd64/etc/xdg/autostart/


Now, i don't use fat clients, so it seems the 2nd option does nothing.
But if i use the first option, apps are not run locally, but from the server.

Was it a mistake to install the apps in the "server" AND as "local apps" ?

BONUS QUESTION:
If i run chrome from the launcher bar, a 2nd chrome icon appears if it runs locally. Can we avoid this? skype does work like this.

---

### Post by rcocchiararo on 2014-04-04
To partially answer to my own questions (which i made after lots of research, but i had even more time now):

1) I have yet to try pam_mount again, but i learned today that i had to enable extra mounts so that localapps could access some stuff, so for now, i mounted the shared folders using fstab (windows domain permissions are completely ignored :() and i used some dirty tricks

2) Auto start is suposed to be setup in the server, i guess. I learned today that i can modify the launcher files to use "ltsp-localapps APPNAME" command instead of the stock stuff. Now the IP phone (jitsi client) starts automatically (skype does not work, but not a big issue). 

BONUS: this is related to the part i learnt about the extra mounts in question 1 :P

ps: i have now to experiment and see if i can use empathy to fully use skype single/multi voice/text chats and also as a SIP client, since both official skype for linux and jitsi are HORRIBLE :P

---

### Post by rcocchiararo on 2014-04-07
Regretably, pam_mount still does nothing for me in the thin clients, but works ok if i log in locally into the machine :(

---

