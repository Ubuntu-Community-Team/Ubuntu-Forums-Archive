---
title: "baffled by sys(8) utility option"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-15
Hi, 
I'm following some instructions on how to establish my old scrn res but have recievied some unexpected options that  i don't understand?

The procedure is as follows:

...

sudo install NVIDIA-Linux-185.18.pkg.run /usr/src
sudo ln -fs /usr/src/NVIDIA-Linux-185.18.pkg.run /usr/src/nvidia-driver


Kill X
Now, it's time to stop X and the gdm (or kdm for Kubuntu Users)
This requires that you logout and switch to another tty console ( Ctrl+Alt+F1 ).

Login to the shell, and kill gdm:
Code:

sudo /etc/init.d/gdm stop


[But this returns...]


Rather than invoking init script through /etc/init.d/gdm, use the service(8) utility, e.g. service 

Since the script you are attempting to invoke has been converted to an upstart job, you may also use the stop(8) utility, eg stop gdm stop:...

[~$ stop gdm stop returns:]

~$ stop gdm stop
stop: Env must be KEY=VALUE pairs


[i'm completely flummoxed by what ever options i'm being offered here]

---

### Post by matthewbpt on 2009-11-15
Just type
```
sudo service gdm stop
```
to stop the gdm.

---

### Post by nnjond on 2009-11-15
Hi, 
I'm following some instructions on how to establish my old scrn res but have recievied some unexpected options that  i don't understand?

The procedure is as follows:

...

sudo install NVIDIA-Linux-185.18.pkg.run /usr/src
sudo ln -fs /usr/src/NVIDIA-Linux-185.18.pkg.run /usr/src/nvidia-driver


Kill X
Now, it's time to stop X and the gdm (or kdm for Kubuntu Users)
This requires that you logout and switch to another tty console ( Ctrl+Alt+F1 ).

Login to the shell, and kill gdm:
Code:

sudo /etc/init.d/gdm stop


[But this returns...]


Rather than invoking init script through /etc/init.d/gdm, use the service(8) utility, e.g. service 

Since the script you are attempting to invoke has been converted to an upstart job, you may also use the stop(8) utility, eg stop gdm stop:...

[~$ stop gdm stop returns:]

~$ stop gdm stop
stop: Env must be KEY=VALUE pairs


[i'm completely flummoxed by what ever options i'm being offered here]

---

### Post by Sef on 2009-11-15
merged threads.

---

### Post by nnjond on 2009-11-15
Dear Sef

Thanks for your intervention; however ihave looked through that thread and havn't recognised anything relevant to my predicament. Do you understand my prob?

---

### Post by -=hazard=- on 2010-02-05
> **nnjond said:**
> Dear Sef

Thanks for your intervention; however ihave looked through that thread and havn't recognised anything relevant to my predicament. Do you understand my prob?

matthewbpt answered you correctly.

Type to stop: ```
sudo service gdm stop
``` and to start ```
sudo service gdm start
```

---

### Post by demontager on 2010-02-27
Following methods are not work
sudo service gdm stop
sudo service gdm start
I want to install NVIDIA drivers as well.

---

### Post by 3rdalbum on 2010-02-27
> **demontager said:**
> Following methods are not work
sudo service gdm stop
sudo service gdm start
I want to install NVIDIA drivers as well.

In what way did they not work? Did the Nvidia installer still complain that X was running?

I always used to use:

```
sudo killall gdm
```

which I think should still work?

And I'm not sure why you're not using the Hardware Drivers program, or installing the Nvidia driver through a [PPA]("https://launchpad.net/~nvidia-vdpau/+archive/ppa"). You're just creating more work with yourself, especially when you upgrade your kernel and find that you have to reinstall the Nvidia driver manually again. If you use the Hardware Drivers program or the PPA, the Nvidia driver stays in sync with your kernel.

---

