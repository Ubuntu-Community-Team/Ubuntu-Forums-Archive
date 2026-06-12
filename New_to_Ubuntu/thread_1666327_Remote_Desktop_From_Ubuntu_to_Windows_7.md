---
title: "Remote Desktop From Ubuntu to Windows 7"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by jarthda on 2011-01-13
Hello everyone.  I am a very excited new user of Ubuntu and have an installation on a notebook which I'd like to use as my main machine.  My windows 7 professional installation is on a huge bulky Dell and I'd get rid of it completley accept my Lexmark Z1420 wifi printer is not compatible with Ubuntu.  I've researched this and would like us to assume the possibility of using the lexmark with ubutu is not there (open to suggestions)
Onto remote desktop/vcn ubuntu -> windows.  Although I am new to Ubuntu I am a decent troubleshooter and definately know how to follow instructions.  I can NOT make anything work.  The machine are on a local network and I can file share and ping no problem.  But any remote desktop strategy is unable to connect.
 
I've tried rdesktop from the command line and made sure windows seven had remot desktop allowed.  I turned off the firewall and reduced things to zero security (i think - I'm more a dba than a sysadmin)  All the tutorials out there present this as a simple setup.  What can be going wrong?  
 
Again it's not necessarily essencial I have remote desktop, I want to print from ubuntu with my lexmarkz1420.  I do like remote desktop because I can use the old dell as a file/print server and get it out of my shoebox apt.   
 
Let me know any ideas.  this ecstatic new linux user will be happy!

---

### Post by davidmohammed on 2011-01-13
hi there and welcome to the forums.

You are correct - the lexmark is not supported by the vendor for linux.

There are probably two things you should check for rdesktop to work - one is the terminal service enabled and started.  Second - is the firewall turned off.

Have a read of [this thread]("http://ubuntuforums.org/showthread.php?t=1400518&page=2") for what sounds like your issues and possible resolutions.

---

### Post by jarthda on 2011-01-13
Remote Desktop is on and running on windows 7. The firewall is off. I've run nmap on ubuntu against the windows machin and port 3389 is open. ubuntu can see windows files and ping the machine but I still can not remote desktop in. :( what can the problem be?
 
rdesktop  results in ERROR:  Failed to open dispaly

---

### Post by CharlesA on 2011-01-13
Try using the terminal service client.

You might have to turn the security settings down on remote desktop on the Win7 box so that it'll let any version of remote desktop client connect.

---

### Post by jarthda on 2011-01-13
that has been done.  What is working is remote desktop client, which I just installed.  the performance is not that good but it does work so I doubt the problem with I'm still curious why the remote desktop viewer is on the windows side?  I'd still like to figure this out.  Sounds like my solution is buy a new printer or transfer documents to windows, walk down to the garage when I want to print.  I'll probably just do that.  At least I get that monster desktop out of my apt.
:)

---

