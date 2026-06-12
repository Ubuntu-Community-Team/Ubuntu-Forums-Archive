---
title: "Can not ssh with X11 forwarding"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by khuevu on 2013-09-05
Hi, 
I am using a Mac to remotely log in to my Ubuntu 12 computer. 
I have enable X11 forwarding in my Ubuntu machine: In /etc/ssh/sshd_config: 
```
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalHost no
```

xauth is installed: 
```
$ which xauth
/usr/bin/xauth
```

But when ssh -vvv -X user@ubuntumachine
There is no Requesting X11 forwarding in the debug trace. 

```
...
debug1: Authentication succeeded (password).
Authenticated to 192.168.1.115 ([192.168.1.115]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug2: channel 0: request pty-req confirm 1
...
```

And when invoking a gui program like "firefox &", I see "Error: no display specified"

Then I explicitly set the DISPLAY in the client machine before ssh in. 

```
export DISPLAY=192.168.1.117:0.0 #my mac ip
```

Then ssh -X into the Ubuntu machine again: 

```
uthenticated to 192.168.1.115 ([192.168.1.115]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
[COLOR=#ff0000]debug2: Checking for xauth using xauth -f /var/folders/9s/s5hl5w4x7zjdjkdljw9cnsrm0000gn/T//xauth_test exit > /dev/null 2> /dev/null

debug1: No xauth program.
Warning: No xauth data; using fake authentication data for X11 forwarding.
debug1: Requesting X11 forwarding with authentication spoofing.[/COLOR]
debug2: channel 0: request x11-req confirm 1
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug3: Ignored env VIRTUALENVWRAPPER_PROJECT_FILENAME
debug3: Ignored env TERM_PROGRAM
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env TMPDIR
debug3: Ignored env Apple_PubSub_Socket_Render
debug1: Sending env LC_ALL = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env USER
debug3: Ignored env COMMAND_MODE
debug3: Ignored env VIRTUALENV_USE_DISTRIBUTE
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env __CF_USER_TEXT_ENCODING
debug3: Ignored env Apple_Ubiquity_Message
debug3: Ignored env WORKON_HOME
debug3: Ignored env PATH
debug3: Ignored env VIRTUALENVWRAPPER_HOOK_DIR
debug3: Ignored env C_INCLUDE_PATH
debug3: Ignored env PIP_VIRTUALENV_BASE
debug3: Ignored env PWD
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env ITERM_PROFILE
debug3: Ignored env PS1
debug3: Ignored env PIP_RESPECT_VIRTUALENV
debug3: Ignored env SHLVL
debug3: Ignored env COLORFGBG
debug3: Ignored env HOME
debug3: Ignored env ITERM_SESSION_ID
debug3: Ignored env LOGNAME
debug1: Sending env LC_CTYPE = UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env DISPLAY
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
[COLOR=#ff0000]debug2: X11 forwarding request accepted on channel 0[/COLOR]
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
```

When entering "firefox &"
i have the following error: 

```
* (firefox:16274): WARNING **: Command line `dbus-launch --autolaunch=ea7e29098a107107d153b6b70000000b --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 50891
debug2: connect 192.168.1.117 port 6000: Connection refused
connect 192.168.1.117 port 6000: Connection refused
debug1: failure x11
Error: cannot open display:
```

Any pointer ? 

Thank you very much.

K.

---

### Post by TheFu on 2013-09-05
This is probably a stupid question, but does OSX support X/Windows by default?  I didn't think so.  You need an X/Server running on your Mac.

---

### Post by Lars Noodén on 2013-09-05
OS X needs X11 support added.  Depending on which version you have, it is either on the installation DVD or via the App Store.  In the latter, I think it is part of Xcode.  You'll have to check to be sure.  They seem to be closing things off steadily for years now.  

However, once you have X11 installed, it will launch automatically when you need an X server in the later versions.  In the older versions, you'll have to launch it manually and then connect via SSH from within the special console.

---

### Post by houstonbofh on 2013-09-05
[http://www.cs.umd.edu/faq/mac.html](http://www.cs.umd.edu/faq/mac.html)
Note that 10.8 and later need you to install software.

More on what you are trying to do, and why you should not.
[http://dyhr.com/2009/09/05/how-to-enable-x11-forwarding-with-ssh-on-mac-os-x-leopard/](http://dyhr.com/2009/09/05/how-to-enable-x11-forwarding-with-ssh-on-mac-os-x-leopard/)

---

