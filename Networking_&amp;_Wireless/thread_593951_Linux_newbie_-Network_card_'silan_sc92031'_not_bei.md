---
title: "Linux newbie -Network card 'silan sc92031' not being recognized -no idea abt commands"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by phabe on 2007-10-27
this is the first time im trying linux hands on. 
with Ubuntu 7.10
installation and everything was fine, no probs.

Not able to access internet as my Network card **'silan sc92031'** is being recognized
'unable to detect network devices'

im not technologically challenged, i fix my friends computers. 
but have no clue about the command prompt. i dont know how to use it.

i read other threads here regarding this network card. ndiswrapper etc. Have no idea how to deal with the command prompt.

is there an easier way to solve this prob. 

all further things like installing codecs to play media have been halted due to no access to internet. im stuck here. once im thru, i can be on my own as il have the internet.

I really hope i can accomplish this without having to know much abt the commands.
or i can do it with an explanation aimed at dummies.
can u guide me pls.

thank u

---

### Post by Lambert on 2007-10-28
don't be afraid of the command line. It will be easier to help you trouble shoot as we can type the commands out. all you have to do is copy and paste then hit enter. 

The following will just be information gathering. Open a terminal and run these commands.

```

sudo lshw 

ifconfig

```

Post the output from those commands here.

The lshw command lists all your hardware. If you can narrow that down to just this device you can post just that. If not just post everthing.

And I'm not sure if this next command will work but just a try.

When you run ifconfig, it shows interfaces to your network devices. You will see lo and hopefully something like eth0. If you see eth0 or soemthing similar try this.

```

sudo ethtool eth0

```

of course replacing eth0 if needed with interface from ifconfig command. If you get output, post that here also.

---

