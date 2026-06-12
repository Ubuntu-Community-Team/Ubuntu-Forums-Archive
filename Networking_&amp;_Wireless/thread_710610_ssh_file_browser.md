---
title: "ssh file browser"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by dhap on 2008-02-28
I am connected to the server in our lab via vpn. But how do I browse files from the server?
With ssh I can do it in a console but not with the file browser.

---

### Post by sancho panza on 2008-02-28
Yes you can use ssh...and you dont need vpn to just browse the files on an ssh server.
In the file browser (nautilus), use GO>Location and type
sftp://username@server_address/folder/
and book mark it in nautilus. Then you should be able to browse all the files on the server thru ur file browser.

---

### Post by dedmonds on 2008-02-28
Thanks, sancho panza. I've been using ssh and sftp solely through the command line interface. I didn't realize Nautilus could do this.

---

### Post by Eiríkr on 2008-02-28
If this answers your concerns, please don't forget to mark the thread as SOLVED in the Thread Tools dropdown at the top of the page.  

Cheers,

Eiríkr

---

### Post by vagus on 2008-02-29
Hi,

I've been trying to do the same, but Nautilus throws up an error ("Nautilus cannot display ssh://...... please try another viewer") after typing the password in. ssh works fine via the command line.  I have tried deleting the "known_hosts" file, in case it was a key problem for ssh, but no joy. Nautilus works fine with ftp but not ssh. Any ideas?

Cheers :-)

---

### Post by dhap on 2008-02-29
It worked for me,thanks a lot. Should I close the thread as solved, as I was the one started it? Or should I leave it open as I see other unsolved questions.

---

### Post by Whiffle on 2008-02-29
> **vagus said:**
> Hi,

I've been trying to do the same, but Nautilus throws up an error ("Nautilus cannot display ssh://...... please try another viewer") after typing the password in. ssh works fine via the command line.  I have tried deleting the "known_hosts" file, in case it was a key problem for ssh, but no joy. Nautilus works fine with ftp but not ssh. Any ideas?

Cheers :-)


try doing sftp:// instead of ssh://

---

### Post by Lacrimstein on 2008-02-29
You can also setup NFS (pretty secure as well), mount the remote machine to a directory on your computer, and just use your regular file browser to navigate it

Or, you can tunnel X through ssh, like this:

ssh -X -C [user@]hostname              

( -C tells ssh to compress the transferred data, not necessary but is usually faster)

and then run your file manager from the ssh session

---

### Post by sancho panza on 2008-03-02
> **Whiffle said:**
> try doing sftp:// instead of ssh://

Even with sftp:// , I have occasionally encountered this issue of nautilus not being able to open the location. But thats a rare occurence, and I'm not sure if its a problem at the client or server end.

---

### Post by kevdog on 2008-03-02
In terms of security, whats the difference between sftp and ssh?

---

### Post by Eiríkr on 2008-03-03
sftp is just FTP over SSH.  From the sftp man page:
> **sftp** is an interactive file transfer program, similar to ftp(1), which performs all operations over an encrypted ssh(1) transport.  It may also use many features of ssh, such as public key authentication and compression.  **sftp** connects and logs into the specified _host_, then enters an interactive command mode.

Cheers,

Eiríkr

---

### Post by Eiríkr on 2008-03-03
> **sancho panza said:**
> Even with sftp:// , I have occasionally encountered this issue of nautilus not being able to open the location. But thats a rare occurence, and I'm not sure if its a problem at the client or server end.

To find out better which end is at issue, next time you run into this, open a terminal and try:
```
ssh -v -v -v USERNAME@REMOTE_MACHINE
```
Replace USERNAME with the username at the remote machine you're logging into, and REMOTE_MACHINE with the remote hostname (or IP address if the hostname is not in your /etc/hosts file and you're not running DNS somewhere on your network).  As noted previously, sftp is basically FTP over SSH, so when you have connection problems, either SSH is having problems (which you'll find by trying the CLI command above), or the folder specified doesn't exist, or the folder specified doesn't have the right permissions assigned for your username.  

HTH,

Eiríkr

---

### Post by vagus on 2008-03-03
sftp does not work either, the same error. I might have to take the NFS route. I guess I just wanted to figure out why the secure file transfer in Nautilus is not working for me (and I am one of those people who wants their system to be working perfectly ;-) ). Am I doing something silly, I mean do you know of any settings or something that might be off to cause this error in Nautilus? 

It seems to throw an error only when I use the secure connection. ssh still works on the command line. I have used the -X option before, but it tends to be very slow in response. 

Cheers.

---

### Post by vagus on 2008-03-03
Sorry Eirikir, forgot to mention the results of what you suggested! It gave a long output: I am not sure what I am looking for, so hope you don't mind if I put the debug list here (well some of it!) :-)

This is some of the stuff after I enter the password. I thought this might be relevant as the problem in Nautilus occurs after I enter the password. I have omitted some debug lines that contain stuff about tty_make_modes. 

Thanks for your help :-)

debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).

debug1: Sending environment.
debug3: Ignored env SSH_AGENT_PID
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
debug1: Sending env LANG = en_GB.UTF-8
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
debug2: channel 0: rcvd adjust 131072

---

