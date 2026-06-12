---
title: "Truecrypt startup"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by scweston on 2009-01-17
Hi,

I've installed Truecrypt and have already set up an encrypted volume file which I have saved as one of my 'favorites'.

What I would like to do is have Truecrypt start up with just the taskbar icon, nothing else. This way all I have to to is right click over the taskbar icon and select to mount the volume from the favorites listed when I want access to my encrypted data. I do not want the computer to automount the favorites on login.

Is there a way I can set this up. So far I have tried adding the following to the System> Preferences> Sessions> Startup Programs list...

Name: Truecrypt
Command: truecrypt
Comment: Encryption Software.

But, unfortunately, this brings up the main Truecrypt GUI window which I find a bit obtrusive and untidy on startup.

Your help will be much appreciated.

Stephen.

---

### Post by nhasian on 2009-01-17
i'm  not sure you can launch truecrypt minimized, but i have an alternate solution to your problem.  you could create a button on your taskbar or desktop and have it execute this command:

```
truecrypt --auto-mount=devices
```

this will mount any truecrypt volumes you have.  then you can create another icon to dismount them with:

```
truecrypt -d
```

truecrypt should only ask for the password decrypt the volume.  if you have to put in your superuser password to give it mount/dismount privileges, then you just need to to edit your sudoers file with the command:

```
sudo visudo
```

then append to the file:

```
username localhost=NOPASSWD : /usr/bin/truecrypt
```

where username is the username you use to log into ubuntu

---

### Post by scweston on 2009-01-17
Hi,

Thank you nhasian! I have tried your alternative suggestion and this works well. It is possibly the best solution so far. In the absence of any better solution I will probably use this.

Unfortunately I'm a bit 'Obsessive Compulsive' over things and do like things to be neat and tidy. So if there is any possibility I could get it working the way I described in my first post I would like that.

Hope you don't mind if I don't tag this thread 'SOLVED' just yet in case someone offers a better solution.

Thanks!

Stephen

---

