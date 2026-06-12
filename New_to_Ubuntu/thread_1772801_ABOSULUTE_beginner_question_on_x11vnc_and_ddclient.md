---
title: "ABOSULUTE beginner question on x11vnc and ddclient"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by yeechoong on 2011-06-01
I'm sorry I've to ask this really beginner question as I've spend days of sleepless nights trying to configure my x11vnc and ddclient. I believe my settings are not correct and trying to follow various websites/versions is not helping either.

I'm using 11.04/natty.

What I'm trying to do
x11vnc - set it to localhost only, password auth, port 5901
I can't seem to find the config file to edit and also I don't understand where to put the configurations where some website says put it in ~/.x11vncrc.

On DDclient - I "think" its running with the setting but it does not update. I tried ddclient -refresh -force but it did not work

If anyone could walk me through step by step would be greatly appreciated.

---

### Post by krunge on 2011-06-02
You will need to start x11vnc manually at the command line, or put the command in an X session startup script somewhere. Are you doing this? Installing the x11vnc package does not mean the system automatically starts it for you... all it does it make the command available for use.

I suggest for now deleting ~/.x11vncrc and put all of the options on the x11vnc cmdline to avoid confusion.

Show your command line and x11vnc output.  And say what steps you have done to redirect the SSH port from your router to your desktop (I assume you want to use SSH secure tunnel since you said you want x11vnc to listen on localhost...) and what steps you have done to run ssh with a tunnel.

More info:

[indent][http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)[/indent]

---

### Post by yeechoong on 2011-06-03
Ok I think my ddclient is working fine as I tested it by switching off the modem and switching IP in the process

I was trying to follow these 2 guides 
[http://z.cs.utexas.edu/users/habals/blog/index.php/archives/22](http://z.cs.utexas.edu/users/habals/blog/index.php/archives/22)
[http://www.ubuntux.org/vnc-as-a-system-service](http://www.ubuntux.org/vnc-as-a-system-service)
and one other which I can't remember and as a result I don't remember where I put my password/config file. Are all these .xxx files hidden? Where do I put the configuration and which file should I edit to do that

My tunnel is fine as I'm currently tunneling to my server, running vnc service from prompt x11vnc -display :0 without password or anything, use VNC, then reboot the PC after using in case I mess up some config and prevent outsider from connecting to my vnc

---

