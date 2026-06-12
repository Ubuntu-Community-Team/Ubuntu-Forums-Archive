---
title: "Monitor blank at startup"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by japhyr on 2009-10-02
Hello,

I am trying to install ubuntu on an old Dell Optiplex GX260.  I was able to run ubuntu from the liveCD, and then I installed it.  It seemed to work, and I was able to connect to the internet.

I installed 8.04.3, and when I ran update manager it said I could install about 95 updates.  I started them, but many did not work.  After running the updates that worked, I still had 83 or so to go.

Now when I start up I end up with a blank screen.  I see the prompt to get into BIOS if I want to, and I am able to press esc at the grub option.  Booting in recovery mode, I am able to get to a command line.  I tried running updates from there, but it did not work.  I get a bunch of messages that start "Could not resolve 'security.ubuntu.com'.

Any recommendations?  Should I try a reinstall, or is there something to do from the command line?

---

### Post by JC Cheloven on 2009-10-02
> **japhyr said:**
> Hello,

I am trying to install ubuntu on an old Dell Optiplex GX260.  I was able to run ubuntu from the liveCD, and then I installed it.  It seemed to work, and I was able to connect to the internet.

I installed 8.04.3, and when I ran update manager it said I could install about 95 updates.  I started them, but many did not work.  After running the updates that worked, I still had 83 or so to go.

Now when I start up I end up with a blank screen.  I see the prompt to get into BIOS if I want to, and I am able to press esc at the grub option.  Booting in recovery mode, I am able to get to a command line.  I tried running updates from there, but it did not work.  I get a bunch of messages that start "Could not resolve 'security.ubuntu.com'.

Any recommendations?  Should I try a reinstall, or is there something to do from the command line?

I suspect two problems here:
1) the servers you're trying to connect may be down or bussy.
2) your system is messed by an uncomplete update

With internet connection, go command line and try  ```
sudo dpkg --configure -a
``` then update using aptitude (you told you know how to). Hope the servers serve you!

---

### Post by japhyr on 2009-10-03
How do I establish an internet connection from the command line, and how do I verify that the connection is working?

All I've used in the past is "/etc/init.d/networking restart".  I tried that, but then I couldn't ping google, so I don't think it was actually connected.

---

### Post by JC Cheloven on 2009-10-03
> **japhyr said:**
> How do I establish an internet connection from the command line, and how do I verify that the connection is working?

All I've used in the past is "/etc/init.d/networking restart".  I tried that, but then I couldn't ping google, so I don't think it was actually connected.

Yes, the easiest way to check if you have internet access from cli is to ping to a responsive site (I usually use ping  [www.ubuntu.com](www.ubuntu.com)). 

I would expect you to already have internet access when booting in recovery mode (please check that at recovery boot time you've choosen "netroot", which is shell root with internet connection, and that wou're wired to the router, not wireless).

Typing ```
ifconfig | less
``` should give you, among many other things, a line under eth0 beginning by something as 
"inet adr 192.168.1.36 ...(more follows)" 
The number is your assigned local ip, of course. If it appears, ping-ing to ubuntu should work as well. If you don't get internet this way, I can guide you to manual configuration, but it's a bit of a hassle though.

Anyway, I think you can run the "sudo dpkg --configure -a" part without internet, as most packages are stored locally (if installed via apt-synaptic). So please try out.

---

### Post by BinaryFeast on 2009-10-03
Honestly, I think this issue is because of updates no longer being provided for your version of Ubuntu. If you can, updating to 9.04 would solve the problem.

---

### Post by japhyr on 2009-10-05
> **JC Cheloven said:**
> I would expect you to already have internet access when booting in recovery mode (please check that at recovery boot time you've choosen "netroot", which is shell root with internet connection, and that wou're wired to the router, not wireless).

Anyway, I think you can run the "sudo dpkg --configure -a" part without internet, as most packages are stored locally (if installed via apt-synaptic). So please try out.

I don't see an option to choose "netroot".  The four options in the recovery menu are
[LIST]
[*]resume - resume normal boot
[*]dpkg - repair broken packages
[*]root - drop to root shell prompt
[*]xfix - try to fix x server
[/LIST]

If I choose the root option, I don't seem to have an internet connection.  Am I not getting the netroot option because it knows it can't connect for some reason?

If I choose dpkg, it tells me that it needs to get 82MB of archives.  I press y, and I get a bunch of "failed to fetch" messages.  The final error message is "unable to fetch some archives, maybe run apt-get update or try with --fix-missing".  Attempts at both of these end with more "failed to fetch" messages.

Any suggestions, or is reinstalling best?

---

