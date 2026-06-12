---
title: "Ndiswrapper - start wireless at startup"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by swatto on 2008-02-22
Hi all,

Ive got my wireless card working with linux using ndiswrapper and ndiswrapper loads at startup however in order to switch my wireless card on I have to open a terminal and type:

**sudo modprobe ndiswrapper**

and then my user password.

Is it possible to get this command run automatically at startup so I dont have to type it when my computer loads?

Also when the wireless is connecting it keeps asking to access kdewallet which means i have to type my user password in again - is there anyway to automate this.

Cheers :)

---

### Post by alan34 on 2008-02-22
Hi in a terminal Applications - Accessories -Termnal

copy and paste

gksudo gedit /etc/modules

and put ndiswrapper on a line on its own, like this

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

Then restart the PC

Should do the trick

---

### Post by swatto on 2008-02-22
Thanks alan34 but is this the same as doing:

ndiswrapper -m

in the terminal window? im currently at work so can't test it out.

---

### Post by SebMKd on 2008-02-22
Hi Swatto. I have the same problem. However, I did the modules edit as suggested above, and only get my wireless working once in a while; meaning that every two boot I need to redo the ndiswrapper -m. So I don't know what's really working 100%.

I read somewhere else to do the following:
After the '[FONT="Courier New"] sudo ndiswrapper -m[/FONT]' do:
[FONT="Courier New"]sudo depmod -a
sudo modprobe ndiswrapper[/FONT]
I will try that later on and post results.

I have another "issue", which isn't too bothering, that I'd like to solve as well. After editing the modules with ndiswrapper at the end, every time I boot my system I have to enter my user password to unlock something like 'nm-keymanager'. It seems to be my network manager wep/wpa key manager requesting admin rights... have you experienced s.th similar? Does anybody know how to address that issue?

Thanks

---

### Post by alan34 on 2008-02-22
Editing the /etc/modules file will insert the ndiswrapper module when the computer
is booting up, you will not even see it and your wireless should be working when
you login. No terminal and no commands - works for me.

( I think it is the same as sudo modprobe ndiswrapper)

Sorry never used nm-keymanager which I guess controls passwords I
would do a separate new post for that one.

---

