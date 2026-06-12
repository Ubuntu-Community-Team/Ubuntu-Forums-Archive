---
title: "Is SSH an needed item"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by jmore9 on 2008-05-06
I keep getting 75.125.234.250 TCP SSH denied connections in the firestarter log do i need SSH for anything ?  I understand it is installed bu default.
Thanks for your time in advance.

---

### Post by jetsam on 2008-05-06
Ssh isn't needed if you don't want it, but the log doesn't necessarily mean you have it.

The firestarter log probably means that firestarter/iptables is doing just what it's supposed to and denying an unwanted ssh connection from that ip address.

I don't think that ssh is installed by default.  This command in a terminal will list openssh-server or openssh-client if you have them installed:
```
dpkg --list "*ssh*" | grep ii
```

It should output nothing if they aren't.  

You could also just search for ssh in Synaptic to see if they're installed or not.

---

### Post by jmore9 on 2008-05-06
This is what i get when i run the script provided

jeff@c-71-205-135-55:~$ dpkg --list "*ssh*" | grep ii
ii  openssh-client                             1:4.7p1-8ubuntu1                    
secure shell client, an rlogin/rsh/rcp repla
jeff@c-71-205-135-55:~

Does this mean it is running or just being used by some other installed software ?

---

### Post by jetsam on 2008-05-06
Ok.  That's the client software only.  I guess the client side is installed by default.  It isn't dangerous because it won't accept incoming connections.  It's for connecting to other computers from yours.  

If it makes you uneasy, you can remove it with
```
sudo apt-get remove openssh-client
```

I don't think there's any harm either way.  You can always install it again if you need it in the future.  It is a handy thing to have around.

**Added**:  Oh, and "dpkg --list" lists installed and not installed packages, not running programs.  "pgrep -l ssh" will show you if anything with ssh in the process name is running.

---

### Post by jmore9 on 2008-05-06
I was just wondering because i am switching over to kubuntu from winxp for everything but mu HDTV card so it was different from winxp.  Thanks a lot.  Also how do you mark this as solved ?  Just edit the title of the first one ?

---

### Post by jetsam on 2008-05-06
Glad I could help.  

You used to mark things as solved by using the thread tools drop down menu, but I think that's gone away since the forum did an upgrade.  I suppose editing the title would work.  Can you do this, though?  

Hopefully they'll solve the [solved] thing sometime soon.  :)

---

### Post by jmore9 on 2008-05-07
ok thanks thats what i will do .  Thanks for your help.

---

