---
title: "Operation not Permitted, can't change my MTU."
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Entrenched on 2009-04-29
I just installed Ubuntu 8.10 on my computer, rather different from Windows that's for certain.

Anyhow, my computer is super slow, with lots interruptions and such. Seems the MTU is set to a ridiculously low level by default. I have tried altering the MTU based upon what my research has told me, yet when I try to change it, the damn terminal service window says "Operation not permitted. Below is as copy of the terminal log, and all the info about my connection. If anyone can tell me how to bypass this problem and alter the MTU, which is set super low by default, I'd sure appreciate it.

Also had another command I tried, which said I "don't have permission" or some such nonsense. Anyhow, the log is below.


eth0      Link encap:Ethernet  HWaddr 00:0a:eb:81:72:86  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:461941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:386610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:262036108 (262.0 MB)  TX bytes:28033260 (28.0 MB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3600 (3.6 KB)  TX bytes:3600 (3.6 KB)

valinor@valinor-desktop:~$ iface eth0 inet static
bash: iface: command not found
valinor@valinor-desktop:~$  iface eth0 inet static
bash: iface: command not found
valinor@valinor-desktop:~$ ifconfig eth0 mtu 1492
SIOCSIFMTU: Operation not permitted
valinor@valinor-desktop:~$ 


Anyone know what I need to do to alter my MTU to an acceptable level that "is permitted"? Also, for some reason my computer, when in Terminal services, won't allow me to type my password, or there is some kind of bug, for it says "Authentication Failure" after I type in my password. Like I said though, the cursor doesn't move, and no text is being input, clearly. Below is what I mean.

valinor@valinor-desktop:~$ su
Password: 
su: Authentication failure
valinor@valinor-desktop:~$ su
Password: 
su: Authentication failure
valinor@valinor-desktop:~$ su
Password: 
su: Authentication failure
valinor@valinor-desktop:~$ 


Is this a bug, or am I missing something? OK, hope someone out there knows what the heck is going on, I'm starting to miss the virus ridden XP at this point.

---

### Post by Kosimo on 2009-04-29
> **Entrenched said:**
> I just installed Ubuntu 8.10 on my computer, rather different from Windows that's for certain.

Anyhow, my computer is super slow, with lots interruptions and such. Seems the MTU is set to a ridiculously low level by default. I have tried altering the MTU based upon what my research has told me, yet when I try to change it, the damn terminal service window says "Operation not permitted. Below is as copy of the terminal log, and all the info about my connection. If anyone can tell me how to bypass this problem and alter the MTU, which is set super low by default, I'd sure appreciate it.

Also had another command I tried, which said I "don't have permission" or some such nonsense. Anyhow, the log is below.


eth0      Link encap:Ethernet  HWaddr 00:0a:eb:81:72:86  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:461941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:386610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:262036108 (262.0 MB)  TX bytes:28033260 (28.0 MB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3600 (3.6 KB)  TX bytes:3600 (3.6 KB)

valinor@valinor-desktop:~$ iface eth0 inet static
bash: iface: command not found
valinor@valinor-desktop:~$  iface eth0 inet static
bash: iface: command not found
valinor@valinor-desktop:~$ ifconfig eth0 mtu 1492
SIOCSIFMTU: Operation not permitted
valinor@valinor-desktop:~$ 


Anyone know what I need to do to alter my MTU to an acceptable level that "is permitted"? Thanks.


Why don't you just try using Network manager?

---

### Post by Pollox on 2009-04-29
In general, if something is denied, not permitted, etc, I just put "sudo" before it (assuming I know what I'm doing will not break my computer).  But like the above poster says, network manager has a gui way of adjusting MTU.

---

### Post by brunogirin on 2009-04-29
According to [this thread in linuxquestions]("http://www.linuxquestions.org/questions/linux-hardware-18/support-of-jumbo-frames-by-nic-531217/"), it looks like your NIC doesn't support the MTU you request.

But to come back to the original problem about your system being slow, can you be more precise about this? Are you sure the performance you observe is related to the MTU?

---

### Post by freak42 on 2009-04-29
you need root (super user , administrator) rights to change this.
prepend 'sudo' in front of your command, and enter your own password (it won't be displayed) when requested:

sudo ifconfig eth0 mtu 1492


brunogirin's post is somewhat off.. OP doesn't want to set jumbo frames (mtu >1500) nor does the returning error message
match the other threads.. afaik

hth

---

### Post by Entrenched on 2009-04-29
I changed the MTU, however once I had done that I had a different problem cropping up, the computer telling me it can not find an address. Now that I have restarted my computer, the MTU is right back to 576, and showing the same error as it did before. Some of the time it just doesn't load the website I requested. Below is the error message.

Connection Interrupted

      

      
      
      

      
        
        

          

The connection to the server was reset while the page was loading.

        


        
        

The network link was interrupted while negotiating a connection. Please try again.


That's what happens when set at 576. However set at 1492, and even 1452, I get "Address not found" for the most mundane sites. I never had this problem with Windows, ever. Spyware, yeah, viruses sure, but this, never. Any thoughts or ideas?

---

