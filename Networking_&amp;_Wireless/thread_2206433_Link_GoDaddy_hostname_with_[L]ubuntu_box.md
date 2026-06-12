---
title: "Link GoDaddy hostname with [L]ubuntu box"
date: 2014-02-19
forum: Networking &amp; Wireless
---

### Post by Elastic_Potential on 2014-02-19
As a disclosure, I'm very new at all this; I last forayed into a web-accessible SSH server as a college junior back in 2010, and I'm gradually -- painfully so -- re-remembering much of what I'd forgotten.

I've happened upon an old pc, which I'm currently managing on my local network via SSH (username@192.168.x.xx).  It's set-up primarily for me to manage my documents, music, etc.  I was hoping to find a way to link this with an old Godaddy domain; a representative told me to point the "A (Host)" IP to my router, which I did, and I can get a successful ping (it shows a mixture of my router IP and some ISP info).

However, I'm not really sure how this is supposed to work because my lubuntu box has an IP address of 192.168.x.xx, and there are at least five other internet-connected devices in our apartment; simply adding the router IP seems strange. Also, I've read in very dated posts that connecting your server with Godaddy only works for static IPs (the recommendation is using the now-nonfree DynDNS), and we're using DHCP; the rep with whom I spoke seemed pretty confident about his solution, but I thought it'd be worth bringing up.

If I had to posit this as a question, I suppose I would ask: how do I SSH into my ubuntu box via a Godaddy domain?

I have a headache, so I apologize in advance for punctuation/grammatical/conceptual errors.

---

### Post by SeijiSensei on 2014-02-19
You need to go into the router's configuration and find the tool that allows you to forward ports.  I recommend using an arbitrary external port, say 22222.  Tell the router to forward traffic arriving on that port back to port 22  on the SSH server.  Then if the A record points to your router, you should be able to run "ssh example.com" and be connected.

However if your ISP does not grant long IP leases, so that your external address changes frequently, this method will fail as soon as the address changes.  For that you need those types of DNS solutions that work with dynamic IP assignments.  I know nothing about them, but others here can help.

---

### Post by Elastic_Potential on 2014-02-19
> **SeijiSensei said:**
> You need to go into the router's configuration and find the tool that allows you to forward ports.  I recommend using an arbitrary external port, say 22222.  Tell the router to forward traffic arriving on that port back to port 22  on the SSH server.  Then if the A record points to your router, you should be able to run "ssh example.com" and be connected.
Thanks for the reply.  Are you suggesting setting-up a port forward that looks like: Start 2222/End 22?  If so, my router won't accept this combination :\

I did, however, try Start 22/End 22; "ssh example.org" resulted in a lovely greeting:
```

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@       WARNING: POSSIBLE DNS SPOOFING DETECTED!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
The RSA host key for EXAMPLE.org has changed,
and the key for the corresponding IP address xx.xxx.xxx.xx
is unknown. This could either mean that
DNS SPOOFING is happening or the IP address for the host
and its host key have changed at the same time.
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
s0:m3:l0:ng:h3:x5:tr:1n:9x.
Please contact your system administrator.
Add correct host key in /home/caeser/.ssh/known_hosts to get rid of this message.
Offending RSA key in /home/caeser/.ssh/known_hosts:2
  remove with: ssh-keygen -f "/home/caeser/.ssh/known_hosts" -R example.org
RSA host key for example.org has changed and you have requested strict checking.
Host key verification failed.

```

---

### Post by Elastic_Potential on 2014-02-19
I was able to solve the above by setting the start/end for another random port (I read somewhere that some malware likes to listen on 2222) and set openssh to listen on that port.  It now seems to work fine :)  No RSA errors or anything.  Thank you so much for your time.

As a personal side-note, do you have any recommendations for extra reading about network security?

---

