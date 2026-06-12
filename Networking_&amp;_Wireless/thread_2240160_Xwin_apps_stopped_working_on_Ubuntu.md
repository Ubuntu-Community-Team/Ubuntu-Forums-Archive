---
title: "Xwin apps stopped working on Ubuntu"
date: 2014-08-18
forum: Networking &amp; Wireless
---

### Post by bulrush2 on 2014-08-18
[LIST=1]
[*]Windows 7 using Putty 0.63 (using ssh2), and Xming 6.9.0.31, trying to connect to Ubuntu 14.04LTS. Xming running in "multiple window" mode started via Xlaunch. 
[*]Ubuntu 14.04LTS is running as a VM under VMware on a different machine. Openssh installed here and enabled, but I don't know if it's setup right. At least it worked on Friday. 
[/LIST]
 
I was logging on Friday and all was working fine. Today (Monday) I restarted my PC, I logged into Ubuntu, but cannot use nedit (an X window editor). From Ubuntu (I assume) I get an error "Invalid MIT-MAGIC-COOKIE-1". 

When I do "xhost" on Ubuntu I get a similar message: "Invalid MIT-MAGIC-COOKIE-1 keyxhost: unable to open display "my.ip.address.yep".

So, after some googling I found a webpage that said edit /etc/ssh/sshd_config" and to change KeyRegnerationInterval to 0. I did that and restarted the sshd with "sudo /etc/init.d/ssh restart". Still I can't use nedit and get the same error about MIT-MAGIC-COOKIE-1. 

Someone suggested using xhost on Windows to control what IP can access the Xming server, but I don't have xhost or xauth on my Windows intallation of Xming. 

Any ideas what I have to do to make nedit work from Ubuntu? I'm new to X11 stuff and Ubuntu administration. Detailed steps would be helpful. 

I have already googled and read a few pages, with no luck. xterm works running on Ubuntu, as I can execute nano editor, and CLI commands. But nedit does not work because of something wrong with MIT-MAGIC-COOKIE-1.

Thanks.

EDIT: Here's the bottom part of my Xming log: 
winInitMultiWindowWM - XOpenDisplay () returned and successfully opened the display.
winMultiWindowXMsgProc - XOpenDisplay () returned and successfully opened the display.
winClipboardProc - XOpenDisplay () returned and successfully opened the display.
AUDIT: Mon Aug 18 09:28:27 2014: 2252 C:\chuck\ubuntu\Xming\Xming.exe: client 5 rejected from IP 1.2.3.4
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Mon Aug 18 09:28:55 2014: 2252 C:\chuck\ubuntu\Xming\Xming.exe: client 5 rejected from IP 1.2.3.4
AUDIT: Mon Aug 18 09:29:32 2014: 2252 C:\chuck\ubuntu\Xming\Xming.exe: client 5 rejected from IP 1.2.3.4
AUDIT: Mon Aug 18 09:32:54 2014: 2252 C:\chuck\ubuntu\Xming\Xming.exe: client 5 rejected from IP 1.2.3.4
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1

---

### Post by tgalati4 on 2014-08-18
Try suppressing authentication with ssh -2 -Y username@computername and see if nedit works.

Since *nedit* uses Motif widgets, it's possible that it is also using a much older authentication protocol.  I presume nedit works locally--that is on the linux machine directly?  Did you try *gedit*?

Back when Motif widgets were popular (1980's calling, they want their buttons back), kerberos was the prominent authentication system:

tgalati4@Mint14-Extensa ~ $ apt-cache search kerberos
auth-client-config - pam and NSS profile switcher
curl - command line tool for transferring data with URL syntax
fetchmail - SSL enabled POP3, APOP, IMAP mail gatherer/forwarder
freeradius - high-performance and highly configurable RADIUS server
heimdal-dbg - Heimdal Kerberos - debugging symbols
heimdal-dev - Heimdal Kerberos - development files
heimdal-docs - Heimdal Kerberos - documentation
heimdal-multidev - Heimdal Kerberos - Multi-implementation Development
john - active password cracking tool
krb5-config - Configuration files for Kerberos Version 5
krb5-doc - Documentation for MIT Kerberos
krb5-locales - Internationalization support for MIT Kerberos
krb5-multidev - Development files for MIT Kerberos without Heimdal conflict

Perhaps you need kerberos on your system or pick another editor.

```
apt-cache search krb5
```

---

### Post by bulrush2 on 2014-08-19
> Since *nedit* uses Motif widgets, it's possible that it is also using a much older authentication protocol.


Thank you for a useful answer. Several people recommended not using nedit, but never said why. I have lots of experience of people recommending X without specifying a reason. Reasons help me understand the big picture. :)

I will try gedit, or kate, and see if I can find an editor that has multiple bookmarks (like when you hit ^-1 to go there) like PSPad. I was using PSPad but I need samba to work. But since Samba is not working, I'll have to use an XWin editor for now. 

I just realized my Ubuntu 14.04 64-bit is running on a server. The VM manager, vSphere, is running under Win 7 which is 32-bit. So I wonder if this is the root of some of my problems. From my post here: [http://ubuntuforums.org/showthread.php?t=2240302&p=13102325#post13102325](http://ubuntuforums.org/showthread.php?t=2240302&p=13102325#post13102325)

EDIT: I got nedit working, along with kate and jedit. Thank you.

---

