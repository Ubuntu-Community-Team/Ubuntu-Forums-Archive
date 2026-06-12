---
title: "remote desktop/vnc from ubunto 10.04 into windows vista"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by _BIG_ on 2010-05-09
ive tried searching and reading thru a sea of text on this and have gotten more confused as ive gone on lol.

i have realvnc enterprise server installed on my home desktop with windows vista and can connect to it perfectly using realvnc viewer from other windows systems.

when i try to connect from ubuntu 10.04 using remote desktop viewer with protocol set to VNC and host set a few different things ive tried (example host: 192.168.111.1 or host: 192.168.111.1:5XXX or host: 192.168.111.1::5XXX) i get back a reply of "Authentication method to host 192.168.111.1 is unsupported. (5)"

i have installed these packages in synaptic package manager in attempts to help get this workin from reading other threads:
libgtk-vnc-1.0-0
tsclient
vinagre
vino
xvnc4viewer

i have also downloaded "VNC Enterprise Edition Viewer for Linux (x64)
Stand-alone Viewer
Version 4.5.3"
from [http://www.realvnc.com/download/enterprise/4.5.1]("http://www.realvnc.com/download/enterprise/4.5.1")''both the executable(which i dont know how to run) and the gzipped file(again dont know what to do with) to try and solve this problem.

ive read many suggestions saying things about ssh but would prefer not to have to go thru that as i am very new to linux and feel i might get even more lost with that.

from what i understand realvnc encrypts everything so security shouldnt be too bad with it i dont think


thanks again

---

### Post by _BIG_ on 2010-05-23
damn...i dont like to bump but its been 2 weeks.

anyone have ANY ideas?

---

### Post by gmxgeek on 2010-05-23
In general, enterprise VNC has issues with connectivity. Is there a reason you can't use the free edition?

---

### Post by _BIG_ on 2010-05-23
> **gmxgeek said:**
> In general, enterprise VNC has issues with connectivity. Is there a reason you can't use the free edition?

free edition on which side?

the win vista server side or the ubuntu side im trying to connect from?

ive downloaded a free realvnc viewer for ubuntu from their site but have no clue how to install it lol

ive installed different things in synaptic that are i believe the realvnc packages for ubuntu but no help

i dont think the free ditions have encryption either which would mean id have to set up ssh at home also and get connected to that from work

---

### Post by drdos2006 on 2010-05-23
Have a look at TeamViewer, it has linux and Windows distros. You will need a server on one machine and a client on another.

regards

---

### Post by CharlesA on 2010-05-23
Check the firewall on Windows and see what port VNC is running on.

---

### Post by sylvester_0 on 2010-05-23
Err, why don't you use the remote desktop server (ms terminal services) that's built into Windows (enable it under Control Panel -> System -> Remote then forward port 3389 on your router) then connect to it via rdesktop? It's much faster and offers far more features than VNC could ever offer. It's encrypted by default, no additional config necessary.

---

