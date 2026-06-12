---
title: "X-windows launch on host, not client, computer"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by jeremiahbuddha on 2011-07-26
I have an Ubuntu 11.04 Desktop computer at home, and I have been trying to set up X11 so that I can ssh into this box remotely and launch x-applications on my Mac. I've edited both my /etc/ssh/ssh_config and /etc/ssh/sshd_config files (on my linux box) to include "ForwardAgent yes" and "ForwardX11 yes", and restarted my ssh server. 

I am able to ssh into my linux box just fine (ssh -X mycomputer), but when I launch an x-application, the window appears on my linux box (server) not my Mac (client)!

To make sure something wasn't wrong with my Mac setup, I was able to ssh into a work computer running RedHat and launch an x-application. It appeared on my Mac as expected.

Any idea what settings I have off on my linux box that won't allow me to launch x-applications on my Mac after I've ssh'd in?

---

### Post by androssofer on 2011-07-26
mine worked out the box, no changing of conf files...(client is a mac also) weird...

ssh onto ur server:

```
ssh -X -C username@hostname
```

then do:

```
echo $DISPLAY
```

and post the results.

mine is localhost:10.0. on a few difference machine to different hosts.

so maybe try: (on the server machine)

```
export DISPLAY=localhost:10.0

```

then try and launch sumthing

or try:

```
ssh -Y -C username@hostname
```

and try to launch sumthing...

-Y is less secure tho, so dnt open anything important...


EDIT: Additional: read other posts on this. is synaptic package manager check tht libx-stuff and xauth are installed..

---

### Post by jeremiahbuddha on 2011-07-26
My $DISPLAY echoes back as " :0 ". I spent about three hours trying to figure this out last night, and from [what I read]("http://www.cisl.ucar.edu/docs/ssh/guide/node29.html"), I shouldn't have to manually set the DISPLAY env variable if I have my server configured right. Any tips here?

And could you link me to some of the other posts you mentioned? Thanks!

---

### Post by androssofer on 2011-07-26
> **jeremiahbuddha said:**
> My $DISPLAY echoes back as " :0 ". I spent about three hours trying to figure this out last night, and from [what I read]("http://www.cisl.ucar.edu/docs/ssh/guide/node29.html"), I shouldn't have to manually set the DISPLAY env variable if I have my server configured right. Any tips here?

And could you link me to some of the other posts you mentioned? Thanks!

yeah should automaticly configure it... humm.

this is the post about the libx-stuff and xauth [http://dbaspot.com/bsd-freebsd-misc/251580-problem-ssh-x11-display-variable-not-set.html]("http://dbaspot.com/bsd-freebsd-misc/251580-problem-ssh-x11-display-variable-not-set.html")

---

