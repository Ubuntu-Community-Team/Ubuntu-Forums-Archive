---
title: "Samba vanishes"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by proituk on 2010-11-26
I am evaluating Ubuntu. I am trying to create a standalone, solely Ubuntu pc and connect it to a Windows workgroup so that the workgroup can use it as a file server. I have installed Ubuntu 10.10 and have persuaded it to function after many attempts.
 
I then followed the instruction on how to set-up Samba from [http://www.linuxuser.co.uk/tutorials/build-a-samba-file-server/](http://www.linuxuser.co.uk/tutorials/build-a-samba-file-server/) and it worked for a few minutes.
 
When I attempted to remodify smb.conf again (as suggested) and then re-start samba.... (sudo /etc/init.d/samba restart) the system tells me that samba does not exist in the defined 'directory' of /etc/init.d. If I view the directory.... it's correct... there is no Samba....
 
Any suggestions as to where it's gone and what I do about it? How do I get it back?

---

### Post by Morbius1 on 2010-11-26
The samba service no longer exists and has been replaced by it's component parts - smbd and nmbd.
> sudo /etc/init.d/samba restartis now:
```
sudo service smbd restart
```

---

### Post by proituk on 2010-11-26
Thank you Morbius.
 
However, that elicits the reponse:
 
    restart: Uknown instance
 
.....and the _U_buntu machine is still not visible in Windows even thought it had been before Samba vanished.
 
Can you help further, please?
 
Ian

---

### Post by proituk on 2010-11-26
continued....
 
I guessed that the message meant that I shoud be 'starting' smbd rather than restarting it and tried:-
 
                   sudo service smbd start
      
That got the respone:-
 
                  smbd start/running process 1563
 
but still no sign of the Ubuntu pc from Windows
 
Does the change from Samba to smbd imply that the smb.conf file which I have modified (in line with that web page) is not the one being 'used'? If so, what file do I edit, now?
 
Ian

---

### Post by Morbius1 on 2010-11-26
It's the same smb.conf.

If smbd stopped for some reason then perhaps nmbd stopped as well. nmbd is the service that actually broadcasts your machine name. So start or restart it:
```
sudo service nmbd start
```

---

### Post by proituk on 2010-11-26
I have tried that and I now:-
 
sudo service nmbd start
 
 .......gets the response...
 
Job failed to start
 
Ian

---

### Post by Morbius1 on 2010-11-26
To be honest I have never seen nor read about that error message after explicitly starting a service in a terminal before.

Using some exotic firewall or apparmor by any change?

---

### Post by proituk on 2010-11-26
Nope.....
 
I have now tried re-installing Ubuntu 10.10 for the 5th time, suspecting that I must have corrupted it while editing the 'interface' file.... I now doubt that I have. Each time I install it, it boots into a dappled mauve background with not a SINGLE icon, toolbar (panel) or anything else showing, just that background screen. After trial and error, I found that alt f2 and alt f1 will bring up stuff but all completely useless for my needs. I don't even get anywhere to 'shut down' unless I press the PC's on/off switch!
 
After randomly rebooting, I occasionally get the Gnome 'panel' (I assume it's Gnome) but that only appears on subsequent reboots as and when it can be bothered.
 
Is there a known problem with version 10.10? It certainly 'feels' buggy!
 
So far, I am singularly unimpressed by Ubuntu and thus Linux.
 
Ian

---

### Post by Morbius1 on 2010-11-26
I think you have a bigger problem than just Samba. You've either got hardware that is just not compatible with it or there was something wrong with either the downloaded iso itself or with the burning to CD.

You might as a check look through this HowTo and check the iso and burned CD for errors to see if that's the source of your problems:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by merlinn31 on 2010-12-30
I'm having this exact same problem with 10.10.

root@Beast:~# service smbd restart
smbd start/running, process 1303
root@Beast:~# service nmbd restart
restart: Unknown instance:
root@Beast:~# service nmbd start
start: Job failed to start
root@Beast:~#

I'm using the same, generic config file from a working 10.04 configuration.

***Edit***
So, running /usr/sbin/nmbd -D manually lets me see the server in the networks.  I tracked this down to the upstart script in /etc/init/nmbd.conf.

The lines:

NMBD_DISABLED=`testparm -s --parameter-name='disable netbios' 2>/dev/null`
[ "x$NMBD_DISABLED" = xYes ] && { stop; exit 0; }

Seem to be the problem.  It looks like they're trying to test to see if netbios is disabled in smb.conf, but it's not working for some reason, although it works fine on my 10.04 install on another server.  I commented these lines out, because I obviously want NetBIOS to work.  After commenting the lines out:

root@Beast:~# service nmbd start
nmbd start/running, process 1476


***Last Edit, I swear***

apt-get install samba-common-bin samba4-common-bin 

installs testparm, which was apparently not included in the packages when I installed samba the first time.  No commenting of any upstart scripts is needed.


Hope this helps someone.

---

### Post by vrtx99 on 2011-01-10
Hi
 
i think the error is in 
[FONT=Courier New]/etc/init/nmbd.conf[/FONT]
 
WRONG CODE:
[FONT=Courier New]NMBD_DISABLED=`testparm -s --parameter-name='disable netbios' 2>/dev/null`[/FONT]
 
[FONT=Courier New]NMBD_DISABLED=`testparm[COLOR=darkgreen].samba3[/COLOR] -s --parameter-name='disable netbios' 2>/dev/null`[/FONT]
 
So it work fine with 
[FONT=Courier New]service nmbd start[/FONT]
[FONT=Courier New]:D[/FONT]

---

