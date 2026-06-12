---
title: "Hotel Internet Connection and SSH"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by wolf08 on 2007-11-23
I'm having a problem with using SSH from my hotel's internet connection. It's a 'stayonline' (lodgenet) system where guests get free access. 

When I try and ssh to my home box, I am able to connect and get in, but the connection freezes after ~20 seconds, regardless of what I am doing in the ssh. I have found that if I try and start nano, vim, or use cat, etc.... it freezes instantly. I've also found that I can't visit certain websites (ie the individual tribalwars servers en9.tribalwars.net, etc...) and that sometimes in my browser I get snapped back to the original hotel logon page.

I *think* what is happening is that after a certain amount of jibbersish data (an ssh connection would seem like that, no?) the hotel's server resets my computer's connection and forces me to relogin, which would kill the current ssh session. 

So, can anyone provide me with any suggestions or help?

Thanks,

Wolf08

---

### Post by mellowd on 2007-11-23
Can you telnet to port 22? You won't open a full connection of course but it should tell you if you can't connect

---

### Post by timcredible on 2007-11-23
you probably need to agree to some sort of legal baloney before the connection will be maintained.  try going somewhere in your browser first, see if you get a screen that says you need to agree to something, agree to it, then the connection should stay alive.

---

### Post by wolf08 on 2007-11-23
> **mellowd said:**
> Can you telnet to port 22? You won't open a full connection of course but it should tell you if you can't connect

Yes, I can connect. I was probably way too confusing in my first post. Here is what happens:


1. I connect to the hotel's wireless AP (stayonline)
2. I open up konqueror and try and visit a website
3. The hotel's page pops up, I say "free access" and then I can browse websites
4. I open up my terminal, and 'ssh username@my-home-server' 
5. I'm now ssh'd into my home server. 

From this point, I have ~20 seconds before the ssh connection freezes. If I try to open any configuration files or view things with cat, less, etc... it also freezes. Once this happens, I have to kill the terminal (ctrl-c doesn't work). However, I _can_ reconnect right away (for another 20 seconds).

Why might this be happening? It doesn't matter whether I use ssh or putty or my n800, it's all the same.

---

### Post by wolf08 on 2007-11-23
> **timcredible said:**
> you probably need to agree to some sort of legal baloney before the connection will be maintained.  try going somewhere in your browser first, see if you get a screen that says you need to agree to something, agree to it, then the connection should stay alive.

Well, I did do this initially. I think for some reason my connection status is being reset. bah!

---

### Post by kevdog on 2007-11-23
When you connect with ssh can you connect with the -dd switch to produce some debugging output to see why exactly the connection is dropping?

---

### Post by wolf08 on 2007-11-24
ssh -dd user@host didn't work. Did you mean -vv?

using 'ssh -vv user@host' and then running something verbose like 'find' froze it again, but with no output. 

If it helps, this is what the debug output showed between the password auth and login (it displayed nothing after login, and things like 'ls' didn't show any debug output either)

```
user@host's password:
debug3: packet_send2: adding 48 (len 62 padlen 18 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug3: tty_make_modes: 1 3
debug3: tty_make_modes: 2 28
debug3: tty_make_modes: 3 127
debug3: tty_make_modes: 4 21
debug3: tty_make_modes: 5 4
debug3: tty_make_modes: 6 0
debug3: tty_make_modes: 7 0
debug3: tty_make_modes: 8 17
debug3: tty_make_modes: 9 19
debug3: tty_make_modes: 10 26
debug3: tty_make_modes: 12 18
debug3: tty_make_modes: 13 23
debug3: tty_make_modes: 14 22
debug3: tty_make_modes: 18 15
debug3: tty_make_modes: 30 0
debug3: tty_make_modes: 31 0
debug3: tty_make_modes: 32 0
debug3: tty_make_modes: 33 0
debug3: tty_make_modes: 34 0
debug3: tty_make_modes: 35 0
debug3: tty_make_modes: 36 1
debug3: tty_make_modes: 37 0
debug3: tty_make_modes: 38 0
debug3: tty_make_modes: 39 0
debug3: tty_make_modes: 40 0
debug3: tty_make_modes: 41 0
debug3: tty_make_modes: 50 1
debug3: tty_make_modes: 51 1
debug3: tty_make_modes: 52 0
debug3: tty_make_modes: 53 1
debug3: tty_make_modes: 54 1
debug3: tty_make_modes: 55 1
debug3: tty_make_modes: 56 0
debug3: tty_make_modes: 57 0
debug3: tty_make_modes: 58 0
debug3: tty_make_modes: 59 1
debug3: tty_make_modes: 60 1
debug3: tty_make_modes: 61 1
debug3: tty_make_modes: 62 0
debug3: tty_make_modes: 70 1
debug3: tty_make_modes: 71 0
debug3: tty_make_modes: 72 1
debug3: tty_make_modes: 73 0
debug3: tty_make_modes: 74 0
debug3: tty_make_modes: 75 0
debug3: tty_make_modes: 90 1
debug3: tty_make_modes: 91 1
debug3: tty_make_modes: 92 0
debug3: tty_make_modes: 93 0
debug1: Sending environment.
debug3: Ignored env KDE_MULTIHEAD
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env DM_CONTROL
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDM_MANAGED
debug3: Ignored env GTK2_RC_FILES
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env GS_LIB
debug3: Ignored env WINDOWID
debug3: Ignored env KDE_FULL_SESSION
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env KONSOLE_DCOP
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env KONSOLE_DCOP_SESSION
debug3: Ignored env PWD
debug3: Ignored env KDE_SESSION_UID
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env HISTCONTROL
debug3: Ignored env HOME
debug3: Ignored env SHLVL
debug3: Ignored env XCURSOR_THEME
debug3: Ignored env LOGNAME
debug3: Ignored env LESSOPEN
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env _
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 131072

```

---

### Post by jflaker on 2007-11-24
> **timcredible said:**
> you probably need to agree to some sort of legal baloney before the connection will be maintained.  try going somewhere in your browser first, see if you get a screen that says you need to agree to something, agree to it, then the connection should stay alive.

I believe you must keep the browser open for the extent of your online time.  Once you agree to the TOS, you will be allowed to do what you need. 

IF you continue to have issues, you may need to contact the hotel's help desk to get an alternate connection as there is usually some level of security on the network where some ports may be blocked as they are not considered normal.

(As helpdesk at my last job, I had to help 3 remote sales people connect from their hotel and ports were indeed blocked)  One other salesperson never opened a browser and therefore was not allowed internet access)

---

### Post by wolf08 on 2007-11-24
Well, I have had my browser open. I'll be calling the support desk, but then again, I do leave tomorrow morning which means I'm not sure how much help it'll be.

A quick addendum to the debug logs. I left the 'frozen' session open for a while, and when I came back tried a 'ctrl-c' again. This time it did kill the client with this log:

```
debug1: channel 0: free: client-session, nchannels 1
Read from remote host wserver.chatonka.com: Connection reset by peer
Connection to wserver.chatonka.com closed.
debug1: Transferred: stdin 0, stdout 0, stderr 114 bytes in 6436.3 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status -1
astromme@Lentren:~$                 
```

---

### Post by kevdog on 2007-11-24
Not sure what is going on -- Id be curious to see if this behaivor happens if you go to the local coffee shop and use their free wifi.

---

### Post by wolf08 on 2007-11-24
Well, I do have my n800 with me. And, when I connect via the GPRS of my phone, I can ssh in to my home computers just fine. It's just that it's hard to use the on screen keyboard for any real work.

And, this is interesting....

It looks like the hotel is running a transparent proxy to monitor the use of the internet. Also, it seems to have a very restrictive firewall, which might be the source of the problem.

---

### Post by rabil on 2008-05-24
i'm at an hotel now with almost exactly the same problems. i'm using fedora 8. I hit accept the agreement but the page never loads to continue yet I can ssh to my home computer - but it always freezes after 20 seconds or so. My Nokia N810 connects fine - i'm typing this on it now. Same problem when I stayed here before - IT could not figure it out. My F8 laptop connects every where else. Help!!!

---

### Post by rabil on 2008-05-25
OK, I found a post on another site (Unix Forum) that mentioned tcp_window_scaling as the culprit. To turn it off (as root in a terminal shell):

echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

As soon as I did this, I could get to a web page to get access (some hotels you have to pay, others give you an access code). I had to talk to stayonline tech support to get me connected without having to pay twice (I was already connected using the Nokia N810). Tech Support said that Vista has the same problem.

This worked on Fedora 8 and I'm assuming it will work on Ubuntu.

I hope this helps someone.

---

