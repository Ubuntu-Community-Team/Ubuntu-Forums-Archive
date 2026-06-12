---
title: "Ssh between Ubuntu 7.04 and Mandriva 2008.0"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by Linux_oid on 2008-03-04
I have two boxes: Ubuntu 7.04  and Mandriva 2008.0-free (minimal installation; no X). I installed openssh, openssh-client and openssh-server on both of them.

Unfortunately, I can't ssh from Ubuntu to Mandriva (ssh: connect to host xxx.xxx.xxx.xxx port 22: Connection timed out). I can ssh from Mandriva box  to Ubuntu box with no problem. I tried to telnet Mandriva box it didn't work either.

Any thoughts?

---

### Post by jcwmoore on 2008-03-04
are you trying to connect to this machine from inside or outside of your network? i.e. are both machines on the same network or is this a situation were you have one machine at work and another at home, or something like that?

EDIT:

you may also want to check that your mandriva box is listening on port 22 (i know it is the default, but it might be listening on something eles), /etc/sshd_config is the file that tells ssh what port to listen to.

---

### Post by AdamWill on 2008-03-04
22 is default on Mandriva. Check you don't have the Mandriva firewall running and blocking ssh: run 'drakfirewall' (or just find it in the Mandriva Control Center) and either disable it or check the box that allows ssh through.

edit: yep, I saw you're not using X - the drak* tools run from console, too :)

---

### Post by Linux_oid on 2008-03-04
I did *vi /etc/sshd_config*. Vi told it was a new file. 
*Vi /etc/sssh/shd_config* gave me access to configuration file. It told me the default setting is port 22. I tried to disable something like "Authentication s/key". It didn't help. The same story about "RSAAuthentication" and "Pubkeyauthentication"  (changed yes to no and uncommented)

*Drakfirewal* let me disable all the item protected. It didn't help.

I restarted ssh (*/etc/init.d/ssh restart*) every time I made changes.

---

### Post by The Cog on 2008-03-04
If the server wasn't listening you would get a connection refused message. We know routing is OK because they can talk - ssh works the other way. Timeout means no response received at all - so firewall is the only remaining theory I have. 

This command will remove all firewall rules (just for testing briefly):
[B]sudo iptables -F
sudo iptables -X[/B]

Are they on the same LAN? If they are at separate locations on the internet, could it be that port forwarding in one of the routers isn't configured correctly?

---

### Post by Linux_oid on 2008-03-04
Well, I misunderstood Mandriva box firewall configuration. I need to checkmark service (ssh) if I want it to be accessible. I did opposite.  

Now  I've got an ansver from Mandriva box after issuing *ssh [email]username@xxx.xxx.xxx.xxx[/email]*


@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

[..]
Host key verification failed.

---

### Post by The Cog on 2008-03-05
This info is stored in your home area, in ~/.ssh/known-hosts. You must have connected to a different machine with the same hostname/address in the past. You can either delete the appropriate entry in known-hosts, or if you can't figure out which entry that is, just delete the file.

---

### Post by Linux_oid on 2008-03-05
Yeah, I modified both boxes: installed/reinstalled ssh even OS a few times. I have wireless LAN with static IP. It sounded like I have no choise but to delete ~/.ssh/known_hosts (Ubuntu box). 

I can ssh Mandriva box now.

P.S. Just wandered, how to delete the same file on Mandriva box? It doesn't have GUI and I've just started having the same problem (ssh from Mandriva box to Ubuntu box WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!).

Thanks in advance.

---

### Post by The Cog on 2008-03-05
log in and type:
**rm .ssh/known_hosts**
or if you know how to identify the line to delete:
**vi .ssh/known_hosts**
or
**nano .ssh/known_hosts**

---

### Post by AdamWill on 2008-03-06
nano's not in a default MDV install, so only the 'vi' line would work =) you have to add nano from the repositories if you use it (like I do).

---

### Post by The Cog on 2008-03-06
Ah. I had doubts in my mind when I wrote that. But I also know that many beginners won't know how to drive vi.

---

