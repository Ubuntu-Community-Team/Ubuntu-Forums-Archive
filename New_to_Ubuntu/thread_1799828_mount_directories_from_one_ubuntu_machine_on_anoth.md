---
title: "mount directories from one ubuntu machine on another ubuntu machine"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-07-08
Hi Ubuntu Community:

I have two Ubuntu machines. The user ids on those machines are:

machine1 and machine2

I have directories on machine1 that I want to mount on boot up on machine 2.

Specifically, I want 

[COLOR="Green"]**/home/machine1/Documents**[/COLOR]

to mount on boot up at

[COLOR="Red"]**/home/machine2/Documents**[/COLOR]

I'm having trouble with this. 

Here is what I've done:
1. installed samba: 
applications > ubu software center > samba > install

2. made /home/machine1/Documents shared on machine 1: 
system > administration > samba > preferences > server settings where I selected authentication mode: share and guest account: machine1. Clicked "ok'

3. clicked on the green "+" on samba server configuration, browsed to /home/machine1/Documents, clicked "writable" and "visible' and on the access tab, clicked on "allow access to everyone"

When I log onto machine2, when I choose places > network I can see "machine1" icon. When I click on it, I can see /home/machine1/Documents and I'm able to open that director, and read and write files there.

My question is:

[COLOR="Red"]**How do I mount that share automatically on boot up?**[/COLOR]

I've followed advice at [http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html]("http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html").

Specifically, in my /etc/fstab I added:

[COLOR="Green"]**//192.168.1.66:/home/machine1/Documents /home/machine2/Documents smb defaults 0 0**[/COLOR]

However, when I reboot, I get a message that something went wrong with the mount, and am asked to type "S" to skip trying to mount the share.

How do I get this to work?

Thanks!

Phil Smith de Duluthistan, GA









on machine2.

---

### Post by nothingspecial on 2011-07-08
If both machines are Ubuntu, samba is completely unecessary, it is for using with Windows.

Have a look at ssh and for automounting, sshfs.

---

### Post by dasan on 2011-07-08
You can even try NFS 
I have tried it and was working for me.

---

### Post by Morbius1 on 2011-07-08
> //192.168.1.66:/home/machine1/Documents /home/machine2/Documents smb defaults 0 0First, make sure you have the following package installed:
```
sudo apt-get install cifs-utils
```If you are using an older version of ubuntu the package is called:
```
sudo apt-get install smbfs
```Then change the fstab line to this:
```
//192.168.1.66/Documents /home/machine2/Documents cifs guest,uid=1000 0 0
```[COLOR=Blue][I]The line above may need to be tweaked depending on  how the share is being used on the client but it should mount with  access to you.

[/I][/COLOR]Notes:
* > 2. made /home/machine1/Documents shared on machine 1: 
system > administration > samba > preferences > server  settings where I selected authentication mode: share and guest account:  machine1. Clicked "ok'Since you created a guest share it really doesn't matter but you might want to go back in there and set the share level security back to the default of "user" instead of "share". Share level security hasn't been used since Jimmy Carter was President and no one living remembers how it works - that may be a slight exaggeration :wink:

* Don't wait for a reboot to test the new line in fstab. Run the following command instead:
```
sudo mount -a
```That will run the new line, post any errors if it finds a problem, and mount the remote share.

If you still run into problems post the output of the following command from machine1:
```
testparm -s
```

---

