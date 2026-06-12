---
title: "enabling telnetd (it's on a closed network)"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by ford50gt on 2007-02-02
I know the risks invilved with telnet.  This box is on a closed network.  I need to have a telnet server running on this box.

I have run apt-get install:
inetd
telnetd

restarted the box and still get "Connection refused"

Please no posts about using something else.

Thanks,

Greg

---

### Post by mightyteegar on 2007-02-02
1.  Is there a firewall running on the server machine that's perhaps blocking connections?

2.  Can you ping the server from another machine?

---

### Post by ford50gt on 2007-02-05
not firewalled.

I can ping from other boxes

inetd.conf:
telnet   stream   tcp   nowait    telnetd.telnetd   /usr/sbin/tcpd   /usr/sbin/in.telnetd

tried adding ALL:  ALL in /etc/hosts.allow

---

### Post by spd106 on 2007-02-05
Try this [http://www.ubuntuforums.org/showpost.php?p=1558629&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1558629&postcount=9)

---

### Post by ford50gt on 2007-02-05
No telnet in netstat -a

the only difference I had was that I installed telnetd before inetd.

Do I need to uninstall these and do it again in the proper order?

Greg

---

### Post by ford50gt on 2007-02-05
I can force it to work once by running **/usr/sbin/in.telnetd 23 &** 

nmap shows no open port for telnet unless I run the above command then it works.

could tcpd be failing?

Greg

---

### Post by ford50gt on 2007-02-05
Figured it out!

I had the wrong internet superserver installed.

inetutils-inetd instead of netkit-inetd once I remedied that I was good to go.

Thanks spd106 for the info and everyone else for the help!

Greg

---

