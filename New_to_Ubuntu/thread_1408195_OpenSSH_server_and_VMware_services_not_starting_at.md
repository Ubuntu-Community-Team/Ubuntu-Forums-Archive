---
title: "OpenSSH server and VMware services not starting at reboot"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by kevinhobson2000 on 2010-02-16
Hi,

I have a problem with openssh server and Vmware services not starting up after a reboot.

I can only start them manually from cli.

I have tried adding them to the startup applications for eg i have added the SSH.

/etc/init.d/ssh start

I have also done.

sudo /etc/init.d/ssh start

But when i reboot the service has not started.

Thanks

Kev

---

### Post by Temposs on 2010-02-16
to start the ssh daemon, this is what I add to the startup programs:

```
/usr/bin/sshd
```

---

### Post by kevinhobson2000 on 2010-02-16
Hi,

I dont have the file sshd in that location.

I do have a file called ssh so i tried adding that as a startup program.

It still doesnt start automatically though i still have to start it manually after logging in.

Thanks

Kev

---

### Post by bodhi.zazen on 2010-02-16
Well, to start them add the commands to /etc/rc.local

You may need to add a sleep before your commands, but that does not tell us why the services are not starting.

Check your logs for error messages.

---

### Post by Temposs on 2010-02-16
I think it may be that you don't have the openssh-server package installed. Try installing that, and then you should have the /usr/bin/sshd file, which you can have started automatically using either my method or the one bodhi zazen suggests. Both should work fine.

---

### Post by kevinhobson2000 on 2010-02-17
Hi,

I tried installing open ssh server again and got the following:



kev@ubuntu:~$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 121 not upgraded.
kev@ubuntu:~$ 


So its definately installed but i dont have the sshd files in the /use/bin directory.

Cheers

Kev

---

### Post by Temposs on 2010-02-17
actually, I just looked up the Startup Applications on my server, and I just used:

```
sshd
```

as the command.

---

### Post by kevinhobson2000 on 2010-03-03
Hi,  I put in sshd for startup and ssh didnt start on a reboot.  Thanks  Kev

---

### Post by Temposs on 2010-03-03
Show me a screenshot of where you put it.

---

### Post by amrypma on 2010-03-03
You should make a symbolic link from /etc/rc2.d to /etc/init.d/ssh

```
cd /etc/rc2.d
sudo ln -s /etc/init.d/ssh ./S20ssh
```

Linux usually runs in runlevel 2 (the rc2 in the code above) and starts up every program listed in that directory with 'start' added to the commandline.

In this case:
```
/etc/rc2.d/S20ssh start
```

The S20 prefix is used to create some order in the startup procedure. It's no use running a ssh server when networking isn't possible jet.

As for VMWare you can create a startup link in the same manner. But you may have to write a script that only expects options like start or stop or restart.

Also note that ubuntu is switching to something else to manage this. So this might already be out of date.

---

