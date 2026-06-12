---
title: "i can ssh, not vnc"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by ninjaprawn on 2007-05-18
hi,
as the title suggests, i can get an ssh connection to bash, but i can not get vnc to work atall!!!!!!

my problem,
im vnc'ing from a win xp pc behind a proxy(8080), which only allows outbound traffic for ports 80, and 443!
im going to ubuntu feisty, which only has a software firewall! and has an external ip!

what ive done so far,
ive set the sshd to port 443, this connects and i login!, i then tell realvnc or tightvnc to connect 2 127.0.0.1:8080, and i get nothing!

help? i dont think i can set vnc to run on port 443, cos ssh is already there! is that right?? if so, how do i go from the ssh connection on 443, to the vncserver on, say 5900,???

im using putty for the ssh!

any ideas appreciated!

thanks

---

### Post by calraith on 2007-05-18
You can always tunnel VNC over your SSH connection.  If you're using PuTTY, the Tunneling section is down near the bottom of the configuration list.  Set the following settings:
```
source: 5900
destination: localhost:5900 (destination is from the point of view of the SSH server)
```and leave all other settings as default.  Then, from Windows, when you launch VNC Viewer, connect to localhost.  Let me know if you need more detailed instructions.

=)

---

### Post by ninjaprawn on 2007-05-18
ive already got a tunnel, its from 8080 on the win xp box, to myip:443

the proxy i have only lets out on 443 and 80!

do u mean another tunnel aswell? going from 443 to 5900??

if that works, then i dont no why i didnt try it!!

or do u mean on the ubuntu box from 443 to 5900, so i would have to have the tunnel set up on the ubuntu box first to direct 443 to 5900??

thanks

---

### Post by calraith on 2007-05-18
You have SSH running on port 443.  When you establish the tunnel, you set up something like this:
```
Source >-- 443 --> Destination
```Think of it like a garden hose.  You can have as many ports as you want tunneled through SSH, and during the trip through the garden hose between PuTTY and the SSHD, it all gets funneled into the single port, port 443.  Since VNC runs on port 5900 for display :0 (5901 for display :1, etc), think of it this way:[INDENT]port 5900 >-- ssh (port 443) --> target:5900 (where target is the relationship of the VNC server to the SSH server, in this case, "localhost:5900")
port 5901 >-- ssh (port 443) --> target:5901
port 21 >-- ssh (port 443) --> target:21
[/INDENT]Since you're able to connect with PuTTY, the garden hose through the proxy is already taken care of.  SSH takes care of the rest of the translation.

---

### Post by ninjaprawn on 2007-05-18
as i understand, in putty, i set the target to myip:443  -> then in the tunnels part, i have a tunnel which goes from 8080 -> myip:443,  then another tunnel from 443 -> myip:5900?

is that right?

the tunnel from 8080 -> myip:443 gives me the sshd
then the 2nd tunnel that is set from 443 -> myip:5900  just carries the vnc down the first tunnel to 443, then to port 5900?

or

do i set the first tunnel  from 8080 -> myip:443, then the 2nd  443 -> localhost:5900?

im a bit confused?

---

### Post by calraith on 2007-05-18
On the Session page, enter the address of the SSH server to which you'll be connecting as myip:443.  In the Tunnels page, enter the source as "5900," and the destination as "localhost:5900."  Nothing more, nothing less.  Port 8080 shouldn't be needed anywhere.

---

### Post by ninjaprawn on 2007-05-21
sorry, i have to go from the xp machine on port 8080 thru a proxy, the proxy only allows 443 and 80 connections, so i go from port 8080 -> myip:443 for the ssh, then i need to jump from 443(ssh) to 5900 for the vnc!

is this possible??

ive got in the tunnels, 
tunnel 1 - source 8080, destination myip:443
then i just added another tunnel
tunnel 2 - source 443, destination localhost:5900

i get to bash,
then go to vncviewer.exe, and try to connect to 127.0.0.1:8080, i get a small box saying
tightvnc connection
connecting to 127.0.0.1::8080...
status: connection established.
then there is a hide button

nothing else happens!

---

### Post by ninjaprawn on 2007-05-21
wow!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

its taken me ages to get this working!!!!!

thanks for the help!!!

---

### Post by calraith on 2007-05-21
Just out of curiosity and for future reference for anyone happening across this thread from a Google search, what did you do to get it working?

---

