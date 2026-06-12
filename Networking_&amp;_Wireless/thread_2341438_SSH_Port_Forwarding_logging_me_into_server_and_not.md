---
title: "SSH Port Forwarding logging me into server and not forwarding onto the remote host?"
date: 2016-10-28
forum: Networking &amp; Wireless
---

### Post by Barry_Keegan on 2016-10-28
My goal is to type one command and be greeted by the login of a **remtoe-host** that is reachable through an **ssh-server**, I am running the command below.

**ssh -L 1300:remote-host:22 user@ssh-server**

It's my understanding that the **ssh-server** will forward my request onto **remote-host** and I will be greeted by a login screen for the **remote-host**. However I am asked for the credentials of the **ssh-server** where I can log into but then I have to ssh from there onto the **remote-host. ** Not the desired outcome.

My understanding of this subject is in its infancy so I'm clearly missing something. Perhaps a simple addition to the command?

I have checked that the **ssh-server **can reach the **remote-host** via port 22. 

Any help would be greatly appreciated,

Thanks in advance

---

### Post by TheFu on 2016-10-28
That command doesn't do what you think.  It forwards localhost port 1300 --> port 22 on remote-host.  So after you make the connection to ssh-server, you need to do **ssh -p 1300 localhost** to see the login you want.  That is using an ssh-tunnel inside an ssh-tunnel, effectively.

I wouldn't bother. 

I'd just **ssh -A -t  user@ssh-server ssh remote-host** and be done.

I'd also setup ssh-keys to make this easier. More details: [http://sshmenu.sourceforge.net/articles/transparent-mulithop.html](http://sshmenu.sourceforge.net/articles/transparent-mulithop.html)
and [http://dailytechvideo.com/bo-jeanes-black-magic-ssh/](http://dailytechvideo.com/bo-jeanes-black-magic-ssh/) might help if you learn by watching, but that video has some pretty advanced stuff.

---

### Post by Barry_Keegan on 2016-10-29
Awesome you explained that perfectly it it worked for me. I will check out the links definitely.

The 2nd option **ssh -A -t  user@ssh-server ssh remote-host **unfortunately doesn't work as the ssh-server is a windows operating system and doesn't recognize the 2nd ssh command. The connection stops at the windows command line. I could perhaps install something on the ssh-server to allow the 2nd command. Something to research further.

---

### Post by TheFu on 2016-10-29
> **Barry_Keegan said:**
> Awesome you explained that perfectly it it worked for me. I will check out the links definitely.

The 2nd option **ssh -A -t  user@ssh-server ssh remote-host **unfortunately doesn't work as the ssh-server is a windows operating system and doesn't recognize the 2nd ssh command. The connection stops at the windows command line. I could perhaps install something on the ssh-server to allow the 2nd command. Something to research further.

Sorry ... forgot the port.

```
$ ssh -A -t user@ssh-server ssh -p 1300 remote-host 
```

I use ~/.ssh/config files to abstract away the port and userid stuff.  Don't know if Windows supports that or not.

---

### Post by Barry_Keegan on 2016-10-31
unfortunately the addition of **-p 1300 remote-host** does not work. I get the same issue, it drops me into the ssh-server command line saying ssh is not a recogonised command.

---

### Post by TheFu on 2016-10-31
does ssh-server have an ssh-client on it?  Specify the full path to it.

---

### Post by kpatz on 2016-10-31
If the ssh-server is Windows, you'll need to install something like OpenSSH for Windows to gain the ssh command in Windows.

When you ssh into ssh-server, do you get a regular Windows command prompt (i.e. cmd.exe)?

---

### Post by Barry_Keegan on 2016-11-01
When I issue this command **ssh -A -t user@ssh-server ssh -p 1300 remote-host **I don't get into the cmd line on the windows server. the connection gets terminated. This is down to not having an ssh client installed on the ssh-server for sure. See error below. Don't know if I can mark this thread as resolved but I am very satisifed with the answers from TheFu, thanks very much.


'ssh' is not recognized as an internal or external command,
operable program or batch file.
Connection to ssh-server closed.

---

### Post by TheFu on 2016-11-01
Windows doesn't support ssh without a 3rd party program.  I've heard that MSFT was planning to add support (announced about a year ago) - but never heard they did. Perhaps that was one of the reasons they worked to get ubuntu working under Windows?  I thought that effort was really more about Docker/container support.

In the future, please specify the OSes involved in the OP.  I missed that Windows was one of the servers and wasted a bunch of time on this.

---

### Post by Barry_Keegan on 2016-11-01
Message noted regarding OS specification.

Is your command **ssh -A -t user@ssh-server ssh -p 1300 remote-host **possible to use in conjunction with the windows server so I do not have to enter 2 commands?

---

### Post by TheFu on 2016-11-01
Don't know. i don't use windows in that way. The idea of windows having **any** ssh-server capabilities is new to me.
OTOH, if you remove windows, it DOES work.

---

### Post by Barry_Keegan on 2016-11-02
acknowledged, thanks for the help!

---

