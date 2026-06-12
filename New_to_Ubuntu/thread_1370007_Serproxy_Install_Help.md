---
title: "Serproxy Install Help"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Husar on 2010-01-01
Trying to get Serproxy working under Ubuntu.  I had no problems with the 'make' and then 'make install' process. The install instructions says to do the following:

1. Unpack the source.
2. 'cd' into the source directory
3. Type 'make' to compile
4. If all goes well, become too and type 'make install', which will install the 'serproxy' binary to /usr/local/bin
5. Copy the config file 'serproxy.cfg' to /etc
6. Edit  /etc/serproxy.cfg to configure the proxy.

I have done all that with any issues.  I have configured the serproxy.cfg. I am running serproxy on another machine running OS X without any issues so I know my serproxy.cfg should  be correct. 

Now comes my problem.  If I terminal into /etc/ and type 'serproxy' I get the following error....

**pipe_init: Address already in use**

Also, I am pretty sure that the serproxy.cfg needs to be in the same directory as serproxy so I did copy it to the install directory as well for good measure. Either way I still get that same error.

Can anyone help me or explain what the pipe_init means or what I am doing wrong?

Thanks in advance.

---

### Post by Max_Mackie on 2010-01-01
This may be trivial, but try a reboot. There might have been something started up thats hogging what serproxy needs to start.

---

### Post by Husar on 2010-01-01
Okay, doing that now. One question. Should serproxy start up at boot each time under Ubuntu?  It is not that way under OS X but not sure about Ubuntu.

---

### Post by Husar on 2010-01-01
Okay, looks like a reboot and I am able to get Serproxy running. But I have two more questions.   

How can I create a shortcut to Serproxy and place this in my Favorites tab?

Even though I am now able to launch Serproxy I can't seem to connect like expected. I get the following error.

**Failed to open comm port - connection refused.**

On a different machine OS X my serproxy.cfg is mapped to the following ports like below. Do I have to use different ports under Ubuntu?

----------------------------------

# Comm ports used
comm_ports=1,2,3,4

# Default settings
comm_baud=115200
comm_databits=8
comm_stopbits=1
comm_parity=none

# Idle time out in seconds
timeout=300

# Port 1 settings (ttyS0)
net_port1=5331

# Port 2 settings (ttyS1)
net_port2=5332

# Port 3 settings (ttyS2)
net_port3=5333

# Port 4 settings 
net_port4=5334

-------------------------

---

### Post by Husar on 2010-01-10
A quick update. I was able to solve this problem. Looks like I was one version behind on serproxy. Make sure you get version 0.1.3 and not 0.1.2. Big difference in results.

---

