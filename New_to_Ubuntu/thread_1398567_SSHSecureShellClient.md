---
title: "SSHSecureShellClient"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by arpit.iitkgp on 2010-02-04
i want to connect to a server. someone told me to download SSHSecureShellclient 3.2.5 .
I am a noob. HELP 
btw I am running Ununtu Karmik

---

### Post by ibuclaw on 2010-02-04
Ubuntu already has SSH installed.

In a nutshell, to connect, type in:
```
ssh username@hostname
```
or
```
ssh username@10.1.254.254
```
to connect via IP address.

I'll just have a quick nose round to see if there is any official documentation on the subject (not that there is alot to document :)).

Regards
Iain

---

### Post by ibuclaw on 2010-02-04
Nope, can't see anything else, only for ssh-server (which is not what you want).

I've already mentioned how to connect to a server via command-line:
```
ssh username@hostname
```

You can also use ssh to run commands:
```
ssh username@hostname touch ~/hello_world
```

You aren't limited to command-line though, to run GUI applications via SSH, use the -X argument:
```
ssh -X username@hostname xeyes
```
In each instance, you will be asked to type in your server account's password.

Regards
Iain

---

### Post by arpit.iitkgp on 2010-02-04
first of all thanks 
i typed in the code in the terminal 
but nothing is happening 
  here's a screen-shot

---

### Post by arpit.iitkgp on 2010-02-04
gui didnt run

---

### Post by ibuclaw on 2010-02-04
Can you ping the server?

Do they use a particular port for ssh connections other than the default?

If so, there is the -p argument too to specify the port use.
```
ssh -p 22 username@hostname
```

Regards
Iain

---

### Post by arpit.iitkgp on 2010-02-04
I am using an internet connection which is proxy enabled
Can it possibly cause a problem?(the server is located outside my lan)
Plus i want an interface to run the server(like a window or something if its possible) ... and download things and stuff... is it possible??

---

### Post by arpit.iitkgp on 2010-02-04
> **ibuclaw said:**
> Can you ping the server?

Do they use a particular port for ssh connections other than the default?

If so, there is the -p argument too to specify the port use.
```
ssh -p 22 username@hostname
```

Regards
Iain
The port is default(22)
but then again the output of the post which came after some time was"ssh: connect to host drum.cs.usm.edu port 22: Connection timed out"
help..

---

### Post by ibuclaw on 2010-02-04
> **arpit.iitkgp said:**
> I am using an internet connection which is proxy enabled
Can it possibly cause a problem?(the server is located outside my lan)
Plus i want an interface to run the server(like a window or something if its possible) ... and download things and stuff... is it possible??
You mean, like a filesystem?

Sure, look up sshfs
```
sudo apt-get install sshfs
```

Ensure you are added to the fuse group:
```
sudo usermod -aG fuse jstdio
```
**Note**: you need to logout / login for the group permission to take affect.

Then to connect:
```
sshfs -o idmap=user [COLOR="Navy"]username[/COLOR]@[COLOR="Navy"]hostname[/COLOR]: ~/[COLOR="Navy"]mountpoint[/COLOR]
```
The bits highlighted are all that require changing to suit your needs.

Then browse to the mountpoint location on your local filesystem, and all files should be there.

Regards
Iain

---

### Post by ibuclaw on 2010-02-04
> **arpit.iitkgp said:**
> The port is default(22)
but then again the output of the post which came after some time was"ssh: connect to host drum.cs.usm.edu port 22: Connection timed out"
help..

Can you ping the server?

```
ping drum.cs.usm.edu
```
If not, the chances am that the server hardware/software firewall is not setup correctly for access from the outside world.

In this instance, you should contact the administrator for further advice/instructions, as you are doing nothing wrong in terms of "client-side" actions.

Regards
Iain

---

