---
title: "SSH freezes after authentication"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by Peter Anselmo on 2008-07-23
Hi all, thanks in advance for the help.  I have a new laptop with Hardy installed.  When I'm on certain wireless networks (like my apartment) I can connect to any server using SSH just fine.  But if I'm on my work connection or at my friend's house, the SSH connection hangs after authentication.

Here is the output using the -vvv option:
```

$Username@$Hosts's password: 
debug3: packet_send2: adding 48 (len 65 padlen 15 extra_pad 64)
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
debug3: tty_make_modes: 6 255
debug3: tty_make_modes: 7 255
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
debug3: tty_make_modes: 38 1
debug3: tty_make_modes: 39 1
debug3: tty_make_modes: 40 0
debug3: tty_make_modes: 41 1
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
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env SHELL
debug3: Ignored env DESKTOP_STARTUP_ID
debug3: Ignored env TERM
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env WINDOWID
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env GNOME_KEYRING_SOCKET
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env GDM_XSERVER_LOCATION
debug3: Ignored env PWD
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env HISTCONTROL
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768

```

This is a huge probem as much of the reason I bought the laptop is to do sysadmin work.  Any help is appreciated.

---

### Post by LeonS on 2008-08-24
I am having the exact same issue. I can plug in the ethernet and ssh works just fine. I note that I have been wrestling with getting my BCM4312 802.11b/g (rev 01) wireless to work at all, and finally did by following these instructions: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

---

### Post by ElSlunko on 2008-08-25
Same issue with me. BCM4326 wireless card. DIR-655 DLINK router.

Everything works perfectly normal when I'm connected directly to the router. However, when I'm connected through wireless, all communication between my card and the network stops whenever I try to move files between my laptop and the server. All other SSH activity is normal, it's simply the file transfer that triggers the disconnect. I can't reconnect untill after the laptop is rebooted.

---

### Post by ElSlunko on 2008-08-25
Oops that was a typo. It's BCM4328 and I use ndiswrapper.

---

### Post by Iowan on 2008-08-27
> **ElSlunko said:**
> Oops that was a typo. It's BCM4328 and I use ndiswrapper.That's what the [EDIT] button is for. ;)

---

### Post by the7erm on 2008-08-27
I too am having difficulties getting ssh to work.

I have an BCM4312
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Everything else seems to work fine wireless.  I can surf, IM, irc, smb nfs you name it.  But as soon as I ssh it hangs right after login.

Looking at the auth logs it seems that it's a successful login.

I came across another post that mentioned "wl" in applications -> system -> hardware drivers, however if I disable this, and reboot I can't do anything at all on the net.

This is sorta frustrating :?

---

### Post by Xerampelinae on 2008-09-01
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237894](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237894)

Try going to restricted driver manager and unchecking "wl", then restart.  It worked for me, although I used ndiswrapper before and already had that set up.  You might have to set up ndiswrapper after unchecking "wl".

Otherwise, check that bug for more info..

---

