---
title: "Tiny os crahed my terminal"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by bharani16 on 2010-05-16
i installed Tinyos ..Tossim yesterday...it didnt work fine..It had some  installation problems...

But when i rebooted i got this unique problem..

It booted well but when i entered terminal following happened on own

[FONT=Century Gothic]$command not found
connecting to Tinyos[/FONT]

Then all themes got disabled..basic ubuntu came but couldn open any  application until i put my visual effects to normal...The same happened  repatedly...

Now i am unable to enter terminal itself..

Please help soon

These were the steps i followed to install tossim

1) add bellow repository to your [FONT=courier new]/etc/apt/sources.list[/FONT]  though it is for hardy, it is working for intrepid also

deb  [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) hardy main

2) with  following commands you can update the apt-cache and search the required  packages thin you can install the required version and all.

apt-get  update
apt-cache search tinyos
apt-get install tinyos-2.1.0

3)  then install python development package (headers)

apt-get  install python-dev

4) Edit /opt/tinyos-2.1.0/tinyos.sh  and change the CLASSPATH env-variable as bellow

CLASSPATH=$CLASSPATH:$TOSROOT/support/sdk/java/tinyos.jar:.

4)   Import /opt/tinyos-2.1.0/tinyos.sh   in your .bashrc; include bellow code snippet to ~/.bashrc

[FONT=courier new]if [ -f /opt/tinyos-[/FONT][FONT=courier new]2.1.0[/FONT]/tinyos.sh ] ; then
.  /opt/tinyos-[FONT=courier new]2.1.0[/FONT][FONT=courier new]/tinyos.sh[/FONT]
[FONT=courier new]fi[/FONT]

5) Now  execut bash again or restart the terminal and chech your enviorenment  with bellow command. It will check the enviorenment and report you the  status. (Ignore the WORNING returned due to graphvis version)

tos-check-env

6)  Lets compile the first application

cd $TOSROOT/apps/Blink
[FONT=courier new]make micaz[/FONT]

for  simulator

make micaz sim

Please help soon 

Thanks in advance

---

### Post by gmargo on 2010-05-16
> **bharani16 said:**
> 
It booted well but when i entered terminal following happened on own

[FONT=Century Gothic]$command not found
connecting to Tinyos[/FONT]

Then all themes got disabled..basic ubuntu came but couldn open any  application until i put my visual effects to normal...The same happened  repatedly...

Now i am unable to enter terminal itself..



You either messed up your $HOME/.bashrc when editing it, or that script is not meant to be sourced.  Comment out the .bashrc addition (or restore the version of .bashrc that you saved before editing - you did save it, didn't you?) and reboot to get back to a working setup.  Then figure out what went wrong.

---

### Post by gmargo on 2010-05-16
[LEFT]On my 8.04 Hardy system, I installed tinyos-2.1.1 (why did you choose an older version?).  After sourcing the unmodified setup file, I was able to compile the examples you listed.
[/LEFT]
 ```

$ source /opt/tinyos-2.1.1/tinyos.sh
$ cd $TOSROOT
$ sudo chown -R gmargo:gmargo .
$ cd apps/Blink
$ make micaz
$ make micaz sim
[LEFT] 
```[/LEFT]

---

### Post by bharani16 on 2010-05-18
Hey got my terminal working back....restored my ~home/.bashrc....

Can you provide me the correct steps to install tiny os on ubuntu:confused:

---

### Post by gmargo on 2010-05-18
> Can you provide me the correct steps to install tiny os on ubuntu:confused:
You had the procedure correct, but I installed the more recent version.
```

apt-get install tinyos-2.1.1

```

---

