---
title: "Thin client server + client"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by bcmiller on 2007-03-19
I am getting a new computer, just intime for Fiesty, and I wanted to make the best use of my old computer.

I have two kids, 9 and 6 respectively and my 9 yr old has a really slow computer running PCLOS (very slowly).  

The computer I am handing down is really fast.  2.8 gig pentium (overclocked to 3.0) 1 gig of ram, 128mb Nvidia 5200 and 120 GIG HD.  currently running Ubuntu 6.10

I am only getting a new computer because this one has an odd issue of shutting down when I burn CDs/DVDs and at other odd times...  It's been very stable when it's just used for email/web and some games and that's all the kids need.  [/aside]

My Goal:
I would like to allow my 9yr old to use my discarded fast computer and allow the >1gig computer to become a thin client running from the 9yr olds computer.

How would I go about doing this or where can I get more info.

Both the Discarded Computer and the potential thin client would need to connect from my wireless router.

Thanks for any help you can provide.

---

### Post by flyboy_2003 on 2007-03-19
You can use NoMachine (FreeNX) as a server on one box, and the NoMachine Client (NX Client) on the other to log in. You can log into the server box from the LAN or over the internet (WAN). If you need specific instructions on how to set it up, then email me back here:

rfennimore (AT) gmail.com

Cheers.

- Rick

PS: I run Ubuntu 6.10

---

### Post by superjet on 2007-03-19
You could also try Linux Terminal Server Project [http://www.ltsp.org/](http://www.ltsp.org/). 
 If your old machine has a Network card that can boot over a network, then you can actually remove the Hard Disk from your kids machine and everything is stored on your main machine.

 Edbuntu has LTSP installed already and is very easy to set up. It is directed toward schools with the thought of having one robust machine that allows lesser machines to boot off the robust machine and use it's resources.
 
 Regards,
 Jamie

---

### Post by bcmiller on 2007-03-21
I was really impressed with nomachine but it wasn't really clear how it can be installed.

It looked like I needed a working distro on my slow computer in order to run the nomachine client.  Is that so?


__________________________________________________________-
for the LTSP

If I cannot boot from the network on my terminal machine (slow computer) what should I do to get the client working?  It can boot from CD fine and I could use a floppy if nessesary.

I have seen a verison of LTSP that isn't the latest version (version 5 is latest I think).  Should I just install those packages via Synaptic?

again, thanks for the advice.

---

### Post by serpentine on 2007-03-21
NoMachine NX is pretty straightforward to install and you can reference the documentation that is available here:
[URL="http://www.nomachine.com/do/index.php"]
http://www.nomachine.com/do/index.php[/URL]

NoMachine does offer a NX Free Edition which is a free, 2-user version of the software.  You can reference the feature list here:

[http://www.nomachine.com/features.php](http://www.nomachine.com/features.php)

Edubuntu would also be a nice way to go since it includes a lot of learning packages that may benefit your 9 yr. old.

---

