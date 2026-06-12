---
title: "ssh -X: can't open display"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by tospo on 2007-12-05
Hi, 

I know variations of this question are asked all the time but somehow I couldn't find a solution for my problem anywhere so I'll just give it a go here:

I am simply trying to get x-forwarding in ssh to work on my newly installed Kubuntu box and I get the infamous "can't open display" error.

I know that the remote machine (Centos server) is correctly configured for x forwarding because I access  it all the time from yet another machine (Debian) and it works. 

When I use this command on the Kubuntu machine
```
ssh -X USER@REMOTEHOST
```
I can log on to  the Centos machine but when I launch an application like xterm on the remote machine  I get:
```
xterm Xt error: Can't open display: client-xx-xx-xx-xx.cmbg.adsl.virgin.net:0.0
```

Virgin.net is my ISP and I am using a Netgear DG834 router. I thought that the router is blocking the port but even when I allow all inbound and outbound traffic in the router's firewall settings I get the same problem. I also tried 
```
xhost +
```
on the local machine and that too didn't have an effect.

Could it be that my ISP is blocking this or is there anything else (probably blatantly obvious to anybody but me :-? ) that I have overlooked?

I should probably mention that the Debian box from which the x-forwarding does work is not on my home LAN and also not on the same network as the Centos machine to which I need access. I hope this makes sense....

Thanks for your help!!

---

### Post by Friek on 2007-12-05
It seems to me like you're doing this:
* Log in to the remote host using ssh -X
* Set DISPLAY to yourip:0.0
* Run xhost + and startup the application on the remote box.

That's not the way to go ;)
You should be doing something like:
```
ssh -X remotehost xterm
```

Display settings will be dealt with by the remote sshd.
Besides, if you're able to ssh into the box, the X connection work regardless of any firewalls.

Good luck :)

---

### Post by tospo on 2007-12-05
Hi Friek,

Sorry if that was a bit unclear. What I do is simply
```
ssh -X user@remotehost
```

The ssh works, so I am then on the remote machine and start xterm, xclock, firefox, whatever and I get the "can't open display" error. 
I haven't set the DISPLAY environment variable on either machine.
As a "last resort" I tried the "xhost +" command once (on local machine) and then logged into the remote host with the above ssh command but I got the same error.

I must admit that I know very little about networking but I heard somewhere that it is possible to specifically block x-forwarding with firewalls. Is that not true?

Thanks for your help!

---

### Post by Friek on 2007-12-05
Nope, unless the firewalls are enable to analyze the ssh conversations :)
You can run ssh -v -X user@host and check if the remote sshd actually allows to use forwarded X11.
And run echo $DISPLAY on the remote host to see if the DISPLAY env var is set. If it's not, the X11 forward failed somehow (which is probably mentioned in the debugging output).

I assume you are running the ssh command from some sort of xterm.

---

### Post by reckless2k2 on 2007-12-05
yeah this is pretty simple. you are already running on :0. More than likely you are running a GUI already on that machine you are on. hence the running on :0 error. you need to get to :1 and run it from there. so you will have :0 for local pc and :1 for remote machine. do this:

at current desktop:

ctrl+alt+f2 (this will switch you to another console)

login as normal and the command line

then start an x session on :1

```
xinit -- :1
```

now in that box ssh with X to the remote machine

```
ssh -X remoteip
```

depending on your X setup start your gui and you'll be fine

startx or gnome-session or startkde or startfluxbox etc

now you'll have remote machine on ctrl+alt+f9 and local machine on ctrl+alt+f7

BANG!!!! mark is solved. MARK IT

---

### Post by reckless2k2 on 2007-12-05
side note.....i admin my centos server this same way IF i need a GUI but it is suggested in general to not really use GNOME over X. there are disconnect issues and such. i don't know all the particulars but in general it's not good to GNOME over ssh. i would suggest fluxbox as that is probably the best usable GUI over ssh in LAN or across WAN. other than that you can run KDE without much issue too but not over WAN. over WAN you want to run with compression:

```
ssh -X -C hostname/ip
```

some suggest trusted ssh but you have to comment the sshd_config file then you can run:

```
ssh -Y -C hostname/ip
```

anyway, point is that GNOME over ssh is not good idea. things don't term right then you have issues.

---

### Post by Friek on 2007-12-05
There is no need to run an additional X server. This is only useful if you're running the window manager at the remote box, which is obviously not the case.

Now that I think of it, it's very odd that if a DISPLAY gets set at ssh login, it points to yourhost:0.0. By default (when no other user has logged in with X11 forwarding), the display is set to localhost:10.0. If it's not set at all, or to yourhost:0.0 anyway, try telnetting to localhost at port 6010 to verify if the X11 forward succeeded.

---

### Post by reckless2k2 on 2007-12-05
tospo,

just do what i said. if you are on kubuntu on your LAN running your kubuntu gui and you just open a plain ole konsole window inside your running kubuntu desktop, you're going to get :0 errors. keep :0 running and jump to another console and you'll be fine. 

if you boot you kubuntu box to runlevel 3 with commandline only and do the deal then there's no :0 running. 

again, across WAN you should be using compression as well. i would assume that port 22 is open at the remote point as well. 

if you follow my gimmick and it'll work soldier. 

i'm not sure how friek doesn't see that. tospo is using :0 local.

---

### Post by Friek on 2007-12-05
I am not seeing it because I do it my way every day:
```
johan@laptop:~$ echo $DISPLAY
:0.0
johan@laptop:~$ ssh -X granny
johan@granny:~$ echo $DISPLAY
localhost:10.0
johan@granny:~$ xterm

```

And wow, an xterm pops up ;)

Now explain to me why the additional X session is needed.
('granny' is a remote box not even close to my own network)

---

### Post by reckless2k2 on 2007-12-05
i'm not trying to start a fight. he said something about xterm....yadda..working fine but he can't run a full GUI. 

my suggestion is to try it. if he doesn't get any farther, then trying my way won't hurt. your way is right for regular or most x programs but a full desktop needs another session. 

how about we all hold hands, sing, and try it. i think you can run a desktop environment using the info i suggested. your way will pull some programs. it won't work for full gui. i could be wrong but his :0 issue is because he already has a desktop running at :0. just and run at :1 and he will be fine. 

hold hands, maybe sing together some, and then try the commands. don't hate me.....i'm reading the X over SSH tutorial. hahaha

don't hate the playa. jahjahaha

---

### Post by Friek on 2007-12-05
:)
Well, the OP said it works alright on a remote debian box, so if it doesn't work with exactly the same procedure on the centos box, the centos box must be misconfigured somehow..

---

### Post by tospo on 2007-12-06
No fighting please :cool:
thanks for all your help. I will try your suggestions later when I get home.
I run the ssh command in a KDE konsole window. I know that the remote machine supports x forwarding because I use it from another machine all the time. 

I tried to run ssh in verbose mode but couldn't find anything in the output that would give me a hint (but then again I probably don't know enough about it). If is still doesn't work I'll post the output here.

I don't actually want the full remote desktop. I just need to run some programs like Emacs (hate to do it in command-line mode) and firefox (to access some local content) etc.

OK, I'll report back when I had a chance to try it out. Thanks for your help!!!

---

### Post by tospo on 2007-12-06
oh-oh, I have a confession to make: I have been trying to log into the wrong machine - I can' t access the config files on that one but I doubt that it is configured for x-forwarding - DUH ](*,) ](*,) ](*,)

I was SO sure this was the correct one.

Now that I am using the correct machine it all works fine (as Friek suggested and as I also thought it should). Ahem....

reckless2k2, I haven't had time yet to try out your full-remote desktop solution. Sounds interesting although normally, as I said, I only need a few windows and not a full desktop but I will give it a go when I have some time to play.

Thank you both for your help.

---

