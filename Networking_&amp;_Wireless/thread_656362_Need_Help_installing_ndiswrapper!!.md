---
title: "Need Help installing ndiswrapper!!"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by khanoftartary on 2008-01-02
Alrighty, I just installed my shiny new version of Ubuntu 7.04, got things up and running and everythings looks good. Whoops, my internet isn't connected anymore. I use the network manager (using a wireless network), and it doesn't even detect my wireless network. So...gotta trouble shoot, so I jump over to my roomates Windows machine, jump on the internet, and start looking. As far as I can tell, my wireless card isn't supported, so I pull out the driver CD, pull everything I need off it, and then go looking for ndiswrapper. I can't find it in synaptic, so I try 'add CD' and add my installation CD...hmmm...already added, and ndiswrapper is still not there. I can't add anymore sources to synaptic, because I have no internet connection. Back to my roomies computer, and I grab 'ndiswrapper-1.51.tar.gz' off the internet. I put it on a stick, and move it to my computer. Hmmm, well, now I can't seem to get synaptic to recognize the new file in this form...let's see what it says. I extract it to my desktop, look at the install file and find...command line:(. So...I'm not very good with terminal, and the instructions seem to suggest that I ought to be, or at least know some basics (which I don't, it's been years since I've done anything in command line). So....I need one of the following, pretty please:
1. a way to get synaptic to recognize either ndiswrapper on my install cd (I've been told that it's there, but synaptic doesn't see it)
2. A way to get synaptic to use the tarball
3. Very simple terminal commands to install the tarball (explain as you would to a three year old)
4. A way to install wine-0.9.52 from a tarball (also not recognized in synaptic, in the CD or in the tarball) which I was planning on doing through synaptic after I got my internet up and running, but which I think I might be able to use to simply use the .exe on my wireless driver CD (this one is kinda of a last ditch effort that I don't expect to work, I would prefer one of the previous solutions).

Thanks a bunch.

---

### Post by Saint Angeles on 2008-01-02
usually a tarball will have source code in it open it up and extract it into a directory on your desktop, then navigate to it in the command line (cd Desktop/ndis...)
then:```
./configure
make
sudo make install
```thats generally how you compile your own source code.

now as for ndiswrapper specifically, im having issues with it on my sisters computer so im kind of confused too.

anybody else have any ideas?

---

### Post by khanoftartary on 2008-01-03
I put in **./configure**, and got the following error: **bash: ./configure: No such file or directory**

Any Advice?



*Edit:* Okay, I went and looked at the install file on the tarball again, and it says to check the 'modules directory' using the command **ls /lib/modules/`uname -r`/build** and look for **include** and **.config** before attempting install. I have **include**, but I don't have **.config**. It says that that means that I don't have a recent enough kernel and that I need to update it. Could anyone tell me what that means, and, more importantly, how to fix it?

Thanks a bunch!

---

