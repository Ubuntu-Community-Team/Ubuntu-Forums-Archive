---
title: "Serring up file server for Mac"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by Julez Edward on 2007-10-14
I've done one month of research on the web for this and still no solution, so I have little hope someone in here could help me out.

I have a linux box with 1TB capacity running perfectly Kubuntu. There are two laptops that need access to this box. I have a samba server on the linux box, and everyone can connect to straight from the Finder without troubles.

The problem starts when I try to copy files or folders with a " / etc in. The two pseudo solutions I found so far were a filerenamer utility and using dmg files on the server with some kind of a clone app. I didn't try them out myself, because I really need to be able to use the linux box as an external shared harddrive. (push & pull files, and having a share ready for the upcoming TimeMachine space of the several laptops at our company)

As far as I'm informed it makes no sense to format the linux box drives to HFS (HFS+ is still not supported in the current linux kernel) using AFS instead of samba doesn't solve it either. The problem would be in the samba (or whatever other filetransfer protocol you like). Is that correct?

On the internet there are no real solutions to this problem, while this might seem a quite important thing to most Apple based companies that want to save money on the X-Serve stuff by setting up a linux server. If there is really no solution available at the moment, then I which to be informed on who might be responsible for solving this problem or who I'd have to address this issue to. 

If anyone might have the same issues or maybe a solution, feel free to post it here. 

Thank you very much in advance.

---

### Post by arkhitekton on 2007-10-14
Hi

I'm not sure if this is relevant but the /etc directory is restricted to root.  If I'm doing things in there I use sudo.  You could try
sudo cp <source> <destination>

Apologies if you know this already.

---

