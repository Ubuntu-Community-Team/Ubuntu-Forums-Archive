---
title: "[SOLVED] cannot connect to internet"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by lrs52200 on 2008-10-23
Talk about noob - I'm barely past conception....

Okay, I can no longer connect to the internet because I apparently did something when I was aimlessly clicking around in 'networking' and 'network tools.'

I'm getting the following error after the page fails to load:  could not resolve us.archive.ubuntu.com

....I'm not sure if anyone is able to help me because I have no idea what I did.  But could someone try?  I'm using my daughter's computer to try to resolve this.
    Oh yes, I also am not able to use the synaptic package manager to uninstall/reinstall firefox - or anything else for that matter because I cannot connect at all......

---

### Post by Ayuthia on 2008-10-23
If it is wireless, did you switch off roaming?

---

### Post by lrs52200 on 2008-10-23
It's a wired network........

---

### Post by Ayuthia on 2008-10-23
Have you tried restarting your computer?  The selection you made might be a temporary one.

There should be a network icon on the panel that you can left-click (looks like a computer or maybe something with bars or balls).  It should give you an option to select a network.

---

### Post by lrs52200 on 2008-10-23
What about the system log?  Would that be helpful at all in determining the havoc I wreaked?

---

### Post by lrs52200 on 2008-10-23
Oh yes, I tried to restart the computer but it failed to correct the problem.

---

### Post by Ayuthia on 2008-10-23
Are you able to see the computer on the panel?  If you right click on it, there should be an option to Enable Networking.  Is it checked?

EDIT: As for the syslog, it most likely won't give us any information because it was a change in the properties.

---

### Post by lrs52200 on 2008-10-23
Yes, I see the computer icon and right-clicked it, however, it is already enabled.

---

### Post by lrs52200 on 2008-10-23
I found this in the debug report:  Oct 23 08:28:37 pamela-desktop kernel: [ 4381.369545] eth0: no IPv6 routers present

Does that mean I uninstalled my router?

---

### Post by Ayuthia on 2008-10-23
Can you go into Accessories->Terminal and try the following:
```
sudo ifconfig eth0 up
sudo dhclient eth0
ping -c1 www.google.com
```
This will try to bring up your wired card manually and then try to see if it can reach [www.google.com](www.google.com).  To get out of the Terminal, just type exit at the prompt.

---

### Post by lrs52200 on 2008-10-23
I have no idea what you just had me do, but it worked!  Thank you.  I am now able to access the internet again.  One question though, after I typed in ping -cl www. google.com, it returned:  bad number of packets to transmit....

does that mean anything bad?

---

### Post by Ayuthia on 2008-10-23
> **lrs52200 said:**
> I have no idea what you just had me do, but it worked!  Thank you.  I am now able to access the internet again.  One question though, after I typed in ping -cl www. google.com, it returned:  bad number of packets to transmit....

does that mean anything bad?

No, it just means that you type -cl (lower case L) instead of -c1 (the number one).

---

### Post by lrs52200 on 2008-10-23
Thank you again!!

---

