---
title: "run gtk command as logged in user on remote system ssh?"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by iansane on 2010-08-03
Hi,

I am trying to start teamviewer through ssh. It seems to start but doesn't actually start. I found the problem I think but don't know how to get around it. When I try gksudo teamviewer I get error could not open display.

I'm assuming this is because I'm in a ssh terminal so of course gui's can be run.

What I want to do is have the remote machine start teamviewer so I tried creating a script in the home directory and running it through ssh but it still tries to open it in ssh.

The purpose of this is so if I forget to start teamviewer  before I leave home, I can still use ssh to get it started for a remote desktop session. I also have freenx but it was being blocked by my companies firewall the other day so I needed to be able to start teamviewer as if someone was at my keyboard typing in "teamviewer" 

Is there a way to run commands as the user logged in locally rather than as the user logged into ssh?

Thanks

---

### Post by iansane on 2010-08-03
If I run a script that runs a cron job to start teamviewer after a few seconds and then close the ssh before it runs will my system run the job still?

I don't understand why running a script that is in the home directory tries to run through ssh instead of just running on the remote system.

---

### Post by iansane on 2010-08-06
bump

anyone here ever run a gui on the remote machine but send the command through ssh?

---

### Post by nothingspecial on 2010-08-06
You need to run screen in your ssh session

Then  ```
export DISPLAY=:0.0
```Then guis that you launch from your ssh will open on the remote computer.

Then press Ctrl A then D to detach your screen session

---

### Post by Zorgoth on 2010-08-06
ssh -X user@host

Best -- Command -- Ever

(with the exception of "echo emacs | ssh -X user@host")

---

### Post by iansane on 2010-08-06
Neither of those two way makes any difference.  

I type teamviewer which works locally in terminal and it acts like it's working but nothing ever happens on the remote machine. 

Also I always get this "you have new mail in /var/mail/lotus" (lotus is my user name that's logged in.)

Can one of you give me a full example to make sure i"m not missing something?

Thanks

---

### Post by nothingspecial on 2010-08-07
I don't know what teamviewer is, but

test this on a lan

From your remote machine

```
ssh -X -C -c blowfish user@address_of_host
sudo apt-get install screen
screen
export DISPLAY=:0.0
teamviewer
[Ctrl A]
[D]
```

---

### Post by iansane on 2010-08-07
Thank you nothingspecial! :-)

The first time I tried it I left out the colon in front of the 0
so it was a syntax error on my part. Sorry about that.

This is working perfectly.

```

ssh -X me@mydomain.com
screen
export DISPLAY:0.0
teamviewer

```

teamviewer is a remote desktop app that uses https and requires the session be started on the remote computer to be able to connect. I generates a ID based on the computers mac address so you can keep the ID because it will always be the same.

I use it on my home computer because my place of work seems to be blocking freeNX.

Now that I can start it from ssh I don't need to worry about the security of having a open session running just in case I need it. And what started all this is, I forgot to start the session before leaving home one day and the only way I knew to get to my home computer was ssh but I needed remote desktop.

Thank you very much.

---

### Post by nothingspecial on 2010-08-07
No problem

:popcorn:

---

