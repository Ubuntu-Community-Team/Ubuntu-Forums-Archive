---
title: "scp one file to several machines"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by chrisdee on 2010-03-10
Hello. I'm running a ubuntu 9.04 computer lab with 8 machines.
I have a common admin user on all the machines.

Any idea how I can copy one file out to all the other machines
wich scp or something ?

Currently I'm having to manually scp 8 times for each machine I want to send a file to.
Is it possible to do it with one command or automate it in some way ?

---

### Post by undecim on 2010-03-10
Try this:

```
for machine in machine1.local machine2.local machine3.local
do
	scp /path/to/file $machine:/destination/path/
done
```

This will transfer to each machine, one after the other. You can add as many machines to the machine*.local list as you want.

EDIT: If you have to type in your password though, this could be a bit annoying, because you would have to type in your password each time. Of course, if you don't already have pubkey authentication set up, you could set it up on the other machines while the first one is transferring.

---

### Post by undecim on 2010-03-10
Also, another word of advice:

If you have to do this kind of thing often, it may be easier to set up NFS or SSHFS on each of the 8 machines to access the file over the network, or set up a cron job to check an NFS or SSHFS folder on the main machine every few minutes and copy any new files (rsync would be good for this)

I can help you out with that stuff too, if you want.

---

