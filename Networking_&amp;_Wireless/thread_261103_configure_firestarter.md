---
title: "configure firestarter"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by tempo500 on 2006-09-19
hi,

i am using firestarter(on my office pc) for sharing my internet connection (on my workstation). the internet connection is working great, thanx to this [thread]("http://ubuntuforums.org/showthread.php?t=76346&highlight=%22internet+access+point%22+desktop")

but it seems to me that firestarter is blocking the normal lan connection for sharing files. i got to the point(through trial and error) that i can access the shared folders on the office pc, but i cant see the shared folders on the workstation when i am sitting infront the office machine.

so far i have entered 192.168.2.103 in the inbound traffic policy / allow connections from host.

where do i have to enter the second ip, to see the folders on the office pc?
everything is smb... how do i install nfs? i guess this protocol is better?

please help, i almost got a functioning workstation! just swithced form windows...

thanx, phil

---

### Post by kidders on 2006-09-19
Hi Phil,

It's not really a great idea to allow unrestricted access to your PC from anywhere ... it kinda defeats the purpose of having a firewall. Basically, if you want to permit certain kinds of connections, your first stop should be a google search for common port numbers. For instance, if you want to allow incoming connections to a samba server, you need to open ports 139 and 445, afaik.

Try to limit such access to within your local subnet though.

**Edit:** I re-read your post ... I'm not quite confident your firewall is the problem. It seems you're having trouble accessing shares on another PC from the firewalled one, in which case, the other PC is probably the one with the problem?

---

### Post by tempo500 on 2006-09-20
thanx for your feedback! i removed the ip in "allow connections from host" and allowed the apropiate service ports. works like a charm.

thanx again, phil

---

