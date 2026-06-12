---
title: "Transfer files from ubuntu live to windows pc"
date: 2014-03-25
forum: Networking &amp; Wireless
---

### Post by John66645 on 2014-03-25
Hey, 

I am trying to recover some files laptop that will not boot ( windows xp installed ), dvd-rom isn't working either. The largest usb key i have is 2gb. I installed **ubuntu 11.10** on it since the old cpu doesnt support newer ubuntu and i **live booted** into it ( **without instlaling** ). I figured the best way to transfer files ( about 30 gb ) would be using local network. I tried installing **samba **but no matter what i do, i get errors. I tried basicly all hints i could find online but i still get the error. Is there a simple alternative to samba ? If not, one way would be to transfer files using internet, i can transfer about 5gb per hour which means in 6 hours it would be transfered. I want to transfer files to windows 7 computer. Any ideas ?

---

### Post by Morbius1 on 2014-03-25
So you basically have a Linux - to - Linux setup?

On the LiveCD system:

** make sure all the Windows partitions are mounted.
** Open a terminal and change to the root directory:
```
cd /
```
** Then create a baby http server:```

python -m SimpleHTTPServer
```

** On the real Linux system open your internet browser and enter the other systems web server:
```
http://ubuntu.local:8000
```
All of your files will appear as down-loadable entities.

[I][COLOR=#0000cd]**Note**[/COLOR]: This method has no idea what to do with Directories. So if you have a whole bunch of stuff in a directory the usual method is to Zip it ( or any other archive ) and then download that since it will then appear as a file not a directory.

[COLOR=#0000cd]**EDIT**[/COLOR]: Misread the original post. Seems like you are trying to transfer this to another Windows system. The LiveCD part will still work but Windows ( and only Windows btw ) has no idea what an "ubuntu.local" is so you will have to use the ip address instead. As in:
```
 http://192.168.0.100:8000
```
[/I]

---

### Post by untrustytahr on 2014-03-25
OpenSSH & Putty

---

### Post by John66645 on 2014-03-25
I am having problems with SSH, similar to samba.
I tried SimpleHTTPserver and it worked. The problem though is that my ubuntu isnt installed, rather ran from usb ( same as cd-rom live). That means that my backup files are on disk while my ubuntu isnt. While i can see Home, Downloads, Desktop and soo on .. i dont know how to access Devices or media where my hard drive is.

edit: i solved it by creating a shortcut. Thank you for your help, i feel like i just performed an 8 hour brain surgery, i need a week off -.-

---

